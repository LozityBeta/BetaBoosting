<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Fortnite Boosting Service Calculator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f4;
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    .calculator-container {
      background-color: white;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      max-width: 400px;
      width: 100%;
    }
    h2 {
      text-align: center;
    }
    label {
      font-weight: bold;
    }
    select, input {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
      border-radius: 5px;
      border: 1px solid #ccc;
    }
    .price-display {
      text-align: center;
      font-size: 1.5em;
      margin: 20px 0;
    }
    button {
      background-color: #007bff;
      color: white;
      border: none;
      padding: 10px;
      width: 100%;
      border-radius: 5px;
      font-size: 1em;
    }
  </style>
</head>
<body>

  <div class="calculator-container">
    <h2>Fortnite Boosting Calculator</h2>
    <label for="current-rank">Current Rank:</label>
    <select id="current-rank">
      <option value="bronze-1">Bronze 1</option>
      <option value="bronze-2">Bronze 2</option>
      <option value="bronze-3">Bronze 3</option>
      <option value="silver-1">Silver 1</option>
      <option value="silver-2">Silver 2</option>
      <option value="silver-3">Silver 3</option>
      <option value="gold-1">Gold 1</option>
      <option value="gold-2">Gold 2</option>
      <option value="gold-3">Gold 3</option>
      <option value="platinum-1">Platinum 1</option>
      <option value="platinum-2">Platinum 2</option>
      <option value="platinum-3">Platinum 3</option>
      <option value="diamond-1">Diamond 1</option>
      <option value="diamond-2">Diamond 2</option>
      <option value="diamond-3">Diamond 3</option>
      <option value="elite">Elite</option>
      <option value="champion">Champion</option>
    </select>

    <label for="desired-rank">Desired Rank:</label>
    <select id="desired-rank">
      <option value="bronze-1">Bronze 1</option>
      <option value="bronze-2">Bronze 2</option>
      <option value="bronze-3">Bronze 3</option>
      <option value="silver-1">Silver 1</option>
      <option value="silver-2">Silver 2</option>
      <option value="silver-3">Silver 3</option>
      <option value="gold-1">Gold 1</option>
      <option value="gold-2">Gold 2</option>
      <option value="gold-3">Gold 3</option>
      <option value="platinum-1">Platinum 1</option>
      <option value="platinum-2">Platinum 2</option>
      <option value="platinum-3">Platinum 3</option>
      <option value="diamond-1">Diamond 1</option>
      <option value="diamond-2">Diamond 2</option>
      <option value="diamond-3">Diamond 3</option>
      <option value="elite">Elite</option>
      <option value="champion">Champion</option>
      <option value="unreal">Unreal</option>
    </select>

    <label for="duo-queue">Duo Queue (+50%):</label>
    <input type="checkbox" id="duo-queue">

    <label for="streaming">Streaming (+10%):</label>
    <input type="checkbox" id="streaming">

    <label for="express-delivery">Express Delivery (+15%):</label>
    <input type="checkbox" id="express-delivery">

    <div class="price-display">
      Total Price: <span id="price">0</span> USD
    </div>

    <button onclick="calculatePrice()">Calculate</button>
  </div>

  <script>
    const rankPrices = {
      'bronze-1': (10 - (10 * 0.6)),  // 60% discount applied
      'bronze-2': (15 - (15 * 0.6)),  // 60% discount applied
      'bronze-3': (20 - (20 * 0.6)),  // 60% discount applied
      'silver-1': (25 - (25 * 0.6)),
      'silver-2': (30 - (30 * 0.6)),
      'silver-3': (35 - (35 * 0.6)),
      'gold-1': (40 - (40 * 0.6)),
      'gold-2': (50 - (50 * 0.6)),
      'gold-3': (60 - (60 * 0.6)),
      'platinum-1': (70 - (70 * 0.6)),
      'platinum-2': (85 - (85 * 0.6)),
      'platinum-3': (100 - (100 * 0.6)),
      'diamond-1': (120 - (120 * 0.6)),
      'diamond-2': (150 - (150 * 0.6)),
      'diamond-3': (180 - (180 * 0.6)),
      'elite': (250 - (250 * 0.6)),  // Updated Elite price
      'champion': (300 - (300 * 0.6)),  // Updated Champion price
      'unreal': (500 - (500 * 0.6))
    };

    function calculatePrice() {
      const currentRank = document.getElementById('current-rank').value;
      const desiredRank = document.getElementById('desired-rank').value;
      const duoQueue = document.getElementById('duo-queue').checked;
      const streaming = document.getElementById('streaming').checked;
      const expressDelivery = document.getElementById('express-delivery').checked;

      const currentRankPrice = rankPrices[currentRank];
      const desiredRankPrice = rankPrices[desiredRank];

      if (desiredRankPrice <= currentRankPrice) {
        alert('Please select a higher desired rank than your current rank!');
        return;
      }

      let totalPrice = desiredRankPrice - currentRankPrice;

      if (duoQueue) {
        totalPrice *= 1.5; // Add 50% for duo queue
      }

      if (streaming) {
        totalPrice *= 1.1; // Add 10% for streaming
      }

      if (expressDelivery) {
        totalPrice *= 1.15; // Add 15% for express delivery
      }

      document.getElementById('price').innerText = totalPrice.toFixed(2);
    }
  </script>

</body>
</html>
