# Matplotlib

#### 넘파이 패키지의 기능을 바탕으로 개발된 멀티플랫폼 시각화 라이브러리

#### Matplotlib의 가장 중요한 특징: Matplotlib이 다양한 운영체제 위에서 동작하고 다양한 포맷으로 그래프를 생성할 수 있다는 것

맷플롯립을 실습하기 위한 환경 구축 방법: 파이썬의 라이브러리 이므로 파이썬이 필요, 코랩에서 사용 가능

Numpy의 축약어는 np 그리고 Pandas의 축약어는pd라고 사용한 것처럼 matplotlib의 축약어는 mpl로 자주 사용하는 matplotlib.pyplot은 plt라는 축약어를 사용함

<pre><code>plt.savefig('my_figure.jpg')</pre></code>
맷플롯립의 편리한 기능 중 하나는 다양한 포맷의 그림으로 저장하는 것

그림을 저장하기 위해 savefig() 명령을 사용하면 되고 파일의 포맷은 확장자로 설정할 수 있음

괄호 안에는 저장하고자 하는 파일의 이름을 확장자와 함께 입력하면 됨

<pre><code>from google.colab import files
files.download('my_figure.jpg')</pre></code>
구글 코랩의 클라우드 저장소에 있는 그림 파일을 로컬 컴퓨터로 다운로드하는 법

구글 코랩의 파일 처리를 위한 라이브러리를 불러오기한 이후에 files.download('파일명')과 같이 입력하면 된다.

## Matplotlib 인터페이스(두 종류의 인터페이스 사용 가능)
### MATLAB의 스타일

1. 단순하고 편리함

2. Matlab 사용자 친화적

### 객체 지향 스타일
> 복잡하고 상세한 설정 가능

> 파이썬 프로그램 친화적

일반적으로 단순한 그림을 빠르게 그릴 생각이라면 매트랩 스타일을 사용하고,
여러가지 옵션을 적용하여 복잡한 그림을 그릴 때는 객체지향 인터페이스 스타일을 사용

<pre><code>plt.figure()</pre></code>
그림이 담길 틀 생성

<pre><code>x = np.linspace(-10,10,100)</pre></code>
두개의 패널 중 첫 번째 패널을 생성하고 현재 축을 설정

<pre><code>plt.subplot(2,1,1)
plt.plot(x,np.sin(x))</pre></code>

2행 1열 구조 그리드의 첫번째 패널에 사인 그래프 작성

<pre><code>plt.subplot(2,1,2)
plt.plot(x, np.cos(x))</pre></code>
2행 1열 구조 그리드의 두번째 패널에 코사인 그래프 작성

매트랩 스타일의 인터페이스에서는 그림의 상태를 저장한다는 것을 알고 있어야 합니다. 모든 plt 명령어가 적용되는 곳에 있는 "현재 상태의" 그림과 축을 기록함

현재 그림을 참조하기 위해 plt.gcf() (get current figure) 명령어를 사용하고 현재 축을 참조하기 위해 plt.gca() (get current axes)를 사용

상태 기반의 인터페이스는 간단한 그림을 빠르고 편리하게 그릴 수 있지만, 여러가지 문제점이 있음

복잡한 상황과 그림을 좀 더 세밀하게 제어하고 싶을 때는 객체지향 스타일 인터페이스를 사용

<pre><code>fig,ax = plt.subplots(2,1)</pre></code>
객체지향 인터페이스에서는 현재 활성화된 상태의 그림이나 축의 개념에 의존하지 않고, 명시적으로 그림(Figure)과 축(Axes) 객체를 생성하는 메서드를 사용

<pre><code>ax[0].plot(x,np.cos(x));</pre></code>
적절한 객체의 plot()메소드를 호출

##### 그림이 복잡하고 많은 설정이 필요한 경우 객체지향 방식을 선택하는 것이 더 적합

## Matplotlib 사용법
### 1) 선그림
y=f(x)를 시각화하는 경우

변수 x의 값이 연속적이고 이에 해당하는 y의 값을 시각화하여 x의 변화에 대한 y의 변화 또는 추세를 시각적으로 표시하기 위해 사용
<pre><code>
%mataplotlib inline
import mataplotlib.pyplot as plt
plt.style.use('seaborn-whitegrid')
import numpy as np
</pre></code>

맷플롯립 그림을 화면에 표시하는 방법을 설정

