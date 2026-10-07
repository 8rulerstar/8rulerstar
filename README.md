## Hi, I'm Byungkun Jang

I build computer vision and machine learning tools, and the checks that show
whether they actually work: audits that reveal what a model's headline score
leaves out, and harnesses that test a change against the real code path.

### Projects

**[poseaudit](https://github.com/8rulerstar/poseaudit)** · Python<br>
Checks how far off the angles, tilts and lengths you read from a pose model are,
not just whether its keypoints land near the labels. On YOLO11n-pose against COCO,
small arms get far worse elbow angles than large ones, which a good mAP hides.<br>
→ [PyPI](https://pypi.org/project/poseaudit/)

**[Epokio](https://github.com/8rulerstar/epokio)** · Python<br>
Watches ML training runs on your machine or a remote GPU server from the macOS
menu bar, or a web page on Windows, Linux and your phone. No code changes and no
account: point it at the folder your runs already write to.<br>
→ [PyPI](https://pypi.org/project/epokio/)

Also: [Stella Ball](https://github.com/8rulerstar/stella-ball), a small browser game
prototype ([play on itch.io](https://8rulerstar.itch.io/stella-ball)).

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

I like knowing whether a change actually did anything, and what a number leaves
out. poseaudit comes from that: a pose model can score a good mAP while the angles
you compute from its keypoints are badly off, so it measures how far, by segment
size, and says which readings it could not score.

The same habit shows up elsewhere. Stella Ball has a headless runner that drives
the game's real update loop, so a design question gets answered from the code the
browser runs, with its report stating what it does not measure.

Always happy to chat about any of this. Feel free to open an issue or say hi.
