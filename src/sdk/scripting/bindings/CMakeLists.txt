# bindings CMakeLists

find_package(wxWidgets REQUIRED COMPONENTS net core base)
include(${wxWidgets_USE_FILE})

include_directories(
	"${PROJECT_SOURCE_DIR}/src/include/scripting/include"
	"${PROJECT_SOURCE_DIR}/src/include"
	"${PROJECT_SOURCE_DIR}/src/include/tinyxml"
	"${PROJECT_SOURCE_DIR}/src/sdk/wxscintilla/include"
	"${PROJECT_SOURCE_DIR}/src/include/scripting/squirrel"
	"${PROJECT_SOURCE_DIR}/src/include/scripting/bindings"
	"${PROJECT_SOURCE_DIR}/src/include/scripting/sqplus"
)

add_library(sqbindings STATIC
	scriptbindings.cpp
	sc_consts.cpp
	sc_dialog.cpp
	sc_globals.cpp
	sc_io.cpp
	sc_plugin.cpp
	sc_progress.cpp
	sc_util_dialogs.cpp
	sc_wxtypes.cpp
)

# target_link_libraries(sqbindings
#	${wxWidgets_LIBRARIES}
# )
