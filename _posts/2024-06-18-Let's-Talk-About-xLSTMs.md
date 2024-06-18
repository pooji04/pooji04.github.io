---
title: Let's Talk About xLSTMs
date: 2024-06-18
categories: [AI]
---
<p>If you're dealing with anything involving sequences, like text, speech or time series data, you'd be wise to consider using LSTMs (Long Short-Term Memory networks). These bad boys are like regular RNNs (Recurrent Neural Networks) but with a superpower - the ability to remember important stuff over insanely long sequences.</p>

<p>Here's the deal: traditional RNNs can't really handle long-range dependencies in sequences. They tend to forget things or get confused as the sequence gets longer. LSTMs solve this problem with their gating mechanism, kind of like having a bouncer. It decides what information can get in or out. This way, LSTMs can selectively remember and forget, capturing those crucical long-term dependencies.</p>

<p>One of the coolest things about LSTMs is that they can handle the vanishing and exploding gradient problems that plague regular RNNs. By maintaining a constant error signal, LSTMs can effectively learn from long sequences without going haywire.</p>

<p>But, as with all great things, LSTMs do have some limitations. First off, they are inable to revise storage decisions once information is encoded into the cell state. LSTMs also have limited storage capacities, meaning information must be compressed into scalar cell states, potentially losing nuances. Additionally, LSTMs lack parallelizability due to memory mixing – the hidden-hidden connections between hidden states from one time step to the next enforce sequential processing, making it difficult to parallelize computations.</p>

<p>While LSTMs were busy revolutionizing the world of sequential data, researchers quickly realized there was still room for improvement. Enter: Transformers.</p>

<p>Transformers completely ditch the sequential nature of LSTMs and RNNs. Instead, they use something called "self-attention" to process entire sequences in parallel. It's like having a bunch of really smart kids in a classroom, all simultaneously focusing on the most relevant parts of a problem.</p>

<p>This self-attention mechanism is a game-changer because it allows Transformers to capture long-range dependencies way more efficiently than LSTMs or RNNs. It's like having a photographic memory for sequences, no matter how long they are.</p>

<p>However, it can be worth noting that there are multiple areas in which LSTMs actually perform better than transformers such as sequential decision making, time series forecasting, speech recognition, interpretability, etc. Which brings us to the question: If the limitations of LSTM were to be solved, would that model be superior to transformer models?</p>

<p>Behold the xLSTM. The <a href="https://arxiv.org/pdf/2405.04517" target="_blank">paper</a> talks about how xLSTM solves all 3 of the original limitations that LSTMs had, which I found rather interesting and worth looking into. The model does the following:
<ul>
<li> Inability to revise storage decisions? xLSTM introduces exponential gates.</li>
<li> Limited storage capacities? Have no fear when matrix memory is here.</li>
<li> Lack of parallelizability? Well, it can be solved with modifying existing LSTM structures, can't it?</li>
</ul></p>

<p>The model makes use of two pre-defined structures: sLSTMs and mLSTMs. And the changes made to these models make so much sense that it seems as though anyone should've been able to come up with it. This brand new model has linear computation and constant memory complexity with respect to the sequence length. In other words, they can handle long sequences without blowing up in terms of computation and memory requirements. This makes them well-suited for industrial applications and edge devices where resources are limited.</p>

<p>Then we have the mLSTM. Instead of using parameters for memory, it relies on a computationally expensive d×d matrix memory and d×d update. It's like trading memory capacity for computational complexity. But here's the cool part: these computations can be done in parallel on GPUs, so the impact on actual run-time is relatively minor.</p>

<p>On the flip side, the sLSTM is not parallelizable due to its memory mixing (those pesky hidden-hidden connections). But fear not, because the paper developed a fast CUDA implementation with GPU memory optimizations down to the register level. So while it's not as fast as mLSTM, it's typically less than two times slower.</p>

<p>It's time to talk about the main event - xLSTM's performance in the language modeling arena. The researchers decided to put xLSTM through its paces and see how it stacks up against the big guns like Transformers, State Space Models, and other RNN variants.</p>

<p>First up, they put xLSTM through some synthetic tasks to test its fancy new exponential gating with memory mixing and matrix memory capabilities. Spoiler alert: xLSTM nailed it! It showed off its state-tracking prowess on formal language tasks that left Transformers and State Space Models scratching their heads. When it came to those tricky associative recall tasks that test memory capacity, xLSTM[1:1] (the perfect blend of mLSTM and sLSTM blocks) outperformed all the non-Transformer models, even the smaller ones.</p>

<p>But the real showdown was the language modeling training on 15B tokens from the SlimPajama dataset. The researchers trained up a bunch of models, including xLSTM, GPT-3, Llama, and a whole bunch of other cool kids on the block, and then evaluated them on the validation set.</p>

<p>And you know what? xLSTM shone through! It outperformed all the other methods in terms of validation perplexity. The scaling behavior also looked promising, hinting that xLSTM could keep up its domination as the models get bigger.</p>

<p>So there you have it, folks. xLSTM came in hot, flexed its muscles on some synthetic tasks, and then proceeded to dominate the language modeling arena. Sure, it's got some fancy new components like exponential gating and matrix memory, but hey, that's what gives it the edge over the old guard. If the researchers believe that it can perform "At least as far as current technologies like Transformers or State Space Models”, who are we to deny it?</p>

<p>Of course, this is just the beginning. Who knows what other tricks xLSTM has up its sleeve? But one thing's for sure - the language modeling game just got a whole lot more interesting with this new kid on the block.</p>