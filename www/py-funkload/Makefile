# Created by: Li-Wen Hsu <lwhsu@lwhsu.org>
# $FreeBSD$

PORTNAME=	funkload
PORTVERSION=	1.17.1
PORTREVISION=	1
CATEGORIES=	www python
MASTER_SITES=	CHEESESHOP
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	lwhsu@FreeBSD.org
COMMENT=	Functional and load web tester

LICENSE=	GPLv2

DEPRECATED=	Uses deprecated version of python
EXPIRATION_DATE=	2020-08-15

RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}docutils>0:textproc/py-docutils@${PY_FLAVOR} \
		${LOCALBASE}/bin/gnuplot:math/gnuplot \
		${PYTHON_PKGNAMEPREFIX}webunit>=1.3.8:www/py-webunit@${PY_FLAVOR} \
		tcpwatch.py:net/tcpwatch

USES=		python:2.7
USE_PYTHON=	autoplist distutils

.include <bsd.port.mk>
