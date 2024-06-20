# 基底

## 定义
线性空间$V$的极大线性无关组称为$V$的一组*基*

## 基扩充定理
设$V$是有限维线性空间. 如果$S\subset V$是线性无关集，则存在$V$的基底$T$使得$S \subset T$

## 线性映射基本定理II
设$V$的一组基为$\boldsymbol v_1, \cdots, \boldsymbol v_n$, $W$是$F$上的线性空间且$\boldsymbol w_1, \cdots, \boldsymbol w_n \in W$. 则存在唯一的线性映射$\phi: V \to W$使得
$$
\phi(\boldsymbol v_1) = \boldsymbol w_1 , \cdots,\phi(\boldsymbol v_n) = \boldsymbol w_n
$$
## 子空间直和的基底
设$U = V_1 \oplus \cdots \oplus V_k$且$B_i$为$V_i$的基底，那么$B_1 \cup \cdots \cup B_k$是$U$的一组基

# 维数
## 定义
线性空间$V$的一组基的向量个数为$V$的*维数*

## 线性同构的维数判定
设$V, W$是$F$上的有限维线性空间，则$V$和$W$同构当且仅当$\dim(V) = \dim(W)$. 特别地，当$\dim_F(V) = n$时, $V$和$F^n$线性同构。这告诉我们，**可以通过一个线性同构将任意$n$维子空间当作（转化为）坐标空间$F^n$来处理**

## 维数公式
### [[Quotient Space|商空间]]的维数
设$U$是$V$的子空间，则
$$
\dim(V/ U) =\dim(V) -\dim(U)
$$
### 子空间维数
设$U$是$V$的子空间，则$U \neq V$当且仅当$\dim(U) < \dim(V)$

### 子空间和的维数
$$
\dim(V_1) + \dim(V_2) = \dim(V_1 + V_2) + \dim(V_1 \cap V_2)
$$
及
$$
\dim(V_1 + \cdots + V_k) \le \dim(V_1) + \cdots + \dim(V_k)
$$
等号成立当且仅当$V_1 + \cdots + V_k$是直和

### 对偶定理
设$\phi: V \to W$是线性映射，则
$$
\dim(\ker \phi) + \dim(\operatorname{im} \phi) = \dim(V)
$$


