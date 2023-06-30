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

### 1. Quick Use
We provide a demo for quick testing in this repo, simply running:

```
python3 inference.py --prompt "a bear walking through stars, artstation" --input_video bear.mp4 --control_mode depth 
```

Args:
- `--input_video`: path of input video(mp4 format).
- `--num_sample_frames`: nums of frames to generate. (recommend > 8).
- `--each_sample_frame`: sampling frames for each time. (for auto-regressive generateion.)
- `--sampling_rate`: skip sampling from the input video.

- `--control_mode`: allows for different control, currently support **`canny`, `depth`, `hed`**. (you need to download the weight of **hed** annotator from [link](https://huggingface.co/wf-genius/controlavideo-hed/resolve/main/hed-network.pth) and put it in work space.)
- `--video_scale`: guidance scale of video consistency, borrows from GEN-1. (don't be too large, 1~2 work well, set 0 to disable it.)
- `--init_noise_thres`: the propoed threshold of residual-based noise init. (range from 0 to 1, larger value leads to more smooth but may introduce artifacts.)

- `--inference_step, --guidance_scale, --height, --width, --prompt`: same as other T2I model.

If the automatic downloading not work, the models weights can be downloaded from: [depth_control_model](https://huggingface.co/wf-genius/controlavideo-depth), [canny_control_model](https://huggingface.co/wf-genius/controlavideo-canny), [hed_control_model](https://huggingface.co/wf-genius/controlavideo-hed).

###  2. Auto-Regressive Generation
Our model firstly generates the first frame. Once We get the first frame, we generate the subsquent frames conditioned on the first frame. Thus, it will allow our model to generate longer videos auto-regressive. (This operation is still under experiment and it may collaspe after 3 or 4 iterations.)
```
python3 inference.py --prompt "a bear walking through stars, artstation" --input_video bear.mp4 --control_mode depth --num_sample_frames 16 --each_sample_frame 8
```
Note that `num_sample_frames` should be multiple of `each_sample_frame`. 

###  Replace the 2d model (Experimentally)
Since we freeze the 2d model, you can replace it with any other model based on `stable-diffusion-v1-5` to generate custom-style videos. 

```
state_dict_path = os.path.join(pipeline_model_path, "unet", "diffusion_pytorch_model.bin")
state_dict = torch.load(state_dict_path, map_location="cpu")
video_controlnet_pipe.unet.load_2d_state_dict(state_dict=state_dict)    # reload 2d model.
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
