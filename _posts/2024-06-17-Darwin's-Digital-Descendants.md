---
title: Darwin's Digital Descendants
date: 2024-06-27
categories: [AI]
---

<p>Hey there, AI enthusiasts! Buckle up, because we're about to dive into the fascinating realm of model merging. But forget everything you thought you knew about smashing AI models together - we're talking about letting evolution take the wheel, and it's about to get wild!</p>

<h3><b>From Black Box to Pandora's Box of Possibilities</b></h3>

<p>AI has always been a bit of a black box, right? Well, some brilliant minds decided to make that box even more intriguing. They've cooked up a method called Evolutionary Model Merge, and it's about to turn the AI world on its head.</p>

<p>Here's the deal: model merging has been democratizing the AI-building process, making it accessible to everyone. But there's a catch - it relies heavily on human intuition and domain knowledge. And let's face it, human intuition is about as reliable as a chocolate teapot when it comes to the vast, complex world of AI models.</p>

<p>Enter evolutionary algorithms - nature's own optimization technique! These algorithms can explore a vast space of possibilities, discovering novel and counter-intuitive combinations that would make even the most creative human designer scratch their head in bewilderment. It's like unleashing a swarm of super-smart bees to find the sweetest nectar in a field of AI flowers. (My analogies go beyond me sometimes, I apologise.)</p>

<h3><b>The Merging Menagerie: Paramater Space and Data Flow Space</b></h3>

<p>Hold onto your pocket protectors, because we're about to get technical. Our evolutionary approach is operating in two distinct, yet equally mind-bending spaces:</p>
<ol>
<li>Parameter Space (PS): This is where we evolve the weights for mixing parameters at each layer. It's like being a DJ, but instead of mixing beats, you're mixing neural network weights. And just like a DJ, sometimes you create a masterpiece, and sometimes you create something that makes people's ears bleed. The researchers are using some fancy techniques here, like enhancing TIES-Merging with DARE. It's like giving your DJ superpowers to mix tracks from different genres seamlessly.</li>
<li>Data Flow Space (DFS): This is where things get really wild. We're evolving layer permutations, optimizing the very path that tokens take through the neural network. It's like rearranging the rooms in your house, but instead of rooms, it's layers of a neural network, and instead of furniture, it's knowledge. Imagine if you could reorganize your brain to become a genius - that's basically what we're doing here, but for AI.</li>
</ol>

<p>The best part? We're combining both of these approaches into one cohesive framework. It's like if Dr. Frankenstein had access to a supercomputer and decided to play God with AI models. "It's alive!" has never been so appropriate.</p>

<h3><b>The Great Layer Cake Experiment</b></h3>
<p>Now, let's talk about merging in the data flow space. Imagine you're building the world's most complicated layer cake, but instead of cake layers, you're using layers from different AI models. And instead of following a recipe, you're letting an evolutionary algorithm decide which layers to use and in what order.</p>

<p>Here's the kicker: we're not just randomly stacking layers. Oh no, that would be too simple. We're using an indicator array to decide which layers to include or exclude, and we're even scaling the inputs between layers to handle the distribution shift. It's like having a tiny AI sommelier that decides which flavors will pair well together.</p>

<p>And the search space for this layer-stacking extravaganza? It's astronomical. We're talking about 2^T possibilities, where T is the total number of layers times the number of repetitions. It's like trying to find a specific grain of sand on all the beaches in the world, while blindfolded, on a pogo stick. But our evolutionary algorithm is up for the challenge!</p>

<h3><b>Evolution of the Fittest: Nature's Algorithm to the Rescue</b></h3>
<p>Now, we're bringing in the big guns: evolutionary algorithms like CMA-ES (Covariance Matrix Adaptation Evolution Strategy). These algorithms are exploring combinations we mere humans might never think of. It's like giving a bunch of LEGO to a superintelligent child and saying, "Go wild, but make sure it can understand Japanese, do calculus, and write haiku." And somehow, the kid builds a rocket ship that can do all three.</p>

<p>The beauty of this approach is that it's not constrained by human preconceptions. It can discover entirely new architectures, mixing and matching pre-trained transformer blocks. And the best part? Unlike other approaches that require training each candidate model from scratch, this method can evaluate candidates right away.</p>

