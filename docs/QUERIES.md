# Magma Subgraph Documentation

## Introduction

Welcome to the documentation for the Magma Subgraph, a powerful tool for data processing in the DeFi ecosystem. This subgraph provides a structured representation of on-chain data related to swaps, transactions, tokens, pairs, mints, liquidity positions, factories, day datas, and burns within the Magma DeFi ecosystem. These queries are designed to help developers, researchers, and users access and analyze essential data for various purposes within the DeFi space.

## Queries

### `getSwaps`

This query allows you to retrieve information about swaps, including details such as timestamp, sender, and pair information.

```graphql
query getSwaps {
  swaps {
    to
    timestamp
    sender
    pair {
      volumeUSD
      volumeToken1
      volumeToken0
      untrackedVolumeUSD
      txCount
      trackedReserveKava
      totalSupply
      token1Price
      token1 {
        name
        id
        derivedKava
        decimals
        pairBase {
          createdAtBlockNumber
          createdAtTimestamp
          id
          isStable
          reserve0
          reserve1
          reserveKava
          reserveUSD
          token0Price
          token0 {
            id
            name
            totalLiquidity
            totalSupply
            tradeVolume
            tradeVolumeUSD
            txCount
            untrackedVolumeUSD
          }
        }
      }
    }
  }
}
```

### `getTransactions`

Retrieve transaction data, including timestamps and related swap and mint information.

```graphql
query getTransactions {
  transactions {
    timestamp
    swaps {
      to
      timestamp
      sender
      logIndex
      id
      from
      amountUSD
      amount1Out
      amount1In
      amount0Out
      amount0In
    }
    mints {
      to
      timestamp
      sender
      logIndex
      liquidity
      id
      feeTo
      feeLiquidity
      amountUSD
      amount1
      amount0
    }
  }
}
```

### `getTokens`

This query retrieves token information, including names, IDs, total liquidity, total supply, trade volume, trade volume in USD, and symbols.

```graphql
query getTokens {
  tokens {
    name
    id
    totalLiquidity
    totalSupply
    tradeVolume
    tradeVolumeUSD
    symbol
  }
}
```

### `getPairs`

Access data about trading pairs, including volume, reserves, liquidity, and other important metrics.

```graphql
query getPairs {
  pairs {
    volumeUSD
    volumeToken1
    volumeToken0
    untrackedVolumeUSD
    txCount
    trackedReserveKava
    token1Price
    totalSupply
    token1 {
      decimals
      derivedKava
      id
      name
    }
    token0 {
      decimals
      id
      name
    }
    reserveUSD
    reserveKava
    reserve1
    reserve0
    liquidityProviderCount
    isStable
    id
    createdAtTimestamp
    createdAtBlockNumber
  }
}
```

### `getMints`

Retrieve data about minting transactions, including timestamps, sender information, and related transaction details.

```graphql
query getMints {
  mints {
    to
    timestamp
    sender
    transaction {
      id
      blockNumber
      timestamp
    }
    id
    liquidity
    feeTo
    feeLiquidity
    amountUSD
    amount1
    amount0
  }
}
```

### `getLiquidityPositions`

Access liquidity positions, including user data and pair information.

```graphql
query getLiquidityPositions {
  liquidityPositions {
    id
    liquidityTokenBalance
    user {
      id
      usdSwapped
    }
    pair {
      createdAtBlockNumber
      isStable
      id
      createdAtTimestamp
      volumeUSD
      volumeToken1
      volumeToken0
      untrackedVolumeUSD
      txCount
      totalSupply
      trackedReserveKava
      token1Price
      token1 {
        untrackedVolumeUSD
        txCount
        tradeVolumeUSD
        tradeVolume
        totalSupply
        totalLiquidity
        symbol
        name
        id
        derivedKava
        decimals
      }
      token0 {
        derivedKava
        id
        name
        decimals
        symbol
        untrackedVolumeUSD
        txCount
        tradeVolumeUSD
        tradeVolume
        totalLiquidity
        totalSupply
      }
      reserveUSD
      reserveKava
      reserve1
      reserve0
    }
  }
}
```

### `getFactories`

Retrieve factory data, including information about trading pairs and liquidity.

```graphql
query getFactories {
  factories {
    untrackedVolumeUSD
    txCount
    totalVolumeUSD
    totalVolumeKava
    totalLiquidityUSD
    totalLiquidityKava
    pairCount
    id
  }
}
```

### `getDayDatas`

Access daily data statistics, including transaction counts, total volumes, and liquidity metrics.

```graphql
query getDayDatas {
  dayDatas {
    txCount
    totalVolumeUSD
    totalVolumeKava
    totalLiquidityUSD
    totalLiquidityKava
    id
    date
    dailyVolumeUntracked
    dailyVolumeUSD
    dailyVolumeKava
  }
}
```

### `getBurns`

Retrieve information about burns, including timestamps, sender details, and related transaction information.

```graphql
query getBurns {
  burns {
    to
    timestamp
    sender
    needsComplete
    logIndex
    liquidity
    id
    feeTo
    feeLiquidity
    amountUSD
    amount1
    amount0
    transaction {
      timestamp
      id
      blockNumber
    }
  }
}
```

## Conclusion

The Magma Subgraph provides an extensive set of queries to access valuable data within the DeFi ecosystem. Whether you're a developer looking to build applications, a researcher conducting analysis, or a user seeking insights, these queries offer a powerful way to interact with Magma's on-chain data. Explore and utilize these queries to unlock the full potential of DeFi data processing with Magma.