# sqstdlib CMakeLists

include_directories(
	"${PROJECT_SOURCE_DIR}/src/include/scripting/include"
	"${PROJECT_SOURCE_DIR}/src/include/scripting/squirrel"
	"${PROJECT_SOURCE_DIR}/src/include/scripting/sqstdlib"
)

add_library(sqstdlib STATIC
	sqstdsystem.cpp
	sqstdmath.cpp
	sqstdstream.cpp
	sqstdaux.cpp
	sqstdrex.cpp
	sqstdstring.cpp
	sqstdio.cpp
	sqstdblob.cpp
)
