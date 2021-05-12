# lower src CMakeLists

add_subdirectory(resources)

find_package(wxWidgets REQUIRED COMPONENTS richtext std aui propgrid net core base)
include(${wxWidgets_USE_FILE})

find_package(PkgConfig REQUIRED)
pkg_check_modules(GLIB REQUIRED glib-2.0)
pkg_check_modules (GTK2 REQUIRED gtk+-2.0)

# set(CMAKE_CXX_FLAGS "-DHAVE_CONFIG_H -DTIXML_USE_STL=YES")

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

# set(CMAKE_INSTALL_RPATH_USE_LINK_PATH TRUE)
# set(CMAKE_SKIP_INSTALL_RPATH FALSE)
set(CMAKE_INSTALL_RPATH "${CMAKE_INSTALL_PREFIX}/lib" )

add_executable(codeblocks
	app.cpp 
	appglobals.cpp 
	backtracedlg.cpp 
	breakpointsdlg.cpp 
	compilersettingsdlg.cpp 
	cpuregistersdlg.cpp 
	crashhandler.cpp 
	debugger_interface_creator.cpp 
	debuggermenu.cpp 
	debuggersettingscommonpanel.cpp 
	debuggersettingsdlg.cpp 
	debuggersettingspanel.cpp 
	disassemblydlg.cpp 
	dlgabout.cpp 
	dlgaboutplugin.cpp 
	editkeywordsdlg.cpp 
	editorconfigurationdlg.cpp 
	environmentsettingsdlg.cpp 
	examinememorydlg.cpp 
	find_replace.cpp 
	goto_file.cpp 
	infopane.cpp 
	main.cpp 
	notebookstyles.cpp 
	printdlg.cpp 
	projectmanagerui.cpp 
	projectdepsdlg.cpp 
	projectoptionsdlg.cpp 
	recentitemslist.cpp 
	scriptconsole.cpp 
	scriptingsettingsdlg.cpp 
	splashscreen.cpp 
	startherepage.cpp 
	switcherdlg.cpp 
	threadsdlg.cpp 
	virtualbuildtargetsdlg.cpp 
	watchesdlg.cpp
)

target_link_libraries(codeblocks
	${wxWidgets_LIBRARIES} 
	${GLIB_LDFLAGS}
	${GTK2_LIBRARIES}
	libcodeblocks
)

install(TARGETS codeblocks DESTINATION bin)
