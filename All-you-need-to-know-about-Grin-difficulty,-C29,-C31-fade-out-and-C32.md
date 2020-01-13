## Introduction

The Grin C31 fade out has started - or will very soon (from Jan 15th 2020). Recently I get a lot of questions about this and how this affects C31 mining. Many people are concerned about "will my rewards on that now be lower" or "should I switch to C29 or C32 instead" and similar thoughts. This is why I decided to write this article about what is behind the fade out and the implication for miners. 

tl;dr: As long as no one starts mining C32 seriously your are fine to continue as well and nothing will harm your rewards. Then consider a switch to C32.

## About Share Difficulties
To understand the fade out we need to know how Grin balances the number of C29/C31/C32 blocks. For this we need to know the concept of a share difficulty. 

This is rather simple: When ever your miner finds a 42 cycle on a graph (this is what it searches for) the solution found is put into a hash function (Blake2B) and the result is a number **n** between 0 and 2^256-1. Yes, that is a huge number. This number decides how good your found solution is. The smaller it is, the better.

In fact what the miner and a pool will calculate is ![**d** = 2^256 / **n**](https://latex.codecogs.com/gif.latex?d%20%3D%20%5Cfrac%7B2%5E%7B256%7D%7D%7Bn%7D). This is the difficulty of your share. Here its: the higher it is, the better for your or the pool.

Usually the miner will compare this difficulty with the one given by the pool if its good enough to be send to the pool. If the pool says diff 1 is ok to be submitted, then every solution found passes this threshold. In case of pool diff 4 only approx every 4th share will make it over this barrier. The pool uses this mechanism to control how many shares it gets from you and thus how much traffic it receives. The rule here is: the higher the pool diff the less traffic it receives, but also the harder it is for the pool to accurately estimate your hash rate.   

## About Scale Factors
Now we know when the miner will send a share to the pool. But when can the pool create a block? On every normal chain with only one PoW for this there is the so called network difficulty controlling this. A block then can be created when ever ShareDiff >= NetworkDiff. Easy isn't it?

Well for Grin this doesn't work, because we have more then just one PoW. In Grin we need to take the so called scale factors into account, that modify the condition for block creation to  ShareDiff \* PoW-Scale >= NetworkDiff. So there are two factors determining if a block can be created: the one if the NetworkDiff, which mainly has the job to keep the average number of blocks near one block per minute. The second are the scale factors which have the job to balance how many blocks of which of the proof of were schemes are approximately created per day.

## And how high are this Scale Factors?
Well this is the tricky part. First you need to know that there are two groups of PoWs in Grin. The first group are the primary PoW schemes, which are C31+ - the plus stands for that also higher instances like C32, C33, C34 ... are in this group. **Common mistake:** many believe C32 / 33... need to start on the chain. Nope, they are always there and can be mined. But they were too unprofitable ;)

The proof of work schemes from this first group have most of the time a constant scale factor. For C**n** this is ![n * 2^(n-23)](https://latex.codecogs.com/gif.latex?n%20%5Ccdot%202%5E%7Bn-23%7D). So for C31 we have 31 \* 256 = 7936, C32 has 32 \* 512 = 16384, C33 has 33 \* 1024 = 33792 ....

So to say: any C32 share has a ~2.064 times higher chance to create a block then a C31 one and also every serious pool should reward a C32 higher by this factor. Unfortunately its a bit more then this 2.064x difficult to create a C32 share. Thats why no one mines it, because C31 is plainly more profitable.

By the way if you are massively bored and have enough free RAM (~64TB+) you could try to find a cycle on a C49 graph which at the current grin difficulty would be an instantaneous block no matter how low the share difficulty is (because the scale factor is high enough). Good luck.

For C29 things are a bit different. C29 has a variable scale factor that balances the number of blocks with C29 and C31+ to a pre-defined rate. This started with the genesis block and the target to have 90% C29 blocks and only 10% C31+. When Grin has its 2nd birthday C29 will be deactivated and only C31+ (well C32+ then) will remain, so the scale factor moving towards 0. Slowly but steady. By the way mid December 2019 we reached equilibrium, e.g. the first days with as many C29 as C31+ blocks. 

## And what now about the C31 fade out?
Well what will happen from Jan 15th when C31 will start to fade out? Well over a period of 31 weeks the C31 factor will slowly go down from its current 7936 to 1. And what does this mean for the miner?

Lets assume first no one starts mining C32 at all. Then what happens is: **nothing**. The scale factor will go down, yes, but then the total number of blocks per day does not fit and C29 would be overweight. So what also will happen is that the global difficulty goes down as well (to maintain right number of blocks per day) and the C29 scale will also correct down to get the ratio of C31 / C29 blocks back to balance. And because this is in balance this means that you do not need to fear about your C31 profits: your still competing for same number of blocks per day. Nothing changed.

Nothing? Well we assumed that no one mines C32... but it will happen that someone starts doing so. Why? Because that scale factor does not change! So same scale factor + lower global diff will slowly drive up the C32 profitability. For example when we are 10 weeks into the fade out the C31 scale factor will be at approx 5461 while C32 stays at 16384. Then each C32 share has a 3x higher chance to build a block compared to C31 and that is where it may start making sense mining C32 instead of C31 given the current mining software speeds. 

This then will be the slow death of C31, because C31 and C32 are competing for the same blocks while C29 has its own set. So when C32 profitability surpasses the one of C31 more and more miners will switch over and at some point the last C31 block will be mined. We already miss you good friend.

## What do I need to do now as C31 miner?
In the beginning: Nothing at all - I think is January and also first half of February you are very save on that. Till then you may start some benchmark runs comparing C31 and C32 on your card to compare how much slower C32 is compared to C31. Then monitor the C31 fade out on explorers and see when 16384 / C31 Scale goes above your speed difference ratio. Hint: On 16G cards I would expect the switching time early March, 8G rather later that month or April, but all based on the current miner speeds.  


   