# OP_RETURN transaction
Synonyms:
- Data carrier transaction
- Null data transaction
- OP_RETURN transaction

- **Data carrier transaction**: A transaction type relayed and mined by default in Bitcoin Core 0.9.0 and later that adds arbitrary data to a provably unspendable pubkey script that full nodes don’t have to store in their UTXO database.

- **Not to be confused with:** OP_RETURN (an opcode used in one of the outputs in an OP_RETURN transaction)

# Null data transaction

[Null data](https://developer.bitcoin.org/glossary.html#term-Null-data-transaction) transaction type relayed and mined by default in [Bitcoin Core 0.9.0](https://bitcoin.org/en/release/v0.9.0) and later that adds arbitrary data to a provably unspendable pubkey script that full nodes don’t have to store in their UTXO database. It is preferable to use null data transactions over transactions that bloat the UTXO database because they cannot be automatically pruned; however, it is usually even more preferable to store data outside transactions if possible.

Consensus rules allow null data outputs up to the maximum allowed pubkey script size of 10,000 bytes provided they follow all other consensus rules, such as not having any data pushes larger than 520 bytes.

Bitcoin Core 0.9.x to 0.10.x will, by default, relay and mine null data transactions with up to 40 bytes in a single data push and only one null data output that pays exactly 0 satoshis:

Pubkey Script: OP_RETURN <0 to 40 bytes of data>
(Null data scripts cannot be spent, so there's no signature script.)

Bitcoin Core 0.11.x increases this default to 80 bytes, with the other rules remaining the same.

Bitcoin Core 0.12.0 defaults to relaying and mining null data outputs with up to 83 bytes with any number of data pushes, provided the total byte limit is not exceeded. There must still only be a single null data output and it must still pay exactly 0 satoshis.

The `-datacarriersize` Bitcoin Core configuration option allows you to set the maximum number of bytes in null data outputs that you will relay or mine.

# Opcode explained
[Opcode Explained](https://opcodeexplained.com/opcodes/OP_RETURN.html)

### References:
1. Bitcoin Mastering - Book
2. [Developer Guides — Bitcoin](https://developer.bitcoin.org/devguide/)
