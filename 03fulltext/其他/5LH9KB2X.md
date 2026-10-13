---
title: "Normalizing Flow-Based Differentiable Particle Filters"
zotero_key: "5LH9KB2X"
pdf_key: "1C8YZBM5"
collection: "其他"
source: "Open-access PDF (arXiv, pypdf extraction)"
page_mapping: unverified
---

# Normalizing Flow-Based Differentiable Particle Filters — Fulltext

> 由开放获取 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射）。

---

IEEE TRANSACTIONS ON SIGNAL PROCESSING 1
Normalizing Flow-based Differentiable Particle
Filters
Xiongjie Chen and Yunpeng Li
Abstract—Recently, there has been a surge of interest in incor-
porating neural networks into particle filters, e.g. differentiable
particle filters, to perform joint sequential state estimation and
model learning for non-linear non-Gaussian state-space models
in complex environments. Existing differentiable particle filters
are mostly constructed with vanilla neural networks that do not
allow density estimation. As a result, they are either restricted
to a bootstrap particle filtering framework or employ predefined
distribution families (e.g. Gaussian distributions), limiting their
performance in more complex real-world scenarios. In this paper
we present a differentiable particle filtering framework that uses
(conditional) normalizing flows to build its dynamic model, pro-
posal distribution, and measurement model. This not only enables
valid probability densities but also allows the proposed method
to adaptively learn these modules in a flexible way, without
being restricted to predefined distribution families. We derive
the theoretical properties of the proposed filters and evaluate the
proposed normalizing flow-based differentiable particle filters’
performance through a series of numerical experiments.
Index Terms —Sequential Monte Carlo, Differentiable Parti-
cle Filters, Normalizing Flows, Parameter Estimation, Machine
Learning.
I. I NTRODUCTION
Particle filters, also known as sequential Monte Carlo
(SMC) methods, are a class of importance sampling-based
methods developed for performing sequential state estimation
tasks in state-space models [1]–[3]. Because particle filters do
not assume the linearity or Gaussianity on the considered state-
space model and produce consistent estimators [4]–[8], they
are particularly suitable for solving non-linear non-Gaussian
filtering problems and have been widely adopted in various
domains [9]–[12].
In cases where the state-space model of interest is known,
particle filters can provide reliable approximations to posterior
distributions of latent states. Since the celebrated bootstrap
particle filter (BPF) was proposed [2], a series of particle
filtering algorithms have been developed. For instance, the
auxiliary particle filter (APF) improves its sampling efficiency
by employing an auxiliary variable, such that the particles
that are more compatible with the next observation have
higher chances of survival [13]–[15]. The variance of the
Monte Carlo estimates is reduced in the Rao-Blackwellized
particle filter (RBPF) by marginalizing out some latent states
analytically [16], [17]. We refer readers to [1], [18], [19]
for more detailed discussions of the above and several other
variants of particle filtering methods.
X. Chen and Y . Li are with the Center for Oral, Clinical & Transla-
tional Sciences, Faculty of Dentistry, Oral & Craniofacial Sciences, King’s
College London, London SE1 9RT, U.K. (email: xiongjie.chen@kcl.ac.uk;
yunpeng.li@kcl.ac.uk).
In many real-world applications, parameters in the state-
space model of interest are often unknown. Several techniques
have been proposed to estimate the parameters in the state-
space model [20], [21], among which maximum likelihood
estimation methods and Bayesian estimation methods are the
two main approaches in this direction. In maximum likelihood
methods [22]–[24], estimates of the unknown parameters are
obtained by searching for parameters that maximize the likeli-
hood of observations given the estimate. In contrast, Bayesian
estimation methods aim to estimate the posterior of parameters
given observations through a specified prior distribution on the
estimated parameters and the conditional likelihood of obser-
vations given parameters [25], [26]. In addition, depending on
whether the observations are from fixed datasets or streaming
dataflows, both Bayesian estimation and maximum likelihood
estimation methods can be further divided into off-line and
on-line methods [5], [27]–[30].
These parameter estimation methods have shown their effec-
tiveness in certain scenarios, e.g. where the structure or a part
of the parameters of the state-space model is known. Complex
real-world cases require the learning of a full, complex state-
space model from data. Recently, an emerging class of particle
filters, often named differentiable particle filters (DPFs) [31]–
[37], has received a surge of interest. Compared with classical
parameter estimation techniques developed for particle filters,
differentiable particle filters often make much less restrictive
assumptions about the considered state-space model. Such
flexibility makes them a promising tool for solving filtering
tasks with complex high-dimensional environments, where the
observations can be high-dimensional unstructured data such
as images [32]–[34].
Components of differentiable particle filters, including dy-
namic models, measurement models, and proposal distribu-
tions, are mostly constructed with neural networks and opti-
mized by minimizing a loss function via gradient descent [32],
[33], [38]–[40]. Due to the discrete nature of the standard
multinomial resampling, different resampling strategies have
been developed to estimate the gradient of neural network
parameters w.r.t. different loss functions [32], [33], [35], [37],
[41], [42]. It was investigated in [36] the impact of different
design choices of dynamic models, measurement models,
noise models, loss functions, and resampling schemes on
the performance of differentiable particle filters. A detailed
discussion of previous work that is most relevant to the
proposed work is presented in Section I-A.
One limitation of existing differentiable particle filters is
that most of them only employ vanilla neural networks to
construct their components [32]–[34]. However, as vanilla
arXiv:2403.01499v2  [cs.LG]  3 Jan 2025

IEEE TRANSACTIONS ON SIGNAL PROCESSING 2
neural networks do not allow density estimation, i.e. we do
not know the probability density of their outputs, differentiable
particle filters built with vanilla neural networks often include
multiple levels of approximations such that desired statistical
properties of standard particle filtering frameworks do not
apply to these methods. For example, the transition density
of particles is either modeled by simple distributions such as
Gaussian distributions [33], [34] or ignored [32]. As a result,
for all but a few trivial low-dimensional examples, existing
differentiable particle filters are often restricted to the bootstrap
particle filtering framework, making them susceptible to the
weight degeneracy issue [43].
To address these issues, in this paper, we present a nor-
malizing flow-based differentiable particle filtering framework.
By leveraging (conditional) normalizing flows, the proposed
method provides a flexible mechanism to model complex dy-
namics of latent states and design valid and effective proposal
distributions. In addition, we use conditional normalizing flows
to construct measurement models that admit valid probability
densities. The contributions of this paper are as follows:
• We propose a normalizing flow-based differentiable parti-
cle filter (NF-DPF), which provides a flexible mechanism
for modeling complex state-space models and admits
valid probability densities for each component of the
proposed method;
• We establish convergence results for the proposed
method, proving that the approximation error of the
resulting Monte Carlo estimates vanishes when the num-
ber of particles approaches infinity; To the best of our
knowledge, this is the first work that established such
convergence properties for both predictive and posterior
approximations in differentiable particle filters.
• We report that the proposed method leads to improved
performance over state-of-the-art differentiable particle
filters on a variety of benchmark datasets in this field.
Compared with existing differentiable particle filtering meth-
ods, the proposed method offers three main advantages. Firstly,
since normalizing flows are universal approximators [44], the
proposed NF-DPF can theoretically approximate any dynamic
models, proposal distributions, and measurement models arbi-
trarily well. Secondly, the proposed NF-DPF is not restricted
to the bootstrap particle filtering framework and thus can
alleviate the weight degeneracy issue. Lastly, in contrast to
differentiable particle filters built with vanilla neural networks,
all the components of the NF-DPF yield valid probability
density. This enables maximum likelihood training of the NF-
DPF, making it suitable for scenarios where ground-truth latent
states are not accessible.
Some of our initial explorations on building differentiable
particle filters with normalizing flows were reported in abbre-
viated forms in conference papers [45], [46]. In this paper,
more details of the proposed method are presented and dis-
cussed. Additionally, in this work, we establish convergence
results for the proposed method and validate the effectiveness
of the proposed method on a more extensive set of numerical
experiments.
The rest of this paper is organized as follows. A detailed
review of previous work relevant to our work is presented
in Section I-A. The problem statement is presented in Sec-
tion II. In Section III, we provide the necessary background
knowledge for introducing the proposed method. The proposed
normalizing flow-based differentiable particle filter is detailed
in Section IV. Convergence results of the proposed method
are established in Section V. The performance of the proposed
method is evaluated and compared with the other differentiable
particle filters in Section VI. We conclude this paper in
Section VII.
A. Related Work
Parameter estimation for particle filters has long been an ac-
tive research area, and various techniques have been proposed
to address this task in several different directions [20], [21].
One type of such parameter estimation methods is the max-
imum likelihood (ML) methods [22]–[25], [47]–[51]. In [24]
and [22], importance sampling and common random numbers
methods are respectively used to create a continuous version of
the resampling step and learn parameters of particle filters by
maximizing the marginal observation likelihood with gradient
descent. To obtain a low-variance estimate of the gradient of
log-likelihood, different variance reduction techniques have
been proposed [23], [47]. An alternative approach that can
maximize the log-likelihood in a numerically more stable
way is the expectation-maximization (EM) algorithm [25],
[48], [49]. Another main category of techniques developed
for estimating parameters of state-space model is the Bayesian
parameter estimation methods, where the parameters to be es-
timated are assigned with a prior distribution and the estimate
is characterized by the posterior distribution of the parameters
given the observations [5], [27]–[30], [52]–[55]. One typical
example of Bayesian parameter estimation methods is the
particle Markov chain Monte Carlo (PMCMC) method and
its variants [27], [30], [55], which use Markov chain Monte
Carlo (MCMC) samplers to generate Monte Carlo estimates
of the parameter posterior.
One common assumption in the aforementioned methods
is that the structures or part of parameters of the dynamic
and measurement models are known, which often cannot be
satisfied in real-world applications. To alleviate this limitation,
several methods resort to combining particle filtering methods
with machine learning tools such as neural networks and
gradient descent. We refer to these methods as differentiable
particle filters [31]–[36], [56], [57].
For dynamic models in differentiable particle filters, it was
proposed in [32], [33] to parametrize dynamic models using
fully-connected neural networks with previous states and given
actions as inputs. In [34], [35], [57], recurrent neural networks
such as long short-term memory (LSTM) networks and gated
recurrent unit (GRU) networks were applied in differentiable
particle filters to model the transition of latent states. Dynamic
models with known functional forms are considered in [36],
while the covariance matrices for dynamic noise variables need
to be learned. To the best of our knowledge, existing dynamic
models of differentiable particle filters are limited to pre-
specified distribution families, such as Gaussian distributions.
This limitation highlights the need for a more general and

IEEE TRANSACTIONS ON SIGNAL PROCESSING 3
flexible framework to enable differentiable particle filters to
construct complex latent dynamics.
For measurement models in existing differentiable particle
filters, they are either only able to produce unnormalized prob-
ability densities or limited to pre-defined simple distribution
families like Gaussian distributions. For example, in robot
localization tasks reported in [32], [33], [57], the unnormalized
conditional likelihood of observations given states is estimated
by vanilla neural networks with observations and particles
as inputs. The conditional likelihood function in [34]–[36]
is defined as probability density functions (PDFs) of known
distributions with parameters determined by state features.
In several trivially simple cases, hand-crafted proposal dis-
tributions have shown to be effective [38], [39]. However,
most existing differentiable particle filters are built with vanilla
neural networks, while in general, it is not feasible to compute
the density of vanilla neural networks’ output. There is a
lack of more general mechanisms for constructing proposal
distributions in these differentiable particle filters.
A key ingredient to achieving fully differentiable particle
filters is a differentiable resampling scheme [56]. Several ap-
proaches have been developed towards this direction [33]–[35],
[37], [56]. One class of differentiable resampling schemes
designs the particle weights after resampling as a differentiable
function of particle weights before resampling such that the
gradients backpropagated through resampling steps are non-
zero [33], [56]. A truly differentiable resampling scheme was
proposed in [34], where the deterministic and differentiable re-
sampling output is obtained by solving an entropy-regularized
optimal transport problem with the Sinkhorn algorithm [58]–
[60]. It was shown that the resampling scheme proposed
in [34] leads to biased but asymptotically consistent estimates
of the log-likelihood. A particle transformer was introduced
in [37] based on a set transformer architecture [61], [62],
which needs to be trained from collected data beforehand
and therefore can hardly be adapted to new tasks. Because
these resamplers do not conform to the standard multinomial
resampling framework, establishing convergence results for
differentiable particle filters is challenging. In this paper, we
adopted the entropy-regularized optimal transport resampler
and, for the first time, established convergence results for
both predictive and posterior approximations in the proposed
method.
Loss functions that are often used in training differentiable
particle filters can be grouped into two main classes. The
first class is the likelihood-based loss functions [38]–[40].
In [38]–[40], an evidence lower bound (ELBO) of obser-
vation log-likelihood was derived within a general particle
filtering framework and maximized to learn system models
and proposal distributions [34], [38]. The other type of loss
functions involves task-specific objectives, e.g. root mean
square error (RMSE) between estimates of states and ground-
truth states [32]–[34], [57], among others [12], [57], [63],
[64]. It was reported in [57] that combining task-specific
loss functions with log-likelihood objectives gives the best
empirical performance in numerical simulations.
II. P ROBLEM STATEMENT
We consider filtering problems in state-space models
(SSMs). State-space models refer to a class of sequential
models that consist of two discrete-time variables, the latent
state variable xt, t ≥ 0 defined on X ⊆RdX , and the observed
measurement variable yt, t ≥ 0 defined on Y ⊆RdY [65]. The
latent state xt, t ≥ 0 is characterized by a Markov process
with an initial distribution π(x0) and a transition kernel
p(xt|xt−1; θ) for t ≥ 1. The observation yt is conditionally
independent given the current latent state xt:
x0 ∼ π(x0; θ) , (1)
xt|xt−1 ∼ p(xt|xt−1; θ) for t ≥ 1 , (2)
yt|xt ∼ p(yt|xt; θ) for t ≥ 0 , (3)
where θ ∈ Θ is the parameter set of interest. Denoted
by x0:t := {x0, · · ·, xt} and y0:t := {y0, · · ·, yt} the
sequences of latent states and observations up to time step
t respectively. In this work, our goal is to jointly estimate
the joint posterior distribution p (x0:t|y0:t; θ) or the marginal
posterior distribution p (xt|y0:t; θ) and the parameter set θ.
III. P RELIMINARIES
A. Particle Filtering
Except for a limited class of state-space models such as lin-
ear Gaussian models [66], analytical solutions for the posterior
distribution p(x0:t|y0:t; θ) are unavailable since they involve
complex high-dimensional integrations over X t+1. Particle
filters are an alternative solution to the above problem. In
particular, particle filters approximate intractable joint posteri-
ors with empirical distributions consisting of sets of weighted
samples { ˜wit, xi0:t}i∈[N ]:
p(x0:t|y0:t; θ) ≈
NX
i=1
˜wit δxi0:t (x0:t) , (4)
where [N ] := {1, · · ·, N}, N is the number of particles,
δxi0:t (·) denotes the Dirac delta measure located in xi0:t, and
˜wit ≥ 0 with PNi=1 ˜wit = 1 is the normalized importance
weight of the i-th particle at the t-th time step. Particles
with higher importance weights are believed to be closer to
the true state than those with lower importance weights. The
particles {xi0:t}i∈[N ] are sampled from proposal distributions
q(x0|y0; ϕ) when t = 0 and q(xt|yt, xt−1; ϕ) for t ≥ 1. Denote
by wit unnormalized importance weights of particles, impor-
tance weights of particles are updated recursively through:
wit = wit−1 p(yt|xit; θ)p(xit|xit−1; θ)q(xit|yt, xit−1; ϕ) , (5)
with wi0 = p(y0|xi0;θ)π(xi0;θ)q(xi0|y0;ϕ) and normalized as ˜wit = witPNj=1 wjt .Particle resampling is triggered when a predefined condition
is satisfied [67], [68].

