---
title: "猫咪的卡路里"
subtitle: ""
date: 2024-08-28T16:41:45+08:00
draft: true
authors: [andy90s]
description: ""

tags: []
categories: []
series: []
keywords: []

hiddenFromHomePage: false
hiddenFromSearch: false

featuredImage: ""
featuredImagePreview: ""

toc:
  enable: true
math:
  enable: true
lightgallery: true
license: ""
---
<!--more-->

## 前言

目的是为了根据猫咪6轴数据计算出猫咪消耗的卡路里。

## 几个名称概念

### 1.RER

`RER` [^1] **Resting Energy Requirement**，即静息能量需求，是指动物在安静状态下，维持正常生理功能所需的能量。RER 通常用于估算动物（包括宠物）的基础代谢率，即在不进行任何额外活动的情况下，维持心跳、呼吸、体温调节等基本生理功能所消耗的能量[^2]

猫咪的RER计算公式如下：

$ \text{RER} = 70 \times \text{体重(kg)}^{0.75} $

### 2.猫咪RER各种状态系数 [^3]

|猫咪状态|静息消耗系数|
|---|---|
|幼猫|2.5|
|已结扎成年猫|1.2~1.4|
|未结扎成年猫|1.4~1.6|
|过胖的成年猫|1.2~1.8|
|偏瘦的成年猫|0.8~1.0|
|中年猫咪7~11岁左右|1.1~1.4|
|老年猫咪11岁以上|1.1~1.6|
|怀孕期猫咪|1.6~2.0|
|哺乳期猫咪|2.0~|

### 3.MET

MET（Metabolic Equivalent of Task）是一种用于衡量人体运动强度的单位，1 MET等于人体在安静状态下的基础代谢率。MET值越高，运动强度越大，消耗的卡路里也越多。

举例(人类18~69岁健康成年人):

- 静态行为: <= 1.5 MET
- 低强度运动: 1.6-2.9 MET
- 中等强度运动: 3.0-5.9 MET
- 高强度运动: >= 6.0 MET

## 用到的公式计算

### 计算猫咪静止状态下的均值

对于每个方向的加速度和角速度，计算其均值：

$$\bar{a}_x = \frac{1}{n} \sum_{i=1}^{n} a_{x,i}$$

$$\bar{a}_y = \frac{1}{n} \sum_{i=1}^{n} a_{y,i}$$

$$\bar{a}_z = \frac{1}{n} \sum_{i=1}^{n} a_{z,i}$$

$$\bar{\omega}_x = \frac{1}{n} \sum_{i=1}^{n} \omega_{x,i}$$

$$\bar{\omega}_y = \frac{1}{n} \sum_{i=1}^{n} \omega_{y,i}$$

$$\bar{\omega}_z = \frac{1}{n} \sum_{i=1}^{n} \omega_{z,i}$$

### 计算运动强度

1. 计算每个方向的加速度和角速度变化量：

$$\Delta a_x = a_{x} - \bar{a}_x$$

$$\Delta a_y = a_{y} - \bar{a}_y$$

$$\Delta a_z = a_{z} - \bar{a}_z$$

$$\Delta \omega_x = \omega_{x} - \bar{\omega}_x$$

$$\Delta \omega_y = \omega_{y} - \bar{\omega}_y$$

$$\Delta \omega_z = \omega_{z} - \bar{\omega}_z$$

2. 计算加速度和角速度的均方根（RMS）值：

$$\text{RMS加速度} = \sqrt{(\Delta a_x)^2 + (\Delta a_y)^2 + (\Delta a_z)^2}$$

$$\text{RMS角速度} = \sqrt{(\Delta \omega_x)^2 + (\Delta \omega_y)^2 + (\Delta \omega_z)^2}$$

### 运动强度到 MET 值的转换

将运动强度转换为 MET 值：

$$\text{MET} = \alpha \times \text{RMS加速度} + \beta$$

其中，\(\alpha\) 和 \(\beta\) 是假设的系数和基准值。

### 计算卡路里消耗

1. 计算每个时间段的持续时间：

$$\text{持续时间} = \frac{t_{\text{end}} - t_{\text{start}}}{3600}$$

2. 计算每个时间段的卡路里消耗：

$$\text{卡路里} = \text{MET} \times \text{体重(kg)} \times \text{持续时间(小时)}$$

