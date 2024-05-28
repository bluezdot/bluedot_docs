## Parachain
- whenExecutation = parachainStaking.delegationScheduledRequests(addr).whenExecutation
- targetBlock = (whenExecutation - round.current) * round.length * round.first
- remainingBlock = targetBlock - system.number
- targetTimestamp = remainingBlock * BLOCK_TIME + timestamp.now

## Amplitude group
- targetBlock from unstaking(address)
- remainingBlock = targetBlock - system.number
- targetTimestamp = remainingBlock * BLOCK_TIME + timestamp.now

## Relaychain

CurrentEra = staking.activeEra.index
TargetEra = staking.ledger.unlocking.era
RemainingEra = TargetEra - CurrentEra
RemainingTimestampMs = RemainingEra * ERA_TIME * 3600 * 1000

StartTimestampMs = staking.activeEra.start
TargetTimestampMs = StartTimestampMs + RemainingTimestampMs

Notes:
- ERA_TIME sử dụng đơn vị giờ
- Ms (milli giây)

## Nomination Pool

## Era time
eraTime (hours) = const.babe.epochDuration * blockTime * const.staking.sessionsPerEra / 3600
unstakingTime (hours) = eraTime * const.staking.bondingDuration