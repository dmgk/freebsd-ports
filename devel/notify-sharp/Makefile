# Created by: Romain Tartiere <romain@blogreen.org>
# $FreeBSD$

PORTNAME=	notify-sharp
PORTVERSION=	0.4.0
PORTREVISION=	2
CATEGORIES=	devel
MASTER_SITES=	http://romain.blogreen.org/distfiles/

MAINTAINER=	mono@FreeBSD.org
COMMENT=	C\# client library for notification-daemon

BROKEN=		unfetchable
DEPRECATED=	Broken for more than 6 months
EXPIRATION_DATE=	2020-05-05

BUILD_DEPENDS=	${LOCALBASE}/libdata/pkgconfig/ndesk-dbus-glib-1.0.pc:devel/ndesk-dbus-glib
RUN_DEPENDS=	${LOCALBASE}/libdata/pkgconfig/ndesk-dbus-glib-1.0.pc:devel/ndesk-dbus-glib \
		${LOCALBASE}/libexec/notification-daemon:deskutils/notification-daemon

GNU_CONFIGURE=	yes
CONFIGURE_ENV=	ac_cv_path_GMCS=${LOCALBASE}/bin/mcs
USES=		gmake gnome mono pathfix pkgconfig
USE_GNOME=	gtksharp20

.include <bsd.port.mk>
