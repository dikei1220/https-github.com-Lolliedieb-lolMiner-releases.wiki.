## Introduction

The Grin C31 fade out has started - or will very soon (from Jan 15th 2020). Recently I get a lot of questions about this and how this affects C31 mining. Many people are concerned about "will my rewards on that now be lower" or "should I switch to C29 or C32 instead" and similar thoughts. This is why I decided to write this article about what is behind the fade out and the implication for miners. 

tl;dr: As long as no one starts mining C32 seriously your are fine to continue as well and nothing will harm your rewards. Then consider a switch to C32.

## About Share Difficulties
To understand the fade out we need to know how Grin balances the number of C29/C31/C32 blocks. For this we need to know the concept of a share difficulty. 

This is rather simple: When ever your miner finds a 42 cycle on a graph (this is what it searches for) the solution found is put into a hash function (Blake2B) and the result is a number **n** between 0 and 2^256-1. Yes, that is a huge number. This number decides how good your found solution is. The smaller it is, the better.

In fact what the miner and a pool will calculate is **d** = 2^256 / **n**. This is the difficulty of your share. Here its: the higher it is, the better for your or the pool.

Usually the miner will compare this difficulty with the one given by the pool if its good enough to be send to the pool. If the pool says diff 1 is ok to be submitted, then every solution found passes this threshold. In case of pool diff 4 only approx every 4th share will make it over this barrier. The pool uses this mechanism to control how many shares it gets from you and thus how much traffic it receives. The rule here is: the higher the pool diff the less traffic it receives, but also the harder it is for the pool to accurately estimate your hash rate.   

## About Scale Rates
Now we know when the miner will send a share to the pool. But when can the pool create a block? On every normal chain with only one PoW for this there is the so called network difficulty controlling this. A block then can be created when ever ShareDiff >= NetworkDiff. Easy isn't it?

Well for Grin this doesn't work, because we have more then just one PoW. In Grin we need to take the so called scale factors into account, that modify the condition for block creation to  ShareDiff * PoW-Scale >= NetworkDiff. So there are two factors determining if a block can be created: the one if the NetworkDiff, which mainly has the job to keep the average number of blocks near one block per minute. The second are the scale factors which have the job to balance how many blocks of which of the proof of were schemes are approximately created per day.

## And how high this Scale factors?
Well this is the tricky part. First you need to know that there are two groups of PoWs in Grin. The first group are the primary PoW schemes, which are C31+ - the plus stands for that also higher instances like C32, C33, C34 ... are in this group. **Common mistake:** many believe C32 / 33... need to start on the chain. Nope, they are always there and can be mined. But they were too unprofitable ;)

The proof of work schemes from this first group have most of the time a constant scale factor. For C**n** this is ![n * 2^(n-23)](https://latex.codecogs.com/gif.latex?n%20%5Ccdot%202%5E%7Bn-23%7D). So for C31 we have 31 \* 256 = 7936, C32 has 32 \* 512 = 16384, C33 has 33 \* 1024 = 33792 ....

So to say: any C32 share has a ~2.064 times higher chance to create a block then a C31 one and also every serious pool should reward a C32 higher by this factor. Unfortunately its a bit more then this 2.064x difficult to create a C32 share. Thats why no one mines it, because C31 is plainly more profitable.

By the way if you are massively bored and have enough free RAM (~64TB+) you could try to find a cycle on a C49 graph which at the current grin difficulty would be an instantaneous block no matter how low the share difficulty is (because the scale factor is high enough). Good luck.

   