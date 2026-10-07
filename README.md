## Hi, I'm 8rulerstar

I build small games and the tooling that keeps them honest: simulators and
checkers that let me verify a design decision without opening the editor.

### Projects

**[Stella Ball](https://github.com/8rulerstar/stella-ball)** · JavaScript, Canvas
A browser action-strategy prototype. Roll a meteor and three starkeepers around
a top-down billiards battlefield, then choose each shot whether the starlight you
made goes into aim or into a constellation.
→ [Play on itch.io](https://8rulerstar.itch.io/stella-ball)

**[poseaudit](https://github.com/8rulerstar/poseaudit)** · Python
Checks how far off the angles, tilts and lengths you read from a pose model are,
not just whether its keypoints land near the labels. On YOLO11n-pose against COCO,
small arms get far worse elbow angles than large ones, which a good mAP hides.
→ [PyPI](https://pypi.org/project/poseaudit/)

### Open source

- [roboflow/supervision#2655](https://github.com/roboflow/supervision/pull/2655):
  `from_yolo` parsed whole YOLO pose label rows as polygons, giving wrong boxes.
  It now reads the box and skips the keypoints. Shipped with its own section in
  the [0.30.8 release notes](https://github.com/roboflow/supervision/releases/tag/0.30.8).
- [sktime/sktime#11233](https://github.com/sktime/sktime/pull/11233):
  re-enabled the tests of two estimators that were skipped by mistake, a follow-up
  the maintainer asked for while reviewing my fix for the VM test path.
- [repowise-dev/repowise#2392](https://github.com/repowise-dev/repowise/pull/2392):
  report an unknown search mode instead of silently coercing it. My review of a
  competing PR showed it would break existing calls, and the maintainer merged this one.

[All merged pull requests](https://github.com/search?q=is%3Apr+author%3A8rulerstar+is%3Amerged&type=pullrequests)

### How I work

I like knowing whether a change actually did anything, so most of my projects end
up with a small harness beside them.

Stella Ball has one: a headless runner that drives the game's real `update`
functions at a fixed timestep, plus 34 probe scripts. So "is stage 5 still
clearable without a weapon?" is a question I can answer in a few seconds, from the
same code the browser runs, not from a physics model I rewrote for testing and
would have to keep in sync.

The part I care about just as much is writing down what the harness *doesn't*
see. Its report says plainly that it measures outcomes (clear rate, damage,
shape recognition) and not feel, pacing or frame stability, and that its clear
rates assume a player with no weapons equipped. A number is only useful if you
know what it left out.

Always happy to chat about any of this. Feel free to open an issue or say hi.
