运行环境为python2.7的算法，评分脚本为score.py
运行环境为python3.5或高于此版本的算法，评分脚本为score_py3.py

组委会从训练集中随机选取300个record文件作为验证集（），存储在validation_set文件夹，该验证集目的仅仅是验证参赛者程序能够运行成功。

参赛者需将自己的预测函数写进cpsc2018.py脚本，并封装为函数 def cpsc2018(record_base_path)。每个record文件对应的识别结果为1-9之间的整数值。
输入参数：
record_base_path: 表示数据文件存储的路径
函数cpsc2018()最终应该在本地路径下生成answers.csv文件，存储预测函数识别数据集的结果，存储格式为：
Recoding    Result
B0001       1
.           .
.           .
.           .
即第一列为record文件名，第二列为识别结果。

以识别./validation_set路径下的数据为例：
cpsc2018(record_base_path='./validation_set/')
参赛团队需在运行评分脚本score.py之前运行cpsc2018.py脚本，以生成识别结果文件answers.csv，同时检验函数封装是否正确。
Linux/Unix环境下可运行指令： $python cpsc2018.py -p ./validation_set/
Windows环境下可运行指令   :  >python cpsc2018.py -p .\\validation_set\\
若成功生成answers.csv，且记录结果和格式符合要求，则封装正确。

cpsc2018.py脚本框架已给出，参赛者在该框架基础上，将自己算法的预测部分写入函数 cpsc2018() 的 INFERENCE PART。
生成answers.csv后，参赛团队可运行score.py(或score_py3.py)验证自己的算法：
Linux/Unix环境下可运行指令： $python score.py -r ./validation_set/REFERENCE.csv
Windows环境下可运行指令   :  >python score.py -r .\\validation_set\\REFERENCE.csv
最终会在本地路径下产生评分结果score.txt。

希望各参赛团队在运行验证集的过程中尽量优化算法时间复杂度，并提交在您本地电脑分类300个验证集record的算法运行时间，请把运行300个验证集record的时间结果提交为time_validation.txt文件，我们会根据此时间预测在test数据集上的执行时间并规划后续评估周期：
在所有test数据上，若算法预期运行时间小于30分钟，我们会在3天内给出评分反馈；
若算法预期运行时间在30分钟到120分钟之间，我们会在1周内给出评分反馈；
若算法预期运行时间超过120分钟，我们无法保证及时的评分反馈，请大家理解！
