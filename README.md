## Hi, I'm Byungkun Jang

I'm a university student in Korea. I build computer vision and machine learning
tools, and I'm especially interested in how accurate the measurements from pose
models really are.

### Projects

**[poseaudit](https://github.com/8rulerstar/poseaudit)** · Python<br>
Checks how far off the angles, tilts and lengths you read from a pose model are,
not just whether its keypoints land near the labels. On YOLO11n-pose against COCO,
58% of elbow angles are off by 15° or more when the arm segments are under 30 px,
against 26% above 60 px.<br>
→ [PyPI](https://pypi.org/project/poseaudit/)

**[Epokio](https://github.com/8rulerstar/epokio)** · Python<br>
Watches ML training runs on your machine or a remote GPU server from the macOS
menu bar, or a web page on Windows, Linux and your phone. No code changes and no
account: point it at the folder your runs already write to.<br>
→ [PyPI](https://pypi.org/project/epokio/)

### Open source

- [roboflow/supervision#2655](https://github.com/roboflow/supervision/pull/2655):
  `from_yolo` parsed whole YOLO pose label rows as polygons, giving wrong boxes.
  It now reads the box and skips the keypoints. Released in
  [0.30.8](https://github.com/roboflow/supervision/releases/tag/0.30.8).
- [sktime/sktime#11233](https://github.com/sktime/sktime/pull/11233):
  re-enabled the tests of two estimators that were skipped by mistake, a follow-up
  the maintainer suggested while reviewing my fix for the VM test path.
- [MODSetter/SurfSense#2027](https://github.com/MODSetter/SurfSense/pull/2027):
  when the last connection to a host is deleted, its network access grant is now
  withdrawn too, while hosts still shared by other connections keep theirs.

[All merged pull requests](https://github.com/search?q=is%3Apr+author%3A8rulerstar+is%3Amerged+-user%3A8rulerstar&type=pullrequests)

### How I work

I like to check whether a change did what it was meant to, on real data. poseaudit
came from that: a pose model can score a good mAP while the angles computed from
its keypoints are badly off, so it reports the error by segment size and lists the
readings it could not score.
