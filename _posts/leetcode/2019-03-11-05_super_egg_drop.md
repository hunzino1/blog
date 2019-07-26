---
layout:     post
title:      leetcod(005) - 鸡蛋掉落
category: better
tags: [better]
excerpt: 坚持这件小事，20190311打卡。
---


[合并两个有序数组](https://leetcode-cn.com/explore/interview/card/top-interview-quesitons-in-2018/261/before-you-start/1109/)
=======

一、题目描述
----------

### 1、English版本

<div class="question-description__3U1T"><div class="translation-tool__3Ffj"><span class="" data-toggle="tooltip" data-placement="left" data-original-title="显示中文" aria-hidden="true" style="cursor: pointer;"><div class="switch-base__1Zql" data-on="true"><div class="toggle__3ZBJ"></div></div></span></div><div><p>You are given <code>K</code> eggs, and you have access to a building with <code>N</code> floors from <code>1</code> to <code>N</code>.&nbsp;</p>

<p>Each egg is identical in function, and if an egg breaks, you cannot drop it&nbsp;again.</p>

<p>You know that there exists a floor <code>F</code> with <code>0 &lt;= F &lt;= N</code> such that any egg dropped at a floor higher than <code>F</code> will break, and any egg dropped at or below floor <code>F</code> will not break.</p>

<p>Each <em>move</em>, you may take an egg (if you have an unbroken one) and drop it from any floor <code>X</code> (with&nbsp;<code>1 &lt;= X &lt;= N</code>).&nbsp;</p>

<p>Your goal is to know&nbsp;<strong>with certainty</strong>&nbsp;what the value of <code>F</code> is.</p>

<p>What is the minimum number of moves that you need to know with certainty&nbsp;what <code>F</code> is, regardless of the initial value of <code>F</code>?</p>

<p>&nbsp;</p>

<ol>
</ol>

<div>
<p><strong>Example 1:</strong></p>

<pre><strong>Input: </strong>K = <span id="example-input-1-1">1</span>, N = <span id="example-input-1-2">2</span>
<strong>Output: </strong><span id="example-output-1">2</span>
<strong>Explanation: </strong>
Drop the egg from floor 1.  If it breaks, we know with certainty that F = 0.
Otherwise, drop the egg from floor 2.  If it breaks, we know with certainty that F = 1.
If it didn't break, then we know with certainty F = 2.
Hence, we needed 2 moves in the worst case to know what F is with certainty.
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre><strong>Input: </strong>K = <span id="example-input-2-1">2</span>, N = 6
<strong>Output: </strong><span id="example-output-2">3</span>
</pre>

<div>
<p><strong>Example 3:</strong></p>

<pre><strong>Input: </strong>K = <span id="example-input-3-1">3</span>, N = <span id="example-input-3-2">14</span>
<strong>Output: </strong><span id="example-output-3">4</span>
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
	<li><code>1 &lt;= K &lt;= 100</code></li>
	<li><code>1 &lt;= N &lt;= 10000</code></li>
</ol>
</div>
</div>
</div>
</div></div>

### 2、 中文版

<div class="question-detail"><div class="question-description__3U1T"><div class="translation-tool__3Ffj"><span class="" data-toggle="tooltip" data-placement="left" data-original-title="显示英文" aria-hidden="true" style="cursor: pointer;"><div class="switch-base__1Zql" data-on="false"><div class="toggle__3ZBJ"></div></div></span></div><div><p>你将获得&nbsp;<code>K</code>&nbsp;个鸡蛋，并可以使用一栋从&nbsp;<code>1</code>&nbsp;到&nbsp;<code>N</code>&nbsp;&nbsp;共有 <code>N</code>&nbsp;层楼的建筑。</p>

<p>每个蛋的功能都是一样的，如果一个蛋碎了，你就不能再把它掉下去。</p>

<p>你知道存在楼层&nbsp;<code>F</code> ，满足&nbsp;<code>0 &lt;= F &lt;= N</code> 任何从高于 <code>F</code>&nbsp;的楼层落下的鸡蛋都会碎，从&nbsp;<code>F</code>&nbsp;楼层或比它低的楼层落下的鸡蛋都不会破。</p>

<p>每次<em>移动</em>，你可以取一个鸡蛋（如果你有完整的鸡蛋）并把它从任一楼层&nbsp;<code>X</code>&nbsp;扔下（满足&nbsp;<code>1 &lt;= X &lt;= N</code>）。</p>

<p>你的目标是<strong>确切地</strong>知道 <code>F</code> 的值是多少。</p>

<p>无论 <code>F</code> 的初始值如何，你确定 <code>F</code> 的值的最小移动次数是多少？</p>

<p>&nbsp;</p>

<ol>
</ol>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>K = 1, N = 2
<strong>输出：</strong>2
<strong>解释：</strong>
鸡蛋从 1 楼掉落。如果它碎了，我们肯定知道 F = 0 。
否则，鸡蛋从 2 楼掉落。如果它碎了，我们肯定知道 F = 1 。
如果它没碎，那么我们肯定知道 F = 2 。
因此，在最坏的情况下我们需要移动 2 次以确定 F 是多少。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>K = 2, N = 6
<strong>输出：</strong>3
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>K = 3, N = 14
<strong>输出：</strong>4
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= K &lt;= 100</code></li>
	<li><code>1 &lt;= N &lt;= 10000</code></li>
</ol>
</div></div></div>

二、ruby方案
----------

之前的做法陷入了思路误区，其实还是没有理解题意，蛋碎还是不碎的判断是怎么判断的？（cry、cry）

不过思考方向错误还是欠缺经验。

最小移动次数，很明显是最优解，应该向着动态规划思考；

而我是用了2分，这个并不是能保证最优解的方法；

```ruby
```

三、python方案
-------------

> 同上

```python
```

四、java方案
----------

```java
null
```

五、经典解法，算法思想
----------

### 动态规划思路1

```html

首先明确一点，动态规划是取的最优解，而本题取得是最坏情况下尝试的次数，所以应用到动态规划上取得应该是max，而非min。

记k是鸡蛋个数， n是楼层数；

1、简单情形

鸡蛋数 k = 0 或者 楼层数 n = 0, 那么最坏的情况就是尝试0次；
若鸡蛋数 k = 1, 对于n层楼来说最坏情况是尝试n次， 因为可能在n层时鸡蛋才碎；

2、状态转换公式

记f(k, n) 表示k个鸡蛋n层楼所需要的最坏尝试次数；

假设鸡蛋从第i层扔下，有两种情况：

（1） 蛋碎， 鸡蛋剩余k-1个，而此时需要考虑i层以下的楼层(0...i)，因为i以上肯定会碎。 故问题变成了 f(k-1, i-1)
（2） 不碎， 鸡蛋剩余k个， 此时需要考虑i层以上的楼层(i+1..n), 故问题变成了 f(k, n - i), (这里都是楼层数，而不是楼高，剩余需排查的楼层数就是n - i)

对于以上两种情况，最坏应该取最大值， 故得到一下状态转移公式：

f(k, n) = 1 + min{ max( f(k-1, i-1), f(k, n-i) ) } (1 <= i <= n)

初始状态： 
f(0, n) = 0
f(k, 0) = 0
f(1, n) = n

如下递归模式会超出时间限制，需要使用记忆数组。
```

```ruby
# 超出时间限制
# @param {Integer} k
# @param {Integer} n
# @return {Integer}
def super_egg_drop(k, n)
  if k == 0 || n == 0
    return 0
  end

  if k == 1
    return n
  end

  min = -1
  i = 1
  while i <= n do
    breaken = super_egg_drop(k-1, i-1)
    unbreak = super_egg_drop(k, n-i)
    min_time = (breaken > unbreak ? breaken : unbreak) + 1
    if min > min_time || min < 0
      min = min_time
    end
    i += 1
  end

  min
end


# 非递归测试内部错误
# @param {Integer} k
# @param {Integer} n
# @return {Integer}
def super_egg_drop(k, n)
  if k == 0 || n == 0
    return 0
  end

  if k == 1
    return n
  end

  drop_eggs = Array.new(k+1, Array.new(n+1, 0))
  (1..n).to_a.each do |index|
    drop_eggs[1][index] = index
  end

  (1..n).to_a.each do |floor|
    (2..k).to_a.each do |egg|
      min = drop_eggs[egg-1][floor]
      (1..floor).to_a.each do |i|
        breaken = drop_eggs[egg-1][i-1]
        unbreak = drop_eggs[egg][floor-i]
        cur_min = (breaken > unbreak ? breaken : unbreak) + 1
        if cur_min < min
          min = cur_min
        end
      end

      drop_eggs[egg][floor] = min
    end
  end

  drop_eggs[k][n]
end
```

### 动态规划思路2

```html
1、状态转移方程

记 f(k, step) k是鸡蛋个数， step表示尝试的次数， f(k, step) 表示k个鸡蛋，尝试step次最多能确认多少层楼。 显然step <= n n为楼层数。

(1) 初始状态
鸡蛋个数为0的时候  f(0, step) = 0
尝试次数为1是，判断最高楼层最多是1层 f(j, 1) = 1 j >= 1

(2) 转移方程
f(i, j) 分两种情况：
  (1) 鸡蛋碎掉，尝试次数减一，鸡蛋减一，我们可以通过i - 1个鸡蛋和 j - 1次尝试找到最高不会碎掉的楼层。故最高楼层为 f(i-1, j-1)
  (2) 鸡蛋不碎，尝试次数减一，          可以继续向上检查楼层，所以最高楼层数应该是 f(i-1, j-1) + f(i, j-1) + 1;  蛋碎检测的最高楼层数 + 1(当前楼层) + f(i, j-1)

因此，这次扔鸡蛋，我们最多能测出 dp[k-1][m-1] (摔碎时能确定的层数) + dp[k][m-1] (没摔碎时能确定的层数) + 1 (本层) 层的结果。

故 f(i, j) = n;  知道最小的j满足楼层为n， j即为所求。
状态转移方程： f(i,j) = f(i−1,j−1) + f(i−1,j) + 1
```
