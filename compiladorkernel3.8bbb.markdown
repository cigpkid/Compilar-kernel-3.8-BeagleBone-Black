***Compilar kernel 3.8 para BeagleBone Black.***

**Requerimientos**

    Laptop/PC Linux 14.04
    ARM cross compiler
    Linux kernel para BeagleBone Black
    U-Boot

**Instalar ARM cross compiler.**

    En terminal, ejecutar el siguiente comando para instalar el compilador

> apt-get install gcc-arm-linux-gnueabihf

    validar que la instalación es correcta, consultando la versión

> arm-linux-gnueabihf-gcc --version

![1_compilador.png](C:/Users/kaetzer/crosscompile/Compilar-kernel-3.8-BeagleBone-Black/img/1_compilador.png "")

**Clonar kernel.**

    Crear una carpeta en la que clonaremos el kernel

> git clone https://github.com/beagleboard/linux.git

    terminando de clonar cambiamos la version a la 3.8 con la siguiente instrucción

> git checkout 3.8

![2_kernel.png](C:/Users/kaetzer/crosscompile/Compilar-kernel-3.8-BeagleBone-Black/img/2_kernel.png "")

![2_kernel_3.8.png](C:/Users/kaetzer/crosscompile/Compilar-kernel-3.8-BeagleBone-Black/img/2_kernel_3.8.png "")

**Clonar U-Boot.**

    Crear una carpeta en la que clonaremos U-Boot

> git clone git://git.denx.de/u-boot.git

![3_uboot.png](C:/Users/kaetzer/crosscompile/Compilar-kernel-3.8-BeagleBone-Black/img/3_uboot.png "")

**Pasos para compilar kernel.**

    Dentro de la carpeta de U-Boot compilamos con la siguiente instrucción, que le indica que cargara la configuracion default de BeagleBone Black

> make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- am335x_boneblack_defconfig

![4_uboot_compilar.png](C:/Users/kaetzer/crosscompile/Compilar-kernel-3.8-BeagleBone-Black/img/4_uboot_compilar.png "")

    ahora preparamos a U-Boot para una compilación cruzada

> make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf-

![5_uboot_cross_compile.png](C:/Users/kaetzer/crosscompile/Compilar-kernel-3.8-BeagleBone-Black/img/5_uboot_cross_compile.png "")

![6_uboot_cross_compile.png](C:/Users/kaetzer/crosscompile/Compilar-kernel-3.8-BeagleBone-Black/img/6_uboot_cross_compile.png "")

    Dentro de la carpeta kernel, definimos una configuracion default BeableBone Black

> sudo make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- bb.org_defconfig

![8_2_kernel_config.png](C:/Users/kaetzer/crosscompile/Compilar-kernel-3.8-BeagleBone-Black/img/8_2_kernel_config.png "")

    La siguiente linea indica la direccion de carga, al momento de compilar

> sudo make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- uImage dtbs LOADADDR=0x80008000

![9_kernel_compilar_ini.png](C:/Users/kaetzer/crosscompile/Compilar-kernel-3.8-BeagleBone-Black/img/9_kernel_compilar_ini.png "")

![9_kernel_compilar_ini.png](C:/Users/kaetzer/crosscompile/Compilar-kernel-3.8-BeagleBone-Black/img/9_kernel_compilar_fin.png "")



