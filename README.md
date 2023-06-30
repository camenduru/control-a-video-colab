🐣 Please follow me for new updates https://twitter.com/camenduru <br />
🔥 Please join our discord server https://discord.gg/k5BwmmvJJU <br />
🥳 Please join my patreon community https://patreon.com/camenduru <br />

## 🦒 Colab

# 🚦 WIP 🚦

| Colab | Info
| --- | --- |
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/camenduru/control-a-video-colab/blob/main/control_a_video_colab.ipynb) | control_a_video_colab

## Tutorial

```
--control_mode', type=str, default='depth', help='support: hed, canny, depth'
--inference_step', type=int, default=20, help='denoising steps for inference'
--guidance_scale', type=float, default=7.5, help='guidance scale'
--seed',  type=int, default=1, help='seed'
--num_sample_frames', type=int, default=8, help='total frames to inference'
--each_sample_frame', type=int, default=8, help='auto-regressive generation for each iteration'
--sampling_rate', type=int, default=3, help='skip sampling from input video'
--height', type=int, default=512, help='ouput height'
--width', type=int, default=512, help='ouput width'
--video_scale', type=float, default=1.5, help='video smoothness scale'
--init_noise_thres', type=float, default=0.1, help='thres for res noise init'
--input_video',type=str, default='bear.mp4'
--prompt',type=str, default="a bear walking through stars, artstation"
```

## Main Repo
https://github.com/Weifeng-Chen/control-a-video

## Paper
https://arxiv.org/abs/2305.13840

## Page
https://controlavideo.github.io/

## Output
<table><tbody><tr><td><center>
input
<br>
<video src="https://user-images.githubusercontent.com/54370274/250072255-4afaea76-b804-417f-b618-4c75e7a0969f.mp4" data-canonical-src="https://user-images.githubusercontent.com/54370274/250072255-4afaea76-b804-417f-b618-4c75e7a0969f.mp4" controls="controls" muted="muted" class="d-block rounded-bottom-2 border-top width-fit" style="max-height:640px; min-height: 200px">
</video>
</center></td><td><center>
a bear walking through stars, artstation.
<br>
<img src="https://github-production-user-asset-6210df.s3.amazonaws.com/54370274/250072935-19eca168-95c1-433f-b607-fdc34bc84c33.gif" alt="a bear walking through stars, artstation" style="width: 300px;">
</center></td></tr></tbody></table>
