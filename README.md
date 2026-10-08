## Hi there, I'm Byungkun Jang 👋

Thanks for dropping by! I'm based in Korea and build computer vision and machine learning
tools, and I'm especially interested in how much you can trust the measurements
taken from pose estimation models. I also like making games.

한국에서 컴퓨터 비전과 머신러닝 도구를 만듭니다. 특히 포즈 추정 모델의 측정값을 얼마나 믿을 수 있는지에 관심이 많고, 게임 만들기도 좋아합니다.

### Projects

**[poseaudit](https://github.com/8rulerstar/poseaudit)** · Python<br>
Measures how far angles, tilts and lengths derived from pose keypoints disagree
with the labels, not just whether the keypoints land near them. With YOLO11n-pose
on 322 elbows from 200 COCO val2017 images, 58% of angles disagree with
COCO's labels by 15° or more when the arm segments average under 30 px (37% at
30 to 60 px, 26% above 60 px). Part of that is the labels' own noise.<br>
[PyPI →](https://pypi.org/project/poseaudit/)

**[Epokio](https://github.com/8rulerstar/epokio)** · Python<br>
Watches ML training runs on your machine or a remote GPU server from the macOS
menu bar, or from a browser on Windows, Linux or your phone. No code changes and no
account: point it at the folder your runs already write to.<br>
[PyPI →](https://pypi.org/project/epokio/)

(Also a small browser game: [Stella Ball](https://github.com/8rulerstar/stella-ball),
[Play on itch.io](https://8rulerstar.itch.io/stella-ball).)

### Open source

- [ultralytics/ultralytics#26564](https://github.com/ultralytics/ultralytics/pull/26564):
  `convert_coco(use_keypoints=True)` kept people with no labelled keypoints, so pose
  validation counted them as targets. On a 200-image COCO val2017 sample, pose mAP50-95
  for yolo26n-pose goes from 0.347 to 0.576, matching pycocotools. I found and reproduced
  it in [#26563](https://github.com/ultralytics/ultralytics/issues/26563); the maintainer
  merged it as a smaller fix at the source.
- [roboflow/supervision#2655](https://github.com/roboflow/supervision/pull/2655):
  `from_yolo` parsed whole YOLO pose label rows as polygons, giving wrong boxes.
  It now reads the box and skips the keypoints. Released in
  [0.30.8](https://github.com/roboflow/supervision/releases/tag/0.30.8).
- [sktime/sktime#11233](https://github.com/sktime/sktime/pull/11233):
  Re-enabled tests for two estimators that were skipped by mistake, a follow-up the
  maintainer requested while reviewing my other (still open) PR.
- [MODSetter/SurfSense#2027](https://github.com/MODSetter/SurfSense/pull/2027):
  Deleting the last connection to a host now also revokes its network access.
  Hosts still used by other connections keep it.

[See all merged pull requests →](https://github.com/search?q=is%3Apr+author%3A8rulerstar+is%3Amerged+-user%3A8rulerstar&type=pullrequests)

If you're working on pose estimation, building games, or just want to talk about
either, I'd love to hear from you. Questions and feedback are always welcome.

**Contact**: bkbkjang@gmail.com
