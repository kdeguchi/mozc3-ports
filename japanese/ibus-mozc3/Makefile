PKGNAMEPREFIX=	ja-ibus-
PKGNAMESUFFIX=	3

COMMENT=	Mozc engine for IBus

DATADIR=	${PREFIX}/share/ibus-${PORTNAME}

MASTERDIR=	${.CURDIR}/../../japanese/mozc3-server
SUB_FILES=	${WRKDIR}/pkg-message-ibus
PKGMESSAGE=	pkg-message-ibus

BUILD_MOZC_LIST=	ibus_mozc

.include "${MASTERDIR}/Makefile"
