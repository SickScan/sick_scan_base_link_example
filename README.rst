# Linking a User Application with SSBL

git clone https://github.com/SickScan/sick_scan_base_link_example.git ssbl-link
cd ssbl-link

git clone -q https://github.com/SickScan/sick_scan_base.git ssbl
cd ssbl
mkdir build
cd build
cmake -G"Visual Studio 16 2019" -A"x64"  -DCMAKE_INSTALL_PREFIX=./install ..
cmake --build . --target install --config Debug

cd ../..

mkdir build
cd build 


cmake  -G"Visual Studio 16 2019" -A"x64" -DSSBL_INSTALL_DIR=./ssbl/build/install -Bbuild .
cmake --build build --config Debug