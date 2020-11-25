# toPinyin
# uniapp 文字汉字一键转拼音，转简写，转首字母 
封装了下使用方法，原作者: lieft@qq.com https://ext.dcloud.net.cn/plugin?id=3294

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

提供个一位数组转成按照首字母排序的方法(在 `utils.js` 文件中)：
```
import toPinyin from "./toPinyin";

/**
 * 根据拼音首字母筛选排序分组，注意原数组需要筛选排序的字段是name，如不是自行修改
 * @param {Array} arr 原数组
 */
export function getGroupByPinyin(arr) {
    // 获取A-Z字母数组
    let keys = [...Array(26).keys()].map((i) => String.fromCharCode(i + 65));
    
    // 原数组添加py字段，其中name字段注意修改
    arr = arr.map((n) => ({
        ...n,
        py: toPinyin.chineseToInitials(
            toPinyin.chineseToPinYin(n.name.substr(0, 1))
        ),
    }));

    let group = [];
    for (const i of keys) {
        // 新数组一级结构，可自行修改
        let item = {
            name: i,
            value: [],
        };
        for (const j of arr) {
            if (j.py === i) {
                item.value.push(j);
            }
        }
        if (item.value.length > 0) {
            // 注意name字段
            item.value.sort((a, b) => a.name.localeCompare(b.name));
            group.push(item);
        }
    }
    return group;
}
```