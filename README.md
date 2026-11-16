# 🎬 ComfyUI + Wan 2.1 & Qwen 2509 全能视频与图像生成工作站

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/felixyu9722/ComfyUI-Wan2.1-Workstation/blob/main/ComfyUI_Wan2.1_Qwen2509_Workstation.ipynb)

<div align="center">
  <img src="./Google Colab AI Video Workstation.png" alt="ComfyUI + Wan 2.1 & Qwen 全能工作站" width="100%">
</div>

一套开箱即用的 **ComfyUI 全能视频生成与双图换装工作站**，支持在 Google Colab 或本地 GPU 一键部署，内置 **14 套全场景预配置工作流**：涵盖 **文生视频 (T2V)**、**图生视频 (I2V)**、**4~6步极速蒸馏加速**、**双图参考极速换装 (`Qwen-Image-Edit-2509`)**、**换装直转视频一条龙**、**无限制高清生图**、**首尾帧变装转场 (`FLF2V`)**、**多参考图融合 (`VACE`)**、**动作复刻 (`FunControl`)**、**数字人语音驱动说话 (`InfiniteTalk`)** 以及 **镜头运镜控制 (`FunCamera`)**。

---

## ✨ 核心亮点

- **🚀 一键部署**：提供完整 Colab Notebook (`ComfyUI_Wan2.1_Qwen2509_Workstation.ipynb`)，7 步全自动安装模型、插件与公网 WebUI 隧道。
- **📂 14 套预置工作流**：本仓库 [`workflows/`](./workflows/) 目录下提供全部 14 个 `.json` 工作流文件，可直接拖入任何 ComfyUI 画布使用。
- **⚡ 极致推理加速**：集成 `SageAttention` + `CausVid 4步蒸馏 LoRA` + `LightX2V 6步蒸馏 LoRA`，14B 大模型视频生成提速 **4 倍**。
- **👗 双图极速换装 + 转视频一条龙**：输入「人物图 + 衣服图」，2 秒完成精准换装并自动衔接生成 5 秒动态走秀视频。
- **💾 自动防丢备份**：内置 Google Drive 实时同步守护进程与一键 ZIP 打包。

---

## 📋 14 套预置工作流一览（位于 [`workflows/`](./workflows/) 目录）

| 编号 | 工作流文件 | 功能简介 | 核心模型 |
| :---: | :--- | :--- | :--- |
| **01** | `1_Wan2.1_T2V_1.3B_极速文生视频.json` | 480P 极速文生视频，几秒出片测试构图 | `wan2.1_t2v_1.3B_bf16` |
| **02** | `2_Wan2.1_T2V_14B_旗舰文生视频.json` | 14B 旗舰电影级画质文生视频 | `wan2.1_t2v_14B_fp8` |
| **03** | `3_Wan2.1_I2V_14B_480P_图生视频.json` | 单张静态图片转 5 秒动态视频 (480P) | `wan2.1_i2v_480p_14B_fp8` |
| **04** | `4_Wan2.1_I2V_14B_720P_高清图生视频.json` | 单张静态图片转 720P 高清视频 | `wan2.1_i2v_720p_14B_fp8` |
| **05** | `5_双图参考换装_Qwen2509极速版.json` | 输入「人物图 + 衣服图」，4 步精准换装生图 | `qwen_image_edit_2509_fp8` + `4steps LoRA` |
| **06** | `6_双图换装并直接转视频_一条龙.json` | 先自动给人物换装存图，再自动转为动态视频 | `Qwen-Edit-2509` + `Wan2.1-I2V-14B` |
| **07** | `7_无限制高清文生图_Wan2.1_14B.json` | 单张/多张批量/24小时无限连续生图 | `wan2.1_t2v_14B_fp8` (`length=1`) |
| **08** | `8_两张图首尾帧变装转场_Wan2.1_FLF2V_720P.json` | 输入起始帧+结束帧，生成丝滑变装或镜头转场 | `wan2.1_flf2v_720p_14B_fp8` |
| **09** | `9_VACE参考图融合视频_Wan2.1_VACE_14B.json` | 多参考图主体融合生视频 (含 4 步加速 LoRA) | `wan2.1_vace_14B_fp16` + `CausVid LoRA` |
| **10** | `10_Wan2.1_T2V_14B_4步极速文生视频.json` | 14B 旗舰文生视频 4 步蒸馏加速版 | `wan2.1_t2v_14B_fp8` + `CausVid LoRA` |
| **11** | `11_Wan2.1_I2V_14B_6步极速图生视频.json` | 14B 旗舰图生视频 6 步蒸馏加速版 | `wan2.1_i2v_480p_14B_fp8` + `LightX2V LoRA` |
| **12** | `12_动作复刻与视频模仿_Wan2.1_FunControl.json` | 上传人物图 + 参考动作视频，1:1 复刻视频动作 | `wan2.1_fun_control_1.3B_bf16` |
| **13** | `13_数字人语音开口说话_Wan2.1_InfiniteTalk.json` | 上传人物图 + 语音 MP3，生成口型同步说话视频 | `wan2.1_infiniteTalk` + `Wav2Vec2` |
| **14** | `14_镜头运镜精准控制_Wan2.1_FunCamera.json` | 下拉菜单精确控制推、拉、摇、移运镜 | `wan2.1_fun_camera_v1.1_1.3B_bf16` |

---

## 🚀 快速开始

1. 在 Google Colab 中打开本仓库中的 [`ComfyUI_Wan2.1_Qwen2509_Workstation.ipynb`](./ComfyUI_Wan2.1_Qwen2509_Workstation.ipynb)。
2. 依次运行 **步骤 1 ~ 步骤 7**。
3. 点击 **步骤 7** 底部输出的 `.trycloudflare.com` 公网链接即可进入 ComfyUI WebUI。
