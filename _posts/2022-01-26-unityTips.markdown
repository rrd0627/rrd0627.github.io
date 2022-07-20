---
layout: post
title: Unity Tips
date: 2022-01-26 23:48:27 +0900
category: ETC
---
# UniTask 사용법


```cpp

using Cysharp.Threading.Tasks;
using System.Threading;

public class unitasktest : MonoBehaviour
{
    // Start is called before the first frame update
    async void Start()
    {
        List<UniTask> tasks = new List<UniTask>();
        for (int i = 0; i < 3; i++)
            tasks.Add(test(i + 1));
        await UniTask.WhenAll(tasks);
        print("ALL DONE");
        WhileTest().Forget();
    }

    private async UniTask test(float duration)
    {
        float timer = 0;

        print($"STart {duration}");

        while (timer < duration)
        {
            timer += Time.deltaTime;
            await UniTask.Yield();
        }
        print($"End {duration}");
    }

    CancellationTokenSource cts = new CancellationTokenSource();
    private void Update()
    {
        if (Input.GetMouseButtonDown(0))
        {
            this.gameObject.SetActive(false);
            cts.Cancel();
        }
    }
    private async UniTaskVoid WhileTest()
    {
        while (true)
        {
            print("Still working");
            await UniTask.Delay(1000, DelayType.DeltaTime, PlayerLoopTiming.Update, cts.Token);
        }
    }
}


```

