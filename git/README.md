## Git Cloning
[Source](https://github.blog/open-source/git/get-up-to-speed-with-partial-clone-and-shallow-clone/)
[Comparisons](https://github.blog/open-source/git/git-clone-a-data-driven-study-on-cloning-behaviors)

Relates to [sparse checkouts](https://github.blog/2020-01-17-bring-your-monorepo-down-to-size-with-sparse-checkout/)

### Full Clone

This should be obvious.

```
git clone
```

### Blobless Partial Clones

```
git clone --filter=blob:none
```


### Treeless Partial Clones

```
git clone --filter=tree:0
```

### Shallow Clones

Fast to clone but more expensive to update.

```
git clone depth=1
```