IEEE TRANSACTIONS ON SIGNAL PROCESSING 4
B. Differentiable particle filters
In differentiable particle filters, both the evolution of latent
state xt and the relationship between the observation yt and the
latent state xt are modeled by neural networks. Particularly,
differentiable particle filters describe the transition of the state
xt using a parametrized function gθ(·) : X ×Rdς → X:
xt = gθ(xt−1, ςt) ∼ p(xt|xt−1; θ) , (6)
where ςt ∈ Rdς is the noise sample used to simulate the
dynamic noise, and gθ(·) is differentiable w.r.t. xt and ςt. For
measurement models, one commonly adopted construction is
through a parametrized function lθ(·) : Y × X →R:
p(yt|xt; θ) ∝ lθ(yt, xt) , (7)
lθ(·) measures compatibilities between yt and xt and needs to
be differentiable w.r.t. both yt and xt. Similarly, the proposal
distribution can also be constructed through a parametrized
function fϕ(·) : X × Y ×Rdυ → X:
xt = fϕ(xt−1, yt, υt) ∼ q(xt|xt−1, yt; ϕ) , (8)
where υt ∈ Rdυ refers to the sampling noise.
While it has been widely documented that the resampling
step is non-differentiable [33], [56], several approaches have
been developed to solve this problem [33]–[35], [37], [56].
With the differentiable components discussed above, differ-
entiable particle filters are optimized by minimizing a loss
function through gradient descent.
C. Normalizing flows
Consider a D-dimensional variable z ∼ pZ(z), where pZ(·)
is a known simple distribution, e.g. Gaussian, defined on
Z ⊆ RD. We define a variable s on S ⊆ RD through
a transformation s = Tϑ(z), Tϑ(·) : Z → S, where ϑ is
the parameter of the transformation. The transformation Tϑ(·)
is called a normalizing flow if it is invertible w.r.t. z and
differentiable w.r.t. ϑ and z [44], [69]. Under some mild
assumptions, s = Tϑ(z) can represent arbitrarily complex
distributions, even if the distribution of z is as simple as a
standard Gaussian [44].
Recent developments in normalizing flows focus on con-
structing invertible transformations with neural networks [70]–
[75]. Compared with vanilla neural networks which cannot
produce valid probability densities, the density of normaliz-
ing flows’ output s = Tϑ(z) can be obtained by applying
the change of variable formula. Since the composition of a
series of invertible and differentiable transformations is still
invertible and differentiable, we can stack K simple invert-
ible transformations {Tϑk (·)}Kk=1 together and yield a more
expressive normalizing flow s = TϑK ◦ TϑK−1 ◦ · · · ◦ Tϑ1 (z).
Correspondingly, the density of s can be computed by succes-
sively applying the change of variable formula.
One simple example of normalizing flows is the planar
flow [73]. Denote by z ∈ RD the input of a planar flow,
the output of the planar flow is computed as follows:
Tϑ(z) = z + vh(w⊺z + b) , (9)
where Tϑ(·) is parametrized by ϑ := {w ∈ RD, v∈ RD, b∈
R}, and h(·) : R → R is a smooth non-linear function. It
has been proved in [73] that Eq. (9) is invertible when some
mild conditions on w, u, and h(·) are satisfied. The Jacobian
determinant of planar flow can be computed in O(D) time.
Another variant of normalizing flows, the Real-NVP
model [70], constructs invertible transformations through cou-
pling layers. In standard coupling layers the input z is split
into two parts z = [z1, z2], where z1 = z1:d refers to the firstd dimensions of z, and z2 = zd+1:D refers to the last D − d
dimensions of z. The partition is uniquely determined by an
index d < D, and the output s ∈ RD of the coupling layer is
given by:
s
1:d
= z
1:d
, (10)
s
d+1:D
= z
d+1:D
⊙ e
γϑ( z1:d) + ηϑ( z1:d) , (11)
where γϑ(·) : Rd → RD−d and ηϑ(·) : Rd → RD−d stand for
the scale function and the translation function, respectively,
⊙ refers to element-wise products, and the exponential of the
vector γϑ( z1:d) is also applied element-wise. With the specialstructure defined by Eq. (10), coupling layers are invertible by
design, and Jacobian matrices of coupling layers are lower or
upper triangular matrices, such that the Jacobian determinants
can be efficiently computed. In addition to coupling layers,
more tricks to build expressive invertible transformations such
as multi-scale structure, masked convolution, and batch nor-
malization can be found in [70].
To model the conditional probability density of s condi-
tioned on u ∈ Rdu, i.e. p(s|u; φ), one can use another type of
normalizing flows, called conditional normalizing flow [76],
[77]. Both planar flows and Real-NVP models have their
conditional counterparts. Given a condition u ∈ Rdu, a planar
flow can be made conditional with the following modification:
Fφ(z; u) = z + vh(w⊺z + b ⊙ s(u)) , (12)
where s(·) : Rdu → RD can be any linear or non-linear
functions and does not impair the invertibility of the flow. Con-
ditional Real-NVP models were proposed in [76] by replacing
standard coupling layers with conditional coupling layers.
Compared to standard coupling layers, the scale and translation
functions in conditional coupling layers are functions of con-
catenations of the base variable z1 = z1:d and a given condition
u ∈ Rdu, i.e. the input of the translation and scale functions
now becomes [ z
1:d
, u]. Specifically, a conditional coupling layer
can be formulated as:
s
1:d
= z
1:d
, (13)
s
d+1:D
= z
d+1:D
⊙ e
˜γφ( z1:d,u) + ˜ηφ( z1:d, u) , (14)
where ˜γφ(·) : Rd+du → RD−d and ˜ηφ(·) : Rd+du → RD−d
stand for the conditional scale function and the conditional
translation function, respectively.

IEEE TRANSACTIONS ON SIGNAL PROCESSING 5
Fig. 1: A diagram that shows the overall structure of the
proposed NF-DPF, illustrating how to generate new particles
and update particle weights in NF-DPFs. Blue circles refer to
random variables. Green rectangles refer to operations such as
drawing samples or evaluating certain functions.
IV. N ORMALIZING FLOW -BASED DIFFERENTIABLE
PARTICLE FILTERS
In this section, we present details of the proposed normalizing
flow-based differentiable particle filter (NF-DPF), including
its dynamic model, measurement model, and proposal distri-
bution. Specifically, we first show that normalizing flows can
provide a flexible mechanism for learning complex dynamics
of latent states. In addition, the construction of proposal distri-
butions with tractable proposal densities can also be achieved
using conditional normalizing flows. Lastly, we elaborate on
how to construct measurement models with valid probability
densities using conditional normalizing flows. An illustration
of the structure of the proposed NF-DPF is presented in Fig. 1.
Note that the parameter sets ϑ and φ in Section III-C are
respectively subsets of θ and ϕ and the normalizing flows in
this section are used to construct components in state-space
models, so we use Tθ(·) and Gϕ(·) instead of Tϑ(·) and Gφ(·)
to denote the normalizing flows in the following contents.
A. Dynamic models with normalizing flows
We first show how to use normalizing flows to construct
flexible dynamic models. Here we consider a base distribution
g(·|xt−1; θ), e.g. Gaussian distribution, from which we can
draw samples and obtain tractable probability density, and a
normalizing flow Tθ(·) : X → Xparametrized by θ. To draw
samples from the proposed dynamic model, a set of particles
{ ˙xit}Ni=1 are first drawn from g(·|xt−1; θ). Thereafter, { ˙xit}Ni=1
are further transformed by the normalizing flow Tθ(·) and
considered as samples from p(xt|xt−1; θ):
˙xit ∼ g( ˙xt|xt−1; θ) , (15)
xit = Tθ( ˙xit) ∼ p(xt|xt−1; θ) . (16)
By applying the change of variable formula, the probability
density function of the proposed dynamic model can be
formulated as:
p(xt|xt−1; θ) = g
 
˙xt|xt−1; θ
 det JTθ ( ˙xt)−1 , (17)
˙xt = T −1θ (xt) ∼ g  ˙xt|xt−1; θ , (18)
where det JTθ ( ˙xt) is the Jacobian determinant of Tθ(·) eval-
uated at ˙xt = T −1θ (xt).
B. Proposal distributions with conditional normalizing flows
We propose to incorporate information from observations
to construct proposal distributions by using conditional nor-
malizing flows. We use Fϕ(·) : X × Y → Xto denote a
conditional normalizing flow defined on X × Y, where X and
Y are the ranges of state xt and observation yt, respectively.
In the proposed method, particles sampled from the proposal
distributions are obtained by transforming samples from a base
proposal distribution h(·|xt−1, yt; ϕ), t ≥ 1, and h0(·|y0; ϕ),
t = 0, with the conditional normalizing flow Fϕ(·):
ˆxi0 ∼ h0(ˆx0|y0; ϕ) , (19)
ˆxit ∼ h(ˆxt|xt−1, yt; ϕ) , (20)
xi0 = Fϕ(ˆxi0; y0) ∼ q(x0|y0; ϕ) , (21)
xit = Fϕ(ˆxit; yt) ∼ q(xt|xt−1, yt; ϕ) . (22)
The base proposal distribution h(·|xt−1, yt; ϕ) is a distribu-
tion with a tractable probability density which we can draw
samples from, e.g. a Gaussian distribution. The conditional
normalizing flow Fϕ(·) is an invertible function of particles
ˆxit given the observation yt. Since the information from
observations is taken into account, the conditional normalizing
flow Fϕ(·) provides the capability to migrate particles to
regions that are closer to the true posterior distributions.
The proposal density can be obtained by applying the
change of variable formula:
q(xt|xt−1, yt; ϕ) = h (ˆxt|xt−1, yt; ϕ)
 det JFϕ (ˆxt; yt) −1 ,
(23)
ˆxt = F −1ϕ (xt; yt) ∼ h (ˆxt|xt−1, yt; ϕ) , (24)
where det JFϕ (ˆxt, yt) refers to the determinant of the Jacobian
matrix JFϕ (ˆxt; yt) = ∂Fϕ(ˆxt;yt)∂ ˆxt evaluated at ˆxt.
C. Conditional normalizing flow measurement models
Given an observation yt and a state value xt, we model
the relationship between yt and xt through a conditional
normalizing flow Gθ(·) : RdY × X:→ Y:
yt = Gθ(zt; xt) , (25)
where dY is the dimension of the observation yt, zt =
G−1θ (yt; xt) is the base variable which follows an independent
marginal distribution pZ(zt) defined on RdY , and the state xt
is the condition variable. Note that while the base distribution
pZ(zt) can be an arbitrary distribution with tractable densities,
standard Gaussian distributions are employed in this work

IEEE TRANSACTIONS ON SIGNAL PROCESSING 6
for the sake of simplicity. The main reason that conditional
normalizing flows are used for our measurement models is
that standard normalizing flows require their input and output
to have the same dimensionality, while yt and xt often differ in
their dimensionalities. Note that the invertible transformation
Gθ(·) used here is a new construction of conditional normal-
izing flow that is different from Fϕ(·), as they are used to
model different conditional probabilities.
With the conditional generative process of yt defined by
Eq. (25), we can evaluate the likelihood of the observation yt
given xt through:
zt = G−1θ (yt; xt) , (26)
p(yt|xt; θ) = pZ(zt)
 det JGθ (zt; xt)−1 . (27)
In scenarios where observations are high-dimensional such
as images, evaluating p(yt|xt; θ) with Eq. (27) using raw
observations yt can be computationally expensive. As an
alternative solution, we propose to map the observation yt to
a lower-dimensional space via et = Uθ(yt) ∈ Rde, where Uθ
is a parametrized encoder function Uθ(·) : RdY → Rde. To
ensure that the feature et maintains key features contained in
yt, we introduce a decoder Dθ(·) : Rde → RdY to reconstruct
yt, and include the following autoencoder (AE) loss into the
training objective:
LAE(θ) = 1T
TX
t=0
||Dθ(Uθ(yt)) − yt||22 , (28)
where T is the trajectory length. We then assume that the con-
ditional probability density p(et|xt; θ) of observation features
given state is an approximation of the actual measurement
likelihood p(yt|xt; θ) [34]:
et = Uθ(yt) , (29)
zt = G−1θ (et; xt) , (30)
p(yt|xt; θ) ≈ p(et|xt; θ) (31)
= pZ(zt)
 det JGθ (zt; xt)−1 . (32)
D. Importance weights update
Combining Eqs. (17), (23), and (32), in the proposed nor-
malizing flow-based differentiable particle filters, importance
weights of xit ∼ q(xit|xit−1, yt; ϕ) for t ≥ 1 are updated as
follows:
wit ∝ wit−1 p(yt|xit; θ)p(xit|xit−1; θ)q(xit|xit−1, yt; ϕ) (33)
= wit−1 pZ(zit) det JFϕ  ˆxit; yt g  ˙xit|xit−1; θ det JGθ (zit; xit)h  ˆxit|xit−1, yt; ϕ  det JTθ ( ˙xit) ,
(34)
where zit is computed by either Eq. (30) or Eq. (26), ˆxit =
F −1ϕ (xt; yt), ˙xit = T −1θ (xit), and wi0 is obtained by:
wi0 = pZ(zi0) det JFϕ  ˆxi0; y0 π(xi0; θ)h0(ˆxi0|y0; ϕ) det JGθ (zi0; xi0) . (35)
We provide in Algorithm 1 a detailed description of the
proposed normalizing flow-based differentiable particle filters
(NF-DPFs), where we use the entropy-regularized optimal
transport resampler Rϵ({xit}i∈[N ], { ˜wit}i∈[N ]) : RN ×dX ×
RN → RN ×dX in resampling steps [34], and denote the
entropy regularization coefficient by ϵ, the base distribution
pZ(·) is set to be a standard Gaussian distribution.
Algorithm 1 Normalizing flow-based differentiable particle
filters
1: Notations:
T Trajectory length
y0:T Observations
g(·) Base dynamic model
Fϕ(·)Proposal normalizing flow
N Number of particles
ξ Learning rate
Uθ(·) Observation encoder
ϵ regularization coefficient
x0:T Latent states
π(·; θ) Initial distribution of latent states
Tθ(·) Dynamic model normalizing flow
Gθ(·) Measurement normalizing flow
ESSmin Resampling threshold
L(θ, ϕ)Overall loss function
Rϵ(·) regularized OT resampler [34]
pZ (·) Standard Gaussian distribution
2: initialization: Randomly initialize θ and ϕ;
Sample ˆxi0 i.i.d∼ h0(ˆx0|y0; ϕ), ∀i ∈ [N ] := {1, · · ·, N}
(Eq. (19));
3: Generate proposed particles (Eq. (21)):
xi0 = Fϕ(ˆxi0; y0) ∼ q(x0|y0; ϕ), ∀i ∈ [N ];
4: [optional] Encode observation (Eq. (29)): y0 := Uθ(y0);
5: Compute the base variable (Eq. (30)):
zi0 = G−1θ (y0; xi0), ∀i ∈ [N ];
6: Compute weights wi0 using Eq. (35), ∀i ∈ [N ];
7: [optional] ˆp(y0; θ) = PNi=1 wi0/N;
8: for t = 1 to T do
9: Normalize weights ˜wit−1 ∝ wit−1, PNi=1 ˜wit−1 = 1;
10: Compute the effective sample size:
ESSt−1({ ˜wit−1}i∈[N ]) = 1PN
i=1( ˜wit−1)2 ;
11: if ESSt({ ˜wit−1}i∈[N ]) < ESSmin then
12: {˜xit−1}Ni=1 ← Rϵ({xit−1}i∈[N ], { ˜wit−1}i∈[N ]);
13: wit−1 ← 1, ∀i ∈ [N ];
14: else
15: ˜xit−1 ← xit−1, ∀i ∈ [N ];
16: end if
17: xit−1 ← ˜xit−1;
18: Sample ˆxit i.i.d∼ h (ˆxt|xt−1, yt; ϕ), ∀i ∈ [N ] (Eq. (19));
19: Generate proposed particles (Eq. (22)):
xit = Fϕ(ˆxit; yt) ∼ q(xt|xt−1, yt; ϕ), ∀i ∈ [N ];
20: [optional] Encode observation (Eq. (29)): yt := Uθ(yt);
21: Compute the base variable (Eq. (30)):
zit = G−1θ (yt; xit), ∀i ∈ [N ];
22: Update weights using Eq. (34):
wit = wit−1 p(yt|xit;θ)p(xit|xit−1;θ)q(xit|yt,xit−1;ϕ) , ∀i ∈ [N ];
23: [optional] ˆp(yt|y0:t−1; θ) = PNi=1 wit/ PNi=1 wit−1,
ˆp(y0:t; θ) = ˆp(yt|y0:t−1; θ)ˆp(y0:t−1; θ);
24: end for
25: Compute the overall loss L(θ, ϕ) (Examples of L(θ, ϕ)
can be found in Eq. (44) and Eq. (51));
26: Update θ and ϕ through gradient descent:
θ ← θ − ξ∇θL(θ, ϕ) , ϕ← ϕ − ξ∇ϕL(θ, ϕ) .

