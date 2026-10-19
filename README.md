# goreleaser-repro

Repro repo for OS / arch matrix issue with generated Homebrew Casks

## To repro:

```bash
goreleaser release --snapshot --clean
mkdir -p /opt/homebrew/Library/Taps/test/homebrew-test
git init /opt/homebrew/Library/Taps/test/homebrew-test/
cp -r dist/homebrew/ /opt/homebrew/Library/Taps/test/homebrew-test/
brew trust test/test
brew readall --os=all --arch=all test/test
```

You will get output similar to the following:

```
Error: Invalid cask (macOS 27 on intel): /opt/homebrew/Library/Taps/test/homebrew-test/Casks/test.rb
Missing URL
Error: Invalid cask (macOS 26 on intel): /opt/homebrew/Library/Taps/test/homebrew-test/Casks/test.rb
Missing URL
Error: Invalid cask (macOS 15 on intel): /opt/homebrew/Library/Taps/test/homebrew-test/Casks/test.rb
Missing URL
Error: Invalid cask (macOS 14 on intel): /opt/homebrew/Library/Taps/test/homebrew-test/Casks/test.rb
Missing URL
Error: Invalid cask (macOS 13 on intel): /opt/homebrew/Library/Taps/test/homebrew-test/Casks/test.rb
Missing URL
Error: Invalid cask (macOS 12 on intel): /opt/homebrew/Library/Taps/test/homebrew-test/Casks/test.rb
Missing URL
Error: Invalid cask (macOS 11 on intel): /opt/homebrew/Library/Taps/test/homebrew-test/Casks/test.rb
Missing URL
Error: Invalid cask (Linux on ARM64): /opt/homebrew/Library/Taps/test/homebrew-test/Casks/test.rb
Missing Linux stanzas can leave Linux `sha256` as nil. Add `depends_on :macos` if this cask is macOS-only or `depends_on arch:` if it does not support this architecture.
```
