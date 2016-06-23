# tensorflow-mnist-osxtest-easy<BR>
<pre>
This is a repository for testing tensorflow on osx for easy attitude.<BR>
osx 10.10.5/mac mini (late 2012)/mem 4gb/no gpus.
<BR>
1. motivation<BR>
I saw Keras with tensorflow here.<BR>
http://amacbee.hatenablog.com/entry/2015/12/02/220414<BR>
So did test on osx yosemite and mac mini.<BR>
<BR>
2. then, why mnist?<BR>
Then I saw this.<BR>
http://qiita.com/haminiku/items/36982ae65a770565458d<BR>
saw Deep MNIST for Experts exist.<BR>
<BR>
3. contents<BR>
3.1 installation check<BR>
I saw bellow.<BR>
python tensorflow/examples/tutorials/mnist/fully_connected_feed.py<BR>
RuntimeError: module compiled against API version 0xa but this version of numpy is 0x9<BR>
after do this:<BR>
http://stackoverflow.com/questions/37002134/having-error-with-tensorflow-mnist<BR>
sudo pip install --upgrade https://storage.googleapis.com/tensorflow/mac/tensorflow-0.8.0-py2-none-any.whl<BR>
It works for Mac os<BR>
how to fix<BR>
import numpy<BR>
numpy.__version__<BR>
numpy.__path__<BR>
>>> numpy.__path__<BR>
['/Library/Python/2.7/site-packages/numpy-override/numpy']<BR>
>>><BR>
sh-3.2# mv /Library/Python/2.7/site-packages/numpy-override/numpy /Library/Python/2.7/site-packages/numpy-override/numpy.bk<BR>
sh-3.2# pip install --upgrade numpy<BR>
Requirement already up-to-date: numpy in /Library/Python/2.7/site-packages<BR>
Cleaning up...<BR>
And also.<BR>
http://sechiro.hatenablog.com/entry/2016/04/02/Mac%E3%81%ABTensorFlow%E3%82%92%E5%85%A5%E3%82%8C%E3%82%88%E3%81%86%E3%81%A8%E3%81%97%E3%81%9F%E3%82%89%E3%80%81Numpy%E3%81%AE%E3%82%A8%E3%83%A9%E3%83%BC%E3%81%8C%E5%87%BA%E3%81%9F%E3%81%AE%E3%81%A7<BR>
sh-3.2# mv /System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/numpy<BR> /System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/numpy.bk<BR>
And also.<BR>
https://github.com/pypa/pip/issues/3165<BR>
  sudo easy_install --upgrade six<BR>
  pip install --ignore-installed --upgrade https://storage.googleapis.com/tensorflow/mac/tensorflow-0.8.0-py2-none-any.whl<BR>
<BR>
3.2 Finally fixed<BR>
http://domkade.hatenablog.jp/entry/2016/04/07/011016<BR>
I saw Deep MNIST for Experts codes all in one above.<BR>
So paste it as mnist4exp.py.<BR>
sh-3.2# python mnist4exp.py<BR>
Traceback (most recent call last):<BR>
  File "mnist4exp.py", line 1, in <module><BR>
    from tensorflow.examples.tutorials.mnist import input_data<BR>
  File "/private/var/root/tensorflow-master/tensorflow/__init__.py", line 23, in <module><BR>
    from tensorflow.python import *<BR>
  File "/private/var/root/tensorflow-master/tensorflow/python/__init__.py", line 48, in <module><BR>
    from tensorflow.python import pywrap_tensorflow<BR>
ImportError: cannot import name pywrap_tensorflow<BR>
mv mnist4exp.py  tensorflow/examples/tutorials/mnist/<BR>
sh-3.2# python tensorflow/examples/tutorials/mnist/mnist4exp.py<BR>
Successfully downloaded train-images-idx3-ubyte.gz 9912422 bytes.<BR>
Extracting MNIST_data/train-images-idx3-ubyte.gz<BR>
Successfully downloaded train-labels-idx1-ubyte.gz 28881 bytes.<BR>
Extracting MNIST_data/train-labels-idx1-ubyte.gz<BR>
Successfully downloaded t10k-images-idx3-ubyte.gz 1648877 bytes.<BR>
Extracting MNIST_data/t10k-images-idx3-ubyte.gz<BR>
Successfully downloaded t10k-labels-idx1-ubyte.gz 4542 bytes.<BR>
Extracting MNIST_data/t10k-labels-idx1-ubyte.gz<BR>
0.9092<BR>
step 0, training accuracy 0.08<BR>
step 100, training accuracy 0.84<BR>
step 200, training accuracy 0.92<BR>
step 300, training accuracy 0.96<BR>
step 400, training accuracy 0.94<BR>
step 500, training accuracy 0.9<BR>
step 600, training accuracy 0.92<BR>
step 700, training accuracy 0.98<BR>
step 800, training accuracy 0.98<BR>
:<BR>
:<BR>
It is OK!.<BR>
</pre>
