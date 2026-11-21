<img src="assets/logo.png" width="112" height="112" alt="Blyx penguin measuring the widest gap on a sample ruler with a compass.">

# GridGap

Locate the coarsest gap and count nonincreasing steps in a sample grid. This Blyx library is part of the numerics and visualization collection.

An arithmetic average ignores the spacing between measurements. Integrate on the supplied time grid and flag large gaps. [NumPy, composite trapezoidal integration](https://numpy.org/doc/stable/reference/generated/numpy.trapezoid.html)

## Install and run

Install [Blyx 0.2.1](https://www.blyx-lang.space/download) with a Rust toolchain and host linker for native builds.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-gridgap.git
cd blyx-gridgap
blyxc native-run example.blyx
blyxc native-run tests.blyx
```

[Run the editable browser example](https://www.blyx-lang.space/play?example=package-gridgap) · [Package page](https://www.blyx-lang.space/packages/gridgap) · [Handbook](https://doc.blyx-lang.space/guide/magpie)

## Import the module

Run this in the directory containing your application's entry file.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-gridgap.git vendor/gridgap
```

```blyx
use vendor::gridgap::gridgap;

fn main() {
    let x = [0, 1, 4, 3];
    let result = gridgap_inspect(x);
    if len(result) == 0 { println!("invalid"); return; }
    let mut i = 0;
    while i < len(result) {
        println!(at(result, i));
        i += 1;
    }
}
```

Expected output

```text
3
2
1
```

## API

`gridgap_inspect(x)`

Returns [largest absolute step, right index of the first largest step, nonincreasing steps]. At least two points are required. Invalid arguments and nonfinite results return an empty vector. Integers carried in numeric vectors use the exact range from −(2^53−1) to 2^53−1.

| Argument | Domain |
| --- | --- |
| x | Vector of values, each a finite number |

## In use

[Magpie](https://github.com/Rahulchaube1/blyx-magpie) uses this module to integrate an increasing sample grid and flag under-sampled sections.

## Verification and contributions

The regression suite in [tests.blyx](tests.blyx) checks the example, boundary cases and invalid inputs. Include a short reproducer and your compiler version in [an issue](https://github.com/Rahulchaube1/blyx-gridgap/issues). The source is dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE). Read the [artwork notice](assets/NOTICE.txt) for credits.

## Connect with Rahul Chaube

[Portfolio](https://www.rahulchaube1.com/) · [GitHub](https://github.com/Rahulchaube1) · [LinkedIn](https://www.linkedin.com/in/rahulchaube1) · [Hugging Face](https://huggingface.co/oncody) · [X](https://x.com/RahulChaube_) · [EverestQ](https://www.everestqai.com/) · [Contact](https://www.rahulchaube1.com/contact)

[Blyx website](https://www.blyx-lang.space/) · [BlyxTorch](https://www.blyx-lang.space/packages/blyxtorch) · [Handbook](https://doc.blyx-lang.space/) · [Community](https://www.blyx-lang.space/community)

Support Rahul’s open-source work through [GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) or [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube).
