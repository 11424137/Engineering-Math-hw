# 工程數學筆記

## 1. 拉普拉斯轉換 (Laplace Transform)

**題目：**
求解微分方程式：
$$\frac{d^2x(t)}{dt^2} + 6\frac{dx(t)}{dt} + 8x(t) = 1$$

**已知初始條件：**
* $x(0) = 1$
* $x'(0) = 0$

---

### 步驟說明：

1. **基本公式與轉換：**
   * $\mathcal{L}\{x''(t)\} = s^2X(s) - sx(0) - x'(0)$
   * $\mathcal{L}\{x'(t)\} = sX(s) - x(0)$
   * $\mathcal{L}\{1\} = \frac{1}{s}$

2. **帶入初始條件：**
   * $\mathcal{L}\{x''(t)\} = s^2X(s) - s$
   * $\mathcal{L}\{x'(t)\} = sX(s) - 1$

3. **將轉換後的式子帶回原微分方程式：**
   $$(s^2X(s) - s) + 6(sX(s) - 1) + 8X(s) = \frac{1}{s}$$

4. **整理並求解 $X(s)$：**
   $$(s^2 + 6s + 8)X(s) - s - 6 = \frac{1}{s}$$
   $$(s^2 + 6s + 8)X(s) = s + 6 + \frac{1}{s}$$
   $$(s^2 + 6s + 8)X(s) = \frac{s^2 + 6s + 1}{s}$$
   $$X(s) = \frac{s^2 + 6s + 1}{s(s+2)(s+4)}$$

5. **部分分式展開 (Partial Fraction Expansion)：**
   $$X(s) = \frac{A}{s} + \frac{B}{s+2} + \frac{C}{s+4}$$
   
   * **求 $A$：**
     $$A = \left. \frac{s^2 + 6s + 1}{(s+2)(s+4)} \right|_{s=0} = \frac{1}{8}$$
   * **求 $B$：**
     $$B = \left. \frac{s^2 + 6s + 1}{s(s+4)} \right|_{s=-2} = \frac{4 - 12 + 1}{-2(2)} = \frac{7}{4}$$
   * **求 $C$：**
     $$C = \left. \frac{s^2 + 6s + 1}{s(s+2)} \right|_{s=-4} = \frac{16 - 24 + 1}{-4(-2)} = -\frac{7}{8}$$

   **帶回 $X(s)$：**
   $$X(s) = \frac{1}{8s} + \frac{7}{4(s+2)} - \frac{7}{8(s+4)}$$

6. **反拉普拉斯轉換 (Inverse Laplace Transform)：**
   $$x(t) = \frac{1}{8} + \frac{7}{4}e^{-2t} - \frac{7}{8}e^{-4t} \quad (t \ge 0)$$

**最終答案：**
$$\underline{\underline{x(t) = \frac{1}{8} + \frac{7}{4}e^{-2t} - \frac{7}{8}e^{-4t} \quad (t \ge 0)}}$$

---

## 2. 傅立葉級數 (Fourier Series)

**題目：**
求週期函數之傅立葉級數（範圍為 $-\pi$ 到 $\pi$），函數為 $f(x) = x^2$

**公式：**
$$f(x) = a_0 + \sum_{n=1}^{\infty} a_n \cos(nx)$$

---

### 步驟說明：

1. **計算 $a_0$：**
   $$a_0 = \frac{1}{2\pi} \int_{-\pi}^{\pi} x^2 dx = \frac{1}{\pi} \int_{0}^{\pi} x^2 dx$$
   $$a_0 = \frac{1}{\pi} \left[ \frac{1}{3}x^3 \right]_{0}^{\pi} = \frac{1}{\pi} \cdot \frac{\pi^3}{3} = \frac{\pi^2}{3}$$

2. **計算 $a_n$（使用速積法 / 表格法）：**
   
   * **微分項遞減：**
     $$x^2 \rightarrow 2x \rightarrow 2 \rightarrow 0$$
   * **積分項遞增：**
     $$\cos(nx) \rightarrow \frac{1}{n}\sin(nx) \rightarrow -\frac{1}{n^2}\cos(nx) \rightarrow -\frac{1}{n^3}\sin(nx)$$
   
   **正負相乘結合後得到積分結果：**
   $$\int x^2 \cos(nx) dx = x^2\left(\frac{\sin(nx)}{n}\right) - 2x\left(-\frac{\cos(nx)}{n^2}\right) + 2\left(-\frac{\sin(nx)}{n^3}\right)$$

   **帶入上下限 $[0, \pi]$ 計算：** *(註：因 $\sin(n\pi) = 0$ 且 $\sin(0) = 0$，$\sin$ 項皆消去)*
   $$a_n = \frac{2}{\pi} \left[ \frac{2x \cos(nx)}{n^2} \right]_{0}^{\pi}$$
   $$a_n = \frac{2}{\pi} \left( \frac{2\pi \cos(n\pi)}{n^2} - 0 \right) = \frac{4}{n^2}\cos(n\pi)$$
   
   因 $\cos(n\pi) = (-1)^n$，故：
   $$a_n = \frac{4(-1)^n}{n^2}$$

3. **得出最終傅立葉級數：**
   $$\underline{\underline{f(x) = \frac{\pi^2}{3} + \sum_{n=1}^{\infty} \frac{4(-1)^n}{n^2} \cos(nx)}}$$

---
**學號：** 11424137  
**姓名：** 楊維倫
