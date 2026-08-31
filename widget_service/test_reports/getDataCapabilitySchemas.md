# getDataCapabilitySchemas 测试报告

- 生成时间：2026-07-10T02:03:51.678293+00:00
- 接口名：`getDataCapabilitySchemas`
- WebSocket path：`/api/v1/ws/tools/getDataCapabilitySchemas`
- 请求协议：content/deviceInfo/session 外层包络
- requestId：`7676c2c8-a6d3-413c-8074-c62ed30db8de&2`
- 消息状态：`result`
- 业务状态：`success`

## 入参

```json
{
  "content": {
    "odid": "5e64f3e9-0a80-d719-d689-3c36eca5eeb6",
    "bundleName": "com.omega_w_0823.hmservice",
    "dataCapabilityIds": [
      "ViewWeather"
    ]
  },
  "deviceInfo": {
    "countryCode": "CN",
    "deviceFormation": "HDSpeaker",
    "deviceType": 0,
    "locale": "zh-CN",
    "phoneType": "CLS-AL30",
    "prdVer": "11.7.5.205",
    "sysVer": "EmotionUI_9.0.0",
    "romVersion": "CLS-AL30 6.0.0.328",
    "time": "20260707115342975"
  },
  "pagination": {
    "limit": 5,
    "start": ""
  },
  "session": {
    "interactionId": "2",
    "isNew": false,
    "sessionId": "7676c2c8-a6d3-413c-8074-c62ed30db8de"
  },
  "userAuth": {
    "user": {
      "userId": "test-user-001"
    }
  },
  "utterance": {
    "original": "",
    "type": "text"
  },
  "version": "1.0",
  "bundleName": "com.omega_w_0823.hmservice"
}
```

## 出参

