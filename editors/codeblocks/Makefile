# $NetBSD: Makefile,v 1.2 2016/06/19 23:01:01 joerg Exp $
#

DISTNAME=	codeblocks_16.01
PKGNAME=	${DISTNAME:S/_/-/}
CATEGORIES=	editors x11
MASTER_SITES=	${MASTER_SITE_SOURCEFORGE:=codeblocks/}

MAINTAINER=	pkgsrc-users@NetBSD.org
HOMEPAGE=	http://www.codeblocks.org/
COMMENT=	Open source, cross platform, free C++ IDE
LICENSE=	gnu-gpl-v3

WRKSRC=		${WRKDIR}/${PKGNAME_NOREV}.release
GNU_CONFIGURE=	yes
USE_LIBTOOL=	yes
USE_TOOLS+=	pkg-config gmake
USE_LANGUAGES=	c c++

CONFIGURE_ARGS+=	--with-contrib-plugins=AutoVersioning,BrowseTracker,byogames,cbkoders,codesnippets,codestat,dragscroll,envvars,help,keybinder,libfinder,profiler,regex,exporter,symtab
# wxsmith makes error in build process

BUILD_DEPENDS+=	zip-[0-9]*:../../archivers/zip

PKGCONFIG_OVERRIDE+=	codeblocks.pc.in

.include "../../mk/compiler.mk"
.if !empty(PKGSRC_COMPILER:Mclang)
CXXFLAGS+=	-std=c++11
.endif

.include "../../databases/shared-mime-info/mimedb.mk"
.include "../../graphics/hicolor-icon-theme/buildlink3.mk"
.include "../../sysutils/desktop-file-utils/desktopdb.mk"
.include "../../x11/wxGTK30/buildlink3.mk"
.include "../../mk/bsd.pkg.mk"
