---
layout:     post
title:      动态规划 例题四、 最长回文字符串
category: algorithmtree
tags: [algorithmtree]
excerpt: 动态规划
---


动态规划 例题四、 最长回文字符串
=======

[最长回文子串](https://leetcode-cn.com/explore/interview/card/tencent/221/array-and-strings/896/)

描述
-------

给定一个字符串 s，找到 s 中最长的回文子串。你可以假设 s 的最大长度为1000。

示例 1：

输入: "babad"

输出: "bab"

注意: "aba"也是一个有效答案。

示例 2：

输入: "cbbd"

输出: "bb"

分析
----------

1、两种情况： 单回文 和 双回文 形式；

### 动态规划思路

1、状态： maxLen(n) 下标n为中心点的最长回文字符串长度。

    那么：

```htnl
        单回文：
        left = right = n;
        while(left >= 0 && right < length && arr[left] == arr[right]) {
            maxLen(n) += 1;
        }

        双回文：
        left = n;
        right = n + 1;
        while(left >= 0 && right < length && arr[left] == arr[right]) {
            maxLen(n) += 1;
        }
```

2、是否可用动态规划？

    1、最优子结构符合。

    2、无后效性也符合。

代码实现
----------

1、先按照以上状态找到每个下标对应的最长单回文和双回文的长度。

2、枚举最长的即可。

3、具体细节不必考虑， 比如一个字符是不是回文，空怎么算，这些都是细节，不是思想


ruby代码：

```ruby
# @param {String} s
# @return {String}
def longest_palindrome(s)
    if s.empty?
        return ""
    elsif s.length == 1
        return s
    end
    
    single_length = []
    double_length = []
    
    #1 初始化回文长度为0
    (0..s.length).each do |index|
        single_length[index] = 0
        double_length[index] = 0
    end
    
    #以每个字符为中间值得最大回文字符串长度(单回文，或者双回文)
    (1..s.length - 1).each do |index|
        single_index = index
        double_index = index
        
        #单回文
        (single_index..s.length).each do |index1|
            abs = index1 - index
            left = index - abs - 1
            rigth = index + abs + 1
            
            if s[left].eql?(s[rigth]) && left >= 0 && rigth < s.length
                single_length[index] += 1
                left -= 1
                rigth += 1
            else
                break
            end
        end
    
        #双回文
        (double_index..s.length).each do |index2|
            abs = index2 - index
            left = index - abs - 1
            right = index + abs
            if s[left].eql?(s[right]) && left >= 0 && right < s.length
                double_length[left] += 1
                left -= 1
                right += 1
            else
                break
            end
        end
    end
    
    single_max = single_length.sort.last
    single_index = single_length.index(single_max)
    double_max = double_length.sort.last
    double_index = double_length.index(double_max)
    
    
    
    res = single_max > double_max ? s[single_index - single_max..single_index + single_max] :
                            s[double_index - double_max + 1, double_index + double_max]
    
    if res.empty?
        s[0]
    else
        res
    end
    #return [single_max, single_index, double_max, double_index]
end
```

### 动态规划的另一种实现

```html
f[i][j] 表示从i到j是否是回文。
    f[i+1][j-1] 是回文 并且 a[i] == a[j]  就是回文
    a[i] != a[j]  就不是回文。
```

但是循环条件很麻烦，因为要循环i和j，不如中心点好写，不过思路也不错。都是 枚举 + 动归

复杂度都是n^2