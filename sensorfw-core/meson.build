sensorfw_core_utils_srcs = files(
  'utils/socketreader.cpp',
  'utils/dbus_connection_handle.cpp',
  'utils/event_loop.cpp',
  'utils/handler_registration.cpp',
  'include/utils/socketreader.h'
)

sensorfw_core_plugins_srcs = files(
  'plugins/sensorfw_accelerometer_sensor.cpp',
  'plugins/sensorfw_common.cpp',
  'plugins/sensorfw_compass_sensor.cpp',
  'plugins/sensorfw_gyroscope_sensor.cpp',
  'plugins/sensorfw_humidity_sensor.cpp',
  'plugins/sensorfw_lid_sensor.cpp',
  'plugins/sensorfw_light_sensor.cpp',
  'plugins/sensorfw_magnetometer_sensor.cpp',
  'plugins/sensorfw_orientation_sensor.cpp',
  'plugins/sensorfw_pressure_sensor.cpp',
  'plugins/sensorfw_proximity_sensor.cpp',
  'plugins/sensorfw_rotation_sensor.cpp',
  'plugins/sensorfw_stepcounter_sensor.cpp',
  'plugins/sensorfw_tap_sensor.cpp',
  'plugins/sensorfw_temperature_sensor.cpp'
)

sensorfw_core_lib = static_library(
  'sensorfw-core',
  sensorfw_core_utils_srcs + sensorfw_core_plugins_srcs,
  include_directories: include_directories('include'),
  dependencies: [gio, gio_unix, glib_util]
)
