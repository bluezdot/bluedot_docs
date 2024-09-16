relaychain validators:
- alephZero
- ternoa
- else

APY mạng
```
function calcInflation (api: ApiPromise, totalStaked: BN, totalIssuance: BN, numAuctions: BN): Inflation {  
  const { auctionAdjust, auctionMax, falloff, maxInflation, minInflation, stakeTarget } = getInflationParams(api);  
  const stakedFraction = totalStaked.isZero() || totalIssuance.isZero()  
    ? 0  
    : totalStaked.mul(BN_MILLION).div(totalIssuance).toNumber() / BN_MILLION.toNumber();  
  // Ideal is less based on the actual auctions, see  
  // https://github.com/paritytech/polkadot/blob/816cb64ea16102c6c79f6be2a917d832d98df757/runtime/kusama/src/lib.rs#L531  const idealStake = stakeTarget - (Math.min(auctionMax, numAuctions.toNumber()) * auctionAdjust);  
  const idealInterest = maxInflation / idealStake;  
  // inflation calculations, see  
  // https://github.com/paritytech/substrate/blob/0ba251c9388452c879bfcca425ada66f1f9bc802/frame/staking/reward-fn/src/lib.rs#L28-L54  const inflation = 100 * (minInflation + (  
    stakedFraction <= idealStake  
      ? (stakedFraction * (idealInterest - (minInflation / idealStake)))  
      : (((idealInterest * idealStake) - minInflation) * Math.pow(2, (idealStake - stakedFraction) / falloff))  
  ));  
  
  return {  
    idealInterest,  
    idealStake,  
    inflation,  
    stakedFraction,  
    stakedReturn: stakedFraction  
      ? (inflation / stakedFraction)  
      : 0  
  };  
}
```

![[Pasted image 20240828123421.png]]

APY_{commission}= APY\times (1-commission) \\

APY=\frac{100\times avgStake}{totalValidatorStake}\times APY_{Chain} \\

avgStake = \frac{currentTotalEraStake}{numberOfValidator} 