@def title = "Differentiation in Deep Learning"
@def tags = ["deep learning"]


# Differentiation in Deep Learning
{{page_tags}}

When I started to learn Neural Networks,
people kept emphasizing the importance of Back Propagation, that it worths to
thoroughly understand it, that one could not fully grasp and utilise Neural Networks
without it, etc. On the other hand, coding in Deep Learning frameworks like
TensorFlow or PyTorch does not give the feeling that Back Propagation is
that indispensible.

At that time, I took these remarks seriously and read or watched a whole bunch
of videos, books and articles on Backprop.
But I always had had an uneased feeling about Backprop.

With hindsight, the single most used differentiation technique in Deep Learning
is gradient descent, which is taught to almost everyone who has a university degree
and which was discovered long long ago in the history of Mathematics.
So what novelty is there in Deep Learning that has to wait until the 21st century?

### Autodiff
To me, the novelty is automatic differentiation. It is the way computers nowadays efficiently calculate
the differential of a function (when either or both the dimensions of the domain and the codomain is large).

As for Back Propagation, I think what is important is that one really takes a specific example (e.g.
a shallow NN, CNN, RNN, etc.), and figures out the following

- with respect to which variables the gradient is computed
- despite the length and complexity of calculation, how to systematically and correctly carry it out
- subgradient
    - Admittedly, I myself only start to notice this concept since year 2022.
      I plan to write a new post exclusively on it, a draft of which can be found at
      [**here**](/cs/ml/dl/subgradient/ez_viz_with_NN.jl)
    - There seems to be many resources introducing subgradient and related methods for non differentiable
      function optimization, one of which I find particularly good was
      [Lieven Vandenberghe's handouts](http://www.seas.ucla.edu/~vandenbe/ee236c.html)
    - How subgradients can be taken into consideration under the framework of autodiff is
      also a question worth answering. That is, how deep learning frameworks
      (TensorFlow, PyTorch, Flux, etc.) really minimize their loss function when the loss function is not
      differentiable.

Below are a few materials that I particularly recommend:

- Autodiff
  - [Alan Edelman](https://www.youtube.com/watch?v=rZS2LGiurKY&t=1356s)
    - In case you could not manage to find the Juypter notebook that Professor Edelman used in the video, you may try [this one ](https://github.com/phunc20/youtube/blob/master/mit/18.065/spring2018/36-alan_edelman_and_julia/autodiff.ipynb) on my github
  - [Ari Seff](https://www.youtube.com/watch?v=wG_nF1awSSY)
- Backprop
  - [_Backprop: A Simple Case_](/cs/ml/dl/en_nn_andrew_ng.pdf)
    
    This is an article I wrote independently after my first job as a data scientist
    and before my second one. Chronologically, I only discovered the wonderful topic
    of Autodiff months later.

I have mentioned earlier that I had had an uneased feeling about Backprop. By sitting down and scratching
the ideas written in the article, I have realized that Backprop is just a fancy word. It's nothing
but ordinary differentiation. What really matters is that one really carries out an example's calculation
and convince themselves that they have understood.

Even after finishing editing the article in LaTeX, the uneased feeling did not disappear. I thought,

> "Now, theoretically I can carry out the computations in similar examples, but how on Earth should I
> command a computer to do that?"

Indeed, it's simply too complicated if a computer has to go that way. And that's where Autodiff comes
up on stage.


### Flux
TensorFlow, PyTorch, Flux and most Deep Learning frameworks implements autodiff.
The readers of this post could choose any one of them and start to play with it.

It's also very educative to introduce these frameworks to those who starts to learn Calculus.

I have started to write a tutorial of my own on how to use Flux, a Julia DL framework.
In particular, the following article demonstrates how Autodiff could be easily done
in such frameworks:
[`gradient` function in Flux](/cs/julia/Flux/tuto/gradient_jacobien.jl)
