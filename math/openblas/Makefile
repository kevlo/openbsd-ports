ONLY_FOR_ARCHS =	${CLANG_ARCHS}

COMMENT =		optimized BLAS library based on GotoBLAS2

V =			0.3.20
PKGNAME =		openblas-${V}

GH_ACCOUNT =		xianyi
GH_PROJECT =		OpenBLAS
GH_TAGNAME =		v${V}

SHARED_LIBS +=		openblas	0.0	# 0.0

CATEGORIES =		math

HOMEPAGE =		https://www.openblas.net/

MAINTAINER =		Kevin Lo <kevlo@openbsd.org>

# BSD 3-clause
PERMIT_PACKAGE =	Yes

WANTLIB =		c m

.if ${MACHINE_ARCH} != "arm"
WANTLIB +=		pthread
.endif

MODULES=		fortran
MODFORTRAN_COMPILER =	gfortran

MAKE_ENV =		CFLAGS="${CFLAGS}" FFLAGS="${CFLAGS}" \
			CC=clang FC="${MODFORTRAN_COMPILER}" \
			LIBopenblas_VERSION="${LIBopenblas_VERSION}" \
			USE_THREAD=1 USE_OPENMP=0 NUM_THREADS=64
.if ${MACHINE_ARCH} == "amd64" || ${MACHINE_ARCH} == "i386"
MAKE_ENV +=		DYNAMIC_ARCH=1 DYNAMIC_OLDER=1 TARGET=GENERIC
.endif
.if ${MACHINE_ARCH} == "aarch64" || ${MACHINE_ARCH} == "arm"
MAKE_ENV +=		DYNAMIC_ARCH=1 DYNAMIC_OLDER=1
.endif

FAKE_FLAGS = 		DESTDIR=

USE_GMAKE =		Yes

.include <bsd.port.mk>
