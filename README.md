# datasets

一些常见的开源数据集

# 使用方法
## MNIST
- 大名鼎鼎的MNIST手写数字数据  
- 这里已经转成 .csv 格式并打包了，打包后约18Mb  
- 用下面的代码自动下载并读取为 numpy.array 格式
```py
import requests
url = 'https://github.com/guofei9987/datasets_for_ml/blob/master/MNIST/MNIST_data_csv.zip?raw=true'
r = requests.get(url)
with open('MNIST_data_csv.zip', 'wb') as f:
    f.write(r.content)
import zipfile
azip = zipfile.ZipFile('MNIST_data_csv.zip')
azip.extractall()

# 读取
import pandas as pd
mnist_train_images = pd.read_csv('mnist_train_images.csv', header=None).values
mnist_test_images = pd.read_csv('mnist_test_images.csv', header=None).values
mnist_train_labels = pd.read_csv('mnist_train_labels.csv', header=None).values
mnist_test_labels = pd.read_csv('mnist_test_labels.csv', header=None).values
```

## [rt-polaritydata](http://www.cs.cornell.edu/people/pabo/movie-review-data/)
- 电影影评文本数据
- 官网源数据不是UTF-8格式，这里已经转换成UTF-8，用Python读取时，无须再考虑编码问题。
- 用下面的代码直接读取即可
```
import pandas as pd
url_neg = 'http://www.guofei.site/datasets_for_ml/rt-polaritydata/rt-polaritydata/rt-polarity.neg'
url_pos = 'http://www.guofei.site/datasets_for_ml/rt-polaritydata/rt-polaritydata/rt-polarity.pos'
df_neg = pd.read_csv(url_neg, sep='\t', header=None, names=['text'])
df_pos = pd.read_csv(url_pos, sep='\t', header=None, names=['text'])
texts = list(df_pos.text) + list(df_neg.text)
target = [1] * df_pos.shape[0] + [0] * df_neg.shape[0]
```

## SMSSpamCollection
恶意短信文本库
```py
import pandas as pd
df=pd.read_csv('http://www.guofei.site/datasets/nlp/SMSSpamCollection.csv',sep='\t',header=None,names=['label','sentences'])
```

## 其它

LaTeX写的中文开源医学书籍：https://github.com/scienceasdf/medical-books

中文常用停用词表（哈工大停用词表、百度停用词表等）：https://github.com/goto456/stopwords
