# 5.3 时间效率与空间效率的平衡

## 面试题34 丑数
> 要求：只含有2、3、5因子的数是丑数，求第1500个丑数
>
> 思路: 按顺序保存已知的丑数，下一个是已知丑数中某三个数乘以2，3，5中的最小值

```python
def get_ugly(n):
    ugly = [1]
    t2, t3, t5 = 0, 0, 0  # 分别标记乘以2，3，5的丑数索引
    while n > 1:
        while ugly[t2] * 2 <= ugly[-1]:
            t2 += 1
        while ugly[t3] * 3 <= ugly[-1]:
            t3 += 1
        while ugly[t5] * 5 <= ugly[-1]:
            t5 += 1
        ugly.append(min([ugly[t2]*2, ugly[t3]*3, ugly[t5]*5]))
        n -= 1
    return ugly[-1](''.join([str(num) for num in sorted(nums, cmp=cmp)]))
```

## 面试题35 第一个只出现一次的字符
> 要求：求字符串中第一个只出现一次的字符
>
> 思路: 使用两个hash，一个记录每个字符穿线的次数，另一个记录每个字符第一次出现的位置

```python
def first_not_repeating_char(string):
    if not string:
        return -1
    count = {}
    loc = {}
    for k, s in enumerate(string):
        count[s] = count[s] + 1 if count.get(s) else 1
        loc[s] = loc[s] if loc.get(s) else k
    ret = float('inf')
    for k in loc.keys():
        if count.get(k) == 1 and loc[k] < ret:
            ret = loc[k]
    return ret
```

## 面试题36 数组中的逆序对

## 面试题37 两个链表的第一个公共结点