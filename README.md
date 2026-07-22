# zmk-keymap-shared

Shared keymap logic for 3*6 split keyboards (Corne, Cornix).

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
