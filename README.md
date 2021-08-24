# PoA_Blockchain_HW Instructions 

## In order to start the network, the following must be done for a Proof of Authority Blockchain:

### 1) Generate node(s) with an account or two that act as the pre-approved sealer addresses.
Make account(s) for the node(s) of the network with different directories.
The commands in the terminal would be:
./geth --datadir node1 account new
./geth --datadir node2 account new

### 2) Now, you should be able to generate the genesis block & select the Clique (Proof of Authority).
For the first command: ./puppeth -> 2 Configure new genesis -> 1 Create new genesis from scratch -> 2 Clique - proof-of-authority 

### 3) Add account(s) intended for the private chain so they can be pre-funded.
Paste both of the address so they can be pre-funded without the 0x since the terminal will already have it.

### 4) Once back to the main menu, export the files with the following steps.
2 for Manage existing genesis -> 2 Export genesis configurations -> Save file(s) in current folder
![Screenshot (129) - Copy](https://user-images.githubusercontent.com/68878624/130690312-f972aeb6-2a46-4c1a-b8e1-7304d7effcd6.png)
![Screenshot (130)](https://user-images.githubusercontent.com/68878624/130690494-228d0f29-25b5-4496-b9e0-83aec1b8d6b2.png)

### 5) With the genesis block made, initialize the nodes by using geth with these commands.
For Node 1:
./geth --datadir node1 init networkname.json

For Node 2:
./geth --datadir node2 init networkname.json

### 6) Now that the nodes have become operational, attempt to send a test transaction.
This begins with adding the custom node(s) into the application, MyCrypto in this case, and including the following parameters:
- Example below is based on sending the transaction with MyCrypto 
- Node name
- Type of Network
- Network name
- Currency -> Should already be ETH
- Chain/Network ID
- URL 

### With the node added onto MyCrypto, have the following done for both a transaction sent but a check on the transaction status as well
Have the keystore file from the keystore folder within a node available on MyCrypto imported 
- The private key will be imported within completing this step

Send a transaction from the available account

Get the transaction hash & find the status within the "TX Status" part of MyCrypto
![Transaction_metadata_on_MyCrypto](https://user-images.githubusercontent.com/68878624/130690573-53da085b-4a61-4aea-9375-45bde742ef44.png)
![tx_from_node_POV](https://user-images.githubusercontent.com/68878624/130690624-0a4553c4-7dd8-49a9-9f1e-0353e8aadb97.png)

### The nodes will be reactivated & unlocked with the following command(s):
For Node 1: 
./geth --datadir node1 --unlock "SEALER_ONE_ADDRESS" --mine --rpc --allow-insecure-unlock

For Node 2:
./geth --datadir node2 --unlock "SEALER_TWO_ADDRESS" --mine --port 30304 --bootnoes "enode://SEALER_ONE_ENODE_ADDRESS@127.0.0.1:30303" --ipcdisable -allow-insecure-unlock