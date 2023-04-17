# Welcome to DeFutures

[Our Website](http://eth-tokyo-defutures.s3-website-ap-northeast-1.amazonaws.com/)


- To maximize the user's investment experience, we designed the platform to enable DEX investments and hedging positions with a single ERC20 asset in a single transaction.
- As the hedging products target users who are new to crypto, we designed a user-friendly interface that clearly shows how the user's actions affect their investment returns and risks.
- To calculate values such as strike amount, margin ratio, and tolerance in real-time based on the user's input, we chose to perform complex calculations directly on the front-end instead of fetching pre-computed values from the blockchain.
- We utilized a Typescript-focused technology stack to enable all builders to share their products and provide constructive feedback to each other.


## Inspiration

### Problem

In the recent years, the popularity of futures trading exploded as it returned highest yields, especially in the world of DeFi where high fluctuations exists. Futures trading is proven to provide stability by its hedging mechanism and at the same time maintaining high profit when chosen the right volatility. However, the appearance of futures trading resulted DeFi users to lean more towards profitability in trading that exposes their positions to the heightened price volatility. High gas costs resulted for syncing off-chain data inevitable as well, resulting in a less decentralized dapp, counterfeiting blockchain’s main functions.     

### Solution

We have figured this problem by implementing a fully decentralized futures exchange through integration of on-chain AMM formulas. This easily decides the cost of the position from given amount to buy. This is essential as it solves high gas costs when trying to form a cost in other ways, for instance order book mechanism. Bringing in an existing AMM formula, also helps in deriving a simpler structural mechanism, leading into high scalability and compatibility interchain and layers. Variating futures options in an existing DeFi protocol is expected to induce immense number of user pool and overall TVL.

## What it does

Defutures, a decentralized futures trading exchange, meets users expectations to invest in a way it provides back both stability and high yield returns. Users are open to choices of volatility and a pair of their own desire. 

### Main Functions
`Hedged Liquidation`   
Liquidators choose one pair of an asset, the amount to invest, an asset of either to farm and margin ratio aka. volatility. A portion of the base tokens will be swapped to farm tokens, creating a stake consisting of both tokens with equivalent value. The other portion calculated by volatility will enter futures contract that commits to swapping the farm token back to a predetermined amount of base tokens in the future. One intriguing fact from the function is that it enables both transaction and hedging at one transaction.

`AMM Integration`  
Defutures is fully flexible as it welcomes multiple chains and layers, and to DeFi protocols with an existing AMM. It is structured to focus solely on providing low-risk investment products to the user, and at the same time guaranteeing constant profits. Therefore being designed in a simple, straightforward manner, scalability throughout the entire blockchain system is relatively easily drawn. 

`Market stabilizer`  
Positions from both ends when placed together, this impacts the whole market to stabilize prize fluctuations as it will act as key axis throughout the duration. In other words, more positions the more impact it will strive the market, creating a firm market price dome reaching stability preventing price sudden peaks. This powerful feature is expected to reach high demands as users tend to look for stable, safe products to invest in.

## How we built it

For each AMM defutures integrate with, it will duplicate the same AMM to create its own pricing mechanisms. Both spot trades and futures trades is highly expected to converge to one another as long as arbitrage will be available between the two pairs. Otherwise when arbitrage will not be available, the whole system of futures will break down as there will be no guarantee involved in the pricing system of the futures. Theoretically, syncing futures prices and spot prices every time a position order happens, and daily liquidation occurring based on spot margin will allow the two distinct pairs converge creating one healthy steady pricing system. Assuming the premise is proven true, the following scenario would be satisfied true.

Bob deposits 100 USDT in pair USDC-DOGE, asserting 1 USDC = 10 DOGE.  
Given 10 USDT to be used as margin, addLiquidatedHedged function will divide the other 90 USDT into both USDC and DOGE in both equivalent values, staking them to receive fees throughout the stake duration. For instance, 45 USDT will be swapped to 450 DOGE. The other half of 90 USDT, 45 USDT, will be staked together with 450 DOGE into a pool where fees will be collected. The problem appears as there is no guarantee that 450 DOGE will be swapped back at 45 USDT. If 450 USDT is swapped for a 40 USDT, user’s loss would be greater than the fee user had retrieved. This is where our stabilizer, defutures comes in place, as it uses the 10 USDT as margin to buy a position 450 DOGE → 45 USDT. Risks to a certain point still remains has been greatly reduced. The two following scenario could be drawn to envision our product.


**To provide an example, we will consider `Uniswap`’s CPMM.**

### 1. 1 USDC → 12 DOGE
To maintain 1 USDC → 12 DOGE, the amount staked (45 USDT, 450 DOGE) could be rephrased to 41.08 USDC + 492.95 DOGE, and when expressed in USDC, it will result to 82.16 USDC. This implies 7.84 USDC loss during the stake duration, excluding fees collected. However, at the same time the futures price for 45 USDC is now 540(=45*12) DOGE, implying 90 DOGE as opportunity cost. Including margin of 17.5 USDC (10 USDC as margin, 7.5 USDC from 90 DOGE opportunity cost), despite the price loss of DOGE, Bob secured 99.66 USDC + fees to be collected.

### 2. 1 USDC → 8 DOGE 
Amount staked 45 USDT, 450 DOGE could be recalculated to 50.31 USDC + 402.49 DOGE. This will equivalent to 100.62 USDC. Despite the profit, the position for stabilizing this model, would turn into a loss of opportunity cost. 45 USDC is now 360(=8*12) DOGE, implying 7.5 USDC of loss. Bob however, still secured 103.12(100.62+margin-7.5 USDC) excluding fees to be collected.

The big picture of this product it to allow users to buy stability, broadening choices of investments and getting closer to users’ needs and flavor in investments. 

## Challenges we ran into

Futures Price Formation : As mentioned earlier, a pair is instantiated using the AMM from the DeFi protocol defutures is added on. However, these two are distinct from another and one does not necessarily affect the other in certain cases. Several complex simulations involving compound numeric values had to be dealt with until we could prove the possibility of arbitrage between the two pairs, resulting to convergence from one another.

Security level management: DeFi is finance. It heavily associates with money, where security is most demanded. We had to think of scenarios from scratch where security features should be added especially as futures involve complex mechanisms. Moreover, every functions were designed to be extremely explicit leaving no room for security issues.     

## User Flow 
<img width="3328" alt="Untitled (8)" src="https://user-images.githubusercontent.com/59263564/232258782-25e3f41b-187b-46c9-9226-0e8bf1850fbe.png">


## Before Maturaity & After Maturaity
<img width="3328" alt="Untitled (8)" src="https://user-images.githubusercontent.com/89185836/232258084-d4c31b41-d495-40fa-a826-98e4012d5786.jpeg">


## Defuture has a great potential for expansion
<img width="1824" alt="Untitled (4)" src="https://user-images.githubusercontent.com/59263564/232258787-9e616aa7-935c-43a9-8ee8-2bd92dba270f.png">