IEEE TRANSACTIONS ON SIGNAL PROCESSING 7
V. T HEORETICAL ANALYSIS
In this section, we establish convergence results for par-
ticle approximations in normalizing flow-based differentiable
particle filters. We assume resampling is performed at each
time step using the entropy-regularized optimal transport re-
sampler [34]. We use the notations below for the following
contents:
α(t) := p(xt|y0:t−1; θ) , α(t)N (ψ) := 1N
NX
i=1
ψ(xit) , (36)
β(t) := p(xt|y0:t; θ) , β(t)N (ψ) :=
NX
i=1
˜witψ(xit) , (37)
ω(t)(xt) = p(yt|xt; θ) , (38)
with α(0) := π(x0; θ), ψ(·) : X → R is a function
defined on X , α(t)N is an approximation of the predictive
distribution αt with N uniformly weighted particles, and β(t)N
is an approximation of the posterior distribution β(t) with N
particles weighted by ˜wit. For a measure α defined on X
we use α(ψ) =
R
X ψ(x)α(dx) to denote the expectation of
ψ(·) w.r.t. α. For the sake of simplicity, we restrict ourselves
to the bootstrap particle filtering framework, i.e. particles
xit are sampled from p(xt|xt−1; θ). However, our proof can
be modified to adapt to particle filters employing proposal
distributions that are distinct from their dynamic models by
taking into account the estimation error caused by sampling
from q(xt|xt−1, yt; ϕ) instead of p(xt|xt−1; θ).
To prove the consistency of particle approximations pro-
vided by NF-DPFs, we introduce the following assumptions:
Assumption V .1.X is a compact subset of RdX with diameter
d := sup
x,x′∈X
||x − x′||2, where || · ||2 denotes the Euclidean
distance.
Assumption V .2. For ∀t ≥ 0, there exists a unique optimal
transport plan between α(t) and β(t) featured by a determin-
istic transport map Tt(·) : X → X, and the transport map
Tt(·) is λ-Lipschitz for ∀t ≥ 0 with λ >0.
Assumption V .3. Denote by f (·) the transition kernel
p(xt|xt−1; θ) of NF-DPFs defined in Eq. (17) and ψ(·) : X →
R the considered bounded k-Lipschitz function, there exists an
η ∈ R such that for any two probability measures µ, ρon X
|µf (ψ) − ρf (ψ)| ≤η|µ(ψ) − ρ(ψ)| , s.t. µ(ψ) ̸= ρ(ψ) .
Assumption V .4. There exists a constant ζ ∈ R such that for
any continuous probability measure µ on X and its empirical
approximation µN , for weighted probability measures µωt =
ωtµ/µ(ωt) and µN,ωt = ωµN /µN (ωt), we have
W2(µN,ωt , µωt ) ≤ ζW2(µN , µ) ,
where ωt(·) : X → R is defined in Eq. (38), and W2(·, ·)
refers to the 2-Wasserstein distance [60], [78].
With the above assumptions, we provide the following
proposition for the consistency of NF-DPFs:
Proposition V .1. For a bounded weight function ωt(xt) =
p(yt|xt; θ) : X →R and a measurable bounded k-Lipschitz
function ψ(·) : X →R, when the regularization coefficient
in entropy-regularized optimal transport resampler ϵN =
o(1/ log N ), there exist constants ct and c′t such that for t ≥ 0
E
"
α(t)N (ψ) − β(t−1)f (ψ)
2#
≤ ct
||ψ||2∞
N 1/2dX
(39)
(replacing β(t−1)f by the initial distribution π(x0, θ) at time
t = 0 defined in Eq. (1)) and
E
"
β(t)N (ψ) − β(t)(ψ)
2#
≤ c′t ||ψ||2∞N 1/2dX , (40)
where ||ψ||∞ := sup
x∈X
|ψ(x)| is the infinity norm of ψ(·), β(t)
and α(t)N are respectively defined by Eqs. (36) and (37), and
f (·) is the transition kernel defined by Eq. (2).
The proof of Proposition V .1 can be found in Appendix B.
The results in Proposition V .1 show that the particle estimates
given by the NF-DPF are consistent estimators if ϵN =
o(1/ log N ), i.e. the estimation error vanishes when N → ∞.
The error bounds we derived converge at OP ( 1N 1/2dX ) andare tighter than those derived in [34], which converge at
OP ( 1N 1/8dX ), where OP denotes the ”big O in probability” no-
tation. Specifically, in [34] the upper bound on W2(β(t), β(t)N )
is adopted as the upper bound on the approximation error.
As a result, the upper bound derived in [34] is loose since
the gap between W2(β(t), β(t)N ) and the approximation error
is included in the upper bound. The tighter bound presented
in Proposition V .1 is achieved by directly deriving an upper
bound for E
"
α(t)N (ψ) − β(t−1)f (ψ)
2#
and E
"
β(t)N (ψ) −
β(t)(ψ)
2#
without relying on the upper bound on the Wasser-
stein distances. However, compared with traditional particle
filters [79], the error bound is loose due to the use of entropy-
regularized optimal transport resampling, as we revealed in
the proof. We provide background knowledge about optimal
transport and related notations in Appendix A.
VI. E XPERIMENTS
In this section, we present experimental results to compare
the performance of the proposed normalizing flow-based dif-
ferentiable particle filters (NF-DPFs) with other DPF variants1.
We consider in Section VI-A a one-dimensional linear Gaus-
sian state-space model similar to an example used in [39]. In
Section VI-B we evaluate the performance of the proposed
method on a multivariate linear Gaussian state-space model
similar to the one used in [34] with varying dimensionalities.
In Section VI-C we compare the performance of NF-DPFs
with other state-of-the-art DPFs in a synthetic visual tracking
task following the setup in [36], [46], [80]. The experimental
results on a simulated robot localization task from [32], [34],
1Code to reproduce experiment results is available at https://github.com/
xiongjiechen/Normalizing-Flows-DPFs.

IEEE TRANSACTIONS ON SIGNAL PROCESSING 8
[81] are reported in Section VI-D. For all experiments pre-
sented in this section, the entropy-regularized optimal transport
resampler [34] is applied in the resampling step. We use
the Real-NVP and the conditional Real-NVP models as the
default normalizing flows and conditional normalizing flows in
the NF-DPF, except in the one-dimensional example, because
Real-NVP models have to split the latent state dimension-wise.
We compare NF-DPFs with five baseline methods in our
experiments, the deep state-space model (Deep SSM), the au-
toencoder sequential Monte Carlo (AESMC) and the AESMC-
bootstrap proposed in [39], the particle filter recurrent neural
networks (PFRNNs) [57], and the particle filter networks
(PFNets) [33]. The deep state-space model (Deep SSM) em-
ploys recurrent neural networks to infer the parameters of
state-space models [82]. The AESMC-bootstrap uses Gaussian
distributions to construct its dynamic model and measurement
model and new particles are generated from the learned
dynamic model. The proposal distributions of the AESMC
are constructed by Gaussian distributions with parameters
determined by observations. The PFRNN uses recurrent neural
networks with observations and latent states as inputs to
generate new particles. We use PFNets to denote the method
proposed in [33] and its concurrent work [32], which are
bootstrap differentiable particle filters with dynamic models
and measurement models built by vanilla neural networks.
A. One-dimensional Linear Gaussian State-Space Models
1) Experiment setup: We first consider a one-dimensional
example as in [39], for which the goal is to learn the parame-
ters θ∗ := [θ∗1, θ∗2] and a proposal distribution q(xt|xt−1, yt; ϕ)
for the following linear Gaussian state-space model:
x0 ∼ N(0, 1) , (41)
xt|xt−1 ∼ N(θ∗1xt−1, 1) for t ≥ 1 , (42)
yt|xt ∼ N(θ∗2xt, 0.1) for t ≥ 0 . (43)
We adopt the evidence lower bound (ELBO)
E[log p(y0:T ; θ)] of the log marginal likelihood as the
training objective as in [38]–[40], and we approximate the
ELBO through:
E[log p(y0:T ; θ)] ≈ 1K
KX
k=1
log ˆp(ykT ; θ) , (44)
where K = 10 is the number of training sequences, and
log ˆp(ykT ; θ) is computed as in Line 23 of Alg. 1. We use
a fixed learning rate of 0.002 and optimize the model for
500 iterations. At each iteration, we feed the model K = 10
sequences of observations y0:T generated with T = 50 and
θ∗ := [ θ∗1, θ∗2] = [0 .9, 0.5]. We also use 1000 sequences of
observations as our validation set. The trained model is then
tested with another 1000 observation sequences. We set the
number of particles as N = 100 for training, validation, and
testing stages. Since the goal in this experiment is to simul-
taneously learn the model parameters θ := [θ1, θ2] (initialized
as [0.1, 0.1]) and proposal distributions q(xt|xt−1, yt; ϕ), the
state-space model to be optimized is in the same form as the
true model:
x0 ∼ N(0, 1) , (45)
xt|xt−1 ∼ N(θ1xt−1, 1) for t ≥ 1 (46)
yt|xt ∼ N(θ2xt, 0.1) for t ≥ 0 , (47)
such that we can evaluate the difference between the true
model parameters and the learned model parameters.
The performance of trained models is evaluated based on
four metrics:
• The L2-norm ||θ − θ∗||2 between the learned parameters
θ := [ θ1, θ2] and true parameters θ∗ := [ θ∗1, θ∗2] =
[0.9, 0.5];
• The L2-norm || ¯χT − ¯χ∗T ||2 between the estimated poste-
rior means ¯χT and the true posterior means ¯χ∗T computed
by Kalman filter, where ¯χT := [¯x0, ¯x1, · · ·, ¯xT ] and
¯χ∗T := [¯x∗0, ¯x∗1, · · ·, ¯x∗T ];
• The ELBO defined by Eq. (44).
• The effective sample size.
Lower ||θ−θ∗||2, || ¯χT − ¯χ∗T ||2, and higher ELBO and effective
sample size indicate better performance of evaluated models.
2) Experimental results: We report in Fig. 2 and Table I the
evaluated metrics for different methods on the validation set
and the test set, respectively. We observe that the PFNet can
achieve arbitrarily large ELBOs but produces poor tracking
performance, so we do not report the performance of the
PFNet in this experiment. The main reason for this is that
the measurement model of the PFNet is constructed with
vanilla neural networks, and the ELBO can be increased
by simply amplifying the magnitude of the neural network’s
output without learning the relationship between observations
and states.
For the ELBO, all methods converge to almost the same
validation ELBO as demonstrated in Fig. 2c. The AESMC-
bootstrap converges the fastest. We speculate that this is
because it does not have proposal parameters to learn, so it
can focus on learning model parameters. This is also reflected
in Fig. 2a and the second column of Table I, where we
can observe that all approaches produce similar parameter
estimation errors after their convergence, and the AESMC-
bootstrap has the highest convergence rate but exhibits slightly
larger parameter estimation error than other methods. The NF-
DPF converges faster than the AESMC and the PFRNN has
the highest ELBO and the lowest parameter estimation error.
We report posterior mean errors || ¯χT − ¯χ∗T ||2 evaluated on
the validation set and the test set for different methods in
Fig. 2b and Table I respectively. The AESMC-bootstrap leads
to the highest estimation error as expected. The AESMC pro-
duces better results compared to the AESMC-bootstrap. The
PFRNN reports the second lowest test posterior mean error
after the convergence. Deep SSM has similar performance to
PFRNN on both validation and test datasets. The NF-DPF
outperforms all the compared baselines regarding both the
convergence rate and the validation error when training has
converged. The NF-DPF leads to the highest effective sample
size among all the evaluated methods.

IEEE TRANSACTIONS ON SIGNAL PROCESSING 9
TABLE I: Evaluation metrics of different methods evaluated on the test set with 1000 sequences. Lower parameter estimation
error, posterior mean error, higher effective sample size, and ELBO indicate better performance. The reported parameter
estimation error, posterior mean error, and ELBO are computed with the model saved at the last iteration. The average
effective sample size is the mean of effective sample sizes at each time step. The reported mean and standard deviation are
computed with 50 random runs. The running time per training iteration is computed based on a computer with an 13th Gen
Intel(R) Core(TM) i9-13900KF CPU 3000Mhz and 64GB of RAM, and a RTX 4090 graphic card with 24GB memories.
Method ||θ − θ∗||2 ↓ || ¯χT − ¯χ∗T ||2↓ Average effectivesample size ↑ ELBO ↑ Training time(s/it)
Deep SSM [38] 0.0234 ± 0.0121 3.20 ± 0.389 63.7 ± 8.52 −50.3 ± 1.68 0.189
AESMC-Bootstrap [38] 0.0271 ± 0.0133 7.13 ± 0.233 36.9 ± 1.52 −50.4 ± 1.72 0.182
AESMC [38] 0.0231 ± 0.0108 3.99 ± 1.316 58.1 ± 14.24 −50.1 ± 1.51 0.192
PFRNN [57] 0.0251 ± 0.015 3.18 ± 0.456 63.8 ± 11.11 −50.1 ± 1.94 0.204
NF-DPF 0.0207 ± 0.0083 2.07 ± 0.304 76.0 ± 6.26 -49.6 ± 1.61 0.231
1 100 200 300 400 500
Iteration
.02
.04
.08
.16
.32
.64
||θ−θ*||2
AESMC-Bootstrap
AESMC
PFRNN
Deep SSM
NF-DPF
1 100 200 300 400 500
Iteration
2
4
6
8
10
12
14
||̄ χT−̄ χ*T||2
1 100 200 300 400 500
Iteration
−400
−300
−200
−100
ELBO
0 10 20 30 40 50
Step
40
50
60
70
80Effective sample size
(a)
1 100 200 300 400 500
Iteration
.02
.04
.08
.16
.32
.64
||θ−θ*||2
AESMC-Bootstrap
AESMC
PFRNN
Deep SSM
NF-DPF
1 100 200 300 400 500
Iteration
2
4
6
8
10
12
14
||̄ χT−̄ χ*T||2
1 100 200 300 400 500
Iteration
−400
−300
−200
−100
ELBO
0 10 20 30 40 50
Step
40
50
60
70
80Effective sample size (b)
1 100 200 300 400 500
Iteration
.02
.04
.08
.16
.32
.64
||θ−θ*||2
AESMC-Bootstrap
AESMC
PFRNN
Deep SSM
NF-DPF
1 100 200 300 400 500
Iteration
2
4
6
8
10
12
14
||̄ χT−̄ χ*T||2
1 100 200 300 400 500
Iteration
−400
−300
−200
−100
ELBO
0 10 20 30 40 50
Step
40
50
60
70
80Effective sample size
(c)
1 100 200 300 400 500
Iteration
.02
.04
.08
.16
.32
.64
||θ−θ*||2
AESMC-Bootstrap
AESMC
PFRNN
Deep SSM
NF-DPF
1 100 200 300 400 500
Iteration
2
4
6
8
10
12
14
||̄ χT−̄ χ*T||2
1 100 200 300 400 500
Iteration
−400
−300
−200
−100
ELBO
0 10 20 30 40 50
Step
40
50
60
70
80Effective sample size (d)
Fig. 2: Evaluation metrics of different methods evaluated on
the validation set with 1000 sequences. (a) L2-norm between
the true parameter set and the estimated parameter sets. (b)
L2-norm of posterior mean error evaluated on validation set.
(c) ELBO evaluated on validation set. (d) Effective sample
size on validation set. Lower parameter estimation error,
posterior mean error, higher effective sample size, and ELBO
indicate better performance. The shaded area represents the
standard deviation of the presented evaluation metrics among
50 random simulations.
B. Multivariate Linear Gaussian State-Space Models
1) Experiment setup: In this experiment, we extend
the one-dimensional example in Section VI-A to higher
dimensional-spaces to evaluate the performance of the NF-
DPF. Following the setup in [34], we consider a similar
multivariate linear Gaussian state-space model as below:
x0 ∼ N(0dX , IdX ) , (48)
xt|xt−1 ∼ N(θ∗1xt−1, IdX ) for t ≥ 1 , (49)
yt|xt ∼ N(θ∗2xt, 0.1IdX ) for t ≥ 0 , (50)
where 0dX is a dX × dX null matrix, IdX is a dX × dX
identity matrix, the element of θ∗1 at the intersection of its
i-th row and j-th column θ∗1(i, j) = (0 .42|i−j|+1)1≤i,j≤dX ,
θ∗2 is a dY × dX matrix with 0.5 on the diagonal for the
first dY rows and zeros elsewhere. We set dX = dY in
this experiment. We again want to learn model parameters
θ∗ := [ θ∗1, θ∗2] and proposal distributions by maximizing the
evidence lower bound (ELBO) as in Section VI-A. We also use
the same hyperparameter setting in Section VI-A, and train the
compared models with 5000 sequences for 500 iterations (10
sequences for each iteration). Validation and test sets contain
1000 i.i.d sequences each. Model parameters θ := [θ1, θ2] to
be optimized are initialized as [0.1 × IdX , 0.1 × IdX ].
2) Experimental results: In Fig. 3 and Table II, we
show the test performance of NF-DPFs, the Deep SSM,
the PFRNN, and the AESMC in dX -dimensional spaces for
dX ∈ {2, 5, 10, 25, 50, 100}. The AESMC-bootstrap particle
filter is excluded in this experiment because its estimation
error is too large to be compared with the other methods in the
same figure. The evaluation metrics reported in Section VI-A
are used in this experiment as well.
For model parameters learning, from Fig. 3a, Fig. 3c, and
Table II, we found that NF-DPFs produced the highest ELBOs
in 4 out of 6 setups, and all the evaluated methods achieved
similar parameter estimation errors. We also observed that
higher ELBOs and lower parameter estimation errors do not
necessarily correspond to better posterior approximation errors
as we can see from Fig. 3 and Table II. Specifically, from
Fig. 3b and Table II, NF-DPFs outperform the compared base-
lines in terms of posterior approximation errors by consistently
leading to the lowest posterior mean errors and the highest
effective sample sizes for dX ∈ {2, 5, 10, 25, 50, 100}.
C. Disk Localization
1) Experiment setup: We consider in this experiment a disk
localization task, where the goal is to locate a moving red
disk based on observation images. Specifically, an observation
image is a 128 ×128 RGB image that contains 25 disks,
including the red disk and 24 distracting disks with varying
sizes and colors, and such an observation image is given at
each time step. The colors of distracting disks are uniformly
drawn with replacement from the set of {green, blue, cyan,
purple, yellow, white }, and the radii of them are uniformly

