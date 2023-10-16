# Area51Club
Explanation of how to generate a single image in layers and how to deploy an ERC-721 smart-contract to the blockchain using Remix IDE.

# Generate images

The first thing we must do is generate the images from layers to be able to achieve various combinations with unique attributes. For this we can use several tools, one that I found interesting since it generates the images and also the metadata is the one created by Haslips, here I will provide the link: https://github.com/HashLips/hashlips_art_engine

# Image and metadata storage

In order to generate a url where the smart-contract can interact with the metadata, we will need to use a cloud to host the images and metadata. In this case we use IPFS.
In IPFS we will have to first host the images and COPY the CID with us in order to update it in all the JSON files where the metadata is hosted so that it reveals the location of the image.
Once the CID of the images in the metadata has been updated, we will have to upload the JSON files to IPFS.

# Deploy the smart-contract in Remix IDE

We will open https://remix.ethereum.org/ and create a file with a .sol extension in the contracts folder where we will paste the ERC-721 smart-contract.
First compile our smart-contract in the corresponding Solidity version (in our case it is v0.8.12) and we will activate the enable optimization option at 200.
Finally we will go to the deploy and run section, we will connect our wallet and we will choose the corresponding contract and NOT THE INTERFACES. We will choose the name and the symbol and paying the gas fee we will launch it.

# URI Configuration

Once the smart-contract is launched we will have to go to the _setbaseURI writing function and write ipfs://thecidthatgivesyouIPFSofthejsonfile/ and call the function, pay the gas fee and that's it.
Then you can call the _setCost function to modify the price per mint of each token, using uint256, that is, if you want the price per mint to be 1 ether you would have to set it to 1000000000000000000.
Then you can call the _mint function and set the price in ether and the number of NFTs to be minted, the price is price*ether.

# Examples 

Collection: https://opensea.io/collection/area51clubnft

PolygonScan: https://polygonscan.com/address/0x9cd03986a4c8b1c6b1c3273d4121b18fae4e9cfb
