---
layout: post
title: 深度學習500問-01-數學基礎
categories: Dev
tags: [deep learning]
---

author: [scutan90](https://github.com/scutan90/DeepLearning-500-questions)

> Description:
>
> 深度學習內容相關筆記	

<!-- more -->

# 第一章 數學基礎

深度學習通常又需要哪些數學基礎？深度學習裡的數學到底難在哪裡？通常初學者都會有這些問題，在網絡推薦及書本推薦裡，經常看到會列出一系列數學科目，比如微積分、線性代數、概率論、複變函數、數值計算、優化理論、信息論等等。這些數學知識有相關性，但實際上按照這樣的知識範圍來學習，學習成本會很久，而且會很枯燥，本章我們通過選舉一些數學基礎裡容易混淆的一些概念做以介紹，幫助大家更好的理清這些易混淆概念之間的關係。

## 1.1 向量和矩陣

### 1.1.1 標量、向量、矩陣、張量之間的聯繫
**標量（scalar）**
一個標量表示一個單獨的數，它不同於線性代數中研究的其他大部分對象（通常是多個數的數組）。我們用斜體表示標量。標量通常被賦予小寫的變量名稱。

**向量（vector）**
一個向量表示一組有序排列的數。通過次序中的索引，我們可以確定每個單獨的數。通常我們賦予向量粗體的小寫變量名稱，比如xx。向量中的元素可以通過帶腳標的斜體表示。向量$X$的第一個元素是$X_1$，第二個元素是$X_2$，以此類推。我們也會註明存儲在向量中的元素的類型（實數、虛數等）。

**矩陣（matrix）**
矩陣是具有相同特徵和緯度的對象的集合，表現為一張二維數據表。其意義是一個對象表示為矩陣中的一列，一個特徵表示為矩陣中的一行，每個特徵都有數值型的取值。通常會賦予矩陣粗體的大寫變量名稱，比如$A$。

**張量（tensor）**
在某些情況下，我們會討論坐標超過兩維的數組。一般地，一個數組中的元素分佈在若干維坐標的規則網格中，我們將其稱之為張量。使用 $A$ 來表示張量“A”。張量$A$中坐標為$(i,j,k)$的元素記作$A_{(i,j,k)}$。

**四者之間關係**

> 標量是0階張量，向量是一階張量。舉例：
> 標量就是知道棍子的長度，但是你不會知道棍子指向哪兒。
> 向量就是不但知道棍子的長度，還知道棍子指向前面還是後面。
> 張量就是不但知道棍子的長度，也知道棍子指向前面還是後面，還能知道這棍子又向上/下和左/右偏轉了多少。

### 1.1.2 張量與矩陣的區別

- 從代數角度講， 矩陣它是向量的推廣。向量可以看成一維的“表格”（即分量按照順序排成一排）， 矩陣是二維的“表格”（分量按照縱橫位置排列）， 那麼$n$階張量就是所謂的$n$維的“表格”。張量的嚴格定義是利用線性映射來描述。
- 從幾何角度講， 矩陣是一個真正的幾何量，也就是說，它是一個不隨參照系的坐標變換而變化的東西。向量也具有這種特性。
- 張量可以用3×3矩陣形式來表達。
- 表示標量的數和表示向量的三維數組也可分別看作1×1，1×3的矩陣。

### 1.1.3 矩陣和向量相乘結果

若使用愛因斯坦求和約定（Einstein summation convention），矩陣$A$, $B$相乘得到矩陣$C$可以用下式表示：
$$ a_{ik}*b_{kj}=c_{ij} \tag{1.3-1} $$
其中，$a_{ik}$, $b_{kj}$, $c_{ij}$分別表示矩陣$A, B, C$的元素，$k$出現兩次，是一個啞變量（Dummy Variables）表示對該參數進行遍歷求和。
而矩陣和向量相乘可以看成是矩陣相乘的一個特殊情況，例如：矩陣$B$是一個$n \times 1$的矩陣。

### 1.1.4 向量和矩陣的範數歸納
**向量的範數(norm)**
​ 定義一個向量為：$\vec{a}=[-5, 6, 8, -10]$。任意一組向量設為$\vec{x}=(x_1,x_2,...,x_N)$。其不同範數求解如下：

- 向量的1範數：向量的各個元素的絕對值之和，上述向量$\vec{a}$的1範數結果就是：29。
  
$$
\Vert\vec{x}\Vert_1=\sum_{i=1}^N\vert{x_i}\vert
$$

- 向量的2範數：向量的每個元素的平方和再開平方根，上述$\vec{a}$的2範數結果就是：15。
  
$$
\Vert\vec{x}\Vert_2=\sqrt{\sum_{i=1}^N{\vert{x_i}\vert}^2}
$$

- 向量的負無窮範數：向量的所有元素的絕對值中最小的：上述向量$\vec{a}$的負無窮範數結果就是：5。
  
$$
\Vert\vec{x}\Vert_{-\infty}=\min{|{x_i}|}
$$

- 向量的正無窮範數：向量的所有元素的絕對值中最大的：上述向量$\vec{a}$的正無窮範數結果就是：10。
  
$$
\Vert\vec{x}\Vert_{+\infty}=\max{|{x_i}|}
$$

- 向量的p範數：
  
$$
L_p=\Vert\vec{x}\Vert_p=\sqrt[p]{\sum_{i=1}^{N}|{x_i}|^p}
$$

**矩陣的範數**

定義一個矩陣$A=[-1, 2, -3; 4, -6, 6]$。任意矩陣定義為：$A_{m\times n}$，其元素為 $a_{ij}$。

矩陣的範數定義為

$$
\Vert{A}\Vert_p :=\sup_{x\neq 0}\frac{\Vert{Ax}\Vert_p}{\Vert{x}\Vert_p}
$$

當向量取不同範數時, 相應得到了不同的矩陣範數。

- **矩陣的1範數（行範數）**：矩陣的每一行上的元素絕對值先求和，再從中取個最大的,（列和最大），上述矩陣$A$的1範數先得到$[5,8,9]$，再取最大的最終結果就是：9 。
$$
\Vert A\Vert_1=\max_{1\le j\le n}\sum_{i=1}^m|{a_{ij}}|
$$

- **矩陣的2範數**：矩陣$A^TA$的最大特徵值開平方根，上述矩陣$A$的2範數得到的最終結果是：10.0623。 
  
$$
\Vert A\Vert_2=\sqrt{\lambda_{max}(A^T A)}
$$

其中， $\lambda_{max}(A^T A)$ 為 $A^T A$ 的特徵值絕對值的最大值。
- **矩陣的無窮範數（列範數）**：矩陣的每一列上的元素絕對值先求和，再從中取個最大的，（列和最大），上述矩陣$A$的列範數先得到$[6；16]$，再取最大的最終結果就是：16。

$$
\Vert A\Vert_{\infty}=\max_{1\le i \le m}\sum_{j=1}^n |{a_{ij}}|
$$

- **矩陣的核範數**：矩陣的奇異值（將矩陣svd分解）之和，這個範數可以用來低秩表示（因為最小化核範數，相當於最小化矩陣的秩——低秩），上述矩陣A最終結果就是：10.9287。

- **矩陣的L0範數**：矩陣的非0元素的個數，通常用它來表示稀疏，L0範數越小0元素越多，也就越稀疏，上述矩陣$A$最終結果就是：6。
- **矩陣的L1範數**：矩陣中的每個元素絕對值之和，它是L0範數的最優凸近似，因此它也可以表示稀疏，上述矩陣$A$最終結果就是：22 。
- **矩陣的F範數**：矩陣的各個元素平方之和再開平方根，它通常也叫做矩陣的L2範數，它的優點在於它是一個凸函數，可以求導求解，易於計算，上述矩陣A最終結果就是：10.0995。  
  
$$
\Vert A\Vert_F=\sqrt{(\sum_{i=1}^m\sum_{j=1}^n{| a_{ij}|}^2)}
$$

- **矩陣的L21範數**：矩陣先以每一行為單位，求每一行的F範數（也可認為是向量的2範數），然後再將得到的結果求L1範數（也可認為是向量的1範數），很容易看出它是介於L1和L2之間的一種範數，上述矩陣$A$最終結果就是：17.1559。
- **矩陣的 p範數**
  
$$
\Vert A\Vert_p=\sqrt[p]{(\sum_{i=1}^m\sum_{j=1}^n{| a_{ij}|}^p)}
$$

### 1.1.5 如何判斷一個矩陣為正定

判定一個矩陣是否為正定，通常有以下幾個方面：

- 順序主子式全大於0；
- 存在可逆矩陣$C$使$C^TC$等於該矩陣；
- 正慣性指數等於$n$；
- 合同於單位矩陣$E$（即：規範形為$E$）
- 標準形中主對角元素全為正；
- 特徵值全為正；
- 是某基的度量矩陣。

## 1.2 導數和偏導數

### 1.2.1 導數偏導計算

**導數定義**:

導數(derivative)代表了在自變量變化趨於無窮小的時候，函數值的變化與自變量的變化的比值。幾何意義是這個點的切線。物理意義是該時刻的（瞬時）變化率。
​

*注意*：在一元函數中，只有一個自變量變動，也就是說只存在一個方向的變化率，這也就是為什麼一元函數沒有偏導數的原因。在物理學中有平均速度和瞬時速度之說。平均速度有

$$
v=\frac{s}{t}
$$

其中$v$表示平均速度，$s$表示路程，$t$表示時間。這個公式可以改寫為

$$
\bar{v}=\frac{\Delta s}{\Delta t}=\frac{s(t_0+\Delta t)-s(t_0)}{\Delta t}
$$

其中$\Delta s$表示兩點之間的距離，而$\Delta t$表示走過這段距離需要花費的時間。當$\Delta t$趨向於0（$\Delta t \to 0$）時，也就是時間變得很短時，平均速度也就變成了在$t_0$時刻的瞬時速度，表示成如下形式：

$$
v(t_0)=\lim_{\Delta t \to 0}{\bar{v}}=\lim_{\Delta t \to 0}{\frac{\Delta s}{\Delta t}}=\lim_{\Delta t \to 0}{\frac{s(t_0+\Delta t)-s(t_0)}{\Delta t}}
$$

實際上，上式表示的是路程$s$關於時間$t$的函數在$t=t_0$處的導數。一般的，這樣定義導數：如果平均變化率的極限存在，即有

$$
\lim_{\Delta x \to 0}{\frac{\Delta y}{\Delta x}}=\lim_{\Delta x \to 0}{\frac{f(x_0+\Delta x)-f(x_0)}{\Delta x}}
$$

則稱此極限為函數 $y=f(x)$ 在點 $x_0$ 處的導數。記作$f'(x_0)$ 或$y'\vert_{x=x_0}$ 或$\frac{dy}{dx}\vert_{x=x_0}$ 或$\frac{df(x)}{ dx}\vert_{x=x_0}$。

通俗地說，導數就是曲線在某一點切線的斜率。

**偏導數**:

既然談到偏導數(partial derivative)，那就至少涉及到兩個自變量。以兩個自變量為例，$z=f(x,y)$，從導數到偏導數，也就是從曲線來到了曲面。曲線上的一點，其切線只有一條。但是曲面上的一點，切線有無數條。而偏導數就是指多元函數沿著坐標軸的變化率。


*注意*：直觀地說，偏導數也就是函數在某一點上沿坐標軸正方向的的變化率。

設函數$z=f(x,y)$在點$(x_0,y_0)$的領域內有定義，當$y=y_0$時，$z$可以看作關於$x$的一元函數$f (x,y_0)$，若該一元函數在$x=x_0$處可導，即有

$$
\lim_{\Delta x \to 0}{\frac{f(x_0+\Delta x,y_0)-f(x_0,y_0)}{\Delta x}}=A
$$

函數的極限$A$存在。那麼稱$A$為函數$z=f(x,y)$在點$(x_0,y_0)$處關於自變量$x$的偏導數，記作$f_x(x_0,y_0)$或$\frac{\partial z}{\partial x}\vert_{y=y_0}^{x=x_0}$或$\frac{\partial f}{\partial x}\vert_{y=y_0}^{x= x_0}$或$z_x\vert_{y=y_0}^{x=x_0}$。

偏導數在求解時可以將另外一個變量看做常數，利用普通的求導方式求解，比如$z=3x^2+xy$關於$x$的偏導數就為$z_x=6x+y$，這個時候$y$相當於$x$的係數。

某點$(x_0,y_0)$處的偏導數的幾何意義為曲面$z=f(x,y)$與面$x=x_0$或面$y=y_0$交線在$y=y_0$或$x=x_0$處切線的斜率。  

### 1.2.2 導數和偏導數有什麼區別？
導數和偏導沒有本質區別，如果極限存在，都是當自變量的變化量趨於0時，函數值的變化量與自變量變化量比值的極限。

> - 一元函數，一個$y$對應一個$x$，導數只有一個。
> - 二元函數，一個$z$對應一個$x$和一個$y$，有兩個導數：一個是$z$對$x$的導數，一個是$z$對$y$的導數，稱之為偏導。
> - 求偏導時要注意，對一個變量求導，則視另一個變量為常數，只對改變量求導，從而將偏導的求解轉化成了一元函數的求導。

## 1.3 特徵值和特徵向量

### 1.3.1 特徵值分解與特徵向量

- 特徵值分解可以得到特徵值(eigenvalues)與特徵向量(eigenvectors)；

- 特徵值表示的是這個特徵到底有多重要，而特徵向量表示這個特徵是什麼。

  如果說一個向量$\vec{v}$是方陣$A$的特徵向量，將一定可以表示成下面的形式：
  
$$
A\nu = \lambda \nu
$$

$\lambda$為特徵向量$\vec{v}$對應的特徵值。特徵值分解是將一個矩陣分解為如下形式： 
    
$$
A=Q\sum Q^{-1}
$$

其中，$Q$是這個矩陣$A$的特徵向量組成的矩陣，$\sum$是一個對角矩陣，每一個對角線元素就是一個特徵值，裡面的特徵值是由大到小排列的，這些特徵值所對應的特徵向量就是描述這個矩陣變化方向（從主要的變化到次要的變化排列）。也就是說矩陣$A$的信息可以由其特徵值和特徵向量表示。

### 1.3.2 奇異值與特徵值有什麼關係
那麼奇異值和特徵值是怎麼對應起來的呢？我們將一個矩陣$A$的轉置乘以$A$，並對$A^TA$求特徵值，則有下面的形式：

$$
(A^TA)V = \lambda V
$$

這裡$V$就是上面的右奇異向量，另外還有：

$$
\sigma_i = \sqrt{\lambda_i}, u_i=\frac{1}{\sigma_i}AV
$$

這裡的$\sigma$就是奇異值，$u$就是上面說的左奇異向量。 【證明那個哥們也沒給】
​奇異值$\sigma$跟特徵值類似，在矩陣$\sum$中也是從大到小排列，而且$\sigma$的減少特別的快，在很多情況下，前10%甚至1%的奇異值的和就佔了全部的奇異值之和的99%以上了。也就是說，我們也可以用前$r$（$r$遠小於$m、n$）個的奇異值來近似描述矩陣，即部分奇異值分解：

$$
A_{m\times n}\approx U_{m \times r}\sum_{r\times r}V_{r \times n}^T
$$

右邊的三個矩陣相乘的結果將會是一個接近於$A$的矩陣，在這兒，$r$越接近於$n$，則相乘的結果越接近於$A$。

## 1.4 概率分佈與隨機變量

### 1.4.1 機器學習為什麼要使用概率

事件的概率是衡量該事件發生的可能性的量度。雖然在一次隨機試驗中某個事件的發生是帶有偶然性的，但那些可在相同條件下大量重複的隨機試驗卻往往呈現出明顯的數量規律。
​機器學習除了處理不確定量，也需處理隨機量。不確定性和隨機性可能來自多個方面，使用概率論來量化不確定性。
​概率論在機器學習中扮演著一個核心角色，因為機器學習算法的設計通常依賴於對數據的概率假設。

> 例如在機器學習（Andrew Ng）的課中，會有一個樸素貝葉斯假設就是條件獨立的一個例子。該學習算法對內容做出假設，用來分辨電子郵件是否為垃圾郵件。假設無論郵件是否為垃圾郵件，單詞x出現在郵件中的概率條件獨立於單詞y。很明顯這個假設不是不失一般性的，因為某些單詞幾乎總是同時出現。然而，最終結果是，這個簡單的假設對結果的影響並不大，且無論如何都可以讓我們快速判別垃圾郵件。

### 1.4.2 變量與隨機變量有什麼區別
**隨機變量**（random variable）

表示隨機現象（在一定條件下，並不總是出現相同結果的現象稱為隨機現象）中各種結果的實值函數（一切可能的樣本點）。例如某一時間內公共汽車站等車乘客人數，電話交換台在一定時間內收到的呼叫次數等，都是隨機變量的實例。
​隨機變量與模糊變量的不確定性的本質差別在於，後者的測定結果仍具有不確定性，即模糊性。

**變量與隨機變量的區別：**
​當變量的取值的概率不是1時,變量就變成了隨機變量；當隨機變量取值的概率為1時,隨機變量就變成了變量。

> 比如：
> ​ 當變量$x$值為100的概率為1的話,那麼$x=100$就是確定了的,不會再有變化,除非有進一步運算.
> ​ 當變量$x$的值為100的概率不為1,比如為50的概率是0.5,為100的概率是0.5,那麼這個變量就是會隨不同條件而變化的,是隨機變量,取到50或者100的概率都是0.5,即50%。  

### 1.4.3 隨機變量與概率分佈的聯繫

一個隨機變量僅僅表示一個可能取得的狀態，還必須給定與之相伴的概率分佈來製定每個狀態的可能性。用來描述隨機變量或一簇隨機變量的每一個可能的狀態的可能性大小的方法，就是 **概率分佈(probability distribution)**.

隨機變量可以分為離散型隨機變量和連續型隨機變量。

相應的描述其概率分佈的函數是

概率質量函數(Probability Mass Function, PMF):描述離散型隨機變量的概率分佈，通常用大寫字母 $P$表示。

概率密度函數(Probability Density Function, PDF):描述連續型隨機變量的概率分佈，通常用小寫字母$p$表示。

### 1.4.4 離散型隨機變量和概率質量函數

PMF 將隨機變量能夠取得的每個狀態映射到隨機變量取得該狀態的概率。

- 一般而言，$P(x)$ 表示時$X=x$的概率.
- 有時候為了防止混淆，要明確寫出隨機變量的名稱$P($x$=x)$
- 有時候需要先定義一個隨機變量，然後製定它遵循的概率分佈x服從$P($x$)$

PMF 可以同時作用於多個隨機變量，即聯合概率分佈(joint probability distribution) $P(X=x,Y=y)$*表示$X=x$和$Y=y$同時發生的概率，也可以簡寫成$P(x,y)$.

如果一個函數$P$是隨機變量 $X$ 的 PMF， 那麼它必須滿足如下三個條件

- $P$的定義域必須是的所有可能狀態的集合
- $∀x∈$x, $0 \leq P(x) \leq 1 $.
- $∑_{x∈X} P(x)=1$. 我們把這一條性質稱之為 歸一化的(normalized)

### 1.4.5 連續型隨機變量和概率密度函數

如果一個函數$p$是x的PDF，那麼它必須滿足如下幾個條件

- $p$的定義域必須是x的所有可能狀態的集合。
- $∀x∈X,p(x)≥0$. 注意，我們並不要求$ p(x)≤1$，因為此處$p(x)$不是表示的對應此狀態具體的概率，而是概率的一個相對大小(密度)。具體的概率，需要積分去求。
- $∫p(x)dx=1$, 積分下來，總和還是1，概率之和還是1.

注：PDF$p(x)$並沒有直接對特定的狀態給出概率，給出的是密度，相對的，它給出了落在面積為$δx$的無線小的區域內的概率為$ p(x)δx$. 由此，我們無法求得具體某個狀態的概率，我們可以求得的是某個狀態$x$ 落在某個區間$[a,b]$內的概率為$ \int_{a}^{b}p(x)dx$.

### 1.4.6 舉例理解條件概率

條件概率公式如下：
$$
P(A|B) = P(A\cap B) / P(B)
$$
說明：在同一個樣本空間$\Omega$中的事件或者子集$A$與$B$，如果隨機從$\Omega$中選出的一個元素屬於$B$，那麼下一個隨機選擇的元素屬於$A$ 的概率就定義為在$B$的前提下$A$的條件概率。條件概率文氏圖示意如圖1.1所示。  
![条件概率](/public/img/deep-learning-01/conditional_probability.jpg)

圖1.1 條件概率文氏圖示意

根據文氏圖，可以很清楚地看到在事件B發生的情況下，事件A發生的概率就是$P(A\bigcap B)$除以$P(B)$。
​舉例：一對夫妻有兩個小孩，已知其中一個是女孩，則另一個是女孩子的概率是多少？ （面試、筆試都碰到過）
​**窮舉法**：已知其中一個是女孩，那麼樣本空間為男女，女女，女男，則另外一個仍然是女生的概率就是1/3。
​**條件概率法**：$P(女|女)=P(女女)/P(女)$,夫妻有兩個小孩，那麼它的樣本空間為女女，男女，女男，男男，則$P(女女)$為1/4，$P（女）= 1-P(男男)=3/4$,所以最後$1/3$。
這里大家可能會誤解，男女和女男是同一種情況，但實際上類似姐弟和兄妹是不同情況。 

### 1.4.7 聯合概率與邊緣概率聯繫區別

**區別：**
​聯合概率：聯合概率指類似於$P(X=a,Y=b)$這樣，包含多個條件，且所有條件同時成立的概率。聯合概率是指在多元的概率分佈中多個隨機變量分別滿足各自條件的概率。
​邊緣概率：邊緣概率是某個事件發生的概率，而與其它事件無關。邊緣概率指類似於$P(X=a)$，$P(Y=b)$這樣，僅與單個隨機變量有關的概率。

**聯繫：**
​聯合分佈可求邊緣分佈，但若只知道邊緣分佈，無法求得聯合分佈。  

### 1.4.8 條件概率的鍊式法則

由條件概率的定義，可直接得出下面的乘法公式：
​乘法公式 設$A, B$是兩個事件，並且$P(A) > 0$, 則有
$$
P(AB) = P(B|A)P(A)
$$
推廣 
$$
P(ABC)=P(C|AB)P(B|A)P(A)
$$
一般地，用歸納法可證：若$P(A_1A_2...A_n)>0$，則有
$$
P(A_1A_2...A_n)=P(A_n|A_1A_2...A_{n-1})P(A_{n-1}|A_1A_2...A_{n-2})...P(A_2|A_1)P(A_1)
=P(A_1)\prod_{i=2}^{n}P(A_i|A_1A_2...A_{i-1})
$$
任何多維隨機變量聯合概率分佈，都可以分解成只有一個變量的條件概率相乘形式。

### 1.4.9 獨立性和條件獨立性

**獨立性**
​兩個隨機變量$x$和$y$，概率分佈表示成兩個因子乘積形式，一個因子只包含$x$，另一個因子只包含$y$，兩個隨機變量相互獨立(independent)。
​條件有時為不獨立的事件之間帶來獨立，有時也會把本來獨立的事件，因為此條件的存在，而失去獨立性。
​舉例：$P(XY)=P(X)P(Y)$, 事件$X$和事件$Y$獨立。此時給定$Z$，
$$
P(X,Y|Z) \not = P(X|Z)P(Y|Z)
$$
事件獨立時，聯合概率等於概率的乘積。這是一個非常好的數學性質，然而不幸的是，無條件的獨立是十分稀少的，因為大部分情況下，事件之間都是互相影響的。

**條件獨立性**
​給定$Z$的情況下,$X$和$Y$條件獨立，當且僅當
$$
X\bot Y|Z \iff P(X,Y|Z) = P(X|Z)P(Y|Z)
$$
$X$和$Y$的關係依賴於$Z$，而不是直接產生。

> **舉例**定義如下事件：
> $X$：明天下雨；
> $Y$：今天的地面是濕的；
> $Z$：今天是否下雨；
> $Z$事件的成立，對$X$和$Y$均有影響，然而，在$Z$事件成立的前提下，今天的地面情況對明天是否下雨沒有影響。 

## 1.5 常見概率分佈

### 1.5.1 Bernoulli分佈

**Bernoulli分佈**(伯努利分佈，0-1分佈)是單個二值隨機變量分佈, 單參數$\phi$∈[0,1]控制,$\phi$給出隨機變量等於1的概率. 主要性質有: 
$$
\begin{align*}
P(x=1) &= \phi \\
P(x=0) &= 1-\phi  \\
概率質量函數：P(x=x) &= \phi^x(1-\phi)^{1-x} \\
\end{align*}
$$
其期望和方差為：
$$
\begin{align*}
E_x[x] &= \phi \\
Var_x(x) &= \phi{(1-\phi)}
\end{align*}
$$
**適用範圍**: **伯努利分佈**適合對**離散型**隨機變量建模.

**Multinoulli分佈**也叫**範疇分佈**, 是單個*k*值隨機分佈,經常用來表示**對象分類的分佈**. 其中$k$是有限值.Multinoulli分佈由向量$ \vec{p}\in[0,1]^{k-1}$參數化,每個分量$p_i$表示第$i$個狀態的概率, 且$p_k=1-1^Tp$.這裡$1^T$表示元素全為1的列向量的轉置，其實就是對於向量p中除了k的概率之和。可以重寫為$p_k=1-\sum_{0}^{k-1}p_i$ 。

補充二項分佈、多項分佈：

二項分佈，通俗點硬幣拋多次。二項分佈(Binomial distribution)是**n重伯努利試驗**成功次數的離散概率分佈。

多項式分佈(Multinomial Distribution)是二項式分佈的推廣。二項式做n次伯努利實驗，規定了每次試驗的結果只有兩個，如果現在還是做n次試驗，只不過每次試驗的結果可以有多m個，且m個結果發生的概率互斥且和為1，則發生其中一個結果X次的概率就是多項式分佈。

### 1.5.2 高斯分佈

高斯也叫正態分佈(Normal Distribution), 概率度函數如下:  
$$
N(x;\mu,\sigma^2) = \sqrt{\frac{1}{2\pi\sigma^2}}exp\left ( -\frac{1}{2\sigma^2}(x-\mu)^2 \right )
$$
其中, $\mu$和$\sigma$分別是均值和方差, 中心峰值x坐標由$\mu$給出, 峰的寬度受$\sigma$控制, 最大點在$x=\mu$處取得, 拐點為$x=\mu\pm\sigma$

正態分佈中，±1$\sigma$、±2$\sigma$、±3$\sigma$下的概率分別是68.3%、95.5%、99.73%，這3個數最好記住。 

此外, 令$\mu=0,\sigma=1$高斯分佈即簡化為標準正態分佈:
$$
N(x;\mu,\sigma^2) = \sqrt{\frac{1}{2\pi}}exp\left ( -\frac{1}{2}x^2 \right )
$$
對概率密度函數高效求值: 
$$
N(x;\mu,\beta^{-1})=\sqrt{\frac{\beta}{2\pi}}exp\left(-\frac{1}{2}\beta(x-\mu)^2\right)
$$


其中，$\beta=\frac{1}{\sigma^2}$通過參數$\beta∈（0，\infty）$來控制分布精度。

### 1.5.3 何時採用正態分佈

問: 何時採用正態分佈?
答: 缺乏實數上分佈的先驗知識, 不知選擇何種形式時, 默認選擇正態分佈總是不會錯的, 理由如下:

1. 中心極限定理告訴我們, 很多獨立隨機變量均近似服從正態分佈, 現實中很多複雜系統都可以被建模成正態分佈的噪聲, 即使該系統可以被結構化分解.
2. 正態分佈是具有相同方差的所有概率分佈中, 不確定性最大的分佈, 換句話說, 正態分佈是對模型加入先驗知識最少的分佈.

正態分佈的推廣:
正態分佈可以推廣到$R^n$空間, 此時稱為**多位正態分佈**, 其參數是一個正定對稱矩陣$\Sigma$: 
$$
N(x;\vec\mu,\Sigma)=\sqrt{\frac{1}{(2\pi)^ndet(\Sigma)}}exp\left(-\frac{1}{2}(\vec{x}-\vec{\mu})^T\Sigma^{-1}(\vec{x}-\vec{\mu})\right)
$$
對多為正態分佈概率密度高效求值: 
$$
N(x;\vec{\mu},\vec\beta^{-1}) = \sqrt{det(\vec\beta)}{(2\pi)^n}exp\left(-\frac{1}{2}(\vec{x}-\vec\mu)^T\beta(\vec{x}-\vec\mu)\right)
$$
此處，$\vec\beta$是一個精度矩陣。

### 1.5.4 指數分佈

深度學習中, 指數分佈用來描述在$x=0$點處取得邊界點的分佈, 指數分佈定義如下:
$$
p(x;\lambda)=\lambda I_{x\geq 0}exp(-\lambda{x})
$$
指數分佈用指示函數$I_{x\geq 0}$來使$x$取負值時的概率為零。

### 1.5.5 Laplace 分佈（拉普拉斯分佈）

一個聯繫緊密的概率分佈是 Laplace 分佈（Laplace distribution），它允許我們在任意一點 $\mu$處設置概率質量的峰值
$$
Laplace(x;\mu;\gamma)=\frac{1}{2\gamma}exp\left(-\frac{|x-\mu|}{\gamma}\right)
$$

### 1.5.6 Dirac分佈和經驗分佈

Dirac分佈可保證概率分佈中所有質量都集中在一個點上. Diract分佈的狄拉克$\delta$函數(也稱為**單位脈衝函數**)定義如下: 
$$
p(x)=\delta(x-\mu), x\neq \mu
$$

$$
\int_{a}^{b}\delta(x-\mu)dx = 1, a < \mu < b
$$

Dirac 分佈經常作為 經驗分佈（empirical distribution）的一個組成部分出現
$$
\hat{p}(\vec{x})=\frac{1}{m}\sum_{i=1}^{m}\delta(\vec{x}-{\vec{x}}^{(i)})
$$
, 其中, m個點$x^{1},...,x^{m}$是給定的數據集, **經驗分佈**將概率密度$\frac{1}{m}$賦給了這些點.

當我們在訓練集上訓練模型時, 可以認為從這個訓練集上得到的經驗分佈指明了**採樣來源**.

**適用範圍**: 狄拉克δ函數適合對**連續型**隨機變量的經驗分佈.


## 1.6 期望、方差、協方差、相關係數
### 1.6.1 期望

在概率論和統計學中，數學期望（或均值，亦簡稱期望）是試驗中每次可能結果的概率乘以其結果的總和。它反映隨機變量平均取值的大小。

- 線性運算： $E(ax+by+c) = aE(x)+bE(y)+c$
- 推廣形式： $E(\sum_{k=1}^{n}{a_ix_i+c}) = \sum_{k=1}^{n}{a_iE(x_i)+c}$
- 函數期望：設$f(x)$為$x$的函數，則$f(x)$的期望為
    - 離散函數： $E(f(x))=\sum_{k=1}^{n}{f(x_k)P(x_k)}$
    - 連續函數： $E(f(x))=\int_{-\infty}^{+\infty}{f(x)p(x)dx}$

> 注意：
>
> - 函數的期望大於等於期望的函數（Jensen（詹森）不等式，即$E(f(x))\geqslant f(E(x))$
> - 一般情況下，乘積的期望不等於期望的乘積。
> - 如果$X$和$Y$相互獨立，則$E(xy)=E(x)E(y)$。

### 1.6.2 方差

概率論中方差用來度量隨機變量和其數學期望（即均值）之間的偏離程度。方差是一種特殊的期望。定義為：

$$
Var(x) = E((x-E(x))^2)
$$

> 方差性質：
>
> 1）$Var(x) = E(x^2) -E(x)^2$
> 2）常數的方差為0;
> 3）方差不滿足線性性質;
> 4）如果$X$和$Y$相互獨立, $Var(ax+by)=a^2Var(x)+b^2Var(y)$

### 1.6.3 協方差

協方差是衡量兩個變量線性相關性強度及變量尺度。兩個隨機變量的協方差定義為：
$$
Cov(x,y)=E((x-E(x))(y-E(y)))
$$

方差是一種特殊的協方差。當$X=Y$時，$Cov(x,y)=Var(x)=Var(y)$。

> 協方差性質：
>
> 1）獨立變量的協方差為0。
> 2）協方差計算公式：

$$
Cov(\sum_{i=1}^{m}{a_ix_i}, \sum_{j=1}^{m}{b_jy_j}) = \sum_{i=1}^{m} \sum_{j=1}^{m}{a_ib_jCov(x_iy_i)}
$$

>
> 3）特殊情況：

$$
Cov(a+bx, c+dy) = bdCov(x, y)
$$

### 1.6.4 相關係數

相關係數是研究變量之間線性相關程度的量。兩個隨機變量的相關係數定義為：
$$
Corr(x,y) = \frac{Cov(x,y)}{\sqrt{Var(x)Var(y)}}
$$

> 相關係數的性質：
> 1）有界性。相關係數的取值範圍是 [-1,1]，可以看成無量綱的協方差。
> 2）值越接近1，說明兩個變量正相關性（線性）越強。越接近-1，說明負相關性越強，當為0時，表示兩個變量沒有相關性。  



## 參考文獻

[1]Ian，Goodfellow，Yoshua，Bengio，Aaron...深度學習[M]，人民郵電出版，2017

[2]周志華.機器學習[M].清華大學出版社，2016.

[3]同濟大學數學系.高等數學（第七版）[M]，高等教育出版社，2014.

[4]盛驟，試式千，潘承毅等編. 概率論與數理統計（第4版）[M]，高等教育出版社，2008
