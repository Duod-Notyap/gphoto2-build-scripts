gphoto2 Build Scripts

## Quick Start

```bash
docker build -t libgphoto2-build:latest android
./start-all
# Wait for all the containers to finish. 
./format-all
```

## Scripts
The scripts here have been modified so that the docker container may be started with `-e TARGET="x86|x86_64|aarch64|armeabi"`, and the corresponding architecture will be built. Some convenience scripts are provided for ease of use.
- `start-all`: Starts 4 containers, one for each architecture, also with `LDFLAGS="-Wl,-z,max-page-size=16384"` for 16KB page alignment. Expects the image to be named `libgphoto2-build:latest`
- `format-all`: Formats all the libs into one flat directory for easy importing into android studio. Expects the containers to be named `libgphoto2-build-$TARGET`.




---
### Original README

This repository contains build scripts for specialized builds of libgphoto2 and gphoto2. Currently, there are two directories containing two different scripts:
* android: an Android port using the Android NDK cross compiler
* appimage: a standalone AppImage encapsulating dependencies plus camlibs/iolibs

DON'T INVOKE THE SCRIPTS DIRECTLY (or else you might mess up your host system). Instead, the scripts are designed to be run within a corresponding Docker/podman container that encapsulates the build environment. First build the container, then launch the container with a volume mount pointing to a host directory. Sources and build artifacts will appear there. You can find more detailed instructions in the README files in the above directories.

These scripts are licensed under the GPL unless otherwise stated. The projects and corresponding build artifacts are licensed separately.

Use these scripts at your own risk and inspect them thoroughly. While these scripts work for me, I bear no responsibility for any damage that may occur to your own devices.


Legal stuff:

Copyright 2021 fahrion.2600

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.
