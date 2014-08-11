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


=========================
windows config
=========================

#define BOOST_COMPILER_CONFIG  "boost/config/compiler/visualc.hpp"
#define BOOST_PLATFORM_CONFIG  "boost/config/platform/win32.hpp"

// strongly recommended to define BOOST_FILESYSTEM_NO_DEPRECATED. 
// place before including system headers. http://www.boost.org/doc/libs/1_56_0/libs/filesystem/doc/index.htm
// however, can't define this when building boost.
#if !defined(CDP_BUILDING_BOOST) 
# define BOOST_FILESYSTEM_NO_DEPRECATED
#endif //!defined(CDP_BUILDING_BOOST)

// print lib name when linking
#define BOOST_LIB_DIAGNOSTIC


/*
#if !defined(BUILDING_BOOST)
# if !defined(BOOST_ALL_DYN_LINK)
#   define BOOST_ALL_DYN_LINK
# endif //!defined(BOOST_ALL_DYN_LINK)
//# define BOOST_FILESYSTEM_NO_DEPRECATED
#endif //!defined(BUILDING_BOOST)
*/

// todo - not needed in 1.56 ?
// vs12 does not support this. see http://msdn.microsoft.com/en-us/library/vstudio/dn457344.aspx
// #define BOOST_NO_CXX11_DEFAULTED_FUNCTIONS


// thread lib

//BOOST_THREAD_VERSION default is 2
#define BOOST_THREAD_VERSION 4 
// BOOST_THREAD_PROVIDES_THREAD_EQ ??
// BOOST_THREAD_PROVIDES_CONDITION ??
