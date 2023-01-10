[[ReadItLater]] [[Article]]

# [[Simulators seminar sequence] #1 Background & shared assumptions - LessWrong](https://www.lesswrong.com/posts/nmMorGE4MS4txzr8q/simulators-seminar-sequence-1-background-and-shared)

Crossposted from the [AI Alignment Forum](https://alignmentforum.org/posts/nmMorGE4MS4txzr8q/simulators-seminar-sequence-1-background-and-shared). May contain more technical jargon than usual.

*Meta: Over the past few months, we've held a seminar series on the* [*Simulators theory*](https://www.alignmentforum.org/posts/vJFdjigzmcXMhNTsx/simulators) *by janus. As the theory is actively under development, the purpose of the series is to discover central structures and* [*open problems*](https://www.alignmentforum.org/posts/vJFdjigzmcXMhNTsx/simulators#Next_steps)*. Our aim with this sequence is to share some of our discussions with a broader audience and to encourage new research on the questions we uncover. Below, we outline the broader rationale and shared assumptions of the participants of the seminar.*

*Going into the seminar series, we determined a number of assumptions that we share. The degree to which each participant subscribes to each assumption varies, but we agreed to postpone discussions on these topics to have a maximally productive seminar. This restriction does not apply to the reader of this post, so please feel free to question our assumptions.*

1.  **Aligning AI is a crucial task** that needs to be addressed as AI systems rapidly become more capable.
    1.  (Probably a rather uncontroversial assumption for readers of this Forum, but worth stating explicitly.)
2.  The core part of the **alignment problem involves "deconfusion research."**
    1.  We do not work on deconfusion for the sake of deconfusion but in order to [engineer concepts](https://www.lesswrong.com/posts/9iA87EfNKnREgdTJN/a-revolution-in-philosophy-the-rise-of-conceptual), identify unknown unknowns, and transition from philosophy to mathematics to algorithms to implementation.
3.  The problem is complex because **we have to reason about something that doesn't yet exist.**
    1.  AGI is going to be fundamentally different from anything we have ever known and will thus present us with challenges that are very hard to predict. We might only have a very narrow window of opportunity to perform critical actions and might not get the chance to iterate on a solution.
4.  However, this **does not mean that we should ignore evidence as it emerges.**
    1.  It is essential to carefully consider the GPT paradigm as it is being developed and implemented. At this point, it appears to us more plausible than not that GPT will be a core component of AGI.
5.  One **feasible-seeming approach is "**[**accelerating alignment**](https://openai.com/blog/our-approach-to-alignment-research/)**,"** which involves leveraging AI as it is developed to help solve the challenging problems of alignment**.**
    1.  This is not a novel idea, as it's related to previously suggested concepts such as [seed AI](https://www.lesswrong.com/tag/seed-ai), [nanny AI](https://www.lesswrong.com/tag/nanny-ai), and iterated amplification and distillation (IDA).

## **Simulators refresher**

*Going into the seminar series, we had all read the original* [*Simulators post*](https://www.alignmentforum.org/posts/vJFdjigzmcXMhNTsx/simulators) *by janus. We recommend reading the post in the original but provide a condensed summary as a refresher below.*

> A *fruitful* way to think about GPT is
> 
> -   GPT is a **simulator** (i.e. a model trained with predictive loss on a self-supervised dataset)[\[1\]](https://www.lesswrong.com/posts/nmMorGE4MS4txzr8q/simulators-seminar-sequence-1-background-and-shared#fnb9zte924tyg)
> -   The entities simulated by GPT are **simulacra** (agentic or non-agentic; different objective than the simulator)
> 
> The simulator terminology has appropriate connotations
> 
> -   GPT is not (per se) an oracle, genie, agentic, …
> -   **all GPT “cares about” is simulating/modeling the training distribution**
>     -   log-loss is a proper scoring rule[\[2\]](https://www.lesswrong.com/posts/nmMorGE4MS4txzr8q/simulators-seminar-sequence-1-background-and-shared#fnqquyuy43h2a)

## **Solving alignment with simulators**

*While much of this sequence will focus on the details and consequences of simulator theory, we want to clearly state at the outset that we do this work with the goal of* [*contributing to a solution to the alignment problem*](https://www.alignmentforum.org/posts/vJFdjigzmcXMhNTsx/simulators?commentId=iYwjFxh8NkfoiFu7E)*. In this section, we briefly outline how we might expect simulator theory to concretely contribute to such a solution.*

One slightly[\[3\]](https://www.lesswrong.com/posts/nmMorGE4MS4txzr8q/simulators-seminar-sequence-1-background-and-shared#fnbfrcjj3p18a) naive approach to solving the alignment is to use a strong, GPT-like model as a simulator, prompt it with "`the solution to the alignment problem is`", to cross your fingers and hit `enter`. The list of ways in which this approach fails is hard to exhaust and includes the model's tendency to [hallucinate](https://arxiv.org/abs/2202.03629), the [generally weak reasoning ability](https://arxiv.org/abs/2201.11903), as well as more fundamental [issues with steering simulations](https://www.alignmentforum.org/posts/nXeLPcT9uhfG3TMPS/conditioning-generative-models). Strategies to mitigate some of these problems [have been proposed](https://www.alignmentforum.org/posts/HAz7apopTzozrqW2k/strategy-for-conditioning-generative-models), but (in line with our shared assumptions listed above), we believe that a foundational understanding of simulators is *necessary* in order to enable/ensure positive outcomes.

Conditional on having a foundational understanding of simulators (supported by theorems and empirical results), we hope to be able to construct a simulation (or a set of simulations) that reliably produces useful alignment research. On a high level, it seems wise to optimize for *augmenting* human cognition rather than outsourcing cognitive labor or producing good-looking outputs ([here](https://www.alignmentforum.org/posts/vJFdjigzmcXMhNTsx/simulators?commentId=iYwjFxh8NkfoiFu7E), [here](https://www.alignmentforum.org/posts/vJFdjigzmcXMhNTsx/simulators?commentId=J6nccirDiK4gkTZa9)). We acknowledge the worries of some that constructing a simulator that reliably produces useful alignment research [is an alignment-complete problem](https://www.lesswrong.com/s/TLSzP4xP42PPBctgw/p/DwqgLXn5qYC7GqExF). However, we believe that the simulator framework provides a few key advantages that are afforded by the "non-agency" of simulators:

-   simulators are not as exposed to goodharting since they are not optimizing for an objective (other than predicting the data distribution)
-   simulators (in particular, the simulacra they simulate) are not optimizing for survival by default and thus do not present the same degree of worry about treacherous turns
-   simulators can be configured to simulate many simulacra in tandem and can thus produce a variety of perspectives on a given problem

We hope to substantiate these claims with more rigor over the course of this sequence (or to at least point in the direction in which other alignment researchers might fruitfully work).

1.  **[^](https://www.lesswrong.com/posts/nmMorGE4MS4txzr8q/simulators-seminar-sequence-1-background-and-shared#fnrefb9zte924tyg)**
    
    While a base GPT model trained with the predictive loss approximates a simulator, this property [can get lost with further training](https://www.lesswrong.com/posts/t9svvNPNmFf5Qa3TA/mysteries-of-mode-collapse). When talking about simulators, we tend to think of base GPT without fine-tuning. Understanding how and to which degree the simulator property interacts with fine-tuning is very high on our list of priorities.
    
2.  **[^](https://www.lesswrong.com/posts/nmMorGE4MS4txzr8q/simulators-seminar-sequence-1-background-and-shared#fnrefqquyuy43h2a)**
    
    A proper scoring rule is optimized by predicting the “true” probabilities of the distribution which generates observations, and thus incentivizes honest probabilistic guesses. Log-loss (such as GPT is trained with) is a proper scoring rule.
    
    This means the model is directly incentivized to match its predictions to the probabilistic transition rule which implicitly governs the training distribution. As a model is made increasingly optimal with respect to this objective, the rollouts that it generates become increasingly statistically indistinguishable from training samples, because they come closer to being described by the same underlying law: closer to a perfect simulation.
    
3.  **[^](https://www.lesswrong.com/posts/nmMorGE4MS4txzr8q/simulators-seminar-sequence-1-background-and-shared#fnrefbfrcjj3p18a)**
    
    The proposal is "naive" in the sense that it is by far not pessimistic/prepared enough for the worst-case.
    

## 39

## Ω 19