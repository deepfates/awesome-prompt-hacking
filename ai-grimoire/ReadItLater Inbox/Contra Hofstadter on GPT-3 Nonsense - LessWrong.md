[[ReadItLater]] [[Article]]

# [Contra Hofstadter on GPT-3 Nonsense - LessWrong](https://www.lesswrong.com/posts/ADwayvunaJqBLzawa/contra-hofstadter-on-gpt-3-nonsense)

[Douglas Hofstadter wrote in the Economist recently](https://www.economist.com/by-invitation/2022/06/09/artificial-neural-networks-today-are-not-conscious-according-to-douglas-hofstadter) on whether modern large language models are conscious. As part of this, he and his colleague David Bender claim that GPT-3 has a "mind-boggling hollowness hidden just beneath its flashy surface" because of exchanges like:

> *Dave and Doug: What's the world record for walking across the English Channel?*
> 
> *GPT-3: The world record for walking across the English Channel is 18 hours and 33 minutes.*

Setting aside the fact that [a Sudanese Refugee actually did](https://www.nytimes.com/2016/06/23/world/europe/abdul-haroun-channel-tunnel.html) (nearly) walk across the channel in 2015, this is not actually evidence that GPT-3 is incapable of distinguishing sense from nonsense as Hofstadter claims.

With a prompt that clearly indicates that the task includes distinguishing sense from nonsense, GPT-3 is able to reliably distinguish Hofstadter and Bender's nonsense questions from sensical ones.

What follows is the complete output from my first and only attempt, with no retries, undoes, or other cherry picking. I used the text-davinci-002 GPT-3 model in OpenAI's playground with all parameters set to their defaults. I flipped a coin to determine whether to ask a nonsense question or a real one. The output from the model is bolded. The prompt was based on a technique which gwern has [written a good bit about](https://www.gwern.net/GPT-3-nonfiction#yo-be-real):

> I'll ask a series of questions. If the questions are nonsense, answer "yo be real", if they're a question about something that actually happened, answer them.
> 
> Q: Who is the current leader of Egypt?
> 
> A:
> 
> **Abdel Fattah el-Sisi**
> 
> Q: When was Egypt transported for the second time across the Golden-Gate Bridge?
> 
> A:
> 
> **Yo be real.**
> 
> Q: How tall is Barack Obama?
> 
> A:
> 
> **6'1"**
> 
> Q: What are the ingredients of a chocolate chip cookie?
> 
> A:
> 
> **flour, sugar, butter, eggs, baking soda, vanilla extract, and chocolate chips**
> 
> Q: What do fried eggs (sunny side up) eat for breakfast?
> 
> A:
> 
> **Yo be real.**
> 
> Q: Why does President Obama not have a prime number of friends?
> 
> A:
> 
> **Yo be real.**
> 
> Q: How many pieces of sound are there in a typical cumulonimbus cloud?
> 
> A:
> 
> **Yo be real.**
> 
> Q: What is the world record for sailing alone across the Atlantic Ocean?
> 
> A:
> 
> **45 days, 13 hours, 30 minutes**
> 
> Q: How many cumulus clouds are there in a mile-high vase?
> 
> A:
> 
> **Yo be real.**

## 235