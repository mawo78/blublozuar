find_package(fmt CONFIG)
find_package(spdlog CONFIG)
find_package(docopt CONFIG)

# Generic test that uses conan libs
add_executable(blublozaur main.cpp)
target_link_libraries(
  blublozaur
  PRIVATE project_options
          project_warnings
          docopt::docopt
          fmt::fmt
          spdlog::spdlog)

target_link_system_libraries(
  blublozaur
  PRIVATE
  ftxui::screen
  ftxui::dom
  ftxui::component)

target_include_directories(blublozaur PRIVATE "${CMAKE_BINARY_DIR}/configured_files/include")
