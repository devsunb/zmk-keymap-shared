# zmk-keymap-shared

Shared keymap logic for Corne, Cornix split keyboards.

## Usage

`west.yml`:

```yaml
manifest:
  remotes:
    - name: devsunb
      url-base: https://github.com/devsunb
  projects:
    - name: zmk-keymap-shared
      remote: devsunb
      revision: main
```

`<keyboard>.keymap`:

```c
#include <zmk-helpers/helper.h>
#include "<keyboard>.h"   // key positions: RT0.., LM5.., RH1, LH1, LH2 ...
#include <zmk-keymap-shared/keymap.dtsi>

ZMK_LAYER(Base, BASE_L1 ... BASE_R1 ...)
```

## keymap-drawer

`keymap-drawer.yaml` maps the behaviors defined here to legends, so it is
versioned with `keymap.dtsi`. Consumers reference it instead of keeping a copy:

```sh
keymap -c zmk-keymap-shared/keymap-drawer.yaml parse -z config/<keyboard>.keymap |
    keymap -c zmk-keymap-shared/keymap-drawer.yaml draw -j config/<keyboard>.json - -o keymap.svg
```

Run it from the west workspace root. `zmk_additional_includes` in the config
resolves against the current directory, not against the config file.