IEEE TRANSACTIONS ON SIGNAL PROCESSING 10
TABLE II: Evaluation metrics of different methods evaluated on a test set with 1000 sequences. Lower parameter estimation
error, posterior mean error, higher effective sample size, and ELBO indicate better performance. The reported parameter
estimation error, posterior mean error, and ELBO are computed with the model saved at the last iteration. The average
effective sample size is the mean of effective sample size at each time step. The reported mean and standard deviation is
computed with 50 random runs.
Dimension Method ||θ − θ∗||2 ↓ || ¯χT − ¯χ∗T ||2↓ Average effectivesample size ↑ ELBO ↑ Training time(s/it)
D = 2
Deep SSM [82] 0.061 ± 0.0229 6.83 ± 1.92 58.8 ± 6.01 −120.3 ± 1.30 0.279
AESMC [38] 0.065 ± 0.0226 6.85 ± 1.16 47.5 ± 12.51 −119.3 ± 2.80 0.272
PFRNN [57] 0.071 ± 0.0181 5.82 ± 1.45 57.2 ± 10.18 −119.8 ± 2.67 0.317
NF-DPF 0.075 ± 0.0120 4.48 ± 0.84 58.6 ± 6.46 -119.2 ± 1.88 0.361
D = 5
Deep SSM [82] 0.171 ± 0.0172 10.68 ± 1.48 32.2 ± 4.87 −301.8 ± 3.52 0.319
AESMC [38] 0.148 ± 0.0120 13.25 ± 1.62 17.1 ± 2.83 −303.3 ± 2.64 0.309
PFRNN [57] 0.158 ± 0.0156 10.27 ± 0.40 26.6 ± 2.60 −302.6 ± 3.19 0.328
NF-DPF 0.151 ± 0.0105 7.44 ± 1.55 34.9 ± 5.29 -301.6 ± 3.25 0.371
D = 10
Deep SSM [82] 0.264 ± 0.0292 12.64 ± 0.82 17.1 ± 2.98 −604.8 ± 4.85 0.351
AESMC [38] 0.304 ± 0.0214 19.17 ± 1.88 8.6 ± 1.73 −609.7 ± 6.24 0.327
PFRNN [57] 0.275 ± 0.0148 14.89 ± 0.32 16.2 ± 1.24 −608.5 ± 7.18 0.357
NF-DPF 0.257 ± 0.0116 11.18 ± 1.28 18.5 ± 2.37 -603.3 ± 5.02 0.385
D = 25
Deep SSM [82] 0.657 ± 0.0372 25.41 ± 1.35 5.7 ± 0.79 −1532.7 ± 8.62 0.351
AESMC [38] 0.712 ± 0.0191 31.46 ± 2.12 4.0 ± 0.22 −1537.5 ± 12.14 0.348
PFRNN [57] 0.704 ± 0.0312 30.21 ± 1.03 4.0 ± 0.39 −1534.2 ± 6.46 0.378
NF-DPF 0.626 ± 0.0188 20.51 ± 1.21 5.6 ± 0.45 -1529.0 ± 12.53 0.412
D = 50
Deep SSM [82] 1.23 ± 0.0168 38.33 ± 0.58 2.6 ± 0.65 −3128.6 ± 16.40 0.387
AESMC [38] 1.233 ± 0.0260 44.83 ± 0.92 2.7 ± 0.37 −3135.0 ± 19.56 0.382
PFRNN [57] 1.210 ± 0.0222 40.14 ± 0.61 2.7 ± 0.13 -3121.7 ± 6.39 0.442
NF-DPF 1.252 ± 0.0189 34.73 ± 1.81 3.0 ± 0.11 −3135.4 ± 28.53 0.482
D = 100
Deep SSM [82] 2.158 ± 0.0531 60.19 ± 1.69 1.3 ± 0.26 -6431.8 ± 69.67 0.501
AESMC [38] 2.007 ± 0.0255 70.16 ± 2.23 1.9 ± 0.28 −6438.1 ± 34.80 0.478
PFRNN [57] 2.064 ± 0.0272 63.51 ± 2.78 1.9 ± 0.47 −6454.8 ± 52.32 0.501
NF-DPF 2.228 ± 0.0419 58.27 ± 1.45 2.0 ± 0.18 −6447.4 ± 80.01 0.581
2 5 10 25 50 100
Dimension
0.0
0.5
1.0
1.5
2.0
||θ−θ*||2
NF-DPF
PFRNN
AESMC
Deep SSM
2 5 10 25 50 100
Dimension
0
20
40
60
||̄ χT−̄ χ*T||2
2 5 10 25 50 100
Dimension
-6e3
-4e3
-2e3
0
ELBO
2 5 10 25 50 100
Dimension
0
10
20
30
40
50
60
Effective sample size
(a)
2 5 10 25 50 100
Dimension
0.0
0.5
1.0
1.5
2.0
||θ−θ*||2
NF-DPF
PFRNN
AESMC
Deep SSM
2 5 10 25 50 100
Dimension
0
20
40
60
||̄ χT−̄ χ*T||2
2 5 10 25 50 100
Dimension
-6e3
-4e3
-2e3
0
ELBO
2 5 10 25 50 100
Dimension
0
10
20
30
40
50
60
Effective sample size (b)
2 5 10 25 50 100
Dimension
0.0
0.5
1.0
1.5
2.0
||θ−θ*||2
NF-DPF
PFRNN
AESMC
Deep SSM
2 5 10 25 50 100
Dimension
0
20
40
60
||̄ χT−̄ χ*T||2
2 5 10 25 50 100
Dimension
-6e3
-4e3
-2e3
0
ELBO
2 5 10 25 50 100
Dimension
0
10
20
30
40
50
60
Effective sample size
(c)
2 5 10 25 50 100
Dimension
0.0
0.5
1.0
1.5
2.0
||θ−θ*||2
NF-DPF
PFRNN
AESMC
Deep SSM
2 5 10 25 50 100
Dimension
0
20
40
60
||̄ χT−̄ χ*T||2
2 5 10 25 50 100
Dimension
-6e3
-4e3
-2e3
0
ELBO
2 5 10 25 50 100
Dimension
0
10
20
30
40
50
60
Effective sample size (d)
Fig. 3: Evaluation metrics of different methods evaluated
on a test set with 1000 sequences. (a) L2-norm between
the true parameter set and the estimated parameter sets. (b)
L2-norm of posterior mean error evaluated on test set. (c)
ELBO evaluated on test set. (d) Effective sample size on
test set. Lower parameter estimation error, posterior mean
error, higher effective sample size, and ELBO indicate better
performance. The reported results are the mean of evaluation
metrics computed over 50 random simulations.
sampled with replacement from {3, 4,· · ·, 10}. The radius of
the target, i.e. the red disk, is set to be 7. The initial locations
of the 25 disks are uniformly distributed over the observation
image as shown in Fig. 4a.
Following the setup in [34], [45], [46], we use a combination
of two loss functions as our training objective:
L(θ, ϕ) := LRMSE(θ, ϕ) + LAE(θ) , (51)
where LRMSE(θ, ϕ) is the root mean square error (RMSE) be-
tween the estimated location ¯xt and the ground truth location
x∗t of the red disk
LRMSE(θ, ϕ) :=
vuut 1
T
TX
t=0
||¯xt − x∗t ||22 , (52)
and LAE(θ) is the autoencoder reconstruction loss of ob-
servation images as defined in Eq. (28). We use an Adam
optimizer [83] with a learning rate of 0.001 to minimize the
overall loss function L(θ, ϕ).
The dynamic system used for generating training, validation,
and test sets for this experiment follows the setup in [36]. The
training set we use to optimize DPFs contains 500 trajectories,
each with 50 time steps, and both the validation and test sets
are composed of 50 trajectories with the same length as the
training trajectories.
The performance of different DPFs is evaluated by the
RMSE between estimated locations and ground truth locations
of the tracking objective. We report both the test RMSE and
the validation RMSE to investigate the tracking performance
of different DPFs during and after training.
2) Experimental results: The experimental results shown
in Fig. 4c are the validation RMSEs of different methods

IEEE TRANSACTIONS ON SIGNAL PROCESSING 11
(a)
1 10 20 30 40 50
Evaluated time step
1
2
4
8
16
32
64T est RMSE
Deep SSM
PFRNN
AESMC-Bootstrap
PFNet
AESMC
NF-DPF (b)
1 50 100 150
Training Epoch
3
4
7
17
50Validation RMSE
Deep SSM
AESMC-Bootstrap
AESMC
PFRNN
PFNet
NF-DPF
(c)
Fig. 4: (A) An example of observation images. (B) RMSE
of different methods evaluated at selected time steps on test
set. (C) RMSE of different differentiable particle filters on
the validation set during training. Shaded areas represent the
standard deviation of the presented evaluation metrics among
5 random simulations.
1 10 20 30 40 50
Evaluated time step
1
2
4
8
16
32
64T est RMSE
NF-DPF-D
NF-DPF
NF-DPF-P
NF-DPF-M
(a)
1 50 100 150
Training Epoch
3
4
7
17
50Validation RMSE
NF-DPF-D
NF-DPF-P
NF-DPF-M
NF-DPF (b)
Fig. 5: Ablation studies conducted in the disk localization ex-
periment to investigate how each individual component of the
NF-DPF affects its performance. (a) RMSE of variants of the
NF-DPF evaluated at selected time steps on test set. (b) RMSE
of different variants of the NF-DPF on the validation set during
training. Shaded areas represent the standard deviation of the
presented evaluation metrics among 5 random simulations.
TABLE III: Disk tracking RMSE of different differentiable
particle filters. The reported RMSE is averaged over 50 time
steps for 50 trajectories in the test set, and the standard
deviation is computed with 5 simulation runs with different
random seeds.
Method Deep
SSM
AESMC
Bootstrap
AESMC PFRNN PFNet NF-DPF
RMSE 5.91±1.20 6.35±1.15 5.85±1.34 6.12±1.23 5.34±1.27 3.62±0.98
Training
time (s/it) 0.578 0.572 0.618 0.687 0.572 1.041
TABLE IV: Disk tracking RMSE of different variants of the
NF-DPF. The reported RMSE is averaged over 50 time steps
for 50 trajectories in the test set, and the standard deviation is
computed with 5 simulation runs with different random seeds.
Method NF-DPF-D NF-DPF-P NF-DPF-M NF-DPF
RMSE 5.65±0.95 5.21±1.12 3.81±1.05 3.62±0.98
evaluated during training. It can be observed that the NF-
DPF requires fewer training epochs to converge but in the
meantime achieves better tracking performance compared with
the other evaluated approaches. For all methods, we saved the
best models with the lowest validation error and used them to
compute the tracking error on the test set.
We report the test RMSEs of different differentiable particle
filters in Table III. The experimental results in Table III again
demonstrated the benefit of using (conditional) normalizing
flows to construct differentiable particle filters. It can be
observed from Table III that among all the tested methods, the
proposed NF-DPF produces the lowest mean tracking error.
Fig. 4b compares tracking RMSEs from different methods
on the test set. From Fig. 4b, we found that, except for the
first step t = 1, the proposed NF-DPFs achieved the lowest
tracking RMSE at all evaluated time steps compared with the
other evaluated methods.
To investigate how each component of the NF-DPF influ-
ences its performance, we conducted an ablation study in this
experiment. The results of the ablation study are presented
in Figure 5 and Table IV, where NF-DPF-D, NF-DPF-P, and
NF-DPF-M respectively refer to the method that only uses
normalizing flows to construct its dynamic model, proposal
distribution, and measurement model. It can be observed that
among the three components, the measurement model brought
the most significant performance improvement to the NF-
DPF. The NF-DPF-P produced lower localization error than
all the other baseline methods. The NF-DPF-D outperformed
3 out of 4 baseline methods. We hypothesize that the primary
factor contributing to the superior performance of NF-DPF-
M compared to other variants is that, in this experiment, the
location of the target disk can be directly observed from the
observation image. Please note that the conclusions drawn
from this ablation study may not be applicable to other
environments. More extensive ablation studies are required to
gain a better understanding of the role of different components
in the NF-DPF.
D. Robot Localization in Maze Environments
1) Experiment setup: In this experiment, we evaluate the
performance of NF-DPFs in three environments, namely Maze
1, Maze 2, and Maze 3, simulated in the DeepMind Lab [81]
following the setup in [32], [34]. In each of the three maze
environments, there exists a simulated robot moving through
the maze, and its locations lt = ( l(1)t , l(2)t ), orientations ϱt,
velocity ∆lt = (∆ l(1)t , ∆l(2)t , ∆ϱt), and camera images yt
are available for model training. The collected dataset is split
into training, validation, and test sets containing 900, 100, and
100 robot trajectories, each with a length of 100 time steps,

IEEE TRANSACTIONS ON SIGNAL PROCESSING 12
respectively. We set the learning rate to be 0.001, and use the
Adam optimizer to train DPFs.
Based on image observations given by robot cameras, the
goal in this task is to infer the location and the orientation
of the robot at each time step, i.e. the latent state xt :=
(l(1)t , l(2)t , ϱt). We give an example of observation images in
Fig. 6a. Particles are uniformly initialized over the maze in the
first step. The dynamic model we use in DPFs is as follows:
xt+1 : =

 l(1)t+1l(2)t+1
ϱt+1


=

 l(1)t + ∆l(1)t cos (ϱt) + ∆l(2)t sin (ϱt)l(2)t + ∆l(1)t sin (ϱt) − ∆l(2)t cos (ϱt)
ϱt + ∆ϱt

 + ςt ,
(53)
where ςt ∼ N(0, Σ2) is the dynamic noise, and Σ :=
diag(σl, σl, σϱ) with σl = 10 and σϱ = 0.1.
The loss function L(θ, ϕ) := LRMSE(θ, ϕ) + LAE(θ) used
in this experiment consists of a root mean square error loss
LRMSE(θ, ϕ) and an autoencoder loss LAE(θ) as in Sec-
tion VI-C. The evaluation metric we use to compare the
performances of different DPFs is the RMSE error between
estimated robot locations and true robot locations on validation
and test sets.
(a)
1 25 50 75 100
Training Epoch
100
150
200
250
300Validation RMSE
Deep SSM
AESMC-Bootstrap
AESMC
PFRNN
PFNet
NF-DPF (b)
1 25 50 75 100
Training Epoch
150
250
350
450Validation RMSE
Deep SSM
AESMC-Bootstrap
AESMC
PFNet
PFRNN
NF-DPF
(c)
1 25 50 75 100
Training Epoch
400
500
600
700Validation RMSE
Deep SSM
AESMC
AESMC-Bootstrap
PFNet
PFRNN
NF-DPF (d)
Fig. 6: (A) An example of observation images in maze
environments. RMSE of different DPFs on the validation set
during training in (B) Maze 1. (C) Maze 2. (D) Maze 3. The
shaded area represents the standard deviation of the presented
evaluation metrics among 5 random simulations.
2) Experimental results: We first show validation RM-
SEs of tested methods in Figs. 6b, 6c, and 6d. Since the
size of environments varies from maze to maze (Maze 1:
500×1000, Maze 2: 900 ×1500, Maze 3: 1300 ×2000), the
reported RMSEs increase as the maze gets larger. As expected,
(a) Time step 0
 (b) Time step 25
(c) Time step 50
 (d) Time step 100
