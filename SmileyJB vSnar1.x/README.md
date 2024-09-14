# SmileyJB vSnar1.x

Went over SmileyJB with a fine-toothed comb, fixing errors and de-slopping the hell out of it. I did this on GitHub so you can view diffs of the changes via the commits pretty easily. Here's a summary:

+ Significant changes to response formatting and examples given to the AI for this purpose
  + _See below
+ Decoupled the opening prompt from Main Prompt so that Main Prompt can be used as an anchor you can place anywhere you'd like
  + _Useful for SillyTavern features that attach to the Main Prompt or override it_
+ For GPT, added a penultimate prompt gaslight prompt & a closing guidance prompt
  + _The gaslight prompt was inspired by k0lache's pancatb3ta_
  + _The closing guidance prompt is the Claude prefill but set as a system prompt_
+ Added an instruction to prefer action beats over dialogue tags
+ Added an in-chat depth 0 prompt for randomized writers and a reminder to use action beats over dialogue tags
  + _Randomized writer list blatantly stolen from ashtrayii_
+ Made the way bulleted lists were done consistent throughout the jailbreak
+ Made the way non-dialogue quotes were done consistent throughout the jailbreak
+ Made the way references to XML-style tags consistent throughout the jailbreak
+ Altered First Person POV prompt
+ Altered Lewd Language to be more permissive and a little less cringe
  + _I also renamed it to Lewd Lingo for no particularly good reason_
+ Removed duplicate lines in the `👀` (POV) prompts
+ Removed unnecessary newlines here and there that seemed to be there for no reason
+ Fixed comments that weren't correctly commented out, and also added `{{trim}}` after them to prevent an extra newline
+ Fixed various misspellings
+ Other shit I don't remember

There's also a gpt-4o logit bias I recommend importing and using, which helps kill a ton of AO3-isms.

## Formatting

This notably does NOT do the fucking asterisks around all actions/narrative style because:
1. Its training data associates this with much poorer quality writing
1. It's token pollution that will often lead to formatting errors
1. It's unnecessary in the first place
1. Fuck you

The AI is now instructed to put subquotes inside of `‘smart-apostrophes’`, sound effects inside of `*single-asterisks*`, and thoughts inside of `_underscores_`.

Previously, thoughts were enclosed in <code>`backticks`</code>, but as backticks are used to refer the AI to the XML-style instruction set tags, I felt this was necessary.

Does the AI always get the formatting correct? ***No.*** Is the prose improved overall? ***Yes.***

## Advanced

In the Advanced version, `{{char}}` & `{{user}}` are replaced with `{{getvar::_SMILEY-tgtChar}}` & `{{getvar::_SMILEY-notThem}}`

Should you switch which one is which, it'd be as if the persona was the card and the card was the persona.

This is particularly useful for Impersonate, though it's recommended to use a QR (Quick Reply) to speed things up.

Even on Claude, which has an Assistant Impersonation Prefill, it's beneficial to do this.

Aside from Impersonate, being able to control how the characters are handled by the prompts like this can potentially allow you to better control an NPC for a time.

Note that, in the Advanced version, Claude's Assistant Prefill and Assistant Impersonation Prefill are the same. However, there's a copy of the Assistant Impersonation Prefill (with {char} & {user} swapped out) toward the bottom of the Prompt Manager, should you require it or just want to see what the difference was.