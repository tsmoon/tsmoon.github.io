---
layout: post
title: "学习天气Demo笔记"
date: 2014-03-06 20:07:03 +0800
comments: true
categories: 
---


###学习天气Demo
[教程地址](http://sjpsega.com/blog/2014/02/11/yi--ios-7-best-practices-part-1/)

####使用MTLModel
######作用将Json转化为Objc对象,使用方法
1. 导入头文件Mantle.h
2. 超类继承MTLModel,并实现协议MTLJSONSerializing>
3. json字段到ObjC字段映射对应,实现静态方法+(NSDictionary*) JSONKeyPathsByPropertyKey

```
+(NSDictionary*) JSONKeyPathsByPropertyKey{
    return @{
             @"date": @"dt",
             @"locationName": @"name",
             @"humidity": @"main.humidity",
             @"temperature": @"main.temp",
             @"tempHigh": @"main.temp_max",
             @"tempLow": @"main.temp_min",
             @"sunrise": @"sys.sunrise",
             @"sunset": @"sys.sunset",
             @"conditionDescription": @"weather.description",
             @"condition": @"weather.main",
             @"icon": @"weather.icon",
             @"windBearing": @"wind.deg",
             @"windSpeed": @"wind.speed"
             };
}
```

4. 若属性字段需要转换,定义静态"属性名+JSONTransformer"方法,此方法用来对特定属性名称进行转化(若多层级中属性名相同,但转换不同,如何处理?)

```
+ (NSValueTransformer *)dateJSONTransformer {
    // 1
    return [MTLValueTransformer reversibleTransformerWithForwardBlock:^(NSString *str) {
        return [NSDate dateWithTimeIntervalSince1970:str.floatValue];
    } reverseBlock:^(NSDate *date) {
        return [NSString stringWithFormat:@"%f",[date timeIntervalSince1970]];
    }];
}

```

对JSON数组的示例

```
+ (NSValueTransformer *)conditionDescriptionJSONTransformer {
    return [MTLValueTransformer reversibleTransformerWithForwardBlock:^(NSArray *values) {
        return [values firstObject];
    } reverseBlock:^(NSString *str) {
        return @[str];
    }];
}

```
