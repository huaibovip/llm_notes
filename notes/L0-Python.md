# 任务一
> 请用Python实现一个wordcount函数，统计英文字符串中每个单词出现的次数。返回一个字典，key为单词，value为对应单词出现的次数。
>
>
> **TIPS:**
>> 记得先去掉标点符号,然后把每个单词转换成小写。不需要考虑特别多的标点符号，只需要考虑实例输入中存在的就可以。
>>
> **Input:**
>> Got this panda plush toy for my daughter's birthday, who loves it and takes it everywhere. It's soft and super cute, and its face has a friendly look. It's a bit small for what I paid though. I think there might be other options that are bigger for the same price. It arrived a day earlier than expected, so I got to play with it myself before I gave it to her.
>>
> **Output:**
>> {'got': 2, 'this': 1, 'panda': 1, 'plush': 1, 'toy': 1, 'for': 3, 'my': 1, 'daughter': 1, 's': 3, 'birthday': 1, 'who': 1, 'loves': 1, 'it': 7, 'and': 3, 'takes': 1, 'everywhere': 1, 'soft': 1, 'super': 1, 'cute': 1, 'its': 1, 'face': 1, 'has': 1, 'a': 3, 'friendly': 1, 'look': 1, 'bit': 1, 'small': 1, 'what': 1, 'i': 4, 'paid': 1,
'though': 1, 'think': 1, 'there': 1, 'might': 1, 'be': 1, 'other': 1, 'options': 1, 'that': 1, 'are': 1, 'bigger': 1, 'the': 1, 'same': 1, 'price': 1, 'arrived': 1, 'day': 1, 'earlier': 1, 'than': 1, 'expected': 1, 'so': 1, 'to': 2, 'play': 1, 'with': 1, 'myself': 1, 'before': 1, 'gave': 1, 'her': 1}
>>
>

实现代码:
```
import re


def wordcount(text):
    word_counts = {}
    # 使用正则表达式来分割单词, 忽略标点符号, 转换为小写以统一计数
    words = re.findall(r'\b\w+\b', text.lower())

    # 遍历单词列表并更新字典中的计数
    for word in words:
        if word in word_counts:
            word_counts[word] += 1
        else:
            word_counts[word] = 1

    return word_counts


if __name__ == '__main__':
    text = """
        Got this panda plush toy for my daughter's birthday,
        who loves it and takes it everywhere. It's soft and
        super cute, and its face has a friendly look. It's
        a bit small for what I paid though. I think there
        might be other options that are bigger for the
        same price. It arrived a day earlier than expected,
        so I got to play with it myself before I gave it
        to her.
        """

    print(wordcount(text))
```

# 任务二
> 请使用本地vscode连接远程开发机，将上面你写的wordcount函数在开发机上进行debug，体验debug的全流程，并完成一份debug笔记(需要截图)。


## 1.设置断点
  在代码行号旁边点击，可以添加一个红点，这就是断点（如果不能添加红点需要检查一下python extension是否已经正确安装）。当代码运行到这里时，它会停下来，这样你就可以检查变量的值、执行步骤等。
![image](https://img2024.cnblogs.com/blog/1664152/202407/1664152-20240710112836088-742325769.png)

## 2.启动debug
  点击VSCode上边栏的 “Python 调试程序：调试 Python 文件” 按钮，或者按 F5 键。
![image](https://img2024.cnblogs.com/blog/1664152/202407/1664152-20240710112847479-162423422.png)

## 3.查看变量
  当代码在断点处停下来时，你可以查看和修改变量的值。在“Run and Debug”侧边栏的“Variables”（变量）部分，你可以看到当前作用域内的所有变量及其值。
![image](https://img2024.cnblogs.com/blog/1664152/202407/1664152-20240710113108095-772690740.png)

## 4.单步执行代码
  你可以使用“Run and Debug”侧边栏顶部的按钮来单步执行代码。这样，你可以逐行运行代码，并查看每行代码执行后的效果。
![image](https://img2024.cnblogs.com/blog/1664152/202407/1664152-20240710113123839-906103575.png)


debug面板各按钮功能介绍：
  1. `continue`: 继续运行到下一个断点
  2. `step over`：跳过，可以理解为运行当前行代码，不进入具体的函数或者方法
  3. `step into`: 进入函数或者方法。如果当行代码存在函数或者方法时，进入代码该函数或者方法。如果当行代码没有函数或者方法，则等价于step over
  4. `step out`：退出函数或者方法, 返回上一层
  5. `restart`：重新启动debug


## 5.其他
进行debug调试时使用了Debug扩展，关于命令的解释如下：

`/usr/bin/env`: 这是一个环境变量，用于在系统上查找Python解释器的路径

`/root/.conda/envs/demo/bin/python`: 这是Python解释器的路径

`/root/.vscode-server/extensions/ms-python.debugpy-2024.0.0-linux-x64/bundled/libs/debugpy/adapter/../../debugpy/launcher`: 这是debugpy调试器的启动脚本的路径。它位于Visual Studio Code的扩展目录中

`34991`: 这通常是调试器监听的端口号

`--`: 在命令行参数解析中，-- 后面跟着的是传递给脚本的参数

`/root/projects/demo/word_count.py`: 这是要调试的Python脚本的路径
![image](https://img2024.cnblogs.com/blog/1664152/202407/1664152-20240710113503348-1501693661.png)
