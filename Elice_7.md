## Elice_7일째 최대공약수, 최소공배수
+ 유클리드 호제법 사용
+ 두 수의 나머지와 작은 수 간의 나머지를 반복해서 구한다
```python
N, M = map(int, input().split(" "))
B = max(N, M)
S = min(N, M)
while(True):
    if B%S == 0:
        gcd = S
        break
    else:
        temp = B%S
        B = S
        S = temp
lcm = int(M*N/gcd)
print(gcd)
print(lcm)
```
+ 재귀로도 풀어본다
+ 시간은 비슷하게 걸린다. 코드 길이가 조금 줄고, 더 보기 좋다
```python
N, M = map(int, input().split(" "))
B = max(N, M)
S = min(N, M)
def gcd(B, S):
    if B%S == 0:
        return S
    else:
        return gcd(S, B%S)
lcm = int(M*N/gcd(B, S))
print(gcd(B, S))
print(lcm)
```
