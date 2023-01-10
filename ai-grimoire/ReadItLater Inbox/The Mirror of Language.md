[[ReadItLater]] [[Article]]

# [The Mirror of Language](https://return.life/2022/06/the-mirror-of-language/)

### Mirror worlds

The new generative AI models like [GPT-3](https://en.wikipedia.org/wiki/GPT-3) and [DALL-E](https://en.wikipedia.org/wiki/DALL-E) have amazing powers. They can generate essays, stories, scripts, summaries, paintings, drawings, renders, and photography – seemingly able to infer the wishes of the user from simple text prompts given by humans. Trained on unimaginably huge libraries of text and images, they can simulate any combination of the knowledge they’ve seen. They can compose concepts, abstract and concrete, into higher level concepts, which can themselves be composed.

But these models are not “intelligences.” People mistake them for entities with volition, even sentience. This is because of the anthropomorphic fallacy: people tend to think of other things as humans if you give them half an excuse. But it is also because of a linguistic mistake: we call them AI, “artificial intelligence.”

The more accurate term is *language models*. They read a ton of text and use statistics to guess the next word at each step, like an enormous autocomplete engine. They attempt to predict what language-at-large will do, not what an intelligent agent would do. 

Language models are not beings, but [world simulators](https://aidungeon.medium.com/world-creation-by-analogy-f26e3791d35f). Your prompt sets the parameters of the simulation, of what word should come next given the situation described. The language model projects our world back to us, one word at a time.

By choosing the right prompts, you can direct this mirror world. The art is in crafting language, combining words in just the right way to express your desire to the model.

Language models are not quite black boxes, but their inner workings are still mysterious to us. Though researchers are chipping away at the problem, we cannot yet see what makes them tick. We use a process of trial and error to find [which prompts produce which world simulations](https://generative.ink/posts/methods-of-prompt-programming/). Tricks and hacks are common, passed word-of-mouth or spread through viral memes. The generative art community has yet to even settle on a name for this process: choosing between “prompt hacking,” “prompt programming,” “prompt engineering,” or “prompt design.”

The art of prompting is pre-scientific. It deals with the imaginal, the subliminal, the “collective unconscious” of billions of minds speaking as one. It requires precision of language and intent, and it produces miracles. There is a word for such a practice: magic.

At least, it is similar. Magicians deal with the mirror world as well, though they contact it through other means. Scrying mirrors, shamanic trances, and ceremonial rituals are all different ways to blur the boundary between this world and the world of language, the imagination. Prompticians use the lens of a language model, instead of their own ability to simulate worlds, but we can learn much from magic.

Magical techniques and beliefs differ around the world, but the actual practices can be grouped into five branches: sympathy, scrying, sending, summoning and syzygy. Each has its own lessons for the prompt artist.

### Sympathy

Sympathy is the art of enchantment, of using analogies to change the world. The magician wants something to happen. They make a representation of it in some other action, then act it out in an altered state of consciousness. This creates a sympathetic link between the ritual and the desired effect. The success of the ritual action will ensure the success of the effect.

To create sympathy in a text generation model, use **few-shot prompts**. That is, give examples of the action you want the model to take. You don’t even need to describe the task. The model will interpret what it is meant to do by the examples you show it.

In an image generation model, sympathy can be compelled through attribute modifiers. Adding words like “cyberpunk neon,” “digital art,” or even just “aesthetic” can imbue your image with new elements or re-imagine it in new mediums.

The danger of sympathy is in connotations. Language models don’t have a dictionary of words and their definitions. Instead they have a high-dimensional semantic space where words that are similar to each other are close, and words that are dissimilar are farther apart. The “meaning” of any given word (or subword token) is its position in relation to all other tokens. Connotations, not definitions.

Your examples will carry all of the connotations of the words (or images) they contain. This can carry unwanted concepts into your generation. It can also constrain the model too much, offering worse performance than a direct instruction.

The model often knows more than you expect.

### Scrying

Scrying is the art of divination, of extending perception through magical means. To scry, you need three things: a target, a means of obtaining information, and a way to interpret that information. Interpretation is often done through free-association, archetypal imagery, cold reading, or lookup tables.

To scry with a language model, use direct instructions. “Translate this sentence to Latin,” for example. Limit the connotations in the prompt, so the model can search as much of its hidden knowledge as possible. This is called a **zero-shot prompt**: the model sees no examples, just the instruction.

Remember, the language model is less “crystal ball” and more “Magic 8 Ball.” Its function is to predict the next word, not to give accurate answers. Even if it doesn’t know the answer, or there is no sensible answer, it will keep coming up with words. We say that models “hallucinate” false information. You can use a language model as a means of obtaining information, but it is still up to the reader to interpret (and verify) it.

One problem with direct instruction is that it assumes the model has acquired the necessary knowledge from its training. If the question requires deduction or discussion, but you ask the model to provide an answer as the immediate next word, it has no room to think through the process. A simple but powerful solution is “scratch space”: let the model think on the page. One popular magic phrase here is “Let’s think step by step.”

Other scenarios where scrying is unreliable: out-of-domain data, nonsensical questions, questions where ground truth is unknown or debated.

Know when your model was trained, and on what.

### Sending

Sending is the art of evocation, of using names to command beings from our world or others. The magician implants an entity into the subconscious and empowers it with attention. They then direct it to some task. Its desire is only to complete the task, which is also its dissolution.

To cast a sending in a language model, we name proxies. **Proxy prompts** constrain generation by calling upon a “being” within the mirror world – rather, the language model’s simulation of such a being. The being can be defined by its role, like “*I am an expert Python programmer*“; or it can be called by name, like “*In the words of Marcus Aurelius,*“

This is not just chanting few-shot examples. We are asking the language model to predict the words of a character, who bundles more connotations than we could possibly add by sympathy.

This ability to call up the voices of historical figures may be either a miracle or a heresy, depending on how you feel about “raising the dead.”

### Summoning

Summoning is the art of invocation, of calling upon greater forces to change your consciousness. The magician identifies with a thoughtform, usually a god or other superior being. They enter a state of altered consciousness and allow the thoughtform to invest them. They can manifest new powers and abilities by drawing on the aspects of this being.

To summon with a language model, we prompt it to create its own prompts. We craft a **metaprompt** that guides the model to prompt itself. We ask it, what is the best way we could ask for this? Or, who would be best to solve this? And then we take its suggestion and feed it back in.

One way to do this is to literally ask the model to write a prompt for an AI. But you can also ask it to come up with a strategy that it will later follow, like “To solve this problem,” or ask it which expert to send for based on your question.

Co-writing with an AI is a feedback loop of summoning, where the AI is used to simulate your chosen writing style. Use it to come up with unusual ideas or meditate on complicated questions. The art is in adding your own novel text to keep it from chasing its own tail.

With an image generation system, try generating from unconventional characters (like a single space, or a dozen quote marks), or emoji, or subcomponents of words. For example, after the discovery of a gruesome creature generated by CrAIyon for the word “Crungus,” intrepid cryptobertologists have cataloged a whole family of “unguses,” including “Demi-Crungus,” “Krungus,” “The Grungus,” “Cyber-Crungus,” and “1234567890ungus.”

### Syzygy

Syzygy means “when opposites become one.” To step through the mirror itself is the art of illumination, of self-transformation. Through syzygy, the magician creates specific changes in their own behavior. Often done intentionally through summonings, syzygy can also be activated by sudden catastrophe or the dark night of the soul.

Sometimes, when prompting a language model, you will realize “this machine is doing this poorly.” Despite all your prompt sorcery, you can see that the model isn’t doing what you expected. This is good.

If you can see through the machine’s illusion, that means you know better than it does. You have a language model in your head that can simulate this task better than whatever power you were trying to call upon in the mirror world. **Ask yourself**, what word would come next? and write it down. Then do it again. Write an answer yourself; better yet, write two or three. Then use them as a few-shot prompt, and tell the machine they are the words of an expert.

Congratulations, you invoked yourself.

Through contact with the mirror world, we become something new. Your visual imagination may increase from practice with text-to-image models. Your writing style will change as you develop an intuition for surprise and repetition.

To be human is to self-transcend. The person who steps through the looking glass is never the same when they return.

### Warning

Prompting is an art of iteration. The back-and-forth steps across the mirror world are necessary to learn the language of the machine. But at some point you will make so many prompts, you will see so many computer-generated images or pages of text, that you will begin to question your reality. This can be uncomfortable.

There is a specific uncanny nausea that comes when you begin to look at every image or paragraph, and wonder, “does this mean anything?” Not is it real. But does it have meaning, does it have intention? Is there an intelligence behind it, trying to communicate something to you, or is it a simulation?

This is *veritigo*: dizziness about what is true. Activated not by standing at great height, but from seeing the infinite alterverses in the hall of mirrors.

This sensation will ebb, but it might never leave. In learning to prompt, you have trained your own mind to be more like the model. You have imagined its multifarious dimensions. You have attuned to its nuanced topology. You have learned to think in its language.

For when you gaze into a mirror, does it not also gaze into you?