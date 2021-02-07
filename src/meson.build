vapi_dir = meson.source_root() / 'vapi'
add_project_arguments(['--vapidir', vapi_dir], language: 'vala')

autosampler3_sources = [
  'main.vala',
  'window.vala',
]

autosampler3_deps = [
  dependency('gio-2.0', version: '>= 2.50'),
  dependency('gtk+-3.0', version: '>= 3.22'),
  meson.get_compiler('c').find_library('portmidi'),
  meson.get_compiler('vala').find_library('portmidi', dirs: vapi_dir),
]

gnome = import('gnome')

autosampler3_sources += gnome.compile_resources('autosampler3-resources',
  'autosampler3.gresource.xml',
  c_name: 'autosampler3'
)

executable('autosampler3', autosampler3_sources,
  vala_args: '--target-glib=2.50',  dependencies: autosampler3_deps,
  install: true,
)


