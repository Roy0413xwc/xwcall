---
title: "Overparameterized ReLU Neural Networks Learn the Simplest Model Neural Isometry and Phase Transitions"
zotero_key: "IZAZ7ZJW"
pdf_key: "41ANLAVB"
collection: "其他"
source: "Open-access PDF (arXiv, pypdf extraction)"
page_mapping: unverified
---

# Overparameterized ReLU Neural Networks Learn the Simplest Model Neural Isometry and Phase Transitions — Fulltext

> 由开放获取 PDF 提取生成，保留原文（英文），不做翻译与改写。
> PDF 页码未验证（pypdf 文本提取不含可靠页码映射）。

---

1
Overparameterized ReLU Neural Networks Learn
the Simplest Model: Neural Isometry and Phase
Transitions
Yifei Wang1, Yixuan Hua 2, Emmanuel J. Cand` es3, Mert Pilanci 1 Member, IEEE
Abstract
The practice of deep learning has shown that neural networks generalize remarkably well even with an extreme
number of learned parameters. This appears to contradict traditional statistical wisdom, in which a trade-oﬀ between
model complexity and ﬁt to the data is essential. We aim to address this discrepancy by adopting a convex optimization
and sparse recovery perspective. We consider the training and generalization properties of two-layer ReLU networks
with standard weight decay regularization. Under certain regularity assumptions on the data, we show that ReLU
networks with an arbitrary number of parameters learn only simple models that explain the data. This is analogous
to the recovery of the sparsest linear model in compressed sensing. For ReLU networks and their variants with skip
connections or normalization layers, we present isometry conditions that ensure the exact recovery of planted neurons.
For randomly generated data, we show the existence of a phase transition in recovering planted neural network models,
which is easy to describe: whenever the ratio between the number of samples and the dimension exceeds a numerical
threshold, the recovery succeeds with high probability; otherwise, it fails with high probability. Surprisingly, ReLU
networks learn simple and sparse models that generalize well even when the labels are noisy . The phase transition
phenomenon is conﬁrmed through numerical experiments.
Index T erms
neural networks, deep learning, convex optimization, sparse recovery, compressed sensing, 𝓁1 minimization, Lasso.
I. Introduction
R
ecent work has shown that neural networks (NNs) exhibit extraordinary generalization abilities in many machine
learning tasks. Although NNs employed in practice are often over-parameterized, meaning the number of param-
eters exceeds the sample size, they generalize to unseen data and perform well. In this work, we study the problem of
generalization in such over-parameterized models from a convex optimization and sparse recovery perspective. We are
interested in the setting where a NN with an arbitrary number of neurons is trained on datasets that have a simple
structure, for instance, when the label vector is the output of a simple NN, which may have additive noise. A natural
question arises: under which conditions, a neural network with an arbitrary number of neurons, in which the number
of trainable parameters can be quite large, recovers the planted model exactly and thus achieve perfect generalization?
We uncover a sharp phase transition in the behavior of NNs in the recovery of simple planted models. Our results imply
that the weight decay regularization solely controls whether the NN recovers the underlying simple model planted in
the data or fails by overﬁtting a more complex model, regardless of the number of parameters in the NN.
Our ﬁndings are close in spirit to classical results on sparse recovery and compressed sensing. It is known that
there exists a sharp phase transition in recovering a sparse planted vector from random linear measurements. To be
speciﬁc, the probability of successful recovery will be close to one when the sample number exceeds a certain threshold.
Otherwise, the probability of recovery is close to zero. This can be shown by analyzing the intersection probability of
a convex cone with a random subspace, which undergoes a sharp phase transition as the statistical dimension of the
cone changes with respect to the ambient dimension [1]. By leveraging recently discovered connections between ReLU
NNs and Group Lasso models [2, 3, 4, 5, 6], we show that a calculation involving statistical dimensions of convex cones
implies a phase transition in two-layer ReLU NNs for recovering simple planted models.
In addition, we consider deterministic training data and derive analogues of the irrepresentability condition [7]
and Restricted Isometry Property [8, 9], which play an important role in the recovery of sparse linear models. We
develop the notion of Neural Isometry Conditions to characterize non-random training data that allow exact recovery
of planted neurons. We further show that random i.i.d. Gaussian, sub-Gaussian, and Haar distributed random matrices
satisfy Neural Isometry Conditions with high probability when the number of samples is suﬃciently high. The random
Gaussian data assumption is widely used in practice. For instance, the subproblem in training diﬀusion models [10, 11]
is equivalent to learn the function over Gaussian random data.
1Yifei Wang and Mert Pilanci are with the Department of Electrical Engineering, Stanford University, Stanford, CA USA. E-mail:
{wangyf18,pilanci}@stanford.edu
2Yixuan Hua is with the Department of Operations Research & Financial Engineering, Princeton University, Princeton, NJ USA.
3Emmanuel J. Cand` es is with the Department of Statistics and Department of Mathematics, Stanford University, Stanford, CA USA.
arXiv:2209.15265v3  [cs.LG]  17 Feb 2023

2
Model Data Success Failure Resultsstrong recovery weak recovery
linear Haar n> 7.613d n> 2d n< 2d Thm. 7 Thm. 9Gaussian n>O (d log(n)) n> 2d n< 2d Thm. 8, Thm. 5
ReLU-normalized Gaussian - n> 2d - Thm. 11
ReLU Gaussian - n→∞ - Prop. 9
two ReLUs-normalized Gaussian - n→∞ - Prop. 8
k ReLUs - - Neural Isometry Condition (NIC-k) - Prop. 4
k ReLUs-normalized - - - - Prop. 5
noisy linear model sub-Gaussian - n>O (d log(n)) - Thm. 10
TABLE I: Summary of our results for the success or failure of the recovery of planted neurons. Gaussian data refers
to training matrices with i.i.d. standard Gaussian entries, Haar data refers to uniformly drawn training matrices from
the set of orthogonal matrices. Strong recovery refers to the recovery of all possible planted neurons, whereas weak
recovery refers to the recovery of ﬁxed neurons.
Although neural networks lead to non-convex optimization problems which are challenging to analyze, a recent line
of work [2, 3, 4] showed that regularized training problems of multilayer ReLU networks can be reformulated as convex
programs. Based on the convex optimization formulations, [6] further gives the exact characterizations of all global
optima in two-layer ReLU networks. More precisely, it was shown that all globally optimal solutions of the nonconvex
training problem are given by the solution set of a simple convex program up to permutation and splitting. In other
words, we can ﬁnd the set of optimal NNs for the regularized training problem by solving a convex optimization
problem. The convex optimization formulations of NNs were also extended to NNs with batch normalization layers
[12], convolutional NNs (CNNs) [13, 4], polynomial activation networks [14], transformers with self-attention layers [15]
and Generative Adversarial Networks (GANs) [16].
We study recovery properties of optimal two-layer ReLU neural networks by considering their equivalent convex
formulations and leveraging connections to sparse recovery and compressed sensing. We also consider variants of the
basic two-layer architecture with skip connections and normalization layers, which are basic building blocks of modern
DNNs such as ResNets [17]. We show the existence of a sharp phase transition in the recovery of simple models via
ReLU NNs. To be more speciﬁc, for a data matrix X∈ Rn×d, there exists a critical threshold for the ratio n/d,
above which a planted network with few neurons will be the unique optimal solution of the convex program of two-
layer networks with probability close to 1, as long as n and d are moderately high. Otherwise, this probability will
be close to 0. The same conclusion applies to the non-convex training of the two-layer network with any number of
neurons, up to permutation and neuron splitting (see Appendix B). Moreover, our results highlight the importance
of skip-connections and normalization layers in the success of recovery as we show in Section III-C. We also provide
deterministic isometry conditions that guarantee the recovery of an arbitrary number of ReLU neurons. We summarize
these results in Table I.
A. Related works
Recent work have investigated linearized neural network models trained with gradient descent from a kernel based
learning perspective [18, 19, 20, 21]. When the width of the neural network approaches inﬁnity, it is known that NNs
can ﬁt all the training data [22, 23, 24]. However, in this regime, the analysis shows that almost no hidden neurons
move from their initial values to learn features [25]. Further experiments also conﬁrm that inﬁnite width limits and
linearized kernel approximations are insuﬃcient to give an adequate explanation for the success of non-convex neural
network models as its width goes to inﬁnity [26]. Due to the non-linear structure of neural networks and non-convexity
of the training problem, only a few works consider the role of over-parameterization when the width of the neural
network is ﬁnite [27, 28, 21].
It was conjectured that models trained with simple iterative methods such as Stochastic Gradient Descent (SGD)
approach ﬂat local minima [29, 30, 31] that generalize well. However, it was also shown that the behavior of the trained
model heavily depends on the choice of the speciﬁc optimization algorithm and its hyper-parameters [32, 33, 30, 34].
Developing algorithms for the recovery of planted two-layer neural networks has been studied in the literature. In
[35, 36], the authors design spectral methods for learning the weight matrices of a planted two-layer ReLU network
with k neurons. In contrast, our work studies the recovery properties of over-parameterized NNs with arbitrary many
neurons that minimize the training objective and sheds light into the optimization landscape. [37, 38, 39, 40] analyze
the recovery of two-layer ReLU neural networks using the gradient descent method, while [41] extends the analysis to
other activation functions, including leaky ReLU. In comparison, our results apply to the case where neural networks
have many more neurons than the planted model.

