project('vk-msaa-triangle', 'cpp',
  license: 'BSL',
	version: '0.1.0',
	meson_version: '>=0.38',
  default_options: ['cpp_std=c++1z'])

# default arrguments
# warnings and stuff
add_project_arguments(
	'-Wall',
	'-Wextra',
	'-Wno-unused-parameter',
	'-Wpedantic',
	'-Wno-missing-braces',
	language: 'cpp')

# project-specific stuff
source_root = meson.source_root().split('\\')
add_project_arguments('-DDLG_BASE_PATH="' + '/'.join(source_root) + '/"', language: 'cpp')

dep_vpp = dependency('vpp', fallback: ['vpp', 'vpp_dep'])
dep_ny = dependency('ny', fallback: ['ny', 'ny_dep'])
dep_vulkan = dependency('vulkan')

subdir('assets/shaders')
shader_inc = include_directories('assets') # for headers in build folder

src = [
	shaders,
	'engine.cpp',
	'main.cpp',
	'render.cpp',
	'window.cpp']

executable('triangle', src,
	dependencies: [dep_vpp, dep_vulkan, dep_ny],
	include_directories: shader_inc)
