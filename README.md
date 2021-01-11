# Quickfix

## BUILDING AND INSTALLING

    Full instructions:
        See doc/html/building.html

    Quick instructions:
        ./bootstrap
        ./configure
        make
        make check
        sudo make install

For SunOS and AIX have a look at README.SunOS and README.AIX.

--------------------------------------------------------------------

It is possible to build many components with a relatively newer version of cmake.


For example on Windows,

mkdir build
cd build
cmake  -DHAVE_SSL=ON -G "Visual Studio 15 2017 Win64" -DCMAKE_INSTALL_PREFIX:PATH="install-path" -DOPENSSL_ROOT_DIR="path to openssl" ..
Then build in Visual Studio or on command prompt.

On Linux (with system openssl),

cmake -DCMAKE_BUILD_TYPE=RelWithDebInfo -DHAVE_SSL=ON -DCMAKE_INSTALL_PREFIX:PATH="install-path" ..
make -j 4 install

If one has Ninja then (with system openssl),

cmake -G Ninja -DCMAKE_BUILD_TYPE=RelWithDebInfo -DHAVE_SSL=ON -DCMAKE_INSTALL_PREFIX:PATH="install-path" ..
ninja install

## Building python package

0) Clone https://github.com/quickfix/quickfix-package. You will also need twine or other packets depending of your OS if you wish to upload your package to local pip repository.

1) cd quickfix-package

2) Clone this repo inside quickfix-package folder and build it (see system specific instruction above. Not that compilation can take time on most systems)
    cd quickfix
    ./bootstrap
    ./configure --with-python3
    make

3) Run OS depending package (./package-python.sh for example). Note that setup.py is called via `python` executable which can be obsolete in modern systems (simply change it to python3 if needed)

4) Install packet into system
    python3 -m pip install --no-index file://<path_to_quickfix-package>/quickfix-python/dist/quickfix-1.15.1.tar.gz


OR just simply download it from assets: (https://github.com/xntltd/quickfix/releases/download/v1.15.1/quickfix-1.15.1.tar.gz)
