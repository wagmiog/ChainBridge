# Create Bridge contract on source
Create bridge contract on source
```
npx cb-sol-cli --url $SRC_GATEWAY --privateKey $SRC_PK --gasPrice 22500000000 deploy \
    --bridge --erc20Handler \
    --fee 0.1 \
    --expiry 115792089237316195423570985008687907853269984665640564039457584007913129639935 \
    --relayers $SRC_ADDR \
    --relayerThreshold 1\
    --chainId 0
```


Deploy on destination

```
npx cb-sol-cli --url $DST_GATEWAY --privateKey $DST_PK --gasPrice 25000000000 deploy\
    --bridge --erc20Handler \
    --fee 0.1 \
    --expiry 115792089237316195423570985008687907853269984665640564039457584007913129639935 \
    --relayers $DST_ADDR \
    --relayerThreshold 1 \
    --chainId 1
```


#Add a  resource/bridge a token

add resource on source chain
```
npx cb-sol-cli --url $SRC_GATEWAY --privateKey $SRC_PK --gasPrice 22500000000 bridge register-resource \
    --bridge $SRC_BRIDGE \
    --handler $SRC_HANDLER \
    --resourceId $RESOURCE_ID \
    --targetContract $SRC_TOKEN
```

create a wrapped token on destination
```
npx cb-sol-cli --url $DST_GATEWAY --privateKey $DST_PK --gasPrice 25000000000 deploy\
    --erc20  --erc20Name $DST_TOKEN_NAME --erc20Symbol $DST_TOKEN_SYMBOL 
```

register wrapped token as resource on destination

```
npx cb-sol-cli --url $DST_GATEWAY --privateKey $DST_PK --gasPrice 25000000000 bridge register-resource \
    --bridge $DST_BRIDGE \
    --handler $DST_HANDLER \
    --resourceId $RESOURCE_ID \
    --targetContract $DST_TOKEN

```

The following registers the token as mintable/burnable on the bridge.

```
npx cb-sol-cli --url $DST_GATEWAY --privateKey $DST_PK --gasPrice 25000000000 bridge set-burn \
    --bridge $DST_BRIDGE \
    --handler $DST_HANDLER \
    --tokenContract $DST_TOKEN
```
The following gives permission for the handler to mint new wWEENUS tokens.

```
npx cb-sol-cli --url $DST_GATEWAY --privateKey $DST_PK --gasPrice 25000000000 erc20 add-minter \
    --minter $DST_HANDLER \
    --erc20Address $DST_TOKEN
```


## DEPOSIT
 npx cb-sol-cli --url $SRC_GATEWAY --privateKey $SRC_PK --gasPrice 22500000000 erc20 deposit \                                      
    --amount 100 \
    --dest 1 \
    --bridge $SRC_BRIDGE \
    --recipient $DST_ADDR \
    --resourceId $RESOURCE_ID

## Add a relayer
```
npx cb-sol-cli --url $SRC_GATEWAY --privateKey $SRC_PK --gasPrice 22500000000 admin add-relayer \
    --relayer $RELAYER_TWO_ADDRESS \
    --bridge $SRC_BRIDGE
```

```
npx cb-sol-cli --url $SRC_GATEWAY --privateKey $SRC_PK --gasPrice 22500000000 admin add-relayer \
    --relayer $RELAYER_TWO_ADDRESS \
    --bridge $DST_BRIDGE
```