```json
{
  "errorCode": "0",
  "errorMessage": "",
  "reply": {
    "streamInfo": {
      "streamContent": "type='result' tool='getDataCapabilitySchemas' operation='getDataCapabilitySchemas' requestId='7676c2c8-a6d3-413c-8074-c62ed30db8de&2' data={'dataCapabilities': [{'id': 'ViewWeather', 'type': 'data', 'description': '查询指定地区的当前天气与未来数日天气预报。如果不能推断出用户的地区名，则需要追问用户提供。注意，当前不支持查询国外的天气。', 'descriptionForLLM': '', 'inputSchema': {'type': 'object', 'properties': {'districtName': {'type': 'string', 'minLength': 1, 'description': \"区县名，如'滨江区'。可选。\"}, 'prefectureName': {'type': 'string', 'minLength': 1, 'description': \"城市名，如'杭州市'。若不能根据用户query或上下文来推断出是哪个城市，则需要向用户发起追问，明确城市名。注意，部分区县对应多个城市，此时也需要让用户明确。\"}, 'forecastDays': {'type': 'integer', 'minimum': 1, 'maximum': 5, 'description': '返回预报天数，支持1至5天；可选，不传时默认返回3天。'}}, 'required': ['prefectureName']}, 'outputSchema': {'type': 'object', 'description': '适合桌面卡片展示的标准化天气概要。current 是固定对象，daily 是数量由 forecastDays 决定的数组。', 'properties': {'location': {'type': 'object', 'description': '实际查询成功的地区。', 'properties': {'cityCode': {'type': 'string', 'description': '城市代码，如60814代表青浦区', 'sampleValue': '60814'}, 'districtName': {'type': 'string', 'description': '区或县名称', 'sampleValue': '青浦区'}, 'prefectureName': {'type': 'string', 'description': '城市名称', 'sampleValue': '上海市'}}}, 'current': {'type': 'object', 'description': '当日天气实况', 'properties': {'temperatureC': {'type': 'number', 'description': '当前温度的纯数值，单位为摄氏度，返回值不包含单位。若直接用于文本展示，必须在数值后追加“℃”；优先使用 temperatureText。', 'sampleValue': 29, 'displayUnits': ['℃'], 'unitIncluded': False}, 'temperatureText': {'type': 'string', 'description': '可直接显示的当前温度文本，已包含“℃”单位；展示时不得再次追加温度单位。例如“29℃”。', 'sampleValue': '29℃', 'displayUnits': ['℃'], 'unitIncluded': True}, 'condition': {'type': 'string', 'description': '当前天气现象，例如“阴”“多云”“小雨”。', 'sampleValue': '多云'}, 'feelsLikeC': {'type': 'number', 'description': '当前体感温度的纯数值，单位为摄氏度，返回值不包含单位。若直接用于文本展示，必须在数值后追加“℃”。', 'sampleValue': 31, 'displayUnits': ['℃'], 'unitIncluded': False}, 'humidityPercent': {'type': 'number', 'minimum': 0, 'maximum': 100, 'description': '当前相对湿度的纯数值百分比，取值范围为 0 到 100，返回值不包含“%”。若直接用于文本展示，必须在数值后追加“%”。', 'sampleValue': 68, 'displayUnits': ['%'], 'unitIncluded': False}, 'airQuality': {'type': 'string', 'description': '当前空气质量等级，例如“优”“良”。', 'sampleValue': '良'}, 'windDirection': {'type': 'string', 'description': '当前风向。', 'sampleValue': '东南风'}, 'windLevel': {'type': 'integer', 'minimum': 0, 'description': '当前风力等级的纯整数，返回值不包含“级”。若直接用于文本展示，必须在数值后追加“级”。', 'sampleValue': 2, 'displayUnits': ['级'], 'unitIncluded': False}, 'uvIndex': {'type': 'string', 'description': '当前紫外线等级，例如“弱”“中等”“强”。', 'sampleValue': '中等'}, 'coldLevel': {'type': 'string', 'description': '感冒指数。', 'sampleValue': '低'}, 'alertLevel': {'type': 'string', 'description': '预警信息。', 'sampleValue': ''}}}, 'daily': {'type': 'array', 'description': '从今天开始按日期升序排列的每日预报。', 'items': {'type': 'object', 'properties': {'date': {'type': 'string', 'description': '预报日期，来源于 day_time。', 'sampleValue': '2026-08-06'}, 'weekday': {'type': 'string', 'description': '星期文本，例如“星期日”。', 'sampleValue': '星期四'}, 'condition': {'type': 'string', 'description': '白天天气现象，来源于weather_icon。', 'sampleValue': '多云'}, 'temperatureRangeText': {'type': 'string', 'description': '可直接显示的最低温与最高温范围文本，每个温度值均已包含“℃”单位；展示时不得再次追加温度单位。例如“25℃ / 32℃”。', 'sampleValue': '25℃ / 32℃', 'displayUnits': ['℃'], 'unitIncluded': True}, 'rainProbabilityPercent': {'type': 'string', 'description': '可直接显示的白天降雨概率文本，已包含“%”单位；展示时不得再次追加“%”。例如“20%”。', 'sampleValue': '20%', 'displayUnits': ['%'], 'unitIncluded': True}, 'airQuality': {'type': 'string', 'description': '当天空气质量等级。', 'sampleValue': '良'}, 'uvIndex': {'type': 'string', 'description': '当天紫外线等级。', 'sampleValue': '中等'}, 'coldLevel': {'type': 'string', 'description': '感冒指数。', 'sampleValue': '低'}}}}, 'updatedAt': {'type': 'string', 'description': '端侧完成天气查询和归一化的时间。如：2026-06-14 15:30', 'sampleValue': '2026-08-06 09:00'}}}, 'defaultWriteResultTo': '/data/weather', 'dataModelSkeleton': {}, 'dependencies': {'requiredPackages': [{'packageName': 'com.huawei.hmsapp.totemweather'}]}}], 'missingCapabilityIds': []} status='success' errorCode='' error={}",
      "streamingTextId": "7676c2c8-a6d3-413c-8074-c62ed30db8de&2",
      "streamType": "final",
      "textType": "plainText"
    },
    "items": []
  }
}
```
