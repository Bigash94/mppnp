# Software to install for USEEPP on mppnp

1. make and go to some scratch dir 

$mkdir tmp 
$cd tmp 

2. get hdf5: 

$ wget http://www.hdfgroup.org/ftp/HDF5/prev-releases/hdf5-1.8.3/src/hdf5-1.8.3.tar.gz 
$ tar -xzvf hdf5-1.8.3.tar.gz 

3. make sure you have a target directory. I recommend using 
/opt. create it if you don't have it. you may use 

$sudo mkdir /opt 

on al Linux box may have to do as superuser, or alternatively use 
$HOME/opt to install everything into your home directory, works 
equally well 

then make a directory for your hdf where the libraries go: 
$mkdir /opt/hdf5-1.8.3 

3. compile 
$ cd hdf5-1.8.3 
$ ./configure --prefix=/opt/hdf5-1.8.3 
$ make 
$ make check 
$ sudo make install 

4. then you go to se/trunk, and you make a target dir for se:  
$sudo mkdir /opt/se-1.2_gfortran 

5. finally compile and install se: 
The config statement for se must be told which fortran compiler to 
use. If you have only one on your system config may find out, but you 
may want to specify: 

for ifort: 
$ ./configure --prefix=/opt/se-1.2 F77=ifort --with-hdf5=/opt/hdf5-1.8.3 
or with gfortran: 
$ ./configure --prefix=/opt/se-1.2_gfortran F77=gfortran --with-hdf5=/opt/hdf5-1.8.3 

then the usual: 
$make 
$make check 
$ sudo make install 
