# Debug Release�Ɍ���
set(CMAKE_CONFIGURATION_TYPES Debug Release CACHE TYPE INTERNAL FORCE )

# �v���W�F�N�g��
project(Test)

# CMake �o�[�W�����`�F�b�N
cmake_minimum_required(VERSION 2.8)

# �\�[�X�R�[�h�ݒ�
set(effekseer_src
	graphics_gl.cpp
	sound_al.cpp
	window.cpp
	main.cpp)

# �C���N���[�h�̐ݒ�
include_directories(
	../Effekseer/
	../EffekseerRendererGL/
	../EffekseerSoundAL/
	)

# 
link_directories(${PROJECT_SOURCE_DIR}/../lib/)

set(common_lib)
set(common_inc)

list(APPEND common_lib Effekseer )
list(APPEND common_lib EffekseerRendererGL )
list(APPEND common_lib EffekseerSoundAL )

if (MSVC)

else()
	list(APPEND common_lib GLEW )

	find_package(PNG REQUIRED)
	list(APPEND common_lib ${PNG_LIBRARY})

	find_package(Threads REQUIRED)
	list(APPEND common_lib ${CMAKE_THREAD_LIBS_INIT})

	find_package(X11 REQUIRED)
	list(APPEND common_inc ${X11_INCLUDE_DIR})
	list(APPEND common_lib ${X11_LIBRARIES})

	find_package(OpenGL)
	list(APPEND common_inc ${OPENGL_INCLUDE_DIR})
	list(APPEND common_lib ${OPENGL_LIBRARY})

	find_package(OpenAL)
	list(APPEND common_inc ${OPENAL_INCLUDE_DIR})
	list(APPEND common_lib ${OPENAL_LIBRARY})

endif()

# �R���p�C�����ǉ�
add_executable( effekseer ${effekseer_src} )
target_link_libraries(effekseer ${common_lib}) 

# �t���O����
add_definitions(-D__EFFEKSEER_RENDERER_GL_GLEW__)

# �o�͐�̐ݒ�
if (MSVC)
set_target_properties(effekseer PROPERTIES OUTPUT_NAME_DEBUG "Test" )
set_target_properties(effekseer PROPERTIES OUTPUT_NAME_RELEASE "Test" )
else()
set_target_properties(effekseer PROPERTIES OUTPUT_NAME "Test" )
endif()

install(
	TARGETS effekseer
	RUNTIME DESTINATION bin
	ARCHIVE DESTINATION bin
	LIBRARY DESTINATION bin)
