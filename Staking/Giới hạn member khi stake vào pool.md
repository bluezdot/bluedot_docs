# Stake trên relaychain/parachain
Mạng ko giới hạn số ng có thể stake cho 1 validator/collator. Mạng chỉ giới hạn số ng có thể nhận được reward, ai cũng có thể stake đc. User chỉ cần vào top nominator/delegator đối với validator/collator đó, tức là stake nhiều hơn ng đang nhận reward mà có lượng stake bé nhất

Vì vậy, validator/collator sẽ có 1 trường data `isCrowded` khi số ng stake vào lớn hơn số ng đc nhận reward. VD: mạng giới hạn 512 nominator đc nhận reward với 1 validator, thì validator sẽ `isCrowded` khi số ng stake > 512. `isCrowded` chỉ là thông tin thêm vào để chú thích, ko ảnh hưởng đến việc user có stake đc cho validator/collator đó hay ko

# Stake vào nomination pool
Nomination pool có giới hạn số member, khi pool đã chạm đến số member này thì user sẽ ko thể stake thêm vào nữa. Nhưng 1 khi đã stake vào pool thì chắc chắn user sẽ nhận đc reward.

Mỗi pool cũng sẽ có data `isCrowded` khi pool vượt ngưỡng về member. Khi có thông tin này thì user sẽ ko thể stake thêm vào pool này

---
- nomination pool: 
	- Vẫn xử lí thông tin `isCrowded` -> Không stake đc khi pool bị đầy.

- relaychain: 
	- Không disable validator bị đầy, xử lí min delegate cho từng collator.
- parachain: 
	- Không disable collator bị đầy, xử lí min delegate cho từng collator.
- amplitude, krest: 
	- Không disable collator bị đầy, xử lí min delegate cho từng collator.
	- Cả mạng chung thông tin max collators mỗi pool

export const _STAKING_CHAIN_GROUP = {  
  relay: ['polkadot', 'kusama', 'aleph', 'polkadex', 'ternoa', 'alephTest', 'polkadexTest', 'westend', 'kate', 'edgeware', 'creditcoin', 'vara_network', 'goldberg_testnet'],  
  para: ['moonbeam', 'moonriver', 'moonbase', 'turing', 'turingStaging', 'bifrost', 'bifrost_testnet', 'calamari_test', 'calamari', 'manta_network', 'polimec'],  
  astar: ['astar', 'shiden', 'shibuya'],  
  amplitude: ['amplitude', 'amplitude_test', 'kilt', 'kilt_peregrine', 'pendulum', 'krest_network'], // amplitude and kilt only share some common logic  
  kilt: ['kilt', 'kilt_peregrine'],  
  nominationPool: ['polkadot', 'kusama', 'westend', 'alephTest', 'aleph', 'kate', 'vara_network', 'goldberg_testnet'],  
  bifrost: ['bifrost', 'bifrost_testnet'],  
  aleph: ['aleph', 'alephTest'], // A0 has distinct tokenomics  
  ternoa: ['ternoa'],  
  liquidStaking: ['bifrost_dot', 'acala', 'parallel', 'moonbeam'],  
  lending: ['interlay'],  
  krest_network: ['krest_network'],  
  manta: ['manta_network']  
};