.. raw:: html

  <embed>
    

    <table class="tg">
      <tr>
        <th class="tg-0pky">Library</th>
        <th class="tg-0pky">Ext. Link</th>
        <th class="tg-0pky">Documentation</th>
        <th class="tg-0pky">License</th>
        <th class="tg-0pky" style='width: 100%;' rowspan="5"><img src="doc/img/SICK_Logo_Claim_RGB.png" align="right"  height="120"/></th>
      </tr>
      <tr>
        <td class="tg-0pky">
          <img src="https://ci.appveyor.com/api/projects/status/2jbep0ss21bh7jxe/branch/master?svg=true"/>
        </td>
        <td class="tg-0pky">
          <img src="https://ci.appveyor.com/api/projects/status/7uy0pko38t6oot6i/branch/master?svg=true"/>
        </td>
        <td class="tg-0pky">
          <img src="https://readthedocs.org/projects/sick-scan-documentation/badge/?version=latest"/>
        </td>

        <td class="tg-0pky">
          <img src="https://img.shields.io/badge/License-Apache%202.0-blue.svg"/>
        </td>
      </tr>
    </table>
    
    
    <p style="margin-bottom:1cm;"/p>
  </embed>


Linking a User Application with SSBL
====================================

  .. code-block:: console

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