3. 总卡路里消耗为所有时间段的卡路里消耗之和：

$$\text{总卡路里消耗} = \sum \text{卡路里}$$

### 计算 RER

计算静息能量需求（RER）,其中1.4是成年大猫的系数：

$$\text{RER} = 70 \times (\text{体重(kg)})^{0.75} \times 1.4$$


## 计算步骤

1. 读取数据：读取静止和运动数据。
2. 计算基线数据：计算静止状态下的基线数据。
3. 计算运动强度：根据基线数据计算运动强度。
4. 转换为 MET 值：将运动强度转换为 MET 值。
5. 计算 RER：根据猫咪的体重计算 RER。
6. 计算卡路里消耗：根据 MET 值和 RER 计算卡路里消耗。

## 代码实现(python)

```python
import json
import numpy as np
# 读取文件内容
def read_sensor_data(filepath):
    with open(filepath, 'r') as file:
        data = [json.loads(line) for line in file]
    return data

# 计算猫咪静止状态下的均值
def calculate_baseline(data):
    a_x = np.mean([d['a_x'] for d in data])
    a_y = np.mean([d['a_y'] for d in data])
    a_z = np.mean([d['a_z'] for d in data])
    omega_x = np.mean([d['omega_x'] for d in data])
    omega_y = np.mean([d['omega_y'] for d in data])
    omega_z = np.mean([d['omega_z'] for d in data])
    return {'a_x': a_x, 'a_y': a_y, 'a_z': a_z, 'omega_x': omega_x, 'omega_y': omega_y, 'omega_z': omega_z}

# 计算运动强度
def calculate_intensity(baseline, data):
    intensity = []
    for d in data:
        delta_a_x = d['a_x'] - baseline['a_x']
        delta_a_y = d['a_y'] - baseline['a_y']
        delta_a_z = d['a_z'] - baseline['a_z']
        delta_omega_x = d['omega_x'] - baseline['omega_x']
        delta_omega_y = d['omega_y'] - baseline['omega_y']
        delta_omega_z = d['omega_z'] - baseline['omega_z']
        
        rms_acceleration = np.sqrt(delta_a_x**2 + delta_a_y**2 + delta_a_z**2)
        rms_angular_velocity = np.sqrt(delta_omega_x**2 + delta_omega_y**2 + delta_omega_z**2)
        
        intensity.append({'timestamp': d['timestamp'], 'rms_acceleration': rms_acceleration, 'rms_angular_velocity': rms_angular_velocity})
    return intensity

# 运动强度到 MET 值的转换
def intensity_to_met(intensity):
    alpha = 0.1  # 假设的系数
    beta = 1.0  # 假设的基准值
    for i in intensity:
        i['met'] = alpha * i['rms_acceleration'] + beta
    return intensity


# 计算卡路里消耗
def calculate_calories_burned(intensity, weight_kg):
    total_calories = 0
    for i in range(len(intensity) - 1):
        start_time = intensity[i]['timestamp']
        end_time = intensity[i + 1]['timestamp']
        duration_hours = (end_time - start_time) / 3600.0
        met = intensity[i]['met']
        calories = met * weight_kg * duration_hours
        total_calories += calories
    return total_calories

# 计算 RER 这里取的系数为 1.4
def calculate_rer(weight_kg):
    return 70 * (weight_kg ** 0.75) * 1.4

# 计算运动数据的变化量
def calculate_motion_delta(baseline, motion_data):
    deltas = []
    for data in motion_data:
        delta = {
            'timestamp': data['timestamp'],
            'delta_a_x': data['a_x'] - baseline['a_x'],
            'delta_a_y': data['a_y'] - baseline['a_y'],
            'delta_a_z': data['a_z'] - baseline['a_z'],
            'delta_omega_x': data['omega_x'] - baseline['omega_x'],
            'delta_omega_y': data['omega_y'] - baseline['omega_y'],
            'delta_omega_z': data['omega_z'] - baseline['omega_z']
        }
        deltas.append(delta)
    return deltas


# 主程序
file_path_static = 'data/log.txt'
file_path_motion = 'data/motion_data.txt'

static_data = read_sensor_data(file_path_static)
motion_data = read_sensor_data(file_path_motion)

baseline = calculate_baseline(static_data)
intensity = calculate_intensity(baseline, motion_data)
intensity_with_met = intensity_to_met(intensity)

weight_kg = 5  # 猫咪的体重

# 计算 RER
rer = calculate_rer(weight_kg)
print(f"RER: {rer:.2f} kcal/day")

# 静息6轴数据
print(f"Baseline: {baseline}")

# 运动强度数据
# print(f"Intensity: {intensity}")
# print(f"Intensity with MET: {intensity_with_met}")

# 根据 静息的6轴数据以及计算的RER值，计算猫咪的卡路里消耗
total_calories = calculate_calories_burned(intensity_with_met, weight_kg)
print(f"Total calories burned: {total_calories:.2f} kcal")
```

