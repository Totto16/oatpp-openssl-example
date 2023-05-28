project(
    'example-ssl',
    'cpp',
    default_options: [
        'buildtype=release',
        'optimization=3',
        'strip=true',
        'cpp_std=c++11',
        'b_ndebug=if-release',
    ],
)

deps = []
deps += dependency('oatpp', version: '1.3.0', default_options: ['tests=false'])
deps += dependency(
    'oatpp-openssl',
    version: '1.3.0',
    default_options: ['tests=false'],
)

flags = [
    '-DCERT_PEM_PATH="' + (
        meson.project_source_root() / 'cert' / 'test_key.pem'
    ) + '"',
    '-DCERT_CRT_PATH="' + (
        meson.project_source_root() / 'cert' / 'test_cert.crt'
    ) + '"',
]



example_ssl_lib = library(
    'example-ssl',
    files(
        'src/AppComponent.hpp',
        'src/client/MyApiClient.hpp',
        'src/controller/MyController.cpp',
        'src/controller/MyController.hpp',
        'src/dto/MyDTOs.hpp',
    ),
    include_directories: include_directories('src'),
    dependencies: deps,
    cpp_args: flags,
    override_options: ['warning_level=3', 'werror=false'],
)

executable(
    'example_ssl',
    files('src/App.cpp'),
    include_directories: include_directories('src'),
    dependencies: deps,
    cpp_args: flags,
    link_with: example_ssl_lib,
    override_options: ['warning_level=3', 'werror=false'],
)


if get_option('tests')

    test_deps = deps
    test_deps += dependency('oatpp-test', version: '1.3.0')

    example_ssl_test = executable(
        'example_ssl_test',
        files('test/tests.cpp'),
        include_directories: include_directories('test', 'src'),
        link_with: example_ssl_lib,
        dependencies: test_deps,
        cpp_args: flags,
        override_options: ['warning_level=1', 'werror=false'],
    )
    test('Example SSL Tests', example_ssl_test)

endif

