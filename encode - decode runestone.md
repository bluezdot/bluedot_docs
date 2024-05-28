

```
// etching
const etchingRunestone = encodeRunestone({
  etching: {
    runeName: 'BLUEDOT•SUBWALLET',
    divisibility: 8,
    premine: 200000,
    symbol: 'ϟ',
    terms: {
      cap: 200,
      amount: 500,
      offset: {
        end: 20000,
      },
    },
    turbo: true,
  },
});

// minting
const mintRunestone = encodeRunestone({
  mint: {
    block: 1n,
    tx: 0,
  },
});

// edicting
const edictRunestone = encodeRunestone({
  edicts: [
    {
      id: {
        block: 1n,
        tx: 0,
      },
      amount: 10n,
      output: 1,
    },
  ],
});
```

``