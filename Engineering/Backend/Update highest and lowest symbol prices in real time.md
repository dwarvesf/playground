---
tags: engineering/backend, nghenhan, hedge-foundation, binance, web-socket
author: Minh Tran
github_id: thminhVN
date: 2023-06-07
icy: 10
---

## Introduction

This technical document outlines a solution to update the highest and lowest prices of millions of symbols in a database in real-time. By leveraging Binance socket data, the aim is to ensure efficient updates without overloading the database with frequent queries.

## Requirement

The primary requirement is to update the highest and lowest prices of a large number of symbols stored in a database. The updates should be based on real-time data received from the Binance socket.

## Challenge

The main challenge arises from the large number of symbol records in the database. Frequent queries to retrieve and update prices for each symbol can lead to unnecessary resource consumption and potentially result in performance issues.

## Approach

To address the challenge mentioned above, the following approach is proposed:

- Maintain an in-memory cache to store the highest and lowest prices for each symbol.
- Establish a WebSocket connection to receive real-time mark prices from Binance.
- Retrieve the second peak timestamp and continuously update the highest and lowest prices for each symbol from that point onwards.
- Implement logic to compare the new prices received through the WebSocket with the cached values.
- Only query the database if a change in the highest or lowest prices is detected.

## Implementation

The implementation of the approach involves the following steps:

1. Establish a WebSocket connection to listen for real-time mark prices from Binance.
2. Retrieve the lowest and highest prices for each symbol from the second peak timestamp to the current time and store them in an in-memory cache.
3. Develop logic to compare the prices received through the WebSocket with the cached values.
4. If a new low or high price is detected, update the corresponding second and third peaks for the symbol in the database.
5. Employ appropriate locking mechanisms to ensure data consistency and prevent conflicts when users modify the date range or access the data concurrently.

### Diagram

A diagram depicting the flow of the implementation can be included here.

![[../../_assets/update-highest-and-lowest-symbol-prices-in-real-time.png|500]]

## Results and Limitations

### Results

By implementing the proposed solution, the following results can be achieved:

- Real-time updates of the second and third peaks for symbol prices can be accomplished without the need for heavy database queries.
- The in-memory cache allows for efficient comparisons and reduces unnecessary database interactions.

### Limitations

The solution has the following limitations:

- Binance socket data updates occur every 1 second, which means there is a possibility of missing new lows or highs during rapid market price fluctuations.

## Work-Around Solution

To mitigate the limitations mentioned above and ensure accurate updates of the second and third peaks, a work-around solution is proposed:

- Implement a long polling service that continuously retrieves data from Binance at shorter intervals.
- By reducing the interval between data retrievals, the likelihood of missing price movements during rapid market changes can be minimized, thus ensuring more accurate updates of the second and third peaks.

---
<!-- CTA -->
### Contributing

At Dwarves, we encourage our people to read, write, share what we learn with others, and [contributing to the Brainery](./CONTRIBUTING.md) is an important part of our learning culture. For visitors, you are welcome to read them, contribute to them, and suggest additions. We maintain a monthly pool of $1500 to reward contributors who support our journey of lifelong growth in knowledge and network.

### Love what we are doing?

- Check out our [products](https://superbits.co)
- Hire us to [build your software](https://d.foundation)
- Join us, [we are also hiring](https://github.com/dwarvesf/WeAreHiring)
- Visit our [Discord Learning Site](https://discord.gg/dzNBpNTVEZ)
- Visit our [GitHub](https://github.com/dwarvesf)