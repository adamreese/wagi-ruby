# Wagi-Ruby

Demo of executing a ruby script in Wagi

## Running the demo

Ruby files are placed in './lib' directory.

Run `make serve` to start wagi.

Pass the script name as the first argument

```
$ curl 'http://localhost:3000?env.rb'
```

The 'ruby-wasm32-wasi/usr' is mounted to '/usr' to allow use of default gems.
(base64, pp, etc...)

### Running the demo on spin

Run `make serve-spin`

Spin mounts files to the path in the repo. Add 'lib' to the script name.

NOTE: Requiring standard library doesn't work with spin yet.

```
$ curl 'http://localhost:3000?lib/env.rb'
```

## Building Ruby for wasi at home

Follow the [Ruby wasm build docs](https://github.com/ruby/ruby/tree/master/wasm)

NOTE: If you're building on arm you must use an arm build of binaryen.  I used
the latest version.

Copy the Ruby build to the project directory

```
$ cp [ruby source dir]/ruby-wasm32-wasi .
```

Rename the ruby binary.

```
cp ./ruby-wasm32-wasi/usr/local/bin/ruby ./ruby.wasm
```

Bindle will only set the media type to 'application/wasm' if the file extension
is '.wasm'.
