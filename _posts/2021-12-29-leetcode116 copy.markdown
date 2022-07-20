---
layout: post
title: LeetCode 116. Populating Next Right Pointers in Each Node
date: 2021-12-29 23:28:42 +0900
category: Algorithm
---
### LeetCode 116. Populating Next Right Pointers in Each Node

![](/assets/img/leetcode/116.png)

- 이진트리 오른쪽아이를 가르키기

<br><br>

>코드

```c#
public class Solution
{
    public Node Connect(Node root)
    {
        if (root == null) return null;

        if (root.left != null)
        {
            root.left.next = root.right;
            if (root.next != null)
                root.right.next = root.next.left;

            Connect(root.left);
            Connect(root.right);
        }
        return root;
    }
}
```

현재 노드를 기준으로 왼쪽아이는 무조건 오른쪽아이를 가르키고

오른쪽아이는 현재노드의 다음아이의 왼쪽아이를 가르킨다

왼쪽부터 죽 DFS로 나가는 방법!

>코드

```c#
public class Solution
{
    Queue<Node> nodes = new Queue<Node>();
    public Node Connect(Node root)
    {
        if (root == null) return root;
        nodes.Enqueue(root);
        while (nodes.Count > 0)
        {
            Node curNode = nodes.Dequeue();
            System.Console.WriteLine(curNode.val);

            Node leftNode = curNode.left;
            Node rightNode = curNode.right;


            if (leftNode != null)
            {
                leftNode.next = rightNode;
                if (curNode.next != null)
                    rightNode.next = curNode.next.left;

                nodes.Enqueue(leftNode);
                nodes.Enqueue(rightNode);
            }
        }
        return root;
    }
}
```

같은 풀인데 BFS로 풀이

