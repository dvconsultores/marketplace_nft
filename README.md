# Venix-back

## Start the Contract

```html
near call cotractowner.your-account.testnet new_default_meta '{ "owner_id": "YOU-OWNERID.testnet", "vault_id": "'YOU-VAULT.testnet'"}'}'  --accountId youraccount.testnet 
```

## Profile 
- Check user profile
```html
near view cotractowner.your-account.testnet get_profile '{"user_id": “USER.testnet"}'  --accountId youraccount.testnet
```

- Create user profile
```html
near call cotractowner.your-account.testnet set_profile '{"name": "hector", "last_name": "palencia", "email": "hpa@gmail.com", "bio": "asdasdasd", "website": "asdasdadsasd"}' --accountId youraccount.testnet
```

- Edit user profile
```html
near call cotractowner.your-account.testnet put_profile '{"name": "Hector Rizziero", "last_name": "Palencia Micarelli", "email": "hpa@gmail.com", "bio": "asdasdasd", "website": "asdasdadsasd"}' 
```

## NFT  ##

## Method near call 

- with Royalty
```html
near call cotractowner.your-account.testnet nft_series '{"token_metadata":{"title": "Naruto Shippuden ch.2: Menolong sasuke","description": "naruto sasuke", "media": "https://upload.wikimedia.org/wikipedia/commons/thumb/0/00/Olympus_Mons_alt.jpg/1024px-Olympus_Mons_alt.jpg", "reference": "bafybeicg4ss7qh5odijfn2eogizuxkrdh3zlv4eftcmgnljwu7dm64uwji", "copies": 100}, "collection": 1, "price":"1000000000000000000000000", "royalty":{"hpalencia.testnet": 1000}}' --accountId venix.hrpalencia.testnet --depositYocto 15200000000000000000000
```

- Royalty free
```html
near call cotractowner.your-account.testnet nft_series '{"token_metadata": {"title": "Naruto Shippuden ch.2: Menolong sasuke", "description": "naruto sasuke", "media": "https://upload.wikimedia.org/wikipedia/commons/thumb/0/00/Olympus_Mons_alt.jpg/1024px-Olympus_Mons_alt.jpg", "reference": "bafybeicg4ss7qh5odijfn2eogizuxkrdh3zlv4eftcmgnljwu7dm64uwji", "copies": 100}, "collection": 1, "price": "1000000000000000000000000"}' --accountId venix.hrpalencia.testnet --depositYocto 15200000000000000000000
```


-  Mine serie
>This function executes successfully only if the caller is the creator of the serial nft.
```html
near call cotractowner.your-account.testnet nft_mint_series '{"token_series_id":"1","receiver_id":"hpalencia.testnet"}' --accountId venix.hrpalencia.testnet --depositYocto 11280000000000000000000
```

- Change serial nft price
>This function is executed successfully only if the caller is the creator of the serial nft. Note: the price parameter is optional, if it is not placed it is automatically assumed that the serial nft is not for sale.
```html
near call cotractowner.your-account.testnet put_nft_series_price '{"token_series_id": "1", "price": "1000000000000000000000000"}' --accountId youraccount.testnet --depositYocto 1
```

- Buy a copy of the nft series
```html
near call cotractowner.your-account.testnet nft_buy '{"token_series_id": "1", "receiver_id": "'venix.hrpalencia.testnet'"}' --accountId youraccount.testnet --depositYocto 1011280000000000000000000
```

- Transfer nft
```html
near call cotractowner.your-account.testnet nft_transfer '{"receiver_id": "'venix.hrpalencia.testnet'", "token_id": "1"}' --accountId youraccount.testnet--depositYocto 1
```


## Method near view

- Query that returns users with more sales
```html
near view cotractowner.your-account.testnet get_Best_sellers
```

- Query nft in user account
```html
near view cotractowner.your-account.testnet nft_tokens_for_owner '{"account_id": "'venix.hrpalencia.testnet'"}'
```
- Query nft series by token id
```html
near view cotractowner.your-account.testnet get_nft_series_single '{"token_series_id": "1"}'
```

- consultar nft series (consulta paginada)
```html
near view cotractowner.your-account.testnet get_nft_series '{"from_index": "0", "limit": 10}'
```

- Query nft series (paginated query)
```html
near view cotractowner.your-account.testnet get_nft_series_creator '{"creator_id": "hrpalencia.testnet", "from_index": "0", "limit": 10}'
```

- Query nft series by creator and by collection (paginated query)
```html
near view cotractowner.your-account.testnet get_nft_series_creator_collection '{"creator_id": "hrpalencia.testnet", "from_index": "0", "limit": 10}' 
```

- Query nft series copies by token id (paginated query)
```html
near view cotractowner.your-account.testnet get_nft_series_copy '{"token_series_id": "1", "from_index": "0", "limit": 10}'
```

- Query to see the ntf for sale (paginated query)
```html
near view cotractowner.your-account.testnet get_market '{"from_index": "0", "limit": 1}'
```

- Query to see the ntf for sale (full query without pagination)
```html
near view cotractowner.your-account.testnet get_market
```

- Query to see the ntf for sale for a specific collection (paginated query)
```html
near view cotractowner.your-account.testnet get_market_collection '{"collection": 1,"from_index": "0", "limit": 1}'
```


- Query to see the ntf for sale by a specific collection (complete query without pagination)
```html
near view cotractowner.your-account.testnet get_market_collection '{"collection": 1}'
```
