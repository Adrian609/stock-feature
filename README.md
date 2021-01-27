# stock-feature
adding stock data to a map, sorting it, and outputting top 3 stocks by quantity purchased 

Link to REPL for demo
https://repl.it/@Adrian609/AwesomeCloudySpreadsheets

```js
let stockDetails = new Map();

addStockInfo("AAPL", 400);
addStockInfo("NFLX", 400);
addStockInfo("NFLX", 500);
addStockInfo("AAPL", 400);
addStockInfo("GOOG", 400);
addStockInfo("JPMC", 400);
addStockInfo("FVRR", 1000);
addStockInfo("PINS", 50);

function addStockInfo(stockName, quantity) {
  if (stockDetails.has(stockName)) {
    let addQuantity = stockDetails.get(stockName);
    stockDetails.set(stockName, (quantity += addQuantity));
  } else {
    stockDetails.set(stockName, quantity);
  }
  return stockDetails;
}

function sortStocksByQuantity(stockDetails) {
  let sortedDetails = new Map(
    [...stockDetails.entries()].sort((a, b) => b[1] - a[1])
  );
  return sortedDetails;
}

function getTopThreeStocks(stockDetails) {
  let topThree = new Map(), count = 0;
  for (const [key, value] of sortStocksByQuantity(stockDetails).entries()) {
    count++;
    if (count <= 3) {
      topThree.set(key, value);
    } else {
      break;
    }
  };
  return topThree;
}

console.log('Added Stock Details: \n', stockDetails);
console.log('Sorted Stocks: \n', sortStocksByQuantity(stockDetails));
console.log('Top 3 Stocks: \n', getTopThreeStocks(stockDetails));

```
