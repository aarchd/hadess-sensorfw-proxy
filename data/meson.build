udev_dep = dependency('udev')
udev_rules_dir = udev_dep.get_variable(pkgconfig: 'udevdir') + '/rules.d'

systemd_dep = dependency('systemd')
systemd_system_unit_dir = systemd_dep.get_variable(pkgconfig: 'systemdsystemunitdir')

dbusconfdir = get_option('datadir') / 'dbus-1' / 'system.d'

polkit_gobject_dep = dependency('polkit-gobject-1', version: '>= 0.91')
polkit_policy_directory = polkit_gobject_dep.get_variable(pkgconfig: 'policydir')

prefix = get_option('prefix')
libexecdir = prefix / get_option('libexecdir')

service_d_dir = join_paths(systemd_system_unit_dir, 'iio-sensor-proxy.service.d')

install_data(
  '80-iio-sensor-proxy.rules',
  install_dir: udev_rules_dir
)

install_data(
  '10-hadess-sensorfw-proxy.conf',
  install_dir: service_d_dir
)

data_conf = configuration_data()
data_conf.set('libexecdir', libexecdir)

configure_file(
  input: 'iio-sensor-proxy.service.in',
  output: 'iio-sensor-proxy.service',
  configuration: data_conf,
  install_dir: systemd_system_unit_dir,
)

configure_file(
  input: 'net.hadess.SensorProxy.conf.in',
  output: 'net.hadess.SensorProxy.conf',
  configuration: data_conf,
  install_dir: dbusconfdir
)

polkit_policy = 'net.hadess.SensorProxy.policy'
if xmllint.found()
  test(polkit_policy,
       xmllint,
       args: [
           '--noout',
           meson.source_root() / 'data' / polkit_policy,
       ])
endif

install_data(
  polkit_policy,
  install_dir: polkit_policy_directory,
)
