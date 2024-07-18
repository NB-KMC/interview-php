# interview php

```php

/**
 * 请重构以下代码
 */
protected function newGetCode($storehouse, $info, $config)
{
    if ($storehouse['us_area'] == StorehouseConstant::US_WEST) {
        if (in_array($info['type'], [3, 4])) {
            // oversize or out-space
            $code = $config['US_WEST']['normal']['oversize'] ?? 'FEDEXOVERSIZE';
        } elseif ($info['weight'] > 70) {
            $code = $config['US_WEST']['normal']['ahs_weight'] ?? 'FEDEX-OS-GROUND';
        } elseif ($info['weight'] >= 47 && $info['weight'] <= 70) {
            // AHS Weight
            $code = $config['US_WEST']['normal']['weight_range'] ?? 'FEDEX-WEIGHT-HOME';
        } elseif ($info['type'] == 1) {
            // AHS DIM
            $code = $config['US_WEST']['normal']['ahs'] ?? 'FEDEX-WEIGHT-HOME';
        } elseif ($info['weight'] >= 16 && $info['weight'] <= 46) {
            // normal
            $code = $config['US_WEST']['normal']['normal'] ?? 'FEDEX-HOMEDELIVERY';
        } else {
            // UPS
            $code = $config['US_WEST']['normal']['ups'] ?? 'UPSGROUND';
        }
    } elseif ($storehouse['us_area'] == StorehouseConstant::US_SOUTH) {
        if ($storehouse['name'] == 'KC-GA2') {
            if (in_array($info['type'], [3, 4])) {
                // oversize or out-space
                $code = $config['US_SOUTH']['GA']['oversize'] ?? 'FEDEXOVERSIZE';
            } elseif ($info['weight'] > 70) {
                $code = $config['US_SOUTH']['GA']['ahs_weight'] ?? 'GASA-FEDEX-GROUND';
            } elseif ($info['weight'] >= 47 && $info['weight'] <= 70) {
                // AHS Weight
                $code = $config['US_SOUTH']['GA']['weight_range'] ?? 'GASA-FEDEX-HD';
            } elseif ($info['type'] == 1) {
                // AHS DIM
                $code = $config['US_SOUTH']['GA']['ahs'] ?? 'GASA-FEDEX-HD';
            } elseif ($info['weight'] >= 16 && $info['weight'] <= 46) {
                // normal
                $code = $config['US_SOUTH']['GA']['normal'] ?? 'FEDEX-HOMEDELIVERY';
            } else {
                // UPS
                $code = $config['US_SOUTH']['GA']['ups'] ?? 'UPSGROUND';
            }
        } else {
            //1.实重在0-70lbs且无oversize
            if ($info['weight'] <= 70 && !in_array($info['type'], [3])) {  // oversize
                $code = $config['US_SOUTH']['normal']['oversize'] ?? 'GANW-FEDEX-HD';
                //1.0-70lbs且有oversize 2.70lbs以上全部
            } else {
                $code = $config['US_SOUTH']['normal']['normal'] ?? 'GANW-FEDEX-GROUND';
            }
        }
    } else {
        if (in_array($info['type'], [3, 4])) {
            // oversize or out-space
            $code = $config['US_EAST']['normal']['oversize'] ?? 'FEDEXOVERSIZE';
        } elseif ($info['weight'] > 70) {
            $code = $config['US_EAST']['normal']['ahs_weight'] ?? 'FEDEX-GROUND';
        } elseif ($info['weight'] >= 47 && $info['weight'] <= 70) {
            // AHS Weight
            $code = $config['US_EAST']['normal']['weight_range'] ?? 'FEDEX-HD-NJ';
        } elseif ($info['type'] == 1) {
            // AHS DIM
            $code = $config['US_EAST']['normal']['ahs'] ?? 'FEDEX-HD-NJ';
        } elseif ($info['weight'] >= 16 && $info['weight'] <= 46) {
            // normal
            $code = $config['US_EAST']['normal']['normal'] ?? 'FEDEX-HOMEDELIVERY';
        } else {
            // UPS
            $code = $config['US_EAST']['normal']['ups'] ?? 'UPSGROUND';
        }
    }

    return $code;
}


/**
 * 最引以为傲的一段代码（如有必要请说明代码实现了什么功能）
 */


/**
 * 经常浏览的技术网站，以及最近学习到的新知识
 */


```

> 作答结果请保存至 gist ，然后将其网址评论至本仓库的名为 gist 的 issue 下，最后记得将 github 用户名告知 HR 或面试官
