<!-- PROFILE README · Aerial Mission Control -->

<div align="center">
  <img src="works/hero-mission.svg" width="100%" alt="Aerial Mission Control header for Wentian Shen" />
</div>

<div align="center">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&weight=600&size=21&pause=1200&color=22D3EE&center=true&vCenter=true&width=760&lines=Turning+visual+intelligence+into+field-ready+systems.;Computer+Vision+%7C+UAV+Inspection+%7C+Spatial+AI+%7C+Deployment" alt="Typing introduction" />
</div>

<div align="center">
  <a href="https://github.com/wawjswt"><img src="https://img.shields.io/badge/GitHub-wawjswt-0F172A?style=for-the-badge&logo=github&logoColor=white" alt="GitHub wawjswt" /></a>
  <a href="mailto:Wentian_Shen@whu.edu.cn"><img src="https://img.shields.io/badge/CONTACT-EMAIL-06B6D4?style=for-the-badge&logo=minutemailer&logoColor=white" alt="Email Wentian Shen" /></a>
  <img src="https://komarev.com/ghpvc/?username=wawjswt&label=MISSION+VISITS&style=for-the-badge&color=0EA5E9" alt="Profile views" />
</div>

<div align="center">
  <a href="#now--smart-detection-api">NOW</a> ·
  <a href="#-recent-work">RECENT WORK</a> ·
  <a href="#-mission-archives">MISSION ARCHIVES</a> ·
  <a href="#-research-radar">RESEARCH RADAR</a> ·
  <a href="#-github-telemetry">GITHUB TELEMETRY</a>
</div>

---

## 🛸 About

> **将视觉智能转化为可落地的现场系统。**

I'm Wentian Shen at Wuhan University. I connect computer vision, drone inspection and spatial computing to build systems that can be used in the field.

| 🎓 Based at | 🛰️ Building | 🔭 Exploring |
| :-- | :-- | :-- |
| WHU · Wuhan, China | UAV vision and mission systems | Remote sensing · 3D scenes · visual geometry |

Outside the lab: photography, games, music and football.

## NOW // Smart Detection API

<div align="center">
  <img src="works/now-smart-detection-api.svg" width="100%" alt="Smart Detection API data-flow diagram from video and DJI telemetry through Flask orchestration, multi-model inference, spatial gating, event confirmation and delivery" />
</div>

> **Current build:** a local Flask prototype turning aerial video and drone context into a controllable inspection mission.
> 当前重点不是“跑一次检测”，而是把检测变成可追踪、可确认、可交付的任务闭环。

`Flask + Waitress` · `YOLOv5` · `RTSP / HTTP` · `DJI MQTT` · `GPS segments + Polygon ROI` · `MJPEG + event push`

<details>
<summary><b>Open the current mission loop</b></summary>

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

## 🛰️ Recent Work

> 最近在做的事情，是把“遥感影像看起来像什么”继续追问到“它能不能变成一个可分析、可对齐、可解释的 3D 场景”。

I am exploring how satellite images can guide navigable 3D scenes, and which parts of those scenes still rely on generation.

### RECENT // ABot-Earth Remote Sensing → 3D Scenes

Two contrasting scenes — water and agriculture, then a working port — reveal the same pattern: **large-scale layout is recognizable; height and hidden surfaces remain uncertain.**

<table>
  <tr>
    <td width="50%" valign="top">
      <img src="works/recent-work/water-input.jpg" width="100%" alt="Dark RGB satellite image of a water and agriculture landscape with reflective ponds" />
      <p align="center"><sub><b>INPUT / WATER–AGRICULTURE</b><br/>RGB scene · dense ponds and field parcels</sub></p>
    </td>
    <td width="50%" valign="top">
      <img src="works/recent-work/water-3d-scene.jpg" width="100%" alt="ABot-Earth generated 3D scene preserving ponds, fields, vegetation and the main road" />
      <p align="center"><sub><b>OUTPUT / SCENE SYNTHESIS</b><br/>water semantics and the main road preserved; details regularized</sub></p>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <img src="works/recent-work/port-input.jpg" width="100%" alt="High-resolution RGB satellite image of a port, container yard and urban road network" />
      <p align="center"><sub><b>INPUT / PORT LOGISTICS</b><br/>fine-resolution RGB scene · port, containers and roads</sub></p>
    </td>
    <td width="50%" valign="top">
      <img src="works/recent-work/port-3d-scene.jpg" width="100%" alt="ABot-Earth generated 3D port scene with water, containers, vehicles and roads" />
      <p align="center"><sub><b>OUTPUT / HIGH-RESOLUTION DETAIL</b><br/>richer small-target expression; oblique views expose height artifacts</sub></p>
    </td>
  </tr>
</table>

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

## 🚀 Mission Archives

### MISSION 01 // Smart Detection API

> **An engineering prototype for UAV inspection workflows.**
> 它将视频流、飞行轨迹、电子围栏、模型策略与实时反馈组织成可观测的任务闭环。

