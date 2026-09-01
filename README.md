<!-- ================================================================ -->
<!--  PROFILE README · Aerial Mission Control / Professional Portfolio -->
<!-- ================================================================ -->

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:07142B,45:123C63,100:7C3AED&height=210&section=header&text=SamMantos%20%7C%20Aerial%20Vision%20Systems&fontSize=38&fontColor=E6F7FF&fontAlignY=36&desc=Computer%20Vision%20%C2%B7%20Drone%20Intelligence%20%C2%B7%20Spatial%20AI%20%C2%B7%20Engineering&descSize=17&descAlignY=58&animation=fadeIn" alt="SamMantos aerial vision systems banner" />
</div>

<div align="center">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&weight=600&size=22&pause=1200&color=22D3EE&center=true&vCenter=true&width=760&lines=Turning+visual+intelligence+into+field-ready+systems.;Computer+Vision+%7C+UAV+Inspection+%7C+Spatial+AI+%7C+Deployment" alt="Typing introduction" />
</div>

<div align="center">
  <a href="https://github.com/wawjswt">
    <img src="https://img.shields.io/badge/GitHub-wawjswt-0F172A?style=for-the-badge&logo=github&logoColor=white" alt="GitHub wawjswt" />
  </a>
  <img src="https://komarev.com/ghpvc/?username=wawjswt&label=MISSION+VISITS&style=for-the-badge&color=0EA5E9" alt="Profile views" />
  <img src="https://img.shields.io/badge/STATUS-BUILDING%20IN%20PUBLIC-22C55E?style=for-the-badge&labelColor=0F172A" alt="Building in public" />
</div>

---

## 🛸 Mission Brief

> **将视觉智能转化为可落地的现场系统。**  
> I explore the path from **computer-vision models** to **observable, controllable, and deployable** UAV / surveillance workflows.

- 🎓 **Based at WHU** · interested in Computer Vision, Remote Sensing, Photogrammetry and AI Engineering.
- 🛰️ **Current focus** · drone inspection, real-time target detection, spatial understanding and 3D reconstruction.
- ⚙️ **What I enjoy building** · systems that connect **model inference + video streams + telemetry + task orchestration**.
- 📷 **Beyond code** · photography, games, music and football.
- 📮 **Contact** · `Wentian_Shen@whu.edu.cn`

<div align="center">
  <img src="https://img.shields.io/badge/FOCUS-Computer%20Vision%20%26%20Spatial%20AI-06B6D4?style=for-the-badge&labelColor=0F172A" alt="Computer vision and spatial AI" />
  <img src="https://img.shields.io/badge/DOMAIN-UAV%20Inspection%20%26%20Remote%20Sensing-8B5CF6?style=for-the-badge&labelColor=0F172A" alt="UAV inspection and remote sensing" />
  <img src="https://img.shields.io/badge/BUILD-Model%20to%20Mission%20System-22C55E?style=for-the-badge&labelColor=0F172A" alt="Model to mission system" />
</div>

## 🟢 Mission Status

<div align="center">

| Signal | Current Focus |
| :-- | :-- |
| 🛰️ **Active Domain** | UAV inspection & real-time vision systems |
| 🧠 **Model Track** | YOLO detection · visual understanding · 3D reconstruction |
| 🗺️ **Spatial Layer** | GPS segments · Polygon ROI · telemetry-aware decisions |
| ⚙️ **System Goal** | Turn model inference into controllable field missions |
| 🔭 **Now Exploring** | Gaussian Splatting · VGGT · spatial AI engineering |

</div>

---

## 🧭 Operational Toolkit

<div align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=python,pytorch,tensorflow,opencv,flask,fastapi,docker,linux,bash,git,github,cpp,js,html,css,react,vue,anaconda,vscode,figma&perline=10&theme=dark" alt="Technology stack: Python, PyTorch, TensorFlow, OpenCV, Flask, Docker, Linux and more" />
  </a>
</div>

<div align="center">

| Vision & AI | Mission & Backend | Spatial Computing | Engineering |
| :-- | :-- | :-- | :-- |
| YOLOv5 · PyTorch · OpenCV | Flask · MQTT · RTSP · MJPEG | Remote Sensing · Photogrammetry · 3DGS | Docker · Git · Linux · C++ |

</div>

---

## 🚀 Selected Systems / Recent Works

### 01 · Smart Detection API — UAV Intelligent Mission Control

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=rect&color=0:0B1220,45:123C63,100:3B1D72&height=108&text=SMART%20DETECTION%20API&fontSize=32&fontColor=E6F7FF&desc=VISION%20%C2%B7%20TELEMETRY%20%C2%B7%20MISSION%20ORCHESTRATION&descAlignY=73&descSize=15" width="100%" alt="Smart Detection API title" />
  <br/>
  <br/>
  <img src="works/smart-detection-api.svg" width="96%" alt="Architecture diagram: video streams and MQTT telemetry enter a detection orchestrator, which provides live operations and events" />
