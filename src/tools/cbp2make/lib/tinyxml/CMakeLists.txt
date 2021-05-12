include_directories("${PROJECT_SOURCE_DIR}/src/include/tinyxml")

add_library (tinyxmlcbp2make
	tinystr.cpp
	tinyxml.cpp
	tinyxmlerror.cpp
	tinyxmlparser.cpp
)
