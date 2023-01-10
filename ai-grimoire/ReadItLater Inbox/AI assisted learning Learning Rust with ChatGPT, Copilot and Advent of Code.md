[[ReadItLater]] [[Article]]

# [AI assisted learning: Learning Rust with ChatGPT, Copilot and Advent of Code](https://simonwillison.net/2022/Dec/5/rust-chatgpt-copilot/)

I’m using this year’s [Advent of Code](https://adventofcode.com/2022) to learn Rust—with the assistance of [GitHub Copilot](https://github.com/features/copilot) and OpenAI’s new [ChatGPT](https://openai.com/blog/chatgpt/).

I think one of the most exciting applications of large language models is to support self-guided learning. Used the right way, a language model such as GPT-3 can act as a sort of super-smart-and-super-dumb teaching assistant: you can ask it questions and follow-up questions, and if you get your questions right it can genuinely help you build a good mental model of the topic at hand.

And it could also hallucinate and teach you things that are entirely divorced from reality, but in a very convincing way!

I’ve started thinking of them as an excellent teacher for some topics who is also a conspiracy theorist around others: you can have a great conversation with them, but you need to take everything they say with a very generous grain of salt.

I’ve been tinkering with this idea for a few months now, mostly [via the GPT-3 Playground](https://simonwillison.net/2022/Jun/5/play-with-gpt3/). ChatGPT provides a much better interface for this, and I’m ready to try it out for a larger, more structured project.

#### Learning Rust

I’ve been looking for an excuse to explore [Rust](https://www.rust-lang.org/) for a few years now. As primarily a Python programmer the single biggest tool missing from my toolbox is something more low-level—I want to be able to confidently switch to more of a systems language for performance-critical tasks, while still being able to use that optimized code in my Python projects.

Rust feels like the best available option for this. It has a really great Python integration support, is already used extensively in the Python ecosystem (e.g. by the [cryptography package](https://cryptography.io/en/latest/)) and lots of people who I respect have used it without loudly expressing their distaste for it later on!

The problem was finding the right project. I learn by building things, but none of the projects I could imagine building in Rust (a high performance web proxy for example) would be useful to me if I built terrible versions of them while still learning the basics.

[Advent of Code](https://adventofcode.com/) turns out to be perfect for this.

Each day you get a new exercise, designed to be solved in a short amount of time (at least so far). Exercises are automatically graded using an input file that is unique to you, so you can’t cheat by copying other people’s answers (though you can cheat by copying and running their code).

The exercise design is *so good*! Eric Wastl has been running it for seven years now and I couldn’t be more impressed with how it works or the quality of the exercises so far (I just finished day 5).

It’s absolutely perfect for my goal of learning a new programming language.

#### AI assisted learning tools

I’ve seen a bunch of people this year attempt to solve Advent of Code by feeding the questions to an AI model. That’s a fun exercise, but what I’m doing here is a little bit different.

My goal here is to get comfortable enough with basic Rust that I can attempt a larger project without feeling like I’m wasting my time writing unusably poor code.

I also want to see if AI assisted learning actually works as well as I think it might.

I’m using two tools to help me here:

-   [GitHub Copilot](https://github.com/features/copilot) runs in my VS Code editor. I’ve used it for the past few months mainly as a typing assistant (and for [writing things like repetitive tests](https://til.simonwillison.net/gpt3/writing-test-with-copilot)). For this project I’m going to lean a lot more heavily on it—I’m taking advantage of comment-driven prompting, where you can add a code comment and Copilot will suggest code that matches the comment.
-   [ChatGPT](https://openai.com/blog/chatgpt/). I’m using this as a professor/teaching-assistant/study partner. I ask it questions about how to do things with Rust, it replies with answers (and usually a code sample too). I’ve also been using it to help understand error messages, which it turns out to be *incredibly* effective at.

#### And copious notes

I’m doing all of my work on this in the open, in my [simonw/advent-of-code-2022-in-rust](https://github.com/simonw/advent-of-code-2022-in-rust) repository on GitHub. Each day gets an issue, and I’m making notes on the help I get from the AI tools in detailed issue comments.

Here are my issue threads so far:

-   [Day 1: Calorie Counting](https://github.com/simonw/advent-of-code-2022-in-rust/issues/1)
-   [Day 2: Rock Paper Scissors](https://github.com/simonw/advent-of-code-2022-in-rust/issues/3)
-   [Day 3: Rucksack Reorganization](https://github.com/simonw/advent-of-code-2022-in-rust/issues/4)
-   [Day 4: Camp Cleanup](https://github.com/simonw/advent-of-code-2022-in-rust/issues/5)
-   [Day 5: Supply Stacks](https://github.com/simonw/advent-of-code-2022-in-rust/issues/6)
-   [Day 6: Tuning Trouble](https://github.com/simonw/advent-of-code-2022-in-rust/issues/8)

I recommend checking out each issue in full if you want to follow how this has all been going.

#### Some examples from ChatGPT

Here are a few highlights from my interactions with ChatGPT so far:

-   Using [“add comments explaining every single line”](https://github.com/simonw/advent-of-code-2022-in-rust/issues/1#issuecomment-1334161700) to cause it to output a replacement code example with extremely verbose comments.
-   Pasting in [both the code and the resulting Rust compiler error](https://github.com/simonw/advent-of-code-2022-in-rust/issues/3#issuecomment-1336192850)—ChatGPT clearly explained the error to me and spat out a version of the code that incorporated a fix!
-   Another example of [a back-and-forth conversation](https://github.com/simonw/advent-of-code-2022-in-rust/issues/4#issuecomment-1336194817)—I started with “Given two strings in Rust, identify the character that appears in both strings”, then said “Can you do this without a HashSet?”, then finally asked for it “without any modules” at all. Then I said “Turn that into a function I can call” and it wrote that code for me too.
-   I got an error from a VS Code extension I was using: “rust-analyzer failed to discover workspace”—so [I pasted that into ChatGPT](https://github.com/simonw/advent-of-code-2022-in-rust/issues/4#issuecomment-1336250499) and it gave me step-by-step instructions for fixing that.
-   I pasted in some gnarly nested code generated by Copilot, and ChatGPT [suggested an improvement that removed the nesting](https://github.com/simonw/advent-of-code-2022-in-rust/issues/4#issuecomment-1336255628) without me even asking it how that code could be improved. Though amusingly it used deprecated Rust syntax for it, which took me quite a while to figure out.
-   Amos has [a series of posts](https://fasterthanli.me/series/advent-of-code-2022/part-3) about this year’s Advent of Code where he uses them to illustrate advanced features of Rust. I occasionally paste his code into ChatGPT and ask it to explain each concept—in [this particular case](https://github.com/simonw/advent-of-code-2022-in-rust/issues/4#issuecomment-1336261936), I used Copilot to generate a list of questions and then pasted them into ChatGPT to get back the answers.
-   Given two examples of how to do something, I asked it [Which of these two options is the more idiomatic Rust code?](https://github.com/simonw/advent-of-code-2022-in-rust/issues/5#issuecomment-1336737517) and it answered along with justification as to why!

#### Handling CLI arguments in Rust

I’ll include my most recent highlight in full:

I wanted to add command-line arguments to my Rust program, so [I asked ChatGPT](https://github.com/simonw/advent-of-code-2022-in-rust/issues/6#issuecomment-1337986027):

> How do I write a Rust program that accepts command line options—a required position argument and an optional --multistack flag?

It replied:

> To write a Rust program that accepts command line options, you can use the `clap` crate. First, add `clap` to your `Cargo.toml` file like this:
> 
> \[dependencies\]
> clap = "2.33.0"
> 
> Next, import the crate and use its macros to define the command line arguments that your program accepts. For example:
> 
> use clap::{App, Arg};
> 
> fn main() {
>     let matches = App::new("My Program")
>         .arg(
>             Arg::with\_name("position")
>                 .help("The position argument")
>                 .required(true)
>                 .index(1),
>         )
>         .arg(
>             Arg::with\_name("multistack")
>                 .help("A flag that enables the use of multiple stacks")
>                 .long("multistack")
>                 .short("m"),
>         )
>         .get\_matches();
> 
>     // Get the value of the position argument
>     let position = matches.value\_of("position").unwrap();
> 
>     // Check if the multistack flag was passed
>     let multistack = matches.is\_present("multistack");
> }
> 
> In this example, the `position` argument is required and must be specified as the first argument to the program. The `multistack` flag is optional and can be specified using the `--multistack` or `-m` flag.

Here’s the thing though: I’m still working on Rust basics, so I didn’t particularly want to jump straight to using an external dependency for this. So I asked a follow-up question:

> Is there a way to do that without using any external crates at all?

And it replied:

> Yes, you can parse command line arguments without using any external crates in Rust. To do this, you can use the `std::env::args` function, which returns an iterator over the arguments that were passed to the program.
> 
> For example, you could parse the required `position` argument and the optional `multistack` flag like this:
> 
> use std::env;
> 
> fn main() {
>     // Get the arguments as an iterator
>     let args: Vec<String\> = env::args().collect();
> 
>     // Ensure that at least one argument was passed
>     if args.len() < 2 {
>         println!("error: missing required argument 'position'");
>         return;
>     }
> 
>     // Get the value of the position argument
>     let position = &args\[1\];
> 
>     // Check if the multistack flag was passed
>     let multistack = args.iter().any(|arg| arg == "--multistack" || arg == "-m");
> }
> 
> In this example, the `position` argument is required and must be specified as the first argument to the program. The `multistack` flag is optional and can be specified using the `--multistack` or `-m` flag.
> 
> You can then use the values of these arguments in your program as shown. Note that this approach does not provide as much functionality or convenience as using a dedicated crate like `clap`, but it can be useful in some situations.

I really like this example.

I deliberately crafted my original question to include details of exactly what I wanted to do—not just add CLI options, but add a specific positional argument and a specific flag.

This generated the exact code I needed, plus a very high quality prose explanation of it.

Then I used a follow-up question to get a completely different approach that better matched my personal taste. Unprompted, it even included a note about the disadvantages of that approach at the end!

#### Copilot as well

I haven’t been keeping as detailed notes on my Copilot interactions, since those take the form of autocompletions in my editor which are harder to write down.

I did capture a few illustrative screenshots though. Some examples:

![I wrote a code comment saying And an extra score based on what I picked X = 1, Y = 2, Z = 3. Copilot suggested: score += me.chars().next().unwrap() as i32 - 'X' as i32 + 1;](ReadItLater%20Inbox/assets/I%20wrote%20a%20code%20comment%20saying%20And%20an%20extra%20score%20based%20on%20what%20I%20picked%20X%20=%201,%20Y%20=%202,%20Z%20=%203.%20Copilot%20suggested%20score%20+=%20me.chars().next().unwrap()%20as%20i32%20-%20'X'%20as%20i32%20+%201;.jpg)

I didn’t like that suggestion at all—way too convoluted. So I changed my comment prompt and got something much better:

![](ReadItLater%20Inbox/assets/copilot-2.jpg)

This comment-driven approach to prompting Copilot has proven to be amazingly effective. I’m learning Rust without having to spend any time looking things up—I’m using Copilot to show me examples, then if I don’t understand them I paste them into ChatGPT and ask for a detailed explanation.

#### Where it goes wrong

An interesting part of this exercise is spotting where things go wrong.

Rust is *not* an easy language to learn. There are concepts like the borrow checker that I’ve not even started touching on yet, and I’m still getting the hang of basic concepts like Options and Results.

Mostly Copilot and ChatGPT have been able to act as confident guides—but every now and then I’ve run up against the sharp edges of their fake confidence combined and the fact that they’re actually just language models with no genuine understanding of what they are doing.

I had one instance where I lost about an hour to an increasingly frustrating back-and-forth over [an integer overflow error](https://github.com/simonw/advent-of-code-2022-in-rust/issues/4#issuecomment-1336249276)—I ended up having to actually think hard about the problem after failing to debug it with ChatGPT!

I wanted to figure out if the first character of a line was a `"1"`. ChatGPT lead me down [an infuriatingly complicated warren](https://github.com/simonw/advent-of-code-2022-in-rust/issues/6#issuecomment-1336783594) of options—at one point I asked it “Why is this so hard!?”—until I finally independently stumbled across `if line.starts_with("1")` which was exactly what I needed. Turns out I should have asked “how do I check if a strings starts with another string”—using the word “character” had thrown it completely off.

I also had an incident where I installed a package using `cargo add itertools` and decided I wanted to remove it. [I asked ChatGPT about it](https://github.com/simonw/advent-of-code-2022-in-rust/issues/5#issuecomment-1336759988) and it confidently gave me instructions on using `cargo remove itertools`... which turns out to be a command that does not exist! It hallucinated that, then hallucinated some more options until I gave up and figured it out by myself.

#### So is it working?

So far I think this is working really well.

I feel like I’m beginning to get a good mental model of how Rust works, and a lot of the basic syntax is beginning to embed itself into my muscle memory.

The real test is going to be if I can first make it to day 25 (with no prior Advent of Code experience I don’t know how much the increasing difficulty level will interfere with my learning) and then if I can actually write a useful Rust program after that without any assistance from these AI models.

And honestly, the other big benefit here is that this is simply *a lot of fun*. I’m finding interacting with AIs in this way—as an actual exercise, not just to try them out—is deeply satisfying and intellectually stimulating.

#### And is this ethical?

The ethical issues around generative AI—both large language models like GPT-3 and image generation models [such as Stable Diffusion](https://simonwillison.net/2022/Sep/5/laion-aesthetics-weeknotes/), continue to be the most complex I’ve encountered in my career to date.

I’m confident that one thing that *is* ethical is learning as much as possible about these tools, and helping other people to understand them too.

Using them for personal learning exercises like this feels to me like one of the best ways to do that.

I like that this is a space where I can write code that’s not going to be included in products, or used to make money. I don’t feel bad about bootstrapping my Rust education off a model that was trained on a vast corpus of data collected without the permission of the people who created it.

(Advent of Code does have a competitive leaderboard to see who can solve the exercises fastest. I have no interest at all in competing on that front, and I’m avoiding trying to leap on the exercises as soon as they are released.)

My current ethical position around these models is best summarized as acknowledging that the technology exists now, and it can’t be put back in its bottle.

Our job is to figure out ways to maximize its benefit to society while minimising the harm it causes.