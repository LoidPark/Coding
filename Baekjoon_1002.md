## Baekjoon_1002번 터렛 (좌표 상 개수 구하기)
+ 두 원이 가까워지고 접하며 포함되는 과정을 케이스별로 표현
+ 메모리 31256KB, 시간 48ms, 코드 길이 599B	
```python
n = int(input())
result = []
for i in range(n):
    x1, y1, r1, x2, y2, r2 = map(int, input().split())
    res = (x1-x2)**2 + (y1-y2)**2
    big = max(r1, r2)
    sml = min(r1, r2)
    if res==0 and big==sml:
        result.append('-1')
    elif res > (big+sml)**2:
        result.append('0')
    elif res == (big+sml)**2:
        result.append('1')
    elif res < (big+sml)**2:
        if res > (big-sml)**2:
            result.append('2')
        elif res == (big-sml)**2:
            result.append('1')
        elif res < (big-sml)**2:
            result.append('0')
for i in result:
    print(i)
```
