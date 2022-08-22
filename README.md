## NOSTR Identity from an OPENPGP private key

#### Generate a gpg private key: (skip this is you have one)

```
gpg --full-generate-key
```
<center>
![](https://github.com/RandyMcMillan/nostr-gpg-keys/blob/master/images/full-generate-key.png?raw=true)
</center>
<center>

![](https://github.com/RandyMcMillan/nostr-gpg-keys/blob/master/images/generate-identity.png?raw=true)

</center>

---

#### Export your GPG private key:

```
gpg --export-secret-keys -a 625BB88FB2862FE90D647B9C2D2B78A516B54645 > 625BB88FB2862FE90D647B9C2D2B78A516B54645.private.key.asc
```

#### Edit the file: (with your preferred editor - show invisibles and be sure to NOT add any invisible characters!)

<center>


![](https://github.com/RandyMcMillan/nostr-gpg-keys/blob/master/images/edit-file.png?raw=true)

![](https://github.com/RandyMcMillan/nostr-gpg-keys/blob/master/images/key-material-top.png?raw=true)

![](https://github.com/RandyMcMillan/nostr-gpg-keys/blob/master/images/key-material-bottom.png?raw=true)

</center>


##### We remove non-key material from the file:

```
vim 625BB88FB2862FE90D647B9C2D2B78A516B54645.private.key.asc
```

#### Check file

```
cat 625BB88FB2862FE90D647B9C2D2B78A516B54645.private.key.modified.asc
```

---

#### Create SHA256 hash of the key material:

##### Pipe the key material into the `shasum -a 256` function

```
cat 625BB88FB2862FE90D647B9C2D2B78A516B54645.private.key.modified.asc | shasum -a 256
```

#### The SHA256 hash of the key material:

```
e5299059462a7ab1811bb6f32397a8994b3a491047d37f3da8a9de533baebf21
```

---

#### Log into a Nostr client: [https://nostr.rocks](https://nostr.rocks)


##### Copy/Paste the SHA256 hash value into the client:

VIEW YOUR KEYS:

##### Private Key:

```
e5299059462a7ab1811bb6f32397a8994b3a491047d37f3da8a9de533baebf21
OR
nsec1u55eqk2x9fatrqgmkmej89agn99n5jgsglfh70dg4809xwawhusss7kt7w
```

##### Public Key:

```
8588bf3b6c4377ca58b088b62d6065bfaef8374cfb4d0a3c100a7aea70942249
OR
npub1skyt7wmvgdmu5k9s3zmz6cr9h7h0sd6vldxs50qspfaw5uy5yfysamkxp9
```

NOTE: I have included the key material used in this demo to ensure you are doing things correctly.

NOTE: IF YOU CHANGE THE PASSWORD ON YOUR GPG KEY - THE KEY MATERIAL WILL CHANGE. SO BACK UP the file you created in the process!!! 

#### Redo the process to ensure that you did everything correctly!

---

### Deterministic-Alias-Account:

```
 cat 625BB88FB2862FE90D647B9C2D2B78A516B54645.private.key.modified.asc | shasum -a 256 | sed 's/  -//' | shasum -a 256 | sed 's/  -//' > 74d40be79c58ab56a081cd57735edbf3426c600a923cb4234dc76f3bb24e20e8.alias.txt
```

SHA256 hash value:

```
74d40be79c58ab56a081cd57735edbf3426c600a923cb4234dc76f3bb24e20e8
```

##### Private Key:

```
74d40be79c58ab56a081cd57735edbf3426c600a923cb4234dc76f3bb24e20e8
OR
nsec1wn2qheuutz44dgype4thxhkm7dpxccq2jg7tgg6dcahnhvjwyr5qsj9hwp
```

##### Public Key:

```
75ca0a657164d6b083337b85e83f37e9b4782175bedf868b30cffd5141471c17
OR
nsec1wn2qheuutz44dgype4thxhkm7dpxccq2jg7tgg6dcahnhvjwyr5qsj9hwp
```

### Deterministic-Alias-of-an-Alias

```
cat 74d40be79c58ab56a081cd57735edbf3426c600a923cb4234dc76f3bb24e20e8.alias.txt | shasum -a 256  | sed 's/  -//'
71db4b1432fab088ad64e7d4fadcdf303158a379f279fd0f4d257808384ad7d4
```

##### Private Key:

```
71db4b1432fab088ad64e7d4fadcdf303158a379f279fd0f4d257808384ad7d4
OR
nsec1w8d5k9pjl2cg3ttyul204hxlxqc43gme7ful6r6dy4uqswz26l2qz2lmdk
```

##### Public Key:

```
6cf0907bfd76870ef2fd5a026bf4ff6fcba69eca1f382c4a80a47eaf2dfab16a
OR
npub1dncfq7law6rsauhatgpxha8ldl96d8k2ruuzcj5q53l27t06k94qnhlmlu
```