</div>

> **A production-minded interface for drone and surveillance workflows.**  
> 它不是只执行一次 YOLO 推理，而是将**视频流、飞行轨迹、电子围栏、模型策略与实时反馈**组织成可观测的任务闭环。

<div align="center">
  <img src="https://img.shields.io/badge/REAL--TIME-VIDEO%20INFERENCE-06B6D4?style=for-the-badge&labelColor=0F172A" alt="Real-time video inference" />
  <img src="https://img.shields.io/badge/MISSION-MULTI--SEGMENT-22C55E?style=for-the-badge&labelColor=0F172A" alt="Multi-segment mission" />
  <img src="https://img.shields.io/badge/GEOFENCE-POLYGON%20ROI-8B5CF6?style=for-the-badge&labelColor=0F172A" alt="Polygon ROI geofence" />
</div>

#### ✦ Interface highlights

1. **多航段任务编排（Multi-segment mission）**  
   一个检测任务可包含多个 `segments`。每个航段拥有独立的起点、终点与 ROI；系统依据无人机 GPS 与航段位置关系，自动进入、退出并切换检测状态，适合巡检航线和分区任务。

2. **双层空间约束：GPS 航段 + 图像电子围栏**  
   - **GPS 起止点**决定何时启用当前航段的检测；
   - **Polygon ROI** 是图像空间多边形电子围栏，仅保留围栏内的候选框。  
   这让任务同时具备“**什么时候检测**”和“**画面中哪里可信**”两层控制。

3. **实时视频与遥测融合**  
   支持 RTSP / HTTP / 本地文件等视频源，使用 MQTT 缓存无人机最新遥测信息（例如 GPS、姿态和高度），使检测事件能与飞行上下文对应。

4. **多模型、分类映射与独立阈值策略**  
   可根据类别将目标分发到不同 YOLO 模型，并使用独立置信度阈值；面对无人机目标、企业 / 现场目标等不同识别任务时，避免一套阈值处理所有场景。

5. **面向现场的结果可信度与任务控制**  
   使用连续帧确认降低瞬时误报；提供 MJPEG 实时结果流、最新确认截图、停止任务和模型热更新能力，支持持续演示、调试与现场迭代。

#### ✦ Mission flow

```text
Create task → enter GPS segment → activate visual inference → apply Polygon ROI
        → confirm detection across frames → save snapshot / deliver event
        → reach segment stop point → switch to the next flight leg
```

#### ✦ API surface

```http
POST /detect                             # 创建目标检测任务
GET  /video_feed/<task_id>               # 获取 MJPEG 实时检测结果流
GET  /api/telemetry?sn=<drone_sn>        # 查询最新 MQTT 遥测缓存
GET  /get_latest_snapshot?task_id=<id>   # 获取最近一次确认截图
POST /stop_detect                        # 停止当前检测任务
POST /reload_models                      # 热更新已配置的 YOLO 模型
```

