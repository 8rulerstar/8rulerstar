## Hi there, I'm Byungkun Jang 👋

Thanks for dropping by! I'm based in Korea and build computer vision and machine learning
tools, and I'm especially interested in how much you can trust the measurements
taken from pose estimation models. I also like making games.

한국에서 컴퓨터 비전과 머신러닝 도구를 만듭니다. 특히 포즈 추정 모델의 측정값을 얼마나 믿을 수 있는지에 관심이 많고, 게임 만들기도 좋아합니다.

### Highlights: pose estimation evaluation

**Ultralytics (YOLO)** · [ultralytics/ultralytics#26564](https://github.com/ultralytics/ultralytics/pull/26564)<br>
Found why YOLO pose validation scored COCO-converted data far below pycocotools: people
with no labelled keypoints were counted as targets. I reproduced it on a 200-image COCO
val2017 sample ([#26563](https://github.com/ultralytics/ultralytics/issues/26563)) and
proposed an ignore rule in the validator; the maintainers replaced it with a one-line fix
at the source, in `convert_coco`. On that sample, pose mAP50-95 for yolo26n-pose goes from
0.347 to 0.576, matching pycocotools. One of the key changes in [8.4.175](https://github.com/ultralytics/ultralytics/releases/tag/v8.4.175).

**supervision (Roboflow)** · [roboflow/supervision#2687](https://github.com/roboflow/supervision/pull/2687)<br>
Added `sv.metrics.KeyPointMeanAveragePrecision`, the first pose metric in supervision:
COCO keypoint mAP using Object Keypoint Similarity for `sv.KeyPoints`, ported from
pycocotools. Its AP, AP50, AP75, APm and APl match pycocotools to within 3e-9 on 200 COCO
val2017 images and 1.4e-8 on synthetic tests. The maintainer refined it before release,
and it shipped in [supervision 0.31.0](https://github.com/roboflow/supervision/releases/tag/0.31.0) as one of the release's headline features.
Before that I fixed `from_yolo` reading pose labels as polygons
([#2655](https://github.com/roboflow/supervision/pull/2655), extended by the maintainers
and featured in the [0.30.8 release highlights](https://github.com/roboflow/supervision/releases/tag/0.30.8)).

### Projects

**[poseaudit](https://github.com/8rulerstar/poseaudit)** · Python<br>
Measures how far angles, tilts and lengths derived from pose keypoints disagree
with the labels, not just whether the keypoints land near them, the way a measuring
device is validated: bias, limits of agreement, ICC and intervals resampled by image
or subject, from COCO, YOLO or supervision output. With YOLO11n-pose on 322 elbows
from 200 COCO val2017 images, 58% of angles disagree with COCO's labels by 15° or
more when the arm segments average under 30 px (37% at 30 to 60 px, 26% above
60 px). Some of that is COCO's own annotators disagreeing; how much, the labels
alone cannot tell.<br>
[PyPI →](https://pypi.org/project/poseaudit/)

<p><img src="assets/poseaudit.gif" width="560" alt="poseaudit: COCO label and yolo11n-pose elbow angles on three photos, then the share of elbows off by 15° or more by arm size">
<br><sub>Photos: COCO val2017, CC BY 4.0</sub></p>

**[Epokio](https://github.com/8rulerstar/epokio)** · Python<br>
Sends a phone alert when an ML training run on your machine or a GPU server stalls,
hits NaN or finishes. It reads the logs your runs already write (Ultralytics, Hugging Face,
Lightning, Keras, TensorBoard), with no code changes and no account. Web page, terminal
view and a macOS menu bar app.<br>
[PyPI →](https://pypi.org/project/epokio/)

<p><img src="assets/epokio.gif" width="560" alt="Epokio: a training run stalls, the web page marks it Stalled and the phone gets an alert"></p>

<table>
<tr>
<td width="50%" valign="top">
<b><a href="https://github.com/8rulerstar/lidtilt">lidtilt</a></b> · Python<br>
Reads the MacBook lid angle sensor to remove the lid's tilt from webcam head pitch.<br><br>
<img src="assets/lidtilt.gif" width="100%" alt="lidtilt: as the lid moves, raw head pitch follows it while the corrected pitch stays flat">
</td>
<td width="50%" valign="top">
<b><a href="https://github.com/8rulerstar/stella-ball">Stella Ball</a></b> · browser game<br>
A small browser game. <a href="https://8rulerstar.itch.io/stella-ball">Play on itch.io →</a><br><br>
<img src="assets/stella-ball.gif" width="100%" alt="Stella Ball gameplay: a shot chains through the party and defeats the boss">
</td>
</tr>
</table>

### More open source

- [ultralytics/ultralytics#26651](https://github.com/ultralytics/ultralytics/pull/26651):
  SAM prompts given for a folder or video reached only the first image, and later frames
  fell back to segmenting everything. Prompts now apply to the whole source without
  modifying the caller's arrays; the maintainers moved the forwarding to the streaming
  entry point before merging. It leads the [8.4.177 release notes](https://github.com/ultralytics/ultralytics/releases/tag/v8.4.177).
- [ultralytics/ultralytics#26635](https://github.com/ultralytics/ultralytics/pull/26635):
  Since a 2025 change, every DataLoader worker drew the same Albumentations augmentations,
  so training saw roughly 1/workers as many distinct draws. Each worker now seeds them
  from its own seed ([#26634](https://github.com/ultralytics/ultralytics/issues/26634));
  shipped in [8.4.176](https://github.com/ultralytics/ultralytics/releases/tag/v8.4.176).
- [MODSetter/SurfSense#2027](https://github.com/MODSetter/SurfSense/pull/2027) and
  [#2061](https://github.com/MODSetter/SurfSense/pull/2061): closed two security-labelled
  gaps in the desktop app's network permissions. Deleting a host's last connection left
  that host allowed ([#1956](https://github.com/MODSetter/SurfSense/issues/1956)), and old
  model-download grants were not carried over to the new per-host permission
  ([#1957](https://github.com/MODSetter/SurfSense/issues/1957)); the migration never
  overwrites an answer the user gave later. Shipped in
  [v2.1.0](https://github.com/MODSetter/SurfSense/releases/tag/v2.1.0) and
  [v2.2.0](https://github.com/MODSetter/SurfSense/releases/tag/v2.2.0).
- [MobiFlight/MobiFlight-Connector#3385](https://github.com/MobiFlight/MobiFlight-Connector/pull/3385):
  a log-level filter for the app's log panel, built after the maintainer's design review
  as a filter component the config list now shares; in the
  [11.3.1.1 beta](https://github.com/MobiFlight/MobiFlight-Connector/releases/tag/11.3.1.1).
- [sktime/sktime#11233](https://github.com/sktime/sktime/pull/11233):
  Re-enabled tests for two estimators that were skipped by mistake, a follow-up the
  maintainer requested while reviewing my other (still open) PR.
- [morluto/rea#3079](https://github.com/morluto/rea/pull/3079):
  Comparing two .NET assemblies paired same-named nested types from different
  enclosing types, so real changes were reported as unchanged. Members are now
  paired by their enclosing types; the maintainers extended the fix before merging.

[See all merged pull requests →](https://github.com/search?q=is%3Apr+author%3A8rulerstar+is%3Amerged+-user%3A8rulerstar&type=pullrequests)

If you're working on pose estimation, building games, or just want to talk about
either, I'd love to hear from you. Questions and feedback are always welcome.

**Contact**: bkbkjang@gmail.com
