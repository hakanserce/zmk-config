# Building shield
## Pre-requisites
- Setup Local ZMK development environment
 - Native (on WSL, I use this): https://zmk.dev/docs/development/local-toolchain/setup/native
 - Container (this might be easier): https://zmk.dev/docs/development/local-toolchain/setup/container
- Install Zephyr SDK
    - this is called out in the above pages as well, but easy to miss
    - just make sure to follow https://docs.zephyrproject.org/3.5.0/develop/getting_started/index.html#install-zephyr-sdk

After we are done with this step, we should have a `zmk` folder, this zmk module (`zmk-config`) folder, west setup.

## Building a shiled (serce42 as an example)

```bash
cd zmk # folder containing the zmk repository
cd app
west build -b nice_nano_v2 -- -DSHIELD=serce42 DZMK_EXTRA_MODULES="../../zmk-config/" -DZMK_CONFIG="../../zmk-config/config"
```

Also check https://zmk.dev/docs/features/modules for more information about building external modules (such as this project).

More details on building: https://zmk.dev/docs/development/local-toolchain/build-flash