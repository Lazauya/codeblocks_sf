# squirrel CMakeLists

include_directories(
	"${PROJECT_SOURCE_DIR}/src/include/scripting/include"
	"${PROJECT_SOURCE_DIR}/src/include/scripting/squirrel"
)

add_library(squirrel STATIC
	sqfuncstate.cpp
	sqcompiler.cpp
	sqmem.cpp
	sqlexer.cpp
	sqstate.cpp
	sqvm.cpp
	sqtable.cpp
	sqbaselib.cpp
	sqclass.cpp
	sqobject.cpp
	sqapi.cpp
	sqdebug.cpp
)
