# $NetBSD: Makefile,v 1.15 2016/04/11 19:01:41 ryoon Exp $

DISTNAME=	qtxmlpatterns-opensource-src-${QTVERSION}
PKGNAME=	qt5-qtxmlpatterns-${QTVERSION}
PKGREVISION=	3
COMMENT=	Qt5 module for XML Patterns

#NO_CONFIGURE=		yes
BUILD_TARGET=		sub-tools

INSTALL_ENV+=		INSTALL_ROOT=${DESTDIR}
INSTALLATION_DIRS+=	lib/pkgconfig

.include "../../x11/qt5-qtbase/Makefile.common"

post-install:
.for i in Qt5XmlPatterns.pc
	cd ${DESTDIR}${PREFIX}/lib/pkgconfig && \
	ln -f -s ${QTPREFIX}/lib/pkgconfig/${i} ${i}
.endfor

.include "../../x11/qt5-qtbase/buildlink3.mk"
.include "../../mk/bsd.pkg.mk"
