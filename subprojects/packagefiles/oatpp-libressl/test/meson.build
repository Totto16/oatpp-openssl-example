test_src_files = files(
    'oatpp-libressl/FullAsyncClientTest.cpp',
    'oatpp-libressl/FullAsyncClientTest.hpp',
    'oatpp-libressl/FullAsyncTest.cpp',
    'oatpp-libressl/FullAsyncTest.hpp',
    'oatpp-libressl/FullTest.cpp',
    'oatpp-libressl/FullTest.hpp',
    'oatpp-libressl/app/AsyncController.hpp',
    'oatpp-libressl/app/Client.hpp',
    'oatpp-libressl/app/Controller.hpp',
    'oatpp-libressl/app/DTOs.hpp',
    'oatpp-libressl/tests.cpp',
)

test_deps = deps
test_deps += dependency('oatpp-test', version: '1.3.0')
test_deps += oatpp_libressl_dep

test_inc_dirs = inc_dirs
test_inc_dirs += include_directories('.')

libressl_tests = executable(
    'oatpp_libressl_tests',
    test_src_files,
    include_directories: test_inc_dirs,
    dependencies: test_deps,
)

test('oatpp libressl module tests', libressl_tests)