- **Role:** Computer vision · backend · system orchestration
- **Stack:** Flask · YOLOv5 / PyTorch · OpenCV · MQTT · Waitress

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

### MISSION 02 // YOLOv5 Drone

Vehicle and fire detection experiments from an aerial viewpoint. [Explore the project →](https://github.com/wawjswt/Yolov5-Drone)

<div align="center">
  <a href="https://github.com/wawjswt/Yolov5-Drone"><img src="works/yolo-car.jpg" width="47%" alt="Vehicle detection from an aerial view" /></a>
  <a href="https://github.com/wawjswt/Yolov5-Drone"><img src="works/yolo-fire.jpg" width="47%" alt="Fire detection demo" /></a>
</div>

<details>
<summary><b>Watch the aerial detection demo</b></summary>

<div align="center">
  <img src="works/drone.gif" width="76%" alt="Animated drone target detection demonstration" />
</div>
</details>

### MISSION 03 // Gaussian Splatting

Exploring scene reconstruction and novel-view synthesis with [Gaussian Splatting](https://github.com/graphdeco-inria/gaussian-splatting).

<div align="center">
  <img src="works/dog.png" width="47%" alt="Gaussian Splatting dog scene" />
  <img src="works/witcher.png" width="47%" alt="Gaussian Splatting Witcher scene" />
</div>

<details>
<summary><b>Watch the novel-view demo</b></summary>

<div align="center">
  <img src="works/demo.gif" width="76%" alt="Animated novel-view synthesis" />
</div>
</details>

### MISSION 04 // VGGT

Learning visual geometry and scene understanding through [VGGT](https://github.com/facebookresearch/vggt).

<div align="center">
  <img src="works/vggt.png" width="64%" alt="VGGT visual geometry demonstration" />
</div>

## 🧭 Operational Toolkit

<div align="center">
  <img src="https://skillicons.dev/icons?i=python,pytorch,opencv,flask,docker,linux,git,github&perline=8&theme=dark" alt="Python, PyTorch, OpenCV, Flask, Docker, Linux, Git and GitHub" />
</div>

- **Vision & AI:** YOLOv5 · PyTorch · OpenCV
- **Mission systems:** Flask · MQTT · RTSP · MJPEG
- **Spatial computing:** Remote sensing · Photogrammetry · 3DGS

## 🔭 Research Radar

<div align="center">
  <img src="works/research-radar.svg" width="92%" alt="Animated radar of aerial vision, spatial AI, 3D geometry and remote sensing research directions" />
</div>

- **Aerial AI:** route-aware detection, UAV inspection and video-stream intelligence.
- **Spatial Computing:** visual geometry, 3D reconstruction, novel-view synthesis and scene understanding.
- **Remote Sensing:** photogrammetry, geospatial perception and image interpretation.
- **AI Engineering:** model serving, streaming, observability and controllable orchestration.

## 🗺️ Flight Log

> I am interested in the boundary where a vision algorithm becomes a dependable system for a real mission.

<details>
<summary><b>View the research timeline</b></summary>

<div align="center">
  <img src="works/mission-timeline.svg" width="92%" alt="Animated timeline of aerial detection, Gaussian Splatting, VGGT and mission systems" />
</div>
</details>

## 📡 GitHub Telemetry

<div align="center">
  <img src="https://github-readme-stats-eight-theta.vercel.app/api?username=wawjswt&show_icons=true&theme=tokyonight&hide_border=true&rank_icon=github" height="170" alt="GitHub statistics" />
  <img src="https://github-readme-stats-eight-theta.vercel.app/api/top-langs/?username=wawjswt&layout=compact&theme=tokyonight&hide_border=true" height="170" alt="Most used languages" />
</div>

<details>
<summary><b>View activity and contribution streak</b></summary>

<div align="center">
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=wawjswt&theme=tokyo-night&hide_border=true&area=true&area_color=22D3EE&line=22D3EE&point=8B5CF6" width="96%" alt="GitHub activity graph" />
  <br/><br/>
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=wawjswt&theme=tokyonight&hide_border=true&background=00000000&ring=22D3EE&fire=8B5CF6&currStreakLabel=E6F7FF" alt="GitHub contribution streak" />
</div>
</details>

## 🐍 Contribution Flight Path

<div align="center"><img src="https://raw.githubusercontent.com/wawjswt/wawjswt/output/github-contribution-grid-snake.svg" alt="Animated contribution snake" /></div>

---

<div align="center">
  <h3>OPEN FREQUENCY</h3>
  <p>Open to exchanging ideas about computer vision, UAV inspection, remote sensing and practical AI systems.</p>
  <a href="mailto:Wentian_Shen@whu.edu.cn">📮 Contact mission control</a>
  <br/><br/>
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:07142B,45:123C63,100:7C3AED&height=110&section=footer" alt="Footer wave" />
</div>
