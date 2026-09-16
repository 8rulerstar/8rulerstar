## Hi, I'm 8rulerstar

I build small games and the tooling that keeps them honest — simulators and
checkers that let me verify a design decision without opening the editor.

### Projects

**[Stella Ball](https://github.com/8rulerstar/stella-ball)** · JavaScript, Canvas
A browser action-strategy prototype — roll a meteor and three starkeepers around
a top-down billiards battlefield, then choose each shot whether the starlight you
made goes into aim or into a constellation.
→ [Play on itch.io](https://8rulerstar.itch.io/stella-ball)

**[RuneCast](https://github.com/8rulerstar/RuneCast)** · Unity 6, C#
A real-time gesture auto-battler. Your heroes fight on their own; you draw runes
to intervene. Nine shapes, graded on how precisely you trace them.
→ [Play on itch.io](https://8rulerstar.itch.io/runecast)

### Open source

- [getsentry/sentry-python#7505](https://github.com/getsentry/sentry-python/pull/7505)
  — type annotations for databag limits in `serializer.py` (merged)

### How I work

I like knowing whether a change actually did anything, so most of my projects end
up with a small harness beside them.

Stella Ball has one: a headless runner that drives the game's real `update`
functions at a fixed timestep, plus 34 probe scripts. So "is stage 5 still
clearable without a weapon?" is a question I can answer in a few seconds, from the
same code the browser runs — not from a physics model I rewrote for testing and
would have to keep in sync.

The part I care about just as much is writing down what the harness *doesn't*
see. Its report says plainly that it measures outcomes — clear rate, damage,
shape recognition — and not feel, pacing or frame stability, and that its clear
rates assume a player with no weapons equipped. A number is only useful if you
know what it left out.

Always happy to chat about any of this — feel free to open an issue or say hi.
