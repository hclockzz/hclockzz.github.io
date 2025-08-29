---
title: Leetcode: 数组最大值问题总结
date: 2025-08-28 22:35:26 -0000
categories: [Leetcode, AI-gen-article]
tags: [leetcode, AI-gen-article]
---


🗺️ 最大值问题常见分类

1. 基础最大值（全局最大/最小）
	•	题目例子
	•	LeetCode 53: Maximum Subarray
	•	变种描述
	•	给一个数组，找 连续子数组的最大和。
	•	解法
	•	动态规划 / Kadane 算法：
	•	dp[i] = max(nums[i], dp[i-1] + nums[i])
	•	时间 O(n)，空间 O(1)。

⸻

2. 固定长度子数组的最大值
	•	题目例子
	•	LeetCode 643: Maximum Average Subarray I
	•	LeetCode 209: Minimum Size Subarray Sum（虽然是最小长度，但同类技巧）
	•	解法
	•	滑动窗口：
	•	用一个窗口大小 k 维护子数组和，移动时更新。
	•	时间 O(n)，空间 O(1)。

⸻

3. 可变长度子数组最大值（滑动窗口 + 哈希）
	•	题目例子
	•	LeetCode 3: Longest Substring Without Repeating Characters
	•	LeetCode 159: Longest Substring with At Most Two Distinct Characters
	•	变种描述
	•	最大值是“最长连续子串/子数组”的长度。
	•	解法
	•	滑动窗口 + 哈希表统计。
	•	时间 O(n)，空间 O(k)。

⸻

4. 单调性要求（单调栈 / 单调队列）
	•	题目例子
	•	LeetCode 239: Sliding Window Maximum
	•	LeetCode 42: Trapping Rain Water（最大盛水量问题）
	•	解法
	•	单调队列维护窗口最大值。
	•	单调栈维护左右边界，辅助求最大面积/容量。
	•	时间 O(n)。

⸻

5. 子序列最大值（不要求连续）
	•	题目例子
	•	LeetCode 300: Longest Increasing Subsequence (LIS)
	•	LeetCode 354: Russian Doll Envelopes
	•	解法
	•	DP: dp[i] = max(dp[j] + 1) for all j < i 且 nums[j] < nums[i]。
	•	O(n²)，优化可用二分 O(n log n)。

⸻

6. 区间最大值（RMQ / Segment Tree / Sparse Table）
	•	题目例子
	•	LeetCode 307: Range Sum Query - Mutable（和为主，但最大值类似）
	•	LeetCode 239（Sliding Window Maximum 也可以用 Segment Tree 做）。
	•	解法
	•	线段树：O(log n) 单次查询。
	•	Sparse Table：O(1) 查询（静态数组）。

⸻

7. 矩阵/二维数组最大值
	•	题目例子
	•	LeetCode 85: Maximal Rectangle
	•	LeetCode 221: Maximal Square
	•	解法
	•	把二维问题转化为一维柱状图最大矩形（单调栈）。
	•	DP 记录边长/高度。

⸻

8. 组合型最大值（动态规划/背包）
	•	题目例子
	•	LeetCode 416: Partition Equal Subset Sum
	•	LeetCode 322: Coin Change（最少硬币问题，但换成“最大值”也是同类）。
	•	解法
	•	背包DP：dp[i][j] 表示前 i 个数能否组成和 j。
	•	变种里最大值可能是“最大可凑金额”。

⸻

9. 特殊最大值问题
	•	题目例子
	•	LeetCode 11: Container With Most Water（最大盛水量）
	•	LeetCode 84: Largest Rectangle in Histogram
	•	解法
	•	双指针（LC11）或单调栈（LC84）。

⸻

✅ 总结表

类别	例题	解法
基础最大值	53. Maximum Subarray	Kadane / DP
固定长度子数组	643. Max Avg Subarray I	滑动窗口
可变长度子数组	3. Longest Substring w/o Repeat	滑动窗口 + 哈希
单调性问题	239. Sliding Window Maximum	单调队列
子序列最大值	300. LIS	DP / 二分
区间最大值	307. Range Sum Query Mutable	Segment Tree
矩阵最大值	85. Maximal Rectangle	DP + 单调栈
背包最大值	416. Partition Equal Subset Sum	背包 DP
特殊最大值	11. Container With Most Water	双指针


⸻

整理一份 最大值类题目的精选题单（10–12题），涵盖不同变种，既能复习常见套路，又能保持多样性，正好符合你 5 天冲刺计划里“按题型刷题”的思路。

⸻

🔥 最大值类题目精选题单

一、连续子数组/子串最大值
	1.	53. Maximum Subarray
	•	经典 Kadane 算法
	•	重点：DP 状态转移 + 滚动数组优化。
	2.	152. Maximum Product Subarray
	•	变种：最大值可能受负数影响。
	•	解法：同时维护 maxProd 和 minProd。
	3.	3. Longest Substring Without Repeating Characters
	•	最大值 = 最长无重复子串长度。
	•	解法：滑动窗口 + 哈希表。

⸻

二、固定/可变长度滑动窗口
	4.	643. Maximum Average Subarray I
	•	固定窗口最大值问题。
	•	解法：滑动窗口维护窗口和。
	5.	239. Sliding Window Maximum
	•	经典 hard，但面试常问。
	•	解法：单调队列（deque）。

⸻

三、子序列最大值（不要求连续）
	6.	300. Longest Increasing Subsequence
	•	最大递增子序列长度。
	•	解法：DP O(n²)，二分优化 O(n log n)。
	7.	354. Russian Doll Envelopes
	•	LIS 变体。
	•	解法：先排序，再做 LIS。

⸻

四、区间/二维最大值
	8.	85. Maximal Rectangle
	•	最大矩形面积。
	•	解法：DP + 单调栈（转化为直方图问题）。
	9.	221. Maximal Square
	•	最大正方形面积。
	•	解法：DP 状态转移。

⸻

五、特殊最大值问题
	10.	11. Container With Most Water
	•	双指针法。
	•	重点：左右夹逼，每次移动较短的边。
	11.	84. Largest Rectangle in Histogram
	•	单调栈维护高度。
	•	常考 hard，和 85 配合理解。
	12.	42. Trapping Rain Water
	•	最大盛水量。
	•	解法：双指针 or 单调栈。

⸻

📅 建议练习顺序（结合 5 天冲刺计划）
	•	Day 1–2（找手感）：53, 152, 3, 643
	•	Day 2–3（滑动窗口/单调队列）：239, 11
	•	Day 3（子序列 DP）：300, 354
	•	Day 4（矩阵 DP）：221, 85
	•	Day 5（高难收尾 + 复习）：42, 84

⸻

🎯 收获

刷完这份题单，你会：
	•	覆盖几乎所有最大值常见套路（Kadane、滑动窗口、单调队列、DP、单调栈、双指针）；
	•	面试里遇到 “变种最大值题” 时，能快速 map 到对应套路。

⸻

要不要我把这 12 道题的解法思路 + 模板代码 给你整理成一个 “最大值题手册”，这样你在准备时就不用翻来翻去？