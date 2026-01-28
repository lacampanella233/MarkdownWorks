# 导数, Christoffel记号, 曲率张量

## (无挠)导数算符

我们来考虑一个微分流形$ M $上的求导运算. 求导的对象当然是各种张量场, 就像三维空间的矢量分析中有梯度、散度、旋度一样. 回忆: 我们通过方向导数来定义矢量, 那么在这里, 导数算符当然要根据矢量来定义.

记$ \mathcal{T}_M(k,l) $为流形$ M $上的所有$ (k,l) $型光滑张量场构成的集合, 简记为$ \mathcal{T}(k,l) $.

---

**(无挠)导数算符**. 称流形$ M $上的算符$ \nabla:\mathcal{T}(k,l)\to\mathcal{T}(k,l+1) $ ($ \forall k,l\le 0 $), 当它满足以下条件:

1. *“确保它是导数”* : 对于矢量场$ v $以及$ f\in\mathcal{T}(0,0) $ (即光滑标量场), 有$ v(f)=v^\mu(\nabla f)_\mu $ (别忘了我们是怎么定义矢量场$ v $的! ). 以下记$ (\nabla T)_\mu=\nabla_\mu T $, 虽然$ \nabla $并不是一个对偶矢量, $ \nabla_\mu $更不是什么东西的分量. 
2. *线性性* : 对于同类型的张量$ T,T_1,T_2 $与$ \lambda\in\mathbb{R} $, 有$ \nabla(T_1+T_2)=\nabla T_1+\nabla T_2 $, $ \nabla(\lambda T)=\lambda\nabla T $.
3. *莱布尼兹律* : 对于(可以是不同类型的)张量$ S,T $, 有$ \nabla(ST)=S\nabla T+T \nabla S $. 如果这个式子的乘积是缩并(即这里省略掉的角标中有重复的), 式子依然成立.
4. *无挠* : $ \nabla_\mu\nabla_\nu T=\nabla_\nu\nabla_\mu T $. 

---

当然, 一个流形上可以有很多个导数算符. 例如, 可以验证, 对于任意光滑标量场$ f $, 考虑$ \partial_\mu f $ (这里的$ \partial_\mu $, 和往常一样, 是某个坐标系下的偏导数), 这个定义满足上述四条性质, 因此它定义了一个导数算符.



## 联络

我们可以来考察一下两个导数算符之间的区别. 设$ \nabla $和$ \nabla' $是流形$ M $上的两个导数算符, 那么对于任意光滑标量场$ f $, 有

