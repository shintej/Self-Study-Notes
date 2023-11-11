## Technical Analysis
<details>
<summary>Q. Why do trends exist in the first place?</summary>
<br>  
Ans>>				
Why trends exist: because fundamenally price needs to change. Price movements within the trend are noise, but when fundamentally there is more supply of, say, crude oil in the world than demand, price needs to go down. It does so by trending down. If a stock is undevalued, while the business is developing and dividends are being paid, there will be more people moving into this stock, so it must appreciate. There is no other way to do it in the market, except by trending.

Now for the fun part.

On a shorter time scale, “trends” become more and more random - what looks like a trend is in fact just a statistically uneven distribution. Here’s how it works - if you flip a coin at the frequency of market transactions of a relatively high-liquidity instrument (let’s say 2–3 transactions per second) for a working day (7 hours), you will have about 1200 flips. Inevitably in this amount of totally random outcomes, you will have several series of continuos “heads” or “tails”. If you charted your flips, those completely random series would look like trends.
![Img1](https://qph.cf2.quoracdn.net/main-qimg-f4c0c1fbc2c7785a8fdffdf6824e5a2b-pjlq)

Look at the chart above. Does it look like a downtrend? With pullbacks and all, right?

Ready to be surprised?

It is 100% noise. NO SIGNAL AT ALL.

This chart is of an excel randomly generated sequence of 1250 1s and -1s. Completely random. I didn’t cheat, it’s absolutely a random distribution of +1s and -1s. You can check in excel yourself.
![Img2](https://qph.cf2.quoracdn.net/main-qimg-dcf2e109194d5ac3900c48394304e661-pjlq)

Here’s another one I generated with the same algorythm, just by refreshing the random sequence. Looks just like a market chart, doesn’t it? That’s what a totally random sequence (with equal step increments) looks like.

In this sequence, every next step has ZERO correlation with a previous step. Every “price move” has ZERO dependance on the past moves and thus ZERO predictive power.

EVERYTHING that looks like a trend here is 100% noise.

For me it’s mind-blowing every time I look at the charts. Even though I’ve known this for a long time, every time I see it with my own eyes, it’s like a cold shower.

So how can one differentiate the REAL trends?

The question you are asking is a fundamental question of trading. The Holy Grail of trading, if you will. If a trader can differentiate trend and random noise, he’s got the market in his pocket.

It’s not impossible, but when you start to solve that riddle, you get into more and more complexity. Exactly why it takes work and practice and time to learn trading. Different markets behave differently, and then same markets behave differently at different times. Market behaviour “personalities” surprisingly, just like trends, stay realtively stable for a time, but at some moment inevitably shift (just as trends reverse).

Markets are VERY random, yet it has been statisticlly proven that they are not 100% random. In one of the statistical studies I’ve read, the mathematic outcome was that about 2% of market movement is signal, 98% is noise.

Just two things I know for sure:

Trends exist.
    
The signal/noise ratio gets progressively higher with the increase of statistical sampling -> more transactions means more signal -> higher time frames are very significantly less random than smaler ones (though still very random).
</details>

<details>
    <summary>Q. What is the difference between long term strategies(swing trading etc.) and HFT strategies.</summary>
    <br>
    Ans>>>    
    From what I have read, high frequency trading programs just find an inefficiency in the market and exploit it as fast as they can. IIRC most of their speed comes from implementation efficiency rather than algorithmic efficiency.

They use techniques like:
    Co-locating in the same place as the trading servers for lower latency (100ms)
    Using hand-rolled text processing instead of regular expressions.
    C for speed and efficiency.
    Use faster hardware like GPGPUs and latest CPUs.
    Tuning the size of network packets so that the whole request is sent in one transmission. 

Usually an inefficiency in a market is just an arbitrage i.e, a definite opportunity to buy low and sell high. All these algorithms rely on the fact that there is a time lag between an event and the price change. These opportunities are usually about 1cent per share or less. But, with leverage one can make millions in a day. Here are a few examples:
    It takes a little bit of time for the price of an option to follow a stock and vice versa. If you can precisely model these differences, then one can use a computer to trade favorably.This needs some idea about options pricing and black-sholes model.Look up CUDA docs for the actual algos.    
    Recently, exchanges started charging companies for co-location and ability to see the raw orders that are yet to be processed. Usually when there is a large order from institutional investors the price goes up by about 2 cents. Some high frequency programs monitor these order feeds to buy shares at the current price (from dark pools and other sources) and sell them at a slightly higher price(about 1cent more) to these institutional investors. All this happens in under 5ms.    
    There is also arbitrage in currency markets. Sometimes the prices of currencies vary slightly and take some time to adjust for various reasons. Some high frequency traders write programs to take advantage of this. This is a simple graph algorithm. I am unsure how it is implemented in practice.    
    Similarly, it takes a few milliseconds for bond prices to reflect a fed/govt announcement. High frequency trading programs monitor the fed feeds to buy these bonds at a lower price to sell them immediately at a higher price.    

There are many more arbitrage opportunities like this.
</details>