其中txt数据格式示例:

静止:
```text
{"omega_z": -0.009272062, "a_z": -9.275469, "a_y": 1.64727, "a_x": 3.682414, "omega_x": 0.04908739, "timestamp": 1724802141, "omega_y": 0.1385355}
{"omega_z": -0.009817477, "a_z": -9.306594, "a_y": 1.541921, "a_x": 3.708751, "omega_x": 0.05726862, "timestamp": 1724802151, "omega_y": 0.1488984}
{"omega_z": -0.009817477, "a_z": -9.277863, "a_y": 1.577835, "a_x": 3.737482, "omega_x": 0.04745114, "timestamp": 1724802161, "omega_y": 0.1379901}
...
```

运动:
```text
{"omega_z": 0.2765256, "a_z": 3.634528, "a_y": 8.808582, "a_x": -4.398305, "omega_x": 0.2421644, "timestamp": 1724887178, "omega_y": 0.9179342}
{"omega_z": -0.1843504, "a_z": 3.560305, "a_y": 7.48933, "a_x": -5.640941, "omega_x": 0.4292419, "timestamp": 1724887229, "omega_y": -0.08617563}
{"omega_z": 0.2574361, "a_z": 3.466928, "a_y": 7.012867, "a_x": -7.585102, "omega_x": -0.4472406, "timestamp": 1724887239, "omega_y": -0.3839725}
...
```

## 参考

[^1]:[https://www.aaha.org/globalassets/02-guidelines/2021-nutrition-and-weight-management/resourcepdfs/nutritiongl_box1.pdf](https://www.aaha.org/globalassets/02-guidelines/2021-nutrition-and-weight-management/resourcepdfs/nutritiongl_box1.pdf)
[^2]:[https://petnutritionalliance.org/site/wp-content/uploads/2017/05/MER.RER_.PNA_.pdf](https://petnutritionalliance.org/site/wp-content/uploads/2017/05/MER.RER_.PNA_.pdf)
[^3]:[https://www.bosscat.com.tw/post/1330/%E6%95%99%E4%BD%A0%E5%A6%82%E4%BD%95%E8%A8%88%E7%AE%97%E8%B2%93%E5%92%AA%E7%86%B1%E9%87%8F%E9%9C%80%E6%B1%82/#%E5%9F%BA%E7%A4%8E%E7%86%B1%E9%87%8F%E9%9C%80%E6%B1%82%E5%8F%88%E5%8F%AB%E3%80%8CRER%E3%80%8D%EF%BC%88Resting_Energy_Requirement](https://www.bosscat.com.tw/post/1330/%E6%95%99%E4%BD%A0%E5%A6%82%E4%BD%95%E8%A8%88%E7%AE%97%E8%B2%93%E5%92%AA%E7%86%B1%E9%87%8F%E9%9C%80%E6%B1%82/#%E5%9F%BA%E7%A4%8E%E7%86%B1%E9%87%8F%E9%9C%80%E6%B1%82%E5%8F%88%E5%8F%AB%E3%80%8CRER%E3%80%8D%EF%BC%88Resting_Energy_Requirement)
[^4]:[https://www.codymaomao.com/zh-TW/blogs/%E7%87%9F%E9%A4%8A%E5%B8%AB%E9%83%A8%E8%90%BD%E6%A0%BC/120686](https://www.codymaomao.com/zh-TW/blogs/%E7%87%9F%E9%A4%8A%E5%B8%AB%E9%83%A8%E8%90%BD%E6%A0%BC/120686)
[^5]:[https://www.163.com/dy/article/FN09ABB70549F6LA.html](https://www.163.com/dy/article/FN09ABB70549F6LA.html)