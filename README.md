# Reproduction of what I think is a bug in yarn's offline-mirror pruning mechanism

Here I have a single dependency that I added via its git url with specific commit hash, like
```
yarn add https://github.com/piuccio/cowsay.git#05b895f06c750e83be4d31ad970e3563f6063e0a
```

If I then remove cowsay with
```
yarn remove cowsay
```
yarn will correctly prune all its dependencies but will leave the cowsay package tarball (and I also noticed it doesn't have an extension, which could be confusing things).

On the other hand, if I were to do
```
yarn add cowsay
yarn remove cowsay
```
I'd end up with an empty offline_modules folder as expected.
