# opentofu-large-module-source

Large module package repo for https://github.com/opentofu/opentofu/issues/1086.

The point of this repo is to provide a simple, sample test case. This repo has
8.3 MB of copies of the OpenTofu logo to provide a meaningful amount of size to
the module package.

If you go to `targets/remote-source` and run `time tofu init`, this will reflect
the current behavior I am describing in this issue where OpenTofu makes a
separate copy of the module package for each of the 100 module calls. On my
machine, this takes `10.094 total`.

If you go to `targets/local-source` and run `time tofu init`, this will reflect
the performance we would see if OpenTofu only downloaded the module package
once, before linking to that single copy of the module package (in this case
mocked out by using local module source path) in the other 99 module calls. On
my machine, this takes `2.557 total`.
