# CMakeList.txt: 顶层 CMake 项目文件，在此处执行全局配置
# 并包含子项目。
#
cmake_minimum_required (VERSION 3.12)

# 如果支持，请为 MSVC 编译器启用热重载。
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project ("SoftwareRasterizationProjects")

# 包含子项目。
#add_subdirectory ("SoftwareRasterizationProjects")
#add_subdirectory ("01_lectureCodes01-Windows")
#add_subdirectory ("02_lectureCodes02-GDI")
#add_subdirectory ("03_lectureCodes03-Lines")
#add_subdirectory ("04_lectureCodes04-Vectors")
#add_subdirectory ("05_lectureCodes05-Triangles")
#add_subdirectory ("06_lectureCodes06-Image")
#add_subdirectory ("07_lectureCodes07-UV")
#add_subdirectory ("08_lectureCodes08-Bilinear")
#add_subdirectory ("09_lectureCodes09-Wrap")
#add_subdirectory ("10_lectureCodes10-Matrix")
#add_subdirectory ("11_lectureCodes11-Transform")
#add_subdirectory ("12_lectureCodes12-VAO-VBO")
#add_subdirectory ("13_lectureCodes13-DataFunctions")
#add_subdirectory ("14_lectureCodes14-Draw")
#add_subdirectory ("15_lectureCodes15-Clip")
#add_subdirectory ("16_lectureCodes16-PerspectiveCorrection")
#add_subdirectory ("17_lectureCodes17-CullFace")
#add_subdirectory ("18_lectureCodes18-depthTest")
add_subdirectory ("19_lectureCodes19-blending")