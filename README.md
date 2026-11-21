<!-- PROFILE README · Aerial field notes -->

<div align="center">
  <picture>
    <source media="(max-width: 600px)" srcset="works/hero-mission-mobile.svg" />
    <img src="works/hero-mission.svg" width="100%" alt="Wentian Shen — Aerial vision and spatial intelligence, Wuhan University" />
  </picture>
</div>

<p align="center">
  <a href="#current-build">Current build</a> &nbsp; / &nbsp;
  <a href="#recent-work">Recent work</a> &nbsp; / &nbsp;
  <a href="#selected-projects">Selected projects</a> &nbsp; / &nbsp;
  <a href="#research">Research</a> &nbsp; / &nbsp;
  <a href="mailto:Wentian_Shen@whu.edu.cn">Get in touch ↗</a>
</p>

<p align="center">
  <a href="https://github.com/wawjswt"><img src="https://img.shields.io/badge/GitHub-wawjswt-17283B?style=flat-square&amp;logo=github&amp;logoColor=white" alt="GitHub wawjswt" /></a>
  <a href="mailto:Wentian_Shen@whu.edu.cn"><img src="https://img.shields.io/badge/Email-Let%27s_talk-17283B?style=flat-square&amp;logo=minutemailer&amp;logoColor=71E8C4" alt="Email Wentian Shen" /></a>
  <img src="https://komarev.com/ghpvc/?username=wawjswt&amp;label=Profile+views&amp;style=flat-square&amp;color=397E73" alt="Profile views" />
</p>

<br/>

### Hi, I’m Wentian Shen

**将视觉智能转化为可落地的现场系统。**

I'm at **Wuhan University**, connecting computer vision, drone inspection and spatial computing to build systems that can be used in the field. Outside the lab: photography, games, music and football.

<picture>
  <source media="(max-width: 600px)" srcset="works/profile-focus-mobile.svg" />
  <img src="works/profile-focus.svg" width="100%" alt="Current focus: UAV mission systems, imagery to 3D scenes, and vision engineering with Python, PyTorch, OpenCV, Flask, MQTT and Linux" />
</picture>

<br/>

<a id="current-build"></a>

## Current build

<sub>UAV INSPECTION &nbsp; / &nbsp; SYSTEM ENGINEERING</sub>

### Smart Detection API

<picture>
  <source media="(max-width: 600px)" srcset="works/mission-feature-mobile.svg" />
  <img src="works/mission-feature.svg" width="100%" alt="Smart Detection API: collect video and telemetry, understand spatial context, confirm detections and deliver events" />
</picture>


> **Current build:** a local Flask prototype turning aerial video and drone context into a controllable inspection mission.
> 当前重点不是“跑一次检测”，而是把检测变成可追踪、可确认、可交付的任务闭环。

`Flask + Waitress` · `YOLOv5` · `RTSP / HTTP` · `DJI MQTT` · `GPS segments + Polygon ROI` · `MJPEG + event push`

**Role:** Computer vision · backend · system orchestration

<details>
<summary><b>Open the current mission loop</b></summary>

<div align="center">
  <img src="works/now-smart-detection-api.svg" width="100%" alt="Smart Detection API data-flow diagram from video and DJI telemetry through Flask orchestration, multi-model inference, spatial gating, event confirmation and delivery" />
</div>

```text
POST /detect
  → attach a video source, drone identity, target classes and optional mission segments
  → keep the stream alive with bounded reconnect attempts and exponential backoff
  → wait for GPS arrival at a segment start point
  → route detections through model-specific confidence policies
  → keep detections whose centers fall inside the active Polygon ROI
  → require four consecutive detection frames before creating an event
  → stream annotated frames, save a snapshot and optionally push business metadata
  → stop at the segment endpoint, switch flight legs or accept a stop command
```

If a stream drops, the service retries within its configured budget; once that budget is exhausted, it marks the stream as failed, releases capture resources and ends the affected task cleanly. The service also caches DJI telemetry from MQTT, exposes the latest location on demand, and supports model reload without rebuilding the whole application.
</details>

<details>
<summary><b>Explore the public route surface</b></summary>

```http
POST /detect                           # create a detection task
GET  /video_feed/<task_id>             # MJPEG result stream
GET  /api/telemetry?sn=<drone_sn>      # latest MQTT telemetry
GET  /get_latest_snapshot?task_id=<id> # latest confirmed snapshot
POST /stop_detect                      # stop task and release stream resources
POST /reload_models                    # hot reload configured models
```

Connection details and deployment configuration are omitted from this public overview.
</details>

<details>
<summary><b>Request shape (placeholder values)</b></summary>

