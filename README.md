# Investigation of Optical Flow attack
In this project I tried to add patch with random noise into input image and predict Optical Flow on changed it.

The main idea about this task that we can make some patch that will totally destroy architecture and flow network will predict noise.

Also, I add a code to run this experiments on Google Colab.

I added some random generated Gaussian noises patch or green square on images, run a prediction and compare those results by calculating MSE for out of patch image, results for that in table bellow:

| Model   | Noise(50x50) | Square(50x50) | Noise(150x150) | Square(150x150) |
|---------|--------------|-------------|----------------|-----------------|
| PWCnet  | 11.033       | 12.076      | 84.22          | 100.923         |
| FlowNet | 78.506       | 78.607      | 62.581         | 91.921          |
| Raft    | -            | -           | **50.787**     | **73.691**      |

All this test was performed on small batch from KITTI2015 dataset

## Video results
Raft: https://drive.google.com/file/d/1Q5g7-9Zl49bjrnQYvG055O3T78PO5h0A/view?usp=sharing

Flownet: https://drive.google.com/file/d/1_EnFB45Vb_GpJ_UyVkdpabfOSEW2MKCR/view?usp=sharing

PWCnet: https://drive.google.com/file/d/1_FzG79u4bf7AeMpGJJRcOHBYO8u0JtDA/view?usp=sharing


## Thoughts
Based on this video examples and metrics I investigated, that PWCnet has the biggest error, and it tries to predict flow of missing patch of the video, so its hardly affect general results.
While Raft and FlowNet just ignores patch and only sometime small artifacts from patch appears on predictions.

Also, on small patch PWC get success with interpolate flow to missing patch.

### Noise vs Green
When compare random Gaussian noise patch and green square iget results that noise patch cause smaller changes, which mean that all this architecture robust to simple noise attack.

# Results

In results, I have a great time while this project for ML Research Winter School 2022 was running, I learned  how to work withOptical flow but can't successfully attack it.


