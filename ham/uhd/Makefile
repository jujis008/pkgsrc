# $NetBSD: Makefile,v 1.19 2016/06/08 07:26:59 wiz Exp $

DISTNAME=		uhd-3.9.4
PKGREVISION=		1
CATEGORIES=		ham
MASTER_SITES=           ${MASTER_SITE_GITHUB:=EttusResearch/}
#                                                                     3.9.1 -> 003_009_001
GITHUB_TAG=		release_${PKGVERSION_NOREV:C/([0-9])\.([0-9])\.([0-9])/00\1_00\2_00\3/}

MAINTAINER=		pkgsrc-users@NetBSD.org
HOMEPAGE=		http://code.ettus.com/redmine/ettus/projects/uhd/wiki
COMMENT=		USRP (Universal Software Radio Peripheral) Hardware Drivers
LICENSE=		gnu-gpl-v2

BUILD_DEPENDS+=		${PYPKGPREFIX}-cheetah-[0-9]*:../../devel/py-cheetah
BUILD_DEPENDS+=		${PYPKGPREFIX}-docutils>=0.12:../../textproc/py-docutils
BUILD_DEPENDS+=		${PYPKGPREFIX}-mako-[0-9]*:../../devel/py-mako

CMAKE_ARGS+=		-DRST2HTML_EXECUTABLE=${PREFIX}/bin/rst2html-${PYVERSSUFFIX}.py
CMAKE_ARGS+=		-Wno-dev

USE_LANGUAGES=		c c++
USE_TOOLS=		cmake pkg-config
USE_CMAKE=		yes
# extra pax_global_header exists, and to avoid that:
EXTRACT_USING=		gtar
#EXTRACT_ELEMENTS=	uhd-${GITHUB_TAG}

# Please note distribution has many stuff under uhd/, but build itself
# needs under host/ only.  Those uhd/ stuff will be handled post-{patch,install}:
WRKSRC=			${WRKDIR}/uhd-${GITHUB_TAG}/host

# The files with their name uhd-xxxx, are moved down from uhd/xxxx for this process.
REPLACE_PYTHON=	\
	utils/latency/graph.py \
	utils/latency/run_tests.py \
	utils/uhd_images_downloader.py.in \
	utils/usrp2_card_burner.py \
	utils/usrp2_card_burner_gui.py \
	utils/usrp_n2xx_net_burner.py \
	utils/usrp_n2xx_net_burner_gui.py

INSTALLATION_DIRS+=	share/uhd
INSTALLATION_DIRS+=	share/uhd/firmware
INSTALLATION_DIRS+=	share/uhd/fpga
INSTALLATION_DIRS+=	share/uhd/images

SUBST_CLASSES+=		man
SUBST_MESSAGE.man=	Convert share/man to man
SUBST_STAGE.man=	pre-configure
SUBST_FILES.man=	docs/CMakeLists.txt
SUBST_SED.man=		-e '/UHD_INSTALL/s,$${PKG_MAN_DIR},${PREFIX}/${PKGMANDIR}/man1,'
# UHD_INSTALL(FILES ${gzfile} DESTINATION ${PKG_MAN_DIR} COMPONENT manpages)

# is it default ? and redundent ?
PLIST_SRC=	${PKGDIR}/PLIST
.include "options.mk"

.include "../../lang/python/application.mk"
.include "../../devel/boost-libs/buildlink3.mk"
.include "../../devel/libusb1/buildlink3.mk"
.include "../../devel/orc/buildlink3.mk"

.include "../../mk/bsd.pkg.mk"
