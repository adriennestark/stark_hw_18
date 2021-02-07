# stark_hw_18

# Building a Proof of Authority Testnet

## Before Getting started
Please be sure that Go Ethereum (aka geth)  blockchain tools have been installed and are saved in a convenient place on your computer. If geth is not installed, you will not be able to build your network. Please also be sure that MyCrypto is installed so you can send test transactions once your network is built.

## Creating your nodes
Since we are building a proof of authority blockchain we will need to create our nodes first so they can be added later when we build our blockchain. First, open a terminal window, then navigate to the blockchain tool folder with your geth, and enter the following command: 

/geth account new --datadir node1

Once the node is created, copy the address into a place where you can find it later. Also, if needed, write down your password as you will need it later.

Repeat this process for the second node, but name it node2.

Hit control + c in your terminal window and hit clear to clear the window.


## Creating your blockchain

Be sure that you are still in your blockchain tools folder with your geth. In your commend line enter the following command: ./puppeth

Next specify a name for your network (no capital letters or special characters allowed!) and hit enter. Select option 2 to Configure new genesis and then select option 1 to create new genesis from scratch. Now we will select option 2 to create clique/proof-of-authority as our consensus algorithm. Now you will need to enter the node addresses that you copied in your first step as the accounts to pre-fund. Hit enter until you move onto the next step and allow the account to be pre-funded with one wei. Hit enter again and then enter your chain ID. Please keep in mind that if you have previously built a genesis, this chain ID should be unique from any others you have created. You will now be brought back to the original menu. This time you will select option 2 to manage your existing genesis and then option 2 again to to expot the genesis configuration. Go into your folder with geth to ensure that you have a file with your networkname.json. Now hit control +c and clear to clear your terminal window.

## Initalizing your nodes

In your cleared terminal window enter the following command ./geth init yournetworkname.json --datadir node1 and then enter again replacing node1 with node2.

## Start mining!

Now we will start mining both nodes! Open a second terminal window as you will need this later. In the first terminal window enter the following command: ./geth -–datadir node1 -–unlock “node1 address copied down earlier” -—mine -–rpc -–allow-insecure-unlock This command should start mining in the first node. Once the mining starts, copy the enode ssomewhere you can find it later. Now go to the second terminal window we we can start mining the second node and enter this command: ./geth -–datadir node2 -–port 30304 -–bootnodes “enode address copied down in last step” –-unlock “node2 address” –mine

Now both nodes should be mining!

## Testing our blockchain

Now open my crypto and create a custom network. The node name will be the name of your genesis, network will be custom, network name will be your genesis name, be sure that the currency is ETH, enter your chain ID, and under URL enter http://127.0.0.1:8545 Once all of the data is entered hit “Save & Use Custom Node.” Next import your keysore file for node1 into the wallet authentication area. When prompted, enter the password. Now go View & Send. Enter the address for node2 and send a transaction from node1 to node2.

## Conclusions

While we did all of this in a testnet environment, this could certainly be applied to actual currency as well. Should you have to stop your network, you can restart using the created genesis and nodes by following the instructions under start mining.

