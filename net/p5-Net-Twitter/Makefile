# $NetBSD: Makefile,v 1.23 2016/06/08 19:24:14 wiz Exp $
#

DISTNAME=	Net-Twitter-4.01008
PKGNAME=	p5-${DISTNAME}
PKGREVISION=	2
CATEGORIES=	net
MASTER_SITES=	${MASTER_SITE_PERL_CPAN:=Net/}

MAINTAINER=	pkgsrc-users@NetBSD.org
HOMEPAGE=	http://search.cpan.org/dist/Net-Twitter/
COMMENT=	Perl interface to the Twitter API
LICENSE=	${PERL5_LICENSE}

DEPENDS+=	p5-Crypt-SSLeay>=0.5:../../security/p5-Crypt-SSLeay
DEPENDS+=	p5-Data-Visitor-[0-9]*:../../devel/p5-Data-Visitor
DEPENDS+=	p5-DateTime>=0.5100:../../time/p5-DateTime
DEPENDS+=	p5-DateTime-Format-Strptime>=1.0900:../../time/p5-DateTime-Format-Strptime
DEPENDS+=	p5-Devel-StackTrace>=1.21:../../devel/p5-Devel-StackTrace
DEPENDS+=	p5-Digest-HMAC-[0-9]*:../../security/p5-Digest-HMAC
DEPENDS+=	p5-HTML-Parser-[0-9]*:../../www/p5-HTML-Parser
DEPENDS+=	p5-IO-Socket-SSL>=2.005:../../security/p5-IO-Socket-SSL
DEPENDS+=	p5-JSON-[0-9]*:../../converters/p5-JSON
DEPENDS+=	p5-JSON-XS-[0-9]*:../../converters/p5-JSON-XS
DEPENDS+=	p5-LWP-Protocol-https-[0-9]*:../../www/p5-LWP-Protocol-https
DEPENDS+=	p5-Moose>=0.90:../../devel/p5-Moose
DEPENDS+=	p5-MooseX-Role-Parameterized-[0-9]*:../../devel/p5-MooseX-Role-Parameterized
DEPENDS+=	p5-Net-[0-9]*:../../net/p5-Net
DEPENDS+=	p5-Net-HTTP>=6.06:../../www/p5-Net-HTTP
DEPENDS+=	p5-Net-OAuth>=0.25:../../net/p5-Net-OAuth
DEPENDS+=	p5-Try-Tiny-[0-9]*:../../devel/p5-Try-Tiny
DEPENDS+=	p5-URI>=1.40:../../www/p5-URI
DEPENDS+=	p5-libwww-[0-9]*:../../www/p5-libwww
DEPENDS+=	p5-namespace-autoclean>=0.09:../../devel/p5-namespace-autoclean

#BUILD_DEPENDS+=	{perl>=5.10.1,p5-Test-Simple>=0.88}:../../devel/p5-Test-Simple

PERL5_PACKLIST=	auto/Net/Twitter/.packlist
USE_LANGUAGES=	# none
PERL5_MODULE_TYPE=	Module::Build

.include "../../lang/perl5/module.mk"
.include "../../mk/bsd.pkg.mk"
