# Text Classification with CNN and RNN


## 数据集

使用THUCNews
本次训练使用了其中的10个分类，每个分类6500条数据。
类别如下：

```
体育, 财经, 房产, 家居, 教育, 科技, 时尚, 时政, 游戏, 娱乐
```
数据集划分如下：

- 训练集: 5000*10
- 验证集: 500*10
- 测试集: 1000*10

- cnews.train.txt: 训练集(50000条)
- cnews.val.txt: 验证集(5000条)
- cnews.test.txt: 测试集(10000条)

## 预处理

`data/cnews_loader.py`为数据的预处理文件。

- `read_file()`: 读取文件数据;
- `build_vocab()`: 构建词汇表，使用字符级的表示，这一函数会将词汇表存储下来，避免每一次重复处理;
- `read_vocab()`: 读取上一步存储的词汇表，转换为`{词：id}`表示;
- `read_category()`: 将分类目录固定，转换为`{类别: id}`表示;
- `to_words()`: 将一条由id表示的数据重新转换为文字;
- `process_file()`: 将数据集从文字转换为固定长度的id序列表示;
- `batch_iter()`: 为神经网络的训练准备经过shuffle的批次的数据。

经过数据预处理，数据的格式如下：

| Data | Shape | Data | Shape |
| :---------- | :---------- | :---------- | :---------- |
| x_train | [50000, 600] | y_train | [50000, 10] |
| x_val | [5000, 600] | y_val | [5000, 10] |
| x_test | [10000, 600] | y_test | [10000, 10] |

## CNN卷积神经网络
结构图:
image/cnn_architure.png
### 配置项

CNN可配置的参数如下所示，在`cnn_model.py`中。

### CNN模型

具体参看`cnn_model.py`的实现。

### 训练与验证

在验证集上的最佳效果为94.04%

准确率和误差如图所示：
image/cnn_train.png

### 测试

在测试集上的准确率达到了95.89%，且各类的precision, recall和f1-score都超过了0.9。

image/cnn_test.png

## RNN循环神经网络

结构图：
image/rnn_arichture.png

### 配置项

RNN可配置的参数如下所示，在`rnn_model.py`中。

### RNN模型

具体参看`rnn_model.py`的实现。

### 训练与验证

电脑过渣，跑不动

### 测试

