---
layout: post
title: Refactoring 1
date: 2022-01-14 23:02:31 +0900
category: Refactoring
---
### LeetCode 452. Minimum Number of Arrows to Burst Balloons

![](/assets/img/leetcode/452.png)

- 가장 적게 찔러 넣기!

<br><br>

>코드

```c#
public class Solution
{
    public int FindMinArrowShots(int[][] points)
    {
        Array.Sort(points, (x, y) => (x[1].CompareTo(y[1])));
        int ret = 1;
        int curpos = points[0][1];

        for (int i = 1; i < points.Length; i++)
        {
            if (curpos < points[i][0])
            {
                curpos = points[i][1];
                ret++;
            }
        }

        return ret;
    }
}
```

극한으로 줄인코드!

sorting은 왠만하면 위와 같은 방법이 편할듯

찔러 넣는 위치를 옮겨가는 방법!