<h3><b>Cross-Domain Merging: When Models Have an Identity Crisis</b></h3>
<p>Remember that Japanese-speaking, calculus-solving, haiku-writing AI we mentioned? Well, it's not just a pipe dream anymore. The researchers have actually created a Japanese LLM with math reasoning capabilities, and the results are off the charts! They evaluated their models using the Japanese Language Model Evaluation Harness (JP-LMEH) benchmark suite. It's like the Olympics for Japanese language AI, with nine different events. And guess what? Their models scored a whopping 70.5 and 66.2 on average! That's not just good, that's "beating-models-with-ten-times-more-parameters" good.</p>

<p>We're talking about a 7B to 10B parameter model outperforming a 70B parameter Japanese LLM. It's like a lightweight boxer knocking out a heavyweight champ. And it's not just math skills - this AI is showing improvements across the board, from question-answering to other language tasks.</p>

<p>But wait, there's more! They also cooked up a culturally-aware Japanese Vision-Language Model. This isn't just any old image-description AI. No sir, this wonderful thing can describe Japanese culture-specific content better than previous models. It's like if you combined a tour guide, an art critic, and a sushi chef into one AI, and then taught it to paint like Hokusai.</p>

<h3><b>The Secret Sauce: Parameter Space Merging</b></h3>

<p>Now, let's peek behind the curtain and see how they made this AI magic happen. In the parameter space merging, they kept things simple. They treated each source model as one big layer and used two special parameters (they call them DARE-TIES parameters) for each model in the evolutionary merging process. And the result? All three source models turned out to be important, but the Japanese LLM was the star of the show, the guitarist who's just shredding it.</p>

<h3><b>The Evolution of an AI Inference Path</b></h3>

<p>They let evolution design the very path that information follows through the AI. It's like letting natural selection design a highway system for knowledge. Evolution, being the clever girl she is, figured out that the early steps were crucial. It kept almost every layer from the first model, only ditching the last decoding layer and the embedding layer. As the process went on, it got pickier, choosing a smaller set of layers and alternating between the two models.</p>

<p>And get this: they found that the scaling parameters were super important. When they tried to simplify things by setting these parameters to 1, the performance dropped by over 20%. It's like trying to bake a cake without eggs - technically possible, but you're gonna have a bad time.</p>

<h3><b>The Future is Merge (and Evolve)</b></h3>

<p>So, what's the takeaway from all this madness? Well, it looks like the future of AI might just be in letting algorithms discover how to combine different models in ways we never thought possible. This approach isn't just about creating better models - it's about fundamentally changing how we think about model development. It's like we've gone from carefully breeding pedigree dogs to unleashing the full power of evolution to create entirely new species. Who knows, maybe the next breakthrough in AI won't come from a human researcher, but from an evolutionary algorithm that's been let loose in the digital playground of neural networks.</p>

<p>But here's the really exciting part: they're talking about using evolution to search for candidate source models from a vast population of existing models. They're also exploring the idea of producing swarms of diverse foundation models, each with its own niche and behaviors. It's giving me serious "rise of the machines" vibes, but in a cool way.</P>

<p>Of course, there are still some kinks to work out. These merged models can sometimes produce responses that don't make logical sense, and there's always the risk of inheriting limitations from the source models. It's like genetic inheritance, but for AI - sometimes you get your mom's eyes and your dad's nose, and sometimes you get your uncle's tendency to spout nonsense at family dinners. (This isn't written to attack anybody.)</p>

<p>But hey, when has a little thing like "occasional logical incoherence" ever stopped us before? We're talking about people who looked at the human brain and said, "Yeah, we can simulate that."</p>

<p>So there you have it. We're merging models, evolving algorithms, and creating AI Frankensteins that speak multiple languages, solve complex math problems, understand culture-specific content, and maybe even create art. It's a brave new world out there in AI land, and it's only getting weirder. But you know what? I wouldn't have it any other way.</p>

<p>Now, if you'll excuse me, I need to go see if my evolved AI can explain the offside rule in Japanese while solving differential equations, composing a sonnet about the beauty of neural networks, and painting a culturally accurate depiction of a sumo match. Who knows? Maybe it'll even be able to explain why my code never works on the first try. A person can dream, right?</P>
