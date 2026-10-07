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
  read the box of YOLO pose labels instead of parsing the row as a polygon.
  Merged and credited in the [0.30.8 release notes](https://github.com/roboflow/supervision/releases/tag/0.30.8)
- [sktime/sktime#11233](https://github.com/sktime/sktime/pull/11233):
  re-enable the test suite for `SARIMAX` and `FreshPRINCE`, a follow-up the maintainer asked for.
  Listed among contributors in the [v1.2.0 release](https://github.com/sktime/sktime/releases/tag/v1.2.0)
- [mochajs/mocha#6356](https://github.com/mochajs/mocha/pull/6356):
  integration test covering `--import=tsx`
- [MODSetter/SurfSense#2027](https://github.com/MODSetter/SurfSense/pull/2027):
  withdraw a host's egress grant when its last connection is deleted.
  Credited in the [v2.1.0 release notes](https://github.com/MODSetter/SurfSense/releases/tag/v2.1.0)
- [repowise-dev/repowise#2392](https://github.com/repowise-dev/repowise/pull/2392),
  [#2391](https://github.com/repowise-dev/repowise/pull/2391):
  report an unknown `search_codebase` mode instead of coercing it; keep pathless
  symbols out of `get_answer`'s homonym union.
  Credited in the [v0.53.0 release notes](https://github.com/repowise-dev/repowise/releases/tag/v0.53.0)
- [kubernetes/website#57550](https://github.com/kubernetes/website/pull/57550),
  [#57649](https://github.com/kubernetes/website/pull/57649):
  keep Korean docs in sync with English (DNS configuration, PID limiting)
- [getsentry/sentry-python#7505](https://github.com/getsentry/sentry-python/pull/7505):
  type annotations for the serializer's databag limits.
  Credited in the [2.69.2 release notes](https://github.com/getsentry/sentry-python/releases/tag/2.69.2)
- [canonical/pycloudlib#532](https://github.com/canonical/pycloudlib/pull/532):
  resolve a mypy `call-overload` error on Azure NIC creation

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
