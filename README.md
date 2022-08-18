# cardano-cli commands

## My wallet addresses
```Bash
$(cat /home/nelsonksh/cardano-src/testnet-wallet-01/payment.addr)
$(cat /home/nelsonksh/cardano-src/testnet-wallet-02/payment.addr)
```

## Build an address
[Creating keys and addresses](https://developers.cardano.org/docs/stake-pool-course/handbook/keys-addresses/)

## Making a transaction
**Build a Transaction:**
```Bash
cardano-cli transaction build \
--babbage-era \
--testnet-magic 1097911063 \
--tx-in $TXIN \
--tx-out $ADDR+<Number of Lovelace> \
--change-address $SENDER \
--out-file tx.draft
```
**Sign a Transaction:**
```Bash
cardano-cli transaction sign \
--tx-body-file tx.draft \
--signing-key-file payment.skey \
--testnet-magic 1097911063 \
--out-file tx.signed
```
**Submit a Transaction:**
```Bash
cardano-cli transaction submit \
--testnet-magic 1097911063 \
--tx-file tx.signed
```


## Minting token
**Create policy script**
```Bash
touch my-policy.script
```
Inside it should be
```text
{
    "keyHash": "22117fbd0f86a213ae4f4d824cd0d38eea29e49764ae22f5f50ba3d3",
    "type": "sig"
}
```
