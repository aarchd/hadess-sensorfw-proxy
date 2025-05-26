project('hadess-sensorfw-proxy', 'cpp', version: '1.0')

gio = dependency('gio-2.0', required: true)
gio_unix = dependency('gio-unix-2.0', required: true)
glib = dependency('glib-2.0', required: true)
glib_util = dependency('libglibutil', required: true)
gbinder = dependency('libgbinder', version: '>=1.1.20', required: true)

add_project_arguments('-pthread', language: ['c', 'cpp'])

subdir('data')
subdir('sensorfw-core')

executable(
  'hadess-sensorfw-proxy',
  [
    'iio-sensor-proxy.cpp',
    'iio-sensor-proxy-resources.cpp',
    'orientation.cpp'
  ],
  include_directories: include_directories('.', 'sensorfw-core/include'),
  dependencies: [
    gio, gio_unix, glib, glib_util, gbinder
  ],
  link_with: sensorfw_core_lib,
  install: true,
  install_dir: get_option('bindir')
)
