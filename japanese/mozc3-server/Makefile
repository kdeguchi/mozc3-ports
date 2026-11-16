CONFLICTS=	ja-fcitx5-mozc-* \
		ja-ibus-mozc-* \
		ja-mozc-el-* \
		ja-mozc-server-* \
		ja-mozc-tool-* \
		ja-uim-mozc-*

MASTERDIR=	${PORTSDIR}/japanese/mozc-server

DISTINFO_FILE=	${.CURDIR}/distinfo
PATCHDIR_UTDIC=	${.CURDIR}/files

BUILD_MOZC_LIST?=	mozc_server_ut

.if ${BUILD_MOZC_LIST:Mmozc_server_ut} == "mozc_server_ut" || make(makesum)

PKGNAMEPREFIX=	ja-
PKGNAMESUFFIX=	3-server

OPTIONS_DEFINE=	UTDIC
OPTIONS_GROUP=		UTDIC
OPTIONS_GROUP_UTDIC=	ALTCANNADIC EDICT2 JAWIKI NEOLOGD PERSONALNAME \
			PLACENAME SKKJISYO SUDACHIDICT
OPTIONS_DEFAULT=	JAWIKI PERSONALNAME PLACENAME SUDACHIDICT

.if make(makesum)
OPTIONS_SET_FORCE=	UTDIC ${OPTIONS_GROUP_UTDIC}
.endif

ALTCANNADIC_DESC=	Dictionary from Alt-Cannadic
EDICT2_DESC=		Dictionary from EDICT2
JAWIKI_DESC=		Dictionary from Japanese Wikipedia
NEOLOGD_DESC=		Dictionary from NEologd
PERSONALNAME_DESC=	Personal Name Dictionary
PLACENAME_DESC=		Place Name Dictionary
SKKJISYO_DESC=		Dictionary from from SKK-JISYO
SUDACHIDICT_DESC=	Dictionary from SudachiDict
UTDIC_DESC=		Additional UT Dictionaries

ALTCANNADIC_GH_TUPLE=	utuhiro78:mozcdic-ut-alt-cannadic:0e23741:altcannadic
EDICT2_GH_TUPLE=	utuhiro78:mozcdic-ut-edict2:8fe8f79:edict2
JAWIKI_GH_TUPLE=	utuhiro78:mozcdic-ut-jawiki:57af6ad:jawiki
NEOLOGD_GH_TUPLE=	utuhiro78:mozcdic-ut-neologd:e33ac4c:neologd
PERSONALNAME_GH_TUPLE=	utuhiro78:mozcdic-ut-personal-names:b557dd4:personal
PLACENAME_GH_TUPLE=	utuhiro78:mozcdic-ut-place-names:98cf8e9:place
SKKJISYO_GH_TUPLE=	utuhiro78:mozcdic-ut-skk-jisyo:384ad92:skkjisyo
SUDACHIDICT_GH_TUPLE=	utuhiro78:mozcdic-ut-sudachidict:13129dd:sudachi

UTDIC_GH_TUPLE=		utuhiro78:merge-ut-dictionaries:6239884:ut
UTDIC_MASTER_SITES=	http://download.wikimedia.org/jawiki/20261001/:jawiki_index
UTDIC_DISTFILES=	jawiki-20261001-pages-articles-multistream-index.txt.bz2:jawiki_index
UTDIC_EXTRA_PATCHES=	${PATCHDIR_UTDIC}/extra-patch-merge_dictionaries.py

ALTCANNADIC_EXTRACT_ONLY=	${DISTFILE_altcannadic}
EDICT2_EXTRACT_ONLY=		${DISTFILE_edict2}
JAWIKI_EXTRACT_ONLY=		${DISTFILE_jawiki}
NEOLOGD_EXTRACT_ONLY=		${DISTFILE_neologd}
PERSONALNAME_EXTRACT_ONLY=	${DISTFILE_personal}
PLACENAME_EXTRACT_ONLY=		${DISTFILE_place}
SKKJISYO_EXTRACT_ONLY=		${DISTFILE_skkjisyo}
SUDACHIDICT_EXTRACT_ONLY=	${DISTFILE_sudachi}
UTDIC_EXTRACT_ONLY=		${DISTFILE_ut}

ALTCANNADIC_IMPLIES=	UTDIC
EDICT2_IMPLIES=		UTDIC
JAWIKI_IMPLIES=		UTDIC
NEOLOGD_IMPLIES=		UTDIC
PERSONALNAME_IMPLIES=	UTDIC
PLACENAME_IMPLIES=		UTDIC
SKKJISYO_IMPLIES=		UTDIC
SUDACHIDICT_IMPLIES=	UTDIC

SUB_FILES+=	mozc

.endif

.include "${MASTERDIR}/Makefile"

.if ${BUILD_MOZC_LIST:Mmozc_server_ut} == "mozc_server_ut"

PLIST_FILES+=	bin/mozc \
		bin/mozc_emacs_helper \
		libexec/mozc_server \
		libexec/mozc_emacs_helper \
		%%DATADIR%%/icons/mozc.png \
		%%DATADIR%%/icons/mozc.svg \
		%%DATADIR%%/icons/alpha_full.png \
		%%DATADIR%%/icons/alpha_full.svg \
		%%DATADIR%%/icons/alpha_half.png \
		%%DATADIR%%/icons/alpha_half.svg \
		%%DATADIR%%/icons/direct.png \
		%%DATADIR%%/icons/direct.svg \
		%%DATADIR%%/icons/hiragana.png \
		%%DATADIR%%/icons/hiragana.svg \
		%%DATADIR%%/icons/katakana_full.png \
		%%DATADIR%%/icons/katakana_full.svg \
		%%DATADIR%%/icons/katakana_half.png \
		%%DATADIR%%/icons/katakana_half.svg \
		%%DATADIR%%/icons/dictionary.png \
		%%DATADIR%%/icons/dictionary.svg \
		%%DATADIR%%/icons/properties.png \
		%%DATADIR%%/icons/properties.svg \
		%%DATADIR%%/icons/tool.png \
		%%DATADIR%%/icons/tool.svg \
		%%DATADIR%%/icons/white/dictionary.svg \
		%%DATADIR%%/icons/white/properties.svg \
		%%DATADIR%%/icons/white/tool.svg \
		%%DATADIR%%/icons/outlined/dictionary.svg \
		%%DATADIR%%/icons/outlined/properties.svg \
		%%DATADIR%%/icons/outlined/tool.svg

