test_env = [
  'SOURCE_ROOT=' + meson.source_root(),
  'BUILD_DIR=' + meson.current_build_dir(),
  'TEST_DIR=' + meson.current_source_dir()
]

run_test = find_program('run-test')

tests = [
  'umpf-init',
  'umpf-merge',
  'umpf-series-build',
  'umpf-merge-build',
  'umpf-distribute',
  'umpf-series-tag',
  'umpf-build-tag',
  'umpf-build-tag-identical',
  'umpf-build-tag-upstreamstatus',
  'umpf-series-tag-continue',
  'umpf-series-tag-rerere',
  'umpf-series-tag-continue-flags',
  'umpf-series-tag-empty',
  'umpf-format-patch',
  'umpf-format-patch-bb',
  'umpf-show',
  'umpf-versions'
]
foreach test_name : tests
  test(test_name, run_test, args: test_name, env: test_env)
endforeach
