# dobby_core_node

Dobby Erlang node that depends on `dobby_core_lib` intended for running
Dobby as standalone service.

## Requirements
- Erlang R17+

## Building
At the beginning get rebar:
```shell
make rebar
```

If you want to connect to the dobby Erlang shell using ssh with
keys, you must
generate keys for `deps/erl_sshd`.  Using make:
```shell
make
```
Using rebar and relx directly:
```shell
./rebar get-deps
./rebar compile
deps/erl_sshd/make_keys
./relx -c _rel/relx.config
```
You may add your own public keys to the `authorized_keys` file in
`priv/erl_sshd` (remember to `./relx -c _rel/relx.config` or `make rel`
afterwards).

If you want to connect to the dobby Erlang shell using ssh with
a username and password,
add or modify the usernames and passwords
to the `erl_sshd` section of `rel/files/sys.config`.

## Running
```shell
_rel/dobby_core_node/bin/dobby_core_node
```

## Connecting via ssh
If you genereated keys in erl_sshd before generating the dobby release,
you can connect to the dobby server's Erlang shell using ssh.
```shell
ssh 127.0.0.1 -p 11133 -i id_rsa
```

or

```shell
ssh lincx@127.0.0.1 -p 11133
```

> The username and password is set via `config/sys.conifg`. Generate
> a new release after changing this file.

To exit the Erlang shell obtained via ssh call `exit().`

## Configuration

The `sys.config` and the `vm.args` files are stored in the `config/` directory.


