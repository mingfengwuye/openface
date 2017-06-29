开源 人脸识别 openface 实用介绍 实例演示 训练自己的模型

Code
https://github.com/cmusatyalab/openface/

Install
http://cmusatyalab.github.io/openface/setup/

Demo train a classifier and test
1.Create a dir and copy images into it
  cd openface
  mkdir training-images
  cp face1/ openface/training-images -r
  cp face2/ openface/training-images -r

2.Find face and alignment
  put output images to /aligned-images and output image size is 96x96
  ./util/align-dlib.py ./training-images/ align outerEyesAndNose ./aligned-images/ --size 96

3.Extract features and put in /generated-embeddings
  ./batch-represent/main.lua -outDir ./generated-embeddings/ -data ./aligned-images

4.Train a classifier model(SVM), put classifier.pkl in generated-embeddings
  ./demos/classifier.py train ./generated-embeddings/　

5.Test classifier
  ./demos/classifier.py infer ./generated-embeddings/classifier.pkl face1test1.jpg