<details>
<summary><b>查看任务请求示例：双航段 + 双电子围栏</b></summary>

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
      "stop": {"lat": 30.53280, "lng": 114.36110},
      "roi": [0.08, 0.18, 0.92, 0.18, 0.96, 0.88, 0.12, 0.88]
    },
    {
      "start": {"lat": 30.53300, "lng": 114.36130},
      "stop": {"lat": 30.53370, "lng": 114.36210},
      "roi": [0.18, 0.20, 0.82, 0.82]
    }
  ]
}
```

</details>

> **Stack:** Flask · YOLOv5 / PyTorch · OpenCV · MQTT · Waitress · Multithreading  
> **Use cases:** aerial inspection · perimeter monitoring · emergency response · safety operations

---

### 02 · YOLOv5 Drone — Aerial Target Detection

<div align="center">
  <a href="https://github.com/wawjswt/Yolov5-Drone">
    <img src="works/yolo-car.jpg" width="48%" alt="Vehicle detection from an aerial view" />
  </a>
  <a href="https://github.com/wawjswt/Yolov5-Drone">
    <img src="works/yolo-fire.jpg" width="48%" alt="Fire detection demo" />
  </a>
  <br/>
  <br/>
  <a href="https://github.com/wawjswt/Yolov5-Drone">
    <img src="works/drone.gif" width="78%" alt="Animated drone target detection demonstration" />
  </a>
</div>

- 面向空中视角与监控场景的实时目标检测探索，覆盖车辆、火情及其他目标类别。
- 基于 **PyTorch + YOLOv5** 构建工程化推理流程，关注检测结果在实际巡检与预警任务中的可用性。
- [进入 YOLOv5 Drone 项目 →](https://github.com/wawjswt/Yolov5-Drone)

---

### 03 · Gaussian Splatting — 3D Scene Reconstruction

<div align="center">
  <img src="works/dog.png" width="48%" alt="Gaussian Splatting reconstruction: dog scene" />
  <img src="works/witcher.png" width="48%" alt="Gaussian Splatting reconstruction: Witcher scene" />
  <br/>
  <br/>
  <img src="works/demo.gif" width="78%" alt="Animated novel-view synthesis from a Gaussian Splatting scene" />
</div>

- 探索 3D 场景重建、Novel View Synthesis 与视觉表达，让空间信息不仅可计算，也更具呈现力。
- [Gaussian Splatting reference →](https://github.com/graphdeco-inria/gaussian-splatting)

---

### 04 · VGGT — Visual Geometry & Spatial Understanding

<div align="center">
  <img src="works/vggt.png" width="72%" alt="VGGT project visual demonstration" />
</div>

- 关注视觉生成、几何理解与交互式表达的连接点；尝试将研究、工程与可视化叙事结合起来。
- [Explore VGGT →](https://github.com/facebookresearch/vggt)

---

## 🧩 System Capabilities Matrix

> The Smart Detection API is designed as a compact **perception → spatial control → decision → operations** loop, rather than an isolated detection endpoint.

| Capability layer | Core capability | Operational value |
| :-- | :-- | :-- |
| 👁️ Perception | YOLO multi-model inference · category mapping | Match different targets with appropriate models and policies |
| 🗺️ Spatiotemporal control | GPS flight segments · Polygon ROI visual fence | Decide **when to detect** and **where to trust** detections |
| 📡 Data connection | RTSP / HTTP streams · MQTT telemetry cache | Connect visual observations with the latest flight context |
| ✅ Decision reliability | Per-model thresholds · consecutive-frame confirmation | Reduce transient false positives in live video |
| 🛠️ Field operations | MJPEG feed · snapshots · stop control · model hot reload | Support demonstrations, debugging and iterative deployment |

---

## 🔭 Research & Learning Radar

<div align="center">
  <img src="https://img.shields.io/badge/AERIAL%20AI-UAV%20Inspection%20%26%20Route--aware%20Detection-06B6D4?style=for-the-badge&labelColor=0F172A" alt="Aerial AI research direction" />
  <img src="https://img.shields.io/badge/SPATIAL%20AI-3D%20Reconstruction%20%26%20Scene%20Understanding-8B5CF6?style=for-the-badge&labelColor=0F172A" alt="Spatial AI research direction" />
</div>

- **Aerial AI** — route-aware detection, UAV inspection workflows and video-stream intelligence.
- **Spatial Computing** — visual geometry, 3D reconstruction, novel-view synthesis and scene understanding.
- **Remote Sensing** — photogrammetry, geospatial perception and image interpretation.
- **AI Engineering** — model serving, streaming, observability and controllable task orchestration.

> I am especially interested in the boundary where a vision algorithm becomes a dependable system for a real mission.

---

## 📡 GitHub Signals

<div align="center">
  <img src="https://github-readme-stats-eight-theta.vercel.app/api?username=wawjswt&show_icons=true&theme=tokyonight&hide_border=true&rank_icon=github" height="170" alt="GitHub statistics" />
  <img src="https://github-readme-stats-eight-theta.vercel.app/api/top-langs/?username=wawjswt&layout=compact&theme=tokyonight&hide_border=true" height="170" alt="Most used languages" />
</div>

<div align="center">
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=wawjswt&theme=tokyo-night&hide_border=true&area=true&area_color=22D3EE&line=22D3EE&point=8B5CF6" width="96%" alt="GitHub activity graph" />
  <br/>
  <br/>
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=wawjswt&theme=tokyonight&hide_border=true&background=00000000&ring=22D3EE&fire=8B5CF6&currStreakLabel=E6F7FF" alt="GitHub contribution streak" />
</div>

---

## 🐍 Contribution Flight Path

<div align="center">
  <img src="https://raw.githubusercontent.com/wawjswt/wawjswt/output/github-contribution-grid-snake.svg" alt="Animated contribution snake" />
</div>

---

## ☕ Off-duty Signal

<div align="center">
  <img src="https://readme-jokes.vercel.app/api?theme=tokyonight" alt="Random programming joke" />
</div>

<div align="center">
  <sub>Open to exchanging ideas about computer vision, UAV inspection, remote sensing and practical AI systems.</sub>
</div>

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:07142B,45:123C63,100:7C3AED&height=110&section=footer" alt="Footer wave" />
</div>


