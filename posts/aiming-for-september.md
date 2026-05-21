I've been building Hearty quietly for a while now, and it feels like the right time to say it out loud: I am targeting a September 2026 launch on Google Play.

Hearty is a food and symptom journal built specifically for neurodivergent people. If you've tried to log your meals consistently and failed; not because you didn't care, but because the friction of opening an app, finding the right field, and typing out what you ate thirty minutes ago is just *too many steps when your brain is already taxed*; this is for you.

The core idea is simple: logging should mentally cost you nothing. Voice input, wake word activation, photo capture. You speak it, you snap it, it's logged. No forms, no friction.

## Where things stand

- Voice logging and a wake word listener are in active development
- Sync is working
- The app runs on Android

## Training "Hey Hearty"

One thing I'm especially excited about: a custom wake word. Rather than relying on a third-party voice platform, I'm training the model myself using [openWakeWord](https://github.com/dscripka/openWakeWord), an open-source wake word engine. Rather than recording my own voice, I'm using synthetic training data; the pipeline generates a wide variety of speech samples from text, which the model trains on. It keeps the app fully offline and avoids handing voice data to anyone else; which felt important given who Hearty is for.

## Building alongside others

I'm co-launching with a few independent makers from my cohort who are building tools for people that bigger companies aren't thinking about. You can read about them on the [Spotlights page](spotlights.html).

If you want to follow along or get early access, join the waitlist.

— Evan
