The hardest part of building an AI-powered app isn't getting the AI to do something impressive. It's getting it to stop doing things you didn't ask for.

This week I fixed two bugs that had been quietly making Hearty feel unreliable. Neither of them was dramatic. Both of them mattered.

## The symptom contamination problem

Hearty's voice loop is conversational. You say what you ate, it logs the meal, and then it checks in: *how are you feeling?* The idea is to capture symptoms close to the time they happen, in a low-friction way.

What was actually happening: when you answered that follow-up — "I'm feeling a bit gassy" — the AI was treating your response as part of the meal log. So "gassy" was getting merged into the meal description. You'd look at your log later and see something like "Quest protein bar, gassy, slight bloating" stored as the food entry.

The fix was to change the order of operations on every follow-up turn. Extract symptoms first. If symptoms are found, log them and stop — don't touch the meal at all. The two pieces of information are separate things and needed to be handled separately. Now a symptom report stays a symptom report, and the meal entry stays clean.

## The AI that wouldn't take yes for an answer

The second bug was more subtle. Hearty asks *how are you feeling?* once after you log a meal. But it was asking again. And again. Even after you'd answered.

The model was ignoring its own conversation history. Each turn it would re-evaluate whether to ask the wellbeing question, conclude that it hadn't been answered yet (incorrectly), and ask again. It felt like talking to someone who wasn't listening.

The fix was to be more explicit in the system prompt: if the conversation history already contains an answer to that question, don't ask it. The AI is capable of following that instruction — it just needed to be given it.

## Why this kind of thing is hard to catch

Both bugs were invisible during happy-path testing. If you said what you ate, answered how you felt, and moved on — everything looked fine. They only showed up when you started having actual multi-turn conversations with the app. Symptom follow-ups, clarifying questions, going back and forth.

That's also the part of Hearty I care most about. The whole premise is that the AI can have a real conversation with you about how food is affecting your body — not just transcribe a food diary. For that to work, the conversation has to actually hold together.

It does now, at least in these two cases. There are probably more edges to find. I'll keep looking.

If you want to hear when Hearty launches on Google Play, join the waitlist.