다음으로, 맷플롯립 패키지를 불러오고 기본 스타일로 'seaborn-whitegrid'를 사용하도록 설정

<pre><code>fig = plt.figure()</pre></code>

모든 맷플롯립 플롯은 그림(figure)과 축(axes)를 만드는 것부터 시작

먼저, plt.figure() 함수를 이용해서 빈 그림판을 생성, 그림판의 크기, 배경색, 테두리색 등을 괄호 안에 인자 값을 설정하여 변경할 수 있음

<pre><code>ig.suptitle("Example 1:line plot")
ax = plt.axes()</pre></code>

축 생성

Matplotlib에서 그림(plt.Figure 클래스의 인스턴스)은 축과 그래픽, 텍스트, 레이블을 표시하는 모든 객체를 포함하는 컨테이너로 생각하면 됨

plt.axes 클래스의 인스턴스인 축은 눈금과 레이블이 있는 테두리 상자로 나중에 데이터가 표시되는 부분

<pre><code>plt.plot(x,y)
ax = plt.axes()</pre></code>

간단한 플롯을 그리기 위해 MATLAB 스타일의 인터페이스를 사용하면 더 간편

여러 개의 라인을 한 화면에 그리고 싶다면 단순히 plot 함수를 여러 번 사용하면 됨

축과 라인의 모양을 변경하는 방법
### 2) 플롯 조정
색을 입력하는 방법은 다양한 방식을 사용할 수 있고, 상황에 따라 선택할 수 있음

가장 간단한 방법은 아래와 같이 색상 코드 문자를 입력하는 방법
<pre><code>plt.plot(x, np.sin(x-1), colot ='g')</pre></code>

###### 선의 스타일은 linestyle 키워드로 설정할 수 있음

맷플롯립은 입력한 데이터의 크기를 판단하여 자동으로 축의 범위를 설정하지만

때때로 사용자가 축의 하한과 상한, 스케일을 세밀하게 조정할 필요가 있을 때가 있음

###### 축의 범위를 지정하는 가장 기본적인 명령: plt.xlim(), plt.ylim() 메소드

축의 상하 또는 좌우를 반전시켜야 한다면 단순히 인수의 순서를 바꾸기만 하면 됨

###### x축과 y축을 동시에 지정하는 방법: plt.axis() 메소드를 사용

인자로 [x축 최소값, x축 최대값, y축 최소값, y축 최대값] 쌍을 리스트로 전달하여 축의 범위를 설정할 수 있음

###### 축의 스케일을 변경해야 하는 경우: plt.xscale(),plt.yscale() 메소드를 사용

###### 괄호 안에 전달하는 인자는 {"log", "linear", "symlog", "logit"} 등이 가능

###### 그림의 제목은 plt.title(), 축의 레이블은 xlabel(), ylabel()을 이용
###### 그림에 범례를 표시: plt.legend() 메소드를 호출

### 3) 점그림
<pre><code>x = np.linspace(0,10,25)</pre></code>
보통 점과 점 사이의 선후관계나 관련성이 없는 경우 보통 산점도를 이용
<pre><code>plt.plot(x,np.sin(x),'-og')</pre></code>
더 편리한 방법은 선의 종류, 마커의 종류, 색상을 나타내는 코드를 한번에 입력하는 것

### 4) 플롯 조정
선과 마커의 종류 색상 변경

### 5) plt.scatter

plt.scatter와 plt.plot의 차이점은 plt.scatter 메소드는 개별 점의 속성(크기, 색상, 모서리 색상 등)을 섬세하게 제어할 수 있다는 것


## 1)다중 서브 플롯 작성
##### 서브플롯: 하나의 큰 그림 내부에 있는 작은 그림이라는 의미

#### 서브플롯을 생성: plt.subplot()
서브플롯을 생성할 때 그리드의 형태를 지정하는 인수를 전달할 수 있음

인수는 (행의 개수, 열의 개수, 서브플롯 번호) 형태로 지정

#### 서브플롯 그리드를 생성: plt.subplots()

이 메소드를 사용하면 전체 그리드를 한번에 생성하여 서브플롯을 Numpy 배열로 반환
인수로 행과 열의 개수를 전달하면 됨

#### plt.GridSpec함수 :복잡한 형태와 크기의 서브플롯을 생성하기 위해서 사용
``plt.GridSpec()`` 를 이용해서 플롯의 틀을 먼저 만들고, 실제 서브플롯을 만들려면 ``plt.subplot(grid[x, y])`` 구문을 사용
