## Baekjoon_1003번 피보나치
1) 재귀로 풀어 본다
+ local variable 'result2' referenced before assignment 이런 문구가 뜨면, 전역변수를 지역변수로 호출했기 때문에 발생한 문제다
 → global 변수명을 추가해서 해결한다
+ 시간 초과됨. 3개 구하는데 무려 4.8sec
```python
start = time.time()

def fibo(n):
    global result1
    global result2
    if n==0:
        result1 += 1
        return 0
    elif n==1:
        result2 += 1
        return 1
    else:
        return fibo(n-1) + fibo(n-2)
result = []
n = int(input())
for i in range(n):
    a = int(input())
    result1=0
    result2=0
    fibo(a)
    result.append([result1, result2])
for i in result:
    print(i[0], i[1])

end = time.time()

print(f"{end - start:.5f} sec")
```
2) 대충 아는 수열이니 풀어서 구현한다
+ 메모리 31256KB, 시간 44ms, 코드 길이 286B
```python
aaa = []
n = int(input())
for i in range(n):
    a = int(input())
    aaa.append(a)
for j in aaa:
    res = [1, 1]
    for i in range(j):
        res.append(res[i]+res[i+1])
    if j==0:
        print(1, 0)
    elif j==1:
        print(0, 1)
    else:
        print(res[j-2], res[j-1])
```
3) 다이나믹 프로그래밍 적용
+ fibo(n-1)이나 fibo(n)이나 어차피 계산은 중복이다
+ 동적 계획법 중 bottom-up으로 작은 문제부터 풀고 모아서 큰 문제를 해결한다
+ 메모이제이션(Memoization)을 활용한다. 미리 계산해 배열로 저장해두고 꺼내 쓴다
+ 메모리, 시간 동일, 코드 길이 256B (조금 줄었다)
```python
aaa = []
n = int(input())
for i in range(n):
    a = int(input())
    aaa.append(a)
for j in aaa:
    dp = [0, 1]
    def fibo(j):
        for i in range(2, j+1):
            dp.append(dp[i-1]+dp[i-2])
        return dp
    print(fibo(j)[j-1], fibo(j)[j])
```
