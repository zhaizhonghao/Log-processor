# Log processor

## Description 

The log processor can extract the ***txNum in a block***,  ***block receive time*** , ***block validation time*** and ***block commit time*** for the log of peer node of Hyperledger Fabric. (The txNum is the number of the transactions in a block).

For example, 

The ***block receive time*** (i.e.,  13:27:54.564) can be extracted from the following log：

```go
[34m2022-06-05 13:27:54.564 UTC [gossip.privdata] StoreBlock -> INFO 294b[0m Received block [252] from buffer channel=mychannel
```

The ***block validation time*** (i.e., 20ms) can be extracted  from the following log:

```go
[34m2022-06-05 13:26:44.967 UTC [committer.txvalidator] Validate -> INFO 096[0m [mychannel] Validated block [252] in 20ms
```

The ***block commit time*** (i.e., 62ms) and the ***txNum*** can be extracted from the following log:

```go
[34m2022-06-05 13:25:22.258 UTC [kvledger] commit -> INFO 02f[0m [mychannel] Committed block [252] with 10 transaction(s) in 62ms (state_validation=0ms block_and_pvtdata_commit=1ms state_commit=55ms) commitHash=[]
```

## Usage

* Rename the log of the peer with "input.log"

* Put the log file into the same directory as the "main.go" file

* Run 

  ```
  go run main.go
  ```

* The program will output three file: ***receive.csv***, ***validate.csv*** and ***commit.csv***.



***receive.csv*** file format:

|receiveTime| blockId |
|----|----|
|x|y|
|...|...|

***validate.csv*** file format:

|blockId| validationTime |
|----|----|
|x|y|
|...|...|

***commit.csv*** file format:

|blockId| txNum | commitTime|
|----|----|----|
|x|y|z|
|...|...|...|