## Troubleshooting

при спробі деплою в девнет отримав помилку

```
anchor deploy --provider.cluster devnet
Deploying cluster: https://api.devnet.solana.com
Upgrade authority: /home/zip/.config/solana/id.json
Deploying program "favorites"...
Program path: /home/zip/favorites/target/deploy/favorites.so...
===========================================================================
Recover the intermediate account's ephemeral keypair file with
`solana-keygen recover` and the following 12-word seed phrase:
===========================================================================
tag lobster defense autumn cream marine equip stone rebel tower sauce final
===========================================================================
To resume a deploy, pass the recovered keypair as the
[BUFFER_SIGNER] to `solana program deploy` or `solana program write-buffer'.
Or to recover the account's lamports, pass it as the
[BUFFER_ACCOUNT_ADDRESS] argument to `solana program close`.
===========================================================================
Error: 5 write transactions failed
There was a problem deploying: Output { status: ExitStatus(unix_wait_status(256)), stdout: "", stderr: "" }.
```

Рішення наступне
```
solana program deploy --use-rpc --url devnet --buffer prompt:// --program-id target/deploy/favorites-keypair.json target/deploy/favorites.so
```