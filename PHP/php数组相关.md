
* 计算数组的交集

```
array array_intersect_assoc()    //返回键值都相同的数组
array array_intersect()          //返回多个数组中值相同的数组
```

* array_merge和 + 的区别
```
//使用array_merge()合并两个数组时，当数组中包含数字键时，合并的数组会自动重新编号
//而使用“+”合并数组时键名不会改变。
//因此在很多时候我们不希望改变数组的键名时，应该使用“+”来合并两个数组：$arr = $arr1 + $arr2;
```


