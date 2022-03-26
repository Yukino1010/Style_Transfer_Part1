# Style_Transfer_Part1
## Introduce
In some tech magazines you may have seen many experiments with style transfer. <br>
Today, I'm going to introduce a very basic but very powerful and useful model call Cycle Gan.<br>
like its name, Cycle Gan is the menber in Gan familly, it has both generator and discriminator as other Gan model,
but the most important part and the reason why we call it "cycle" is come from it loss funtion.

![image](https://github.com/Yukino1010/Style_Transfer_Part1/blob/master/1_y1siCwwrhkrBSTaY7QL5Xw.png)




## Network Structure
![image](https://github.com/Yukino1010/Style_Transfer_Part1/blob/master/model.jpeg)

(https://hardikbansal.github.io/CycleGANBlog/)

In the generator I used 3 conv2D to down sampling the (256 * 256) image to the (64 * 64) and go through 9 residual block. <br>
Finally, after 3 deconv_block (conv2D + upsampling) the output shape return to 256 * 256.

the special trick in cycleGan is that we use ReflectionPadding2D instead of zero padding to reduce the data loss from convolution,
and because in Style Transfer the final result will depend on the specific features ,if we use Batch_norm as the normalization it will actually cause
the reduction of feature, so we use InstanceNormalization instead.


## Hyperparameters

- BATCH_SIZE = 2
- STEP_PER_EPOCH = 250
- LAMBDA_CYCLE = 10 
- LABEL_IDENTITY = 0.5
- DROPOUT_RATE = 0.5
- NUM_RESBLOCK = 9


## Result

![image](https://github.com/Yukino1010/Style_Transfer_Part1/blob/master/pictur.jpg)


## References

