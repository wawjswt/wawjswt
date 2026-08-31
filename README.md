
<!-- 🌟 背景装饰：顶部波浪 (Header) -->
<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&height=77&section=header"/>
</div>

<!-- 头部：动态打字机效果 -->
<div align="center">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&weight=600&size=30&pause=1000&color=33CCFF&center=true&vCenter=true&width=666&lines=Hi+there!+🤗+I'm+SamMantos;From+WHU;Enchante+!+😘" alt="Typing SVG" />
</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/Platform-IO/Platform-IO-for-VSCode/master/assets/platformio-header.gif" width="100%" alt="header gif" />
</div>

<!-- 社交徽章 & 访问量 -->
<div align="center">
  <a href="https://github.com/wawjswt">
    <img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white" alt="Github Badge"/>
  </a>
  <img src="https://komarev.com/ghpvc/?username=wawjswt&label=PROFILE+VIEWS&style=for-the-badge&color=blueviolet" alt="Profile Views" />
</div>

---

### 👨‍💻 About Me


<div align="center">
  <img src="https://img.shields.io/badge/Focus-CV%20%7C%20AI%20%7C%20Engineering-00C2FF?style=for-the-badge" alt="focus badge"/>
  <img src="https://img.shields.io/badge/Build-API%20%2B%20Model%20%2B%20Product-8A2BE2?style=for-the-badge" alt="build badge"/>
  <img src="https://img.shields.io/badge/Status-Exploring%20New%20Ideas-FFB347?style=for-the-badge" alt="status badge"/>
</div>

<div align="center">
  <img src="https://media.giphy.com/media/WUlplcMpOCEmTGBtBW/giphy.gif" width="30" alt="learning" /> 
  <b>Learning:</b> Python, AI Engineering, Latex <br/>
  
  <img src="https://media.giphy.com/media/du3J3cXyzhj75IOgvA/giphy.gif" width="30" alt="focusing" /> 
  <b>Focusing:</b> CV, PR, AI, RS <br/>
    
  🎮 <b>Hobby:</b> 🕹️Game, 📷 Photograph, 🎹 Music, ⚽ Soccer <br/>
  
  📮 <b>Contact:</b> Wentian_Shen@whu.edu.cn
</div>

---

### 🛠️ Tech Stack

<div align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=html,css,js,anaconda,react,vue,nextjs,nodejs,python,pytorch,tensorflow,git,docker,linux,bash,cpp,vscode,figma&perline=8&theme=dark" alt="Skill Icons" />
  </a>
</div>

---

<div align="center">
  <p><b>欢迎来到我的主页</b> ✨ 这里记录了我在计算机视觉、AI 工程、3D 重建与接口开发上的一些探索与实践。</p>
  <p>如果你对目标检测、实时视频流、模型部署或视觉系统感兴趣，欢迎一起交流。</p>
</div>

---

### 🚀 Recent Works

> **From model research to deployable systems** — I enjoy turning computer-vision ideas into practical tools, APIs, and visual demos.

#### 🤖 Object Detect · YOLOv5 Drone

<div align="center">
  <a href="https://github.com/wawjswt/Yolov5-Drone">
    <img src="works/yolo-car.jpg" width="48%" alt="Car detection demo" />
  </a>
  <a href="https://github.com/wawjswt/Yolov5-Drone">
    <img src="works/yolo-fire.jpg" width="48%" alt="Fire detection demo" />
  </a>
</div>

<div align="center">
  <br/>
  <a href="https://github.com/wawjswt/Yolov5-Drone">
    <img src="works/drone.gif" width="78%" alt="Drone detection demo" />
  </a>
</div>

