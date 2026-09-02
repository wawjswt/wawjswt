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
  <a href="#-mission-archives">MISSION ARCHIVES</a> ·
  <a href="#-research-radar">RESEARCH RADAR</a> ·
  <a href="#-github-telemetry">GITHUB TELEMETRY</a>
</div>

---

## 🛸 Identity Cockpit

> **将视觉智能转化为可落地的现场系统。**
> I build the path from computer-vision models to observable, controllable and deployable UAV workflows.

| Signal | Current Readout | Signal | Current Readout |
| :-- | :-- | :-- | :-- |
| 🎓 BASE | WHU · Wuhan, China | 🟢 MODE | Building in public |
| 🛰️ DOMAIN | UAV inspection | 🧠 TRACK | Computer vision + spatial AI |
| ⚙️ BUILD | Model → mission system | 🔭 NEXT | 3D reconstruction + VGGT |

- **Current focus:** drone inspection, real-time detection, telemetry fusion and spatial understanding.
- **What I build:** systems connecting model inference, video streams, GPS, MQTT and task orchestration.
- **Beyond code:** photography, games, music and football.
- **Contact:** [Wentian_Shen@whu.edu.cn](mailto:Wentian_Shen@whu.edu.cn)

## NOW // Smart Detection API

<div align="center">
  <img src="works/now-smart-detection-api.svg" width="100%" alt="Animated Smart Detection API flow from video and DJI telemetry through multi-model inference, spatial filters, frame confirmation and event delivery" />
</div>

> **Current build:** a local Flask prototype turning aerial video and drone context into a controllable inspection mission.
> 当前重点不是“跑一次检测”，而是把检测变成可追踪、可确认、可交付的任务闭环。

| Current signal | Readout | Current signal | Readout |
| :-- | :-- | :-- | :-- |
| 🟢 RUNTIME | Flask + Waitress | 🛰️ INPUT | RTSP · HTTP · local file |
| 🧠 INFERENCE | Multi-model YOLOv5 | 📡 CONTEXT | MQTT GPS · altitude · attitude |
| 🗺️ CONTROL | GPS segments + Polygon ROI | ✅ RELIABILITY | 4-frame confirmation |
| 📤 DELIVERY | MJPEG · snapshots · event push | 🔧 OPERATIONS | stop · hot reload · bounded queue |

<details>
<summary><b>Open the current mission loop</b></summary>

```text
POST /detect
  → attach a video source, drone identity, target classes and optional mission segments
  → wait for GPS arrival at a segment start point
  → route detections through model-specific confidence policies
  → keep detections whose centers fall inside the active Polygon ROI
  → require four consecutive detection frames before creating an event
  → stream annotated frames, save a snapshot and optionally push business metadata
  → stop at the segment endpoint, switch flight legs or accept a stop command
```

The service also caches DJI telemetry from MQTT, exposes the latest location on demand, and supports model reload without rebuilding the whole application.
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

The public showcase intentionally describes the architecture only. Connection credentials, internal service addresses and deployment-specific configuration stay outside this profile README.
</details>

<details>
<summary><b>Sanitized task request</b></summary>

```json
{
  "rtsp_url": "rtsp://camera-or-drone-stream/live",
  "drone_sn": "DRONE-SN-PLACEHOLDER",
  "detect_classes": [0, 1, 3, 4],
  "conf_thres_drone": 0.52,
  "conf_thres_ent": 0.75,
  "segments": [
    {
      "start": [START_LAT, START_LON],
      "stop": [STOP_LAT, STOP_LON],
      "roi": [0.08, 0.18, 0.92, 0.18, 0.96, 0.88, 0.12, 0.88]
    }
  ]
}
```
</details>

## 🟢 Live Mission Dashboard

<div align="center">
  <img src="works/mission-dashboard.svg" width="100%" alt="Animated mission dashboard showing RTSP, MQTT and GPS data flowing through YOLO inference to confirmed events" />
</div>

