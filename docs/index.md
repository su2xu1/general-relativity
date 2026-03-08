<script>
  MathJax = {
    options: {
      renderActions: {
        findScript: [10, function (doc) {
          for (const node of document.querySelectorAll('script[type^="math/tex"]')) {
            const display = !!node.type.match(/; *mode=display/);
            const math = new doc.options.MathItem(node.textContent, doc.inputJax[0], display);
            const text = document.createTextNode('');
            node.parentNode.insertBefore(text, node);
            math.start = {node: text, delim: '', n: 0};
            math.end   = {node: text, delim: '', n: 0};
            doc.math.push(math);
            node.parentNode.removeChild(node);
          }
        }, '']
      }
    }
  };
</script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"></script>
重力波の導出に関するノート

アインシュタイン方程式から出発して、重力波を導出することはできないだろうか？
多くの仮定を伴うものの、導き出すことができた。

まず、計量 $$g_{ik}$$
を考える。平坦な時空からの非常に小さな摂動（弱い重力場）を想定し、次のように表す。
$$
\begin{equation}
g_{ik} = g_{ik}^{(0)} + h_{ik} \quad (h_{ik} \ll 1) \tag{107.1}
\end{equation}
$$

反変テンソル $$g^{ik}$$
については、$$g_{il}g^{lk} = (g_{il}^{(0)} + h_{il})g^{lk} = \delta_i^k$$
を満たす必要があるため、適切な $$g^{ik}$$ の形を考える。

$$g^{ik} = g^{(0)ik} - h^{ik} + h^i_l h^{lk}$$ ならば、
$$
\begin{align*}
g_{il}g^{lk} &= (g_{il}^{(0)} + h_{il})(g^{(0)ik} - h^{ik} + h^i_l h^{lk}) \\
\delta_i^k &= g^{(0)}_{il}g^{(0)lk} - g_{il}^{(0)}h^{lk} + g_{il}^{(0)}h^l_m h^{mk} + h_{il}g^{(0)lk} - h_{il}h^{lk} + h_{il}h^l_m h^{mk}
\end{align*}
$$
となり、$$O(h^3)$$ で等しくなる。
あらためて、$$g^{ik} = g^{(0)ik} - h^{ik} + h^i_l h^{lk}$$ とする。

行列式も $$g = g^{(0)}(1+h) \quad (h \equiv h^i_i)$$ と近似する。

次に、微小な座標変換 $$x'^i = x^i + \xi^i$$ を考える。前提として
$$\xi^i \ll 1$$ とする。

テンソルの定義より、
$$
\begin{align*}
g'^{ik}(x'^l) &= g^{nm}(x^l) \frac{\partial x'^i}{\partial x^n} \frac{\partial x'^k}{\partial x^m} \\
&= g^{nm} \left( \delta^i_n + \frac{\partial \xi^i}{\partial x^n} \right) \left( \delta^k_m + \frac{\partial \xi^k}{\partial x^m} \right) \\
&\simeq g^{nm}(x^l) \left( \delta^i_n\delta^k_m + \delta^i_n\frac{\partial \xi^k}{\partial x^m} + \delta^k_m\frac{\partial \xi^i}{\partial x^n} \right) \\
&= g^{ik}(x^l) + g^{im} \frac{\partial \xi^k}{\partial x^m} + g^{kn} \frac{\partial \xi^i}{\partial x^n}
\end{align*}
$$

$$g'^{ik}(x'^l)$$ （すなわち $$g'^{ik}(x^l + \xi^l)$$）を $$\xi$$
の冪乗で展開し、
$$
\begin{align*}
g'^{ik}(x^l + \xi^l) &= \sum \frac{\xi^n}{n!} \frac{\partial g^{(n)'ik}(x^l)}{\partial x^n} \\
&\rightarrow g'^{ik}(x^l) + \xi^l \frac{\partial g'^{ik}(x^l)}{\partial x^l} \\
&\rightarrow g'^{ik}(x^l) + \xi^l \frac{\partial g^{ik}(x^l)}{\partial x^l}
\end{align*}
$$

したがって、
$$
\begin{align*}
g'^{ik}(x^l) + \xi^l \frac{\partial g^{ik}(x^l)}{\partial x^l} &= g^{ik}(x^l) + g^{im} \frac{\partial \xi^k}{\partial x^m} + g^{kn} \frac{\partial \xi^i}{\partial x^n} \\
g'^{ik}(x^l) &= g^{ik}(x^l) - \xi^l \frac{\partial g^{ik}(x^l)}{\partial x^l} + g^{im} \frac{\partial \xi^k}{\partial x^m} + g^{kn} \frac{\partial \xi^i}{\partial x^n} \\
g'^{ik}(x^l) &= g^{ik}(x^l) + \delta g^{ik} \quad (\delta g^{ik} = \xi^{i,k} + \xi^{k;i} \quad \text{※反変導関数の和}) \\
g'^{(0)ik}(x^l) - h'^{ik} &= g^{(0)ik}(x^l) - h^{ik} + \delta g^{ik} \\
h'^{ik} &= h^{ik} - \delta g^{ik} \\
h'^{ik} &= h^{ik} - \frac{\partial \xi^k}{\partial x_i} - \frac{\partial \xi^i}{\partial x_k}
\end{align*}
$$