Fig. 7: A visualization of the localization results of the NF-
DPF at different time steps. Arrows represent the orientation
ϱt of particles and robots. The deeper the color of a particle,
the higher its importance weight.
the proposed NF-DPF outperformed the other differentiable
particle filtering frameworks regarding validation RMSEs in
all three maze environments when the training has finished. In
Table V, we report the RMSE of different methods at the last
time step t = 100 on the test set. Experimental results shown
in Table V illustrate the superior performance of the proposed
NF-DPF compared with the baseline methods. Specifically,
the NF-DPF has the lowest RMSEs at the last time step in
all three maze environments, implying that the NF-DPF can
better localize the object for longer sequences.
TABLE V: Test RMSE of different DPFs in maze envi-
ronments. The reported RMSE is computed at the last step
t = 100 for 100 trajectories in the test set. Standard deviations
are computed with 5 simulation runs with different random
seeds.
Method Maze 1 Maze 2 Maze 3RMSE s/it RMSE s/it RMSE s/it
Deep SSM 61.0±10.8 0.571 114.0±8.8 0.557 203.0±10.1 0.580
AESMC
Bootstrap 56.5±11.5 0.567 115.6±6.8 0.561 220.6±11.1 0.552
AESMC 52.1±7.5 0.602 109.2±11.7 0.612 201.3±14.7 0.607
PFNet 51.4±8.7 0.581 120.3±8.7 0.597 212.1±15.3 0.601
PFRNN 54.1±8.9 0.644 125.1±8.2 0.631 210.5±10.8 0.650
NF-DPF 46.1±6.9 0.667 103.2±10.8 0.661 182.2±19.9 0.672
We provide a visualization of the localization results in
Fig. 7, where the particles, true robot locations, and estimated
robot locations at different time steps are visualized. Fig. 7a
shows the localization result at the initialization step t = 0.
We can see that in Fig. 7a, the estimation is located around the
center of the maze and is far from the true location, which is
expected because the particles are uniformly initialized at time
step t = 0. In Fig. 7b, Fig. 7c, and Fig. 7d, it can be found
that in later time steps, the NF-DPF can produce estimated
locations that are close to the ground-truth locations, with

IEEE TRANSACTIONS ON SIGNAL PROCESSING 13
particles centered at the ground-truth locations. In addition,
we also observe that the learned measurement model can
capture the relationship between observation images yt and
robot locations xt. In Fig. 7, especially Fig. 7d, it is obvious
that particles that are close to the true robot location are
assigned greater importance weights, and vice versa.
E. Robot tracking in Michigan NCLT dataset
1) Experiment setup: In this experiment, we evaluate the
performance of baseline methods and the proposed NF-DPF
in a real-world dataset, the Michigan North Campus Long-
Term (NCLT) dataset [84]. The NCLT dataset consists of
robot trajectories collected at 26 sessions. The trajectories are
labeled, meaning that the ground-truth location of the robot is
accessible. The latent state is the robot location and its velocity
xt = [l(1)t , l(2)t , ∆l(1)t , ∆l(2)t ]⊺. Observations in this dataset are
noisy sensor readings such as GPS and odometer. In this ex-
periment, we only use the odometer reading as the observation,
following the settings in [85]. The goal in this experiment is
to track the location of the moving robot, and we initialize the
latent state xt with the ground-truth latent state. Following the
setup in [85], we use the trajectory collected on 2012-01-22
and sample the trajectory with a frequency of 1 Hz, resulting
in 5,850 time steps. We split the 5,850 time steps into training,
validation, and test datasets. The training, validation, and test
datasets respectively comprise 20 trajectories of length 234, 3
trajectories of length 195, and 3 trajectories of length 195. We
use the RMSE between the ground-truth location of the robot
and the estimated location of the robot as both the training
objective and the evaluation metric. Since observations in this
experiment are 2-dimensional vectors and there is no need to
encode the observations into feature vectors, the autoencoder
reconstruction loss is not included in the loss function for this
experiment.
From the experimental results shown in Table VI, we
observed that the PFNet achieved the lowest RMSE, and our
method produced slightly higher RMSE and lower standard
deviation than the PFNet in this experiment. We speculate that
the reason why proposed NF-DPF did not produce the best
tracking performance is that the latent dynamics of the robot
are relatively simple and the observation in this experiment
is uninformative, so that using a very expressive model like
NF-DPF only brings very marginal benefit and may result in
overfitting.
TABLE VI: Robot tracking RMSE of different differentiable
particle filters in the NCLT dataset. The reported RMSE is
averaged over 195 time steps for 3 trajectories in the test set,
and the standard deviation is computed with 5 simulation runs
with different random seeds.
Method Deep SSM AESMCBootstrap AESMC PFRNN PFNet NF-DPF
RMSE 56.3±4.5 60.3±3.8 57.5±5.2 59.2±5.1 53.5±5.7 54.8±4.8
VII. C ONCLUSION
This paper introduced a novel variant of differentiable par-
ticle filters (DPFs), the normalizing flow-based differentiable
particle filter (NF-DPF), which is built based on normalizing
flows and conditional normalizing flows. The proposed NF-
DPF first provides a general mechanism to construct data-
adaptive dynamic models, proposal distributions, and measure-
ment models, three of the core components of particle filters.
The theoretical analysis shows the consistency of the proposed
NF-DPF and derives an upper bound for its estimation error.
We empirically showed the superior performance of the NF-
DPF over the other DPF methods on a wide range of simulated
tasks, including parameter learning and posterior approxima-
tion in linear Gaussian state-space models, image-based disk
localization, and robot localization in maze environments.
Experimental results show that the NF-DPF can achieve the
lowest tracking and localization errors in all considered ex-
periments, indicating that (conditional) normalizing flows can
indeed improve the performance of DPFs in various settings.
Interesting future research directions include the development
of differentiable resampling techniques with better statistical
properties.
REFERENCES
[1] A. Doucet, A. M. Johansen et al. , “A tutorial on particle filtering and
smoothing: Fifteen years later,” Handb. Nonlinear Filter. , vol. 12, no.
656-704, p. 3, 2009.
[2] N. Gordon, D. Salmond, and A. Smith, “Novel approach to
nonlinear/non-Gaussian Bayesian state estimation,” in IEE Proc. F
(Radar and Signal Process.) , vol. 140, 1993, pp. 107–113.
[3] P. M. Djuric, J. H. Kotecha, J. Zhang, Y . Huang, T. Ghirmai, M. F.
Bugallo, and J. Miguez, “Particle filtering,” IEEE Signal Process. Mag.,
vol. 20, no. 5, pp. 19–38, 2003.
[4] P. Del Moral and L. Miclo, “Branching and interacting particle systems.
approximations of Feynman-Kac formulae with applications to non-
linear filtering,” S´emin. Probab. Strasbourg, vol. 34, pp. 1–145, 2000.
[5] D. Crisan and A. Doucet, “A survey of convergence results on particle
filtering methods for practitioners,” IEEE Trans. Signal Process. (TSP) ,
vol. 50, no. 3, pp. 736–746, 2002.
[6] P. Del Moral, “Measure-valued processes and interacting particle sys-
tems. application to nonlinear filtering problems,” Ann. Appl. Probab. ,
vol. 8, no. 2, pp. 438–495, 1998.
[7] V . Elvira, J. M´ıguez, and P. M. Djuri´c, “Adapting the number of particles
in sequential Monte Carlo methods through an online scheme for
convergence assessment,” IEEE Trans. Signal Process. (TSP) , vol. 65,
no. 7, pp. 1781–1794, 2017.
[8] V . Elvira, J. Miguez, and P. M. Djuri ´c, “On the performance of particle
filters with adaptive number of particles,” Stat. Comput. , vol. 31, pp.
1–18, 2021.
[9] A. Giremus, J.-Y . Tourneret, and V . Calmettes, “A particle filtering
approach for joint detection/estimation of multipath effects on GPS
measurements,” IEEE Trans. Signal Process. (TSP) , vol. 55, no. 4, pp.
1275–1285, 2007.
[10] T. Zhang, C. Xu, and M.-H. Yang, “Multi-task correlation particle filter
for robust object tracking,” inProc. IEEE Conf. Comput. Vis. and Pattern
Recogn. (CVPR), Honolulu, Hawaii, July 2017.
[11] D. Creal, “A survey of sequential monte carlo methods for economics
and finance,” Econometric Rev., vol. 31, no. 3, pp. 245–296, 2012.
[12] X. Ma et al. , “Discriminative particle filter reinforcement learning for
complex partial observations,” in Proc. Int. Conf. Learn. Rep. (ICLR) ,
New Orleans, USA, May 2019.
[13] M. K. Pitt and N. Shephard, “Filtering via simulation: Auxiliary particle
filters,” J. Amer. Statist. Assoc. , vol. 94, no. 446, pp. 590–599, 1999.
[14] V . Elvira, L. Martino, M. F. Bugallo, and P. M. Djuri ´c, “Elucidating the
auxiliary particle filter via multiple importance sampling,” IEEE Signal
Process. Mag., vol. 36, no. 6, pp. 145–152, 2019.
[15] N. Branchini and V . Elvira, “Optimized auxiliary particle filters: adapting
mixture proposals via convex optimization,” in Proc. Conf. Uncertain.
Artif. Intell. (UAI) , 2021, pp. 1289–1299.
[16] A. Doucet, N. de Freitas, K. Murphy, and S. Russell, “Rao-Blackwellised
particle filtering for dynamic Bayesian networks,” in Proc. Conf. Un-
certain. Artif. Intell. (UAI) , Stanford, USA, 2000, pp. 176–183.

IEEE TRANSACTIONS ON SIGNAL PROCESSING 14
[17] N. De Freitas, “Rao-Blackwellised particle filtering for fault diagnosis,”
in Proc. IEEE Aerosp. Conf. , vol. 4, 2002, pp. 4–4.
[18] A. Doucet, N. De Freitas et al. , Sequential Monte Carlo methods in
practice. Springer, 2001, vol. 1, no. 2.
[19] S. Godsill, “Particle filtering: the first 25 years and beyond,” in Proc.
IEEE Int. Conf. Acoust. Speech Signal Process. (ICASSP) , Brighton,
UK, May 2019.
[20] N. Kantas, A. Doucet, S. S. Singh, J. Maciejowski, and N. Chopin, “On
particle methods for parameter estimation in state-space models,” Stat.
Sci., vol. 30, no. 3, pp. 328–351, 2015.
[21] N. Kantas, A. Doucet, S. S. Singh, and J. M. Maciejowski, “An overview
of sequential Monte Carlo methods for parameter estimation in general
state-space models,” IFAC Proc. Vol., vol. 42, no. 10, pp. 774–785, 2009.
[22] M. H ¨urzeler and H. R. K ¨unsch, “Approximating and maximising the
likelihood for a general state-space model,” Sequential Monte Carlo
methods in practice , pp. 159–175, 2001.
[23] E. L. Ionides, C. Bret ´o, and A. A. King, “Inference for nonlinear
dynamical systems,” Proc. Natl. Acad. Sci., vol. 103, no. 49, pp. 18 438–
18 443, 2006.
[24] S. Malik and M. K. Pitt, “Particle filters for continuous likelihood
evaluation and maximisation,” J. Econometrics, vol. 165, no. 2, pp. 190–
209, 2011.
[25] J. Olsson, O. Capp ´e, R. Douc, and ´E. Moulines, “Sequential Monte
Carlo smoothing with application to parameter estimation in nonlinear
state space models,” Bernoulli, vol. 14, no. 1, pp. 155–179, 2008.
[26] G. Poyiadjis, A. Doucet, and S. S. Singh, “Particle approximations of
the score and observed information matrix in state space models with
application to parameter estimation,” Biometrika, vol. 98, no. 1, pp. 65–
80, 2011.
[27] C. Andrieu, A. Doucet, and R. Holenstein, “Particle markov chain monte
carlo methods,” J. R. Stat. Soc. Ser. B. Stat. Methodol. , vol. 72, no. 3,
pp. 269–342, 2010.
[28] N. Chopin, P. E. Jacob, and O. Papaspiliopoulos, “SMC2: an efficient
algorithm for sequential analysis of state space models,” J. R. Stat. Soc.
Ser. B. Stat. Methodol. , vol. 75, no. 3, pp. 397–426, 2013.
[29] S. P ´erez-Vieites, I. P. Mari ˜no, and J. M ´ıguez, “Probabilistic scheme for
joint parameter estimation and state prediction in complex dynamical
systems,” Phys. Rev. E, vol. 98, no. 6, p. 063305, 2018.
[30] F. Lindsten, M. I. Jordan, and T. B. Schon, “Particle gibbs with ancestor
sampling,” J. Mach. Learn. Res. , vol. 15, pp. 2145–2184, 2014.
[31] X. Chen and Y . Li, “An overview of differentiable particle fil-
ters for data-adaptive sequential Bayesian inference,” arXiv preprint
arXiv:2302.09639, 2023.
[32] R. Jonschkowski, D. Rastogi, and O. Brock, “Differentiable particle
filters: end-to-end learning with algorithmic priors,” in Proc. Robot.:
Sci. and Syst. (RSS) , Pittsburgh, Pennsylvania, July 2018.
[33] P. Karkus, D. Hsu, and W. S. Lee, “Particle filter networks with
application to visual localization,” in Proc. Conf. Robot Learn. (CoRL) ,
Zurich, Switzerland, Oct 2018.
[34] A. Corenflos, J. Thornton, G. Deligiannidis, and A. Doucet, “Differ-
entiable particle filtering via entropy-regularized optimal transport,” in
Proc. Int. Conf. Mach. Learn. (ICML) , July 2021.
[35] A. ´Scibior and F. Wood, “Differentiable particle filtering without mod-
ifying the forward pass,” arXiv preprint arXiv:2106.10314 , 2021.
[36] A. Kloss, G. Martius, and J. Bohg, “How to train your differentiable
filter,” Auto. Robot., vol. 45, no. 4, pp. 561–578, 2021.
[37] M. Zhu, K. Murphy, and R. Jonschkowski, “Towards differentiable
resampling,” arXiv preprint arXiv:2004.11938 , 2020.
[38] T. A. Le, M. Igl, T. Rainforth, T. Jin, and F. Wood, “Auto-encoding
sequential Monte Carlo,” in Proc. Int. Conf. Learn. Rep. (ICLR) ,
Vancouver, Canada, Apr. 2018.
[39] C. Naesseth, S. Linderman, R. Ranganath, and D. Blei, “Variational
sequential Monte Carlo,” in Proc. Int. Conf. Artif. Intel. and Stat.
(AISTATS), Playa Blanca, Spain, Apr. 2018.
[40] C. J. Maddison et al. , “Filtering variational objectives,” in Proc. Adv.
Neur. Inf. Process. Sys. (NeurIPS) , Long Beach, USA, Dec. 2017.
[41] F. Gama, N. Zilberstein, M. Sevilla, R. G. Baraniuk, and S. Segarra,
“Unsupervised learning of sampling distributions for particle filters,”
IEEE Trans. Signal Process. (TSP) , 2023.
[42] G. Revach, N. Shlezinger, T. Locher, X. Ni, R. J. van Sloun, and
Y . C. Eldar, “Unsupervised learned Kalman filtering,” in Proc. Euro.
Sig. Process. Conf. (EUSIPCO) , Belgrade, Serbia, Aug. 2022.
[43] P. Bickel, B. Li, and T. Bengtsson, “Sharp failure rates for the bootstrap
particle filter in high dimensions,” Pushing the limits of contemporary
statistics: Contributions in honor of Jayanta K. Ghosh , 2008.
[44] G. Papamakarios, E. Nalisnick, D. J. Rezende, S. Mohamed, and
B. Lakshminarayanan, “Normalizing flows for probabilistic modeling
and inference,” J. Mach. Learn. Res. , vol. 22, pp. 1–64, 2021.
[45] X. Chen, H. Wen, and Y . Li, “Differentiable particle filters through
conditional normalizing flow,” in Proc. IEEE Int. Conf. Inf. Fusion
(FUSION), Sun City, South Africa, Nov. 2021.
[46] X. Chen and Y . Li, “Conditional measurement density estimation in
sequential Monte Carlo via normalizing flow,” in Proc. Euro. Sig.
Process. Conf. (EUSIPCO) , Belgrade, Serbia, Aug. 2022.
[47] E. L. IONIDES, A. BHADRA, Y . ATCHAD ´E, and A. KING, “Iterated
filtering,” Ann. of Statist. , vol. 39, no. 3, pp. 1776–1802, 2011.
[48] Z. Zhao, B. Huang, and F. Liu, “Parameter estimation in batch process
using EM algorithm with particle filter,” Comput. & Chem. Eng., vol. 57,
pp. 159–172, 2013.
[49] A. Wills, T. B. Sch ¨on, and B. Ninness, “Parameter estimation for
discrete-time nonlinear systems using EM,” IFAC Proc. Vol., vol. 41,
no. 2, pp. 4012–4017, 2008.
[50] C. Andrieu, A. Doucet, and V . B. Tadic, “On-line parameter estimation
in general state-space models,” in Proc. IEEE Conf. Dec. and Contr.
(CDC), Seville, Spain, Dec. 2005.
[51] F. LeGland and L. M ´evel, “Recursive estimation in hidden markov
models,” in Proc. IEEE Conf. Decis. Control (CDC) , vol. 4. IEEE,
1997, pp. 3468–3473.
[52] D. Crisan and J. M ´Iguez, “Nested particle filters for online parame-
ter estimation in discrete-time state-space Markov models,” Bernoulli,
vol. 24, no. 4A, pp. 3039–3086, 2018.
[53] S. P ´erez-Vieites and J. M ´ıguez, “Nested Gaussian filters for recursive
Bayesian inference and nonlinear tracking in state space models,” Signal
Proces., vol. 189, p. 108295, 2021.
[54] N. G. Polson, J. R. Stroud, and P. M ¨uller, “Practical filtering with
sequential parameter learning,” J. R. Stat. Soc. Ser. B. Stat. Methodol ,
vol. 70, no. 2, pp. 413–428, 2008.
[55] J. Fern ´andez-Villaverde and J. F. Rubio-Ram ´ırez, “Estimating macroe-
conomic models: A likelihood approach,” Rev. †Econ. Stud. , vol. 74,
no. 4, pp. 1059–1087, 2007.
[56] C. Rosato, L. Devlin, V . Beraud, P. Horridge, T. B. Sch ¨on, and
S. Maskell, “Efficient learning of the parameters of non-linear models
using differentiable resampling in particle filters,” IEEE Trans. Signal
Process. (TSP) (TSP) , vol. 70, pp. 3676–3692, 2022.
[57] X. Ma, P. Karkus, D. Hsu, and W. S. Lee, “Particle filter recurrent neural
networks,” in Proc. AAAI Conf. Artif. Intell. (AAAI) , New York, USA,
Feb. 2020.
[58] M. Cuturi, “Sinkhorn distances: Lightspeed computation of optimal
transport,” in Proc. Adv. Neur. Inf. Process. Sys. (NeurIPS), Lake Tahoe,
USA, Dec. 2013.
[59] J. Feydy et al., “Interpolating between optimal transport and mmd using
Sinkhorn divergences,” in Proc. Int. Conf. Artif. Intell. Stat. (AISTAS) ,
Naha, Japan, Apr. 2019.
[60] G. Peyr ´e and M. Cuturi, “Computational optimal transport,” Foundations
and Trends® in Machine Learning, vol. 11, no. 5-6, pp. 355–607, 2019.
[61] J. Lee et al. , “Set transformer: A framework for attention-based
permutation-invariant neural networks,” in Proc. Int. Conf. Mach. Learn.
(ICML), Baltimore, USA, June 2019.
[62] A. Vaswani et al. , “Attention is all you need,” in Proc. Adv. Neur. Inf.
Process. Sys. (NeurIPS) , Long Beach, USA, Dec. 2017.
[63] M. H. Dupty, Y . Dong, and W. S. Lee, “PF-GNN: Differentiable particle
filtering based approximation of universal graph representations,” in
Proc. Int. Conf. Learn. Rep. (ICLR) , May 2021.
[64] R. Chen, H. Yin, Y . Jiao, G. Dissanayake, Y . Wang, and R. Xiong, “Deep
samplable observation model for global localization and kidnapping,”
IEEE Robot. Autom. Lett. (RAL) , vol. 6, no. 2, pp. 2296–2303, 2021.
[65] A. Doucet, D. N. Freitas, and N. Gordon, “An introduction to sequential
Monte Carlo methods,” in Sequential Monte Carlo methods in practice .
Springer, 2001, pp. 3–14.
[66] R. E. Kalman, “A new approach to linear filtering and prediction
problems,” J .Basic Eng. , vol. 82, no. 1, pp. 33–45, 1960.
[67] R. Douc and O. Capp ´e, “Comparison of resampling schemes for particle
filtering,” in Proc. Int. Symp. Image and Signal Process. and Anal. ,
Zagreb, Croatia, 2005.
[68] T. Li, M. Bolic, and P. M. Djuric, “Resampling methods for particle
filtering: classification, implementation, and strategies,” IEEE Signal
Process. Mag., vol. 32, no. 3, pp. 70–86, 2015.
[69] I. Kobyzev, S. Prince, and M. Brubaker, “Normalizing flows: An
introduction and review of current methods,” IEEE Trans. Pattern Anal.
Mach. Intell. (TPAMI), vol. 43, no. 11, pp. 3964–3979, 2020.

