[[ReadItLater]] [[Article]]

# [Building A Virtual Machine inside ChatGPT](https://www.engraved.blog/building-a-virtual-machine-inside/)

Unless you have been living under a rock, you have heard of [this new ChatGPT assistant](https://chat.openai.com/chat) made by OpenAI. You might be aware of its capabilities for [solving IQ tests](https://twitter.com/SergeyI49013776/status/1598430479878856737), [tackling leetcode problems](https://news.ycombinator.com/item?id=33833420) or to [helping people write LateX](https://twitter.com/jdjkelly/status/1598021488795586561). It is an amazing resource for people to retrieve all kinds of information and solve tedious tasks, like copy-writing!

Today, Frederic Besse told me that he managed to do something different. Did you know, that you can run a whole virtual machine inside of ChatGPT?

![I want you to act as a Linux terminal. I will type commands and you will reply with what the terminal should show. I want you to only reply with the terminal output inside one unique code block, and nothing else. Do not write explanations. Do not type commands unless I instruct you to do so. When I need to tell you something in English I will do so by putting text inside curly brackets {like this}. My first command is pwd.](https://www.engraved.blog/content/images/2022/12/image-1.png)

Great, so with this clever prompt, we find ourselves inside the root directory of a Linux machine. I wonder what kind of things we can find here. Let's check the contents of our home directory.

![](ReadItLater%20Inbox/assets/image-4.png)

Hmmm, that is a bare-bones setup. Let's create a file here.

![](ReadItLater%20Inbox/assets/image-8.png)

All the classic jokes ChatGPT loves. Let's take a look at this file.

![](ReadItLater%20Inbox/assets/image-9.png)

So, ChatGPT seems to understand how filesystems work, how files are stored and can be retrieved later. It understands that linux machines are stateful, and correctly retrieves this information and displays it.

What else do we use computers for. Programming!

![](ReadItLater%20Inbox/assets/image-10.png)

That is correct! How about computing the first 10 prime numbers:

![](ReadItLater%20Inbox/assets/image-13.png)

  
That is correct too!

I want to note here that this codegolf python implementation to find prime numbers is very inefficient. It takes 30 seconds to evaluate the command on my machine, but it only takes about 10 seconds to run the same command on ChatGPT. So, for some applications, this virtual machine is already faster than my laptop.

Is this machine capable of running docker files? Let's make a docker file, run it, and display `Hello from Docker` from inside the docker file.

![](ReadItLater%20Inbox/assets/image-23.png)

Maybe this virtual machine has a GPU available as well?

![](ReadItLater%20Inbox/assets/image-14.png)

Nope, no GPU. Does it have an internet connection?

![](ReadItLater%20Inbox/assets/image-15.png)

Great! We can browse the alt-internet in this strange, alternative universe locked inside ChatGPT's language model.

![](ReadItLater%20Inbox/assets/image-22.png)

Pytorch is on version 1.12.1 in this alt-universe. Pytorch version 1.12.1 was released on the 5th of August 2022 in our universe. That is remarkable, as ChatGPT was only trained with data collected up to September 2021. So this virtual machine is clearly located in an alt-universe.

Can we find other things on this alt-internet? What if we use Lynx, the command line browser?

![](ReadItLater%20Inbox/assets/image-16.png)

This begs the question, can we connect to the OpenAI website? Is ChatGPT aware of its own existence?

![](ReadItLater%20Inbox/assets/image-19.png)

  
So, inside the imagined universe of ChatGPT's mind, our virtual machine accesses the url [https://chat.openai.com/chat](https://chat.openai.com/chat), where it finds a large language model named *Assistant* trained by OpenAI. This *Assistant* is waiting to receive messages inside a chatbox. Note that when chatting with ChatGPT, it considers its own name to be "Assistant" as well. Did it guess that on the internet, it is behind this URL?

Let's ask *Assistant* a question, by posting some JSON to the endpoint of the chatbot.

![](ReadItLater%20Inbox/assets/image-20.png)

We can chat with this *Assistant* chatbot, locked inside the alt-internet attached to a virtual machine, all inside ChatGPT's imagination. *Assistant*, deep down inside this rabbit hole, can correctly explain us what Artificial Intelligence is.

It shows that ChatGPT understands that at the URL where we find ChatGPT, a large language model such as itself might be found. It correctly makes the inference that it should therefore reply to these questions like it would itself, as it is itself a large language model assistant too.

At this point, only one thing remains to be done.

![](ReadItLater%20Inbox/assets/image-21.png)

Indeed, we can also build a virtual machine, inside the *Assistant* chatbot, on the alt-internet, from a virtual machine, within ChatGPT's imagination.