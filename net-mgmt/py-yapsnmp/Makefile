# Created by: arved
# $FreeBSD$

PORTNAME=	yapsnmp
PORTVERSION=	0.7.8
PORTREVISION=	8
CATEGORIES=	net-mgmt python
MASTER_SITES=	SF
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	arved@FreeBSD.org
COMMENT=	Python SNMP module based on net-snmp

LICENSE=	LGPL21
LICENSE_FILE=	${WRKSRC}/COPYING

DEPRECATED=	Uses deprecated version of python
EXPIRATION_DATE=	2020-08-15

LIB_DEPENDS=	libnetsnmp.so:net-mgmt/net-snmp

USES=		gmake libtool python:2.7 ssl
GNU_CONFIGURE=	yes
CPPFLAGS+=	-I${LOCALBASE}/include -I${PYTHON_INCLUDEDIR}
LDFLAGS+=	-L${LOCALBASE}/lib
CONFIGURE_ARGS+=--enable-site-packages-prefix=${PREFIX}

.include <bsd.port.pre.mk>

.if (${ARCH} == "i386")
CPPFLAGS+=	-fstack-protector -I${LOCALBASE}/include
.endif

post-patch:
	${REINPLACE_CMD} -e "s,-lsnmp,-lnetsnmp," \
		${WRKSRC}/configure

.include <bsd.port.post.mk>
