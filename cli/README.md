# microkv-cli

Command line application implementation for __microkv__

To display help options:

```
$ microkv-cli --help
microkv 0.2.3
ex0dus <ex0dus at codemuch.tech>

USAGE:
    microkv-cli [FLAGS] [OPTIONS] <DATABASE> [SUBCOMMAND]

FLAGS:
    -d, --debug      Print out debug output
    -h, --help       Prints help information
    -u, --unsafe     Interact with the database without encryption.
    -V, --version    Prints version information

ARGS:
    <DATABASE>    Name of database to interact with. Will be created if doesn't exist.

SUBCOMMANDS:
    get     Retrieves and decrypts value in storage by key.
    help    Prints this message or the help of the given subcommand(s)
    list    List out keys existing in the database
    put     Adds a new key and value, encrypts and adds to storage.
    rm      Deletes a key-value pair by key
```

`microkv-cli` can still interact with a local persistent key-value store like so:

```
$ microkv-cli mydb put -k mykey -v myvalue
Password:
Inserting key-value entry into database `mydb`

$ microkv-cli mydb get -k mykey
Password:
myvalue

$ microkv-cli mydb get -k mykey
Password: <WRONG PWD>
CryptoError received from microkv with message: cannot validate value being decrypted

$ microkv-cli mydb rm -k mykey
Removed entry by key `mykey`
```
