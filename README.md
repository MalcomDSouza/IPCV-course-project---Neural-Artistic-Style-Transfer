# IPCV-course-project---Neural-Artistic-Style-Transfer
This is a course project for IPCV course at  NITK. It is a popular neural artistic style transfer algorithm. I have tuned the parameters to give more accurate outputs.

Tune the following according to your liking -

Tuning the Artistic Output  

1. Adjust the Loss Weights
The style_weight, content_weight, and total_variation_weight variables.
Effects:
More Style: To make the image look more like the painting, increase the style_weight (e.g., 1e-1) or decrease the content_weight (e.g., 1e3).
More Content: To make the original image clearer and more defined, decrease the style_weight (e.g., 1e-3) or increase the content_weight (e.g., 1e5).
Less Noise: If your final image looks "staticky" or "pixelated," increase the total_variation_weight (e.g., 60 or 100). This forces the optimizer to prefer smoother results.
More Detail (less "waxy"): If the image looks too blurry or "smudged," decrease the total_variation_weight (e.g., 10 or 15).

2. Change the Content and Style Layers
Different layers of the VGG network capture different scales of features.
Effects:
Content Layer: I used block5_conv2, which is very deep. This is good for capturing the overall structure of the content. If you use a shallower layer (e.g., block4_conv2), the model would try to preserve finer textures from the original image, which often looks less "artistic".
Style Layers: I used a mix of shallow and deep layers.
For a coarser style (e.g., big splotches of color), try using only the shallow layers (e.g., ['block1_conv1', 'block2_conv1']).
For a finer, more complex style, try using only the deeper layers (e.g., ['block3_conv1', 'block4_conv1', 'block5_conv1']).
 
Tuning the Speed and Training Process

1. Adjust Training Duration
Effect: The total of 3000 steps might not be enough. Try increasing to epochs = 40 for 4000 total steps. The image will continue to refine.

3. Adjust the Learning Rate
Effect:
0.02 is actually a very high learning rate for this task. It gets results fast, but they might be noisy.
If your image "explodes" into noise or looks very unstable, you must decrease the learning rate (e.g., 0.002 or 0.001). This will take more steps to converge, but the result will be more stable.
