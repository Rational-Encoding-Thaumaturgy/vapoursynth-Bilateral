project('Bilateral', 'cpp',
  default_options: ['buildtype=release', 'warning_level=2', 'b_lto=true', 'b_ndebug=if-release', 'cpp_std=c++17'],
  license: 'GPL-3.0-or-later',
  meson_version: '>=0.51.0',
  version: '13'
)

cxx = meson.get_compiler('cpp')

gcc_syntax = cxx.get_argument_syntax() == 'gcc'

if gcc_syntax
  vapoursynth_dep = dependency('vapoursynth', version: '>=54').partial_dependency(compile_args: true, includes: true)
  install_dir = vapoursynth_dep.get_variable(pkgconfig: 'libdir') / 'vapoursynth'
else
  vapoursynth_dep = []
  install_dir = get_option('libdir') / 'vapoursynth'
endif

sources = [
  'source/Bilateral.cpp',
  'source/Gaussian.cpp',
  'source/VSPlugin.cpp'
]


shared_module('bilateral', sources,
  dependencies: vapoursynth_dep,
  include_directories: include_directories('include'),
  link_with: [],
  install: true,
  install_dir: install_dir,
  gnu_symbol_visibility: 'hidden'
)
