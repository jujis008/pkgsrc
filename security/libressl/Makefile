# $NetBSD: Makefile,v 1.5 2016/06/28 13:10:51 wiz Exp $

DISTNAME=	libressl-2.2.6
PKGREVISION=	1
CATEGORIES=	security
MASTER_SITES=	${MASTER_SITE_OPENBSD:=LibreSSL/}

MAINTAINER=	pkgsrc-users@NetBSD.org
HOMEPAGE=	http://www.libressl.org/
COMMENT=	Secure Sockets Layer and cryptography libraries and tools
LICENSE=	openssl

GNU_CONFIGURE=	yes
USE_LIBTOOL=	yes
USE_TOOLS+=	pkg-config

PKGCONFIG_OVERRIDE+=	libcrypto.pc.in
PKGCONFIG_OVERRIDE+=	libssl.pc.in
PKGCONFIG_OVERRIDE+=	libtls.pc.in
PKGCONFIG_OVERRIDE+=	openssl.pc.in

LIBRESSL_PREFIX=	${PREFIX}/${PKGBASE}

PKG_SYSCONFSUBDIR=	${PKGBASE}
GNU_CONFIGURE_PREFIX=	${LIBRESSL_PREFIX}
CONFIGURE_ARGS+=	--with-openssldir=${PKG_SYSCONFDIR}
CONFIGURE_ARGS+=	--with-enginesdir=${LIBRESSL_PREFIX}/lib/engines

EGDIR= 			${PREFIX}/share/examples/${PKGBASE}
CONFS= 			cert.pem openssl.cnf x509v3.cnf
.for f in ${CONFS}
CONF_FILES+= 		${EGDIR}/${f} ${PKG_SYSCONFDIR}/${f}
.endfor

# Handle subprefix
LDFLAGS+=		${COMPILER_RPATH_FLAG}${LIBRESSL_PREFIX:Q}/lib
BUILDLINK_PASSTHRU_RPATHDIRS+=	${LIBRESSL_PREFIX:Q}/lib

TEST_TARGET=	check
PLIST_VARS+=	man

.include "../../mk/bsd.prefs.mk"

.if ${OPSYS} != "Darwin"
PLIST.man=	yes
.endif

post-install:
	${INSTALL_DATA_DIR} ${DESTDIR}${EGDIR}
	cd ${WRKSRC}/apps; ${INSTALL_DATA} ${CONFS} ${DESTDIR}${EGDIR}

.include "../../mk/bsd.pkg.mk"
