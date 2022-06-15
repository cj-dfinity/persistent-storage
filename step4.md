# 4. Testing
There are two ways of testing the functionality of this example dapp. One way is by making command line requests using DFX, and the other way is to use the Candid UI. Before the example dapp can be tested, it must be deployed (locally) as described in the above Deployment section.

## 4.1. dfx
`dfx` has a subset of commands for canister operations, and one of them enables calling the public functions added to the `main.mo` file in the previous step. In the following examples the initial value is 0. `increment` will increment value and return 1, `get` will return the current value and `reset` will set the value to 0.

Command usage: `dfx canister call <project>  <function>`

```bash
$ dfx canister call persistent_storage increment
(1 : Nat)
```

```bash
$ dfx canister call persistent_storage get
(1 : Nat)
```

```bash
$ dfx canister call persistent_storage reset
(0 : Nat)
```

The persistence of the stored value can be tested by calling the `increment` function again and making sure the value is larger than zero. Then make a change in the Motoko code, any minor change like changing the function name `get` to `getCount`, and then re-deploy the project and call the `getCount` function to verify that the counter value did not change back to the initial value (0).

```bash
$ dfx canister call persistent_storage increment
(1 : Nat)
// Make code change
$ dfx deploy
$ dfx canister call persistent_storage getCount
(1 : Nat)
```


## 4.2. Candid UI
The Candid UI provides an easy, user friendly interface for testing the backend. The UI is automatically generated, and the canister ID can be found by using the `dfx canister id <canister_name>` command:

```bash
$ dfx canister id __Candid_UI
r7inp-6aaaa-aaaaa-aaabq-cai
$ dfx canister id persistent_storage
rrkah-fqaaa-aaaaa-aaaaq-cai
```

**http://<candid_canister_id>.localhost:8000/?id=<backend_canister_id>**

![Candid UI](images/candid_ui.png)

