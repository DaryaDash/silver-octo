# CMakeList.txt: проект CMake для CMakeProject1; включите исходный код и определения,
# укажите здесь логику для конкретного проекта.
#
cmake_minimum_required (VERSION 3.8)

# Включение горячей перезагрузки для компиляторов MSVC, если поддерживается.
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project ("CMakeProject1")


add_executable (CMakeProject1 "CMakeProject1.cpp" "CMakeProject1.h" )

find_package(glad CONFIG REQUIRED)
target_link_libraries(CMakeProject1 PRIVATE glad::glad)


find_package(glfw3 CONFIG REQUIRED)
target_link_libraries(CMakeProject1 PRIVATE glfw)

find_package(imgui CONFIG REQUIRED)
target_link_libraries(CMakeProject1 PRIVATE imgui::imgui)





# TODO: Добавьте тесты и целевые объекты, если это необходимо.
