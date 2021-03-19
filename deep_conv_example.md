# （深度）转化模型的样本方案

一个`转化`的格式如下所示

## 转化与样本的关系
```protobuf
message Conv {
    ConvId convId = 1;
    int64 conv_time = 2;
    float conv_value = 3;
    repeated int64 conv_item_id = 4;

    repeated Attr attr = 101;
}
```

一个训练样本格式为：

```protobuf
message Meta {
    int64 user_id = 1;
    int64 item_id = 2;
    // ...
    repeated Conv conv = 20;
}
message Example {
    Meta meta = 1;
    repeated float label = 2;
    repeated int64 feature_id = 3;
    repeated Embedding embedding = 4;
}
```

每个训练样本包括若干个Meta

## 对比不同的item_type

在Meta的定义中就有item_type，表示的被推荐内容的类型。这个类型的划分是根据
