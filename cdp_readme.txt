========
source
========
todo: make fork in github 
https://github.com/cperras/boost.git
git@github.com:cperras/boost.git

key: H:\cdp\merging\docs\ssh

co --recursive


https://github.com/boostorg/boost
https://github.com/boostorg/boost.git
git@github.com:boostorg/boost.git

changed from svn to git


cd H:\dev\boost
git clone --recursive git@github.com:boostorg/boost.git modular-boost > modular_clone.log

==================
build config
==================

edit: boost_user_config.hpp
copy into boost/config

define=BOOST_USER_CONFIG=<boost/config/boost_user_config.hpp>


edit: boost/config/user.hpp
#include "boost/config/boost_user_config.hpp"

or: copy boost_user_config.hpp contents into 
  H:\dev\boost\boost\libs\config\include\boost\config\user.hpp


zlib
==========
set NO_COMPRESSION=0
set ZLIB_SOURCE=H:\dev\zlib\zlib-1.2.8

todo: try ??
set NO_ZLIB=0 

mpi
==========
todo:
--without-mpi


python
==========



=========
build 
=========

boostrap


b2 link=shared runtime-link=shared threading=multi variant=debug toolset=msvc-12.0 define=CDP_BUILDING_BOOST define=BOOST_USER_CONFIG="boost/config/boost_user_config.hpp" --without-mpi

note: this had problems with python (inconsistent dll linkage). also could not find unique_lock, etc in 1.57
  b2 link=static runtime-link=shared threading=multi variant=debug toolset=msvc-12.0 define=CDP_BUILDING_BOOST --without-mpi



-DBOOST_USER_CONFIG="<boost/config/user/multithread-gcc-config.hpp>"

--libdir ?
--buildid= ??

b2: http://www.boost.org/boost-build2/doc/html/bbv2/overview/builtins/features.html



//edit: boost/config/user.hpp
//#define BOOST_USER_CONFIG "boost/config/boost_user_config.hpp"

toolset=msvc-12.0 
 -Zm112