- Real-time detection for fire, vehicles, and other targets in aerial or surveillance scenarios.
- Built with **PyTorch**, **YOLOv5**, and an engineering-oriented inference workflow.
- Suitable for drone inspection, safety monitoring, and emergency-warning prototypes.
- [View the YOLOv5 Drone project →](https://github.com/wawjswt/Yolov5-Drone)

---

#### 🛰️ Smart Detection API · Flask + YOLO + MQTT

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=rect&color=gradient&height=100&text=Smart%20Detection%20API&fontSize=31&fontColor=ffffff&desc=Vision%20%C2%B7%20Telemetry%20%C2%B7%20Mission%20Orchestration&descAlignY=72&descSize=16" width="100%" alt="Smart Detection API banner" />
  <br/><br/>
  <img src="works/smart-detection-api.svg" width="96%" alt="Smart Detection API architecture: video and MQTT telemetry pass through the YOLO orchestration layer to live operations and event delivery" />
  <br/><br/>
  <img src="https://img.shields.io/badge/REAL--TIME-VIDEO%20INFERENCE-06B6D4?style=for-the-badge&labelColor=0F172A" alt="Real-time video inference" />
  <img src="https://img.shields.io/badge/POLYGON-ROI%20GEOFENCE-8B5CF6?style=for-the-badge&labelColor=0F172A" alt="Polygon ROI geofence" />
  <img src="https://img.shields.io/badge/MISSION-MULTI--SEGMENT-22C55E?style=for-the-badge&labelColor=0F172A" alt="Multi-segment mission" />
</div>

> **A production-minded vision interface for drone and surveillance workflows.** It combines video inference, MQTT telemetry, route-aware task control, and operational feedback—so detection is not just *running*, but knows **where, when, and how** it should run.

| Capability | What it brings to the workflow |
| :-- | :-- |
| 🧭 **Multi-segment mission control** | A single `/detect` request can carry an ordered `segments` list. Each segment has optional GPS `start`, `stop`, and ROI settings, enabling a mission to progress through multiple flight legs instead of treating the route as one uninterrupted stream. |
| 🛡️ **Visual electronic fence** | ROI accepts either a rectangle or arbitrary polygon vertices. Detection boxes are kept only when their centers lie inside the normalized image-space polygon—an effective **visual geofence** for excluding irrelevant sky, roads, buildings, or camera edges. |
| 📍 **Telemetry-aware activation** | MQTT telemetry supplies latitude, longitude, altitude, heading, roll, gimbal pitch, serial number, and update time. The service can activate a segment on arrival near its start point and move on after reaching its stop point. |
| 🧠 **Multi-model inference** | Designed around multiple YOLO weights and class mappings for scenarios such as vehicles, people, fire, excavators, and trucks. Request-level `detect_classes` keeps every mission focused on the target types that matter. |
| 🎚️ **Per-model confidence control** | Tune confidence thresholds independently (`conf_thres_drone`, `conf_thres_ent`, `conf_thres_swim`, etc.), while preserving compatibility with a unified `model_conf` parameter. |
| 📺 **Live operational visibility** | Browser-friendly MJPEG preview at `/video_feed/<task_id>`, latest confirmed snapshot retrieval, and telemetry querying make a running task inspectable instead of opaque. |
| ✅ **More reliable event output** | Consecutive-frame confirmation reduces transient false alarms before snapshots and downstream events are produced; bounded execution and a push interval help keep the pipeline responsive under load. |
| 🔧 **Service operations** | Stop active detection, inspect the latest result, and reload models without rebuilding the service—useful for field iteration and model updates. |

**Mission flow — from a flight leg to a confirmed event**

```text
Enter segment → GPS proximity activates detection → Polygon ROI filters candidate boxes
      → Consecutive-frame confirmation → Snapshot + event delivery → Reach stop point → Next segment
```

**API surface**

```http
POST /detect                             # create a detection mission
GET  /video_feed/<task_id>               # MJPEG live result stream
GET  /api/telemetry?sn=<drone_sn>        # latest MQTT telemetry cache
GET  /get_latest_snapshot?task_id=<id>   # last confirmed snapshot
POST /stop_detect                        # stop the active detection task
POST /reload_models                      # hot-reload configured YOLO models
```

**Example: one request, two flight legs, two visual fences**

```json
{
  "rtsp_url": "rtsp://camera-or-drone-stream/live",
  "drone_sn": "DRONE-SN-001",
  "detect_classes": [0, 1, 3, 4],
  "conf_thres_drone": 0.52,
  "conf_thres_ent": 0.75,
  "segments": [
    {
      "start": {"lat": 30.53210, "lng": 114.36020},
      "stop":  {"lat": 30.53280, "lng": 114.36110},
      "roi": [0.08, 0.18, 0.92, 0.18, 0.96, 0.88, 0.12, 0.88]
    },
    {
      "start": {"lat": 30.53300, "lng": 114.36130},
      "stop":  {"lat": 30.53370, "lng": 114.36210},
      "roi": [0.18, 0.20, 0.82, 0.82]
    }
  ]
}
```

<details>
<summary><b>Why this interface matters</b></summary>
<br/>

This work turns a detection model into a controllable field-service component: **route context** decides when to infer, **ROI context** decides where to trust detections, and **telemetry + live outputs** let operators observe the whole loop. It is a step toward practical AI systems for aerial inspection, perimeter monitoring, emergency response, and safety operations.
</details>

> **Stack:** Flask · YOLOv5 / PyTorch · OpenCV · MQTT · Waitress · Multithreading
>
> **Design note:** the electronic fence described above is an **image-space polygon ROI**; GPS coordinates handle route/segment activation. Together, they form a layered spatiotemporal control mechanism.

---

#### ✨ Gaussian Splatting

<div align="center">
  <img src="works/dog.png" width="48%" alt="Gaussian Splatting dog scene" />
  <img src="works/witcher.png" width="48%" alt="Gaussian Splatting Witcher scene" />
  <br/><br/>
  <img src="works/demo.gif" width="78%" alt="Gaussian Splatting demo" />
</div>

- Exploring 3D scene reconstruction, novel-view synthesis, and expressive visual rendering.
- From still results to moving viewpoints, this work focuses on making reconstructed scenes vivid and presentable.
- [Reference: Gaussian Splatting →](https://github.com/graphdeco-inria/gaussian-splatting)

---

#### 🎮 VGGT Project

<div align="center">
  <img src="works/vggt.png" width="70%" alt="VGGT project demo" />
</div>

- An exploration of visual generation and game technology, connecting AI creativity with interactive experiences.
- I like projects that combine **research**, **engineering**, and **storytelling** — things that work well and look good, too.
- [Explore VGGT →](https://github.com/facebookresearch/vggt)

---

<!-- Action 区域：包含核心数据、折线图和打卡数据 -->
### 🏃 Action

<div align="center">
  <!-- 第一排：核心数据 + 常用语言 -->
<table>
  <tr>
    <td align="center">
      <img src="https://github-readme-stats-eight-theta.vercel.app/api?username=wawjswt&show_icons=true&theme=tokyonight&hide_border=true" alt="stats graph" />
    </td>
    <td align="center">
      <img src="https://github-readme-stats-eight-theta.vercel.app/api/top-langs/?username=wawjswt&layout=compact&theme=tokyonight&hide_border=true" alt="top langs" />
    </td>
  </tr>
</table>

  <!-- 第二排：Activity Graph (折线活动图) -->
  <br/>
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=wawjswt&theme=tokyonight&hide_border=true" width="95%" alt="Activity Graph" />

  <!-- 第三排：Streak 连续打卡 (居中显示，作为奖杯) -->
  <br/>
  <br/>
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=wawjswt&theme=tokyonight&hide_border=true&background=00000000" alt="streak graph" />
</div>

---

<!-- Contribution 区域：同时保留静态格子和贪吃蛇 -->
### ☁️ Contribution Activity

<div align="center">


  <!-- 2. 贪吃蛇动画 -->
  <!-- 引用你仓库分支里的 SVG 动画 -->
  <img src="https://raw.githubusercontent.com/wawjswt/wawjswt/output/github-contribution-grid-snake.svg" alt="snake animation" />
</div>

---

### 🤣 Random Joke

<div align="center">
  <img src="https://readme-jokes.vercel.app/api?theme=dark" alt="Jokes Card" />
</div>

<!-- 🌟 背景装饰：底部波浪 (Footer) -->
<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&height=77&section=footer" alt="footer" />
</div>