| System | Status | Operational role |
| :-- | :--: | :-- |
| Video inference | 🟢 ONLINE | RTSP / HTTP / local stream processing |
| UAV telemetry | 🟢 LINKED | MQTT GPS, attitude and altitude context |
| Spatial control | 🟣 ACTIVE | GPS segments and polygon ROI |
| Event reliability | 🟡 VERIFYING | Consecutive-frame confirmation |
| Model deployment | 🟢 BUILDING | Serving, hot reload and field iteration |

## 🧭 Operational Toolkit

<div align="center">
  <img src="https://skillicons.dev/icons?i=python,pytorch,tensorflow,opencv,flask,fastapi,docker,linux,bash,git,github,cpp,js,html,css,react,vue,anaconda,vscode,figma&perline=10&theme=dark" alt="Technology stack" />
</div>

| Vision & AI | Mission & Backend | Spatial Computing | Engineering |
| :-- | :-- | :-- | :-- |
| YOLOv5 · PyTorch · OpenCV | Flask · MQTT · RTSP · MJPEG | Remote Sensing · Photogrammetry · 3DGS | Docker · Git · Linux · C++ |

---

## 🚀 Mission Archives

### MISSION 01 // Smart Detection API

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=rect&color=0:0B1220,45:123C63,100:3B1D72&height=108&text=SMART%20DETECTION%20API&fontSize=32&fontColor=E6F7FF&desc=VISION%20%C2%B7%20TELEMETRY%20%C2%B7%20MISSION%20ORCHESTRATION&descAlignY=73&descSize=15" width="100%" alt="Smart Detection API title" />
  <br/><br/>
  <img src="works/smart-detection-api.svg" width="96%" alt="Smart Detection API architecture" />
</div>

> **An engineering prototype for UAV inspection workflows.**
> 它将视频流、飞行轨迹、电子围栏、模型策略与实时反馈组织成可观测的任务闭环。

| Mission field | Readout |
| :-- | :-- |
| STATUS | 🟢 Active development |
| TYPE | UAV inspection / surveillance |
| CORE LOOP | Video → Inference → Telemetry → Decision |
| ROLE | Computer vision · backend · system orchestration |
| STACK | Flask · YOLOv5 / PyTorch · OpenCV · MQTT · Waitress |

#### Interface highlights

1. **Multi-segment mission:** each `segment` has independent start, stop and ROI rules; GPS position controls activation and switching.
2. **Two-layer spatial constraint:** GPS segments decide *when* to detect; polygon ROI decides *where* detections are trusted.
3. **Video + telemetry fusion:** RTSP / HTTP / local streams are linked with the latest MQTT GPS, attitude and altitude data.
4. **Policy-aware inference:** target categories can route to different YOLO models with independent confidence thresholds.
5. **Field operations:** consecutive-frame confirmation, MJPEG output, snapshots, stop control and model hot reload.

#### Mission flow

```text
Create task → enter GPS segment → activate inference → apply Polygon ROI
        → confirm across frames → save snapshot / deliver event
        → reach stop point → switch to next flight leg
```

#### API surface

```http
POST /detect                           # create detection task
GET  /video_feed/<task_id>             # MJPEG result stream
GET  /api/telemetry?sn=<drone_sn>      # latest MQTT telemetry
GET  /get_latest_snapshot?task_id=<id> # latest confirmed snapshot
POST /stop_detect                      # stop task
POST /reload_models                    # hot reload configured models
```

<details><summary><b>任务请求示例：双航段 + 双电子围栏</b></summary>

```json
{
  "rtsp_url": "rtsp://camera-or-drone-stream/live",
  "drone_sn": "DRONE-SN-001",
  "detect_classes": [0, 1, 3, 4],
  "conf_thres_drone": 0.52,
  "conf_thres_ent": 0.75,
  "segments": [
    {"start": {"lat": 30.53210, "lng": 114.36020}, "stop": {"lat": 30.53280, "lng": 114.36110}, "roi": [0.08, 0.18, 0.92, 0.18, 0.96, 0.88, 0.12, 0.88]},
    {"start": {"lat": 30.53300, "lng": 114.36130}, "stop": {"lat": 30.53370, "lng": 114.36210}, "roi": [0.18, 0.20, 0.82, 0.82]}
  ]
}
```
</details>

