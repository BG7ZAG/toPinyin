# toPinyin
uniapp 文字汉字一键转拼音，转简写，转首字母 插件改进版 原作者: lieft@qq.com https://ext.dcloud.net.cn/plugin?id=3294

# 1、引入js
```
import toPinyin from "./toPinyin"
```

# 2、转拼音
```
toPinyin.chineseToPinYin('你好')
```
输出

NiHao

# 3、转首字母
```
toPinyin.chineseToInitials(toPinyin.chineseToPinYin('你好'))
```
或者
```
toPinyin.chineseToInitials('NiHao')
```
输出

NH