```text
POST /detect
  rtsp_url:       <RTSP / HTTP / local video source>
  drone_sn:       <drone identifier>
  detect_classes: <configured target classes>
  segments:
    - start:      <GPS waypoint>
      stop:       <GPS waypoint>
      roi:        <normalized polygon vertices>
```
</details>

<details>
<summary><b>Watch the mission dashboard</b></summary>

<div align="center">
  <img src="works/mission-dashboard.svg" width="92%" alt="Animated mission dashboard showing RTSP, MQTT and GPS data flowing through YOLO inference to confirmed events" />
</div>

The dashboard visualizes stream input, telemetry context, spatial filtering and confirmed event delivery.
</details>

<details>
<summary><b>Explore the architecture and engineering notes</b></summary>

<div align="center">
  <img src="works/smart-detection-api.svg" width="92%" alt="Smart Detection API architecture linking video, telemetry, inference and event delivery" />
</div>

1. **Multi-segment mission:** each `segment` has independent start, stop and ROI rules; GPS position controls activation and switching.
2. **Two-layer spatial constraint:** GPS segments decide *when* to detect; polygon ROI decides *where* detections are trusted.
3. **Video + telemetry fusion:** RTSP / HTTP / local streams are linked with the latest MQTT GPS, attitude and altitude data.
4. **Policy-aware inference:** target categories can route to different YOLO models with independent confidence thresholds.
5. **Field operations:** consecutive-frame confirmation, MJPEG output, snapshots, stop control and model hot reload.
6. **Stream resilience:** failed video connections use bounded exponential-backoff retries; terminal failures release resources and close the affected task cleanly.
</details>

<br/>

<a id="recent-work"></a>

## Recent work

<sub>REMOTE SENSING &nbsp; / &nbsp; GENERATIVE 3D</sub>

> 最近在做的事情，是把“遥感影像看起来像什么”继续追问到“它能不能变成一个可分析、可对齐、可解释的 3D 场景”。

I am exploring how satellite images can guide navigable 3D scenes, and which parts of those scenes still rely on generation.

### From satellite imagery to 3D scenes

**ABot-Earth experiments**

Two contrasting scenes — water and agriculture, then a working port — reveal the same pattern: **large-scale layout is recognizable; height and hidden surfaces remain uncertain.**

<img src="works/gallery/water-scenes.svg" width="100%" alt="Water and agriculture study: original RGB satellite input beside the generated ABot-Earth 3D scene; original images shown without cropping" />

<img src="works/gallery/port-scenes.svg" width="100%" alt="Port logistics study: original satellite input beside the generated 3D port scene; original images shown without cropping" />


- **What held up:** water bodies, roads, field patterns and the port's main spatial layout.
- **What improved with finer imagery:** more visible vehicles, containers and other small objects.
- **What needs care:** building height, side surfaces and occluded areas are inferred; the scenes are for visual exploration rather than surveying.

<details>
<summary><b>Explore the experiment workflow</b></summary>

<div align="center">
  <img src="works/recent-work/recent-work-radar.svg" width="94%" alt="Research flow from satellite imagery through ABot-Earth scene generation, Gaussian inspection, spatial alignment and terrain context" />
</div>

The Gaussian inspection showed broad XY correspondence between the generated scene and its input image. For terrain grounding, a georeferenced image was used as the horizontal anchor; a terrain raster was aligned to the image grid, invalid areas were masked, and two Z constructions were compared: **terrain drape** and **terrain + relative model Z**. The outputs are useful for visualization and scene interpretation, not for publishing exact coordinates or survey accuracy.

The practical boundary is clear: **terrain data supplies ground context, not a verified DSM**. The draped version helps place a generated scene on the landscape; the relative-height version helps explore visual relief, but its Z should not be read as measured building height.
</details>

---

<a id="selected-projects"></a>

## Selected projects

<sub>A COLLECTION OF BUILDS, EXPERIMENTS &amp; VISUAL EXPLORATIONS</sub>

### YOLOv5 Drone · Aerial perception

