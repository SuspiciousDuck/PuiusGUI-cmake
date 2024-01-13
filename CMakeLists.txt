cmake_minimum_required(VERSION 3.5.0)
project(puiusgui)

file(GLOB files CONFIGURE_DEPENDS "src/*.c")
file(GLOB headers "src/include/*.h" "src/include/*.hpp")

add_library(${PROJECT_NAME} SHARED ${files})

find_package(SDL2 REQUIRED)
find_package(SDL2_image REQUIRED)
find_package(SDL2_ttf REQUIRED)
target_include_directories(${PROJECT_NAME} PUBLIC src/include)
target_link_libraries(${PROJECT_NAME} PUBLIC ${SDL2_LIBRARIES})
set_target_properties(${PROJECT_NAME} PROPERTIES
    PUBLIC_HEADER "${headers}"
)

install(TARGETS ${PROJECT_NAME} LIBRARY DESTINATION lib/ PUBLIC_HEADER DESTINATION include/${PROJECT_NAME})