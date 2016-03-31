# Installing Ethereum Mining Software

1. Add repositories and install
```
sudo apt-get install software-properties-common
sudo add-apt-repository -y ppa:ethereum/ethereum
sudo add-apt-repository -y ppa:ethereum/ethereum-qt
sudo apt-get update
sudo apt-get install ethereum
```
2. Create account
```
geth account new
```
3. install cpp-ethereum
```
sudo apt-get install cpp-ethereum -y
```
***This is where things got kind of iffy for me***
4. Set max gpu memory allocation
```
export GPU_MAX_ALLOC_PERCENT=95
```
I tried a 100 and it didn't work but 95 seemed to work for me
5. I was not able to get my only geth rpc server running, but this command
   worked and let me mine in an ethereum pool
```
ethminer -G -F http://ethereumpool.co/?miner=35@0x1234568999123asfsdasfd@adc613
```
Those are made up values but, here's the format
```
ethminer -G -F http://ethereumpool.co/?miner=[Hash rate in
MH/s]@[address]@[Optional Rig Name]
```
That seemed to work for me, there were bugs, I'm hoping that I didn't forget a
step in my debugging process, but this should work.....      

Also it first I was getting errors I let it mine for about 3 minutes and we
were good 

***You should carefully monitor gpu temperatures I periodically run:***
```
aticonfig --odgt
```
***My temperature is remaining steady around 70.00 C, but I'm going to
continure to monitor it more cloesly***
