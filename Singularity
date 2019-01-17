BootStrap: yum
OSVersion: 7
MirrorURL: http://mirror.centos.org/centos-%{OSVERSION}/%{OSVERSION}/os/$basearch/
Include: yum wget

%post
yum -y update
yum -y install yum-utils
yum -y groupinstall development
yum -y install https://centos7.iuscommunity.org/ius-release.rpm
yum -y install build-essential curl git man vim autoconf libtool debootstrap squashfs-tools
yum -y install python36u
yum -y install python36u-pip
yum -y install python36u-devel
pip3.6 install --upgrade setuptools pip
yum -y install cmake lapack-devel lapack blas blas-devel
pip3.6  install progressbar2
git clone https://github.com/JohannesBuchner/MultiNest.git
cd MultiNest/build/
cmake .. && make
export LD_LIBRARY_PATH=/MultiNest/lib/:$LD_LIBRARY_PATH
cd /
yum -y install python-matplotlib scipy numpy
git clone https://github.com/JohannesBuchner/PyMultiNest.git
cd PyMultiNest
python setup.py install


%environment
export LD_LIBRARY_PATH=/MultiNest/lib/:$LD_LIBRARY_PATH

%runscript
echo "Arguments received: $*"
exec python "$@"
