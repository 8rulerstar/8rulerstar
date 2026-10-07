## Hi, I'm Byungkun Jang

Thank you for stopping by. I'm a university student in Korea. I build computer
vision and machine learning tools, and I'm especially interested in how accurate
the measurements from pose models really are.

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
  the maintainer suggested while reviewing my fix for the VM test path.
- [MODSetter/SurfSense#2027](https://github.com/MODSetter/SurfSense/pull/2027):
  when the last connection to a host is deleted, its network access grant is now
  withdrawn too, while hosts still shared by other connections keep theirs.

[All merged pull requests](https://github.com/search?q=is%3Apr+author%3A8rulerstar+is%3Amerged&type=pullrequests)

### How I work

I care about knowing whether a change actually did anything, and what a number
might leave out. poseaudit comes from that: a pose model can score a good mAP while the angles
you compute from its keypoints are badly off, so it measures how far, by segment
size, and says which readings it could not score.

The same habit shows up elsewhere. Stella Ball has a headless runner that drives
the game's real update loop, so a design question gets answered from the code the
browser runs, with its report stating what it does not measure.

If any of this is useful to you, I would be glad to hear from you. Questions,
feedback and corrections are always welcome through issues.