\[\nabla_\mu f=\nabla'_\mu f.\]

但是, 对于矢量场$ v_\mu $, 两个导数算符的作用一般不同. 我们来考虑算符$ \nabla_\mu-\nabla'_\mu $. 按照定义, 这是一个线性的算符, 可以把一个$ (0,1) $型的矢量映射为一个$ (0,2) $型的张量. 

我们来证明: 对于一点$ p $, 若$ v_\mu $在$ p $点为零, 则$ (\nabla_\mu -\nabla'_\mu) v_\nu $在$ p $点为零. 注意: 这是一个很不平凡的结论, 因为若一个函数在某点为零, 它的导数不一定为零. 也就是说, 虽然$ v_\nu $在点$ p $处的值为$ 0 $, 但是$ v_\nu $在点$ p $处的变化率(即导数)一般不为零. 但是现在我们要证明, 对于导数算符的差, 它的作用结果在点$ p $处却为零.

对于一个矢量场$ v $, 它的一个分量$ v_\mu $可以视作$ M $上的标量场, 而我们知道对于标量场$ f $有$ (\nabla_\mu-\nabla'_\mu)f=0 $. 故我们可以作如下展开(注意: 我们把$ \partial_\mu $写在某些东西的后面时, 它代表的是切空间$ T_pM $的基矢; 反之, 写在前面时, 它代表的是坐标系下的偏导数):

\[ \begin{align*}
(\nabla-\nabla') v|_p=&(\nabla_\mu-\nabla'_\mu) (v_\nu\mathrm{d}x^\nu)|_p \partial_\mu=(\nabla_\mu-\nabla'_\mu)(v_\nu)|_p\mathrm{d}x^\nu \partial_\mu +v_\nu|_p(\nabla_\mu-\nabla'_\mu)(\mathrm{d}x^\nu)|_p \partial_\mu \\
=&v_\nu|_p(\nabla_\mu-\nabla'_\mu)(\mathrm{d}x^\nu) \partial_\mu=0.
\end{align*} \]

这里我们用到了莱布尼兹律, 以及$ v_\nu|_p=0 $. 由此可见, 算符$ \nabla_\mu-\nabla'_\mu $的结果只和矢量场$ v $在点$ p $处的值有关, 而和它在点$ p $处的变化率无关. 这就说明了, 对于任意矢量场$ v $, 存在一个张量$ C^\lambda_{\mu\nu} $使得

\[ \nabla'_\mu v_\nu=\nabla_\mu v_\nu-C^\lambda_{\mu\nu}v_\lambda. \]

再利用无挠的条件, 我们可以证明$ C^\lambda_{\mu\nu}=C^\lambda_{\nu\mu} $:

\[ \begin{align*}
0=&(\nabla'_\mu\nabla'_\nu-\nabla'_\nu\nabla'_\mu)f=\nabla'_\mu(\nabla'_\nu f)-\nabla'_\nu(\nabla'_\mu f)\\
=&\nabla_\mu(\nabla_\nu f)-C^\lambda_{\mu\nu}(\nabla_\lambda f)-\nabla_\nu(\nabla_\mu f)+C^\lambda_{\nu\mu}(\nabla_\lambda f)\\
=&(C^\lambda_{\nu\mu}-C^\lambda_{\mu\nu})(\nabla_\lambda f).
\end{align*} \]

由于这个式子对于任意的标量场$ f $成立, 故必然有$ C^\lambda_{\mu\nu}=C^\lambda_{\nu\mu} $. 


上面讨论的是两个导数算符作用在一个*对偶矢量场*上的差别. 那对于*矢量场* 呢? 我们可以注意到, 对于$ v^\mu $与$ \omega_\mu $, 它们的缩并$ v^\mu\omega_\mu $是一个张量场, 因此可以用莱布尼兹律来研究: 

\[ \begin{align*}
0&=(\nabla_\nu-\nabla'_\nu)(v^\mu\omega_\mu)=v^\mu(\nabla_\nu-\nabla'_\nu)(\omega_\mu)+\omega_\mu(\nabla_\nu-\nabla'_\nu)(v^\mu)\\
&=v^\mu(-C^\lambda_{\nu\mu}\omega_\lambda)+\omega_\mu(\nabla_\nu-\nabla'_\nu)(v^\mu).
\end{align*} \]

即, 对于任意的对偶矢量场$ \omega_\mu $, 我们有$ \omega_\mu(\nabla_\nu-\nabla'_\nu)(v^\mu)=\omega_\mu C^\mu_{\nu\lambda}v^\lambda $. 由于这个式子对任意的$ \omega_\mu $都成立, 故我们有

\[ \nabla'_\nu v^\mu=\nabla_\nu v^\mu+C^\mu_{\nu\lambda}v^\lambda. \]

我们再来考虑一下$ (2,0) $型的张量场$ T^{\mu\nu} $. 就像前面一样, 我们可以取一个任意的对偶矢量场$ \omega_\nu $进行缩并, 这样, 由于我们已经知道了矢量场$ T^{\mu\nu}\omega_\nu $在两个导数算符下的差别, 就可以用莱布尼兹律来研究$ T^{\mu\nu} $在两个导数算符下的差别:

\[ \begin{align*}
(\nabla_\lambda-\nabla'_\lambda)(T^{\mu\nu}\omega_\nu)&=T^{\mu\nu}(\nabla_\lambda-\nabla'_\lambda)(\omega_\nu)+\omega_\nu(\nabla_\lambda-\nabla'_\lambda)(T^{\mu\nu})\\
&=T^{\mu\nu}(-C^\sigma_{\lambda\nu}\omega_\sigma)+\omega_\nu(\nabla_\lambda-\nabla'_\lambda)(T^{\mu\nu}).
\end{align*} \]

而另一方面, 根据前面的结论, 我们也有

\[ (\nabla_\lambda-\nabla'_\lambda)(T^{\mu\nu}\omega_\nu)=C^\mu_{\lambda\sigma}(T^{\sigma\nu}\omega_{\nu}). \]

再由于对偶矢量场$ \omega_\nu $是任意的, 故我们有

\[ \nabla'_\lambda T^{\mu\nu}=\nabla_\lambda T^{\mu\nu}+C^\mu_{\lambda\sigma}T^{\sigma\nu}+C^\nu_{\lambda\sigma}T^{\mu\sigma}. \]

通过数学归纳法, 我们可以证明: 对于任意类型的张量场$ T^{\mu_1\mu_2\cdots\mu_k}_{\nu_1\nu_2\cdots\nu_l} $, 都有

\[ \nabla'_\lambda T^{\mu_1\mu_2\cdots\mu_k}_{\nu_1\nu_2\cdots\nu_l}=\nabla_\lambda T^{\mu_1\mu_2\cdots\mu_k}_{\nu_1\nu_2\cdots\nu_l}+\sum_{i=1}^k C^{\mu_i}_{\lambda\sigma}T^{\mu_1\cdots\sigma\cdots\mu_k}_{\nu_1\nu_2\cdots\nu_l}-\sum_{j=1}^l C^{\sigma}_{\lambda\nu_j}T^{\mu_1\mu_2\cdots\mu_k}_{\nu_1\nu_2\cdots\sigma\cdots\nu_l}. \]

看起来很吓人, 但实际上, 这个式子的意思就是: 每个上标都要加一项$ +C $项, 让$ C $与$ T $按照某种方式缩并; 每个下标都要加一项$ -C $项, 让$ C $与$ T $按照某种方式缩并.



## Christoffel记号

现在, 我们给流形$ M $附加一个度规的结构$ g $. 我们希望找到这样的一个性质良好的导数算符$ \nabla $, 使得度规张量被它作用后为$ 0 $, 即:

\[ \nabla_\lambda g_{\mu\nu}=0. \] 

这样的定义在后面有诸多好处. 后面会证明这样的导数算符一定存在. 

由前面的讨论, 知道存在一个(依赖于坐标系的)张量$ \Gamma^{\lambda}_{\mu\nu} $, 称为**Christoffel记号**, 使得

\[ \nabla_\mu v_\nu=\partial_{\mu}v_\nu-\Gamma^{\lambda}_{\mu\nu}v_\lambda,\quad \nabla_\mu v^\nu=\partial_\mu v^\nu+\Gamma^\nu_{\lambda\mu}v^\lambda. \] 

下面我们采用这样的记号: $ \partial_\nu v_\mu=:v_{\mu,\nu}, \nabla_{\nu}v_\mu=v_{\mu;\nu} $. 

通过计算$ \nabla_\lambda g_{\mu\nu}=0 $, 可以得到Christoffel记号的具体形式: 

\[ \Gamma^\lambda_{\mu\nu}=\frac{1}{2}g^{\lambda\sigma}(g_{\mu\sigma,\nu}+g_{\nu\sigma,\mu}-g_{\mu\nu,\sigma}). \] 

可以用上面的$ \Gamma^\lambda_{\mu\nu} $的具体形式, 来验证: 张量$ \nabla_\nu v_\mu $是一个*与坐标系无关* 的张量. 因此, 这样定义的导数算符$ \nabla $也被称为**协变导数**.



## 矢量的平移

我们称一个曲线$ C $(参数方程为$ x^\mu(t) $)上的矢量场$ v^\mu(t) $沿着曲线$ C $**平行移动**, 当这个矢量场$ v^\mu(t) $满足

\[ T^\mu\nabla_\mu v^\nu=0, \] 

其中$ T^\mu $为曲线的切矢的分量. 

可以通过在欧氏平面$ \mathbb{R}^2 $上选取极坐标来考察这个方程的含义. 在这样的情况下, 这个方程表示: 矢量$ v=v^\mu\partial_\mu $(此时这个矢量就是欧氏平面中的普通的二维矢量)本身的方向不变, 尽管它的各个分量$ v^\mu $会因为它所处的位置而变化.

那么, 在一般的流形上, 这样的平移更像是下面这种感觉: 在空间中有正在自转(因而有角动量)的物体, 我们给它施加外力让它沿着某条曲线运动, 但是不给它施加任何力矩, 那么它的角动量矢量在它运动过程中保持不变(即没有受到外力矩的作用). 这就是平行移动的意义.

我们来考虑一个粒子, 它(在四维时空中)的轨迹构成了曲线$ C $, 参数方程为$ x^\mu(\tau) $(这里$ \tau $是粒子的固有时间). 粒子在时空中的四维速度为$ u^\mu=\mathrm{d}x^\mu/\mathrm{d}\tau $. 粒子的四维速度$ u^\mu $也是曲线$ C $的切矢. 如果它无动力地在四维时空中滑行, 那么它的四维速度$ u^\mu $沿着曲线$ C $平行移动, 即满足

\[ u^\mu\nabla_\mu u^\nu=u^\mu(u^\nu_{,\mu}+\Gamma^\nu_{\lambda\mu}u^\lambda)=0. \]

带入$ u^\mu=\mathrm{d}x^\mu/\mathrm{d}\tau $, 就有:

\[ \frac{\mathrm{d}x^\mu}{\mathrm{d}\tau}\frac{\partial}{\partial x^\mu}\left( \frac{\mathrm{d}x^\nu}{\mathrm{d}\tau}\right) + \Gamma^\nu_{\lambda\mu} \frac{\mathrm{d}x^\lambda}{\mathrm{d}\tau}\frac{\mathrm{d}x^\mu}{\mathrm{d}\tau} = 0. \]

整理一下指标并利用链式法则, 我们就得到了粒子在弯曲时空中的运动方程, 也称为**测地线方程**:

\[ \frac{\mathrm{d}^2 x^\lambda}{\mathrm{d}\tau^2} + \Gamma^\lambda_{\mu\nu} \frac{\mathrm{d}x^\mu}{\mathrm{d}\tau}\frac{\mathrm{d}x^\nu}{\mathrm{d}\tau} = 0. \]