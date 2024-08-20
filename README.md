# interview php

## 产品包装信息
长: 68 cm

宽: 70 cm

高: 60 cm

重量: 23 kg

## 规则
### 计算
- 1 in（英寸）= 2.54 cm
- 1 LB（磅）= 0.454 kg
- 长度和重量转换时需要向上取整
- 围长 = 最长边 + (次长边 + 第三边) * 2 （单位 in）
- 体积重 = 最长边 * 次长边 * 第三边 / 体积重基数 （结果向上取整）
- 体积重基数：250
- 实重 = 产品重量（LB）和体积重之间取最大值

### 类型定义
- out-space： （实重大于150）或（最长边大于108）或（围长大于165）
- oversize：（围长大于130，小于等于165）或（最长边大于等于96小于108）
- AHS
  - weight: 实重大于50，小于等于150
  - Size: （围长大于105）或（最长边大于等于48，最长边小于108）或（次长边大于等于30）
  - 若两种类型都符合，则都输出
- 当满足out-space类型，不再判断oversize或AHS；当满足oversize，不再判断AHS；
- 关系：out-space > oversize > AHS

## 要求
请实现类型的输出
```php
class Main()
{
    public function test(float $length, float $width, float $height, float $weight): array
    {
        
    }
}

$obj = new Main();
var_dump($obj->test(68, 70, 60, 23));
```
例如:
- 输入[68, 70, 60, 23], 输出[weight, size]

> 作答结果请发给 HR 