同様に共変成分については、
$$
\begin{align*}
g'_{ik}(x^l) &= g_{ik}(x^l) + \delta g_{ik} \quad (\delta g_{ik} = -\xi_{i,k} - \xi_{k;i}) \\
g'_{(0)ik}(x^l) + h'_{ik} &= g_{(0)ik}(x^l) + h_{ik} + \delta g_{ik} \\
h'_{ik} &= h_{ik} - \frac{\partial \xi_k}{\partial x^i} - \frac{\partial \xi_i}{\partial x^k} \tag{107.4}
\end{align*}
$$

補助条件を $$h_{ik}$$ に与える（いわゆるゲージ固定）。
$$
\begin{equation}
\frac{\partial \phi^k_i}{\partial x^k}=0 \quad \left( \phi^k_i = h^k_i - \frac{1}{2}\delta^k_i h \right) \tag{107.5}
\end{equation}
$$

リッチ・テンソルから、
$$
\begin{equation}
R_{ik} = \frac{\partial \Gamma^l_{ik}}{\partial x^l} - \frac{\partial \Gamma^l_{il}}{\partial x^k} + \Gamma^l_{ik}\Gamma^m_{lm} - \Gamma^m_{il}\Gamma^l_{km} \tag{92.7}
\end{equation}
$$
$$
\begin{equation*}
\delta A_i = \Gamma^m_{il}A_m dx^i
\end{equation*}
$$

共変曲率テンソルの形がどうなるか考える。
$$
\begin{equation}
R_{iklm} = \frac{1}{2} \left(
\frac{\partial^2 g_{im}}{\partial x^k\partial x^l} + \frac{\partial^2 g_{kl}}{\partial x^i\partial x^m} - \frac{\partial^2 g_{il}}{\partial x^k\partial x^m} - \frac{\partial^2 g_{km}}{\partial x^i\partial x^l}
\right) + g_{np}(\Gamma^n_{kl}\Gamma^p_{im} - \Gamma^n_{km}\Gamma^p_{il}) \tag{92.1}
\end{equation}
$$

$$h_{ik} \ll 1$$ という弱い重力場の条件下では $$\Gamma^i_{kl} \ll 1$$
と見なすことが妥当。ゆえに
$$
\begin{equation*}
(\Gamma^m_{kl}\Gamma^p_{im} - \Gamma^m_{km}\Gamma^p_{il}) \rightarrow 0
\end{equation*}
$$

したがって $$R_{iklm}$$ は以下の形が妥当である。
$$
\begin{equation*}
R_{iklm} = \frac{1}{2} \left(
\frac{\partial^2 g_{im}}{\partial x^k\partial x^l} + \frac{\partial^2 g_{kl}}{\partial x^i\partial x^m} - \frac{\partial^2 g_{il}}{\partial x^k\partial x^m} - \frac{\partial^2 g_{km}}{\partial x^i\partial x^l}
\right)
\end{equation*}
$$
$$R_{ik}$$については、以下のように近似できるとした。
$$
\begin{equation*}
R_{ik} = g^{lm}R_{limk} \simeq g^{(0)lm}R_{limk}
\end{equation*}
$$
よって、
$$
\begin{align*}
R_{ik} &= g^{(0)lm} \frac{1}{2} \left(
\frac{\partial^2 g_{lk}}{\partial x^i\partial x^m} + \frac{\partial^2 g_{im}}{\partial x^l\partial x^k} - \frac{\partial^2 g_{lm}}{\partial x^i\partial x^k} - \frac{\partial^2 g_{ik}}{\partial x^l\partial x^m}
\right) \\
&= \frac{1}{2} \left(
g^{(0)lm}\frac{\partial^2 g_{lk}}{\partial x^i\partial x^m} + g^{(0)lm}\frac{\partial^2 g_{im}}{\partial x^l\partial x^k} - g^{(0)lm}\frac{\partial^2 g_{lm}}{\partial x^i\partial x^k} - g^{(0)lm}\frac{\partial^2 g_{ik}}{\partial x^l\partial x^m}
\right)
\end{align*}
$$

