include_directories("${PROJECT_SOURCE_DIR}/src/include/tinyxml")

# set(CMAKE_CXX_FLAGS "-DHAVE_CONFIG_H -DTIXML_USE_STL=YES")

add_library (tinyxml STATIC
    tinystr.cpp
	tinyxml.cpp
	tinyxmlerror.cpp
	tinyxmlparser.cpp
)