_UTDIC=	0

. for utopt in ${OPTIONS_GROUP_UTDIC}
.  if ${PORT_OPTIONS:M${utopt}} == ${utopt}
_UTDIC=	1
.  break
.  endif
. endfor

. if ${_UTDIC} == 1

. if ${PORT_OPTIONS:MNEOLOGD} || ${PORT_OPTIONS:MPERSONALNAME} || \
	${PORT_OPTIONS:MPLACENAME} || ${PORT_OPTIONS:MSUDACHIDICT}
LICENSE+=	APACHE20
LICENSE_DISTFILES_APACHE20=	${DISTFILE_ut} \
		${DISTFILE_neologd} \
		${DISTFILE_personal} \
		${DISTFILE_place}
.  endif

.  if ${PORT_OPTIONS:MEDICT2} || ${PORT_OPTIONS:MJAWIKI}
LICENSE+=	CC-BY-SA-4.0
LICENSE_DISTFILES_CC-BY-SA-4.0=	${DISTFILE_edict2} \
		${DISTFILE_jawiki}
.  endif

.  if ${PORT_OPTIONS:MALTCANNADIC} || ${PORT_OPTIONS:MSKKJISYO}
LICENSE+=	GPLv2
LICENSE_DISTFILES_GPLv2=	${DISTFILE_altcannadic} \
		${DISTFILE_skkjisyo}
.  endif

post-extract-mozc_server_ut:
	${CP} ${WRKSRC_ut}/src/merge/merge_dictionaries.py ${BUILD_WRKSRC}

post-extract: post-extract-mozc_server_ut

post-patch-mozc_server_ut:
	@${ECHO_MSG} "===> Creating mozcdic-ut.txt for UT Dictionary. It takes a long time!"
	cd ${WRKSRC_ut}/src/merge && \
		${CP} ${BUILD_WRKSRC}/merge_dictionaries.py . && \
		${REINPLACE_CMD} -e 's@%%WRKSRC%%@${WRKSRC}@' merge_dictionaries.py && \
		${RLN} ${BUILD_WRKSRC}/data/dictionary_oss/id.def . && \
		${CP} ${DISTDIR}/${DIST_SUBDIR}/${DISTFILES:M*\:jawiki_index:C@:jawiki_index@@} jawiki-latest-pages-articles-multistream-index.txt.bz2 && \
		${BZCAT} ../../../mozcdic-ut-*/mozcdic-ut-*.txt.bz2 > mozcdic-ut.txt && \
		${PYTHON_CMD} merge_dictionaries.py mozcdic-ut.txt && \
		${CAT} mozcdic-ut.txt \
			>> ${BUILD_WRKSRC}/data/dictionary_oss/dictionary00.txt

post-patch: post-patch-mozc_server_ut

. endif # _UDIC

do-build-mozc_server_ut:
	${BUILD_MOZC_CMD} \
		//server:mozc_server \
		//unix/emacs:mozc_emacs_helper \
		//unix:icons

do-install-mozc_server_ut:
	cd ${BUILD_WRKSRC} && ${INSTALL_PROGRAM} \
		bazel-bin/server/mozc_server \
		bazel-bin/unix/emacs/mozc_emacs_helper \
		${STAGEDIR}${PREFIX}/libexec
	${RLN} ${STAGEDIR}${PREFIX}/libexec/mozc_emacs_helper \
		${STAGEDIR}${PREFIX}/bin/mozc_emacs_helper
	${INSTALL_SCRIPT} \
		${WRKDIR}/mozc ${STAGEDIR}/${PREFIX}/bin
	@${MKDIR} ${STAGEDIR}${DATADIR}/icons
	${UNZIP_NATIVE_CMD} -q \
		${BUILD_WRKSRC}/bazel-bin/unix/icons.zip \
		-d ${STAGEDIR}${DATADIR}/icons

.endif

.if ${BUILD_MOZC_LIST:Mmozc_tool} == "mozc_tool"
RUN_DEPENDS:=	${RUN_DEPENDS:S/mozc-/mozc3-/g}
.endif

.if ${BUILD_MOZC_LIST:Mibus_mozc} == "ibus_mozc"
RUN_DEPENDS:=	${RUN_DEPENDS:S/mozc-/mozc3-/g}
.endif

.if ${BUILD_MOZC_LIST:Muim_mozc} == "uim_mozc"
RUN_DEPENDS:=	${RUN_DEPENDS:S/mozc-/mozc3-/g}
.endif

.if ${BUILD_MOZC_LIST:Mfcitx5_mozc} == "fcitx5_mozc"
RUN_DEPENDS:=	${RUN_DEPENDS:S/mozc-/mozc3-/g}
.endif

.if ${BUILD_MOZC_LIST:Mmozc_el} == "mozc_el"
RUN_DEPENDS:=	${RUN_DEPENDS:S/mozc-/mozc3-/g}
.endif