Vehicle and fire detection experiments from an aerial viewpoint. [Explore the project →](https://github.com/wawjswt/Yolov5-Drone)

<a href="https://github.com/wawjswt/Yolov5-Drone"><img src="works/gallery/aerial-detection.svg" width="100%" alt="YOLOv5 Drone experiment gallery: vehicle and fire detections from aerial views" /></a>

<details>
<summary><b>Watch the aerial detection demo</b></summary>

<div align="center">
  <img src="works/drone.gif" width="76%" alt="Animated drone target detection demonstration" />
</div>
</details>

### Gaussian Splatting · Novel views

Exploring scene reconstruction and novel-view synthesis with [Gaussian Splatting](https://github.com/graphdeco-inria/gaussian-splatting).

<img src="works/gallery/gaussian-scenes.svg" width="100%" alt="Gaussian Splatting experiment gallery: dog and Witcher scenes, displayed in full" />

<details>
<summary><b>Watch the novel-view demo</b></summary>

<div align="center">
  <img src="works/demo.gif" width="76%" alt="Animated novel-view synthesis" />
</div>
</details>

### VGGT · Visual geometry

Learning visual geometry and scene understanding through [VGGT](https://github.com/facebookresearch/vggt).

<a href="https://github.com/facebookresearch/vggt"><img src="works/gallery/visual-geometry.svg" width="100%" alt="VGGT visual geometry experiment, shown in a framed gallery" /></a>

<br/>

## Toolkit

<sub>TOOLS BEHIND THE EXPERIMENTS</sub>

<div align="center">
  <img src="https://skillicons.dev/icons?i=python,pytorch,opencv,flask,docker,linux,git,github&perline=8&theme=dark" alt="Python, PyTorch, OpenCV, Flask, Docker, Linux, Git and GitHub" />
</div>

| Vision & AI | Mission systems | Spatial computing |
| :--- | :--- | :--- |
| YOLOv5 · PyTorch · OpenCV | Flask · MQTT · RTSP · MJPEG | Remote sensing · Photogrammetry · 3DGS |

<a id="research"></a>

## Research directions

<div align="center">
  <picture>
  <source media="(max-width: 600px)" srcset="works/research-radar-mobile.svg" />
  <img src="works/research-radar.svg" width="100%" alt="Research atlas connecting aerial AI, spatial computing, remote sensing and AI engineering; topics rather than numerical scores" />
</picture>
</div>

- **Aerial AI:** route-aware detection, UAV inspection and video-stream intelligence.
- **Spatial Computing:** visual geometry, 3D reconstruction, novel-view synthesis and scene understanding.
- **Remote Sensing:** photogrammetry, geospatial perception and image interpretation.
- **AI Engineering:** model serving, streaming, observability and controllable orchestration.

## Field notes

> I am interested in the boundary where a vision algorithm becomes a dependable system for a real mission.

<details>
<summary><b>View the research timeline</b></summary>

<div align="center">
  <img src="works/mission-timeline.svg" width="92%" alt="Animated timeline of aerial detection, Gaussian Splatting, VGGT and mission systems" />
</div>
</details>

## On GitHub

<div align="center">
  <img src="https://github-readme-stats-eight-theta.vercel.app/api?username=wawjswt&show_icons=true&theme=transparent&amp;hide_border=true&amp;title_color=71e8c4&amp;icon_color=71e8c4&amp;text_color=9aafbf&amp;bg_color=101d2d&rank_icon=github" height="170" alt="GitHub statistics" />
  <img src="https://github-readme-stats-eight-theta.vercel.app/api/top-langs/?username=wawjswt&layout=compact&theme=transparent&amp;hide_border=true&amp;title_color=71e8c4&amp;icon_color=71e8c4&amp;text_color=9aafbf&amp;bg_color=101d2d" height="170" alt="Most used languages" />
</div>

<details>
<summary><b>View activity and contribution streak</b></summary>

<div align="center">
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=wawjswt&bg_color=101d2d&amp;color=9aafbf&amp;hide_border=true&amp;area=true&amp;area_color=71e8c4&amp;line=71e8c4&amp;point=e6b975" width="96%" alt="GitHub activity graph" />
  <br/><br/>
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=wawjswt&amp;theme=transparent&amp;hide_border=true&amp;background=101D2D&amp;ring=71E8C4&amp;fire=E6B975&amp;currStreakLabel=71E8C4&amp;sideLabels=9AAFBF&amp;dates=9AAFBF" alt="GitHub contribution streak" />
</div>
</details>

<details>
<summary><b>Contribution flight path</b></summary>


<div align="center"><img src="https://raw.githubusercontent.com/wawjswt/wawjswt/output/github-contribution-grid-snake.svg" alt="Animated contribution snake" /></div>

</details>

<br/>

<a href="mailto:Wentian_Shen@whu.edu.cn"><picture>
  <source media="(max-width: 600px)" srcset="works/profile-contact-mobile.svg" />
  <img src="works/profile-contact.svg" width="100%" alt="Let's exchange ideas about computer vision, UAV inspection, remote sensing and practical AI. Email Wentian Shen." />
</picture></a>

<p align="center"><a href="mailto:Wentian_Shen@whu.edu.cn">Wentian_Shen@whu.edu.cn</a> &nbsp; · &nbsp; <a href="https://github.com/wawjswt">GitHub ↗</a></p>