IEEE TRANSACTIONS ON SIGNAL PROCESSING 15
[70] L. Dinh, J. Sohl-Dickstein, and S. Bengio, “Density estimation using
Real NVP,” in Proc. Int. Conf. Learn. Represent. (ICLR), Toulon, France,
Apr. 2017.
[71] M. Balunovic, A. Ruoss, and M. Vechev, “Fair normalizing flows,” in
Proc. Int. Conf. Learn. Represent. (ICLR) , Apr. 2022.
[72] D. P. Kingma and P. Dhariwal, “Glow: Generative flow with invertible
1x1 convolutions,” in Proc. Adv. Neur. Inf. Process. Sys. (NeurIPS) ,
Montreal, Canada, Dec. 2018.
[73] D. Rezende and S. Mohamed, “Variational inference with normalizing
flows,” in Proc. Int. Conf. Mach. Learn. (ICML) , Lille, France, July
2015.
[74] M. Karami, D. Schuurmans, J. Sohl-Dickstein, L. Dinh, and D. Duck-
worth, “Invertible convolutional flow,” in Proc. Adv. Neur. Inf. Process.
Sys. (NeurIPS), Vancouver, Canada, Dec. 2019.
[75] C. Huang, D. Krueger, A. Lacoste, and A. Courville, “Neural autore-
gressive flows,” in Proc. Int. Conf. Mach. Learn. (ICML) , Stockholm,
Sweden, Aug. 2018.
[76] C. Winkler, D. Worrall, E. Hoogeboom, and M. Welling, “Learn-
ing likelihoods with conditional normalizing flows,” arXiv preprint
arXiv:1912.00042, 2019.
[77] Y . Lu and B. Huang, “Structured output learning with conditional
generative flows,” in Proc. AAAI Conf. Artif. Intell. (AAAI) , New York,
USA, Feb. 2020.
[78] C. Villani, Optimal Transport: old and new. Berlin, Germany: Springer
Science & Business Media, 2008, vol. 338.
[79] N. Chopin and O. Papaspiliopoulos, An introduction to sequential Monte
Carlo. Springer, 2020.
[80] T. Haarnoja, A. Ajay, S. Levine, and P. Abbeel, “Backprop KF: Learning
discriminative deterministic state estimators,” in Proc. Adv. Neur. Inf.
Process. Sys. (NeurIPS) , Barcelona, Spain, Dec. 2016.
[81] C. Beattie, J. Z. Leibo, D. Teplyashin, T. Ward, M. Wainwright,
H. K¨uttler, A. Lefrancq, S. Green, V . Vald´es, A. Sadik et al., “Deepmind
lab,” arXiv preprint arXiv:1612.03801 , 2016.
[82] S. S. Rangapuram et al. , “Deep state space models for time series
forecasting,” Proc. Adv. Neur. Inf. Process. Sys. (NeurIPS), vol. 31, 2018.
[83] K. D. P. and B. J., “Adam: A method for stochastic optimization,” in
Proc. Int. Conf. on Learn. Represent. (ICLR) , San Diego, USA, May
2015.
[84] N. Carlevaris-Bianco, A. K. Ushani, and R. M. Eustice, “University of
michigan north campus long-term vision and lidar dataset,” Int. J. Robot.
Res., vol. 35, no. 9, pp. 1023–1035, 2016.
[85] G. Revach, N. Shlezinger, X. Ni, A. L. Escoriza, R. J. Van Sloun, and
Y . C. Eldar, “Kalmannet: Neural network aided kalman filtering for
partially known dynamics,” IEEE Transactions on Signal Processing ,
vol. 70, pp. 1532–1547, 2022.
[86] Y . Brenier, “Polar factorization and monotone rearrangement of vector-
valued functions,” Commun. Pure Applied Math. , vol. 44, no. 4, pp.
375–417, 1991.
[87] N. Fournier and A. Guillin, “On the rate of convergence in Wasserstein
distance of the empirical measure,” §Probab. Theory Related Fields, vol.
162, no. 3, pp. 707–738, 2015.
APPENDIX A
OPTIMAL TRANSPORT BACKGROUND
In this section, we provide a brief review of concepts
related to the proposed work, including the definition of
Wasserstein distances, the optimal transport plan (coupling),
and the optimal transport map. Note that notations introduced
in Section V also apply in this section.
Wasserstein Distance:
Let Pp(X ) be a set of Borel probability measures with
a finite p-th moment on a Polish metric space (X , d) [78].
Given two probability measures α ∈ Pp(X ), β ∈ Pp(X ′), the
Wasserstein distance of order p ∈ [1, +∞) between α and β
is defined as:
Wp(α, β) =

inf
P∈U (α,β)
Z
X ×X′
d(x, x′)pP(dx, dx′)
 1
p
,
(54)
where d(·, ·)p is the cost function, U (α, β) represents the set
of all transportation plans P(dx, dx′), i.e. joint distributions
whose marginals are α and β, respectively. Formally, the set
of all transportation plans between α and β is defined as:
U (α, β) :=
n
P ∈P (X × X′) : X#P = α, X ′#P = βo ,
(55)
where X#P and X ′#P respectively represent the projection of
a joint measure P ∈P (X ×X′) on X and X ′. Every transport
plan P(dx, dx′) corresponds to a transport map, also called
the barycentric projection map, which is defined as:
T(x) =
Z
x′P(dx′|x) , (56)
P(dx′|x) = P(dx, dx′)R
X ′ P(dx, dx′) . (57)
Optimal Transport Notations:
Solving the original optimal transport problem is compu-
tationally expensive and non-differentiable, an alternative is
to rely on entropy-regularized optimal transport [58], [60].
In the DPF setting, ϵ denotes the regularization coefficient
in the entropy-regularized optimal transport problem, P OTN,ϵ
denotes the regularized transport plan between α(t)N and β(t)N ,
T(·) : X → Xdenotes the optimal transport map between α(t)
and β(t), and TN,ϵ(·) : X → X, TN,ϵ(x) := R x′P OTN,ϵ (dx′|x)
the transport map induced by the transport plan P OTN,ϵ.
APPENDIX B
PROOF OF PROPOSITION V.1
We use notations below for the following proofs:
α(t) := p(xt|y0:t−1; θ) , β(t) := p(xt|y0:t; θ) , (58)
α(t)N (ψ) := 1N
NX
i=1
ψ(xit) , β(t)N (ψ) :=
NX
i=1
˜witψ(xit) , (59)
˜β(t)N (ψ) := 1N
NX
i=1
ψ(˜xit) , ω(t)(xt) = p(yt|xt; θ) , (60)

IEEE TRANSACTIONS ON SIGNAL PROCESSING 16
with α(0) := π(x0; θ), ψ(·) : X → R is a function
defined on X , α(t)N is an approximation of the predictive
distribution αt with N uniformly weighted particles, and β(t)N
is an approximation of the posterior distribution β(t) with
N particles weighted by ˜wit. ˜β(t)N is an approximation of the
posterior distribution β(t) with uniformly weighted particles ˜xit
obtained by applying the entropy-regularized optimal transport
resampler in [34] as shown in the line 12 of Algorithm 1. For
a measure α defined on X we use α(ψ) =
R
X ψ(x)α(dx) to
denote the expectation of ψ(·) w.r.t. α.
To prove Proposition V .1, we introduce the following As-
sumptions V .1-V .4:
Assumption V .1.X is a compact subset of RdX with diameter
d := sup
x,x′∈X
||x − x′||2, where || · ||2 denotes the Euclidean
distance.
Assumption V .1 requires that the domain where the la-
tent state xt is defined on is a compact subset of the dX -
dimensional Euclidean space RdX . In particular, a subset of
Euclidean space is called compact if it is closed and bounded.
For a compact subset of RdX , we can always find a diameter
d such that for all x and x′ in X , we have ||x, x′||2 ≤ d. A
simple example of X that satisfies this assumption is a RdX -
dimensional hypersphere: X := {x ∈ RdX : ||x||2 ≤ d/2}
Assumption V .2. For ∀t ≥ 0, there exists a unique optimal
transport plan between α(t) and β(t) featured by a determin-
istic transport map Tt(·) : X → X, and the transport map
Tt(·) is λ-Lipschitz for ∀t ≥ 0 with λ >0.
It was proved in [86] that on Euclidean space with Euclidean
distance as the transportation cost function, there is always a
unique optimal transportation map if µ and ρ are absolutely
continuous with respect to the Lebesgue measure. Therefore,
the first part of Assumption V .2 is satisfied as long as the
predictive distribution α(t) and the posterior distribution β(t)
are continuous. A transport map Tt(·) is said to be λ-Lipschitz
if ||Tt(·)(x), Tt(·)(x′)||2 ≤ λ||x, x′||2 for all x, x′ in X , so
the second part of Assumption V .2 requires that the transport
map Tt(·) does not change discretely and the gradient of Tt(·)
is bounded. A simple example that satisfies Assumption V .2
is the identity transport map Tt(x) = x.
Assumption V .3. Denote by f (·) the transition kernel
p(xt|xt−1; θ) of NF-DPFs defined in Eq. (17) and ψ(·) : X →
R the considered bounded k-Lipschitz function, there exists an
η ∈ R such that for any two probability measures µ, ρon X
|µf (ψ) − ρf (ψ)| ≤η|µ(ψ) − ρ(ψ)| , s.t. µ(ψ) ̸= ρ(ψ) .
Intuitively, this assumption requires the transition kernel
f (·) not to change the measures µ and ρ too much so that
the absolute difference between the expectation of ψ(·) w.r.t.
µf and ρf is smaller than η times the absolute difference
between the expectation of ψ(·) w.r.t. µ and ρ.
Assumption V .4. There exists a constant ζ ∈ R such that for
any continuous probability measure µ on X and its empirical
approximation µN , for weighted probability measures µωt =
ωtµ/µ(ωt) and µN,ωt = ωµN /µN (ωt), we have
W2(µN,ωt , µωt ) ≤ ζW2(µN , µ) ,
where ωt(·) : X → R is defined in Eq. (38), and W2(·, ·)
refers to the 2-Wasserstein distance [60], [78].
A sufficient condition for Assumption V .4 to hold is that
for a finite N, there is a lower bound B(N ) > 0 on
W2(µN , µ): W2(µN , µ) ≥ B(N ). Specifically, with the lower
bound B(N ), we can choose a constant ζ ≥ N dB(N ) such that
W2(µN,ωt , µωt ) ≤ ζW2(µN , µ) holds for any function ωt(·):
W2(µN,ωt , µωt ) ≤ N d ≤ N dB(N ) B(N ) ≤ ζW2(µN , µ) .
We first present five Lemmas B.1, B.2, B.3, B.4, B.5 and
Proposition B.1. Lemma B.3 is borrowed from [34] (Lemma
C.2). The proof of Proposition V .1 is based on proof by
induction, which is inspired by the proof of Proposition 11.3
of [79].
Lemma B.1. For all bounded k-Lipschitz function ψ(·) : X →
R and any two probability measures µ, ρon X , we have:
|µ(ψ) − ρ(ψ)| ≤kW1(µ, ρ) . (61)
Proof. Denote by
P ∗(dx, dx′) := argmin
P∈U (µ,ρ)
Z
X 2
||x − x′||2 P(dx, dx′)
the optimal transport plan between µ and ρ w.r.t. the Euclidean
distance, we have:
|µ(ψ) − ρ(ψ)| (62)
=
Z
X
ψ(x)µ(dx) −
Z
X
ψ(x′)ρ(dx′)

=
Z
X 2
ψ(x)P ∗(dx, dx′) −
Z
X 2
ψ(x′)P ∗(dx, dx′)

≤
Z
X 2
|ψ(x) − ψ(x′)| P∗(dx, dx′)
≤
Z
X 2
k||x − x′||2P ∗(dx, dx′)
=kW1(µ, ρ) . (63)
Lemma B.2. For probability measures µ and ρ defined on
X , denote by T(·) : X → Xthe optimal transport map
between them. Let µN = PNi=1 aiδx′i and ρN = PMj=1 bjδxj
be approximations of µ and ρ, where x′i ∈ Xand x′j ∈ Xfor
∀i, j∈ {1, · · ·, N}. Denote by PN (dx′, dx) ∈ U(µN , ρN ) a
transport plan between µN and ρN , and TN (·) : X → Xthe
transport map induced by PN (dx′, dx), namely TN (x′i) =
1
ai
PM
j=1 pi,jxj with pi,j = PN,i,j the element at the in-
tersection of PN ’s i-th row and j-th column. The following
inequality holds:
Z
X 2
||T(x) − TN (x)||2PN (dx′, dx)
≤
Z
X 2
||T(x′) − x||2PN (dx′, dx) (64)

