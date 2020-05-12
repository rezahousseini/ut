project('boost_ut', 'cpp', 
  version: '1.1.7',
  license: 'boost',
  default_options : ['warning_level=3', 'cpp_std=c++17']
)

boost_ut_dep = declare_dependency(
  include_directories: include_directories('include')
)

if not meson.is_subproject()
  install_headers('include/boost/ut.hpp', subdir: 'ut')
  
  pkgc = import('pkgconfig')
  pkgc.generate(name: 'boost_ut',
    version: meson.project_version(),
    description: 'C++17/20 μ(micro)/Unit Testing Framework'
  )
endif

if get_option('BOOST_UT_ENABLE_COVERAGE')
  cpp_args = ['--coverage', '-g', '-O0']
endif

if get_option('BOOST_UT_ENABLE_SANITIZERS')
  cpp_args = ['-O0', '-g', '-fno-omit-frame-pointer', '-fsanitize=address', 
              '-fsanitize=leak', '-fsanitize=undefined']
endif

if get_option('BOOST_UT_BUILD_BENCHMARKS')
  subdir('benchmark')
endif
if get_option('BOOST_UT_BUILD_EXAMPLES')
  subdir('example')
endif
if get_option('BOOST_UT_BUILD_TESTS')
  subdir('test')
endif
