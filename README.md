
(Read HowtoBuild.md to build the new hardfork. )

B3CC
=====================================

https://b3cc.com

[View Releases](https://github.com/b3cc/b3cc/releases)

What is B3CC?
---------------

B3CC is an experimental blockchain based on Bitcoin. Almost all instances of SHA256, a prominent algorithm throughout Bitcoin, are replaced with SHA3-256.

Its roadmap is to have extreme parity with Bitcoin and Bitcoin Core, with upstream merges accounting for the bulk of its future changes. The issue tracker may be used for discussion and review of upcoming Bitcoin Core pull requests, as well as code issues.

It has an identical difficulty adjustment and halving functions as Bitcoin in its present form.

Its genesis block has a timestamp (`nTime`) of `1540053565`.

What is Bitcoin?
----------------

Bitcoin is an experimental digital currency that enables instant payments to
anyone, anywhere in the world. Bitcoin uses peer-to-peer technology to operate
with no central authority: managing transactions and issuing money are carried
out collectively by the network. Bitcoin Core is the name of open source
software which enables the use of this currency.

For more information, as well as an immediately useable, binary version of
the Bitcoin Core software, see https://bitcoincore.org/en/download/, or read the
[original whitepaper](https://bitcoincore.org/bitcoin.pdf).

License
-------

B3CC is released under the terms of the MIT license. See [COPYING](COPYING) for more
information or see https://opensource.org/licenses/MIT.

Building
--------

Download either the source code, or a [pre-built release](https://github.com/b3cc/b3cc/releases).

To build from source, run:

```
./autogen.sh
./configure --disable-bench
make
```

The resulting binaries will be created in `src/`, with the GUI wallet in subdirectory `src/qt/`.

**Components -**

- `b3ccd` - Daemon (Syncs and validates blocks and transactions)
- `b3cc-cli` - RPC Client (Runs commands on the daemon) 
- `b3cc-tx` - Transaction Builder
- `b3cc-qt` - GUI Wallet (Standalone, can be used for mining and sending)

Running
-------

**GUI -**

To start, double-click the program. To stop, close the program.

**CLI (Command Line Interface) -**

To start, run `./b3ccd` in a terminal window. Then run `./b3cc-cli getblockchaininfo` in another. You should see the block height and other output. Run `./b3cc-cli help` for more commands.

To stop `b3ccd` cleanly, you should run `./b3cc-cli stop`.

Mining
------

**GUI -**

You will need to visit the debug console to use these commands. It is located at `Help -> Debug Window` on the titlebar.

To start, run command - `setgenerate true <num_cpu_cores>`

To stop, run command - `setgenerate false`

**CLI -**

To start, first run - `./b3ccd`

Then, in a separate terminal, run - `./b3cc-cli setgenerate true <num_cpu_cores>`

You are now mining.

To stop mining, run - `./b3cc-cli setgenerate false`

To stop `b3ccd` cleanly, run - `./b3cc-cli stop`

Wallet Backup
-------------

Create a wallet backup right away. There are two ways to do this:

- Use `b3cc-cli dumpwallet <output_filename>` to create a txt file containing your `xprv` (master private key) and its addresses. From this `xprv`, you can generate all private keys & addresses that your wallet file will ever contain.

- Copy `$DATADIR/wallets/wallet.dat` to a safe destination.

Your datadir is in the following folder for each operating system:

- Windows 10 - `C:\Documents and Settings\<username>\Application Data\B3CC`
- Windows 7 - `C:\Users\<username>\AppData\Roaming\B3CC`
- Mac - `~/Library/Application Support/B3CC`
- Unix - `~/.b3cc`

Development Process
-------------------

> The following text is directly from Bitcoin Core.

The `master` branch is regularly built and tested, but is not guaranteed to be
completely stable. [Tags](https://github.com/bitcoin/bitcoin/tags) are created
regularly to indicate new official, stable release versions of Bitcoin Core.

The contribution workflow is described in [CONTRIBUTING.md](CONTRIBUTING.md).

Testing
-------

> The following text is directly from Bitcoin Core.

Testing and code review is the bottleneck for development; we get more pull
requests than we can review and test on short notice. Please be patient and help out by testing
other people's pull requests, and remember this is a security-critical project where any mistake might cost people
lots of money.

### Automated Testing

Developers are strongly encouraged to write [unit tests](src/test/README.md) for new code, and to
submit new unit tests for old code. Unit tests can be compiled and run
(assuming they weren't disabled in configure) with: `make check`. Further details on running
and extending unit tests can be found in [/src/test/README.md](/src/test/README.md).

There are also [regression and integration tests](/test), written
in Python, that are run automatically on the build server.
These tests can be run (if the [test dependencies](/test) are installed) with: `test/functional/test_runner.py`

The Travis CI system makes sure that every pull request is built for Windows, Linux, and macOS, and that unit/sanity tests are run automatically.

### Manual Quality Assurance (QA) Testing

Changes should be tested by somebody other than the developer who wrote the
code. This is especially important for large or high-risk changes. It is useful
to add a test plan to the pull request description if testing the changes is
not straightforward.

Translations
------------

> The following text is directly from Bitcoin Core.

Changes to translations as well as new translations can be submitted to
[Bitcoin Core's Transifex page](https://www.transifex.com/projects/p/bitcoin/).

Translations are periodically pulled from Transifex and merged into the git repository. See the
[translation process](doc/translation_process.md) for details on how this works.

**Important**: We do not accept translation changes as GitHub pull requests because the next
pull from Transifex would automatically overwrite them again.

Translators should also subscribe to the [mailing list](https://groups.google.com/forum/#!forum/bitcoin-translators).
