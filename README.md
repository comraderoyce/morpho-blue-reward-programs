## Morpho Blue reward programs

This repository allows you to create your own reward program by submitting a pull request.

### Create a Market program

Market Programs can be added in `src/market-programs.ts` at the end of the `marketPrograms` array. You should send funds to the URD with the funds sender before the start date of the program to validate it.

You can see an example below:

```typescript
export const marketPrograms = [
  {
    start: 1717149233n,
    end: 1718149235n,
    fundsSender: "0x061060a65146b3265C62fC8f3AE977c9B27260fF",
    urdAddress: "0x5aC6F9F696b06538A8A0253ab495dC4c638da3be",
    tokenAddress: "0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913",
    marketId: "0xdba352d93a64b17c71104cbddc6aef85cd432322a1446b5b65163cbbc615cd0c",
    rewardAmount: {
      supply: parseUnits("300000", 18),
      borrow: 0n,
      collateral: 0n,
    },
    chainId: ChainId.MAINNET,
  },
];
```

### Create a Vault program

Vault Programs can be added in `src/vault-programs.ts` at the end of the `vaultPrograms` array. You should send funds to the URD with the funds sender before the start date of the program to validate it.

You can see an example below:

```typescript
export const vaultPrograms = [
  {
    start: 1718719200n,
    end: 1723903200n,
    fundsSender: "0x74Cbb1E8B68dDD13B28684ECA202a351afD45EAa",
    urdAddress: "0x9e3380f8B29E8f85cA19EFFA80Fb41149417D943",
    tokenAddress: "0xA88594D404727625A9437C3f886C7643872296AE",
    vault: "0xc1256Ae5FF1cf2719D4937adb3bbCCab2E00A2Ca",
    amount: parseUnits("4165000", 18),
    chainId: ChainId.BASE,
  },
];
```


### Frequently Asked Questions

1. Where should we get the `urdAddress`?

The URDs are not tied to a specific type of program. The incentive provider must ensure that Morpho Association is the updater of the tree to prevent incorrect tree roots from being published on the URD, which could lead to loss of funds. It is recommended to use the following URDs:

- For Mainnet: [0x330eefa8a787552DC5cAd3C3cA644844B1E61Ddb](https://etherscan.io/address/0x330eefa8a787552dc5cad3c3ca644844b1e61ddb)
- For Base: [0x5400dbb270c956e8985184335a1c62aca6ce1333](https://basescan.org/address/0x5400dbb270c956e8985184335a1c62aca6ce1333)

2. Do the borrow and collateral parameters affect anything? Should we set them to 0?

Yes, they can affect the reward distribution. If your program does not intend to provide rewards for borrowing or collateral, you should set these parameters to 0. Otherwise, you can specify the amount accordingly.