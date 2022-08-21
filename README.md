## NOSTR Identity from an OPENPGP private key

#### Generate a gpg private key: (skip this is you have one)

```
gpg --full-generate-key
```

---

#### Export your GPG private key:

` gpg --list-secret-keys`

```
gpg --export-secret-keys -a 625BB88FB2862FE90D647B9C2D2B78A516B54645 > 625BB88FB2862FE90D647B9C2D2B78A516B54645.private.key.asc
```

#### Edit the file: (with your preferred editor - show invisibles and be sure to NOT add any invisible characters!)

##### We remove non-key material from the file:

```
vim 625BB88FB2862FE90D647B9C2D2B78A516B54645.private.key.asc
```

#### Check file

```
cat 625BB88FB2862FE90D647B9C2D2B78A516B54645.private.key.modified.asc
```

#### Create SHA256 hash of the key material:

##### Pipe the key material into the `shasum -a 256` function
```
cat 625BB88FB2862FE90D647B9C2D2B78A516B54645.private.key.modified.asc | shasum -a 256
```

#### The SHA256 hash of the key material:
```
f5231c2c627a271367cab0f7a2b78331c88558329797e3f320d7ecb891850fe8
```

#### Log into a Nostr client: [https://nostr.rocks](https://nostr.rocks)
##### Copy/Paste the SHA256 hash value into the client:

VIEW YOUR KEYS:

##### Private Key:

```
f5231c2c627a271367cab0f7a2b78331c88558329797e3f320d7ecb891850fe8
OR
nsec17533ctrz0gn3xe72krm69durx8yg2kpjj7t78ueq6lkt3yv9pl5qdnxht2
```

##### Public Key:

```
5651d7adfb059e365969face5a2929dc8ab44d4eb4331cafff8cefccc82a2d35
OR
npub12ega0t0mqk0rvktflt8952ffmj9tgn2wkse3etll3nhuejp2956s24n4a7
```
NOTE: I have included the key material used in this demo to ensure you are doing things correctly. 

#### Redo the process to ensure that you did everything correctly!