$$g_{ik} = g^{(0)}_{ik} + h_{ik}$$ だから、
$$
\begin{align*}
R_{ik} &= \frac{1}{2} \left(
-g^{(0)lm}\frac{\partial^2 h_{ik}}{\partial x^l\partial x^m} + g^{(0)lm}\frac{\partial^2 h_{im}}{\partial x^l\partial x^k} + g^{(0)lm}\frac{\partial^2 h_{lk}}{\partial x^i\partial x^m} - g^{(0)lm}\frac{\partial^2 h_{lm}}{\partial x^i\partial x^k}
\right) \\
&= \frac{1}{2} \left(
-g^{(0)lm}\frac{\partial^2 h_{ik}}{\partial x^l\partial x^m} + \frac{\partial^2 h_i^l}{\partial x^l\partial x^k} + \frac{\partial^2 h_k^l}{\partial x^i\partial x^l} - \frac{\partial^2 h}{\partial x^i\partial x^k}
\right)
\end{align*}
$$

ここで、カッコ内の最後の3項は以下のようにキャンセルされる。実際には、そうなるように先ほどのゲージ固定を行ったのである。
式 (107.5) より
$$\frac{\partial \phi^k_i}{\partial x^k}=0 \quad \left( \phi^k_i = h^k_i - \frac{1}{2}\delta^k_i h \right)$$
だから、$$h^k_i = \phi^k_i + \frac{1}{2}\delta^k_i h$$ となり、

$$
\begin{align*}
&\frac{\partial^2 h_i^l}{\partial x^l\partial x^k} + \frac{\partial^2 h_k^l}{\partial x^i\partial x^l} - \frac{\partial^2 h}{\partial x^i\partial x^k} \\
&= \frac{\partial^2 \left( \phi^i_l + \frac{1}{2}\delta^l_i h \right)}{\partial x^l\partial x^k} + \frac{\partial^2 \left( \phi^k_l + \frac{1}{2}\delta^l_k h \right)}{\partial x^i\partial x^l} - \frac{\partial^2 h}{\partial x^i\partial x^k} \\
&= \frac{1}{2}\delta^l_i \frac{\partial^2 h}{\partial x^l\partial x^k} + \frac{1}{2}\delta^l_k \frac{\partial^2 h}{\partial x^i\partial x^l} - \frac{\partial^2 h}{\partial x^i\partial x^k} \\
&= \frac{1}{2}\frac{\partial^2 h}{\partial x^i\partial x^k} + \frac{1}{2}\frac{\partial^2 h}{\partial x^i\partial x^k} - \frac{\partial^2 h}{\partial x^i\partial x^k} \\
&= 0
\end{align*}
$$

式 (107.5) の条件 $$\frac{\partial \phi^k_i}{\partial x^k}=0$$
は、デ・ドンデールゲージ（De Donder gauge）と呼ばれる。別名 harmonic
coordinate gauge である。
余分な自由度を固定して式の見通しをよくする手法は、ここにあったのだ！
Maxwell方程式に対するゲージ固定条件の一つであるローレンツゲージ
$$\partial_{\mu} A^{\mu} = 0$$ からの着想らしい。

結局、次のように単純化される：
$$
\begin{equation*}
R_{ik} = \frac{1}{2} \left( -g^{(0)lm} \frac{\partial^2 h_{ik}}{\partial x^l\partial x^m} \right) = \frac{1}{2}\Box h_{ik} \quad \left( \Box = \Delta - \frac{1}{c^2}\frac{\partial^2}{\partial t^2} \right)
\end{equation*}
$$

アインシュタイン方程式そのもの：
$$
\begin{equation*}
R_{ik} - \frac{1}{2}g_{ik}R = \frac{8\pi k}{c^4}T_{ik}
\end{equation*}
$$
について、伝播する空間は物質やエネルギーが存在しない真空と仮定し、$$T_{ik} \rightarrow 0$$
とおく。

一方、$$R_{ik}$$ については、 アインシュタイン方程式で
$$T_{ik} \rightarrow 0$$ とおくと、
$$
\begin{equation*}
R_{ik} - \frac{1}{2}g_{ik}R = 0
\end{equation*}
$$
となる。ここで両辺に対し、$$g^{ik}$$で縮約を取ると、
$$
\begin{equation*}
g^{ik}\left(R_{ik} - \frac{1}{2}g_{ik}R \right) = R - \frac{1}{2}(4)R = -R = 0
\end{equation*}
$$
となる。$$R$$は物質やエネルギーの存在しない空間では厳密に$$R=0$$である。
ゆえに、$$\frac{1}{2}\Box h_{ik} = 0$$、すなわち、
$$
\begin{equation}
\Box h_{ik} = 0 \tag{107.8}
\end{equation}
$$

ようやく、四次元時空を伝わる波動方程式があらわれ、$$h_{ik}$$ が光速
$$c$$ で伝わる「重力波」であるということができる!!!

参考：ランダウ・リフシッツ『場の古典論』
