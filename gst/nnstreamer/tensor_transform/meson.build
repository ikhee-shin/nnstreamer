tensor_transform_sources = [
  'tensor_transform.c'
]

if orcc_support_is_available
  # tensor_transform does not need to generate -dist files.
  orcsrc = 'transform-orc'

  orc_h = custom_target(orcsrc + '.h',
    input: orcsrc + '.orc',
    output: orcsrc + '.h',
    command: orcc_support_orcc_args + ['--header', '-o', '@OUTPUT@', '@INPUT@'])
  orc_c = custom_target(orcsrc + '.c',
    input: orcsrc + '.orc',
    output: orcsrc + '.c',
    command: orcc_support_orcc_args + ['--implementation', '-o', '@OUTPUT@', '@INPUT@'])

  nnstreamer_sources += [orc_c, orc_h]
  nnstreamer_internal_deps += declare_dependency(sources: orc_h)
endif

foreach s : tensor_transform_sources
  nnstreamer_sources += join_paths(meson.current_source_dir(), s)
endforeach
