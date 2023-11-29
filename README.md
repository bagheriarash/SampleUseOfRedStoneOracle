# Sample Use Of RedStone Oracle
A step-by-step guide on how to use RedStone Oracle for your decentralized applications (DApps):

**Step 1: Setting Up the Project**
To kick off your DApp’s development, initiate a new React project using the ‘create-react-app’ command. This forms the foundation for your DApp’s construction.

**Step 2: Integrating RedStone Oracles**
Seamlessly integrate price data by installing the RedStone Oracles package via ‘npm install redstone-oracles’. This enables direct access to RedStone’s robust oracles, powering your application with accurate price information.

**Step 3: Crafting the DApp Interface**
Create the DApp’s interface by editing the ‘tracker.js’ file. This interface allows users to input their ETH and BNB amounts for tracking. Import your custom CSS for styling to enhance the visual appeal.

Here's a sample code snippet for the interface:

```javascript
import React, { useState, useEffect } from "react";
import { RedstoneOracles } from "redstone-oracles";
import "./tracker.css"; // Import your custom CSS for styling

const App = () => {
  const [ethPrice, setEthPrice] = useState(0);
  const [bnbPrice, setBnbPrice] = useState(0);
  const [ethAmount, setEthAmount] = useState(0);
  const [bnbAmount, setBnbAmount] = useState(0);

  useEffect(() => {
    // Get the Ethereum price from RedStone Oracles
    RedstoneOracles.getPrice("ETH", (err, price) => {
      if (err) {
        console.log(err);
        return;
      }
      setEthPrice(price);
    });

    // Get the Binance Coin price from RedStone Oracles
    RedstoneOracles.getPrice("BNB", (err, price) => {
      if (err) {
        console.log(err);
        return;
      }
      setBnbPrice(price);
    });
  }, []);

  return (
    <div className="tracker-container">
      <header className="tracker-header">
        <h1 className="tracker-title">Blockchain Price Tracker</h1>
      </header>
      <main className="tracker-main">
        <section className="price-section">
          <h2>Current ETH Price: $ {ethPrice}</h2>
          <h2>Current BNB Price: $ {bnbPrice}</h2>
        </section>
        <section className="input-section">
          <div className="input-container">
            <input type="number" className="input-field" placeholder="Enter ETH amount" onChange= { (e) => setEthAmount (e.target.value)} />
            <input type="number" className="input-field" placeholder="Enter BNB amount" onChange= { (e) => setBnbAmount (e.target.value)} />
          </div>
        </section>
      </main>
      <footer className="tracker-footer">
        <p className="footer-text">Powered by RedStone Oracles</p>
      </footer>
    </div>
  );
};

export default App;
```

 
A more complex example of a React interface using RedStone Oracles to track the price of a specific NFT (Non-Fungible Token):

```javascript
import React, { useState, useEffect } from "react";
import { RedstoneOracles } from "redstone-oracles";
import Web3 from "web3";

const App = () => {
  const [nftPrice, setNftPrice] = useState(0);
  const [nftId, setNftId] = useState("");
  const [nftContract, setNftContract] = useState("");
  const web3 = new Web3(Web3.givenProvider);

  const getNftPrice = async () => {
    const contract = new web3.eth.Contract(ABI, nftContract);
    const price = await contract.methods.priceOf(nftId).call();
    setNftPrice(web3.utils.fromWei(price, 'ether'));
  };

  useEffect(() => {
    // Get the Ethereum price from RedStone Oracles
    RedstoneOracles.getPrice("ETH", (err, price) => {
      if (err) {
        console.log(err);
        return;
      }
      setEthPrice(price);
    });
  }, []);

  return (
    <div>
      <h1>NFT Price Tracker</h1>
      <input type="text" placeholder="Enter NFT Contract Address" onChange= { (e) => setNftContract(e.target.value)} />
      <input type="text" placeholder="Enter NFT ID" onChange= { (e) => setNftId(e.target.value)} />
      <button onClick={getNftPrice}>Get NFT Price</button>
      <h2>NFT Price: {nftPrice} ETH</h2>
      <p>Powered by RedStone Oracles</p>
    </div>
  );
};

export default App;
```

In this example, the interface allows users to input the contract address and ID of the NFT they want to track. The price of the NFT is fetched from the smart contract using Web3.js and displayed in Ether (ETH). The Ethereum price is fetched from RedStone Oracles. The interface is a bit more complex due to the interaction with the Ethereum blockchain, but it provides a more accurate and up-to-date price for the NFT.


**Step 4: Starting the Project**
Witness your creation in action by launching the project using ‘npm start’. Your DApp will come to life right in your browser.

**Step 5: Testing and Deployment**
Thoroughly test your DApp’s functionality and appearance. Once confident, deploy the DApp for wider usage, allowing others to benefit from its capabilities.


