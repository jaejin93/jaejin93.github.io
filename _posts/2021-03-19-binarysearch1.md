---
title: "BinarySearch 개념"
categories: 
  - Algorithm
  - BinarySearch
last_modified_at: 2021-03-19
toc: false #Table of Contents
comments: true
use_math: true # MathJax On
---

## 범위를 반씩 좁혀가는 탐색

#### 순차 탐색

리스트 내에서 데이터를 매우 빠르게 **탐색**하는 이진 탐색(Binary Search)을 이해하기 전에 순차 탐색(Sequential Search)을 먼저 이해 해야한다. 순차 탐색은 리스트 안에 있는 데이터를 찾기 위해 앞에서부터 데이터를 하나씩 차례대로 확인하는 방법이다. 보통 정렬되지 않은 리스트에서 데이터를 찾을 때 사용한다. 쉽게 구현 가능하며 특정 원소가 있는지 체크할 때 `count()`를 활용하기도 한다.

```python
# 순차 탐색 소스코드 구현
def sequential_search(n,target, array):
    # 각 원소를 하나씩 확인
    for i in range(n):
        # 현재의 원소가 찾고자 하는 원소와 동일한 경우
        if array[i] == target:
            return i+1 #현재 위치 반환, 인덱스는 0부터 시작해서 +1

print("생성할 원소 개수를 입력한 다음 한 칸 띄고 찾을 문자열을 입력하세요.")
input_data = input().split() #입력 데이터는 리스트 형태로 저장

n = int(input_data[0]) #원소의 개수
target = input_data[1] #찾는 문자열

print("앞서 적은 원소 개수만큼 문자열을 입력하세요. 구분은 띄어쓰기 한 칸으로 합니다.")
array = input().split()

#순차 탐색 수행 결과
print(sequential_search(n,target,array))
```

    생성할 원소 개수를 입력한 다음 한 칸 띄고 찾을 문자열을 입력하세요.
    5 jaejin
    앞서 적은 원소 개수만큼 문자열을 입력하세요. 구분은 띄어쓰기 한 칸으로 합니다.
    apple banana jaejin kiwi grape
    3
    
#### 이진 탐색 : 반으로 쪼개면서 탐색하기

이진 탐색은 배열(혹은 리스트)의 내부 데이터가 **정렬되어 있어야만 사용할 수 있는 알고리즘이다.** 범위를 절반씩 좁혀가며 데이터를 탐색한다. 구체적으로 **시작점, 끝점, 중간점** 세개의 포인트를 두고 찾으려는 데이터와 중간점을 비교해 데이터를 찾는다.

**재귀 함수로 구현한 이진 탐색 소스코드**
재귀 함수로 구현한 이진 탐색 코드는 $$O(logN)$$의 시간 복잡도를 갖는다. 데이터가 2개면 1번, 4개면 2번, 8개면 3번이라고 생각하면 이해하기 쉽다.

```python
# 이진 탐색 소스코드 구현 (재귀 함수)
def binary_search(array, target, start, end):
    if start > end:
        return None
    mid = (start + end) // 2
    # 찾은 경우 중간점 인덱스 반환
    if array[mid] == target:
        return mid
    # 중간점의 값보다 찾고자 하는 값이 작은 경우 왼쪽 확인
    elif array[mid] > target:
        return binary_search(array, target, start, mid - 1)
    # 중간점의 값보다 찾고자 하는 값이 큰 경우 오른쪽 확인
    else:
        return binary_search(array, target, mid + 1, end)

# n(원소의 개수)과 target(찾고자 하는 값)을 입력 받기
n, target = list(map(int, input().split()))
# 전체 원소 입력 받기
array = list(map(int, input().split()))

# 이진 탐색 수행 결과 출력
result = binary_search(array, target, 0, n - 1)
if result == None:
    print("원소가 존재하지 않습니다.")
else:
    print(result + 1)
```

    10 7
    1 3 5 7 8 11 13 15 17 19
    4

**반복문으로 구현한 이진 탐색 소스코드**

존 벤틀리의 말에 의하면 이진 탐색 코드를 작성한 프로그래머는 10% 내외로 실제 구현은 까다롭기에 꼭 외우자. 보통 탐색 범위가 2,000만을 넘어가면 접근하면 좋다. 시간 복잡도가 $$O(logN)$$으로 매우 뛰어나기 때문이다.

```python
def binary_search(array, target, start, end):
    while start <= end:
        mid = (start + end) // 2
        # 찾은 경우 중간점 인덱스 반환
        if array[mid] == target:
            return mid
        # 중간점의 값보다 찾고자 하는 값이 작은 경우 왼쪽 확인
        elif array[mid] > target:
            end = mid - 1
        # 중간점의 값보다 찾고자 하는 값이 큰 경우 오른쪽 확인
        else:
            start = mid + 1
    return None

# n(원소의 개수)과 target(찾고자 하는 값)을 입력 받기
n, target = list(map(int, input().split()))
# 전체 원소 입력 받기
array = list(map(int, input().split()))

# 이진 탐색 수행 결과 출력
result = binary_search(array, target, 0, n - 1)
if result == None:
    print("원소가 존재하지 않습니다.")
else:
    print(result + 1)
```

    10 7
    1 3 5 7 8 11 13 15 17 19
    4
    
## 트리 자료구조
