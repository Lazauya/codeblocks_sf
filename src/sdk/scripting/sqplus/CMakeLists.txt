# sqplus CMakeLists

include_directories(
	"${PROJECT_SOURCE_DIR}/src/include/scripting/include"
	"${PROJECT_SOURCE_DIR}/src/include/scripting/squirrel"
	"${PROJECT_SOURCE_DIR}/src/include/scripting/sqplus"
)

add_library(sqplus STATIC
	SqPlus.cpp
	SquirrelVM.cpp
	SquirrelBindingsUtils.cpp
	SquirrelObject.cpp
)
