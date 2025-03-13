# MathWorks Microchip Repository
MathWorks yocto build repository for generating SD card images for Microchip Platforms.


#### Current Supported Boards
- Microchip PolarFire SoC Icicle Kit

#### General build instructions
- Clone this repository and switch tags to the corresponding version. The release tags are labeled as **mathworks_microchipsoc_R2x.y.z**, where the "R2x" denotes the year of the MATLAB release and "y" denotes the 'a' or 'b' release. The "z" is used for updates to the image within a particular MATLAB release. For example, the tag "R25.1.0" is interperted as MATLAB R2025a where "R25" represents R2025 and "1.0" is for release 'a'. If there were updates to the image within the R2025a release, the versions would be "R25.1.1", "R25.1.2", etc. The MATLAB R2025b release would then start with the tag "R25.2.0".

`$ git checkout mathworks_microchipsoc_R25.1.0`

- Before continuing, ensure that the prerequisite packages are present on your system. Please see the https://github.com/polarfire-soc/meta-polarfire-soc-yocto-bsp?tab=readme-ov-file#Dependencies for Yocto section for further details.

   Ensure you are using `/bin/bash` before calling this. 

- In the project directory (microchip-bsp), change directories to the board of interest. As an example:

`$ cd mw_icicle_kit`

- Update the repo workspace 
 
`$ repo sync` 
`$ repo rebase` 
   
  
- Setup Bitbake environment

`$ . ./meta-polarfire-soc-yocto-bsp/polarfire-soc_yocto_setup.sh`

- Run Build command

`$ MACHINE=icicle-kit-es bitbake core-image-minimal-dev`

- After the build has succeeded, core-image-minimal-dev-icicle-kit-es.wic image will be available in mw_icicle_kit/build/tmp-glibc/deploy/images/icicle-kit-es
	
- Flash your SD card with the wic file using Win32DiskImager software and boot the evaluation board

#### Use Microchip Linux image
The generated core-image-minimal-dev Linux image will be used to boot the Microchip PolarFire SoC Icicle Kit, allowing you to work on various applications.
