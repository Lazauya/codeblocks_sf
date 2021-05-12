# cb share config CMakeLists

find_package(wxWidgets REQUIRED COMPONENTS net core base)
include(${wxWidgets_USE_FILE})

find_package(PkgConfig REQUIRED)

pkg_check_modules(GLIB REQUIRED glib-2.0)

include_directories(
	"${PROJECT_SOURCE_DIR}/src/include"
	"${PROJECT_SOURCE_DIR}/src/include/tinyxml"
	"${GLIB_INCLUDE_DIRS}"
)

add_executable(cb_share_config app.cpp mainframe.cpp)

# target_include_directories(cb_share_config PRIVATE ${GLIB_INCLUDE_DIRS})
target_link_libraries(cb_share_config ${wxWidgets_LIBRARIES} ${GLIB_LDFLAGS} tinyxml)
