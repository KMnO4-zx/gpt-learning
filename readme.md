# 吴恩达prompt学习笔记

使用chatglm-6b的模型api完成吴恩达prompt课程，在学习笔记中有与chatgpt的回答做一些比较。课程内容采用的是DataWhale的中文翻译教程。[课程地址](https://github.com/datawhalechina/prompt-engineering-for-developers.git)


# prompt demo

一些觉得好玩的prompt，当然用到chatgpt也是没有问题。


## 代码大师

```python
def code_master(code):
    prompt = f"""
    我希望你能充当代码解释者，帮我阐明下面三个引号括起来的代码的语法和语义。使用markdown格式回复我。\。
    \"\"\"{code}\"\"\"
    """
    response = get_completion(prompt)
    return response

res = code_master("requests.post(url='http://127.0.0.1:8000', headers=headers, data=json.dumps(data))")
Markdown(res)
```

这段代码使用了Python的`requests`库发送HTTP请求,并使用了`json.dumps()`函数将JSON数据转换为字符串格式发送。

首先,三个引号括起来的代码中,第一个引号是一个字符串格式化指令,用于指定请求的URL。第二个引号是一个参数格式化指令,用于指定请求的参数。第三个引号是一个参数格式化指令,用于指定请求的数据。这些参数将被传递给`requests.post()`函数,该函数用于发送HTTP请求。

因此,完整的代码如下:

```
import requests

headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.3'}
data = '这是请求的数据'

requests.post(url='http://127.0.0.1:8000', headers=headers, data=json.dumps(data))
```

这段代码将一个JSON对象作为请求的数据,并将其传递给`requests.post()`函数,该函数用于发送HTTP请求。在函数内部,它将检查请求的参数是否与请求的数据匹配,并将它们替换为正确的参数。

## 诗人

```python
def poet(text):
    prompt = f"""
        我希望你能作为一个诗人。你要创作出能唤起人们情感并有力量搅动人们灵魂的诗篇。\
        写任何话题或主题，但要确保你的文字以美丽而有意义的方式传达你所要表达的感觉。你也可以想出一些短小的诗句，\
        但仍有足够的力量在读者心中留下印记。请用下面三个引号括起来的文本，创作一首古诗，使用markdown格式回复我。\。
        \"\"\"{text}\"\"\"
        """
    return get_completion(prompt)

Markdown(poet('此时夕阳仍在柳'))
```

```
此时夕阳仍在柳,
几许微风拂面来。
落叶纷飞飘舞处,
留连思绪任徘徊。
```

希望这首诗能够唤起您的灵感,为读者带来美的享受和力量搅动他们灵魂的感受。如果您有其他的话题或主题想要创作,请随时告诉我,我会尽力为您提供一些帮助。
