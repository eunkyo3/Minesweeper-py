# 문제
표준 입력으로 2차원 리스트의 가로(col)와 세로(row)가 입력되고 그 다음 줄부터 리스트의 요소로 들어갈 문자가 입력됩니다. 이때 2차원 리스트 안에서 *는 지뢰이고 .은 지뢰가 아닙니다. 지뢰가 아닌 요소에는 인접한 지뢰의 개수를 출력하는 프로그램을 만드세요(input에서 안내 문자열은 출력하지 않아야 합니다).
여러 줄을 입력 받으려면 다음과 같이 for 반복문에서 input을 호출한 뒤 append로 각 줄을 추가하면 됩니다(list 안에 문자열을 넣으면 문자열이 문자 리스트로 변환됩니다).
# 입력
5 5 <br>
..\*.. <br>
...\*. <br>
.\*... <br>
.\*\*\*. <br>
\*.\*..
# 출력
01\*21 <br>
123\*1 <br>
2\*532 <br>
3\*\*\*1 <br>
\*4\*31
# 나의 풀이
```python
# 가로 세로 크기를 입력받음
col, row = map(int, input().split())

# 빈 리스트 생성
matrix = []

# 2차원 리스트 생성
for i in range(row):
    matrix.append(list(input()))
    
# 지뢰 제조 공장 (설명 나중에 귀찮;)
for i in range(row):
    for j in range(col):
        cnt = 0
        if matrix[i][j] == '.':
            for a in range(i-1, i+2):
                for b in range(j-1, j+2):
                    if not (a<0 or b<0 or a>=row or b>= col):
                        if matrix[a][b] == '*':
                            cnt += 1
            matrix[i][j] = cnt
            print(matrix[i][j], end='')
        else:
            print(matrix[i][j], end='')
    print()
```
츨처: [파이썬 코딩도장 23.7문제](https://dojang.io/mod/quiz/review.php?attempt=2012267&cmid=2298)
