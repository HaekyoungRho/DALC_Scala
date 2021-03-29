# 빅데이터란?


RDBMS과 같은 전통적 데이터 관리 기법으로 다루기 힘든 데이터


빅데이터를 다루는 대표적 언어로 R과 파이썬이 있음


## 파이썬 지원 패키지


> Numpy : 동일한 데이터타입을 가진 배열 기반의 데이터 처리

> Pandas: data frame형태로 데이터를 다룸

> Scipy: 과학 계산 작업

> Mataplotlib: 데이터 시각화

> Scikit-Learn: 머신러닝

데이터 분석은 빅데이터 분석을 위한 기본 절차 - 숫자 배열을 전문적으로 다루는 Numpy

## 데이터 분석을 위해서는


1. 원본 데이터를 숫자 배열로 변환


2. 편한 방식으로 연산 적용


3. 연산을 다루기 쉬운 형태로 변환


4. 분석


## Numpy(Numerical Python):
빅데이터 분석을 위해 사용되는 기본적인 패키지
array단위로 데이터 관리 및 연산 수행(규모가 커질수록 저장 및 처리에 효율적)

#### 1) 넘파이 패키지 임포트
<pre><code>Import numpy as np</pre></code>

#### 2)arr정의와 사용 방법
arr 정의 후
<pre><code>ar = np.array(data1)</pre></code>

데이터 타입을 설정할 때는 dtype 키워드 사용
<pre><code>arr = np.array(data1, dtype = "float32")</pre></code>

#### 3)다차원 배열 구성
<pre><code>ar3 = np.array(\[range(i, i+3) for i in data1 \])</pre></code>

full 함수
<pre><code>ar4=np.full((3,5), 3.14)</pre></code>
3,5행렬을 3,14로 채우기

#### 4)배열 구성

arange함수
<pre><code>ar5 = np.arange(0, 20, 2)</pre></code>
0-20까지 2씩 더해서 배열을 만듦 20은 제외

linspace 함수
<pre><code>ar6 = np.linspace(0,1,3)</pre></code>
0.5간격의 3개 요소 값을 가진 배열

#### 5)무작위 값의 배열 구성
randint 함수
<pre><code>ar8=np.random.randint(0, 100, (3,3))</pre><code>
0은 구간의 시작 100은 구간의 끝 세번째는 배열의 크기

#### 6)단위 행렬 생성
eye 함수
<pre><code>ar9 = np.eye(3)</pre></code>
대각선은 1 나머지는 0

### 배열의 분할, 재구성, 결합
#### 1)배열 속성
ndim: 차원의 개수
shape: 각 차원의 크기
size: 전체 배열의 크기

### 배열 인덱싱
<pre><code>y = np.array([2, 4, 6, 8, 10])</pre></code>


<pre><code>print(y[0], y[-2])</pre></code>
개별 배열 요소 값을 가져오거나 특정 위치에 값을 설정하기 위해 사용
다차원 배열에서는 인덱스 튜플을 사용 -->(\[2,4,6,7\],\[3,5,7,9\])


### 배열 슬라이싱
콜론 기호(;)를 나타내는 슬라이스 표기법
x\[start:stop:step\]

기본값
> start는 0으로 설정
> stopdms 차원 크기로 설정
> step은 1로 설정


x\[4:8\]-->4,5,6,7
x\[:5\] --> 0 , 1, 2, 3, 4
x = np.arange(10)
x\[5:\] --> 5,6,7,8,9
다차원 슬라이싱도 동일한 방법


### 배열의 재구조화(배열의 형상 변경)
reshape 함수
<pre><code>z = np.arange(1,10).reshape(3,3)</pre></code>
3x3행렬에 1-9까지 넣음

### 배열 결합
concatenate, vstack(수직스택), hstack(수평스택)

### 배열 분할
split,vsplit,hsplit
split(분할 대상 리스트, 분할 위치)

<hr/>
단항 유니버셜 함수: 매개변수 한개, 사칙연산 사용 가능(//는 나머지 버리고 몫만)<br/>
이항 유니버셜 함수: 매개변수 두개



### 1)단항 유니버셜 함수
절대값 함수: abs함수
<pre><code>np.abs(x)</pre></code>

삼각함수, 역삼각함수, 지수함수, 로그함수 제공<br/>
out인자 : 지정한 배열에 직접 연산 결과 표기 가능 -대규모 연산에 유리

#### 집계함수
reduce함수: 결과가 하나만 남을때까지 해당 연산을 배열 요소에 반복적으로 사용
<pre><code>np.add.reduce(x)</pre></code>

#### sum, min, max 함수
axis인자
0: 열 기준 1: 행 기준 None: 모든 요소의 집계 연산

#### 브로드캐스팅 연산:
서로 다른 크기의 배열에 이항 유니버셜 함수를 적용할 수 있는 기능

1차원 + 2차원 --> 1차원 배열 x가 2차원 배열 m의 형상에 맞춤

행렬 데이터의 조건에 따른 결과 산출

#### any함수: 하나라도 만족하면 true

팬시 인덱싱: 인덱스 배열을 전달하고 인덱스 배열의 값을 인덱스로 사용 - 배열의 요솟값에 접근

#### sort함수
np.sort함수: 원래 데이터는 그대로 유지한 채 정렬된 배열이 복사본으로 반환

> x.sort 함수: 원래 배열 자체를 정렬

> np.argsort함수: 정렬된 요소의 인덱스를 반환

> x_reverse: 내림차순 정렬

axis 인자: 0일때 열을 기준으로 1일때는 행을 기준으로
