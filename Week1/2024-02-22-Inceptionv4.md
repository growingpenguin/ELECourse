---
layout: post
title:  "Inception v4"
---
# Overview
### Inception 
While Res-Net is more about going deeper in the neural networks when stacking layers on top of each other withou adding much more complexity,<br/>
Inception-Net is more about going wider in each of the individual layers in our modules rather than going deeper in each of the individual networks in our models <br/>
**Inception V1 Module** <br/>
![Inception1](https://github.com/growingpenguin/growingpenguin.github.io/assets/110277903/11aa8c34-901e-4903-a23f-198f0f47d408) <br/>
(1) Previous Layer <br/>
Input from the previous layer to this inception module in version1 <br/>
(2) 1x1 convolutions, 3x3 convolutions, 5x5 convolutions, 3x3 maxpooling <br/>
Have different kind of transformations or operations for that specific layer <br/>
-ResNet or other traditional layers  <br/>
One operation for layer like a 3x3 convolution or 5x5 convolution or max pooling layer <br/>
=> Do one specific operation or transformation for that convolutional layer <br/>
(One operation per layer like a 3x3 convolution or 5x5 convolutions or max pooling layer) <br/>
Idea behind inception is we go wider per convolution layer in the network so we do all the operations 
(3)Filter Concatenation <br/>
Do the transformations for all the operations, concatenate all of the results from those and have filter concatenation in the module <br/>
Different kind of transformations concatenated will now be fed to the next inception module <br/>
The process is repeated <br/>
Why this structure? <br/>
We want to have operations in the layer <br/>
Don't know what is the best operation or transformation to do layer by layer <br/>
Can have multiple operations or transformations layer by layer  <br/>
to choose what is the best transformation or what extracts the most useful information in this layer here from neural network or images passed through the neural network <br/>
So we can get the most useful and most exact important information from each of the individual layers by having different kind of transformations concatenated, choosing the best one and repeating this over and over again <br/>
**Inception V1 module optimized** <br/>
![Inception2](https://github.com/growingpenguin/growingpenguin.github.io/assets/110277903/312ac87a-7c2c-423b-9997-f201bfade615) <br/>
Have reduced complexity compared to Inception v1 module <br/>
If having four different kind of transformations per layer, computational cost would be increased when adding layer by layer <br/>
Inception is optimized and dimensions are reduced of the inputs from the previous layers <br/>
![Inception5](https://github.com/growingpenguin/growingpenguin.github.io/assets/110277903/e9d8188f-bd9d-4d17-9a8e-e5682e1f6c46) <br/>
To reduce the dimensions. 1x1 convolutions are done before doing the heavy convolution operations such as 3x3, 5x5, or 7x7 <br/>
1x1 convolutions reduce dimensions for our inputs to the neural network before doing heavy computations <br/>
Can reduce the complexity of our model and computational costs by training neural networks <br/>
By using this inception module, we can train faster and optimize the training process so that we learn faster and better with less computational costs <br/>
**Inception V2 module** <br/>
How can I reduce the complexity of the 5x5 convolution modules <br/>
To further reduce the amount of computation, the original Filter was divided and used <br/>
![Inception3](https://github.com/growingpenguin/growingpenguin.github.io/assets/110277903/9608bb6f-a673-4341-a0d1-f9fec6d0c645) <br/>
=> Try out different kind of convolutions to find an optimal way of having these larger convolutional blocks in our neural network <br/>
-Split up 3x3 convolution to 1x3 convolution and 3x1 convolution <br/>
And at the end concatenate those, then it will further reduce the complexity of our neural network <br/>
Reduce computational costs with up to 30% for bigger and larger kernels in neural network <br/>
Huge improvement to the inception module, we can now do bigger operations or bigger convolutional neural networks on neural network <br/>
without reducing the computational costs <br/>
We can now train neural networks in larger convolutional kernels <br/>
**Inception V3 module** <br/>
Optimizer Change: <br/>
Switched to RMSProp <br/>
Label Smoothing <br/>
Did not use one-hot encoding for target values to prevent overfitting <br/>
Distributed a very small value, e, even for labels with a value of 0 <br/>
BN-auxiliary <br/>
Applied Batch Normalization (BN) to the last Fully Connected layer <br/>

### Inception v4
The Premise <br/>
Make the modules more uniform. <br/>
The authors also noticed that some of the modules were more complicated than necessary <br/>
This can enable us to boost performance by adding more of these uniform modules <br/>
The Solution <br/>
The “stem” of Inception v4 was modified. The stem here, refers to the initial set of operations performed before introducing the Inception blocks. <br/>
What’s new <br/>
Change in the stem part <br/>
The number of Inception modules is increased <br/>
Inception modules made more uniform i.e. same numbers of filters are used in modules <br/>
Three types of inception module are named A, B, and C ( similar inception modules as that in inception-v2 )<br/>
They had three main inception modules, named A,B and C (Unlike Inception v2, these modules are infact named A,B and C). They look very similar to their Inception v2 (or v3) counterparts <br/>
![Inception4](https://github.com/growingpenguin/growingpenguin.github.io/assets/110277903/707206cb-b7a1-4546-95fa-1b8de6d3ffb3) <br/>
**Stem Module** <br/> 
기존 v1~v3가 성능은 좋지만 모델 구조가 너무 복잡했다 <br/> 
최대한 단순화 + Inception module을 더 많이 사용해서 성능과 구조 모두 잡았다 <br/> 
Stem: 이미지를 직접적으로 입력으로 받는 모듈 <br/> 
1) 초반부 3 x 3 Conv 3개는 Inception v2에서 사용한것과 완전히 동일 <br/> 
2) 채널의 수를 늘리기 위해 Pooling과 Conv 연산을 취한 뒤, concatenation한 것도 Inception v2에서도 동일 <br/> 
3 ) Channel reduction, Asymmetric Convolution을 취하는 과정 Inception v2에서 사용한것과 완전히 동일 <br/> 
Reference: <br/>
https://www.youtube.com/watch?v=STTrebkhnIk&t=662s <br/>
https://www.youtube.com/watch?v=STTrebkhnIk&t=662s <br/>
https://teddylee777.github.io/pytorch/inception-module/ <br/>
