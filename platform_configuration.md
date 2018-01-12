#Runtime Platform Configuration

- previous generations: 12000+ line xml file and 8000+ line sdrs
 
>describe i2c devices, gpios, dimm configuration, drive slots, sensor rearm states, 
>thresholds, thermal, clamps, custom fields anything that could change from one platform to another

- one file per platform
- becomes difficult with tangent platforms

#goals

- platform ports in less than a day, our current shipping platforms take about 2
- no hard-codes per platform, minimum code changes for a new platform
- centralized place for configuration
- monolithic image possible
- no sdrs (generated sdrs for compatibility)
- stretch: multi-vendor support "just works" - add another vendors card, detected and enumerated

#how to

- device tree overlays, created from final result configuration
- multiple (or 1) json files with probe strings that allow detection (such as fru fields)
- dbus attached devices that describe system state (plug-able)
- each demon needs to be configured at start: read configuration from dbus or JSON direct
- POC: [https://gerrit.openbmc-project.xyz/#/c/8197/](https://gerrit.openbmc-project.xyz/#/c/8197/), to be hardened and added to repo shortly.