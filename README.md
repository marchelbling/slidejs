# Setup

Requires:
* nodejs
* [broccoli](https://github.com/broccolijs/broccoli)
```bash
npm install --save-dev broccoli
npm install --global broccoli-cli
```

Then simply

```bash
npm install
```

# Build

```bash
rm -fr tmp && broccoli serve
```

# Philosophy

This intends to be a very simple solution to build HTML slides. No transition or fancy stuff. Just some markdown describing the deck.

# Credits

The broccoli build, slide navigation and dark theme design was written by [Szymon Witamborski](https://brainshave.com) [[github](https://github.com/brainshave/brainshave.com)]
