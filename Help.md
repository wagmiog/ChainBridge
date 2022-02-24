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