### MISSION 02 // YOLOv5 Drone

<div align="center">
  <a href="https://github.com/wawjswt/Yolov5-Drone"><img src="works/yolo-car.jpg" width="48%" alt="Vehicle detection from an aerial view" /></a>
  <a href="https://github.com/wawjswt/Yolov5-Drone"><img src="works/yolo-fire.jpg" width="48%" alt="Fire detection demo" /></a><br/><br/>
  <a href="https://github.com/wawjswt/Yolov5-Drone"><img src="works/drone.gif" width="78%" alt="Animated drone target detection demonstration" /></a>
</div>

| Mission field | Readout |
| :-- | :-- |
| STATUS | 🟣 Exploration / research demo |
| OBJECTIVE | Aerial target detection for vehicles, fire and monitoring scenes |
| STACK | PyTorch · YOLOv5 · OpenCV |
| SOURCE | [Open repository →](https://github.com/wawjswt/Yolov5-Drone) |

### MISSION 03 // Gaussian Splatting

<div align="center"><img src="works/dog.png" width="48%" alt="Gaussian Splatting dog scene" /><img src="works/witcher.png" width="48%" alt="Gaussian Splatting Witcher scene" /><br/><br/><img src="works/demo.gif" width="78%" alt="Animated novel-view synthesis" /></div>

| Mission field | Readout |
| :-- | :-- |
| STATUS | 🟡 Spatial research |
| OBJECTIVE | 3D reconstruction, novel-view synthesis and visual expression |
| REFERENCE | [Gaussian Splatting →](https://github.com/graphdeco-inria/gaussian-splatting) |

### MISSION 04 // VGGT

<div align="center"><img src="works/vggt.png" width="72%" alt="VGGT visual geometry demonstration" /></div>

| Mission field | Readout |
| :-- | :-- |
| STATUS | 🟣 Learning radar |
| OBJECTIVE | Visual geometry, scene understanding and interactive spatial expression |
| REFERENCE | [Explore VGGT →](https://github.com/facebookresearch/vggt) |

## 🔭 Research Radar

<div align="center"><img src="works/research-radar.svg" width="100%" alt="Animated research radar" /></div>

- **Aerial AI:** route-aware detection, UAV inspection and video-stream intelligence.
- **Spatial Computing:** visual geometry, 3D reconstruction, novel-view synthesis and scene understanding.
- **Remote Sensing:** photogrammetry, geospatial perception and image interpretation.
- **AI Engineering:** model serving, streaming, observability and controllable orchestration.

## 🗺️ Flight Log

<div align="center"><img src="works/mission-timeline.svg" width="100%" alt="Animated research and project timeline" /></div>

> I am interested in the boundary where a vision algorithm becomes a dependable system for a real mission.

## 📡 GitHub Telemetry

<div align="center">
  <img src="https://github-readme-stats-eight-theta.vercel.app/api?username=wawjswt&show_icons=true&theme=tokyonight&hide_border=true&rank_icon=github" height="170" alt="GitHub statistics" />
  <img src="https://github-readme-stats-eight-theta.vercel.app/api/top-langs/?username=wawjswt&layout=compact&theme=tokyonight&hide_border=true" height="170" alt="Most used languages" />
  <br/><br/>
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=wawjswt&theme=tokyo-night&hide_border=true&area=true&area_color=22D3EE&line=22D3EE&point=8B5CF6" width="96%" alt="GitHub activity graph" />
  <br/><br/>
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=wawjswt&theme=tokyonight&hide_border=true&background=00000000&ring=22D3EE&fire=8B5CF6&currStreakLabel=E6F7FF" alt="GitHub contribution streak" />
</div>

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
