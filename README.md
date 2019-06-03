# 도시화에 따른 여름철 폭염일수의 

학과 | 학번 | 성명
---- | ---- | ---- 
대기환경과학과 |201514336 | 장영환


## 프로젝트 개요
기상자료개방포털(https://data.kma.go.kr/cmmn/main.do) 에서 2009년부터 2018년까지, 6월부터 8월까지의 평균온도와 최고온도를 다운받은 후, 전체 변화량은 그래프로, 총 평균기온과 폭염일수는 print함수로 나타내었다.

## 사용한 공공데이터 
[데이터보기](https://github.com/201514336/file)

## 소스
* [링크로 소스 내용 보기](https://github.com/201514336/file/blob/master/test.py) 

* 코드 삽입
~~~python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from matplotlib import font_manager, rc
font_name = font_manager.FontProperties(fname = "C:\Windows\Fonts\HANBatangB.ttf").get_name()
rc('font', family = font_name)
df = pd.read_excel('fr.xlsx', sheet_name = '201514336')
df1 = pd.read_excel('fr1.xlsx', sheet_name = '201514336')

#city = ['서울', '인천', '울릉도', '대구', '부산', '인제', '보은', '장수']
year = [2009, 2010, 2011, 2012, 2013, 2014, 2015, 2016, 2017, 2018]
x = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

a, l = [0 for _ in range(80)], [0 for _ in range(80)]
b, c, d = [0 for _ in range(10)], [0 for _ in range(10)], [0 for _ in range(10)]
e, f, g = [0 for _ in range(10)], [0 for _ in range(10)], [0 for _ in range(10)]
h, k, b1 = [0 for _ in range(10)], [0 for _ in range(10)], [0 for _ in range(10)]
c1, d1, e1 = [0 for _ in range(10)], [0 for _ in range(10)], [0 for _ in range(10)]
f1, g1, h1, k1 = [0 for _ in range(10)], [0 for _ in range(10)], [0 for _ in range(10)], [0 for _ in range(10)]

for i in range(1, 81):
    a[i-1] = np.mean(df[df['지점'] == i].loc[:, ['평균기온(°C)']].mean(axis = 1))
    l[i-1] = len(df1[df1['지점'] == i].loc[:, ['최고기온(°C)']].mean(axis=1))

for j in range(0, 10):
    b[j] = a[j * 8]
    c[j] = a[j * 8 + 1]
    d[j] = a[j * 8 + 2]
    e[j] = a[j * 8 + 3]
    f[j] = a[j * 8 + 4]
    g[j] = a[j * 8 + 5]
    h[j] = a[j * 8 + 6]
    k[j] = a[j * 8 + 7]
    b1[j] = l[j * 8]
    c1[j] = l[j * 8 + 1]
    d1[j] = l[j * 8 + 2]
    e1[j] = l[j * 8 + 3]
    f1[j] = l[j * 8 + 4]
    g1[j] = l[j * 8 + 5]
    h1[j] = l[j * 8 + 6]
    k1[j] = l[j * 8 + 7]
print("서울=blue", "인천=green", "대구=red", "부산=cyan")
print("울릉도=blue dashed line", "인제=green dashed line", "보은=red dashed line", "장수=cyan dashed line")
print("도시 총 평균기온 :", np.mean(b+c+e+f), "°C")
print("시골 총 평균기온 :", np.mean(d+g+h+k), "°C")
print("도시 총 폭염일수 :", sum(b1+c1+e1+f1), "일")
print("시골 총 폭염일수 :", sum(d1+g1+h1+k1), "일")

plt.plot(b, 'bo-')
plt.plot(c, 'go-')
plt.plot(d, 'bo--')
plt.plot(e, 'ro-')
plt.plot(f, 'co-')
plt.plot(g, 'go--')
plt.plot(h, 'ro--')
plt.plot(k, 'co--')
plt.title('평균온도 변화')
plt.xlabel('연도')
plt.ylabel('온도')
plt.xticks(x, year)
plt.show()
plt.plot(b1, 'bo-')
plt.plot(c1, 'go-')
plt.plot(d1, 'bo--')
plt.plot(e1, 'ro-')
plt.plot(f1, 'co-')
plt.plot(g1, 'go--')
plt.plot(h1, 'ro--')
plt.plot(k1, 'co--')
plt.title('폭염일수 변화')
plt.xlabel('연도')
plt.ylabel('폭염일')
plt.xticks(x, year)
plt.show()
~~~
