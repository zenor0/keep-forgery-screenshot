# KEEP FORGERY

> [!NOTE]
> 由于不同的设备分辨率不同, 请根据底图中实际的各个组件的位置修改 PSD 文件中图层的位置.

利用 photoshop-python-api 自动化生成 Keep 跑步截图. 输入一张 Keep 的截图, 通过修改代码中的配置文件, 你可以自定义截图上不同字段的内容.

另外提供从 Keep 安装包中提取出的 Keep Sans 字体, 你可以在 `fonts` 文件夹下找到. 使用本项目前请确保你已经安装了该字体.


# 运行环境

项目在 Python 3.10.12 on Windows 11 上开发测试.
Photoshop 版本为 Adobe Photoshop 25.3.1.

# 安装依赖

```shell
pip install -r requirements.txt
```


# 使用方法

## 生成

指定 `base_image` 作为你的底图

```python
base_image = "修改为你的图片路径"
```

然后执行 notebook 中的所有代码, 你将会在 `output` 文件夹下看到生成的图片.

## 自定义配置


通过修改代码中的配置文件, 你可以自定义生成截图的内容.

样例数据:

```python
weather = random.choice(['晴', '阴', '雨', '雪', '多云', '雷阵雨', '小雨', '小雪', '中雨', '中雪', '大雨', '大雪'])
temperature = random.randint(10, 20)

# 配置修改的模块
config = {
    'time': False,
    'user_id': False,
    'stamp': False,
    'mile': False,
    'total_time': False,
    'sport_time': False,
    'speed_avg': False,
    'cal': False,
    'climb': False,
    'step_frequency': True,
}

# 自定义生成的数据
img_data = {
    'time': datetime.datetime.now().strftime("%H:%M"),
    'user_id': '你的名字',
    'stamp': f'{datetime.datetime.now().strftime("%Y/%m/%d")} {datetime.datetime.now().strftime("%H:%M")} - {datetime.datetime.now().strftime("%H:%M")} · {weather} · {temperature}℃',
    'mile': random.randint(100, 200) / 100,
    'total_time': datetime.timedelta(seconds=random.randint(600, 3000)).__str__(),
    'sport_time': datetime.timedelta(seconds=random.randint(600, 3000)).__str__(),
    'speed_avg': f'{random.randint(10, 20)}\'{random.randint(10, 59)}\'\'',
    'cal': f'{random.randint(100, 200)}',
    'climb': f'{random.randint(100, 200)}',
    'step_frequency': f'{random.randint(60,80)}',
}
flag_attr = ['cal', 'climb', 'step_frequency']
img_data
```
