# openwrt-niceshaper

## Description

This is the OpenWrt feed containing build script for [NiceShaper - Dynamic Traffic Shaper](http://niceshaper.jedwabny.net/page/en/index).

## Usage

This repository is intended to be used with [OpenWrt SDK](http://wiki.openwrt.org/doc/howto/obtain.firmware.sdk) or [OpenWrt Buildroot](http://wiki.openwrt.org/doc/howto/buildroot.exigence).

The feed needs to be enabled first. Add this line to `feeds.conf.default` file in the root of your extracted SDK or buildroot:
```
src-git niceshaper https://github.com/arturdm/openwrt-niceshaper
```

To install all its package definitions, run:
```
./scripts/feeds update niceshaper
./scripts/feeds install -a -p niceshaper
```

Make sure niceshaper package is enabled in your build configuration using:
```
make menuconfig
```
and browsing to `Network > niceshaper`.

To build the `.ipk` file run:
```
make package/niceshaper/compile V=s
```

You can find the resulting `.ipk` file in `bin/{target}/packages/niceshaper/`

## License

See [LICENSE](LICENSE) file.
