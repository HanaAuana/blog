---
title: Hello World
date: 2015-03-22
tags: About
layout: post
---

Welcome! On the roughly 1 year anniversary of getting my first job out of college, I thought it was time to finally get down to business and start writing this blog. I've been meaning to do this for a few years, but kept putting it off for one reason or another. Now that I've gotten things up and running, I hope to make this a somewhat regular part of my personal development. I've started this blog as a multi part endeavor:

1. As a portfolio for my side projects
2. A place to elaborate on my goals, plans, and experiences of building my development skills
3. An opportunity to try out new libraries, frameworks, and techniques in the process of building this blog

The title 'Hana Auana' roughly translated from Hawaiian would be something like 'Modern Work.' I like the adage 'Work smart, not hard' (and I'm sure it resonates with many programmers), but it doesn't capture the whole picture. It's not enough to 'work smart' since this often relies on heuristics, tricks, and 'life hacks' that are based on what's worked in the past. Whether or not you believe there's any substance in all the buzz about 'disruption,' most successful people build something new, or capitalize on some new way of thinking, rather than just rehashing something old in a 'smart' way. Forward-thinking, fresh ideas is what I mean by 'modern' versus just 'smart' work. So let's leave 'working smart' behind, and instead: HanaAuana

## Colophon

On that note, here are some of the things I'm using to both power this blog and expand my skill-set:

* [Github Pages](https://pages.github.com/): I'm hosting this blog and any project pages associated with it using Github Pages. It's free, it's simple, and since I use Github for hosting my code anyway, it's easy to incorporate into my workflow
* [Middleman](https://middlemanapp.com/): I'm generating these pages using Middleman, a Ruby-powered static site generator similar to Jekyll. I'm also using a few extensions to add make [deploying to Github easier](https://github.com/middleman-contrib/middleman-deploy) and to add [a nice, clean theme](https://github.com/danielbayerlein/middleman-casper)
* [Vagrant](https://www.vagrantup.com/): Vagrant is a great way to create lightweight virtual dev environments. Since working with Middleman (and Ruby in general) proved to be a bit of a hassle on Windows, I'm using Vagrant to create a simple Ubuntu box that I can use to develop, build, and deploy these pages
* [Markdown](http://daringfireball.net/projects/markdown/): Markdown is "a text-to-HTML conversion tool for web writers." In other words, you write readable text files, and have them converted into valid HTML using various tools.  One of the great things about Middleman is that I can write posts in Markdown and they'll be automatically converted into these posts during the build process. This post is also a chance for me to "kick the tires" and try out a few Markdown formatting features. 

Those are the main pieces for now, but if I modify what I'm using, I'll do my best to keep this as up to date as possible

## What to expect?

> Be extremely subtle, even to the point of formlessness

This quote from Sun Tzu's The Art of War is one of my favorites. Great for warfare maybe, but not so much for blogs. To give you a rough idea of what I'll be adding here, I've listed some of my interests and goals that I might be covering:

* Web development/design: Obvious. This is a big one, but very important (especially when I'm writing a blog). I've never had much of an eye for design, but practice makes perfect right?
* Algorithms: Due to weird scheduling, I took my algorithms class as one of my last CS classes. I'm eager to continue digging into this rich treasure trove of O(n) goodness
* Machine learning/AI: I took an AI class in college, and it was an eye-opening experience. I'd really like to do some more in this area, particularly with genetic algorithms and recommender systems
* Simulation: Building off of AI, I think the ability to simulate large, complex systems is one of the most fascinating opportunities that computers and programming allow us to take advantage of
* Automation: Repetitive, mundane tasks are the bane of my existence. Let's see what we can make computers do for us instead, shall we?

## Bonus Code Example

As a special super bonus, here's a small snippet from the first big project I worked on: A basic Blackjack game in highschool for my AP Computer Science class. It's not the most elegant, and I definitely like to think the code I write nowadays is better, but it's a good reference point to see how far I've come. I hope you'll enjoy it as well:

```java
public int playHand()
  {
    int playerWon = 0;
    while(playerWon == 0)
    {
      while(playerPlaying == true)
      {
          System.out.println("You have :" );
          player.getHand();
          System.out.println("Your total is :");
          System.out.println(player.getTotal());
          System.out.println("Dealer is showing :");
          System.out.println(dealer.showCard(0));
        if(askForHitOrStand(1) == 1)
        {
          if(cardsUsed < 52)
          {
          player.addCardToHand(deck.dealCard());
          cardsUsed ++ ;
          break;
          
          }
          else
          {
            System.out.println("No more cards,... Shuffling");
            deck.shuffle();
            player.addCardToHand(deck.dealCard());
            cardsUsed ++ ;
            break;
          }
          
        }
        else if(askForHitOrStand(1) == 2)
        {
          System.out.println("You Stand.");
          dealerPlaying = true;
          playerPlaying = false; break;
        }
        else
        {
          System.out.println("Error");
        }       
      }
      while(dealerPlaying == true)
      {
        
        System.out.println("Dealer's Turn");
        System.out.println("Dealer has :" );
        dealer.getHand();
        
        if(askForHitOrStand(2) == 1)
        {
          if (cardsUsed < 52)
          {
          dealer.addCardToHand(deck.dealCard());
          System.out.println("Dealer hits.");
          }
          else
          {
            System.out.println("No more cards,... Shuffling");
            deck.shuffle();
            dealer.addCardToHand(deck.dealCard());
            System.out.println("Dealer hits.");
          }
        }
        else if(askForHitOrStand(2) == 2)
        {
          System.out.println("Dealer Stands");
          dealerPlaying = false;
          break;
        }
        else
        {
          System.out.println("Error");
        }       
      }
    }
    if((player.getTotal() - 21) >= (dealer.getTotal() -21))
    {
      playerWon = 2;
    }
    else if ( (player.getTotal() -21) < (dealer.getTotal() - 21))
    {
      playerWon = 1;
    }
    else
    {
      System.out.println("error");
    }
    return playerWon;
  }
```