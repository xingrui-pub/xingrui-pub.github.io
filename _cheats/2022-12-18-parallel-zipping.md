---
layout: none
title: Parallel Zipping with pigz
---

[Pigz](https://superuser.com/questions/591154/time-to-zip-very-large-100g-files) Supports only `tar.gz` files: 

```bash
sudo apt install pigz
tar -c --use-compress-program=pigz -f <filename>.tar.gz <dir-to-zip>
```