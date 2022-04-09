---
title: "Blog Start"
date: 2022-04-01T08:38:02+02:00
tags: ["hugo", "quarkus", "first steps"]

---

# Why?

it all started with the blog post [8 Reasons Why You Should Blog as a Developer](https://medium.com/blankpage/8-reasons-why-you-should-blog-as-a-developer-4bc8e7e87c71) and especially the point about communicating clearly, which is becoming more and more important to me as my role shifts from "doer" to "enabler". So it is more important to effectivly instruct others then doing stuff myself.

Additionally i wanted to explore static site generators, so this was the perfect way to do this.

# How?

my dream setup would be to have a templating engine for basic look and feel and an easy way to write new content/posts, so i looked around which static site generators would suit this need the best.

# The Contenders

## Nuxt & Next.js

I deemed these overkill since these Options are based on React/Vue.js, which i have no use for in my blog, since more tech normally leads to a more complex and powerfull solution, this was not what i needed.

## Gatsby

Gatsby seems to be a very complete solution for CMS/Webapp development, but seems to heavily lean towards plugins and extensibility, so i deemed it too complex for my simple blog.

## Jekyll & Hugo

so i was down to the last 2 Contenders: Jekyll & Hugo.

they both seemed pretty similar in using themes as template for the site and simple Markdown files to create content, the CLI seemed simple enough, so everything i needed, i could've gone either way but ended up choosing Hugo, just because the website was nicer to my eyes, so it was a strict assessment about the capabilities ;).

# Hosting

since this is more a learning journey than something anybody should read, the hosting should above all be free, so i searched for small hosting solutions to find the least expensive way to host this blog, i settled on a provider that would've cost about 1€ a month and could've used my existing domain with it. But as i later found a guide in the [Hugo Documentation](https://gohugo.io/hosting-and-deployment/hosting-on-github/) that is could simply use github pages for free, i went with that.

# Customizing

## Theme

after digging through the themes section of hugo for 10 minutes i decided to use [PaperMod](https://github.com/adityatelange/hugo-PaperMod/) because i wanted a clean look and light and dark mode, there were a couple of candidates that fit the bill, but PaperMod was the most reduced and not "retro" one i found.

## Config

now i was greeted with the generated config.yml of hugo and PaperMod, that i tried to strip down to my liking, since i wanted to start with the bare minimum and add things later if the need arises (this is helpful no matter what i learn, since i can easily get caught up in details). This was a pretty straightforward but tedious task, since i had to consult the documentation numerous times, additionally i was a little uncertain how i would be able to remove the icon in the top right corner, since i had no good icon for this blog (nor am i certain there ever will be). In the end my fears were unfounded, because i started to delete line after line of the config and hugo was gracefully deactivating these features without errors or even warnings (great job, hugo team!).

# Problems!!!!!

## live reloading not working

when i was writing this article i noticed that i needed to restart the server to see the changes in my browser, which is not great but would not be a dealbreaker either, but as far is i understood the documentation and the messages during startup, this should work: `Watching for changes in <gitdir>/blog/{archetypes,content,data,layouts,static,themes}`

So i tried to get more info about the source of this, i stumbled upon this [issue](https://discourse.gohugo.io/t/hugo-server-not-refreshing-with-content-change/23858) which seems to concern the same problem but was fixed and closed in 2020, so this didn't help.

I tried a couple of command line arguments from the [hugo server cli doc](https://gohugo.io/commands/hugo_server/) (-w,--disableLiveReload, -D, -F, -v etc.) but nothing changed the behaviour, the next thing that got into my head was that maybe the changes were not "seen" by the server since i start the server in Windows 11's Subsystem for Linux, but change the posts using [GitHub - marktext/marktext: 📝A simple and elegant markdown editor, available for Linux, macOS and Windows.](https://github.com/marktext/marktext) on windows directly, so i touched the files on zsh, but nothing changed.

### Solution (bittersweet)

unfortunatelly i didn't not find the source of this problem, but i was able to fix it by supplying `--poll 1s`to my server start command, now it worked perfectly (even better than i thought since changes are now shown directly in the browser, not as i anticipated when i reload the browser tab) 

# The biggest Question

so what should i write about, since i basically have nothing new to write? I'm not involved in any mailing lists where the latest technologies are discussed and i sit on no board where the fate of the internet is shaped or new RFCs/HTML Features/JCRs are proposed (i mean i COULD participate in all this if i wanted to, since this is all done in the open, but...). So i really only blindly follow the medium post from the "Why?" section and hope to get something out of this for me during this journey, maybe i will become a better communicator, maybe this will lead to me writing 5 best selling novels, but maybe this will all be for nothing, so we'll see.
