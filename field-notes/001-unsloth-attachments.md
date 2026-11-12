# Why a large PDF could disappear from an Unsloth Studio chat

*Supersynergy Field Note 001 · Maxim · November 12, 2026*

Suppose you attach a long maintenance manual and ask, “What clearance does the pump need?” The answer is in one paragraph. The model has room for that paragraph, but the entire manual exceeds the budget for attachments. In Unsloth Studio, switching to a larger model could leave the request with zero passages from the manual. Here’s how that happened and what changed when Unsloth merged my fix on August 26. [Merged pull request #9630](https://github.com/unslothai/unsloth/pull/9630)

## Two settings sent almost the same request

The manual is an illustrative example. The regression test uses a file called `big.pdf` with a recorded cost of 50,000 tokens. What matters is how the frontend describes the user’s choice to the backend.

| User’s choice | Relevant fields sent to the backend | Expected behavior for the manual |
| --- | --- | --- |
| Auto, with a large model | `autoinject=false`, field `whole_doc` omitted | Use the attachment. If the full text exceeds the budget, look up relevant passages. |
| Off | `autoinject=false`, `whole_doc=false` | Leave the attachment out. |

Both requests had the same value for `autoinject`. The whole-document path already understood that a file attached to the thread could still be used in Auto. The passage-retrieval path checked only whether automatic injection was enabled. That explains the odd symptom: a short manual worked, while a longer edition of the same manual could disappear exactly when retrieval would have helped.

## What the fix does with the manual

When the full document exceeds the budget in large-model Auto, Studio searches the thread attachment for passages relevant to the question. It checks the size of the text that would actually reach the model and drops lower-ranked passages until the block fits. If even the first passage exceeds the budget, it leaves the block out. Choosing Off still skips retrieval. [Merged implementation](https://github.com/unslothai/unsloth/blob/f3e41f4eb6efb1bb7d4fb7ff516c7698cf771f00/studio/backend/core/inference/tools.py)

## How I checked it

The regression test puts a recognizable string in the retrieval result and checks that it reaches the model input. A companion test covers explicit Off. That pair catches a tempting but incorrect fix: always searching attachments would make the first case pass while breaking the second. [Auto fallback tests](https://github.com/unslothai/unsloth/blob/f3e41f4eb6efb1bb7d4fb7ff516c7698cf771f00/studio/backend/tests/test_rag_whole_document.py) · [Off regression](https://github.com/unslothai/unsloth/blob/f3e41f4eb6efb1bb7d4fb7ff516c7698cf771f00/studio/backend/tests/test_rag_retrieval.py)

During development I also tried an over-budget attachment in the desktop app with a 12B model. Four retrieved passages reached the request, which returned HTTP 200 and a complete response. The passage count was the telling observation. A chat can return a perfectly ordinary response even when the model never sees the file. [Original validation notes](https://github.com/unslothai/unsloth/pull/9630)