IEEE TRANSACTIONS ON SIGNAL PROCESSING 17
Proof. Firstly, denote by ⟨·, ·⟩ the inner product operation, we
have that:
NX
i=1
MX
j=1
pi,j
D
T(x′i), xj
E
=
NX
i=1
ai
D
T(x′i), TN (x′i)E
=
NX
i=1
MX
j=1
pi,j
D
T(x′i), TN (x′i)E ,
(65)
NX
i=1
MX
j=1
pi,j
D
TN (x′i), xj
E
=
NX
i=1
ai
D
TN (x′i), TN (x′i)E
=
NX
i=1
MX
j=1
pi,j
D
TN (x′i), TN (x′i)E .
(66)
The above equation leads to:
NX
i=1
MX
j=1
pi,j||T(x′i) − xj||2 (67)
=
NX
i=1
MX
j=1
pi,j
D 
T(x′i) − xj,  T(x′i) − xjE (68)
=
NX
i=1
MX
j=1
pi,j
D
T(x′i), T(x′i)E + DTN (x′i), TN (x′i)E (69)
− 2
D
T(x′i), TN (x′i)E + DTN (x′i), TN (x′i)E
+
D
xj, xj
E
− 2
D
TN (x′i), xj
E
(70)
=
NX
i=1
MX
j=1
pi,j

||T(x′i) − TN (x′i)||2 + ||TN (x′i) − xj||2

(71)
≥
NX
i=1
MX
j=1
pi,j

||T(x′i) − TN (x′i)||2

. (72)
Therefore the stated result is obtained:
Z
X 2
||T(x′) − TN (x′)||2PN (dx′, dx) (73)
=
NX
i=1
MX
j=1
pi,j||T(x′i) − TN (x′i)||2 (74)
≤
NX
i=1
MX
j=1
pi,j||T(x′i) − xj||2 (75)
=
Z
X 2
||T(x′) − x||2PN (dx′, dx) . (76)
Lemma B.3. (Lemma C.2 in [34]) Let X ⊂Rd be compact
with diameter d > 0. Suppose we are given two probability
measures α, βon X with a unique deterministic, λ-Lipschitz
optimal transport map T while αN = PNi=1 aiδx′i with ai > 0
and βN = PNi=1 biδxi. We write P OT,N , resp. P OT,Nϵ , for an
optimal coupling between αN and βN , resp. the ϵ-regularized
optimal transport plan, between αN and βN . Then
Z
||x − T(x′)||2P OTN,ϵ (dx′, dx)
 1
2
≤ 2λ1/2E 1/2 [d + E]1/2
+ max{λ, 1} [W2(αN , α) + W2(βN , β)] ,
where
E := E(N, ϵ, α, β) := W2(αN , α)+W2(βN , β)+
p
2ϵ log(N ).
Proposition B.1. Consider atomic probability measures αN =PN
i=1 aiδx′i with ai > 0 and βN = PNi=1 biδxi, with support
X ⊂Rd. Denote by P OTN,ϵ,i,j the element at the intersection
of i-th row and j-th column of the ϵ-regularized optimal
transport coupling P OTN,ϵ between αN and βN , and define
˜βN = PNi=1 aiδ˜xi,N,ϵ, where ˜xi,N,ϵ = 1ai PNj=1 P OTN,ϵ,i,j xj. Letα, βbe two other probability measures, also supported on X ,
such that there exists a unique λ-Lipschitz optimal transport
map T(·) : X → Xbetween them. Then for any bounded
k-Lipschitz function ψ(·) : X →R, we have
βN (ψ) − ˜βN (ψ) ≤√2k2λ1/2E 1/2 [d + E]1/2
+ max{λ, 1} [W2(αN , α) + W2(βN , β)]

,
(77)
where d := sup
x,x′∈X
||x − x′||2 and E = W2(αN , α) +
W2(βN , β) + √2ϵ log N.
Proof. By definition, we have ˜βN (d˜x) =R
αN (dx′)δTN,ϵ (x′)(d˜x) with TN,ϵ(x′) := R xP OTN,ϵ (dx|x′)
while, as P OTN,ϵ belongs to U (αN , βN ), we also have
βN (dx) =
R
αN (dx′)P OTN,ϵ (dx|x′). We then have for any
1-Lipschitz function
βN (ψ) − ˜βN (ψ)
=
Z Z (ψ(x) − ψ(TN,ϵ(x′)))P OTN,ϵ (dx|x′) αN (dx′)
≤
Z Z
|ψ(x) − ψ(TN,ϵ(x′))| αN (dx′)P OTN,ϵ (dx|x′)
≤k
Z Z
||x − TN,ϵ(x′)||P OTN,ϵ (dx′, dx)
≤k
Z Z
||x − TN,ϵ(x′)||2P OTN,ϵ (dx′, dx)
 1
2
≤k
Z Z
||x − T(x′)||2 + ||T(x′) − TN,ϵ(x′)||2

P OTN,ϵ (dx′, dx)
 1
2
≤
√
2k
Z Z
||x − T(x′)||2P OTN,ϵ (dx′, dx)
 1
2
,
where the final inequality follows from Lemma B.2. The stated
result is then obtained using Lemma B.3.
Lemma B.4. For all bounded k-Lipschitz function ψ(·) :
X → R, when the entropy-regularization hyperparameter
ϵN = o(1/ log N ), for α(t)N , β(t−1)N defined as in Eq. (59), and

IEEE TRANSACTIONS ON SIGNAL PROCESSING 18
transition kernel f (·) defined by p(xt|xt−1; θ) in Eq. (17), the
expectations α(t)N (ψ) and β(t−1)N f (ψ) satisfy:
E

α(t)N (ψ) − β(t−1)N f (ψ)
2
≤ C||ψ||2∞ , (78)
where
C :=C(λ, k, η, ζ, τ, N, p, q, dX ) (79)
=4k
√
Q + 4
√
2kη

2
q
3λ(1 + ζ)τ
√
Q (80)
+ max{λ, 1}(1 + ζ)
√
Q

, (81)
is a constant depending on λ, k, η, ζ, τ, N, p, q, dX . The
function Q is defined as Q := Q(τ, N, p, dX , q) :=
C1τ pH(N, p, dX , q), C1 is a constant depending only on p,
dX , q, and H(N, p, dX , q) is defined as
H(N, p, dX , q)
=



N −1/2 + N −(q−p)/q if p > dX /2
and q ̸= 2p ,
N −1/2 log(1 + N ) + N −(q−p)/q if p = dX /2
and q ̸= 2p ,
N −p/dX + N −(q−p)/q if p ∈ (0, dX /2)
and q ̸= dX /(dX − p) ,
(82)
where q > pis a constant satisfying
R
X |x|qα′(t)N (dx) < ∞
and
R
X |x|qα′(t−1)N (dx) < ∞, p = 2 is the order of Wasser-
stein distances as detailed in the proof, and τ = d||ψ||∞ . Be-
sides, for large enough N and dX such that Q ≤√Q ≤4√Q
and H(N, p, dX , q) = N −p/dX + N −(q−p)/q ≤ 2N −p/dX , we
also have that:
E

α(t)N (ψ) − β(t−1)N f (ψ)
2
≤
˜C||ψ||2∞
N 1/2dX
, (83)
where
˜C := ˜C(λ, k, η,d, τ, N, p, q, dX ) (84)
:=4k
4
p
2C1d2

1 +
√
2η

2
p
3λ(1 + ζ)τ (85)
+ max{λ, 1}(1 + ζ)

(86)
is a constant.
Proof. We first decompose α(t)N (ψ) − β(t−1)N f (ψ) into two
terms:
α(t)N (ψ) − β(t−1)N f (ψ) (87)
=

α(t)N (ψ) − α′(t)N (ψ)

+

α′(t)N (ψ) − β(t−1)N f (ψ)

, (88)
where α′(t)N is defined as α′(t)N := ˜β(t−1)N f. The first term
in Eq. (87) can be bounded by applying Lemma B.1 to
probability measures α(t)N (ψ) and α′(t)N (ψ):α(t)N (ψ) − α′(t)N (ψ) ≤ kW1(α(t)N , α′(t)N ) ≤ kW2(α(t)N , α′(t)N ) .
(89)
We denote by Mq(ρ) the q-th moment
R
X |x|qρ(dx) of a
probability measure ρ defined on X , and assume that X
contains the origin 0dx, otherwise we can add a constant to
the diameter d, such that
|x|q ≤ dq =

τ ||ψ||∞
q
, (90)
where τ = d||ψ||∞ . Assume Mq(α′(t)N ) < ∞ for some q > p=
2, following Theorem 1 of [87] and notice that
α(t)N (ψ) −
α′(t)N (ψ) ≤ 2||ψ||∞, we have that for all N ≥ 1:
E
α(t)N (ψ) − α′(t)N (ψ)2 (91)
≤2k||ψ||∞E

W2(α(t)N , α′(t)N )

(92)
≤2k||ψ||∞
q
C1M p/qq (α′(t)N )H(N, p, dX , q) (93)
≤2k||ψ||∞
q
C1τ p||ψ||p∞H(N, p, dX , q) (94)
≤2k
√
Q||ψ||2∞ (95)
≤C1||ψ||2∞ (96)
where C1 := C1(k, τ, N, p, dX , q) := 2 k
p
Q(τ, N, p, dX , q),
p is the order of the Wasserstein distance ( p = 2 in this
case), C1 is a constant depending only on p, d, q, Q :=
Q(τ, N, p, dX , q) := C1τ pH(N, p, dX , q), and H(N, p, dX , q)
is defined as
H(N, p, dX , q)
=



N −1/2 + N −(q−p)/q if p > dX /2
and q ̸= 2p ,
N −1/2 log(1 + N ) + N −(q−p)/q if p = dX /2
and q ̸= 2p ,
N −p/dX + N −(q−p)/q if p ∈ (0, dX /2)
and q ̸= dX /(dX − p) ,
(97)
For the second term in Eq. (87), by Assumption V .3, V .4 and
Proposition B.1:
α′(t)N (ψ) − β(t−1)N f (ψ) (98)
≤η
 ˜β(t−1)N,ϵ (ψ) − β(t−1)N (ψ) (99)
≤
√
2ηk
 
2λ1/2E 1/2 [d + E]1/2
+ max{λ, 1}

W2

α(t−1)N , α′(t−1)N

+ W2

β(t−1)N , ωα′(t−1)N
α′(t−1)N (ω)
!
(100)
≤
√
2ηk
 
2λ1/2E 1/2 [d + E]1/2
+ max{λ, 1}

(1 + ζ)W2

α(t−1)N , α′(t−1)N
 !
, (101)

IEEE TRANSACTIONS ON SIGNAL PROCESSING 19
where λ is the Lipschitz constant of the optimal transport
map T(·) : X → X between α′(t−1)N and ωα′ (t−1)Nα′(t−1)N (ω),
and E := W2

α(t−1)N , α′(t−1)N

+ W2

β(t−1)N , ωα′ (t−1)Nα′ (t−1)N (ω)  +p
2ϵ log(N ). Again following Theorem 1 of [87], assume
Mq(α′(t−1)N ) < ∞ for q > p= 2, we have that for all N ≥ 1:
E[E] (102)
:=E
h
W2

α(t−1)N , α′(t−1)N

+ W2

β(t−1)N , ωα′(t−1)N
α′(t−1)N (ω)

+
p
2ϵ log(N )
i
(103)
≤E
h
(1 + ζ)W2

α(t−1)N , α′(t−1)N

+
p
2ϵ log(N )
i
(104)
≤(1 + ζ)E
"
W2

α(t−1)N , α′(t−1)N
#
+ E
hp
2ϵ log(N )
i
(105)
≤(1 + ζ)||ψ||∞
p
C1τ pH(N, p, dX , q) + E
hp
2ϵ log(N )
i
,
(106)
and
E[E 2] ≤ EhE 2d + p2ϵ log(N )i (107)
= 2dE[E] + E
h
E
 p
2ϵ log(N )
i
(108)
≤ 2dE[E] + E
h
2d
p
2ϵ log(N ) + 2ϵ log(N )
i
(109)
Let ϵN = o(1/ log N ) such that E
hp
2ϵ log(N )
i
= 0 and
E
h
2ϵ log(N )
i
= 0, we now have:
E[E] ≤ (1 + ζ)||ψ||∞
√
Q , (110)
E[E 2] ≤ 2d(1 + ζ)||ψ||∞√Q . (111)
Therefore we have that:
E
hα′(t)N (ψ) − β(t−1)N f (ψ)i (112)
≤E
"
√
2ηk
 
2λ1/2E 1/2 [d + E]1/2
+ max{λ, 1}

(1 + ζ)W2

α(t−1)N , α′(t−1)N
 !#
(113)
≤
√
2ηkE
h
2λ1/2  dE + E 21/2
+ max{λ, 1}(1 + ζ)||ψ||∞
p
C1τ pH(N, p, dX , q)
i
(114)
≤
√
2ηk
 
2λ1/2
r
E
h
dE + E 2
i
+ max{λ, 1}(1 + ζ)||ψ||∞
p
C1τ pH(N, p, dX , q)
!
(115)
≤
√
2ηk||ψ||∞

2
q
3λ(1 + ζ)τ
√
Q
+ max{λ, 1}(1 + ζ)
√
Q

(116)
In addition, notice that
α′(t)N (ψ) − β(t−1)N f (ψ) ≤ 2||ψ||∞,
therefore,
E
hα′(t)N (ψ) − β(t−1)N f (ψ)2i (117)
≤2||ψ||∞E
hα′(t)N (ψ) − β(t−1)N f (ψ)i (118)
≤2
√
2kη

2
q
3λ(1 + ζ)τ
√
Q + max{λ, 1}(1 + ζ)
√
Q

||ψ||2∞
(119)
=C2||ψ||2∞ , (120)
where C2 := C2(λ, k, η, ζ, τ, N, p, q, dX ) :=
2
√
2kη

2
q
3λ(1 + ζ)τ √Q + max{λ, 1}(1 + ζ)√Q.
From Eq. (96) and Eq. (120), we have that
E

α(t)N (ψ) − β(t−1)N f (ψ)
2
(121)
≤E

α(t)N (ψ) − α′(t)N (ψ)
2
+

α′(t)N (ψ) − β(t−1)N f (ψ)
2
(122)
≤2C1||ψ||∞ + 2C2||ψ||∞ (123)
≤C||ψ||2∞ , (124)
where C := C(λ, k, η, ζ, τ, N, p, q, dX ) = 4 k√Q +
4
√
2kη

2
q
3λ(1 + ζ)τ √Q + max{λ, 1}(1 + ζ)√Q. Be-
sides, for large enough N and dX such that Q ≤√Q ≤4√Q
and H(N, p, dX , q) = N −p/dX +N −(q−p)/q ≤ 2N −p/dX with
p = 2, we also have that:
E

α(t)N (ψ) − β(t−1)N f (ψ)
2
(125)
≤||ψ||2∞
"
4k
√
Q + 4
√
2kη

2
q
3λ(1 + ζ)τ
√
Q (126)
+ max{λ, 1}(1 + ζ)
√
Q
#
(127)
≤||ψ||2∞
"
4k
4√Q + 4√2kη 4√Q2p3λ(1 + ζ)τ (128)
+ max{λ, 1}(1 + ζ)
#
(129)
≤
˜C||ψ||2∞
N 1/2dX
, (130)
where ˜C := ˜C(λ, k, η,d, τ, N, p, q, dX ) := 4 k 4√2C1d2

1 +
√
2η

2
p
3λ(1 + ζ)τ + max{λ, 1}(1 + ζ)

.
Lemma B.5. Provided the weight function ω(·) : X → R
is upper bounded, for all measurable and bounded function
ψ(·) : X →R,
E
hβ(t)N (ψ) − β′(t)N (ψ)2i ≤ ||ψ||2∞Eh(α(t)N (¯ω) − 1)2i ,
(131)

IEEE TRANSACTIONS ON SIGNAL PROCESSING 20
where ¯ω(·) : X →R is defined as ¯ω(x) = ω(x)α(t)(ω), and β′(t)N =
ωα(t)N
α(t)(ω).
Proof. Notice that
β(t)N (ψ) = β′(t)N (ψ)α(t)N (¯ω) ,
therefore, we have that
β(t)N (ψ) − β′(t)N (ψ) = β(t)N (ψ)1 − α(t)N (¯ω) (132)
≤ ||ψ||∞

