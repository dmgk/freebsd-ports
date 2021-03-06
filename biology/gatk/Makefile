# $FreeBSD$

PORTNAME=	gatk
DISTVERSION=	4.1.5.0
CATEGORIES=	biology java
EXTRACT_ONLY=	${DISTNAME}${EXTRACT_SUFX}

MAINTAINER=	yuri@FreeBSD.org
COMMENT=	Variant discovery in high-throughput sequencing data

LICENSE=	BSD3CLAUSE
LICENSE_FILE=	${WRKSRC}/LICENSE.TXT

BUILD_DEPENDS=	gradle:devel/gradle

USES=		gettext-runtime
USE_GITHUB=	yes
GH_ACCOUNT=	broadinstitute
USE_JAVA=	yes

SUB_FILES=	${PORTNAME}.sh
SUB_LIST=	PORTVERSION=${PORTVERSION} JAVA=${JAVA}

NO_ARCH=	yes

DEPS_CACHE_DIR=	${WRKDIR}

PLIST_FILES=	bin/${PORTNAME} \
		${JAVAJARDIR}/GenomeAnalysisTK-${PORTVERSION}.jar

# TODO additionally fetch git-lfs files: https://github.com/broadinstitute/gatk/issues/6395

# to rebuild the deps archive:
#   1. set DEV_UPDATE_MODE=yes
#   2. make makesum build
#   3. upload the *-deps archive
#   4. set DEV_UPDATE_MODE=no
#   5. make clean makesum

DEV_UPDATE_MODE=	no

.if (${DEV_UPDATE_MODE} == "yes")
post-build:
	@cd ${DEPS_CACHE_DIR} && ${TAR} czf ${DISTDIR}/${PORTNAME}-${DISTVERSION}-deps${EXTRACT_SUFX} gradle-${PORTNAME}
	@${ECHO} "(!!!) Please upload the gradle deps archive: ${DISTDIR}/${PORTNAME}-${DISTVERSION}-deps${EXTRACT_SUFX}"
.else
MASTER_SITES=	LOCAL/yuri/:deps
DISTFILES=	${PORTNAME}-${DISTVERSION}-deps${EXTRACT_SUFX}:deps
GRADLE_ARGS=	--offline

post-extract: # need a separate extract step because the cache is in /tmp, and not under work/ like with maven
	@cd ${DEPS_CACHE_DIR} && ${TAR} xzf ${DISTDIR}/${PORTNAME}-${DISTVERSION}-deps${EXTRACT_SUFX}
.endif


do-build:
	@cd ${WRKSRC} && ${SETENV} ${MAKE_ENV} gradle \
		--gradle-user-home ${DEPS_CACHE_DIR}/gradle-${PORTNAME} --project-cache-dir ${DEPS_CACHE_DIR}/gradle-${PORTNAME} \
		${GRADLE_ARGS} --build-cache localJar

do-install:
	${INSTALL_SCRIPT} ${WRKDIR}/${PORTNAME}.sh ${STAGEDIR}${PREFIX}/bin/${PORTNAME}
	${INSTALL_DATA} ${WRKSRC}/build/libs/gatk-package-1.0-SNAPSHOT-local.jar ${STAGEDIR}${JAVAJARDIR}/GenomeAnalysisTK-${PORTVERSION}.jar

.include <bsd.port.mk>
