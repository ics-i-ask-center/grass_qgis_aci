
BootStrap: docker
From: centos:centos7
%setup

%files

%environment 

%runscript


%post
    # commands to be executed inside container during bootstrap
    # add python and install some packages
    yum update -y
    yum install -y epel-release
    yum install -y terminator
    yum install -y centos-release-scl
    yum install -y vte-devel
    yum install -y vte291-devel
    yum install -y vte-profile
#    yum -y install devtoolset-7
    yum install -y devtoolset-7-gcc*
    scl enable devtoolset-7 bash
    yum -y groups install "Development Tools"
#    yum -y groups install "GNOME Desktop"
    yum -y groups install "Base"
#    yum -y groups install "X Window System" "Desktop" "Fonts"
    yum -y install git cmake gcc-c++ gcc binutils \
	libX11-devel libXpm-devel libXft-devel libXext-devel
    yum -y install gcc-gfortran openssl-devel pcre-devel \
	mesa-libGL-devel mesa-libGLU-devel glew-devel ftgl-devel mysql-devel \
	fftw-devel cfitsio-devel graphviz-devel \
	avahi-compat-libdns_sd-devel libldap-dev python-devel \
	libxml2-devel gsl-devel
    yum -y install openmpi-devel
    yum -y install cmake3
    yum -y install hdf5-devel
#    yum -y install boost-devel
    yum -y install patch
    yum -y install git g++ zlib-devel libqt4-devel libgl1-mesa-dev libtiff-devel
    sudo rpm -Uvh http://elgis.argeo.org/repos/5/elgis-release-5-5_0.noarch.rpm
    yum -y install qgis-devel
    yum -y install gdal gdal-python gdal-devel
#    wget -O /etc/yum.repos.d/grass74.repo https://copr.fedoraproject.org/coprs/neteler/grass74/repo/epel-7/neteler-grass74-epel-7.repo
#    yum -y update
#    yum -y install grass grass-libs grass-gui liblas
#    yum -y install grass-devel liblas liblas-devel
#    yum -y update

    # GRASS 7.4.4
    wget -O /etc/yum.repos.d/grass74-epel-6.repo https://copr.fedoraproject.org/coprs/neteler/grass74_epel6/repo/epel-6/neteler-grass74_epel6-epel-6.repo
    yum -y install epel-release

    # get PostgreSQL
    yum -y install http://yum.postgresql.org/9.6/redhat/rhel-6.8-x86_64/pgdg-centos96-9.6-3.noarch.rpm
    yum -y groupinstall "PostgreSQL Database Server 9.6 PGDG"
    yum -y install postgis2_96
    service postgresql-9.6 initdb
    chkconfig postgresql-9.6 on service postgresql-9.6 start

    yum update
    yum -y install grass grass-libs grass-gui liblas
    yum -y install grass-devel liblas liblas-devel
    yum -y update
    
   
    mkdir -p /storage/home
    mkdir -p /storage/work
    mkdir -p /gpfs/scratch
    mkdir -p /gpfs/group