3
B. Notation
We introduce notations used throughout the paper. We use the notation [ n] to represent the set {1,...,n }. We use
the notation I(·) for the 0-1 valued indicator function which takes the value 1 when its argument is a true logical
statement and 0 otherwise. We reserve boldcase lower-case letters for vectors, boldcase upper-case letters for matrices
and plain lower-case letters for scalars. For a vector w∈ Rd, we use‖w‖p :=(∑di=1|wi|p{1/p to represent its 𝓁p norm.
The notation cos ∠(w, v) := wT v‖w‖2‖v‖2 ∈ [−1, 1] represents the cosine angle between two vectors w∈ Rd and v∈ Rd.
For a matrix X∈ Rn×d, we use ‖X‖2 to denote its operator norm. We use ‖X‖∞,∞ for the matrix inﬁnity norm,
i.e., the elementwise maximum absolute value. We use In∈ Rn×n to denote the identity matrix with size n×n. We
denote λmax(X) for the maximum eigenvalue of a symmetric matrix X. Similarly, the notion eigmax( X) represents
the subspace spanned by the eigenvectors corresponding to the maximum eigenvalue for a symmetric matrix X. We
use the shorthand diag(x1,...,x n) to represent a diagonal matrix with entries x1,...,x n on the diagonal. The notation
xrowi ∈ Rd and xcolj ∈ Rn denoted the i-th row and j-th column of an n×d matrix X∈ Rn×d respectively. We use the
notation poly(n) to denote a polynomial function of the variablen. We call a centered random variableX sub-Gaussian
with variance proxy σ2 > 0 if it holds that E[esX≤e 12σ2s2] for any s∈ R.
C. Organization
In Section II, we present a preview of our results for the special case of linear neuron recovery with ReLU NNs. We
introduce variants of the ReLU NN architecture in Section III. In Section IV we develop deterministic conditions, termed
Neural Isometry Conditions , for the recovery of linear and non-linear neurons using diﬀerent NN architectures.
In Section V, we investigate random ensembles of training data matrices, for which we show the existence of a sharp
phase transition in satisfying these deterministic conditions via non-asymptotic probabilistic bounds. In Section VI, we
develop asymptotic results on the recovery probability for the case of multiple ReLU neurons. We present numerical
simulations to corroborate our theoretical results in Section VII. We present our conclusions in Section VIII.
II. A preview: an exact characterization of linear neuron recovery
In this section, we present a preview of our results on two-layer ReLU networks with skip connection in the special
case of linear neuron recovery. We generalize our result to the recovery of nonlinear neurons using diﬀerent architectures
later in Sections IV-VI. We invite the reader to refer to Appendix A for the background on the isometry conditions
in compressed sensing, which share important parallels with our analysis. We start with the following two-layer ReLU
network model with a linear skip connection.
f(X; Θ) = Xw1,1w2,1 +
m
i=2
(Xw1,i)+w2,i,
where Θ ={W1, w2} denotes trainable parameters including ﬁrst layer weights W1∈ Rd×m and second layer weights
w2∈ Rm. We will ﬁrst consider the minimum norm interpolation problem
min
Θ
‖W1‖2F +‖w2‖22/rehtipupleft /rehtipownright/rehtipownleft /rehtipupright
‖Θ‖2F
, s.t. f(X; Θ) = y. (1)
where the objective ‖Θ‖2F stands for the weight-decay regularization term.
A. Hyperplane Arrangements
We now introduce an important concept from combinatorial geometry called hyperplane arrangement patterns, in
order to introduce convex optimization formulations of ReLU network training problems.
Deﬁnition 1 (Diagonal Arrangement Patterns) We deﬁne{0, 1} valued diagonal matrices D1,..., Dp that con-
tain an enumeration of the set of hyperplane arrangement patterns of the training data matrix X as follows. Let us
deﬁne
H :=
{
diag(I(Xh≥ 0))
⏐⏐ h∈ Rd, h⁄= 0}. (2)
We call D1,..., Dp ∈ H, an enumeration of the elements of H in an arbitrary ﬁxed order, diagonal arrangement
patterns associated with the training data matrix X.
The{0, 1} valued patterns on the diagonals of D1,..., Dp encodes a partition of Rd by hyperplanes passing through
the origin that are perpendicular to the rows of X. The number of such distinct patterns is the cardinality of the set
H and is bounded as follows
p :=|H|≤ 2
r−1
k=0
(n− 1
k
{
≤ 2r
(e(n− 1)
r
{r
,

4
D1 =
(1 0 0
0 1 0
0 0 1
{
D2 =
(1 0 0
0 0 0
0 0 1
{
D3 =
(1 0 0
0 0 0
0 0 0
{
D4 =
(0 0 0
0 0 0
0 0 1
{
D5 =
(0 0 0
0 1 0
0 0 0
{
D6 =
(0 0 0
0 1 0
0 0 1
{ x1
x2
Fig. 1: A 2-dimensional example of diagonal arrangement patterns.
where r = rank(X), see [42]. A 2-dimensional example of diagonal arrangement patterns with three hyperplanes, i.e.,
n = 3, is presented in Figure 1. Note that there are p = 2
((2
0
{
+
(2
1
{{
= 6 regions and corresponding patterns associated
with this conﬁguration. For every ﬁxed dimensiond (or rankr), the number of patternsp is bounded by poly(n). In [13],
it was shown that convolutional neural networks (CNNs) have a small ﬁxed rank. For instance, a typical convolutional
layer of size 3× 3× 512, e.g. 512 ﬁlters of size 3 × 3 implies r≤ 3× 3 = 9.
B. Convex Reformulations
The non-convex optimization problem (1) of ReLU networks with skip connection is equivalent1 to a convex program:
min
w0,(wj,w′j)pj=1
p
j=1
(
‖wj‖2 +
‖‖w′j‖‖2{
s.t. Xw0 +
p
j=1
DjX
(
wj− w′j{ = y,
(2Dj− In)Xwj≥ 0, (2Dj− In)Xw′j≥ 0,j ∈ [p].
(3)
Indeed, the global optimal set of the non-convex program (1) can be characterized by the optimal solutions of the
convex program (3). The next result is an extension of the earlier results [5, 6, 3] to NNs with a skip connection.
Lemma 1 All globally optimal solutions of the non-convex problem (1) of ReLU networks with skip connection can be
found (up to splitting and permutation) via the optimal solution set of the convex program (3) when m≥ m∗. Here
m∗ :=∑pj=1 I[w∗j⁄= 0] + I[w∗′j ⁄= 0] is the number of non-zero neurons in the minimum norm optimal solution of (3).
C. Linear Neural Isometry Condition
We now consider the case when the labels are generated by a planted linear model, i.e., y = Xw∗ and ask the
following question:
Can ReLU NNs with a linear skip connection learn a planted linear relation as eﬀectively as a linear model?
In order to prove that the linear model can be recovered by solving the non-convex problem (1) or its convex
reformulation (3), we introduce the following isometry condition on the training data.
Deﬁnition 2 (Linear Neural Isometry Condition) The linear neural isometry condition for recovering the linear
model y = Xw∗ from (12) is given by:
‖‖‖XTDjX(XTX{−1 ˆw‖‖‖2 < 1,∀j∈ [p], (NIC-L)
where ˆw := w∗‖w∗‖2 . Note that (NIC-L) holds uniformly for all w∗ only if‖‖‖‖‖‖Id− k:xTk w<0 xkxTk( nk=1 xkxTk(−1‖‖‖‖‖‖2 < 1,∀w : w⁄= 0. (4)
1Under the condition that the NN has suﬃciently many neurons (see e.g., Theorem 1 in [2])

5
The above is a spectral isometry condition on the empirical covariance ˆΣ :=∑nk=1 xkxTk and its subsampled versionˆΣw :=∑k:xTk w<0 xkxTk that excludes samples activated by a ReLU neuron. Intuitively, for the above condition to hold,the empirical covariance should be relatively stable when samples that lie on a halfspace are removed, and consequently‖‖‖Id− ˆΣw ˆΣ−1‖‖‖2 =‖‖‖(ˆΣ− ˆΣw{ˆΣ−1‖‖‖2 < 1.
In the following proposition, we show that the linear neural isometry condition implies the recovery of the planted
linear model by solving (3).
Proposition 1 Suppose that n>d and the neural network contains an arbitrary number of neurons, i.e., m≥ 1. Let
y = Xw∗. Suppose that the linear neural isometry condition (NIC-L) holds. Then, the unique optimal solution to (1)
and (3) (up to permutation and splitting 2) is given by the planted linear model, i.e., ˆW ={ ˆw0,{ ˆwj, ˆw′j}pj=1}, where
ˆw0 = w∗ and ˆwj = ˆw′j = 0 for j∈ [p].
The above result implies that minimizing the 𝓁22 objective subject to the interpolation condition uniquely recovers the
ground truth model by setting all the neurons except the skip connection to zero, regardless of the number of neurons
in the NN. Remarkably, a NN with an arbitrary number of neurons, i.e., containing arbitrarily many parameters,
optimizing the criteria (1) achieves perfect generalization when the ground truth is the linear model. The exact recovery
follows from the equivalence of the problem (1) to the group sparsity minimization problem (3), however, this sparsity
inducing regularization is hidden in the typical non-convex formulation with weight decay regularization, i.e., ‖Θ‖2F .
D. Sharp Phase Transition
Our second main result in this paper is that there exists a sharp phase transition in training ReLU NNs when the
data is generated by a random matrix ensemble and the observations are produced by a planted linear model. We
precisely identify the relation between the number of samples n and the feature dimension d under i.i.d. training data
and planted model assumptions. We ﬁrst summarize our results in this section informally, and then present detailed
theorems in later sections.
Theorem 1 (informal) Suppose that the training data matrix X∈ Rn×d is i.i.d. Gaussian, and f(X; Θ) is a two-
layer ReLU network containing arbitrarily many neurons with skip connection. Assume that the response is a noiseless
linear model y = Xw∗. The condition n >2d is suﬃcient for ReLU networks with skip connections or normalization
layers to recover the planted model exactly with high probability. Furthermore, when n< 2d, the recovery fails with high
probability.
Interestingly, in the regime where n∈ (d, 2d), ﬁtting a simple linear model instead of a NN recovers the planted
linear model. In contrast, the ReLU network fails to recover the linear model due to the richness of the model class.
We formalize this observation as follows:
Corollary 1 Suppose that the observations are given by y = Xw∗, where w∗∈ Rd is a ﬁxed, unknown parameter. If
n∈ (d, 2d), a simple linear model flin(X; w) = Xw recovers the planted linear neuron w∗ exactly for any w∗, while
the ReLU network with skip connection and m≥ 1 neurons ﬁtted via either (5) with any β≥ 0 or (1) fails with high
probability for all w∗ such that Xw∗≥ 0.
This corollary is illustrated in Figure 2 as a phase diagram in the ( n,d ) plane. This result clearly shows that the model
complexity of ReLU networks can hurt generalization compared to simpler linear models when the number of samples
is limited, but information-theoretically suﬃcient for exact recovery. On the other hand, ReLU networks learn the true
model and close the gap in generalization when twice as many samples are available, i.e., n> 2d.
E. Noisy Observations
We also develop theoretical results when the observation vector y is noisy and the following regularized version of
the training problem is solved. We consider the regularized training problem
min
Θ
1
2‖f(X; Θ)− y‖22 + β2R(Θ), (5)
where R(Θ) =‖Θ‖2F is the weight-decay regularization term.
Theorem 2 (informal) Suppose that the training data matrix X∈ Rn×d is i.i.d. sub-Gaussian, and f(X; Θ) is a two-
layer ReLU network with m neurons, skip connection and a normalization layer applied before the ReLU layer. Assume
that the observation y is the sum of a linear neuron and an arbitrary disturbance term z, i.e., y = Xw∗ + z. Then,
there exists a range of values for the regularization parameter β, such that the non-convex optimization problem in (5)
2Please see Appendix B for a precise deﬁnition of the notion of permutation and splitting.

6
linear
model
recovers
ReLU network
with skip connection
recovers
n<d
no recovery
d<n< 2d
n> 2d
d
n
(b)
Fig. 2: Phase transition in recovering a linear neuron. Left: when n∈ (d, 2d), ReLU network fails to recover a planted
linear model, while a simple linear model succeeds in recovery. Right: Empirical generalization error in recovering a
linear neuron by solving the convex program (3) numerically.
and its corresponding convex formulation (see (24) in Section V) exactly recovers a linear model with high probability
when n is suﬃciently large for all values of the number of neurons m≥ 1. Additionally, the 𝓁2 distance between the
learned linear neuron w and the planted neuron is bounded by
‖w− w∗‖2≤O (β) +O(‖z‖2).
Considering the non-convex optimization problem (6) with weight decay, i.e., 𝓁2-regularization, with a proper choice
of the regularization parameter β, the optimal NN with arbitrary number of neurons consists of only a linear weight.
The key to understand this result involves techniques from sparse recovery combined with the convex re-formulation
of the regularized training problem (5) as group 𝓁1 regularization.
The above result shows the bias of two-layer ReLU networks towards simple models even when the relation between
the data and labels is not exactly linear. Our proof also shows that skip connection and normalization layers in these
two-layer networks are essential, which are the building blocks of the ResNets popularly applied in the practice. The
details of Theorem 2 can be found in Section V-D.
Corollary 2 By combining the above proposition with Lemma 1, we note that the global optima of the nonconvex
problem (7) consists of exactly the planted linear neuron up to permutation and splitting.
III. Convex Formulations of ReLU NNs with Skip Connection and Normalization
In this section, we introduce important variants of the simple ReLU architecture and their corresponding convex
reformulations. As it will be shown next, architectural choices of these models, such as an addition of a normalization
layer play a signiﬁcant role in their recovery properties.
Suppose that X∈ Rn×d is the training data matrix and y∈ Rd is the label vector. We will focus on the following
two-layer ReLU NNs:
• plain ReLU networks:
fReLU(X; Θ) = (XW1)+w2 =
m
i=1
(Xw1,i)+w2,i, Θ = (W1, w2),
where W1∈ Rd×m and w2∈ Rm.
• ReLU networks with skip connections:
fReLU−skip(X; Θ) = Xw1,1w2,1 +
m
i=2
(Xw1,i)+w2,i,
where Θ = (W1, w2), W1∈ Rd×m and w2∈ Rm.

7
• ReLU networks with normalization layers:
fReLU−norm(X; Θ) =
m
i=1
Nαi((Xw1,i)+)w2,i,
where Θ = (W1, w2,α) and the normalization operator N α(v) is deﬁned by
Nα(v) = v‖v‖2α, v∈ Rn,α∈ R.
We note that the normalization layer employed in the model fReLU−norm is a variant of the well-known batch nor-
malization (BN) with a trainable normalization-correction variable. However, convex formulations of ReLU NNs with
exact Batch Normalization layers can be derived as shown in [12]. We now focus on the regularized training problem
min
Θ
1
2‖f(X; Θ)− y‖22 + β2R(Θ). (6)
For plain ReLU networks and ReLU networks with skip connections, we consider weight decay regularization. This is
given by R(Θ) =‖Θ‖2F = (‖W1‖2F +‖w2‖22), while for ReLU networks with normalization layers, we have R(Θ) =
(‖W1‖2F +‖w2‖22 +‖α‖22). When β→ 0, the optimal solution of the above problem approaches the following minimum
norm interpolation problem:
min
Θ
R(Θ) s.t. f(X; Θ) = y. (7)
A. Convex formulations for plain ReLU NNs
According to the convex optimization formulation of two-layer ReLU networks in [2], the minimum norm problem
(7) of plain ReLU networks, i.e., the model fReLU(X; Θ), is equivalent to a convex program:
min
{wj,w′j}pj=1
p
j=1
(
‖wj‖2 +
‖‖w′j‖‖2{
s.t.
p
j=1
DjX
(
wj− w′j{ = y,
(2Dj− In)Xwj≥ 0, (2Dj− In)Xw′j≥ 0,j ∈ [p].
(8)
Here the matricesD1,..., Dp are diagonal arrangement patterns as deﬁned in Deﬁnition 1. Compared to the formulation
in [2], we exclude the hyperplane arrangement induced by the zero vector without loss of generality as justiﬁed in
Appendix C. Analogous to the results in [2, 6], the global optimal set of the non-convex program (7) can be characterized
by the optimal solutions of the convex program (8).
Theorem 3 All globally optimal solutions of the non-convex problem (7) of ReLU networks can be computed via the
optimal solutions of the convex program (8) up to splitting and permutation as soon as the number of neurons m exceeds
a critical threshold m∗.
The inequality constraints in (8) render the analysis of the uniqueness of the optimal solution directly via (8) diﬃcult.
However, we show that we can instead work with a relaxation without any loss of generality. By dropping all inequality
constraints, we obtain a relaxation of the convex program (8) which reduces to the following group 𝓁1-minimization
problem:
min
{wj}pj=1
p
j=1
‖wj‖2 s.t.
p
j=1
DjXwj = y. (9)
The above form corresponds to the well-known Group Lasso model [43] studied in high-dimensional variable selection
and compressed sensing. We note that a certain unique solution to the relaxation in (9) satisfying the constraint in
the original problem (8) implies that the original problem (8) also has the same unique solution.
Another interesting observation is that the above group 𝓁1-minimization problem corresponds to the minimum norm
interpolation problem with gated ReLU activation, for which the NN model is given by
fgReLU(X; Θ) =
m
i=1
diag(I(Xhi≥ 0))(Xw1,i)w2,i, (10)
where Θ = (W1, w2, H). This derivation is provided in Appendix D.

8
B. Convex formulations for ReLU networks with skip connection
The minimal problem (7) of ReLU networks with skip connection, i.e., the model fReLU−skip(X; Θ), is equivalent to
a convex program:
min
w0,(wj,w′j)pj=1
p
j=1
(
‖wj‖2 +
‖‖w′j‖‖2{
s.t. Xw0 +
p
j=1
DjX
(
wj− w′j{ = y,
(2Dj− In)Xwj≥ 0, (2Dj− In)Xw′j≥ 0,j ∈ [p].
(11)
By dropping all inequality constraints, the convex program (3) reduces to the following group𝓁1-minimization problem:
min
{wj}pj=0
p
j=0
‖wj‖2 s.t. Xw0 +
p
j=0
DjXwj = y. (12)
Similarly, this group𝓁1-minimization problem is equivalent to the minimum norm interpolation problem of gated ReLU
networks with skip connection.
C. Convex formulations for ReLU networks with normalization layer
The minimum norm problem (7) of ReLU networks with normalization layer, i.e., the model fReLU−norm(X; Θ). is
equivalent to the following convex program:
min
{wj,w′j}pj=1
p
j=1
(
‖wj‖2 +
‖‖w′j‖‖2{
s.t.
p
j=1
Uj
(
wj− w′j{ = y,
(2Dj− In)XVTj Σ−1j wj≥ 0, (2Dj− In)XVTj Σ−1j w′j≥ 0,j ∈ [p],
(13)
where DjX = UjΣjVj is the compact singular value decomposition (SVD) of DjX for j∈ [p]. Again, the global
optima of the non-convex program (7) can be characterized by the optimal solutions of the convex program (13).
Theorem 4 Suppose that n>d . All globally optimal solutions of the non-convex problem (7) of ReLU networks with
normalization layer can be found by the optimal solutions of the convex program (13) (up to splitting and permutation)
when m is greater than some threshold m∗.
By dropping all inequality constraints, the convex program (13) reduces to a group 𝓁1-minimization problem:
min
{wj}pj=1
p
j=1
‖wj‖2, s.t.
p
j=1
Ujwj = y. (14)
Analogously, the above group 𝓁1-minimization problem corresponds to the minimum norm interpolation problem of
gated ReLU network with normalization layer.
IV. Neural isometry conditions and recovery of nonlinear neurons
In this section, we introduce conditions on the training data, called neural isometry, that guarantee the recovery of
planted models via solving the non-convex problem (7) or the convex problems (9, 12, 14).
A. Recovery of a single ReLU neuron using plain ReLU NNs
In this section we present recovery results on ReLU networks. Suppose that y = (Xw∗)+ is the output of a planted
ReLU neuron 3, where w∗⁄= 0. Let Di∗ = diag(I(Xw∗≥ 0)) be the diagonal arrangement pattern corresponding to
the planted neuron. Based on these diagonal arrangement patterns, we introduce a regularity condition on the data
which is analogous to the irrepresentability condition of sparse recovery, called the Neural Isometry Condition (NIC).
For the recovery of a single neuron, the NIC is deﬁned as follows.
3Here we ignore the second layer weight without loss of generality. Positive weights can be absorbed into the ﬁrst layer weight, while for
negative weights we can consider to use −y as the label.

9
Deﬁnition 3 (Neural Isometry Condition for a single ReLU neuron) A suﬃcient condition for recovering a
single neuron y = (Xw∗)+ via the problem (9) is given by:‖‖‖XTDjDi∗X(XTDi∗X{−1 ˆw‖‖‖2 < 1,∀j⁄=i∗, (NIC-1)
where ˆw = w∗‖w∗‖2 .
We assume that the matrix XTDi∗X = ∑k: xTk w∗≥0 xkxTk is invertible whenever the above condition holds. Thecondition above can be equivalently stated as
‖‖‖‖‖ 
k:xTk w∗≥0, xTk w≥0
xkxTk
( 
k: xTk w∗≥0
xkxTk
{−1
ˆw
‖‖‖‖‖
2
< 1,∀w : I(Xw≥ 0)⁄= I(Xw∗≥ 0). (15)
In the following proposition, we show that the neural isometry condition (NIC-1) implies the recovery of the planted
model by solving the convex reformulation (8), or equivalently the non-convex problem (7).
Proposition 2 Suppose that n≥d. Let y = (Xw∗)+. Suppose that (NIC-1) holds. Then, the unique optimal solution
to (8) is given by the planted ReLU neuronw∗, i.e, ˆW ={( ˆwj, ˆw′j)|j∈ [p]}, where ˆwi∗ = w∗, ˆw′i∗ = 0 and ˆwj = ˆw′j = 0
for j⁄=i∗.
Corollary 3 By combining the above proposition with Theorem 3, we note that all global optima of the nonconvex
problem (7) consist of permuted and split versions of the planted ReLU neuron when the condition (NIC-1) holds.
B. Recovery of a single ReLU neuron using ReLU networks with normalization layer
We now consider the case where y = (Xw∗)+‖(Xw∗)+‖2 , which is the output of a single-neuron ReLU network followed by
a normalization layer. Let Di∗ = diag(I(Xw∗≥ 0)) and denote ˜w∗ = Σi∗Vi∗w∗‖Σi∗Vi∗w∗‖2 . Here, Ui∗, Σi∗, Vi∗ are the SVDfactors of Di∗X as deﬁned in subsection III-C. We note the simpliﬁed expression
Ui∗ ˜w∗ = Ui∗Σi∗Vi∗w∗‖Σi∗Vi∗w∗‖2 = (Xw∗)+‖(Xw∗)+‖2 = y.
We introduce the following normalized Neural Isometry Condition.
Deﬁnition 4 (Normalized Neural Isometry Condition) The normalized neural isometry condition for recovering
the planted model y = (Xw∗)+‖(Xw∗)+‖2 from (14) is given by:‖‖UTj Ui∗ ˜w∗‖‖2 < 1,∀j∈ [p],j ⁄=i∗. (NNIC-1)
Similarly, the normalized neural isometry condition implies the the recovery of the planted model via solving the convex
formulation for ReLU NNs with normalization layer given in (13) or the corresponding non-convex problem (7).
Proposition 3 Let y = (Xw∗)+‖(Xw∗)+‖2 . Suppose that the NNIC91 given in (NNIC-1) holds. Then, the unique optimal
solution to (13) is given by the planted normalized ReLU neuron, i.,e., ˆW = ( ˆwj, ˆw′j)pj=1, where ˆwi∗ = Σi∗Vi∗w∗‖Σi∗Vi∗w∗‖2 ,w′i∗ = 0 and ˆwj = ˆw′j = 0 for j⁄=i∗.
Similarly, by combining the above proposition with Theorem 4, we note that all global optima of the nonconvex
problem (7) consist of split and permuted versions of the planted neuron.
Remark 1 Our analysis reveals that normalization layers play a key role in the recovery conditions. Note that in
(NIC-1), the matrices{D1X,..., DpX} are replaced by their whitened versions, eﬀectively cancelling the matrix inverse(∑
k: xTk w∗≥0 xkxTk{−1 in (NNIC-1). Therefore, the conditioning of the matrices are improved by the addition of anormalization layer, which applies implicit whitening to the data blocks {D1X,..., DpX}. As a result, it can be
deduced that normalization layers help NNs learn simple models more eﬃciently from the data.
C. Recovering Multiple ReLU neurons using plain ReLU NNs
We now extend the Neural Isometry Condition to the recovery of k >1 ReLU neurons, starting with plain ReLU
NNs. Suppose that the label vector is given by
y =
k
i=1
(Xw∗i )+r∗i,
where w∗i∈ Rd,r∗i∈{− 1, +1} fori∈ [k], and diag(I(Xw∗i≥ 0)) are distinct for i∈ [k]. Suppose that an enumeration
of the diagonal arrangement patterns corresponding to the planted neurons are given by D1,..., Dp. We denote Dsi =

10
diag(I(Xw∗i≥ 0)) for i∈ [k], where S ={s1,...,s k}⊆ [p] contain the indices of planted neurons in the enumeration
of arrangement patterns{1,...,p} according to any ﬁxed order.
Deﬁnition 5 (Neural Isometry Condition for k neurons) For recoveringk ReLU neurons from the observations
y =∑ki=1(Xw∗i )+r∗i via the optimization problem (13), we introduce the multi-neuron Neural Isometry Condition:‖‖‖‖‖‖‖‖XTDj)])XTDs1...XTDsk([†)]) ˆw1...ˆwk([‖‖‖‖‖‖‖‖2 < 1,∀j∈ [p],j /∈S, (NIC-k)
where ˆwi :=r∗i w∗i/‖w∗i‖2∀i∈ [k].
In the following proposition, we show that (NIC-k) implies the recovery of the planted model with k neurons by solving
the non-convex problem (7) or its convex reformulation (8).
Proposition 4 Suppose that (NIC-k) is satisﬁed. Then, the unique optimal solution to (8) is given by the planted
neurons, i.e., ˆW = ( ˆwj, ˆw′j)pj=1, where we let ˆwsi = wi‖wi‖2 , w′si = 0 forr∗i = 1, wsi = 0, ˆw′si = wi‖wi‖2 , for r∗i =−1 and
ˆwj = ˆw′j = 0 for j⁄=i∗.
As a corollary, by combining the above proposition with Theorem 3, we deduce that all globally optimal solutions of
the non-convex problem (7) with plain ReLU NNs consist of the planted model up to permutation and splitting.
D. Recovering Multiple ReLU neurons using ReLU NNs with Normalization Layer
Next, we consider ReLU NNs with normalization layers. Suppose that the label vector takes the form
y =
k
i=1
(Xw∗i )+
‖(Xw∗i )+‖2r∗i,
where w∗i∈ Rd are ﬁrst layer weights, r∗i ∈ R are second layer weights for i∈ [k] and diag(I(Xw∗i≥ 0)) are distinct
for each i∈ [k]. For simplicity, denote Dsi = diag(I(Xw∗i ≥ 0)) for i∈ [k], where S ={s1,...,s k} ⊆[p]. Let
DiX = UiΣiVi be the singular value decomposition for i∈ [p].
Deﬁnition 6 (Normalized Neural Isometry Condition for k neurons) For recoveringk normalized ReLU neu-
rons from the observations y =∑ki=1 (Xw∗i )+‖(Xw∗i )+‖2r∗i via the optimization problem (13), the normalized neural isometrycondition is given by ‖‖‖‖‖‖‖‖UTj )])UTs1...UTsk([†)]) ˜w1...˜wk([‖‖‖‖‖‖‖‖2 < 1,∀j∈ [p],j /∈S, (NNIC-k)
where ˜wi :=r∗i ΣsiVsiw∗i/‖ΣsiVsiw∗i‖2∀i∈ [k].
Suppose that Ds1,..., Dsj further satisfy that DsiDsj = 0 for i⁄= j. Then, we can simplify the neural isometry
condition to the following form
‖‖‖‖‖UTj ki=1 (Xw∗i )+‖(Xw∗i )+‖2r∗i‖‖‖‖‖2 =‖‖UTj y‖‖2 < 1,∀j∈ [p]/S. (16)
In the following proposition, we show that (NNIC-k) implies the recovery of the k planted normalized ReLU neurons
via the optimization problem (13).
Proposition 5 Suppose that (NNIC-k) is satisﬁed. Then, the unique optimal solution to (13) is given by the planted
neurons, i.e., ˆW = ( ˆwj, ˆw′j)pj=1, where ˆwsi = ΣsiVsiwi‖ΣsiVsiwi‖2 , ˆw′si = 0 forr∗i = 1, ˆwsi = 0, ˆw′si = ΣsiVsiwi‖ΣsiVsiwi‖2 forr∗i =−1and ˆwj = ˆw′j = 0 for j⁄=i∗.
Corollary 4 By combining the above proposition with Theorem 3, we note that all globally optimal solutions of the
non-convex problem (7) consist of the split and permuted version of the planted model.

11
V. Sharp Phase Transitions
One of our major results in this paper is that there exists a sharp phase transition in the success probability of
recovering planted neurons in the ( n,d ) plane for certain random ensembles for the training data matrix. We start
illustrating this phenomenon with the case of recovering linear neurons through an application of the kinematic formula
for convex cones.
Fig. 3: Optimal ReLU NNs found via the convex program (3). Left: A ReLU neuron is ﬁtted to the observations
generated from a linear model when n = 2,d = 2. Right: Only a linear neuron is ﬁtted to the observations generated
from a linear model when n = 5,d = 2.
A. Kinematic formula
We introduce an important result from [1] that will be used in proving the phase transitions in the recovery of
planted neurons via ReLU NNs.
Lemma 2 For a convex cone K⊆ Rn, deﬁne the statistical dimension of the cone K by
δ(K) = E
[
‖ΠK(g)‖22], (17)
where g is a standard Gaussian random vector and ΠK is the Euclidean projection onto the cone K. Deﬁne α :=
(n−δ(K)−d)2
64n2 . Then, we have
P (∃w⁄= 0 : Xw∈K)
{
≤ 4e−nα, δ (K) +d<n,
≥ 1− 4e−nα, δ (K) +d>n. (18)
Consider the positive orthant K = Rn+, which is a convex cone. It can be easily computed that
δ(K) = E[‖πK(g)‖2] = E
) n
i=1
max{0,gi}2
[
= n2. (19)
A direct corollary of the kinematic formula is as follows.
Proposition 6 Let X∈ Rn×d be a matrix whose entries are i.i.d. random variables following N (0, 1). Then, we have
P (∃h⁄= 0 : Xh≥ 0)
{
≤ 4e−nα, d<n/ 2,
≥ 1− 4e−nα, d>n/ 2,
whereα = (n/2−d)264n2 .
This implies that for n> 2d, the probability that the set of diagonal arrangement patterns contain the identity matrix,
i.e., a vector h⁄= 0 such that I(Xh≥ 0) = 1, is close to 1, while for n< 2d, this probability is close to 0.

12
B. Recovering Linear Models
1) Gaussian random data: For Gaussian random data, our next result shows that the ratio n/d controls whether
the Linear Neural Isometry Condition for linear neuron recovery holds or fails with high probability. Therefore, neural
networks do not overﬁt when the number of samples is above a critical threshold regardless of the number of neurons.
Theorem 5 (Phase transition in Gaussian Data: Success) Suppose that each entry xi,j of the data matrix X∈
Rn×d is an i.i.d. random variable following the Gaussian distribution N (0, 1/n). Forn> 2d, NIC9L shown in (NIC-L)
holds with probability at least 1− exp(−αn) where α = (n/2−d)264n2 . Consequently, the unique optimal ReLU NN with
skip connection found via the convex reformulation (11) uniquely recovers planted linear models up to permutation and
splitting.
Remark 2 This implies that when the planted model is y = Xw∗, the linear term w0 = w∗ is the unique optimal
solution to the convex program (3). It is also the unique globally optimal solution to the non-convex problem (7).
We next show that when the ration/d is below a certain critical threshold, W = (w∗, 0,..., 0) is not the unique optimal
solution to the convex problem (11) (or equivalently to the corresponding non-convex problem (7)). Consequently, neural
networks overﬁt when the number of samples is below this critical threshold.
Theorem 6 (Phase transition in Gaussian Data: Failure) Suppose that n< 2d. Assume that each entry of X is
an i.i.d. random variable following the Gaussian distribution N (0, 1/n). Suppose that the planted parameter w∗ satisﬁes
Xw∗ ≥ 0. Then, with probability 1, W = ( w∗, 0,..., 0) is not the unique optimal solution to the minimum norm
interpolation problem of ReLU NNs with skip connection (7) or its convex reformulation (11).
Proof When n< 2d, according to the kinematic formula, we have
P (∃h∈ Rd : Xh≥ 0, h⁄= 0)≥ 1−e−nα, (20)
where α is as deﬁned in Proposition 6. Suppose that there exists h∈ Rd such that h⁄= 0, Xh≥ 0. This implies that
the identity matrix is among the diagonal arrangement patterns, i.e., there exists j∈ [p] such that Dj = In. Assume
that the planted neuron w∗ further satisﬁes that Xw∗≥ 0. In this case, let ˜wi = w′i = 0 ifi⁄=j, ˜wj = w∗ and ˜w′j = 0.
Then, W′ = (0, ˜w1, ˜w′1,..., ˜wp, ˜w′p) is also a feasible solution to (12). This implies that for n <2d, with probability
close to 1, there exists an optimal solution which consist of at least one non-zero ReLU neuron.
However, if the condition Xw∗≥ 0 is not satisﬁed, we next show that W = (w∗, 0,..., 0) is the unique optimal
solution to the minimum norm interpolation problem (7) even when In∈H.
Proposition 7 Suppose that d < n <2d. Assume that each entry of X is an i.i.d. random variable following the
Gaussian distributionN (0, 1/n). Suppose that Xw∗≥ 0 does not hold. Then, with probability 1, W = (w∗, 0,..., 0) is
the unique optimal solution to the minimum norm interpolation problem (7) for ReLU NNs with skip connection, or the
corresponding convex reformulation (11).
In Figure 4, we numerically verify the phase transition by solving the convex program (11) and its relaxation given by
the group 𝓁1-minimization problem (12), which drops the linear inequality constraints in (3).

13
Fig. 4: The empirical probability of successful recovery of the planted linear neuron estimated over 5 independent trials.
Left panel: solving the group 𝓁1-minimization problem (12) as a relaxation of (3). Right panel: solving the convex NN
program (3). Red (blue) region shows the region where exact recovery probability is close to one (zero). The black
lines represent the boundaries of successful recovery with probability 1.
2) Haar random data: We now investigate the case where the training data X∈ Rn×d is a Haar distributed random
matrix. More precisely, X is uniformly sampled from the set of column orthogonal matrices
{
X∈ Rn×d| XTX = Id}
for n≥d. In this case, since ( XTX)−1 = Id, (NIC-L) for the recovery of a linear neuron reduces to
max
h∈Rd, h⁄=0
‖‖XTdiag(I(Xh≥ 0))X ˆw‖‖2 < 1, (orth-NIC-L)
where ˆw := w∗‖w∗‖2 .
Based on the simpler form of (orth-NIC-L), we derive the phase transition results on the recovery of a planted
linear neuron. Moreover, this form enables the analysis of a stronger recovery condition that ensures the simultaneous
recovery of all planted linear neurons.
Theorem 7 (Phase transition in Haar data) Suppose that the planted neuron w∗ ∈ Rd, w∗ ⁄= 0 is ﬁxed and
X∈ Rn×d is a Haar distributed random matrix. Denote W∗ = (w∗, 0,..., 0). For n > 2d, with probability at least
1− exp(−αn), W∗ is the unique optimal solution to (11), where α = (n/2−d)264n2 . For n <2d, with probability at least
1− exp(−αn), W∗ is not the unique optimal solution to (11).
Similar to our previous analysis for the Gaussian distribution, if Xw∗≥ 0, then W∗ = (w∗, 0,..., 0) is not the
unique optimal solution to (3). However, if Xw∗≥ 0 is not satisﬁed, for n > d, W∗ can still be the unique optimal
solution of (3).
3) Relation between Haar data and normalization layers: Consider the minimum norm interpolation problem of
two-layer ReLU networks with skip connection and normalization layer (before ReLU)
min
W1,w2,α
(
‖W1‖22 +‖w2‖22 +‖α‖22{,
s.t. y = Nα1(Xw1,1)w2,1 +
m
i=2
(Nαi(Xw1,i))+w2,i.
(21)
The above problem can be reformulated as a convex program [12]:
min
w0,{wj,w′j}pj=1

‖w0‖2 +
p
j=1
(‖wj‖2 +‖w′j‖2)
(
(,
s.t. Uw0 +
p
j=1
DjU(wj− w′j) = y,
(2Dj− In)Uwj≥ 0, (2Dj− In)Uw′j≥ 0,j ∈ [p],
(22)
where the matrix U is computed from the compact SVD of X = UΣVT . Therefore, the training problem with Gaussian
random data with an additional normalization layer before the ReLU activation is equivalent to the training problem
with Haar data with no normalization layers.

14
4) Sub-Gaussian random data: Our previous results on Gaussian and Haar data can be extended to a broad class
of random matrices with independent entries. In the following result, we show that for i.i.d., sub-Gaussian data
distributions, ReLU neural networks with a skip connection recovers a planted linear model exactly with suﬃciently
many samples.
Theorem 8 Suppose that each entryxi,j of the data matrix X∈ Rn×d is an i.i.d. symmetric random variable following a
mean-zero sub-Gaussian distribution with variance proxy σ2 and E[x2i,j] = 1n. Then, (NIC-L) holds when n≥C1d log(n)
with probability at least 1−4 exp(−C2n)−2 exp(d) for suﬃciently largen, whereC1,C 2 are absolute constants depending
only on σ2.
We note that there exists an additional logarithmic term in the scalingn≥C1d log(n) provided in Theorem 8, compared
to our results on Gaussian and Haar data matrices.
C. Uniform (Strong) Recovery of All Linear Models
Thus far, we considered the recovery of a ﬁxed planted neuron and the associated exact recovery probability. To
ensure the recovery of all possible planted neurons w∗ simultaneously, we introduce the following stronger form of
NIC9L specialized to column orthogonal matrices by requiring (orth-NIC-L) to hold for every w∗:
max
h∈Rd, h⁄=0
‖‖XTdiag(I(Xh≥ 0))X‖‖2 < 1. (ortho-SNIC-L)
For a diagonal arrangement patternDj,‖XTDjX‖2 < 1 is equivalent toXTDjX≺ Id or, equivalently,XT (In−Dj)X≻
0. As X is column orthonormal, this is also equivalent to tr( In− Dj)≥d, or equivalently, tr(Dj)≤n−d. Therefore,
(ortho-SNIC-L) can be simpliﬁed for column orthogonal matrices as
(orth9SNIC9L) max
h∈Rd, h⁄=0 tr(diag(I(Xh≥ 0)))≤n−d. (23)
Theorem 9 Suppose that X∈ Rn×d is a Haar distributed random matrix. Letθ∗ > 0 be the unique solution of the scalar
equation θ + 12∞F−1χ2 (1−2θ)rdFχ2(r) = 12, where Fχ2(r) is the cumulative distribution function (CDF) of a χ2-random
variable with 1 degree of freedom. Then, for suﬃciently large n,d satisfying dn < θ∗, the orth9SNIC9L given in (23)
holds with high probability.
Remark 3 It can be computed that θ∗ ≈ 0.1314 and ( θ∗)−1 ≈ 7.613 by numerically solving the scalar equation
θ + 12∞F−1χ2 (1−2θ)rdFχ2(r) = 12. This implies that when n> 7.613d, the orth 9SNIC9L shown in (23) holds w.h.p.
D. Inexact/Noisy Linear Recovery
In this section, we consider inexact or noisy observations y = Xw∗ + z, where z∈ Rn is an arbitrary disturbance
component. We will show that the optimal NN only learns a linear model when the regularization parameter β is
chosen from an appropriate interval. This can be understood intuitively as follows: when β is too small, the NN trained
with insuﬃcient norm penalty overﬁts to the noise. On the other hand, when β is too large, the NN underﬁts the
observations as the norms of the parameters are over-penalized.
For two-layer ReLU networks with skip connection and normalization layer before the ReLU, the regularized training
problem (6) can be equivalently cast as the convex program (see e.g., [2, 6]):
min
w0,{wj,w′j}pj=1
‖‖‖Uw0 + p
j=1
DjU
(
wj− w′j{− y‖‖‖22 +β(‖w0‖2 + pj=1(‖wj‖2 +‖‖w′j‖‖2{{
s.t. (2 Dj− In)Uwj≥ 0,j ∈ [p], (2Dj− In)Uw′j≥ 0,j ∈ [p],
(24)
where U is computed from the compact SVD of X = UΣVT .
As a direct corollary of Theorem 1 in [6], the global optima of the nonconvex regularized training problem (6) are
given by the optimal solutions of (24) up to permutation and splitting (see Appendix B for details). By dropping all
inequality constraints, the convex program (24) reduces to the following group-Lasso problem:
min
{wj}pj=0
‖‖‖ p
j=0
DjUwj− y
‖‖‖2
2
+β
p
j=0
‖wj‖2. (25)
As we show next, the convex NN objective (24) inherits recovery properties from its group-Lasso relaxation above. The
following two theorems show that for suﬃciently large n, with a suitable choice of the regularization parameter β, the
optimal neural network learns only a linear component. In addition, the 𝓁2 distance between the optimal solution and
the embedded neuron can be bounded by a linear function of β.

15
Theorem 10 Suppose that the entries of the data matrixX is i.i.d. sub-Gaussian with variance proxyσ2 as in Theorem 8
and the noisy observation takes the form y = Xw∗ + z. Assume that the weight decay regularization parameter satisﬁes
β ∈
[
‖z‖2 7(η−‖z‖2)η−7‖z‖2 ,η−‖ z‖2
]
, the norm of the noise component satisﬁes ‖z‖2 ≤ 114η, where η ≜ ‖‖ΣVTw∗‖‖2 and
n≥ max{4000σ2d log(54n), 1024d}. Then, with probability at least 1− 4 exp(−n/8000σ2)− 2 exp(−d), the optimal
solutions to convex programs (24) and (25) consist of only a linear neuron and no ReLU neurons, i.e., there exists w
such that W = (w, 0,..., 0) is strictly optimal. As a consequence, the non-convex weight decay regularized objective (6)
has the same strictly optimal solutions up to permutation and splitting. Furthermore, we have the 𝓁2 distance upper
bound ‖‖w− ΣVTw∗‖‖2≤ βηη−‖ z‖2 +‖z‖2.
Here,η satisﬁes (1− 1/16)‖w∗‖2≤η≤ (1 + 1/16)‖w∗‖2 with probability 1− 2 exp(−d). Moreover, the optimal weights
of the neural network f(X; Θ) = Nα1(Xw1,1)w2,1 +∑mi=2 (Nαi(Xw1,i))+ w2,i are given by w1,1 = µw,α 1 = w2,1 =√
‖Xw‖2 and w1,j = 0,αj = w2,j = 0 for 2≤j≤n, where µ> 0 is an arbitrary constant.
Remark 4 (Estimating the regularization coeﬃcient) In practice, it may be appropriate to assume the noise
component z follows an i.i.d. sub-Gaussian distribution with zero mean. Under this assumption, we can control the
term‖z‖2 with high probability using classical concentration bounds. From the triangle inequality, we note that‖‖y‖2∈ [η−‖ z‖2,η +‖z‖2]. Thus, we can estimate η using the interval η∈[(‖y‖2−‖ z‖2{+,‖y‖2 +‖z‖2], and use η
to compute the required inverval for β in Theorem 10.
E. Recovering a ReLU Neuron
Now we focus on recovering a single planted ReLU neuron. We consider the case where the training data matrix X
is composed of i.i.d. standard Gaussian variables N (0, 1/n). The following theorem illustrates that when n> 2d, the
NNIC91 will hold with high probability. In other words, ReLU NNs with normalization layer optimizing the objective
(9) uniquely recovers the ReLU neuron with high probability.
Theorem 11 Let w∗ ∈ Rd is a ﬁxed unit-norm vector. Suppose that each entry of X are i.i.d. random variables
following the Gaussian distribution N (0, 1/n). Let Di∗ = diag(I(Xw∗≥ 0)). Then, when n >2d, the NNIC91 given
in (NNIC-k) holds with probability at least 1− exp
(
− 16(n−2dn {2n{.
The above result shows that a single normalized ReLU neuron is uniquely recovered by ReLU NN with normalization
layer via (9) (up to permutation and splitting) and its convex reformulation (13), regardless of the number of neurons
in the NN. In other words the set of global optimum of (9) only consists of networks with only a single non-zero ReLU
neuron along with permutations and split versions of this neuron.
Remark 5 We note that the recovery condition for a single ReLU neuron and a linear neuron is the same using ReLU
NNs with normalization layer and is given by nd≥ 2.
VI. Asymptotic analysis
In this section, we present an asymptotic analysis of the Neural Isometry Conditions when n goes to inﬁnity while
d is ﬁxed. While our analysis in Section V provides sharp estimates on the recovery threshold for a single linear or
ReLU neuron, the asymptotic analysis in this section proves the recovery of multiple ReLU neurons.
We begin with the case of two planted ReLU neurons in the asymptotic setting. Forw, v∈ Rd, recall our notation for
the cosine angle betweenw and v given by cos∠(w, v) = wT v‖w‖2‖v‖2 . In order to show that the NNIC92 in (NNIC-k) holds,and consequently two-neuron recovery succeeds via ReLU NNs with normalization layer, we calculate the asymptotic
limit of the left-hand-side in (NNIC-k) when k = 2, which is given by
T :=
‖‖‖‖‖UTj [Us1 Us2][UTs1Us1 UTs1Us2UTs2Us1 UTs2Us2]−1[ ˜w1˜w2]‖‖‖‖‖2. (26)
We consider the case of w1, w2 satisfying cos ∠(w1, w2) =−1 and cos ∠(w1, w2) = 0 for simplicity.
Proposition 8 Suppose that each entry of X∈ Rn×d is an i.i.d. random variable following the normal distribution
N (0, 1/n). Suppose that y = (Xw1)+‖(Xw1)+‖2 + (Xw2)+‖(Xw2)+‖2 is the planted model, where w1, w2∈ Rd. Let D1 = diag(I(Xw1≥
0)) and D2 = diag(I(Xw2≥ 0)). Consider any diagonal arrangement pattern Dj = diag(I(Xhj≥ 0)). Consider the
random variable T deﬁned in (26).
• Suppose that cos ∠(w1, w2) =−1. Let γ = cos ∠(w1, hj). As n→∞ , T converges in probability to a univariate
function g1(γ). Here g1(γ)≤ 1 and the equality holds if and only γ = 1 or γ =−1.

16
• Suppose that cos ∠(w1, w2) = 0 . Let γ1 = cos ∠(w1, hj) and γ2 = cos ∠(w2, hj). As n→ ∞, T converges in
probability to a bivariate function g2(γ1,γ 2). Here g2(γ1,γ 2)≤ 1 and the equality holds if and only (γ1,γ 2) = (1, 0)
or (γ1,γ 2) = (0, 1).
Therefore, in both of the above cases, we haveT≤ 1 asn→∞ and consequently theNNIC92 holds. Moreover, the planted
two-neuron NN is the unique optimal solution to (7) (up to permutation and splitting) and its convex reformulation
(13).
We validate this asymptotic behavior in Figure 5. It can be observed that the recovery threshold for two ReLU
neurons is approximately n≥ 4d when w1 = e1 and w2 = e2, i.e., cos ∠(w1, w2) = 0 in Figure 5(a). In addition, it
can be observed that the recovery threshold for three ReLU neurons is approximately n≥ 6d.
(a) k = 2, w∗1 = e1, w∗2 = e2,
 (b) k = 3, w∗i = ei(i = 1, 2, 3)
Fig. 5: The empirical probability of successful recovery of the planted normalized ReLU neurons by solving the group
𝓁1-minimization problem (14) over 5 independent trials. The label vector y is generated by a planted ReLU NN with
k neurons.
Similar to the ReLU networks with the normalization layer, we present asymptotic analysis of plain ReLU networks.
Proposition 9 Suppose that each entry of X∈ Rn×d is an i.i.d. random variable following the normal distribution
N (0, 1/n). Let Di = diag(I(Xw∗≥ 0)). Consider any hyperplane arrangement Dj = diag(I(Xhj ≥ 0)) such that
cos ∠(w∗, hj) =:γ <1. Deﬁne
R :=
‖‖‖XTDjDiX(XTDiX{−1 ˆw‖‖‖2, (27)
where ˆw = w∗‖w∗‖2 . Then, as n→∞ ,R converges in probability tog(γ). Here the function g : [−1, 1]→ R monotonicallyincreases on [−1, 1] and g(1) = 1.
This implies that asymptotically, as n→∞ , the NIC 91 given in (NIC-1) holds, and plain ReLU NNs recover a single
planted ReLU neuron.
VII. Numerical experiments
In this section, we present numerical experiments on ReLU networks with skip connection and normalization layer
to validate our theoretical results on phase transitions in diﬀerent NN architectures. We provide the illustration of our
main results in this section and provide additional numerical results for various settings in Appendix L. The code is
available at https://github.com/pilancilab/Neural-recovery
Numerical results are divided into three parts: the ﬁrst part consists of phase transition graphs for the recovery rate
when the observation is noiseless by solving convex NN problems in (12) and (14). The second and third part consist
of phase transition graphs for certain types of distance measures when the observation is noisy by solving convex NN
problems and the regularized training problem (convex and non-convex), respectively.
A. ReLU networks with skip connection
We start with phase transition graphs for successful recovery of the planted neuron by solving the convex optimization
problem (12). We compute the recovery rate for d ranging from 10 to 100 and n ranging from 10 to 400. For each

17
pair of (n,d ), we generate 5 realizations of random training data matrices and solve the convex problem (12) on each
dataset. We test for four types of randomly generated data matrices:
• Gaussian: each entry xi,j of X∈ Rn×d is an i.i.d. random variable following the normal distribution N (0, 1/n).
• cubic Gaussian: each element xi,j of X∈ Rn×d satisﬁes xi,j =z3i,j, where zi,j are i.i.d. random variable following
N (0, 1/n).
• Haar: X∈ Rn×d is drawn uniformly random from the set of column orthonormal matrices. We note that a Haar
matrix can be generated by sampling an i.i.d. Gaussian matrix as above and extracting its d left singular vectors
of dimension n.
• whitened cubic Gaussian: X∈ Rn×d is drawn non-uniformly from the set of column orthonormal matrices the
matrix of left singular vectors of X′ ifn>d and the matrix of right singular vectors of X′ ifn<d . Here X′∈ Rn×d
is a cubic Gaussian data matrix.
In each recovery problem, the planted neuron w∗ is either a random vector followingN (0, Id) or chosen as the smallest
right singular vector of X as speciﬁed. In numerical experiments, we use a random subsetH′ of the setH of all possible
hyperplane arrangements to approximate the solution of the convex program. Here H′ is generated by
H′ ={diag(I(Xhi))|hi∈ Rd,i∈ [˜n]},
where hi is an i.i.d. random vector following the standard normal distribution N (0, Id) and ˜n = max(n, 50). On the
other hand, from our theoretical analysis, the recovery will fail if there exists an all-ones hyperplane arrangement, i.e.,
In∈H . However, as H′ is a random subset of H, it might not be easy to validate In∈H by examining whether
In∈H′ is satisﬁed. Therefore, we solve the following feasibility problem before solving the convex problem (12).
max
w∈Rd,t∈R t
s.t.‖w‖2≤ 1, Xw≥t1n.
(28)
If the optimal value of the above problem is strictly greater than zero, there must exist an all-ones hyperplane
arrangement, i.e.,∃w : Xw >0. In this case, we add In to the subset H′. Otherwise, such an arrangement pattern
does not exist.
In Figure 6, we present the phase transition graph for the probability of successful recovery when the planted neuron
w∗ is randomly generated from N (0, Id). The boundaries indicate a phase transition between n = 2d and n = 3d. In
Appendix L-A, we will show similar phase transition graphs when the planted neuron w∗ is the smallest right singular
vector of X in Figure 18.
The second part is phase transition under noisy observation, i.e., y = Xw∗ +z, where z∼N (0,σ 2/n). We still focus
on the convex problem (12), i.e., the convex optimization formulation of gated ReLU networks with skip connection.
Here we focus on Gaussian data and choose w∗ as the smallest right singular vector of X. We deﬁne the following two
types of distance for the solution of the convex program to evaluate the performance.
• Absolute distance: the 𝓁2 distance between the linear term w0 and w∗.
• Test distance: generate a test set ˜X with the same distribution as X, then the prediction of the learned model is
˜y = ˜Xw0 +
P
j=1
( ˜Xwj)+.
Then the test distance is deﬁned as the 𝓁2 distance between the prediction ˜y and the ground truth y∗ = ˜Xw∗.
The boundaries of red regions in Figure 7, which represents highly unsuccessful recovery, remain around n = 2d for
various noise levels σ. When σ increases, the area of dark blue regions of small absolute distance/test error gradually
vanishes. This implies that the linear part of the neural network no longer approximates the planted linear neuron
and the gated ReLU neurons ﬁt the noise. In Appendix L-A, we will observe the same pattern for absolute distance in
Figure 19
In the third part, we study the generalization property of ReLU networks with skip connections using convex/non-
convex training methods. Results for the convex training methods are provided in Appendix L-A.
For the nonconvex training method, we solve the regularized non-convex training problem (6) with β = 10−6 as
an approximation of the minimum norm problem (7). We set the number of neurons to be m = n + 1 and train the
ReLU neural network with skip connection for 400 epochs. We use the AdamW optimizer and set the weight decay
to be β = 10−6. We note that the nonconvex training may still reach local minimizers. Thus, the absolute distance
to the planted linear neuron does not show a clear phase transition as the convex training. However, the transitions
of test error generally follow the patterns of the group 𝓁1-minimization problem. In Figure 8, we show that the test
error increases as n/d increases, and the rate of increase becomes sharper around n = 2d (the boundary of orange and
yellow region).

18
(a) Gaussian
 (b) Cubic Gaussian
(c) Haar
 (d) Whitened cubic Gaussian
Fig. 6: The probability of successful recovery of the planted linear neuron by solving the group𝓁1-minimization problem
(12) over 5 independent trials. The black lines represent the boundaries of successful recovery with probability 1. Here
the planted neuron w∗ is randomly generated from N (0, Id).
B. Multi-neuron recovery and irrepresentability condition
In this subsection, we analyze the recovery for ReLU networks with normalization layer. Results for single-neuron
recovery can be found in Appendix L-B. Here we focus on the case where the label vector is the combination of several
normalized ReLU neurons. We will test for three types of planted neurons.
• k = 2, w∗1 = w∗, w∗2 =−w∗, where w∗∼U (Sn−1). In this case, the hyperplane arrangements of two neurons do
not intersect.
• k = 2, w∗1, w∗2∼U (Sn−1). It is a general case where the hyperplane arrangements of two neurons can intersect.
• k≥ 2, w∗i = ei, where ei is the i-th standard basis in Rn.
We consider the noisy observation model, i.e., the observation is the combination of several normalized ReLU neurons
and Gaussian noise, i.e.,
y =
k
i=1
(Xw∗i )+
‖(Xw∗i )+‖2 + z,
where z∼N (0,σ 2/n).
As a performance metric, the absolute distance is deﬁned as
( k∑
i=1
‖wsi− ˜w∗i‖22
{1/2
.
In Figure 9, we show the phase transition graph when the planted neurons satisfy w∗1 = w∗, w∗2 =−w∗, w∗∼
U(Sn−1). Results for the other two cases can be found in Appendix L-C.

19
(a) σ = 0(noiseless)
 (b) σ = 0.05
(c) σ = 0.1
 (d) σ = 0.2
Fig. 7: Averaged absolute distance to the planted linear neuron by solving the group 𝓁1-minimization problem (12)
derived from training ReLU networks with skip connection over 5 independent trials.
(a) σ = 0(noiseless)
 (b) σ = 0.05
(c) σ = 0.1
 (d) σ = 0.2
Fig. 9: Averaged absolute distance to the planted normalized ReLU neurons by solving the convex problem (14) from
training ReLU networks with normalization layer over 5 independent trials. Here we set k = 2 planted neurons which
satisfy w∗1 = w∗, w∗2 =−w∗, w∗∼U (Sn−1).

20
(a) σ = 0(noiseless)
 (b) σ = 0.05
(c) σ = 0.1
 (d) σ = 0.2
Fig. 8: Averaged test error by training ReLU networks with skip connection on the regularized non-convex problem
(6) over 10 independent trials.
It is also worth noting that we check the NIC 9k given in (NIC-k), which guarantees recovery for the convex problem
(13) and (14). We compute the probability that the NIC holds for d ranging from 10 to 80 and n ranging from 10 to
400 with 50 independent trials. For each pair of (n,d ). For each data matrix X∈ Rn×d, we use a random subset H′ of
the set H\HS to validate the inequality (NIC-k), where H is the set of all possible hyperplane arrangements and HS
is the set of hyperplane arrangements generated by the planted neurons, i.e.
HS ={diag(I(Xw∗i ))|i∈ [k]}.
In numerical experiments, we generate random hyperplane arrangements. If (NIC-k) holds for all Dj∈H′, we say X
satisﬁes the NIC 9k numerically.

21
(a) k = 2, w∗1 = w∗, w∗2 =−w∗, w∗∼U (Sn−1)
 (b) k = 2, w∗1, w∗2∼U (Sn−1)
(c) k = 2, w∗1 = e1, w∗2 = e2,
 (d) k = 3, w∗i = ei(i = 1, 2, 3)
Fig. 10: The probability that the irrepresentability condition (NIC-k) holds for the group 𝓁1-minimization problem (14)
over 50 independent trials. The label vector y is the combination of several normalized ReLU neurons.
VIII. Conclusion
We presented a framework to analyze recovery properties of ReLU neural networks through convex reparameter-
izations. We introduced Neural Isometry Conditions, which are deterministic conditions on the training data that
ensure the recovery of planted neurons via training two-layer ReLU networks and the variants with skip connection and
normalization layers. Viewing the non-convex neural network training problem from a convex optimization perspective,
we establish theorems analogous to sparse recovery and compressed sensing by using probabilistic methods. For
randomly generated training data matrices, we showed the existence of a sharp phase transition in the recovery of
simple planted models. Interestingly, ReLU neural networks with an arbitrary number of neurons exactly recover
simple planted models, such as a combination of few ReLU neurons, when the number of samples exceed a critical
threshold. Therefore, these models can perfectly generalize even with an extremely large number of parameters when
the labels are generated by simple models. This phenomenon not only aligns with the results developed in sparse
recovery theory, but is also validated by our numerical experiments. Namely, when the training data is i.i.d. Gaussian
and the number of data points is smaller than a critical threshold, the convex program cannot recover the planted
model. On the other hand, when the number of data points is above a critical threshold, the solution of the convex
optimization problem uniquely recovers the planted solution. Our main contribution is that we explicitly characterize
the data isometry conditions that imply exact recovery of planted ReLU and linear neurons, and the speciﬁc relation
between the number of data points and problem dimensions for random data matrices for successful recovery with high
probability. We also extend our results to the case where the observation is noisy, and show that the neural network
can still learn a simple model, even with an arbitrary number of neurons, when the noise component is not too large
and the regularization parameter lies in an appropriate interval.
An immediate open problem is extending our results to neural networks of depth greater than two, and investigating
modern DNN structures such as convolutional and transformer layers. Moreover, the analysis of the exact recovery

22
threshold for an arbitrary number of ReLU neurons is an important open problem. Our numerical experiments suggest
the trend n≥ 2k for recovering k ReLU neurons when the training matrix is composed of i.i.d. Gaussian random
variables. Finally, we note that non-convex training methods might get stuck at local minimizers or stationary points
that are avoided by the convex formulation. The relationship between convex and non-convex training process should be
further revealed to explain this phenomenon. We leave the analysis of non-convex training process when the observation
is derived from a simple model as an open research problem for future work.

23
Appendix A
Review of linear sparse recovery via 𝓁1 minimization
We brieﬂy review conditions required to ensure recovery via 𝓁1-norm minimization in the linear observation case.
Suppose that y = Xw∗ denotes linear observations, where the matrix X∈ Rn×d represents measurements and w∗∈ Rd
is a k-sparse vector of dimension d. Consider the following 𝓁1-minimization problem to recover w∗ from measurements
y:
min
w∈Rd
‖w‖1 s.t. Xw = y. (29)
It can be shown that w∗ can be exactly recovered from y when the data matrix X satisﬁes certain isometry condi-
tions, which are analogous to the ones developed in this work. The KKT optimality conditions of the above convex
optimization problem are
∃λ∈ Rn s.t. |λTxcolj |≤ 1, for wj = 0,
λTxcolj = sign(wj), for wj⁄= 0, (30)
whereλ∈ Rn is a dual variable and xcolj ∈ Rd denotes the j-th column of X.
Let S ={i∈ [d]|w∗i⁄= 0} denote the support set of w∗ and Sc = [n]/S its complement. For the support set S⊆ [d]
of size |S|, denote the subvector of w∗ that corresponds to entries restricted to S as wS = (wi)i∈S∈ R|S|, and the
submatrix XS∈ Rn×|S| of X formed with the columns S that correspond to the support of w. The irrepresentability
condition is a simpler suﬃcient condition that implies that the KKT conditions in (30) hold for w = w∗. This is
ensured by the choice λ∗ = arg minλ : XTS λ=sign(w∗S)‖λ‖2 = XS(XTSXS)−1sign(w∗S) assuming that XTSXS is invertible,and leads to the condition
‖XTScXS(XTSXS)−1sign(w∗S)‖∞ < 1. (31)
Intuitively, the above condition is expected to hold under three conditions: (i) the matrix (XTSXS)−1 is well-conditioned,
(ii) the columns of X have small inner-products with each other, i.e., ‖XTScXS‖∞,∞ is small, and (iii) the size of the
subset S is not too large. Moreover,the irrepresentability condition in (31) also ensures that w∗ is the unique optimal
solution to (29) [7].
The Restricted Isometry Property (RIP) is a stronger condition that imposes well-conditioning of submatrices
uniformly over all size-k subsets. RIP is stated as follows
(1−δk)‖wS‖22≤‖ XSwS‖22≤ (1 +δk)‖wS‖22, ∀wS∈ R|S|, ∀S⊆ [d] : |S|≤ k
whereδk∈ (0, 1) is the Restricted Isometry Constant for some positive integerk. RIP implies that alln×|S| submatrices
of X∈ Rn×d are well-conditioned for all subsetsS of size at mostk. Examples of matrices that satisfy the RIP property
include i.i.d. sub-Gaussian random matrices, random Haar matrices, as well subsampled orthonormal systems, e.g.,
Fourier and Hadamard matrices under conditions on the dimensions n and d, see details in [9, 44]. In [45], it has been
shown that RIP with a suﬃciently small constant δk implies the irrepresentability condition, and hence the recovery
of a linear k-sparse vector from the observations y = Xw∗.
Appendix B
Permutation and splitting of neural networks
In this section, we present the deﬁnition of permutation and splitting of two-layer ReLU neural networks and their
variants with skip connections or normalization layers.
For a ReLU network Θ = ( W1, w2) where W1 ∈ Rd×m, w2 ∈ Rm, a permutation of Θ is any neural network
Θ′ = (W′1, w′2) with W′1∈ Rd×m, w′2∈ Rm such that w′1,j = w1,π(j) andw′2,j =w2,π(j) forj∈ [m]. Hereπ : [m]→ [m]
is a permutation of [m].
Given a neuron-pair ( w1,w 2), we say that a collection of neuron-pairs {(w1,j,w 2,j)}kj=1 is a splitting of ( w1,w 2) if
(w1,j,w 2,j) = (√γjw1,√γjw2) for some γj≥ 0 and ∑kj=1γj = 1. Given a ReLU neural network Θ = ( W1, w2) with
W1∈ Rd×m, w2∈ Rm, a splitting of Θ is any neural network Θ ′ = (W′1, w′2) with W′1∈ Rd×m′, w′2∈ Rm′ such that
the non-zero neurons of Θ′ can be partitioned into splittings of the neurons of Θ.
For a ReLU network with skip connection Θ = (W1, w2) where W1∈ Rd×m, w2∈ Rm, the permutation and splitting
of this network refers to the permutation and splitting of the ReLU neurons ( w1,i,w 2,i)mi=2 in this network.
For a ReLU network with normalization layer Θ = ( W1, w2,α) where W1∈ Rd×m, w2,α∈ Rm, a permutation of
Θ is any neural network Θ′ = (W′1, w′2,α′) such that w′1,j = w1,π(j), w′2,j =w2,π(j) and α′j =απ(j) for j∈ [m]. Here
π : [m]→ [m] is a permutation of [ m].
Given a neuron-pair ( w1,w 2,α ), we say that a collection of neuron-pairs {(w1,j,w 2,j)}kj=1 is a splitting of ( w1,w 2)
if (w2,j,αj) = (√γjw2,√γjα) for some γj ≥ 0 and ∑kj=1γj = 1 and w1,j is positively colinear with w1 for j ∈
[m]. Namely, there exists ζj > 0 such that w1,j = ζjw1,j. Given a ReLU neural network with normalization layer

24
Θ = ( W1, w2,α) with W1 ∈ Rd×m, w2,α∈ Rm, a splitting of Θ is any neural network Θ ′ = ( W′1, w′2,α′) with
W′1∈ Rd×m′, w′2,α′∈ Rm′ such that the non-zero neurons of Θ ′ can be partitioned into splittings of the neurons of
Θ.
Appendix C
Justification for excluding the hyperplane arrangement induced by the zero vector
Consider ˜H ={diag(I(Xh≥ 0))|h∈ Rd}. Firstly, we note that In = diag(I(Xh≥ 0)). If In∈ H, then we have˜H =H. If In /∈H, then this implies that {w∈ Rd : (2In− In)Xw≥ 0} ={0}. Therefore, excluding the hyperplane
arrangement induced by h = 0 does not change the convex program (8).
Appendix D
The convex program for gated ReLU networks
Consider the minimum norm interpolation problem
min
Θ
1
2
(
‖W1‖2F +‖w2‖22{, s.t. fgReLU(X; Θ) = y, (32)
where fgReLU(X; Θ) deﬁned in (10) is the output of a gated ReLU network. We ﬁrst reformulate (32) in the following
way.
Proposition 10 The problem (32) can be reformulated as
min
Θ
‖w2‖1, s.t. fgReLU(X; Θ) = y,‖w1,i‖2≤ 1,i∈ [m]. (33)
For the reformulated problem (33), we can derive the dual problem.
Proposition 11 The dual problem of (33) is given by
max
λ
λTy, s.t. max
‖w‖2≤1,h⁄=0
⏐⏐⏐λTdiag(I(Xh≥ 0))Xw⏐⏐⏐≤ 1. (34)
Based on the hyperplane arrangement described in (2), the dual problem is also equivalent to
max
λ
λTy, s.t. max
j∈[p],‖w‖2≤1
⏐⏐⏐λTDjXw⏐⏐⏐≤ 1 = maxλ λTy, s.t. ‖‖XTDjλ‖‖2≤ 1,j ∈ [p]. (35)
Indeed, the bi-dual problem (dual of the dual problem (34)) is the group Lasso problem (9).
Proposition 12 The dual of the problem (34) is the group Lasso problem (9). For a suﬃciently large m, the minimum
norm interpolation problem (32) is equivalent to (9).
A. Proof of Proposition 10
Proof Fori∈ [m], consider ˆw1,i =αiw1,i and ˆw2,i =α−1i w2,i, where αi > 0. Let ˆΘ = ( ˆW1, ˆW2, H). Then, we note
that fgReLU(X; Θ) = fgReLU(X; ˆΘ). This implies that ˆΘ is feasible for (32). From the inequality of arithmetic and
geometric mean, we note that
1
2
m
i=1
(
α2i‖w1,i‖22 +α−2i w22,i{≥ m
i=1
‖w1,i‖2|w2,i|. (36)
The equality is achieved when αi =
∑
|w2,i|
‖w1,i‖2 . As the scaling operation does not change ∑mi=1‖w1,i‖2|w2,i|, we can set
‖w1,i‖2 = 1 and then the lower bound of the objective value becomes ∑mi=1|w2,i| =‖w2‖1. This completes the proof.
B. Proof of Proposition 11
Consider the Lagrangian function
L(W1, w2, H,λ) =‖w2‖1 +λT
(
y−
m
i=1
diag(I(Xhi≥ 0))Xw1,iw2,i
(
. (37)
The problem (32) is equivalent to
min
W1,w2,H
max
λ
L(W1, w2, H,λ), s.t.‖w1,i‖2≤ 1, hi⁄= 0,i∈ [m]
= min
W1,H
max
λ
min
w2
L(W1, w2, H,λ), s.t.‖w1,i‖2≤ 1, hi⁄= 0,i∈ [m]
= min
W1,H
max
λ
λTy−
m
i=1
˜I(
⏐⏐⏐λTdiag(I(Xhi≥ 0))Xw1,i⏐⏐⏐≤ 1),
s.t.‖w1,i‖2≤ 1, hi⁄= 0,i∈ [m].
(38)

25
Here ˜I(S) = 0 if the statement S is correct and ˜I(S) = +∞ otherwise. By exchanging the order of min and max, we
obtain the dual problem
max
λ
min
W1,H
λTy−
m
i=1
˜I(
⏐⏐⏐λTdiag(I(Xhi≥ 0))Xw1,i⏐⏐⏐≤ 1), s.t.‖w1,i‖2≤ 1, hi⁄= 0,i∈ [m]
= max
λ
λTy, s.t. max
‖w1,i‖2≤1,hi⁄=0
⏐⏐⏐λTdiag(I(Xhi≥ 0))Xw1,i⏐⏐⏐≤ 1,i∈ [m]
= max
λ
λTy, s.t. max
‖w‖2≤1,h⁄=0
⏐⏐⏐λTdiag(I(Xh≥ 0))Xw⏐⏐⏐≤ 1.
(39)
C. Proof of Proposition 12
Proof As the group lasso problem (9) is a convex problem, it is suﬃcient to show that the dual problem of (9) is
exactly (34). Consider the Lagrangian function
L(w1,..., wp,λ) =
p
j=1
‖wj‖2 +λT (y−
p
j=1
DjXwj). (40)
The dual problem follows
max
λ
min
w1,...,wp
L(w1,..., wp,λ) = maxλ λTy, s.t. ‖‖XTDjλ‖‖2≤ 1,j ∈ [p], (41)
which is equivalent to (34). This implies that the optimal value of (9) serves as a lower bound for (32). For a suﬃciently
large m, any feasible point ( w1,..., wp) to (9) also corresponds to a feasible neural network for (32). In this case, the
minimum norm interpolation problem (32) is equivalent to (9).
Appendix E
Proofs in Section II
A. Proof of Lemma 1
Proof Let m∗ be the minimal number of neurons of the optimal solution to the convex program (3). Similar to the
proof of Theorem 1 in [6], assuming that m≥ m∗, for any globally optimal solution to the non-convex problem (7),
we can merge its ReLU neurons into a minimal neural network deﬁned in [6]. This minimal neural network combining
with the linear part corresponds to an optimal solution to the convex program (3). Therefore, we can view this globally
optimal neural network as a possibly split and permuted version of an optimal solution to the convex program (3). For
the case where y = Xw∗, the ReLU network with skip connection can represent y using the linear part. In this case,
m∗ = 1.
B. Proof of Proposition 1
Proof We ﬁrst show that the linear neural isometry condition implies the recovery of the planted linear model by
solving (12).
Proposition 13 Suppose that the linear neural isometry condition (NIC-L) holds. Consider W∗ = (w∗0,..., w∗p) such
that w∗0 = w∗ while w∗j = 0 for j⁄= 0. Then, W∗ is the unique optimal solution to (12).
Proof The KKT conditions for (12) consist of
‖‖‖XTDjλT‖‖‖≤ 1, if wj = 0,
XTDjλT = wj‖wj‖, if wj⁄= 0,
p
j=0
DjXwj = y.
(42)
As a direct corollary of Proposition 14, W∗ is the unique optimal solution to (12).
We then present the proof of Proposition 1. As (12) is derived by dropping all inequality constraints in (3), the optimal
value of (8) is lower bounded by (12). Note that W∗ is the unique optimal solution to (12). Hence, the optimal value
of (12) is ‖w∗‖2. On the other hand, ˆW is feasible for (3) and it leads to an objective value of ‖w∗‖2. This implies
that ˆW is an optimal solution to (3) and the optimal values of (3) and (12) are the same. Suppose that we have
another solution ¯W which is optimal to (3). Consider ˘W ={ ˘wj|j = 0, 1,...,p } where ˘w0 = ˜w0 and ˘wj = ¯wj− ¯w′j for

26
j = 1,...,p . Then, ¯W is also optimal to (12). As W∗ is the unique optimal solution to (9), this implies that ¯W = W∗.
Hence, we have ¯w0 = ¯w0 = w∗. For j = 1, 2,...,p , we have
‖ ¯wj‖2 +‖ ¯w′j‖2≥ 0 =‖w∗j‖2. (43)
The equality holds when ¯wj = ¯w′j = 0. As ¯W is optimal to (3), we have ¯wj = ¯w′j = 0 for j = 1,...,p . This implies
that ¯W = ˆW. Thus, ˆW is the unique optimal solution.
Appendix F
Proofs in Section III
A. Proof of Theorem 3
Proof Letm∗ be the minimal number of neurons of the optimal solution to the convex program (8). In the case there
are multiple optimal solutions, we may take the one with minimal cardinality. We can view the minimal norm problem
(7) as
min
Θ
𝓁(f(X; Θ);y) +R(Θ), (44)
where the loss function is deﬁned by
𝓁(z; y) =
{
0, z = y,
+∞, z⁄= y.
Hence, by applying Theorem 1 in [6], for m≥ m∗, any globally optimal solutions of the non-convex problem (7) of
ReLU networks can be computed via the optimal solutions of the convex program (8) up to splitting and permutation.
For the case y = (Xw∗)+, we have m∗ = 1.
B. Proof of Theorem 4
Proof Because y = Xw∗‖Xw∗‖2 , the ReLU network with skip connection can represent y using m∗ = 1 neurons. LetT1,..., Tq be the enumeration of all possible diagonal arrangement patterns
{diag(sign(Xw))|w∈ Rd, w⁄= 0}.
We denote Qi be closed convex cone of solution vectors for sign( Xw) = Ti for i∈ [q]. Let Bi = Qi× R>0 and
Bi+q = Qi× R<0 for i∈ [q]. Similar to the deﬁnition of minimal neural networks in [6], we can deﬁne the minimal
neural networks with normalization layer as follows:
• We say that a ReLU neural network with normalization layer Θ = ( W1, w2,α ) is minimal if (i) it is scaled, i.e.,
|w2,i| =|αi| (ii) for each cone Bi wherei∈ [2q], the minimal neural network has at most a single non-zero neuron
(w1,j,w 2,j,αj) such that ( w1,j,w 2,jαj)∈Bi.
Similar to the proof of Theorem 1 in [6], for any globally optimal solution to the non-convex problem (7), we can
merge it into a minimal neural network with normalization layer. This minimal neural network corresponds to an
optimal solution to the convex program (13). Therefore, we can view this globally optimal neural network as the split
and permuted version of an optimal solution to the convex program (13).
Appendix G
Proofs in Section IV
To begin with, consider a general group 𝓁1-minimization problem
min
{wj}kj=1
k
j=1
‖wj‖2, s.t.
k
j=1
Ajwj = y, (45)
where Aj∈ Rn×rj and wj∈ Rrj for j∈ [k]. The KKT condition follows
‖‖ATjλ‖‖2≤ 1, if wj = 0,
ATjλ = wj‖wj‖2, if wj⁄= 0,
k
j=1
Ajwj = y,
(46)

27
whereλ∈ Rn is the dual variable. Suppose that y = Ai∗w∗ is the label vector, where w∗∈ Rsi∗ . Assume that ATi∗Ai∗
is invertible. Then, the irrepresentability condition follows
‖‖‖‖ATj Ai∗(ATi∗Ai∗)−1 w∗‖w∗‖2‖‖‖‖2 < 1,∀j⁄=i∗. (47)
Proposition 14 Let y = Ai∗w∗. Suppose that the irrepresentability condition (47) holds. Consider W∗ = (w∗1,..., w∗k)
such that w∗i∗ = w∗ while w∗j = 0 for j⁄=i∗. Then, W∗ is the unique optimal solution to (45).
Proof We ﬁrst show that W∗ is the optimal solution to (45). Let
λ = Ai∗
(
ATi∗Ai∗{−1 w∗‖w∗‖2.
We can examine that ATi∗λ = w∗‖w∗‖2 . For j⁄=i∗, from the irrepresentability condition (47), we have
‖‖ATjλ‖‖2 =‖‖‖‖ATj Ai∗(ATi∗Ai∗)−1 w∗‖w∗‖2‖‖‖‖2 < 1.
Therefore, (W∗,λ) satisﬁes the KKT condition (46). This implies that W∗ is optimal to (45).
Then, we prove the uniqueness. Suppose that W = (w1,..., wk) is another optimal solution to (9). Denote ∆j = wj
for j⁄=i∗ and ∆i∗ = wi∗− w∗i∗. Then, we have
j⁄=i∗
Aj∆j + Ai∗∆i∗ = 0. (48)
We note that
‖wi∗‖2 +

j⁄=i∗
‖wj‖2
≥‖w∗i∗‖2 +
( w∗i∗
‖w∗i∗‖2
{T
∆i∗ +

j⁄=i∗
‖wj‖2
=‖w∗i∗‖2 +λTAi∗∆i∗ +
j⁄=i∗
‖∆j‖2
=‖w∗i∗‖2−λT 
j⁄=i∗
Aj∆j +

j⁄=i∗
‖∆j‖2
≥‖w∗i∗‖2 +
j⁄=i∗
‖∆j‖2
(
1−
‖‖ATjλ‖‖2{≥‖ w∗i∗‖2
(49)
The equality holds when ∆ j = 0 for all j⁄= i∗ and ∆i∗ = γ w∗i∗‖w∗i∗‖2 for certain γ≥ 0. This implies that W∗ is theunique optimal solution to (9).
Consider the following weak irrepresentability condition
‖‖ATj Ai∗(ATi∗Ai∗)−1w∗‖‖2 < 1,j ∈S1,‖‖ATj Ai∗(ATi∗Ai∗)−1w∗‖‖2 = 1,j ∈S2, (50)
where S1∪S2 = [k]/{i∗}. We have the following results when the weak irrepresentability condition holds.
Proposition 15 Suppose that the weak irrepresentability condition holds. Consider W∗ = ( w∗1,..., w∗k) such that
w∗i∗ = w∗ while w∗j = 0 for j⁄=i∗. Then, W∗ is an optimal solution to (45). All optimal solutions W = (w1,..., wk)
shall satisfy wj = 0 for j∈S1.
Proof Similar to the proof of Proposition 14, we can show that W∗ is the optimal solution to (45). Suppose that
W = (w1,..., wk) is another optimal solution to (9). Denote ∆ j = wj forj⁄=i∗ and ∆i∗ = wi∗− w∗i∗. Then, we have

j⁄=i∗
Aj∆j + Ai∗∆i∗ = 0. (51)

28
We note that
‖wi∗‖2 +

j⁄=i∗
‖wj‖2
≥‖w∗i∗‖2 +
( w∗i∗
‖w∗i∗‖2
{T
∆i∗ +

j⁄=i∗
‖wj‖2
=‖w∗i∗‖2 +λTAi∗∆i∗ +
j⁄=i∗
‖∆j‖2
=‖w∗i∗‖2−λT 
j⁄=i∗
Aj∆j +

j⁄=i∗
‖∆j‖2
≥‖w∗i∗‖2 +
j⁄=i∗
‖∆j‖2
(
1−
‖‖ATjλ‖‖2{
≥‖w∗i∗‖2.
(52)
The equality holds when ∆ j = 0 for all j∈S1 and ∆i∗ =γ w∗i∗‖w∗i∗‖2 for certain γ≥ 0. This completes the proof.
We then consider the case where y =∑li=1 Asiw∗si, where S ={s1,...,s l}⊆ [k]. Denote AaugS =
)
)
ATs1
...
ATsk
(
[. Suppose
that AaugS (AaugS )T =:
)
])
ATs1As1 ... ATs1Ask
... ... ...
ATskAs1 ... ATskAsk
(
[ is invertible. Then, the irrepresentability condition follows
‖‖‖‖‖‖‖ATj (AaugS )T (AaugS (AaugS )T )−1)])w∗s1/‖‖w∗s1‖‖2...w∗s1/‖‖w∗sk‖‖2([‖‖‖‖‖‖‖2 < 1,∀j /∈S. (53)
or equivalently, ‖‖‖‖‖‖‖ATj (AaugS )†)])w∗s1/‖‖w∗s1‖‖2...w∗s1/‖‖w∗sk‖‖2([‖‖‖‖‖‖‖2 < 1,∀j /∈S. (54)
Proposition 16 Suppose that the irrepresentability condition (53) holds. Consider ˆW∗ = ( ˆw∗1,..., ˆw∗k) such that
ˆw∗i = w∗i for i∈S while w∗j = 0 for j /∈S. Then, ˆW∗ is the unique optimal solution to (45).
Proof We ﬁrst show that ˆW∗ is the optimal solution to (45). Let
λ = (AaugS )T (AaugS (AaugS )T )−1
)
])
w∗s1/‖‖w∗s1‖‖2
...
w∗s1/‖‖w∗sk‖‖2
(
[.
We can examine that ATiλ = w∗i‖w∗i‖2 fori∈S. Forj /∈S, from the irrepresentability condition (53), we have‖‖ATjλ‖‖2 <1. Therefore, (W∗,λ) satisﬁes the KKT condition (46). This implies that W∗ is optimal to (45).
Then, we prove the uniqueness. Suppose that W = (w1,..., wk) is another optimal solution to (9). Denote ∆ j =
wj− ˆw∗j for j∈ [k]. Then, we have 
j/∈S
Aj∆j +

i∈S
Ai∆i = 0. (55)

29
We note that 
i∈S
‖wi‖2 +

j/∈S
‖wj‖2
≥

i∈S
‖ ˆw∗i‖2 +
i∈S
( ˆw∗i
‖ ˆw∗i‖2
{T
∆i +

j/∈S
‖wj‖2
=

i∈S
‖ ˆw∗i‖2 +λT
i∈S
Ai∆i +

j/∈S
‖∆j‖2
=

i∈S
‖ ˆw∗i‖2−λT
j/∈S
Aj∆j +

j/∈S
‖∆j‖2
≥

i∈S
‖ ˆw∗i‖2 +
j/∈S
‖∆j‖2
(
1−
‖‖ATjλ‖‖2{
≥

i∈S
‖ ˆw∗i‖2.
(56)
The equality holds when ∆ j = 0 for all j /∈S and ∆i =γi w∗i∗‖w∗i∗‖2 for i∈S. Here γi≥ 0 for i∈S. As ∆j = 0 for allj /∈S, we have 
i∈S
Ai∆i = 0. (57)
Note that
)
])
ATs1As1 ... ATs1Ask
... ... ...
ATskAs1 ... ATskAsk
(
[ is invertible. This implies that ∆i = 0 for i∈S. Hence, ˆW∗ is the unique optimal
solution to (9).
A. Proof of Proposition 2
Proof We ﬁrst show that the neural isometry condition (NIC-1) implies the recovery of the planted model via (9).
Proposition 17 Suppose that the neural isometry condition (NIC-1) holds. Consider W∗ = (w∗1,..., w∗p) such that
w∗i∗ = w∗ while w∗j = 0 for j⁄=i∗. Then, W∗ is the unique optimal solution of (9).
Proof The KKT conditions for (9) include
‖‖‖XTDjλT‖‖‖≤ 1, if wj = 0,
XTDjλT = wj‖wj‖, if wj⁄= 0,
p
j=1
DjXwj = y,
(58)
whereλ∈ Rn is the dual variable. As a direct corollary of Proposition 14, W∗ is the unique optimal solution to (9).
Then, we present the proof of Proposition 2. As (9) is derived by dropping all inequality constraints in (8), the optimal
value of (8) is lower bounded by (9). As W∗ is the unique optimal solution to (9), the optimal value of (9) is ‖w∗‖2.
On the other hand, ˆW is feasible for (8) and it leads to an objective value of‖w∗‖2. This implies that ˆW is an optimal
solution to (8) and the optimal values of (8) and (9) are the same. Suppose that we have another solution ¯W which
is optimal to (8). Consider ˘W ={ ˘wj|j∈ [p]} where ˘wj = ¯wj− ¯w′j. Then, ˘W is also optimal to (9). As W∗ is the
unique optimal solution to (9), this implies that ˘W = W∗. Then, we note that for j⁄=i∗,
‖ ¯wj‖2 +‖ ¯w′j‖2≥ 0 =‖w∗j‖2. (59)
The equality holds when ¯wj = ¯w′j = 0. We also note that ¯wi∗− ¯w′i∗ = w∗. This implies that
‖ ¯wi∗‖2 +‖ ¯w′i∗‖2≥‖ ¯wi∗− ¯w′i∗‖2 =‖w∗‖2. (60)
The equality holds if and only if there exists α∈ [0, 1] such that ¯wi∗ = αw∗ and ¯w′i∗ =−(1−α)w∗. If α = 1, then¯W = W∗. If α < 1, as (2 Di∗− In)X ¯w′i∗ ≥ 0 and (2 Di∗− In)Xw∗≥ 0, this implies that (2 Di∗− In)Xw∗ = 0.
Therefore, we have Xw∗ = 0 and XTXw∗ = 0. This leads to a contradiction because w∗⁄= 0 and XTX is invertible
with probability 1 for n>d .

30
B. Proof of Proposition 3
Proof We ﬁrst show that the normalized neural isometry condition implies the the recovery of the planted model via
(13).
Proposition 18 Suppose that the neural isometry condition (NIC-L) holds. Consider W∗ = (w∗0,..., w∗p) such that
w∗i∗ = Σi∗Vi∗w∗‖Σi∗Vi∗w∗‖2 while w∗j = 0 for j⁄=i∗. Then, W∗ is the unique optimal solution to (14).
Proof We note that
y = (Xw∗)+
‖(Xw∗)+‖2 = Di∗Xw∗‖Di∗Xw∗‖2 = Ui∗Σi∗Vi∗w∗‖Ui∗Σi∗Vi∗w∗‖2 = Ui∗w∗i∗.
The KKT conditions for (14) include ‖‖‖UjλT‖‖‖≤ 1, if wj = 0,
UTjλT = wj‖wj‖, if wj⁄= 0,
p
j=1
Ujwj = y,
(61)
As a direct corollary of Proposition 14, W∗ is the unique optimal solution to (14).
We then present the proof of Proposition 3. As (14) is derived by dropping all inequality constraints in (13), the optimal
value of (13) is lower bounded by (14). As W∗ is the unique optimal solution to (14), the optimal value of (14) is 1.
On the other hand, ˆW is feasible for (8) and it leads to an objective value of 1. This implies that ˆW is an optimal
solution to (13) and the optimal values of (13) and (14) are the same. Suppose that we have another solution ¯W which
is optimal to (13). Consider ˘W ={ ¯wj|j∈ [p]} where ˘wj = ¯wj− ¯w′j. Then, ˘W is also optimal to (14). As W∗ is the
unique optimal solution to (14), this implies that ˘W = W∗. Then, we note that for j⁄=i∗,
‖ ¯wj‖2 +‖ ¯w′j‖2≥ 0 =‖w∗j‖2. (62)
The equality holds when ¯wj = ¯w′j = 0. We also note that
‖ ¯wi∗‖2 +‖ ¯w′i∗‖2≥‖ ¯wi∗− ¯w′i∗‖2 =‖w∗i∗‖2. (63)
The equality holds if and only if there exists α∈ [0, 1] such that ¯wi∗ =αw∗ and ¯w′i∗ =−(1−α)w∗i∗. If α = 1, then¯W = ¯W. If α < 1, as (2 Di∗− In)XVTi Σ−1i ¯w′i∗ ≥ 0 and (2 Di∗− In)XVTi Σ−1i w∗i∗ ≥ 0, this implies that (2 Di∗−
In)XVTi Σ−1i w∗i∗ = 0. Therefore, we have XVTi Σ−1i w∗ = 0 and XTXVTi Σ−1i w∗i∗ = 0. This leads to a contradiction
because VTi Σ−1i w∗⁄= 0 and XTX is invertible with probability 1 for n>d .
C. Proof of Proposition 4
Proof We ﬁrst show that the neural isometry condition (NIC-k) implies the recovery of the planted model by solving
(9).
Proposition 19 Consider ˜W∗ = ( ˜w∗1,..., ˜w∗p) satisﬁes that ˜w∗si = r∗i w∗i for i∈{ 1,...,k } and ˜w∗j = 0 for j /∈ S.
Suppose that the neural isometry condition (NIC-k) is satisﬁed. Then, ˜W∗ is the unique optimal solution to (14).
Proof The KKT conditions for (9) consist of
‖‖‖DjXλT‖‖‖≤ 1, if ˜wj = 0,
DjXTλT = ˜wj‖ ˜wj‖, if ˜wj⁄= 0,
p
j=1
DjX ˜wj = y,
(64)
As a direct corollary of Proposition 16, ˜W∗ is the unique optimal solution to (9).
We then present the proof of Proposition 4. From Proposition 19, we note that ˜W∗ is the unique optimal solution to
(14). As (9) is derived by dropping all inequality constraints in (8), the optimal value of (8) is lower bounded by (9).
As ˜W∗ is the unique optimal solution to (9), the optimal value of (9) is ∑ki=1‖w∗i‖2. On the other hand, ˆW is feasible
for (8) and it leads to an objective value of ∑ki=1‖w∗i‖2. This implies that ˆW is an optimal solution to (8) and the
optimal values of (8) and (9) are the same.

31
Suppose that we have another solution ¯W which is optimal to (8). Consider ˘W ={ ˘wj|j∈ [p]} where ˘wj = ¯wj− ¯w′j.
Then, ¯W is also optimal to (9). As W∗ is the unique optimal solution to (9), this implies that ˘W = W∗, or equivalently,
¯wj− ¯w′j = ˜wj for j∈ [p]. Then, we note that for j /∈S
‖ ¯wj‖2 +‖ ¯w′j‖2≥ 0 =‖w∗j‖2. (65)
The equality holds when ¯wj = ¯w′j = 0. For i∈ [k], we have ¯wsi− ¯w′si = ˜wsi =r∗i w∗i . This implies that
‖ ¯wsi‖2 +‖ ¯w′i‖2≥‖ ¯wi− ¯w′i‖2 =‖w∗i‖2. (66)
The equality holds if and only if there exists α∈ [0, 1] such that ¯wsi =αr∗i w∗i and ¯w′si =−(1−α)r∗i w∗i . If 0 <α< 1,
as (2 Dsi− In)X ¯w′si ≥ 0 and (2 Dsi− In)X ¯wsi ≥ 0, this implies that (2 Dsi− In)Xw∗i = 0. Therefore, we have
Xw∗i = 0 and XTXw∗i = 0. This leads to a contradiction because w∗i ⁄= 0 and XTX is invertible with probability 1
for n > d. If r∗i = 1, then α = 1. Otherwise, we have α = 0 and this leads to ¯w′si =−w∗i , which is contradictory
to (2Dsi− In)X ¯w′si ≥ 0. If r∗i =−1, similarly, we have α = 0. Otherwise, it follows that α = 1 and this leads to
¯wsi =−w∗i , which is contradictory to (2 Dsi− In)X ¯wsi≥ 0.
D. Proof of Proposition 5
Proof We ﬁrst show that the neural isometry condition (NNIC-k) implies the recovery of the planted model by solving
(14).
Proposition 20 Consider ˜W∗ = ( ˜w∗1,..., ˜w∗p) satisﬁes that ˜w∗i = r∗i ΣsiVsiw∗i‖ΣsiVsiw∗i‖2 for i∈ S and ˜w∗j = 0 for j /∈ S.
Suppose that the neural isometry condition (NNIC-k) is satisﬁed. Then, ˜W∗ is the unique optimal solution to (14).
Proof We note that for i∈ [k], we have
(Xw∗i )+
‖(Xw∗i )+‖2 = DsiXw∗i‖DsiXw∗i‖2 = UsiΣsiVsiw∗i‖UsiΣsiVsiw∗i‖2 = Usir∗i ˜w∗i.
This implies that
y =
k
i=1
r∗i (Xw∗i )+‖(Xw∗i )+‖2 = ki=1 Usiw∗i ˜w∗i.
The KKT conditions for (14) consist of
‖‖‖UjλT‖‖‖≤ 1, if ˜wj = 0,
UTjλT = ˜wj‖ ˜wj‖, if ˜wj⁄= 0,
p
j=1
Uj ˜wj = y,
(67)
As a direct corollary of Proposition 16, ˜W∗ is the unique optimal solution to (14).
We then present the proof of Proposition 4. From Proposition 16, ˜W∗ is the unique optimal solution to (14). Because
(14) is derived by dropping all inequality constraints in (13), the optimal value of (13) is lower bounded by (14). As
˜W∗ is the unique optimal solution to (14), the optimal value of (14) is k. On the other hand, ˆW is feasible for (13)
and it leads to an objective value of k. This implies that ˆW is an optimal solution to (13) and the optimal values of
(13) and (14) are the same.
Suppose that we have another solution ¯W which is optimal to (8). Consider ˘W ={ ˘wj|j∈ [p]} where ˘wj = ¯wj− ¯w′j.
Then, ¯W is also optimal to (9). As W∗ is the unique optimal solution to (9), this implies that ˘W = W∗, or equivalently,
¯wj− ¯w′j = ˜wj for j∈ [p]. Then, we note that for j /∈S
‖ ¯wj‖2 +‖ ¯w′j‖2≥ 0 =‖w∗j‖2. (68)
The equality holds when ¯wj = ¯w′j = 0. For i∈ [k], we have ¯wsi− ¯w′si = ˜wsi =r∗i ΣiViw∗i‖ΣiViw∗i‖2 . This implies that
‖ ¯wsi‖2 +‖ ¯w′i‖2≥‖ ¯wi− ¯w′i‖2 = 1. (69)
The equality holds if and only if there existsα∈ [0, 1] such that ¯wsi =αr∗i ΣsiVsiw∗i‖ΣsiVsiw∗i‖2 and ¯w′si =−(1−α)r∗i ΣsiVsiw∗i‖ΣsiVsiw∗i‖2 .
If 0 < α < 1, as (2 Dsi− In)XVTsiΣ−1si ¯w′si ≥ 0 and (2 Dsi− In)X ¯XVTsiΣ−1si wsi ≥ 0, this implies that (2 Dsi−
In)XVTsiΣ−1si w∗i = 0. Therefore, we have XVTsiΣ−1si w∗i = 0 and XTXVTsiΣ−1si w∗i = 0. This leads to a contradiction
because VTsiΣ−1si w∗i⁄= 0 and XTX is invertible with probability 1 for n>d . If r∗i = 1, then we have α = 1. Otherwise,

32
we have α = 0 and this leads to ¯w′si =− ΣsiVsiw∗i‖ΣsiVsiw∗i‖2 , which is contradictory to (2 Dsi− In)XVTsiΣ−1si ¯w′si ≥ 0. If
r∗i = −1, similarly, we have α = 0. Otherwise, we have α = 1 and this leads to ¯wsi = − ΣsiVsiw∗i‖ΣsiVsiw∗i‖2 , which is
contradictory to (2Dsi− In)XVTsiΣ−1si ¯wsi≥ 0.
Appendix H
Proofs in Section V
A. Proof of Lemma 2
Proof We ﬁrst illustrate Theorem 1 in [1] as follows:
Theorem 12 Fix a tolerance η∈ (0, 1). Let C and K be convex cones in Rn. Draw a random orthogonal basis W∈
Rn×n. Then,
P (K\ WC⁄={0})
{
≤η δ (C) +δ(K)≤n−aη
√n,
≥ 1−η δ (C) +δ(K)≥n +aη
√n. (70)
whereaη = 8
√
log(4/η).
We can take C =
{
t
[w
0
]
|t≥ 0
}
, where 0∈ Rn−d is a vector of 0s. Then, P (Xw∈ K) = P (WC\K ⁄={0}).
As w(C) = d, for w(K) +d < n, we have aη = n−δ(K)−d√n . This implies that η = 4e− (n−δ(K)−d)264n . Hence, by taking
α = (n−δ(K)−d)264n2 , (18) holds. Similarly, forδ(K)+d>n , we haveaη = w(K)+d−n√n , which implies thatη = 4e− (n−δ(K)−d)264n .
By taking α = (n−δ(K)−d)264n2 , (18) holds
B. Proof of Theorem 8
Proof We ﬁrst note that the matrix in the irrepresentability condition (NIC-L) has the following upper bound
max
h∈Rd:h⁄=0
‖‖‖XTdiag(I(Xh≥ 0))X(XTX{−1‖‖‖
2
≤ 1σ2min maxh∈Rd:h⁄=0‖XTdiag(I(Xh≥ 0))X‖2,
where σmin is the smallest singular value of X. We introduce a lemma to bound the norm of XTdiag(I(Xh≥ 0))X.
Lemma 3 Let h∈ Rd and t > 0 be ﬁxed. Suppose that each element xi,j of X∈ Rn×d are i.i.d. random variables
following a mean-zero sub-Gaussian distribution with variance proxy σ2 such that
• E[x2i,j] = 1n.
• −xi,j has the same distribution as xi,j.
Then, for d≥ 2, with probability at least
1− 4 exp
(
− nt2
162
√
2σ2 + d log(54n)2 {
we have
max
h∈Rd,h⁄=0‖XTdiag(I(Xh≥ 0))X‖2≤ 12 +t. (71)
From Lemma 3, by taking t = 1/4, for n≥ 4000σ2d log(54n), we have
P
(
max
h∈Rd:h⁄=0‖XTdiag(I(Xh≥ 0))X‖2≤ 34{≥ 1− 4 exp(− n8000σ2{. (72)
On the other hand, from Theorem 4.6.1 in [44], we can lower bound the smallest eigenvalue of X,
P
(
σmin≥ 1− 2
√
d
n
(
≥ 1− 2 exp(−d). (73)
Forn≥ 1024d. we have
P
(
σ2min≥ 7/8{≥P (σmin≥ 1− 1/16)≥P
(
σmin≥ 1− 2
√
d
n
(
≥ 1− 2 exp(−d). ‘ (74)
This implies that for n satisfying n ≥ max{1024d, 4000σ2d log(54n)}, with probability at least 1 − 2 exp(−d)−
4 exp
(
− n8000σ2
{
, we have
max
j∈[p]
‖‖‖XTDjX(XTX{−1‖‖‖2≤ 34σ2min≤ 34· 87 < 1. (75)

33
Conditioned on the above event, we note that for any w∗∈ Rd, w∗⁄= 0, we have
max
h∈Rd:h⁄=0
‖‖‖‖XTdiag(I(Xh≥ 0))X(XTX{−1 w∗‖w∗‖2‖‖‖‖2≤ maxh∈Rd:h⁄=0‖‖‖XTdiag(I(Xh≥ 0))X(XTX{−1‖‖‖2 < 1, (76)
i.e., the irrepresentability condition (NIC-L) holds. This completes the proof.
C. Proof of Lemma 3
Proof For a positive semi-deﬁnite matrix A∈ Rd×d, we have‖A‖2 = maxz∈Rd:‖z‖2=1 zTAz. Note that⏐⏐⏐⏐ maxh∈Rd,h⁄=0‖XTdiag(I(Xh≥ 0))X‖2− 12⏐⏐⏐⏐
=
⏐⏐⏐⏐⏐ maxh∈Rd,h⁄=0‖‖‖‖‖ ni=1 xixTi I(hTxi≥ 0))‖‖‖‖‖2− 12⏐⏐⏐⏐⏐
=
⏐⏐⏐⏐⏐ maxz,h∈Rd:‖z‖2=1,h⁄=0 ni=1 zTxixTi zI(hTxi≥ 0))− 12⏐⏐⏐⏐⏐
≤ max
z,h∈Rd:‖z‖2=1,h⁄=0
⏐⏐⏐⏐⏐ ni=1(zTxi)2I(hTxi≥ 0))− 12⏐⏐⏐⏐⏐.
(77)
By rescaling xi =√nxi, we can rewrite the above quantity as
max
z,h∈Rd:‖z‖2=1,h⁄=0
⏐⏐⏐⏐⏐ 1n ni=1(zTxi)2I(hTxi≥ 0))− 12⏐⏐⏐⏐⏐. (78)
As−xi,j has the same distribution as xi,j, we have
P (hTxi≥ 0) =P (hTxi≤ 0),
E[(zTxi)2|hTxi≥ 0] = E[(−zTxi)2|hT (−xi)≥ 0] = E[(zTxi)2|hTxi≤ 0]. (79)
We note that E[(zTxi)2] =‖z‖22 = 1 and
E[(zTxi)2] = E[(zTxi)2|hTxi≥ 0]P (hTxi≥ 0) + E[(zTxi)2|hTxi≤ 0]P (hTxi≤ 0). (80)
This implies that E[(zTxi)2|hTxi≥ 0]P (hTxi≥ 0) = 12, or equivalently,
E[(zTxi)2I(hTxi≥ 0)] = 12. (81)
Therefore, it is suﬃcient to upper-bound the following probability
P
(
max
z,h∈Rd:‖z‖2=1,h⁄=0
⏐⏐⏐⏐⏐ 1n ni=1(zTxi)2I(hTxi≥ 0)− 12⏐⏐⏐⏐⏐≥t( (82)
We note that
P
(
max
z,h∈Rd:‖z‖2=1,h⁄=0
⏐⏐⏐⏐⏐ 1n ni=1(zTxi)2I(hTxi≥ 0)− E) 1n ni=1(zTx′i)2I(hTx′i≥ 0)[⏐⏐⏐⏐⏐≥t(
·P
(
max
z,h∈Rd:‖z‖2=1,h⁄=0
⏐⏐⏐⏐⏐ 1n ni=1(zTxi)2I(hTxi≥ 0)− E) 1n ni=1(zTx′i)2I(hTx′i≥ 0)[⏐⏐⏐⏐⏐≥t(
≥P
(
max
z,h∈Rd:‖z‖2=1,h⁄=0
⏐⏐⏐⏐⏐ 1n ni=1(zTxi)2I(hTxi≥ 0)− 1n ni=1(zTx′i)2I(vTx′i≥ 0)⏐⏐⏐⏐⏐≥ 2t(.
(83)
where x′i are i.i.d. random vectors following the same distribution of xi and they are independent with x1,..., xn. This
implies that
P
(
max
z,h∈Rd:‖z‖2=1,h⁄=0
⏐⏐⏐⏐⏐ 1n ni=1(zTxi)2I(hTxi≥ 0)− E) 1n ni=1(zTx′i)2I(hTx′i≥ 0)[⏐⏐⏐⏐⏐≥t(
≤P
(
max
z,h∈Rd:‖z‖2=1,h⁄=0
⏐⏐⏐⏐⏐ 1n ni=1(zTxi)2I(hTxi≥ 0)− 1n ni=1(zTx′i)2I(vTx′i≥ 0)⏐⏐⏐⏐⏐≥ 2t( 12 , (84)

34
By introducing i.i.d. random variables ϵi uniformly distributed in {−1, 1}, we have the following bound
P
(
max
z,h∈Rd:‖z‖2=1,h⁄=0
⏐⏐⏐⏐⏐ 1n ni=1(zTxi)2I(hTxi≥ 0)− 1n ni=1(zTx′i)2I(hTx′i≥ 0)⏐⏐⏐⏐⏐≥ 2t(
=P
(
max
z,h∈Rd:‖z‖2=1,h⁄=0
⏐⏐⏐⏐⏐ 1n ni=1ϵi((zTxi)2I(hTxi≥ 0)− (zTx′i)2I(hTx′i≥ 0){⏐⏐⏐⏐⏐≥ 2t(
=P
(
max
z,h∈Rd:‖z‖2=1,h⁄=0
⏐⏐⏐⏐⏐ 12n 2ni=1ϵi(zTxi)2I(hTxi≥ 0)⏐⏐⏐⏐⏐≥t(,
(85)
where ϵn+1,...,ϵ 2n are i.i.d. copies of ϵ1,...,ϵ n.
Decoupling: Next, we apply a decoupling result in [46, Theorem 3.4.1] to obtain the following upper bound:
P
(
max
z,h∈Rd:‖z‖2=1,h⁄=0
⏐⏐⏐⏐⏐ 12n 2ni=1ϵi(zTxi)2I(hTxi≥ 0)⏐⏐⏐⏐⏐≥t(
≤8P
(
max
z,h∈Rd:‖z‖2=1,h⁄=0
⏐⏐⏐⏐⏐ 12n 2ni=1ϵi(zTxi)2I(hTx′i≥ 0)⏐⏐⏐⏐⏐≥t( , (86)
were{x′i}2ni=1 is an independent and identically distributed copy of the sequence {xi}2ni=1.
ϵ-net bound: For each realization of x′1,..., x′2n, let P′ ={diag(I(X′h≥ 0))|h∈ Rd, h⁄= 0}, p′ =|P′| and we
writeP′ ={D1,..., Dp′}. According to [42], we have the upper bound p′≤ 2d(2en/d)d. We note that
max
z,h∈Rd:‖z‖2=1,h⁄=0
⏐⏐⏐⏐⏐ 12n 2ni=1ϵi(zTxi)2I(hTx′i≥ 0)⏐⏐⏐⏐⏐ = maxj∈[p′] maxz∈Rd:‖z‖2=1⏐⏐⏐⏐⏐ 12n 2ni=1ϵi(zTxi)2(Dj)i,i⏐⏐⏐⏐⏐ (87)
Consider an ϵ-net of {z∈ Rd :‖z‖2 = 1},{z1,..., zN}, where N≤ (1 + 2/ϵ)d. Namely, for any z∈ Rd satisfying
‖z‖2 = 1, there exists k∈ [N] such that z = zk + ∆, where‖∆‖2≤ϵ. Then, we have
max
z∈Rd:‖z‖2=1
⏐⏐⏐⏐⏐ 12n 2ni=1ϵi(zTxi)2(Dj)i,i⏐⏐⏐⏐⏐
≤ max
k∈[N],‖∆‖2≤ϵ
⏐⏐⏐⏐⏐ 12n 2ni=1ϵi((zk + ∆)Txi)2(Dj)i,i⏐⏐⏐⏐⏐
≤ max
k∈[N]
⏐⏐⏐⏐⏐ 12n 2ni=1ϵi(zTk xi)2(Dj)i,i⏐⏐⏐⏐⏐ + (2ϵ +ϵ2) max‖z‖2≤1⏐⏐⏐⏐⏐ 12n 2ni=1ϵi(zTxi)2(Dj)i,i⏐⏐⏐⏐⏐
(88)
Here we utilize that for an arbitrary symmetric matrix A∈ Rd×d and arbitrary vector z∈ Rd with‖z‖2 = 1,
max
‖∆‖2≤ϵ
|(z + ∆)TA(z + ∆)|≤| zTAz| + (2ϵ +ϵ2)‖A‖2. (89)
This implies that
max
z∈Rd:‖z‖2=1
⏐⏐⏐⏐⏐ 12n 2ni=1ϵi(zTxi)2(Dj)i,i⏐⏐⏐⏐⏐≤ 11− 2ϵ−ϵ2 maxk∈[N]⏐⏐⏐⏐⏐ 12n 2ni=1ϵi(zTk xi)2(Dj)i,i⏐⏐⏐⏐⏐ (90)
For ﬁxed k, we note that zTk xi is also sub-Gaussian with variance proxy σ2. Let gi = (zTk xi)2. Therefore, ϵig2i (Dj)i,i
is sub-exponential with parameters (4
√
2σ2(Dj)i,i, 4σ2). This implies that ∑2ni=1ϵig2i (Dj)i,i is sub-exponential with
parameter (ν∗, 4σ2), where
ν∗ =
/riltp/rilvertex/rilvertex√ 2n
i=1
4
√
2σ2(Dj)i,i =
∑
4
√
2σ2 tr(Dj). (91)
Therefore, for t≤ (ν∗)24σ2 =√2 tr(Dj), we have
P
(⏐⏐⏐⏐⏐ 12n 2ni=1ϵi(zTk xi)2(Dj)i,i⏐⏐⏐⏐⏐>t(≤ 2 exp(−2nt2/(2(ν∗)2){ = 2 exp(− n2t24√2σ2 tr(Dj){≤ 2 exp(− nt24√2σ2{.
This implies that
P
(
max
k∈[N]
⏐⏐⏐⏐⏐ 12n 2ni=1ϵi(zTk xi)2(Dj)i,i⏐⏐⏐⏐⏐>t(≤ 2N exp(− nt24√2σ2{≤ 2 exp(− nt24√2σ2 +d log(3/ϵ){. (92)

35
Again, by applying the union bound, we have
P
(
max
j∈[p′] maxk∈[N]
⏐⏐⏐⏐⏐ 12n 2ni=1ϵi(zTk xi)2(Dj)i,i⏐⏐⏐⏐⏐>t(
≤p′·P
(
max
k∈[N]
⏐⏐⏐⏐⏐ 12n 2ni=1ϵi(zTk xi)2(Dj)i,i⏐⏐⏐⏐⏐>t(
≤2 exp
(
− nt2
4
√
2σ2 +d log(3/ϵ) +d(log(2n)− logd + 1) + log(2d)
{
≤2 exp
(
− nt2
4
√
2σ2 +d log(3/ϵ) +d log(6n)
{
,
(93)
where we assume that d≥ 2. As a result, by taking ϵ = 1/3, we have
P
(
max
z,h∈Rd:‖z‖2=1,h⁄=0
⏐⏐⏐⏐⏐ 1n ni=1(zTxi)2I(hTxi≥ 0)− 12⏐⏐⏐⏐⏐≥t(2
≤8P
(
max
z,h∈Rd:‖z‖2=1,h⁄=0
⏐⏐⏐⏐⏐ 12n 2ni=1ϵi(zTxi)2I(hTx′i≥ 0)⏐⏐⏐⏐⏐≥t(
≤8P
(
max
j∈[p′] maxk∈[N]
⏐⏐⏐⏐⏐ 12n 2ni=1ϵi(zTk xi)2(Dj)i,i⏐⏐⏐⏐⏐> (1− 2ϵ−ϵ2)t(
≤16 exp
(
−nt2(1− 2ϵ−ϵ2)2
4
√
2σ2 +d log(3/ϵ) +d log(6n)
{
=16 exp
(
− nt2
81
√
2σ2 +d log(54n)
{
.
(94)
This completes the proof.
D. Proof of Theorem 5
Proof Without the loss of generality, we can let w∗ satisﬁes that ‖w∗‖2 = 1. As n > 2d, XTX is invertible with
probability 1. Consider the event
E =
{
max
h∈Rd:I(Xh≥0)⁄=1‖XTdiag(I(Xh≥ 0))X(XTX)−1w∗‖2 < 1
}
. (95)
Firstly, we show that
P (E) = 1. (96)
Denote A(h) = XTdiag(I(Xh≥ 0))X and ˜A(h) = (XTX)−1A(h)TA(h)(XTX)−1. We note that A(h) and XTX are
positive semi-deﬁnite and symmetric. As A(h)≽ XTX, we have A(h)TA(h)≼ (XTX)2 and
˜A(h)≼I.
The equality holds if and only if A(h) = XTX. This is equivalent to XTdiag(I(Xh≥ 0)− 1)X = 0, which contradicts
with I(Xh≥ 0)⁄= 1. Hence, we also have
˜A(h)⁄=I.
Recall our notation eigmax
( ˜A(h){ used for the subspace of maximal eigenvectors of the symmetric matrix ˜A(h).
We note that ‖ ˜A(h)w∗‖2 = 1 if and only if ‖ ˜A(h)‖2 = 1 and w∗∈ eigmax( ˜A(h){. As ˜A(h)⁄= In, conditioned on
‖ ˜A(h)‖2 = 1, eigmax( ˜A(h){ is a random subspace with dimension at most d− 1. This implies that
P (‖ ˜A(h)w∗‖2 = 1) =P(‖ ˜A(h)‖2 = 1, w∗∈ eigmax( ˜A(h){{ = 0. (97)
Forσ∈{ 0, 1}n, deﬁne B(σ) = XTdiag(σ)X and ˜B(σ) = (XTX)−1B(σ)TB(σ)(XTX)−1. Then, we have
P
(
max
h∈Rd:I(Xh≥0)⁄=1‖ ˜B(I(Xh≥ 0))w∗‖2 = 1
{
=P
(
max
σ∈{0,1}n:∃h⁄=0,I(Xh≥0)⁄=1,σ=I(Xh≥0)‖ ˜B(σ)w∗‖2 = 1
{
≤

σ∈{0,1}n
P (‖ ˜B(σ)w∗‖2 = 1, I(Xh≥ 0)⁄= 1,σ = I(Xh≥ 0)) = 0.
(98)

36
From the kinematic formula, for n> 2d, we have P (In /∈H)≥ 1− exp(−nα). In this case, the event E implies that
the neural isometry condition (NIC-L) holds. This completes the proof.
E. Proof of Proposition 7
Proof Without the loss of generality, we can let w∗ satisﬁes that ‖w∗‖2 = 1. As n > d, XTX is invertible with
probability 1. Consider the event
E =
{
max
h∈Rd:I(Xh≥0)⁄=1‖XTdiag(I(Xh≥ 0))X(XTX)−1w∗‖2 < 1
}
. (99)
First, we show that
P (E) = 1. (100)
Denote A(h) = XTdiag(I(Xh≥ 0))X and ˜A(h) = (XTX)−1A(h)TA(h)(XTX)−1. We note that A(h) and XTX are
positive semi-deﬁnite and symmetric. As A(h)≼ XTX, we have A(h)TA(h)≼ (XTX)2 and
˜A(h)≼I.
The equality holds if and only if A(h) = XTX. This is equivalent to XTdiag(I(Xh≥ 0)− 1)X = 0, which contradicts
with I(Xh≥ 0)⁄= 1. Hence, we also have
˜A(h)⁄=I.
We note that ‖ ˜A(h)w∗‖2 = 1 if and only if ‖ ˜A(h)‖2 = 1 and w∗∈ eigmax( ˜A(h){. As ˜A(h)⁄= In, conditioned on
‖ ˜A(h)‖2 = 1, eigmax( ˜A(h){ is a random subspace with dimension at most d− 1. This implies that
P (‖ ˜A(h)w∗‖2 = 1) =P(‖ ˜A(h)‖2 = 1, w∗∈ eigmax( ˜A(h){{ = 0. (101)
Forσ∈{ 0, 1}n, deﬁne B(σ) = XTdiag(σ)X and ˜B(σ) = (XTX)−1B(σ)TB(σ)(XTX)−1. Then, we have
P
(
max
h∈Rd:I(Xh≥0)⁄=1‖ ˜B(I(Xh≥ 0))w∗‖2 = 1
{
=P
(
max
σ∈{0,1}n:∃h⁄=0,I(Xh≥0)⁄=1,σ=I(Xh≥0)‖ ˜B(σ)w∗‖2 = 1
{
≤

σ∈{0,1}n
P (‖ ˜B(σ)w∗‖2 = 1, I(Xh≥ 0)⁄= 1,σ = I(Xh≥ 0)) = 0.
(102)
Then, according to Proposition 15, conditioned on the event E, the optimal solution W = (w0,..., wp) to (12) shall
satisfy that wj = 0 for Dj⁄= In. If there does not exist j∈ [p] such that Dj = In, then, W∗ = (w∗, 0,..., 0) is the
unique optimal solution to (12). Thus, it is also the unique optimal solution to (3).
If there exists i∗∈ [p] such that Di∗ = In. Let W = (w0, w1, w′1,..., wp, w′p) be an optimal solution to (3). Let
ˆwj = wj− w′j for j∈ [p]. Then, ˆW = (w0, ˆw1,..., ˆwp) is also optimal to (12). This implies that ˆwj = 0 for j∈ [p]
such that j⁄=i∗. For j∈ [p] such that j⁄=i∗, we have
‖ ˆwj‖2 +‖ ˆw′j‖2≥ 0. (103)
We also note that
X(w0 + wi∗− w′i∗) = Xw∗. (104)
As XTX is invertible, we have w0 + wi∗− w′i∗ = w∗. Thus, we have
‖w0‖2 +‖wi∗‖2 +‖w′i∗‖2≥‖ w∗‖2. (105)
The equality holds when there exists α1,α 2,α 3 ≥ 0 such that α1 +α2 +α3 = 1, w0 = α1w∗, wi∗ = α2w∗ and
w′i∗ =−α3w∗. However, as Xw∗≥ 0 does not hold and Xwi∗≥ 0, Xw′i∗≥ 0, we have α2 =α3 = 0. This implies that
W∗ = (w∗, 0,..., 0) is the unique optimal solution to (12).

37
F. Proof of Theorem 9
Proof Let Kj ={u :Dju≥ 0} and denoteC ={j : tr(Dj)>n −d}. We note that
P
(
max
h∈Rd:h⁄=0 tr(I(Xh≥ 0))≤n−d
{
=P (∃w∈ Rd : Xw∈∪ j∈CKj, w⁄= 0).
(106)
As∪j∈CKj is not a convex set, we cannot directly apply the kinematic formula. Let K = (∪j∈CKj)\Sn−1, where
Sn−1 ={z∈ Rn|‖z‖2 = 1}. It is a closed subset of Sn−1. We give the lower bound of the success probability based on
the Gordon’s escape through a mesh theorem.
Lemma 4 LetK be a closed subset of Sn−1. Deﬁne the Gaussian width of K by:
w(K) = Eg∼N(0,In)
[
max
z∈K
gTz
]
. (107)
Deﬁne ak = Eg∼N(0,Ik)[‖g‖2] for k∈ N. Then, for a n−k dimensional subspace L⊆ Rn drawn at random, we have
P (L\K⁄= ∅)≥ 1− 72e− 118 (ak−w(K)). (108)
Note that Xw is a random d-dimensional subspace of Rn. According to the Gordon’s escape through a mesh theorem,
we have
P (∃w∈ Rd : Xw∈∪ j∈CKj, w⁄= 0)≥ 1− 72e− 118 (an−d−w(K)). (109)
To ensure that there exists w⁄= 0 such that Xw∈∪ j∈CKj with high probability, we require that a2n−d >w (K)2. As
k
k+1k≤a2k≤k, it is suﬃcient to have w(K)2 < n−d. Therefore, it suﬃces to calculate the squared Gaussian width
of K. We can compute that
w(K)2 =
(
E
[
max
j∈C
max
z∈Rn:Djz≥0,‖z‖2=1 gTz
]{2
=
(
E
[
max
j∈C
‖(Djg)+ + ((Dj− In)g)+‖2
]{2
≤E
)(
max
j∈C
‖(Djg)+ + ((Dj− In)g)+‖2
{2[
=E
[
max
j∈C
‖(Djg)+‖22 +‖((Dj− In)g)+‖22
]
.
(110)
By noting that
‖(Djg)+‖22 +‖((Dj− In)g)+‖22
=‖(g)+‖22−‖ ((In− Dj)g)+‖22 +‖((Dj− In)g)+‖22,
we have
E
[
max
j∈C
‖(Djg)+‖22 +‖((Dj− In)g)+‖22
]
=E
[
‖(g)+‖22 + maxj∈C (‖((Dj− In)g)+‖22−‖ ((In− Dj)g)+‖22{]
=n2 + E
)
)max
j∈C

i:(Dj)i,i=0
−sgn(gi)g2i
(
[ = n2 + E
)
max
S⊆[n]:|S|≤d−1

i∈S
sgn(gi)g2i
[
(111)
Let R = sgn(G)G2, where G∼N (0, 1). Denote FR be the CDF of the random variable R. Suppose that d,n →∞
with a ﬁxed ratio d =θn, 1n E[maxS⊆[n]:|S|≤d−1∑i∈S sgn(gi)g2i] will converge to∫ ∞
F−1r (1−θ)
rdFR(r). (112)
We note that
1−FR(r) =P (R≥r) = 12P (G2≥r) = 12(1−Fχ2(r)).
Therefore, we can rewrite (112) as 12∞F−1χ2 (1−2θ)rdFχ2(r). Denote
g(θ) = 12 + 12∫ ∞F−1χ2 (1−2θ)rdFχ2(r) +θ. (113)

38
We note that g(θ) monotonically increases for θ∈ [0, 1/2). By noting that g(0) = 1/2 and g(0.5) = 1.5, there uniquely
exists θ∗∈ (0, 1/2) such that g(θ) = 1. We also note that
lim
n→∞,d=θn
1
n
(
w2(K) +d{ =g(θ). (114)
Therefore, for suﬃciently large n,d with d<nθ , we have w2(K)<n −d, which implies that (23) holds w.h.p..
We present a numerical way to computeg(θ). Denote q =F−1χ2 (1−2θ).By integration by parts, we can compute that
1
2
∫ ∞
q
rdFχ2(r) =−12∫ ∞q rd(1−Fχ2(r))
=− 12r(1−Fχ2(r))|∞q +∫ ∞q (1−Fχ2(r))dr
=qθ + 12∫ ∞q (1−Fχ2(r))dr.
(115)
By the numerical quadrature of the survival function of the χ2 random variable with 1 degree of freedom, we plot g(θ)
in Figure 11. Note that when θ≈ 0.1314, we have g(θ)≈ 1.
Fig. 11: g(θ) as a function of θ in [0, 0.5].
G. Proof of Theorem 7
Proof For h∈ Rd with h⁄= 0, denoteA(h) = XTdiag(I(Xh≥ 0))X. We ﬁrst prove the case wheren< 2d. According
to the kinematic formula, P (∃h∈ Rd : h⁄= 0,A (h) = In)≥ 1− exp−αn, where α = (n/2−d)264n2 . In other words, there
exists an all-ones hyperplane arrangement with probability at least 1 − exp(−nα). In this case, let Dj = In. Construct
˜wi = w′i = 0 if i⁄=j, ˜wj = w∗ and ˜w′j = 0. Then, W′ = (0, ˜w1, ˜w′1,..., ˜wp, ˜w′p) is also a feasible solution to (12).
Then, we consider the case wheren> 2d. We show that with probability at least 1−exp(−αn), the event (orth-NIC-L)
holds. For σ ∈ {0, 1}n, we let B(σ) = XTdiag(σ)X. As XTX = Id, we note that ‖B(σ)w∗‖2 = 1 if and only
if‖B(σ)‖2 = 1 and w∗ ∈ eigmax(B(σ)). For σ∈{ 0, 1}n with σ⁄= 1 and‖B(σ)‖2 = 1, as B(σ)⁄= I, we have
dim(eigmax(B(σ)))≤d−1. This implies that P (w∗∈ eigmax(B(σ)|‖B(σ)‖2 = 1) = 0. Therefore, we have the bound:
P
(
max
h∈Rd:h⁄=0‖A(h)w∗‖2 = 1
{
=P
(
max
σ:∃h⁄=0,σ=I(Xh≥0)
‖B(σ)w∗‖2 = 1
{
≤

σ∈{0,1}n
P (‖B(σ)w∗‖2 = 1,∃h⁄= 0,σ = I(Xh≥ 0))
≤P (∃h⁄= 0, 1 = I(Xh≥ 0)) +

σ∈{0,1}n,σ⁄=1
P (‖B(σ)w∗‖2 < 1)
=P (∃h⁄= 0, 1 = I(Xh≥ 0)).
(116)
According to the kinematic formula, for n> 2d, P (∃h⁄= 0, 1 = I(Xh≥ 0))≤ exp−αn. This implies that
P
(
max
h∈Rd,h⁄=0‖A(h)w∗‖2 < 1
{
= 1−P
(
max
h∈Rd,h⁄=0‖A(h)w∗‖2 = 1
{
≥ 1− exp−αn.
Therefore forn> 2d, the neural isometry condition (orth-NIC-L) holds with probability at least 1−exp(−nα). From
Proposition 13, the neural isometry condition (orth-NIC-L) implies that W is the unique optimal solution to (12).

39
H. Proof of Proposition 21
Proof To ensure that W is an optimal solution to (125), we only require that the KKT conditions (117) at W are
satisﬁed, i.e., ‖‖ATjλ‖‖2≤β, if j⁄=i∗,
ATi∗λ =−β wi∗
‖wi∗‖2
,
Ai∗(wi∗− w∗)− z =λ.
(117)
The last two equations give
ATi∗Ai∗wi∗ +β wi∗
‖wi∗‖2
= ATi∗Ai∗w∗ + ATi∗z. (118)
Let us write wi∗ =rw where r =‖wi∗‖2 and w = wi∗‖wi∗‖2 . Then, the above expression gives
(rATi∗Ai∗ +βI)w = ATi∗Ai∗w∗ + ATi∗z. (119)
As rATi∗Ai∗ +βI is invertible, we obtain an explicit solution for w, i.e.,
w = (rATi∗Ai∗ +βI)−1(ATi∗Ai∗w∗ + ATi∗z).
Because w satisﬁes‖w‖2 = 1, the scalar r shall satisfy
1 =
‖‖(rATi∗Ai∗ +βI)−1(ATi∗Ai∗w∗ + ATi∗z)‖‖2. (120)
Because ATi∗Ai∗ = I, we have r +β =‖w∗ + ATi∗z‖2. This implies that r =‖w∗ + ATi∗z‖2−β. As r≥ 0, we require
that β≤‖ w∗ + ATi∗z‖2. A suﬃcient condition is that β≤‖ w∗‖2−‖ z‖2. We can write the expression of λ as
λ =Ai∗(wi∗− w∗)− z
=Ai∗(ATi∗Ai∗ +β/rI)−1(ATi∗Ai∗w∗ + ATi∗z)− Ai∗w∗− z
= rr +β Ai∗w∗− Ai∗w + rr +β Ai∗ATi∗z− z
=− βr +β Ai∗w∗ +(I− rr +β Ai∗ATi∗{ z.
(121)
Because Ai∗ATi∗ is a projection matrix whose eigenvalues are 0 and 1, we have ‖I−r/(r +β)Ai∗ATi∗‖2≤ 1. Therefore,
for j⁄=i∗, we have the upper bound
‖ATjλ‖2 =
‖‖‖‖− βr +β ATj Ai∗w∗ + ATj (I− rr +β Ai∗ATi∗{ z‖‖‖‖2
≤ βr +β‖ATj Ai∗w∗‖2 +‖Aj‖2‖z‖2
= β‖‖w∗ + ATi∗z‖‖2‖ATj Ai∗w∗‖2 +‖Aj‖2‖z‖2
≤ β‖w∗‖2−‖ ATi∗z‖2‖ATj Ai∗w∗‖2 +‖z‖2
≤ β‖w∗‖2−‖ z‖2‖ATj Ai∗w∗‖2 +‖z‖2
≤β 1−γ1−‖ z‖2/‖w∗‖2 +‖z‖2≤β.
(122)
Here we utilize that ‖Aj‖2≤ 1 and
β≥‖ z‖2
1−‖ z‖2/‖w∗‖2
γ−‖ z‖2/‖w∗‖2. (123)

40
Therefore, it implies that there exists a solution W = ( w1,..., wk) such that w∗j = 0 for j⁄= i∗. In addition, we
provide the upper bound for the 𝓁2 norm‖wi∗− w∗‖2.
‖wi∗− w∗‖2 =‖rw− w∗‖2
=
‖‖‖‖ rr +β(w∗ + ATi∗z{− w∗‖‖‖‖2
≤ βr +β‖w∗‖2 + rr +β‖‖ATi∗z‖‖2
≤ β‖w∗‖2‖‖w∗ + ATi∗z‖‖2 +‖z‖2
≤ β‖w∗‖2
‖w∗‖2−‖ z‖2 +‖z‖2.
(124)
I. Proof of Theorem 10
In order to prove these theorems, we consider a generic group Lasso problem
min
{wj}kj=1
‖‖‖‖‖‖ kj=1 Ajwj− y‖‖‖‖‖‖22 +β kj=1‖wj‖2. (125)
The next result provides a suﬃcient condition on the regularization parameter and the norm of the noise component
to ensure successful support recovery, as well as an estimation of the upper bound on the 𝓁2 distance between the
optimal solution and the embedded neuron.
Proposition 21 Let y = Ai∗w∗ + z, where Ai∗ satisﬁes (Ai∗)TAi∗ = Id. Assume that‖Aj‖2≤ 1 for j⁄=i∗. Suppose
that the following condition holds.
max
j⁄=i∗
‖ATj Ai∗w∗‖2≤ (1−γ)‖w∗‖2
for a certain scalar constantγ >0. Further, suppose that‖z‖2≤ γ2‖w∗‖2. Then, forβ∈[‖z‖2 ‖w∗‖2−‖z‖2γ‖w∗‖2−‖z‖2,‖w∗‖2−‖ z‖2],
there exists a solution W = (w1,..., wk) such that w∗j = 0 for j⁄=i∗. Moreover, the 𝓁2 norm‖wi∗− w∗‖2 is bounded
as follows:
‖wi∗− w∗‖2≤ β‖w∗‖2‖w∗‖2−‖ z‖2 +‖z‖2.
In order to apply Proposition 21, we need to estimate the upper bound of
max
h∈Rd:h⁄=0
‖‖UTdiag(I(Xh≥ 0))U‖‖2.
From Lemma 3, by taking t = 1/4, for n≥ 4000σ2d log(54n), we have
P
(
max
h∈Rd:h⁄=0‖XTdiag(I(Xh≥ 0))X‖2≤ 34{≥ 1− 4 exp(− n8000σ2{. (126)
Note that X = UΣVT , therefore
‖‖XTDjX‖‖2 =‖‖ΣUTDjUΣ‖‖2≥σ2min‖‖UTDjU‖‖2, (127)
where σmin is the smallest singular value of X.
On the other hand, from Theorem 4.6.1 in [44], we have the following lower bound.
P
(
σmin≥ 1− 2
√
d
n
(
≥ 1− 2 exp(−d). (128)
Forn≥ 1024d, we have
P
(
σ2min≥ 7/8{≥P (σmin≥ 1− 1/16)≥P
(
σmin≥ 1− 2
√
d
n
(
≥ 1− 2 exp(−d). (129)

41
This implies that for n satisfying n≥ max{1024d, 4000σ2d log(54n)}, we have
P
(
max
j∈[p]
‖‖XTDjX‖‖2≤ 34{≤P(σ2min maxj∈[p]‖‖UTDjU‖‖2≤ 34{
≤P
(
σ2min maxj∈[p]‖‖UTDjU‖‖2≤ 34|σ2min≥ 78{P(σ2min≥ 78{
+P
(
σ2min maxj∈[p]‖‖UTDjU‖‖2≤ 34|σ2min≤ 78{P(σ2min≤ 78{
≤P
(
max
j∈[p]
‖‖UTDjU‖‖2≤ 67{P(σ2min≥ 78{ + 1−P(σ2min≥ 78{.
(130)
Therefore, we calculate that
P
(
max
j∈[p]
‖‖UTDjU‖‖2≤ 67{
≥1− 4 exp
(
− n8000σ2{/P(σ2min≥ 78{
≥1− 4 exp
(
− n8000σ2{/(1− 2 exp(−d))
≥1− 2 exp(−d)− 4 exp
(
− n8000σ2{
(131)
Applying Proposition 21 with γ = 17 and Ai∗ = U, Aj = DjU, w∗ = ΣVTw∗, we conclude that if the assumptions in
Theorem 10 is satisﬁed, then with probability at least 1−4 exp(−n/8000σ2)−2 exp(−d) there exists W = (w, 0,..., 0)
such that W is the optimal solution to both (24) and (25) whenever n≥ max{4000σ2d log(54n), 1024d}.
Moreover, we obtain the desired upper bound
‖‖w− ΣVTw∗‖‖2≤ βηη−‖ z‖2 +‖z‖2.
Finally, we provide high probability upper and lower bounds for η =‖ΣVTw∗‖2 as follows. Again from Theorem
4.6.1 in [44], we know that for n≥ 1024d, with probability at least 1 − 2 exp(−d) it holds that
1− 1/16≤σmin≤σmax≤ 1 + 1/16, (132)
which immediately implies that (1 − 1/16)‖w∗‖2≤η≤ (1 + 1/16)‖w∗‖2.
J. Numerical Veriﬁcation
In this subsection, we numerically verify Theorem 10. We take n = 40,d = 10 and test for σ = 0, 1/8, 1/4. For
each σ, we solve the regularized group Lasso problem (25) for β∈ [0, 2]. Then we analyze the solution and record
the number of active neurons. The recovery is regarded as success if there is exactly one active neuron. In Figure 12,
the recovery displays a failure-success-failure pattern when β increases. Besides, the lower bound of β that ensures
successful recovery shifts right as σ increases, while the upper bound generally remains the same.
(a) σ = 0
 (b) σ = 1/8
 (c) σ = 1/4
Fig. 12: The pattern of successful recovery of one planted linear neuron by solving regularized group Lasso problem
(125) derived from training ReLU networks with skip connections.

42
Appendix I
Proofs in Section III-C
A. Proof of Theorem 11
Proof We ﬁrst introduce an auxillary lemma:
Lemma 5 Suppose that Ui, Uj∈ Rn×d are column orthonormal, i.e., UTi Ui = Id and UTj Uj = Id. If UTi Uj = Id,
then, we have Ui = Uj.
Proof Fork∈ [d], we let wi,k and wj,k be the k-th column of Ui and Uj. Note that 1 = ( UTi Uj)k,k = wTi,kwj,k.
As UTi Ui = Id and UTj Uj = Id, we have ‖wi,k‖2 =‖wj,k‖2 = 1. Therefore, wTi,kwj,k = 1 implies that wi,k = wj,k.
Hence, we have Ui = Uj.
Consider the event
E1 =
{ n
i=1
I(xTi ˜w∗≥ 0)≥d
{
. (133)
We ﬁrst show that for n >2d, E1 holds with high probability. As xi∼N (0,Id/n), I(xTi w∗≥ 0) are i.i.d. random
variables following Bern(1/2). Denote Bi = I(xTi w∗≥ 0) and let B = 1n∑ni=1Bi. We note that E[B] = 12. According
to the Chernoﬀ bound, we have
P (Ec1) =P
(
B <dn{ =P(B <(1− n− 2dn { E[B]{≤ exp(−16(n− 2dn {2n(. (134)
This implies that P (E1)≥ 1− exp
(
− 16(n−2dn {2n{.
Denote E2 ={σmin
(
XTDi∗X{> 0}, where Di∗ = diag(I(Xw∗≥ 0)). We note that
XTDi∗X =
n
i=1
xixTi I(xTi w∗≥ 0).
As xi∼N (0,Id/n), we have P (Ec2|E1) = P(Ec2,E1)P(E1) = 0, which implies that P (E2|E1) = 1.
Conditioned on the event E2, we have Ui∗∈ Rn×d. For j⁄=i∗, we show that UTi∗UjUTj Ui∗⁄= Id. Let Uj∈ Rn×rj.
If rj < d, then UTi∗UjUTj Ui∗ is with rank at most rj < d. Hence, we have UTi∗UjUTj Ui∗⁄= Id. If rj = d, suppose
that UTi∗UjUTj Ui∗ = Id. Denote P = UTj Ui∗∈ Rd×d. Then, PTP = Id. This implies that P is orthogonal. Hence,
UTj (Ui∗PT ) = PPT = Id. We note that Ui∗PT is also column orthonormal. This is because
(Ui∗PT )TUi∗PT = PUTi∗Ui∗PT = PPT = Id.
As the matrices Uj and Ui∗PT are column orthonormal and UTj (Ui∗PT ) = Id, from Lemma 5, we have Uj = Ui∗PT .
As Di∗⁄= Dj, there exists k∈ [n] such that either of following statements will hold.
• (Di∗)k,k = 1 and (Dj)k,k = 0.
• (Di∗)k,k = 0 and (Dj)k,k = 1.
For the ﬁrst case, we note that
wi∗,k = (Di)k,kxTk Vi∗Σi∗, wj,k = (Dj)k,kxTk VjΣj. (135)
Because xk ⁄= 0 and Vi∗Σi∗ is invertible, we have ‖wi∗,k‖2 > 0. As Ui∗ = UjPT , we have wTi∗,k = wTj,kPT . As
wj,k = 0, this implies that wi∗,k = 0, which leads to a contradiction. For the second case, we note that Ui∗ = UjP.
Similarly, this will lead to a contradiction.
Therefore, conditioned on E2, for j⁄=i∗, we have UTi∗UjUTj Ui∗⁄= Id. We note that UTi∗UjUTj Ui∗≽ UTi∗Ui∗ = Id.
This implies that ‖UTj Ui∗ ˜w∗‖2 = 1 if and only if we have ‖UTi∗UjUTj Ui∗‖2 = 1 and ˜w∗∈ eigmax{UTi∗UjUTj Ui∗}.
As UTi∗UjUTj Ui∗ ⁄= Id, if it follows that ‖UTi∗UjUTj Ui∗‖2 = 1, then eigmax {UTi∗UjUTj Ui∗} is with dimension at
most d− 1. In other words, conditioned on ‖UTi∗UjUTj Ui∗‖2 = 1, eigmax{UTi∗UjUTj Ui∗} is a random subspace with
dimension at most d− 1. This implies that
P ( ˜w∗∈ eigmax{UTi∗UjUTj Ui∗},‖UTi∗UjUTj Ui∗‖2 = 1|E2)
=P (Σi∗Vi∗w∗∈ eigmax{UTi∗UjUTj Ui∗},‖UTi∗UjUTj Ui∗‖2 = 1|E2) = 0. (136)
Immediately, for j⁄=i∗, we have
P (‖UTj Ui∗ ˜w∗‖2 = 1) = 0 (137)

43
Forσ∈{ 0, 1}n, deﬁne U(σ) as the left singular vector of diag(σ)X. Then, we have
P
(
max
h∈Rd:h⁄=0,I(Xh≥0)⁄=I(X ˜w∗≥0)‖U(I(Xh≥ 0))TUi∗ ˜w∗‖2 = 1
⏐⏐⏐⏐E2{
=P
(
max
σ∈{0,1}n:∃h⁄=0,I(Xh≥0)⁄=I(X ˜w∗≥0),σ=I(Xh≥0)‖U(σ)TUi∗ ˜w∗‖2 = 1
⏐⏐⏐⏐E2{
≤

σ∈{0,1}n
P (‖U(σ)TUi∗ ˜w∗‖2 = 1, I(Xh≥ 0)⁄= I(X ˜w∗≥ 0),σ = I(Xh≥ 0)|E2) = 0.
(138)
We note that P (E2)≥P (E1,E 2) =P (E1)≥ 1− exp
(
− 16(n−2dn {2n{. This implies that
P

) max
h∈Rd:h⁄=0,
I(Xh≥0)⁄=I(X ˜w∗≥0)
‖U(I(Xh≥ 0))TUi∗ ˜w∗‖2 < 1
(
[(
=P
(
max
h∈Rd:h⁄=0,I(Xh≥0)⁄=I(X ˜w∗≥0)‖U(I(Xh≥ 0))TUi∗ ˜w∗‖2 < 1,E 2
{
=P
(
max
h∈Rd:h⁄=0,I(Xh≥0)⁄=I(X ˜w∗≥0)‖U(I(Xh≥ 0))TUi∗ ˜w∗‖2 < 1
⏐⏐⏐⏐E2{P (E2)
=P (E2)≥ 1− exp
(
−16(n− 2dn {2n(.
(139)
This completes the proof.
B. Proof of Proposition 8
Proof For simplicity, we assume that‖w1‖2 =‖w2‖2 =‖hj‖2 = 1. We ﬁrst consider the case where cos ∠(w1, w2) =
−1. Then, we have w2 =−w1. In this case, we have D1D2 = 0. Hence, it follows that[UTs1Us1 UTs1Us2
UTs2Us1 UTs2Us2
]
=
[Id 0
0 Id
]
. (140)
Then, we can simply that
UTj [U1 U2][UT1 U1 UT1 U2UT2 U1 UT2 U2]−1[ ˜w1˜w2]
=UTj U1 ˜w1 + UTj U2 ˜w2
=Σ−1j VTj XTDj
(
D1XV1Σ−11 Σ1VT1 w1‖Σ1VT1 w1‖2{ + Σ−1j VTj XTDj(D2XV2Σ−12 Σ2VT2 w2‖Σ2VT2 w2‖2{
= 1‖Σ1VT1 w1‖2 Σ−1j VTj XTDjD1Xw1 + 1‖Σ2VT2 w2‖2 Σ−1j VTj XTDjD2Xw2
(141)
As n→∞ , XTDiDjX converges in probability to
M(hi, hj) = Ex∼N(0,Id)[xxT I(xThi≥ 0)I(xThj≥ 0)]. (142)
As n→∞ , we have XTDjX p→ 12Id and Σj p→ 1√2Id. Therefore, we have
‖‖UTj U1 ˜w1 + UTj U2 ˜w2‖‖2 p→ 2‖M(hj, w1)w1− M(hj,−w1)w1‖2. (143)
According to Lemma 7 in [47], for hi, hj satisfying‖hi‖2 =‖hj‖2 = 1, the matrix M(hi, hj) takes the form
M(hi, hj) =c1(γ)Id +c2(γ)(hihTj + hjhTi ) +c3(γ)(hihTi + hjhTj ). (144)
Here c1,c 2,c 3 are functions of γ. Then, we have
M(hj, w1)w1− M(hj,−w1)w1
=(c1(γ) +γc2(γ) +c3(γ))w1 + 2(c2(γ) +γc3(γ))hj
− (c1(−γ)−γc2(γ)−c3(γ))w1 + 2(c2(−γ)−γc3(−γ))hj.
(145)

44
We observe that‖M(hi, hj)hi−M(−hi, hj)hi‖22 only depends on γ. Denoteg1(γ) = 2‖M(hi, hj)hi−M(−hi, hj)hi‖2.
Therefore, it is suﬃcient to compute the case where hi = e1 and hj =γe1 +
√
1−γ2e2. Utilizing Lemma 7, we have
g1(γ)2 =4‖M(hi, hj)hi− M(−hi, hj)hi‖22
=4
(
Ex
[
σ′(x1)σ′(γx1 +√1−γ2x2)x21]− Ex[σ′(x1)σ′(−γx1 +√1−γ2x2)x21]{2
+ 4
(
Ex
[
σ′(x1)σ′(γx1 +√1−γ2x2)x1x2]− Ex[σ′(x1)σ′(−γx1 +√1−γ2x2)x1x2]{2
=4
(∫ ∞
0
(
F
(
γ√
1−γ2x
(
−F
(
− γ√
1−γ2x
((
p(x)x2dx
(2
.
(146)
We plot g1(γ)2 in Figure 13.
Fig. 13: The plot of g1(γ)2.
Then, we consider the case where wT1 w2 = 0. In this case,[ Id UT1 U2
UT2 U1 Id
]
=
[ Id Σ−11 VT1 XTD1D2XV2Σ−12
Σ−12 VT2 XTD2D1XV1Σ−11 Id
]
(147)
This implies that
[V1 0
0 V2
][ Id UT1 U2
UT2 U1 Id
][ VT1 0
0 VT2
]
p
→
[ Id 2M(w1, w2)
2M(w1, w2) Id
]
(148)
On the other hand, we note that
VTj UTj [U1 U2][VT1 00 VT2]
=VTj Σ−1j VjXTDj[D1XV1Σ−11 VT1 D2XV2Σ−12 VT2] p→ 2[M(hj, w1) M(hj, w2)]. (149)
We also have [
V1 0
0 V2
][ ˜w1
˜w2
]
=
[
VT1 Σ1V1w1
‖Σ1V1w1‖2
VT2 Σ2V2w2
‖Σ2V2w2‖2
] p
→
[w1
w2
]
. (150)
Therefore, we have the limit
‖‖‖‖‖Uj[U1 U2][ Id UT1 U2UT2 U1 Id ]−1[ ˜w1˜w2]‖‖‖‖‖2 p→ 2‖‖‖‖‖[M(hj, w1) M(hj, w2)][ Id 2M(w1, w2)2M(w1, w2) Id ]−1[w1w2]‖‖‖‖‖2
Lemma 6 Suppose that wT1 w2 = 0. Then, we have c1(0) = 14,c 2(0) = 12π andc3(0) = 0. In other words, it follows that
M(w1, w2) = 14Id + 12π (w1wT2 + wT2 w1). (151)
From Lemma 6, we can compute that
[ Id 2M(w1, w2)
2M(w1, w2) Id
]
=
[ Id 12Id + 1π (w1wT2 + w2wT1 )1
2Id + 1π (w1wT2 + w2wT1 ) In
]
. (152)
Suppose that [
Id 12Id + 1π (w1wT2 + wT2 w1)1
2Id + 1π (w1wT2 + wT2 w1) In
][β1
β2
]
=
[w1
w2
]
. (153)
Then, we note that
β1 + 12β2 + wT2β2π w1 + wT1β2π w2 = w1, 12β1 + wT2β1π w1 + wT1β1π w2 +β2 = w2. (154)

45
This implies that β1,β 2∈ span{w1, w2}. Let
[βT1
βT2
]
= A
[wT1
wT2
]
, where A =
[a1,1 a1,2
a2,1 a2,2
]
. Then, the above linear system
reduces to
a1,1 + 12a2,1 + 1πa2,2 = 1,
a1,2 + 12a2,2 + 1πa1,2 = 0,
1
2a1,1 + 1πa2,1 +a2,1 = 0,
1
πa1,1 + 12a1,2 +a2,2 = 1.
(155)
We can solve that
a1,1 =a2,2 =
((
1 + 1π{2− 14(−1(1 + 1π{,a 2,1 =a1,2 =((1 + 1π{2− 14(−1 12. (156)
In other words, we have A =
[1 + 1π 121
2 1 + 1π
]−1
.
Denote γ1 = hTj w1 and γ2 = hTj w2. As wT1 w2 = 0, we have γ21 +γ22≤ 1. Thus, we have
[M(hj, w1) M(hj, w2)][ Id 2M(w1, w2)2M(w1, w2) Id ]−1[w1w2]
=M(w1, hj)(a1,1w1 +a1,2w2) + M(w2, hj)(a2,1w1 +a2,2w2)
=a1,1(c1(γ1) +γ1c2(γ1) +c3(γ1))w1 + 2(c2(γ1) +γ1c3(γ1))hj)
+a1,2(γ2c2(γ1)w1 +c1(γ1)w2 +γ2c3(γ1)hj)
+a2,1(γ1c2(γ1)w2 +c1(γ2)w1 +γ1c3(γ2)hj)
+a2,2(c1(γ2) +γ2c2(γ2) +c3(γ2)w1 + 2(c2(γ2) +γ2c3(γ2))hj)).
(157)
Similarly, the norm of this quantity only depends on γ1 and γ2. Therefore, it is suﬃcient to consider w1 = e1,
w2 = e2 and hj =γ1e1 +γ2e2 +
√
1−γ21−γ22e3. In this case, we note that
M(w1, hj)(a1,1w1 +a1,2w2) + M(w2, hj)(a2,1w1 +a2,2w2)
=a1,1
)
]]]) Ex
[
σ′(x1)σ′(γ1x1 +γ2x2 +√1−γ21−γ22x3)x21]
Ex
[
σ′(x1)σ′(γ1x1 +γ2x2 +√1−γ21−γ22x3)x1x2]
Ex
[
σ′(x1)σ′(γ1x1 +γ2x2 +√1−γ21−γ22x3)x1x3]
(
[
+a1,2
)
]]])Ex
[
σ′(x1)σ′(γ1x1 +γ2x2 +√1−γ21−γ22x3)x1x2]
Ex
[
σ′(x1)σ′(γ1x1 +γ2x2 +√1−γ21−γ22x3)x22]
Ex
[
σ′(x1)σ′(γ1x1 +γ2x2 +√1−γ21−γ22x3)x2x3]
(
[
+a2,1
)
]]]) Ex
[
σ′(x2)σ′(γ1x1 +γ2x2 +√1−γ21−γ22x3)x21]
Ex
[
σ′(x2)σ′(γ1x1 +γ2x2 +√1−γ21−γ22x3)x1x2]
Ex
[
σ′(x2)σ′(γ1x1 +γ2x2 +√1−γ21−γ22x3)x1x3]
(
[
+a2,2
)
]]])Ex
[
σ′(x2)σ′(γ1x1 +γ2x2 +√1−γ21−γ22x3)x1x2]
Ex
[
σ′(x2)σ′(γ1x1 +γ2x2 +√1−γ21−γ22x3)x22]
Ex
[
σ′(x2)σ′(γ1x1 +γ2x2 +√1−γ21−γ22x3)x2x3]
(
[
(158)
Let F (x) and p(x) represent the CDF and pdf of N (0, 1) respectively. We introduce two lemmas for computing the
expectations in (158).
Lemma 7 Suppose that γ∈ [−1, 1]. We have the following computations:
Ex
[
σ′(x1)σ′(γx1 +√1−γ2x2)x21] =∫ ∞
0
(
1−F
(
− γ√
1−γ2x
((
p(x)x2dx,
Ex
[
σ′(x1)σ′(γx1 +√1−γ2x2)x1x2] = 1−γ22π . (159)

46
Lemma 8 Suppose that γ21 +γ22 +γ23 = 1 and γ3≥ 0. Then, we have
E [σ′(x1)σ′(γ1x1 +γ2x2 +γ3x3)x1x2] =
√
1−γ21|γ2|
2π ,
E
[
σ′(x1)σ′(γ1x1 +γ2x2 +γ3x3)x22] =∫ ∞
−∞
(∫ ∞
0
(
1−F
(
−γ1x1 +γ2x2
γ3
{{
p(x1)dx1
{
p(x2)x22dx2,
E [σ′(x1)σ′(γ1x1 +γ2x2 +γ3x3)x2x3] = |γ2|γ1γ3
2π (γ23 +γ22)3/2.
(160)
Denote γ3 =
√
1−γ21−γ22. Hence, we can compute that
M(w1, hj)(a1,1w1 +a1,2w2) + M(w2, hj)(a2,1w1 +a2,2w2)
=a1,1
)
]]])
∞
0
(
1−F
(
− γ1√1−γ21x
{{
p(x)x2dx
√
1−γ22|γ1|
2π
(1−γ21)γ3
2π
(
[ +a1,2
)
]]])
√
1−γ22|γ1|
2π∞
−∞
(∞
0
(
1−F
(
−γ1x1+γ2x2γ3
{{
p(x1)dx1
{
p(x2)x22dx2
|γ2|γ1γ3
2π(γ23+γ22)3/2
(
[
+a2,1
)
]]])
∞
−∞
(∞
0
(
1−F
(
−γ1x1+γ2x2γ3
{{
p(x2)dx2
{
p(x1)x21dx1√
1−γ21|γ2|
2π|γ1|γ2γ3
2π(γ23+γ22)3/2
(
[ +a2,2
)
]]])
√
1−γ21|γ2|
2π
∞
0
(
1−F
(
− γ2√1−γ22x
{{
p(x)x2dx
(1−γ21)γ3
2π
(
[.
(161)
Denote g2(γ1,γ 2) = 2 ‖M(w1, hj)(a1,1w1 +a1,2w2) + M(w2, hj)(a2,1w1 +a2,2w2)‖2. We numerically verify that
g2(γ1,γ 2)2≤ 1 and it is maximized at (0 , 1) and (1, 0).
We plotg2(γ1,γ 2)2 in Figure 14. We note thatg2(γ1,γ 2)2 is maximized at the boundary. Hence, we plotg2(cosθ, sinθ)
for θ∈
[
−π4, 3π4] in Figure 15. We note that g2(cosθ, sinθ) is maximized at θ = 0 or θ =π/2. Therefore, g2(γ1,γ 2) is
maximized at (0, 1) and (1, 0) and the optimal value is 1.
Fig. 14: The contour plot of
g2(γ1,γ 2)2.
Fig. 15: The plot of g2(cosθ, sinθ)2.
C. Proof of Lemma 6
Proof Consider the rotation matrix P∈ Rd×d such that Pw1 = e1 and Pw2 = e2. Then, we have
M(hi, hj)
=E[xxT I(xThi≥ 0)I(xThj≥ 0)]
=E[xxT I(xTPTPhi≥ 0)I(xTPTPhj≥ 0)]
=PT E[˜x˜xT I(˜xTPhi≥ 0)I(˜xTPhj≥ 0)]P
=PTM(Phi, Phj)P
(162)
where we write ˜x = Px. Thus, it is suﬃcient to compute M(Phi, Phj) = M(e1, e2). We note that
M(e1, e2) =
[M1:2,1:2 0
0 Ex
[
σ′(x1)σ′(x2)x23] Id−2
]
, (163)
where M1:2,1:2 follows
M1:2,1:2 =
[ Ex[σ′(x1)σ′(x2)x21] Ex [σ′(x1)σ′(x2)x1x2]
Ex [σ′(x1)σ′(x2)x1x2] Ex[σ′(x1)σ′(x2)x22]
]
=
[ 1
4
1
2π1
2π
1
4
]
. (164)

47
This implies that c1(0) = Ex
[
σ′(x1)σ′(x2)x23] = 14. We also note that
M1:2,1:2 =
[u1(0) +u3(0) u2(0)
u2(0) u1(0) +u3(0)
]
. (165)
Hence, we have c1(0) = 14,c 2(0) = 12π and c3(0) = 0.
D. Proof of Lemma 7
Proof For the ﬁrst equation, by integrating w.r.t. x2 ﬁrst, we immediately obtain that
Ex
[
σ′(x1)σ′(γx1 +√1−γ2x2)x21] =∫ ∞
0
(
1−F
(
− γ√
1−γ2x
((
p(x)x2dx. (166)
Note that ∫ ∞
− γ√
1−γ2x1
xp(x)dx =


∫ 0
− γ√
1−γ2x1
+
∫ ∞
0
(
(xp(x)dx
= 1√2π


∫ 0
− γ√
1−γ2x1
+
∫ ∞
0
(
(e−x22 dx2
2 = 1√2π exp− γ22(1−γ2 )x2.
(167)
Therefore, we have
Ex
[
σ′(x1)σ′(γx1 +√1−γ2x2)x1x2] =∫ ∞
0
1√
2πe
− γ22(1−γ2 )x2p(x)xdx
= 12π∫ ∞0 e− 12(1−γ2 )x2xdx = 1−γ22π . (168)
E. Proof of Lemma 8
Proof We can compute that
E [σ′(x1)σ′(γ1x1 +γ2x2 +γ3x3≥ 0)x1x2]
=
∫ ∞
0
∫ ∞
−∞
∫ ∞
⏐⏐γ1x1 +γ3x3
γ2
⏐⏐x1x2p(x1)p(x2)p(x3)dx1dx3dx2
=
∫ ∞
0
∫ ∞
−∞
x1p(x1)p(x3) 1√2π exp(−(γ1x1 +γ3x3)22γ22 {dx1dx3.
(169)
Note that ∫ ∞
−∞
p(x3) 1√2π exp(−(γ1x1 +γ3x3)22γ22 {dx3
= 12π∫ ∞−∞ exp(−(γ1x1 +γ3x3)2−γ22x232γ22 {dx3
= 12π∫ ∞−∞ exp(−(γ23 +γ22)x23 + 2γ1γ3x1x3 +γ21x212γ22 {dx3
= 12π∫ ∞−∞ exp

)−(γ23 +γ22)(x3− γ1γ3γ23+γ22x1{2 +γ21x21− γ21γ23γ23+γ22x21
2γ22
(
[(dx3
= 12π∫ ∞−∞ exp

)−(γ23 +γ22)(x3− γ1γ3γ23+γ22x1{2 + γ21γ22γ23+γ22x21
2γ22
(
[(dx3
= |γ2|√
2π
√
γ23 +γ22 exp
(
− γ21
2(γ23 +γ22)x21
{
.
(170)

48
Then, we have ∫ ∞
0
∫ ∞
−∞
x1p(x1)p(x3) 1√2π exp(−(γ1x1 +γ3x3)22γ22 {dx1dx3
=
∫ ∞
0
|γ2|
2π
√
γ23 +γ22 exp
(
− γ21
2(γ23 +γ22)x21− x212{x1dx
=
∫ ∞
0
|γ2|
2π
√
γ23 +γ22 exp
(
− 12(γ23 +γ22)x21
{
x1dx
=1−γ21
2π
γ2√
γ23 +γ22 =
√
1−γ21γ2
2π .
(171)
For the second equation, we note that
E
[
σ′(x1)σ′(γ1x1 +γ2x2 +γ3x3)x22]
=
∫ ∞
−∞
∫ ∞
−∞
∫ ∞
max{0,−γ2x2 +γ3x3γ1 }p(x1)p(x2)p(x3)x22dx2dx3dx1
=
∫ ∞
−∞
(∫ ∞
0
(
1−F
(
−γ1x1 +γ2x2
γ3
{{
p(x1)dx1
{
p(x2)x22dx2.
(172)
For the third equation, we have
E [σ′(x1)σ′(γ1x1 +γ2x2 +γ3x3)x2x3] =
∫ ∞
0
∫ ∞
−∞
x3p(x1)p(x3) 1√2π exp(−(γ1x1 +γ3x3)22γ22 {dx1dx3. (173)
Following the previous calculation, we can compute that
∫ ∞
−∞
x3p(x3) 1√2π exp(−(γ1x1 +γ3x3)22γ22 {dx3
= 12π∫ ∞−∞ exp

)−(γ23 +γ22)(x3− γ1γ3γ23+γ22x1{2 + γ21γ22γ23+γ22x21
2γ22
(
[(dx3
= |γ2|√
2π
√
γ23 +γ22
γ1γ3
γ23 +γ22x1.
(174)
Therefore, we have
E [σ′(x1)σ′(γ1x1 +γ2x2 +γ3x3)x2x3] =
∫ ∞
0
|γ2|√
2π
√
γ23 +γ22
γ1γ3
γ23 +γ22x1p(x1)dx1 = |γ2|γ1γ32π (γ23 +γ22)3/2. (175)
Appendix J
Proofs in Section VI
A. Proof of Proposition 9
Proof We denote hi = w∗‖w∗‖2 . For simplicity, we can assume that ‖hj‖2 = 1. Hence, it follows that γ = hTi hj. As
n→∞ , XTDiDjX converges in probability to
M(hi, hj) = Ex∼N(0,Id)[xxT I(xThi≥ 0)I(xThj≥ 0)]. (176)
According to Lemma 7 in [47], the above expectation takes the form
M(hi, hj) =c1(γ)Id +c2(γ)(hihTj + hjhTi ) +c3(γ)(hihTi + hjhTj ). (177)
Here c1,c 2,c 3 are functions of γ. As n→∞ , we note that XTDiX p→ Ex∼N(0,Id)[I(xThi≥ 0)xxT ] = 12Id. Thus, as
n→∞ , we have
T
p
→2‖M(hi, hj)hi‖2. (178)
According to the expression (177), we have
M(hi, hj)hi = (c1(γ) +γc2(γ) +c3(γ))hi + (c2(γ) +γc3(γ))hj. (179)

49
As‖hi‖2 =‖hj‖2 = 1, the quantity ‖M(hi, hj)hi‖2 only depends on γ = hTi hj. Denote g(γ) = 4‖M(hi, hj)hi‖22.
Thus, we can simply consider hi = e1 and hj =γe1 +
√
1−γ2e2. According to Lemma 7, we can compute that
g(γ)2 =4‖M(hi, hj)hi‖22
=4
(
Ex
[
σ′(x1)σ′(γx1 +√1−γ2x2)x21]{2 + 4(Ex[σ′(x1)σ′(γx1 +√1−γ2x2)x1x2]{2
=4
(∫ ∞
0
(
1−F
(
− γ√
1−γ2x
((
p(x)x2dx
(2
+ 4
(1−γ2
2π
{2
.
(180)
We plot g(γ)2 as a function of γ as follows.
Fig. 16: g(γ)2 as a function of γ.
Appendix K
Necessary condition and sufficient condition of the neural isometry condition for ReLU networks
For the recovery of single-neuron ReLU network, we ﬁrst present a necessary condition for the neural isometry
condition (NIC-1).
Deﬁnition 7 We say that a diagonal arrangement pattern Di∈ H satisﬁes the maximal condition if for all index
j∈ [p] and j⁄=i, we have DiDj⁄= Di.
Lemma 9 A necessary condition for (NIC-1) is that the matrix Di∗ satisﬁes the maximal condition.
Then, we present a suﬃcient condition to ensure that the neural isometry condition (NIC-1) holds.
Proposition 22 Suppose that Di∗ satisﬁes the maximal condition. Assume that the planted neuron w∗ satisﬁes the
following conditions
• w∗ is the eigenvector corresponding to the largest eigenvalue of XTDi∗X, i.e.,
‖XTDi∗Xw∗‖2 =‖XTDi∗X‖2‖w∗‖2.
• xTl w∗ > 0 for all l∈ [n] satisfying (Di∗)ll = 1
Then, the NIC91 given in (NIC-1) holds.
Remark 6 The ﬁrst condition on w∗ requires that w∗ lies in the eigenspace of XTDi∗X corresponding to its largest
eigenvalue. Combining with the maximal condition on Di∗, the second condition on w∗ implies that w∗ lie in the
interior of the cone {w|(2Di∗− In)Xw≥ 0}.
A. Justiﬁcation of the assumptions in Proposition 22
We justify the assumption on the planted neuron w∗ in Proposition 22 for the Gaussian mixture model. Let µ1,µ2∈
Rd and σ > 0. Suppose that n1 of the n training samples follow N (µ1,σ 2Id) and the rest of n2 = n−n1 training
samples follows followN (µ2,σ 2Id). Let w∈{ 0, 1}n be the vector deﬁned by
qi =
{
1, s.t. xi∼N (µ1,σ 2Id),
0, s.t. xi∼N (µ2,σ 2Id). (181)
Proposition 23 Suppose that σ2 > 0 and b =: µT1 µ2‖µ1‖2‖µ2‖2 < 1. With probability at least 1− N1e− (1−b)‖µ1‖224σ 2−
N2e−
(1−b)‖µ2‖22
4σ2 , there exists i∗∈ [p] such that Di∗ = diag(w).
Suppose that δ∈ (0, 1). From Proposition 23, for σ≤
√1−b min{‖µ1‖2,‖µ2‖2}
2
√
log(nδ ) , with probability at least 1 −δ, there
exists i∗∈ [p] such that Di∗ = diag(w). The next question is whether this Di∗ also satisﬁes the maximal condition.

50
Proposition 24 Suppose that there exists i∗∈ [p] such that Di∗ = diag(w). Denote K+ = cone({xi|qi = 1,i∈ [n]})
and K− = cone({xi|qi =−1,i∈ [n]}). Then, Di∗ satisfying the maximal condition if and only if −K−⊆ int(K+).
Finally, we show that the eigenvalue condition will hold for some speciﬁc planted neuron.
Proposition 25 Let xn =µ +σzi, where zn∼N (0,I ) forn = 1,...,N . Suppose that δ >0. Denote X(1) =
)
])
xT1
...
xTn1
(
[∈
Rn1×d. Let w satisfy that ‖w‖2 = 1 and‖(X(1){T X(1)w‖2 =‖(X(1){T X(1)‖2. Then, with probability at least 1−δ,
we have ‖‖‖‖w− µ‖µ‖2‖‖‖‖22≤c1σ, (182)
wherec1 = 2dn2‖µ‖22 2n1√2 log(n1d/δ)‖µ‖2 + 2d log(n1d/δ) is a constant depending on δ.
The following proposition illustrates that for suﬃciently small σ, except for the maximal condition, all conditions in
Proposition 22 will hold with probability at least 1 −δ.
Theorem 13 Let 0< δ <2 exp(−d/8). Suppose that 0< σ≤ min
{
1/(32c1), ‖µ‖22(d+8 log(4n/δ))
}
, where c1 is a constant
deﬁned in Proposition 25 Then, there exists i∗∈P such that Di∗ = diag(w) with probability at least 1−δ. Let w∗
satisfy that‖XTDi∗Xw∗‖2 =‖XTDi∗X‖2‖w∗‖2. We also have (2Di∗−I)Xw∗ > 0 with probability at least 1−δ. By
further assuming that the cone condition in Proposition 24 holds, the neural isometry condition holds, i.e., the problem
(9) has a unique solution.
B. Proof of Lemma 9
Proof Suppose that there exists Dj such that Di∗Dj = Di∗ and Dj⁄= Di∗. This implies that
XTDTj DiX = XTDjDi∗X = XTDi∗X. (183)
Thus, we have ‖‖‖‖XTDTj DiX(XTDi∗X)−1 w∗‖w∗‖2‖‖‖‖2 =‖‖‖‖ w∗‖w∗‖2‖‖‖‖2 = 1. (184)
Thus, the irrepresentability condition (NIC-1) is violated.
C. Proof of Proposition 22
Proof Consider anyj∈ [p] andj⁄=i∗. LetIj ={l∈ [n]|(Di∗)ll−(Dj)ll > 0}. As Di∗ satisﬁes the maximal condition,
we have DjDi∗⁄= Di∗. This implies that Ij⁄= ∅. Let k =|Ij|. Note that
XTDi∗X = XTDjDi∗X +
l∈I
xlxTl . (185)
For simplicity, we write w = w∗‖w∗‖2 , A = XTDi∗DjX and B =∑l∈Ij xlxTl . It is suﬃcient to prove that
‖A(A + B)−1w‖2 < 1. (186)
As w∗ is the eigenvector corresponding to the largest eigenvalue of A + B, we have
(A + B)w =‖A + B‖2w, (187)
which also implies that ‖A + B‖−12 w = (A + B)−1w. Therefore, we have
‖(A + B)−1w‖2 =‖(A + B)‖−12 . (188)
As A, B are positive semi-deﬁnite, we have
‖A + B‖2≥‖ A‖2. (189)
This implies that
‖A(A + B)−1w‖2≤‖ A‖2‖(A + B)−1w‖2 =‖A‖2‖A + B‖−12 ≤ 1. (190)
The equality holds if and only if ‖A + B‖2 =‖A‖2 and w is the eigenvector of the largest eigenvalue of A + B. Let
γ =‖A + B‖2 =‖A‖2. Then, we have
(A + B)w =γw, Aw =γw, (191)
which implies that Bw = 0. Therefore, we have wTBw = 0, or equivalently ∑l∈Ij xTl w = 0. As xTl w > 0 for all k
satisfying (Di∗)ll = 1, we have ∑l∈Ij xTl w> 0, which leads to a contradiction.

51
D. Proof of Proposition 23
Proof Let w = µ1‖µ1‖2− µ2‖µ2‖2 . We can compute that
‖w‖22 = 2− 2 µT1µ2‖µ1‖2‖µ2‖2 = 2(1−b).
This implies that ‖w‖2 =
√
2(1−b). Note that
µT1w =‖µ1‖2− µT1µ2‖µ2‖2 =‖µ1‖2−b‖µ1‖2 = (1−b)‖µ1‖2 > 0.
Similarly, we have
µT2 w = µT1µ2‖µ1‖2−‖µ2‖2 =−(1−b)‖µ2‖2 < 0.
For index i∈ [n] such that qi = 1, we can write xi =µ1 +σzi, where zi∼N (0, 1). We can compute that xTi w =
µT1 w +σzTi w = (1−b)‖µ1‖2 +σzTi w. According to the tail bound of Gaussian random variable, we have
P (xTi w≤ 0) =P (σzTi w≤− (1−b)‖µ1‖2)≤ exp
(
−(1−b)2‖µ1‖22
2σ2‖w‖22
{
= exp
(
−(1−b)‖µ1‖22
4σ2
{
,
which implies that
P (xTnw> 0)≥ 1− exp
(
−(1−b)‖µ1‖22
4σ2
{
.
Therefore, we have
P (xTi w> 0,∀i with qi = 1)≥
(
1− exp
(
−(1−b)‖µ1‖22
4σ2
{{n1
≥ 1−n1 exp
(
−(1−b)‖µ1‖22
4σ2
{
.
For index i∈ [n] such that qi = 0, we can write xn =µ2 +σzi. Similarly, we can compute that
P (xTi w< 0,∀i with yi = 0)≥ 1−n2 exp
(
−(1−b)‖µ2‖22
4σ2
{
. (192)
In summary, we have
P ((2ci− 1)xTi w> 0,∀i∈ [n])≥ 1−n1 exp
(
−(1−b)‖µ1‖22
4σ2
{
−n2 exp
(
−(1−b)‖µ2‖22
4σ2
{
. (193)
Under the event {qixTi w > 0,∀i∈ [n]}, the diagonal arrangement pattern Di∗ induced by the vector w is exactly
diag(c). This completes the proof.
E. Proof of Proposition 24
Proof Suppose that Di∗ satisﬁes the maximal condition. Then, for any w satisfying that
wTxi≥ 0,∀i with qi = 1, (194)
we shall have wTxi < 0 for qi = 0. We note that the condition (194) is equivalent to w∈− (K+)◦. Here (K+)◦ =:
{w|wTx≤ 0,∀x∈ K+} is the polar cone of the cone K+. We note that wTxi < 0 for ci = 0 implies that w∈
int((K−)◦). Therefore, (K+)◦⊆ int((K−)◦). This is equivalent to −K−⊆ int(K+).
Suppose that−K−⊆ int(K+). Then, we have (K+)◦⊆ int((K−)◦). This implies that for any w∈ Rd satisfying
(194), we shall have wTxi < 0 for ci = 0. Therefore, Di∗ satisﬁes the maximal condition.
F. Proof of Proposition 25
Proof We can write
X(1) = 1µT +σZ, (195)
where Z =
)
])
zT1
...
zTn1
(
[∈ Rn1×d and 1∈ Rn1 is a vector of 1s. Each element of Z followsN (0, 1). We note that the extreme
eigenvalue vector of ( 1µT )T1µT = n21µµT is µ‖µ‖2 . According to the tail bound of Gaussian random variable, withprobability at least 1−δ, we have
max
i∈[n1],j∈[d]
|zi,j|≤
√
2 log(n1d/δ). (196)

52
Denote E ={maxi∈[n1],j∈[d]|zi,j|≤
√
2 log(n1d/δ)}. Conditioned on the event E, we have
‖(1µT )TZ + ZT1µT + ZTZ‖F≤ 2√2 log(n1d/δ)‖1µT‖F + 2d log(n1d/δ) = 2n1√2 log(n1d/δ)‖µ‖2 + 2d log(n1d/δ) =:c0.
(197)
Let
(
X(1){T X(1) = VΣVT be the eigenvalue decomposition. According the Weil’s theorem, we note that
|n2‖µ‖22−σ1|≤ σ‖(1µT )TZ + ZT1µT + ZTZ‖F≤σc0. (198)
The other eigenvalues σi of
(
X(1){T X(1) satisﬁes that
|σi|≤ σ‖(1µT )TZ + ZT1µT + ZTZ‖F≤σc0. (199)
We note that ‖‖‖‖(X(1){T X(1)µ‖‖‖‖
2
≥n2‖µ‖32−σ‖(1µT )TZ + ZT1µT + ZTZ‖2‖µ‖2
≥n2‖µ‖32−σ‖(1µT )TZ + ZT1µT + ZTZ‖F‖µ‖2
=(n2‖µ‖22−σc0)‖µ‖2.
(200)
As
(
X(1){T X(1)µ = VΣVTµ =∑di=1σivi(vTiµ), we have
σ1|vT1µ|≥
‖‖‖‖‖VΣVTµ− di=2σivi(vTiµ)‖‖‖‖‖2 =‖(X(1){T X(1)µ‖2− di=2σi|wTiµ|≥ (n2‖µ‖22− (d− 1)c0σ)‖µ‖2. (201)
Note that w = v1. This implies that ⏐⏐⏐⏐wT µ‖µ‖2⏐⏐⏐⏐≥ n2‖µ‖22− (d− 1)c0σn2‖µ‖22 +c0σ . (202)
Note that ‖‖‖‖w− µ‖µ‖2‖‖‖‖22 = 2(1−⏐⏐⏐⏐wT µ‖µ‖2⏐⏐⏐⏐{≤ 2dc0σn2‖µ‖22 +c0σ≤c1σ, (203)
where we let c1 = 2dc0n2‖µ‖22. This completes the proof.
G. Proof of Theorem 13
Proof Denote ˆw∗ = w∗‖w∗‖2 . According to Proposition 25, there exists a constant c1 > 0 such that ˆw∗ satisﬁes that
‖‖‖‖ ˆw∗− µ‖µ‖2‖‖‖‖22≤c1σ, (204)
with probability at least 1−δ/2. For σ≤ ‖µ‖22(d+8 log(4n/δ)), the events
σ‖zi‖2≤‖µ‖2/2, (205)
holds with probability at least 1 −δ/(2n) respectively for all i∈ [n]. Denote E ={σ‖zi‖2≤‖µ‖2/2,∀i∈ [n]}. Then,
P (E)≥ 1−δ/4. For indices i∈ [n] such that qi = 1, conditioned on E, we have σ
⏐⏐⏐zTi µ‖µ‖2⏐⏐⏐≤‖µ‖2/2 and
xTi ˆw∗≥xTi µ‖µ‖2−‖ xi‖‖‖‖‖ ˆw∗− µ‖µ‖2‖‖‖‖2≥ xTi µ‖µ‖2−√c1σ‖xi‖2≥‖µ‖2 +σzTn µ‖µ‖2− 2√c1σ‖µ‖2 > 0 (206)
Here we utilize that σ≤ 132c1 . Similarly, for indices i∈ [n] such that qi =−1, conditioned on E, we have σ⏐⏐⏐zTi µ‖µ‖2⏐⏐⏐≤
‖µ‖2/2 and
xTi ˆw∗≤xTi µ‖µ‖2 +‖xi‖‖‖‖‖ ˆw∗− µ‖µ‖2‖‖‖‖2≤ xTi µ‖µ‖2 +√c1σ‖xi‖2xTi µ‖µ‖2≤−‖µ‖2−σzTi µ‖µ‖2 + 2√c1σ‖µ‖2 < 0.(207)
This implies that (2 Di∗−I)X ˆw∗ > 0. Overall, for suﬃciently small a >0, the event (2 Di∗−I)X ˆw∗ > 0 holds with
probability at least
1−δ/2−δ/2 = 1−δ. (208)

53
H. Numerical veriﬁcation
In this subsection, we numerically verify Proposition 23. We take n = 100,n 1 =n2 = 50 and d = 20, 40, 60, 80, and
test for three types of µ1,µ2.
• µ1 = 1d, µ2 =−1d.
• µ1,µ2∼N (0, Id).
• µ1,µ2∼U (Sd−1).
For eachd, we compute the probability that the diagonal arrangement pattern induced by the vectorw = µ1‖µ1‖2− µ2‖µ2‖2
equals to diag(w) forσ in a certain range. For eachσ, we establish 5000 independent trials to compute the probability.
The S-shaped curves shown in Figure 17 correspond with formulation of the lower bound given in Proposition 23.
(a) µ1 = 1d, µ2 =−1d
 (b) µ1,µ2∼N (0,Id)
(c) µ1,µ2∼U (Sd−1)
Fig. 17: The probability that the statement in Proposition 23 holds over 5000 independent trials.
Appendix L
Additional numerical experiments
In this section, we present additional numerical results mentioned in Section VII. These results serve as a complement
to our main numerical results.
A. ReLU networks with skip connection
In Figure 6, we show phase transition graph for the probability of successful recovery of the planted linear neuron
by solving the group 𝓁1-minimization problem (12) when the planted neuron w∗ is randomly generated fromN (0, Id).
In Figure 18 below, we ﬁnd similar results when the planted neuron w∗ is the smallest right singular vector of X.

54
(a) Gaussian
 (b) Cubic Gaussian
(c) Haar
 (d) Cubic Gaussian + whitened
Fig. 18: The probability of successful recovery of the planted linear neuron by solving the group 𝓁1-minimization
problem (12) over 5 independent trials. The black lines represent the boundaries of successful recovery with probability
1. Here the planted neuron w∗ is the smallest right singular vector of X.
In Figure 7, we show phase transition graph for absolute distance by solving the group 𝓁1-minimization problem (12)
derived from training ReLU networks with skip connection. In Figure 19 below, we ﬁnd similar pattern of the phase
transition.
(a) σ = 0(noiseless)
 (b) σ = 0.05

55
(c) σ = 0.1
 (d) σ = 0.2
Fig. 19: Averaged test distance by solving the group𝓁1-minimization problem (12) derived from training ReLU networks
with skip connection over 5 independent trials.
As a complement to Figure 8, we study the generalization property of ReLU networks with skip connections using
convex training methods. We solve the following regularized training problem with small regularization parameter
β = 10−6 as an approximation of the minimal-norm problem (3).
min
w0,{wj,w′j}pj=1
‖‖‖‖‖‖Xw0 + pj=1 DjX(wj− w′j{− y‖‖‖‖‖‖22 +β‖w0‖2 + pj=1(‖wj‖2 +‖‖w′j‖‖2{((,
s.t. (2 Dj− In)Xwj≥ 0, (2Dj− In)Xw′j≥ 0,j ∈ [p].
(209)
Then we compute the corresponding absolute distance and test distance. The results shown in Figures 20 and 21 have
the same sharp n = 2d boundary of the red region. This validates Proposition 1. Namely, the recovery of the group
𝓁1-minimization problem (12) implies the recovery of the convex program (3).
(a) σ = 0(noiseless)
 (b) σ = 0.05

56
(c) σ = 0.1
 (d) σ = 0.2
Fig. 20: Averaged absolute distance to the planted linear neuron by solving the convex regularized training problem
(209) for ReLU networks with skip connection over 5 independent trials.
(a) σ = 0(noiseless)
 (b) σ = 0.05
(c) σ = 0.1
 (d) σ = 0.2
Fig. 21: Averaged test distance by solving the convex regularized training problem (209) for ReLU networks with skip
connection over 5 independent trials.
B. ReLU networks with normalization layer
We ﬁrst present the phase transition graph for successful recovery of the planted normalized ReLU neuron by solving
the group 𝓁1-minimization (14). Analogous to Section VII-A, we compute the recovery rate for d ranging from 10 to

57
100 and n ranging from 10 to 400 and establish 5 independent trials for each pair of ( n,d ). Here each element xi,j
of the dataset X∈ Rn×d is i.i.d. random variable following N (0, 1/n). The planted neuron w∗ is randomly generated
fromN (0, Id).
Fig. 22: The probability of successful recovery of the planted normalized ReLU neuron by solving the group 𝓁1-
minimization problem (14) over 5 independent trials. The black line represents the boundaries of successful recovery
with probability 1. Here the planted neuron w∗ is randomly generated from N (0, Id).
The second part is phase transition under noisy observation, i.e., y = (Xw∗)+‖(Xw∗)+‖2 + z, where z∼N (0,σ 2/n). InFigure 23, we focus on absolute distance, which is deﬁned as the 𝓁2 distance between the optimal solution wi∗ and ˜w∗.
A sharp n = 2d boundary can be observed from the phase transition graphs, which corresponds with Theorem 11.
(a) σ = 0(noiseless)
 (b) σ = 0.05
(c) σ = 0.1
 (d) σ = 0.2
Fig. 23: Averaged absolute distance to the planted normalized ReLU neuron by solving the group 𝓁1-minimization
problem (14) from training ReLU networks with normalization layer over 5 independent trials.

58
In the third part, we study the generalization property of ReLU networks with normalization layer using both
the convex and non-convex training procedures. For the non-convex training procedure, we minimize the regularized
training objective with small regularization parameter β = 10−6 to approximate the minimal-norm problem (13).
min
{wj,w′j}pj=1
‖‖‖‖‖‖ pj=1 Uj(wj− w′j{− y‖‖‖‖‖‖22 +β pj=1(‖wj‖2 +‖‖w′j‖‖2{
s.t. (2 Dj− In)XVTj Σ−1j wj≥ 0, (2Dj− In)XVTj Σ−1j w′j≥ 0,j ∈ [p],
(210)
Then we compute the corresponding absolute distance. The phase transition graphs are shown in Figure 24. We can
also observe a sharp n = 2d transition similar to the group 𝓁1-minimization (14).
(a) σ = 0(noiseless)
 (b) σ = 0.05
(c) σ = 0.1
 (d) σ = 0.2
Fig. 24: Averaged absolute distance by training ReLU networks with normalization layer on the regularized convex
problem (6) over 5 independent trials.
For nonconvex training method, we solve the regularized non-convex training problem (6) with the same setting as
Section VII-A. We set the number of neurons to be m =n + 1 and train the ReLU neural network with normalization
layer for 400 epochs. We use the AdamW optimizer with weight decay β = 10−6. We note that the nonconvex training
may still reach local minimizers. Thus, the absolute distance do not show clear phase transition as the convex training.
However, the transitions of test error generally follow the patterns of the group 𝓁1-minimization problem. In Figure
25, we show that the test error increases as n/d increases, and the rate of increase becomes sharp around n = 2d (the
boundary of orange region).

59
(a) σ = 0(noiseless)
 (b) σ = 0.05
(c) σ = 0.1
 (d) σ = 0.2
Fig. 25: Averaged test error by training ReLU networks with normalization layer on the regularized non-convex problem
(6) over 10 independent trials.
C. Multi-neuron recovery
In this subsection, we present further numerical results on the recovery of ReLU networks with normalization layer
when the label vector is the combination of several normalized ReLU neurons. Readers can refer to the details of the
experiments in Section VII-B and Appendix L-B.
We ﬁrst show phase transition graphs for successful recovery of the planted normalized ReLU neurons. We compute
the recovery rate for d ranging from 10 to 80 and n ranging from 10 to 400 and establish 5 independent trials for each
pair of (n,d ).

60
(a) k = 2, w∗1 = w∗, w∗2 =−w∗, w∗∼U (Sn−1)
 (b) k = 2, w∗1, w∗2∼U (Sn−1)
(c) k = 2, w∗1 = e1, w∗2 = e2,
 (d) k = 3, w∗i = ei(i = 1, 2, 3)
Fig. 26: The probability of successful recovery of the planted normalized ReLU neurons by solving the group 𝓁1-
minimization problem (14) over 5 independent trials. The label vector y is the combination of several normalized
ReLU neurons.
The second part is noisy observation model. In Figure 9, we show the phase transition graph when the planted neurons
satisfy w∗1 = w∗, w∗2 =−w∗, w∗∼U (Sn−1). In Figure 27, 28 and 29 below, we show results when w∗1, w∗2∼U (Sn−1),
w∗1 = e1, w∗2 = e2 and w∗i = ei(i = 1, 2, 3), respectively.
(a) σ = 0(noiseless)
 (b) σ = 0.05

61
(c) σ = 0.1
 (d) σ = 0.2
Fig. 27: Averaged absolute distance to the planted normalized ReLU neurons by solving the group 𝓁1-minimization
problem (14) from training ReLU networks with normalization layer over 5 independent trials. Here we set k = 2
planted neurons which satisfy w∗1, w∗2∼U (Sn−1).
(a) σ = 0(noiseless)
 (b) σ = 0.05
(c) σ = 0.1
 (d) σ = 0.2
Fig. 28: Averaged absolute distance to the planted normalized ReLU neurons by solving the group 𝓁1-minimization
problem (14) from training ReLU networks with normalization layer over 5 independent trials. Here we set k = 2
planted neurons which satisfy w∗1 = e1, w∗2 = e2.

62
(a) σ = 0(noiseless)
 (b) σ = 0.05
(c) σ = 0.1
 (d) σ = 0.2
Fig. 29: Averaged absolute distance to the planted normalized ReLU neurons by solving the group 𝓁1-minimization
problem (14) from training ReLU networks with normalization layer over 10 independent trials. Here we set k = 3
planted neurons which satisfy w∗i = ei(i = 1, 2, 3).
In the third part, we directly study the generalization property of ReLU networks with normalization layer using
non-convex training methods. We note that the transitions of test error generally follow the patterns of the group
𝓁1-minimization problem, analogous to our observation in Appendix L-B.
(a) σ = 0(noiseless)
 (b) σ = 0.05

63
(c) σ = 0.1
 (d) σ = 0.2
Fig. 30: Averaged test error by training ReLU networks with normalization layer on the regularized non-convex problem
(6) over 10 independent trials. Here we set k = 2 planted neurons which satisfy w∗1 = w∗, w∗2 =−w∗, w∗∼U (Sn−1).
(a) σ = 0(noiseless)
 (b) σ = 0.05
(c) σ = 0.1
 (d) σ = 0.2
Fig. 31: Averaged test error by training ReLU networks with normalization layer on the regularized non-convex problem
(6) over 10 independent trials. Here we set k = 2 planted neurons which satisfy w∗1, w∗2∼U (Sn−1).

64
(a) σ = 0(noiseless)
 (b) σ = 0.05
(c) σ = 0.1
 (d) σ = 0.2
Fig. 32: Averaged test error by training ReLU networks with normalization layer on the regularized non-convex problem
(6) over 10 independent trials. Here we set k = 2 planted neurons which satisfy w∗1 = e1, w∗2 = e2.
(a) σ = 0(noiseless)
 (b) σ = 0.05

65
(c) σ = 0.1
 (d) σ = 0.2
Fig. 33: Averaged test error by training ReLU networks with normalization layer on the regularized non-convex problem
(6) over 10 independent trials. Here we set k = 3 planted neurons which satisfy w∗i = ei(i = 1, 2, 3).
Acknowledgment
This work was partially supported by the National Science Foundation (NSF) under grants ECCS- 2037304, DMS-
2134248, NSF CAREER award CCF-2236829, the U.S. Army Research Oﬃce Early Career Award W911NF-21-1-0242,
Stanford Precourt Institute, and the ACCESS – AI Chip Center for Emerging Smart Systems, sponsored by InnoHK
funding, Hong Kong SAR.
References
[1] D. Amelunxen, M. Lotz, M. B. McCoy, and J. A. Tropp, “Living on the edge: Phase transitions in convex programs
with random data,” Information and Inference: A Journal of the IMA , vol. 3, no. 3, pp. 224–294, 2014.
[2] M. Pilanci and T. Ergen, “Neural networks are convex regularizers: Exact polynomial-time convex optimization
formulations for two-layer networks,” International Conference on Machine Learning (ICML) , 2020.
[3] T. Ergen and M. Pilanci, “Convex geometry and duality of over-parameterized neural networks,” Journal of
Machine Learning Research, vol. 22, no. 212, pp. 1–63, 2021.
[4] ——, “Global optimality beyond two layers: Training deep relu networks via convex programs,” in International
Conference on Machine Learning. PMLR, 2021, pp. 2993–3003.
[5] Y. Wang and M. Pilanci, “The convex geometry of backpropagation: Neural network gradient ﬂows converge to
extreme points of the dual convex program,” International Conference on Learning Representations (ICLR), 2022.
[6] Y. Wang, J. Lacotte, and M. Pilanci, “The hidden convex optimization landscape of two-layer relu neural networks:
an exact characterization of the optimal solutions,” International Conference on Learning Representations (ICLR),
2022.
[7] P. Zhao and B. Yu, “On model selection consistency of lasso,” The Journal of Machine Learning Research, vol. 7,
pp. 2541–2563, 2006.
[8] E. J. Candes and T. Tao, “Decoding by linear programming,” IEEE transactions on information theory , vol. 51,
no. 12, pp. 4203–4215, 2005.
[9] E. J. Candes, “The restricted isometry property and its implications for compressed sensing,” Comptes rendus
mathematique, vol. 346, no. 9-10, pp. 589–592, 2008.
[10] J. Sohl-Dickstein, E. Weiss, N. Maheswaranathan, and S. Ganguli, “Deep unsupervised learning using nonequilib-
rium thermodynamics,” in International Conference on Machine Learning . PMLR, 2015, pp. 2256–2265.
[11] J. Ho, A. Jain, and P. Abbeel, “Denoising diﬀusion probabilistic models,” Advances in Neural Information
Processing Systems, vol. 33, pp. 6840–6851, 2020.
[12] T. Ergen, A. Sahiner, B. Ozturkler, J. Pauly, M. Mardani, and M. Pilanci, “Demystifying batch normalization in
relu networks: Equivalent convex optimization models and implicit regularization,” International Conference on
Learning Representations (ICLR), 2022.
[13] T. Ergen and M. Pilanci, “Implicit convex regularizers of cnn architectures: Convex optimization of two- and
three-layer networks in polynomial time,” International Conference on Learning Representations (ICLR) , 2021.
[14] B. Bartan and M. Pilanci, “Neural spectrahedra and semideﬁnite lifts: Global convex optimization of polynomial
activation neural networks in fully polynomial-time,” arXiv preprint arXiv:2101.02429 , 2021.
[15] A. Sahiner, T. Ergen, B. Ozturkler, J. Pauly, M. Mardani, and M. Pilanci, “Unraveling attention via convex duality:
Analysis and interpretations of vision transformers,” International Conference on Machine Learning , 2022.

66
[16] A. Sahiner, T. Ergen, B. Ozturkler, B. Bartan, J. Pauly, M. Mardani, and M. Pilanci, “Hidden convexity
of wasserstein gans: Interpretable generative models with closed-form solutions,” International Conference on
Learning Representations, 2021.
[17] K. He, X. Zhang, S. Ren, and J. Sun, “Deep residual learning for image recognition,” CoRR, vol. abs/1512.03385,
2015. [Online]. Available: http://arxiv.org/abs/1512.03385
[18] A. Jacot, F. Gabriel, and C. Hongler, “Neural tangent kernel: Convergence and generalization in neural
networks,” 2018. [Online]. Available: https://arxiv.org/abs/1806.07572
[19] S. S. Du, X. Zhai, B. Poczos, and A. Singh, “Gradient descent provably optimizes over-parameterized neural
networks,” 2018. [Online]. Available: https://arxiv.org/abs/1810.02054
[20] Z. Allen-Zhu, Y. Li, and Y. Liang, “Learning and generalization in overparameterized neural networks, going
beyond two layers,” arXiv preprint arXiv:1811.04918 , 2018.
[21] C. Liu, L. Zhu, and M. Belkin, “On the linearity of large non-linear models: when and why the tangent kernel is
constant,” Advances in Neural Information Processing Systems , vol. 33, pp. 15 954–15 964, 2020.
[22] D. Zou, Y. Cao, D. Zhou, and Q. Gu, “Stochastic gradient descent optimizes over-parameterized deep relu
networks,” arXiv preprint arXiv:1811.08888 , 2018.
[23] Z. Allen-Zhu, Y. Li, and Z. Song, “A convergence theory for deep learning via over-parameterization,” in
International Conference on Machine Learning . PMLR, 2019, pp. 242–252.
[24] Z. Allen-Zhu, Y. Li, and Y. Liang, “Learning and generalization in overparameterized neural networks, going
beyond two layers,” Advances in neural information processing systems , vol. 32, 2019.
[25] L. Chizat, E. Oyallon, and F. Bach, “On lazy training in diﬀerentiable programming,” 2018. [Online]. Available:
https://arxiv.org/abs/1812.07956
[26] S. Arora, S. Du, W. Hu, Z. Li, and R. Wang, “Fine-grained analysis of optimization and generalization for
overparameterized two-layer neural networks,” in International Conference on Machine Learning . PMLR, 2019,
pp. 322–332.
[27] Z. Chen, Y. Cao, D. Zou, and Q. Gu, “How much over-parameterization is suﬃcient to learn deep relu networks?”
arXiv preprint arXiv:1911.12360 , 2019.
[28] B. Neyshabur, Z. Li, S. Bhojanapalli, Y. LeCun, and N. Srebro, “The role of over-parametrization in generalization
of neural networks,” in International Conference on Learning Representations, 2018.
[29] S. Hochreiter and J. Schmidhuber, “Flat minima,” Neural computation, vol. 9, no. 1, pp. 1–42, 1997.
[30] S. Jastrzkebski, Z. Kenton, D. Arpit, N. Ballas, A. Fischer, Y. Bengio, and A. Storkey, “Three factors inﬂuencing
minima in sgd,” arXiv preprint arXiv:1711.04623 , 2017.
[31] L. Wu, Z. Zhu et al. , “Towards understanding generalization of deep learning: Perspective of loss landscapes,”
arXiv preprint arXiv:1706.10239 , 2017.
[32] P. Goyal, P. Doll´ ar, R. Girshick, P. Noordhuis, L. Wesolowski, A. Kyrola, A. Tulloch, Y. Jia, and K. He, “Accurate,
large minibatch sgd: Training imagenet in 1 hour,” arXiv preprint arXiv:1706.02677 , 2017.
[33] E. Hoﬀer, I. Hubara, and D. Soudry, “Train longer, generalize better: closing the generalization gap in large batch
training of neural networks,” arXiv preprint arXiv:1705.08741 , 2017.
[34] V. Luo and Y. Wang, “How many factors inﬂuence minima in sgd?” arXiv preprint arXiv:2009.11858 , 2020.
[35] R. Ge, R. Kuditipudi, Z. Li, and X. Wang, “Learning two-layer neural networks with symmetric inputs,” arXiv
preprint arXiv:1810.06793, 2018.
[36] A. Bakshi, R. Jayaram, and D. P. Woodruﬀ, “Learning two layer rectiﬁed neural networks in polynomial time,”
in Conference on Learning Theory. PMLR, 2019, pp. 195–268.
[37] Y. Tian, “An analytical formula of population gradient for two-layered relu network and its applications in
convergence and critical point analysis,” in International Conference on Machine Learning . PMLR, 2017, pp.
3404–3413.
[38] M. Soltanolkotabi, “Learning relus via gradient descent,” arXiv preprint arXiv:1705.04591 , 2017.
[39] Y. Li and Y. Yuan, “Convergence analysis of two-layer neural networks with relu activation,” arXiv preprint
arXiv:1705.09886, 2017.
[40] X. Zhang, Y. Yu, L. Wang, and Q. Gu, “Learning one-hidden-layer relu networks via gradient descent,” in The
22nd international conference on artiﬁcial intelligence and statistics . PMLR, 2019, pp. 1524–1534.
[41] K. Zhong, Z. Song, P. Jain, P. L. Bartlett, and I. S. Dhillon, “Recovery guarantees for one-hidden-layer neural
networks,” in International conference on machine learning . PMLR, 2017, pp. 4140–4149.
[42] T. M. Cover, “Geometrical and statistical properties of systems of linear inequalities with applications in pattern
recognition,” IEEE transactions on electronic computers , no. 3, pp. 326–334, 1965.
[43] M. Yuan and Y. Lin, “Model selection and estimation in regression with grouped variables,” Journal of the Royal
Statistical Society: Series B (Statistical Methodology) , vol. 68, no. 1, pp. 49–67, 2006.
[44] R. Vershynin, High-dimensional probability: An introduction with applications in data science . Cambridge
university press, 2018, vol. 47.

67
[45] S. A. Van De Geer and P. B¨ uhlmann, “On the conditions used to prove oracle results for the lasso,” Electronic
Journal of Statistics , vol. 3, pp. 1360–1392, 2009.
[46] V. De la Pena and E. Gin´ e, Decoupling: from dependence to independence. Springer Science & Business Media,
2012.
[47] B. Ghorbani, S. Mei, T. Misiakiewicz, and A. Montanari, “Linearized two-layers neural networks in high
dimension,” The Annals of Statistics , vol. 49, no. 2, pp. 1029–1054, 2021.