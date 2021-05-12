# sdk CMakeLists

# add_subdirectory(mozilla_chardet)
add_subdirectory(resources)
add_subdirectory(scripting)
add_subdirectory(wxscintilla)

find_package(wxWidgets REQUIRED COMPONENTS net core base)
include(${wxWidgets_USE_FILE})

find_package(PkgConfig REQUIRED)
pkg_check_modules(GLIB REQUIRED glib-2.0)
pkg_check_modules (GTK2 REQUIRED gtk+-2.0)

# -DHAVE_CONFIG_H -DTIXML_USE_STL=YES
set(CMAKE_CXX_FLAGS "-DSCI_LEXER -DLINK_LEXERS -D__WX__ -DGTK")

include_directories( 
	"${PROJECT_SOURCE_DIR}/src/include"
	"${PROJECT_SOURCE_DIR}/src/include/tinyxml"
	"${PROJECT_SOURCE_DIR}/src/include/scripting"
	"${PROJECT_SOURCE_DIR}/src/include/scripting/include"
	"${PROJECT_SOURCE_DIR}/src/include/scripting/bindings"
	"${PROJECT_SOURCE_DIR}/src/include/scripting/sqplus"
	"${PROJECT_SOURCE_DIR}/src/include/scripting/sqstdlib"
	"${PROJECT_SOURCE_DIR}/src/include/scripting/squirrel"
	"${PROJECT_SOURCE_DIR}/src/sdk/wxscintilla/include"
	"${PROJECT_SOURCE_DIR}/src/sdk/mozilla_chardet/include"
	"${PROJECT_SOURCE_DIR}/src/sdk/mozilla_chardet/include/mfbt"
	"${PROJECT_SOURCE_DIR}/src/sdk/mozilla_chardet/include/mfbt/mozilla"
	"${PROJECT_SOURCE_DIR}/src/sdk/mozilla_chardet/include/nsprpub/pr/include/"
	"${PROJECT_SOURCE_DIR}/src/sdk/mozilla_chardet/include/xpcom/base"
	"${PROJECT_SOURCE_DIR}/src/sdk/mozilla_chardet/include/xpcom/glue"
	"${GLIB_INCLUDE_DIRS}"
	"${GTK2_INCLUDE_DIRS}"
)

add_library(libcodeblocks SHARED
	annoyingdialog.cpp 
	autodetectcompilers.cpp 
	base64.cpp 
	blockallocated.cpp 
	cbart_provider.cpp 
	cbauibook.cpp 
	cbcolourmanager.cpp 
	cbdebugger_interfaces.cpp 
	cbeditor.cpp 
	cbeditorprintout.cpp 
	cbexception.cpp 
	cbplugin.cpp 
	cbproject.cpp 
	cbstatusbar.cpp 
	cbstyledtextctrl.cpp 
	cbthreadpool.cpp 
	cbtreectrl.cpp 
	cbworkspace.cpp 
	ccmanager.cpp 
	compileoptionsbase.cpp 
	compiler.cpp 
	compilercommandgenerator.cpp 
	compilerfactory.cpp 
	compileroptions.cpp 
	compiletargetbase.cpp 
	configmanager-revision.cpp 
	configmanager.cpp 
	configurationpanel.cpp 
	configuretoolsdlg.cpp 
	confirmreplacedlg.cpp 
	crc32.cpp 
	debuggermanager.cpp 
	editarrayfiledlg.cpp 
	editarrayorderdlg.cpp 
	editarraystringdlg.cpp 
	editor_hooks.cpp 
	editor_utils.cpp 
	editorbase.cpp 
	editorcolourset.cpp 
	editorlexerloader.cpp 
	editormanager.cpp 
	editpairdlg.cpp 
	editpathdlg.cpp 
	edittooldlg.cpp 
	encodingdetector.cpp 
	externaldepsdlg.cpp 
	filefilters.cpp 
	filegroupsandmasks.cpp 
	filemanager.cpp 
	findreplacedlg.cpp 
	genericmultilinenotesdlg.cpp 
	globals.cpp 
	importers_globals.cpp 
	incremental_select_helper.cpp 
	infowindow.cpp 
	loggers.cpp 
	logmanager.cpp 
	macrosmanager.cpp 
	manager.cpp 
	menuitemsmanager.cpp 
	multiselectdlg.cpp 
	newfromtemplatedlg.cpp 
	personalitymanager.cpp 
	pipedprocess.cpp 
	pluginmanager.cpp 
	pluginsconfigurationdlg.cpp 
	printing_types.cpp 
	projectbuildtarget.cpp 
	projectfile.cpp 
	projectfileoptionsdlg.cpp 
	projectlayoutloader.cpp 
	projectloader.cpp 
	projectloader_hooks.cpp 
	projectmanager.cpp 
	projectsfilemasksdlg.cpp 
	projecttemplateloader.cpp 
	scriptingmanager.cpp 
	scriptsecuritywarningdlg.cpp 
	scrollingdialog.cpp 
	sdk_events.cpp 
	searchresultslog.cpp 
	selecttargetdlg.cpp 
	templatemanager.cpp 
	tinywxuni.cpp 
	toolsmanager.cpp 
	uservarmanager.cpp 
	workspaceloader.cpp 
	xtra_res.cpp  
	mozilla_chardet/src/CharDistribution.cpp 
	mozilla_chardet/src/JpCntx.cpp 
	mozilla_chardet/src/LangBulgarianModel.cpp 
	mozilla_chardet/src/LangCyrillicModel.cpp 
	mozilla_chardet/src/LangGreekModel.cpp 
	mozilla_chardet/src/LangHebrewModel.cpp 
	mozilla_chardet/src/LangHungarianModel.cpp 
	mozilla_chardet/src/LangThaiModel.cpp 
	mozilla_chardet/src/nsBig5Prober.cpp 
	mozilla_chardet/src/nsCharSetProber.cpp 
	mozilla_chardet/src/nsEscCharsetProber.cpp 
	mozilla_chardet/src/nsEscSM.cpp 
	mozilla_chardet/src/nsEUCJPProber.cpp 
	mozilla_chardet/src/nsEUCKRProber.cpp 
	mozilla_chardet/src/nsEUCTWProber.cpp 
	mozilla_chardet/src/nsGB2312Prober.cpp 
	mozilla_chardet/src/nsHebrewProber.cpp 
	mozilla_chardet/src/nsLatin1Prober.cpp 
	mozilla_chardet/src/nsMBCSGroupProber.cpp 
	mozilla_chardet/src/nsMBCSSM.cpp 
	mozilla_chardet/src/nsSBCharSetProber.cpp 
	mozilla_chardet/src/nsSBCSGroupProber.cpp 
	mozilla_chardet/src/nsSJISProber.cpp 
	mozilla_chardet/src/nsUniversalDetector.cpp 
	mozilla_chardet/src/nsUTF8Prober.cpp
)

set_target_properties(libcodeblocks PROPERTIES PREFIX "")

target_link_libraries(libcodeblocks
	${wxWidgets_LIBRARIES} 
	${GLIB_LDFLAGS}
	${GTK2_LIBRARIES}
	wxscintilla
	tinyxml
	sqbindings
	sqplus
	squirrel
	sqstdlib	
)

install(TARGETS libcodeblocks DESTINATION lib)