1 − α(t)N (¯ω) . (133)
So, we can conclude that
E
hβ(t)N (ψ) − β′(t)N (ψ)2i ≤ ||ψ||2∞Eh(α(t)N (¯ω) − 1)2i .
(134)
Proposition V .1. For a bounded weight function ωt(xt) =
p(yt|xt; θ) : X →R and a measurable bounded k-Lipschitz
function ψ(·) : X →R, when the regularization coefficient
in entropy-regularized optimal transport resampler ϵN =
o(1/ log N ), there exist constants ct and c′t such that for t ≥ 0
E
"
α(t)N (ψ) − β(t−1)f (ψ)
2#
≤ ct
||ψ||2∞
N 1/2dX
(135)
(replacing β(t−1)f by the initial distribution π(x0, θ) at time
t = 0 defined in Eq. (1)) and
E
"
β(t)N (ψ) − β(t)(ψ)
2#
≤ c′t ||ψ||2∞N 1/2dX , (136)
where β(t) and α(t)N are respectively defined by Eqs. (58)
and (59), and f (·) is a transition kernel defined by
p(xt|xt−1; θ) in Eq. (17).
Proof. We prove the above statement by induction. Firstly,
Eq. (135) holds at time t = 0 with c1 = 4:
Exi0i.i.d∼ π
" 1
N
NX
i=1
ψ(xi0) − π(ψ)
2#
(137)
=Var
 
1
N
NX
i=1
ψ(xi0)
!
(138)
= 1N Varψ(x) (139)
= 1N EX∼µ

ψ(x) − µ(ψ)
2
(140)
≤ 1N  2||ψ||∞2 (141)
≤ 4||ψ||2∞
N 1/2dX
. (142)
Assume Eq. (135) holds at time t ≥ 0, we have:
β(t)N (ψ) − β(t)(ψ) (143)
=

β(t)N (ψ) − β′(t)N (ψ) + β′(t)N (ψ) − β(t)(ψ) .
The MSE of the second term in the r.h.s of Eq. (143) can
be bounded by applying Eq. (135) to function ¯ωψ. The MSE
of the first term in the r.h.s of Eq. (143) can be bounded by
applying Lemma B.5, then Eq. (135) to function ¯ω (using the
fact that β(t−1)f (¯ω) = 1). Therefore
E
"
β(t)N (ψ) − β(t)(ψ)
2#
(144)
≤2E
"
β(t)N (ψ) − β′(t)N (ψ)
2#
+ 2E
"
β′(t)N (ψ) − β(t)(ψ)
2#
(145)
≤4ct
||ψ||2∞||¯ω||2∞
N 1/2dX
, (146)
where we can obtain Eq. (136) with c′t = 4ct ||¯ω||2∞N 1/2dX .We then prove that Eq. (136) at time t−1 implies Eq. (135)
at time t. Firstly, we have that
α(t)N (ψ) − β(t−1)f (ψ) (147)
=

α(t)N (ψ) − β(t−1)N f (ψ) + β(t−1)N f (ψ) − β(t−1)f (ψ) .
(148)
The MSE of the first term in the r.h.s of Eq. (147) can be
bounded by applying Lemma B.4, and the MSE of the second
term in the r.h.s of Eq. (147) can by bounded by applying
Eq. (136) (at time t − 1, replacing ψ by f ψ), therefore we
have that Eq. (135) holds:
E
"
α(t)N (ψ) − β(t−1)f (ψ)
2#
(149)
≤2E
"
α(t)N (ψ) − β(t−1)N f (ψ)2
#
(150)
+ 2E
"
β(t−1)N f (ψ) − β(t−1)f (ψ)2
#
(151)
≤2
  ˜C + c′t ||ψ||2∞N 1/2dX  . (152)
So, Eq. (136) at time t − 1 leads to Eq. (135) at time step t
with ct = 2
  ˜C + c′t, where ˜C is defined by Eq. (84).
To summarize, we have Eq. (135) to hold at time 0, and
Eq. (135) at time step t implies Eq. (136) to hold at time step
t. Then Eq. (136) at time step t lead to Eq. (135) at time step
t + 1, therefore we can conclude that Eq. (135) and Eq. (136)
hold for ∀t ≥ 0.
APPENDIX C
DETAILED EXPERIMENT SETUPS
A. One-dimensional Linear Gaussian State-space Models
In this experiment, we use conditional planar flow for
the construction of proposal distributions in NF-DPFs [73].
Normalizing flows are not used to construct the dynamic
model and the measurement model in this experiment because
the functional form of them are assumed to be known and
we aim to approximate their parameters, following the setup
in [38]–[40].

IEEE TRANSACTIONS ON SIGNAL PROCESSING 21
At time step t + 1, given a particle xit, the following
equations shows how new particles xit+1 are generated from
the proposal distribution of NF-DPFs in this experiment:
ˆxit+1 ∼ N(θ1xt, 1) for t ≥ 1 , , (153)
xit+1 = Fϕ(ˆxit+1; yt+1) ∼ q(xt+1|xt, yt+1; ϕ) . (154)
where Fϕ(ˆxit+1; yt+1) is a planar flow that is defined as:
Fϕ(ˆxit+1; yt+1) = ˆxit+1 + vh(wˆxit+1 + byt+1) , (155)
where v ∈ R, w ∈ R, and b ∈ R are learnable parameters, we
use a tanh function as the smooth non-linear function h(·) :
R → R.
We employed the Adam optimizer to update the parameters,
with a fixed learning rate of 0.002 and optimize the model for
500 iterations. We set number of particles as N = 100 for
both training, validation, and testing stages. The particles are
resampled when effective sample size is smaller than 50.
B. Multivariate Linear Gaussian State-space Models
We use conditional Real-NVP models to construct the
proposal distributions of NF-DPFs in this experiment [76].
Following the setup in [34], as the functional forms of the
dynamic model and the measurement model are given and
the we aim to learn their parameters, normalizing flows
are not employed to construct the dynamic model and the
measurement model.
In this experiment, the conditional normalizing flow
Fϕ(·; ·) : RdX +dY → RdX used in the construction of NF-
DPF’s proposal distributions is defined as a composition of
K conditional normalizing flows Fϕk (·; ·) : RdX +dY → RdX .
Denote by z ∈ RdX , u ∈ RdY the input and s ∈ RdX the
output of Fϕk (·; ·), a single component of Fϕ(·; ·) can be
formulated as:
s′
1:d
= z
1:d
, (156)
s′
d+1:dX
= z
d+1:dX
⊙ e
˜γ′ ϕk ( z1:d,u) + ˜η′ϕk ( z1:d, u) , (157)
s
1:d
= s′
1:d
⊙ e
˜γϕk ( s′d+1:dX ,u) + ˜ηϕk ( s′d+1:dX , u) , (158)
s
d+1:dX
= s′
d+1:dX
, (159)
where dX ∈ {2, 5, 10, 25, 50, 100} is the dimension of
xit, d = ⌊dX /2⌋, ˜γϕk (·) : Rd+dY → RdX −d, ˜ηϕk (·) :
Rd+dY → RdX −d, ˜γ′ϕk (·) : RdX +dY −d → Rd, and˜η′ϕk (·) : RdX +dY −d → Rd are constructed with two-layer
fully-connected neural networks using tanh as their activation
functions. Given a particle xit at time step t, new particles
xit+1 at time step t + 1 are generated by:
ˆxit+1 ∼ N(θ1xit, IdX ) , (160)
xit+1 = Fϕ(ˆxit+1; yt+1) (161)
= FϕK (· · · Fϕ2 (Fϕ1 (ˆxit+1; yt+1); yt+1) · · ·; yt+1) . (162)
Specifically in this experiment, we set K = 1.
We employed the Adam optimizer to update the parameters,
with a fixed learning rate of 0.002 and optimize the model for
500 iterations. We set number of particles as N = 100 for
both training, validation, and testing stages. The particles are
resampled when effective sample size is smaller than 50.
C. Disk Localization
With a slight abuse of notations, in this experiment, we
denote by xt the location of the target disk at the t-th time step,
and at the action. The velocity and the location of the target
disk at the t-th time step can be described as follows [36]:
ˆat = at + ˆςt, ˆςt
i.i.d
∼ N(0, σ 2ˆς I) , (163)
xt+1 = xt + ˆat + ςt, ς t
i.i.d
∼ N(0, σ 2ς I) , (164)
where I is the identity matrix, ˆat is the noisy action obtained
by adding random action noise ˆςt, σˆς = 4 is the standard
deviation of the action noise, and ςt is the dynamic noise
whose standard deviation is σς = 2 . The distractors follow
the same dynamic presented above.
In this experiment, we assume that the action at is given,
but neither the transition of latent state nor the relation
between observations and latent state are known. Therefore,
the dynamic model, the measurement model, and the proposal
distribution of the proposed NF-DPF are constructed with
normalizing flows. Specifically, given a particle xit at time step
t, the dynamic model is constructed with a base distribution
g(·|xit; θ) and a normalizing flow Tθ(·) : RdX → RdX , and
one can draw samples from the dynamic model for time step
t + 1 as below:
˙xit+1 = xit + at + εit ∼ g( ˙xt+1|xt; θ) , (165)
xit+1 = Tθ( ˙xit+1) ∼ p(xt+1|xt; θ) . (166)
The normalizing flow Tθ(·) is defined as a composition of K
conditional normalizing flows Tθk (·) : RdX → RdX . Denote
by z ∈ RdX the input and s ∈ RdX the output of Tθk (·), a
single component of Tθ(·) can be formulated as:
s′
1:d
= z
1:d
, (167)
s′
d+1:dX
= z
d+1:dX
⊙ e
˜γ′ θk ( z1:d) + ˜η′θk ( z1:d) , (168)
s
1:d
= s′
1:d
⊙ e
˜γθk ( s′d+1:dX ) + ˜ηθk ( s′d+1:dX ) , (169)
s
d+1:dX
= s′
d+1:dX
, (170)
where dX is the dimension of xit, d = ⌊dX /2⌋, ˜γθk (·) :
Rd+dY → RdX −d, ˜ηθk (·) : Rd+dY → RdX −d, ˜γ′θk (·) :
RdX +dY −d → Rd, and ˜η′θk (·) : RdX +dY −d → Rd are
constructed with two-layer fully-connected neural networks
using tanh as their activation functions. Given a particle xit
at time step t, new particles xit+1 at time step t are generated
by applying Tθ(·) to ˙xit+1:
xit+1 = Tθ( ˙xit+1) = TθK (· · · Tθ2 (Tθ1 ( ˙xit+1) · · ·) . (171)
Specifically in this experiment, we set K = 2 and use Real-
NVP models to construct Tθ(·).

IEEE TRANSACTIONS ON SIGNAL PROCESSING 22
For this experiment, the proposed NF-DPF approximates
the conditional likelihood p(yt|xt; θ) of an observation yt
conditioned on a latent state xt as follows:
et = Uθ(yt) , (172)
zt = G−1θ (et; xt) , (173)
p(yt|xt; θ) ≈ p(et|xt; θ) (174)
= pZ(zt)
 det JGθ (zt; xt)−1 , (175)
where Uθ(·) : RY → Rde is the encoder function constructed
with convolutional neural networks with that transforms 128×
128 RGB images to 32-dimensional feature vectors, G−1θ (·) :
Rde × X:→ Rde is a conditional normalizing flow built by
stacking two conditional Real-NVP models [76], and pZ(·) is
the PDF of a standard Gaussian distribution.
Similar to the way we constructed the proposal distribution
of NF-DPFs in the multivariate Gaussian experiment we
presented in Appendix C-B, the proposal distribution of NF-
DPF in this experiment is constructed with a conditional
normalizing flow, the conditional Real-NVP model [76], while
we set the number of flows K = 2 for this experiment to
build a more expressive proposal distribution, as the dimension
of observations in this experiment is higher than that of the
multivariate Gaussian experiment. Given a particle xit at time
step t, new particles xit+1 from the proposal distribution at
time step t + 1 are generated by:
ˆxit+1 = xit + at + εit ∼ g(ˆxt+1|xt; θ) (176)
xit+1 = Fϕ(ˆxit+1; yt+1) (177)
= FϕK (· · · Fϕ2 (Fϕ1 (ˆxit+1; yt+1); yt+1) · · ·; yt+1) . (178)
The Adam optimizer [83] with a learning rate of 0.001 is
used in this experiment to minimize the loss function L(θ, ϕ)
defined in Eq. (51).
D. Robot Localization in Maze Environments
The dynamic model, measurement model, and proposal
distribution of NF-DPFs in this experiment are constructed
with normalizing flows. In particular, one can draw samples
from the dynamic model of NF-DPFs by first drawing samples
˙xit+1 with Eq. (53) and then applying a normalizing flow
Tθ(·) : RdX → RdX to ˙xit+1:
xit+1 = Tθ( ˙xit+1) ∼ p(xt+1|xt; θ) , (179)
where Tθ(·) is defined as a composition of K Real-NVP
models defined in Eqs. (167)-(170).
Given a particle xit at time step t, at time step t + 1, new
particles xit+1 from the proposal distribution of the NF-DPF
are generated by first drawing samples ˆxit+1 with Eq. (53)
and then applying a conditional normalizing flow Fϕ(·; ·) :
RdX +dY → RdX :
xit+1 = Fϕ(ˆxit+1; yt+1) ∼ q(xt+1|xt, yt+1; ϕ) , (180)
where Fϕ(·; ·) is defined as a composition of K conditional
Real-NVP models defined in Eqs. (156)-(159).
For this experiment, the proposed NF-DPF approximates
the conditional likelihood p(yt|xt; θ) of an observation yt
conditioned on a latent state xt as follows:
et = Uθ(yt) , (181)
zt = G−1θ (et; xt) , (182)
p(yt|xt; θ) ≈ p(et|xt; θ) (183)
= pZ(zt)
 det JGθ (zt; xt)−1 , (184)
where Uθ(·) : RY → Rde is the encoder function constructed
with convolutional neural networks with that transforms 32 ×
32 RGB images to 32-dimensional feature vectors, G−1θ (·) :
Rde × X:→ Rde is a conditional normalizing flow built by
stacking two conditional Real-NVP models [76], and pZ(·) is
the PDF of a standard Gaussian distribution.
In this experiment, we set K = 2 , i.e. the (conditional)
normalizing flows are constructed by stacking two (condi-
tional) Real-NVP models [70], [76]. We set the learning rate
to be 0.001, and use the Adam optimizer to train DPFs by
minimizing the loss function L(θ, ϕ) defined in Eq. (51).
E. Robot tracking in Michigan NCLT dataset
In this experiment, the dynamics of the moving robot is
modeled as follows:
xt+1 : =


l(1)t+1
l(2)t+1
∆l(1)t+1
∆l(2)t+1

 =


l(1)t + ∆l(1)t
l(2)t + ∆l(2)t
∆l(1)t
∆l(2)t

 + ςt , (185)
where ςt ∼ N(0, Σ2) is the dynamic noise, and Σ :=
diag(σl, σl, σ∆l, σ∆l) with σl = 1.0 and σ∆l = 1.0.
The dynamic model, measurement model, and proposal dis-
tribution of NF-DPFs in this experiment are constructed with
normalizing flows. To draw samples from the dynamic model
of NF-DPFs, one can first draw samples ˙xit+1 with Eq. (185)
and then apply a normalizing flow Tθ(·) : RdX → RdX to
˙xit+1:
xit+1 = Tθ( ˙xit+1) ∼ p(xt+1|xt; θ) , (186)
where Tθ(·) is defined as a composition of K Real-NVP
models defined in Eqs. (167)-(170). To draw samples from
the proposal distribution of the NF-DPF, we first draw samples
ˆxit+1 with Eq. (185) and then apply a conditional normalizing
flow Fϕ(·; ·) : RdX +dY → RdX to ˆxit+1:
xit+1 = Fϕ(ˆxit+1; yt+1) ∼ q(xt+1|xt, yt+1; ϕ) , (187)
where Fϕ(·; ·) is defined as a composition of K conditional
Real-NVP models defined in Eqs. (156)-(159).
For the measurement model in the NF-DPF, the conditional
likelihood p(yt|xt; θ) is approximated as below:
zt = G−1θ (yt; xt) , (188)
p(yt|xt; θ) ≈ p(yt|xt; θ) (189)
= pZ(zt)
 det JGθ (zt; xt)−1 , (190)

IEEE TRANSACTIONS ON SIGNAL PROCESSING 23
where G−1θ (·) : Rde × X:→ Rde is a conditional normalizing
flow built by stacking two conditional Real-NVP models [76],
the observation yt is noisy odometry reading of the robot, and
pZ(·) is the PDF of a standard Gaussian distribution.
In this experiment, we set K = 2 , i.e. the (conditional)
normalizing flows are constructed by stacking two (condi-
tional) Real-NVP models [70], [76]. We set the learning rate
to be 0.001, and use the Adam optimizer to train DPFs by
minimizing the RMSE loss function LRMSE(θ, ϕ) defined in
Eq. (52).