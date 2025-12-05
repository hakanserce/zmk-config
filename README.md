8# Building shield
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

## Miryoku Layout

Note that some keyboards (serce42, banice36) are built for use with the Miryoku layout in mind. If you are not planning to use Miryoku, you need to change the default layout and layers to make it more usable.

Use https://github.com/hakanserce/miryoku_zmk GitHub actions to build the firmware with Miryoku layout.
- Go to Actions
- Select Build Inputs
- Click on Run workflow
- Provide the following input:
  - "board" "nice_nano_v2"
  - "shield" "serce42"/ or "banice36"
  - "alphas" "QWERTY"
  - "nav" "vi"
  - "layers" "default"
  - "mapping" "default"
  - "custom_config" "default"
  - "kconfig" "default"
  - "branches" "default"
  - "modules" "hakanserce/zmk-config/master"
- When the build completes, the firmware will be available under artifacts
