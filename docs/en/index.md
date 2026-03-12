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
Notes on the Derivation of Gravitational Waves

Can we derive gravitational waves starting from the Einstein equations?
Although it involves many assumptions, we were able to derive them.

First, consider the metric $$g_{ik}$$.   
Assuming a very small perturbation from flat spacetime (weak gravitational field), we write:

$$
\begin{equation}
g_{ik} = g_{ik}^{(0)} + h_{ik} \quad (h_{ik} \ll 1) \tag{107.1}
\end{equation}
$$

For the contravariant tensor $$g^{ik}$$,
since it must satisfy $$g_{il}g^{lk} = (g_{il}^{(0)} + h_{il})g^{lk} = \delta_i^k$$,
we consider the appropriate form of $$g^{ik}$$.

If $$g^{ik} = g^{(0)ik} - h^{ik} + h^i_l h^{lk}$$, 

then:
$$
\begin{align*}
g_{il}g^{lk} &= (g_{il}^{(0)} + h_{il})(g^{(0)ik} - h^{ik} + h^i_l h^{lk}) \\
\delta_i^k &= g^{(0)}_{il}g^{(0)lk} - g_{il}^{(0)}h^{lk} + g_{il}^{(0)}h^l_m h^{mk} + h_{il}g^{(0)lk} - h_{il}h^{lk} + h_{il}h^l_m h^{mk}
\end{align*}
$$

This holds to $$O(h^3)$$.  

Again, let $$g^{ik} = g^{(0)ik} - h^{ik} + h^i_l h^{lk}$$.

The determinant is also approximated as $$g = g^{(0)}(1+h) \quad (h \equiv h^i_i)$$.

Next, consider an infinitesimal coordinate transformation $$x'^i = x^i + \xi^i$$.   
We assume $$\xi^i \ll 1$$.

From the definition of tensors,

$$
\begin{align*}
g'^{ik}(x'^l) &= g^{nm}(x^l) \frac{\partial x'^i}{\partial x^n} \frac{\partial x'^k}{\partial x^m} \\
&= g^{nm} \left( \delta^i_n + \frac{\partial \xi^i}{\partial x^n} \right) \left( \delta^k_m + \frac{\partial \xi^k}{\partial x^m} \right) \\
&\simeq g^{nm}(x^l) \left( \delta^i_n\delta^k_m + \delta^i_n\frac{\partial \xi^k}{\partial x^m} + \delta^k_m\frac{\partial \xi^i}{\partial x^n} \right) \\
&= g^{ik}(x^l) + g^{im} \frac{\partial \xi^k}{\partial x^m} + g^{kn} \frac{\partial \xi^i}{\partial x^n}
\end{align*}
$$

Expanding $$g'^{ik}(x'^l)$$ (i.e., $$g'^{ik}(x^l + \xi^l)$$) in powers of $$\xi$$,

$$
\begin{align*}
g'^{ik}(x^l + \xi^l) &= \sum \frac{\xi^n}{n!} \frac{\partial g^{(n)'ik}(x^l)}{\partial x^n} \\
&\rightarrow g'^{ik}(x^l) + \xi^l \frac{\partial g'^{ik}(x^l)}{\partial x^l} \\
&\rightarrow g'^{ik}(x^l) + \xi^l \frac{\partial g^{ik}(x^l)}{\partial x^l}
\end{align*}
$$

Therefore,

$$
\begin{align*}
g'^{ik}(x^l) + \xi^l \frac{\partial g^{ik}(x^l)}{\partial x^l} &= g^{ik}(x^l) + g^{im} \frac{\partial \xi^k}{\partial x^m} + g^{kn} \frac{\partial \xi^i}{\partial x^n} \\
g'^{ik}(x^l) &= g^{ik}(x^l) - \xi^l \frac{\partial g^{ik}(x^l)}{\partial x^l} + g^{im} \frac{\partial \xi^k}{\partial x^m} + g^{kn} \frac{\partial \xi^i}{\partial x^n} \\
g'^{ik}(x^l) &= g^{ik}(x^l) + \delta g^{ik} \quad (\delta g^{ik} = \xi^{i,k} + \xi^{k;i} \quad \text{※ sum of contravariant derivatives}) \\
g'^{(0)ik}(x^l) - h'^{ik} &= g^{(0)ik}(x^l) - h^{ik} + \delta g^{ik} \\
h'^{ik} &= h^{ik} - \delta g^{ik} \\
h'^{ik} &= h^{ik} - \frac{\partial \xi^k}{\partial x_i} - \frac{\partial \xi^i}{\partial x_k}
\end{align*}
$$

Similarly, for the covariant components,

$$
\begin{align*}
g'_{ik}(x^l) &= g_{ik}(x^l) + \delta g_{ik} \quad (\delta g_{ik} = -\xi_{i,k} - \xi_{k;i}) \\
g'_{(0)ik}(x^l) + h'_{ik} &= g_{(0)ik}(x^l) + h_{ik} + \delta g_{ik} \\
h'_{ik} &= h_{ik} - \frac{\partial \xi_k}{\partial x^i} - \frac{\partial \xi_i}{\partial x^k} \tag{107.4}
\end{align*}
$$

An auxiliary condition is imposed on $$h_{ik}$$ (the so-called gauge fixing).

$$
\begin{equation}
\frac{\partial \phi^k_i}{\partial x^k}=0 \quad \left( \phi^k_i = h^k_i - \frac{1}{2}\delta^k_i h \right) \tag{107.5}
\end{equation}
$$

From the Ricci tensor,

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

We consider the form of the covariant curvature tensor.

$$
\begin{equation}
R_{iklm} = \frac{1}{2} \left(
\frac{\partial^2 g_{im}}{\partial x^k\partial x^l} + \frac{\partial^2 g_{kl}}{\partial x^i\partial x^m} - \frac{\partial^2 g_{il}}{\partial x^k\partial x^m} - \frac{\partial^2 g_{km}}{\partial x^i\partial x^l}
\right) + g_{np}(\Gamma^n_{kl}\Gamma^p_{im} - \Gamma^n_{km}\Gamma^p_{il}) \tag{92.1}
\end{equation}
$$

Under the weak gravitational field condition $$$h_{ik} \ll 1$$,it is reasonable to treat $$\Gamma^i_{kl} \ll 1$$.
Therefore,

$$
\begin{equation*}
(\Gamma^m_{kl}\Gamma^p_{im} - \Gamma^m_{km}\Gamma^p_{il}) \rightarrow 0
\end{equation*}
$$

So the appropriate form of $$R_{iklm}$$ is as follows.

$$
\begin{equation*}
R_{iklm} = \frac{1}{2} \left(
\frac{\partial^2 g_{im}}{\partial x^k\partial x^l} + \frac{\partial^2 g_{kl}}{\partial x^i\partial x^m} - \frac{\partial^2 g_{il}}{\partial x^k\partial x^m} - \frac{\partial^2 g_{km}}{\partial x^i\partial x^l}
\right)
\end{equation*}
$$

For $$R_{ik}$$, it can be approximated as follows.

$$
\begin{equation*}
R_{ik} = g^{lm}R_{limk} \simeq g^{(0)lm}R_{limk}
\end{equation*}
$$

Therefore,

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

$$g_{ik} = g^{(0)}_{ik} + h_{ik}$$, so

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

Here, the last three terms in the bracket cancel out. In fact, the gauge fixing above was performed precisely to achieve this.
From equation (107.5),
$$\frac{\partial \phi^k_i}{\partial x^k}=0 \quad \left( \phi^k_i = h^k_i - \frac{1}{2}\delta^k_i h \right)$$,
so $$h^k_i = \phi^k_i + \frac{1}{2}\delta^k_i h$$, and

$$
\begin{align*}
&\frac{\partial^2 h_i^l}{\partial x^l\partial x^k} + \frac{\partial^2 h_k^l}{\partial x^i\partial x^l} - \frac{\partial^2 h}{\partial x^i\partial x^k} \\
&= \frac{\partial^2 \left( \phi^i_l + \frac{1}{2}\delta^l_i h \right)}{\partial x^l\partial x^k} + \frac{\partial^2 \left( \phi^k_l + \frac{1}{2}\delta^l_k h \right)}{\partial x^i\partial x^l} - \frac{\partial^2 h}{\partial x^i\partial x^k} \\
&= \frac{1}{2}\delta^l_i \frac{\partial^2 h}{\partial x^l\partial x^k} + \frac{1}{2}\delta^l_k \frac{\partial^2 h}{\partial x^i\partial x^l} - \frac{\partial^2 h}{\partial x^i\partial x^k} \\
&= \frac{1}{2}\frac{\partial^2 h}{\partial x^i\partial x^k} + \frac{1}{2}\frac{\partial^2 h}{\partial x^i\partial x^k} - \frac{\partial^2 h}{\partial x^i\partial x^k} \\
&= 0
\end{align*}
$$

The condition $$\frac{\partial \phi^k_i}{\partial x^k}=0$$ in equation (107.5) is called the De Donder gauge, also known as the harmonic coordinate gauge.
This is where the technique of fixing the excess degrees of freedom to simplify the equations comes in!
It was apparently inspired by the Lorenz gauge condition $$\partial_{\mu} A^{\mu} = 0$$ used in Maxwell's equations.

Ultimately, it simplifies to:

$$
\begin{equation*}
R_{ik} = \frac{1}{2} \left( -g^{(0)lm} \frac{\partial^2 h_{ik}}{\partial x^l\partial x^m} \right) = \frac{1}{2}\Box h_{ik} \quad \left( \Box = \Delta - \frac{1}{c^2}\frac{\partial^2}{\partial t^2} \right)
\end{equation*}
$$

The Einstein equations themselves:

$$
\begin{equation*}
R_{ik} - \frac{1}{2}g_{ik}R = \frac{8\pi k}{c^4}T_{ik}
\end{equation*}
$$

Assuming the propagating space is a vacuum with no matter or energy, we set $$T_{ik} \rightarrow 0$$.


$$
\begin{equation*}
R_{ik} - \frac{1}{2}g_{ik}R = 0
\end{equation*}
$$

Contracting both sides with $$g^{ik}$$,

$$
\begin{equation*}
g^{ik}\left(R_{ik} - \frac{1}{2}g_{ik}R \right) = R - \frac{1}{2}(4)R = -R = 0
\end{equation*}
$$

Thus $$R$$ is strictly $$R=0$$ in space where no matter or energy exists. Therefore $\frac{1}{2}\Box h_{ik} = 0$, 
i.e.,

$$
\begin{equation}
\Box h_{ik} = 0 \tag{107.8}
\end{equation}
$$

Finally, we find the wave equation of $$h_{ik}$$ propagating four-dimensional spacetime  at  the speed of light , as a "gravitational wave" !!!

Reference: Landau & Lifshitz, "The Classical Theory of Fields"
