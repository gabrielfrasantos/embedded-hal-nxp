# embedded-hal-nxp

[![Linting & Formatting](https://github.com/gabrielfrasantos/embedded-hal-nxp/actions/workflows/linting-formatting.yml/badge.svg)](https://github.com/gabrielfrasantos/embedded-hal-nxp/actions/workflows/linting-formatting.yml) [![OpenSSF Scorecard](https://api.securityscorecards.dev/projects/github.com/gabrielfrasantos/embedded-hal-nxp/badge)](https://api.securityscorecards.dev/projects/github.com/gabrielfrasantos/embedded-hal-nxp)

**Description**: embedded-hal-nxp is a HAL (Hardware Abstraction Layer) implementation for a range of [NXP](https://nxp.com) ARM Cortex-based micro-controllers. embedded-hal-nxp implements the interfaces defined as part of [embedded-infra-lib].

## Dependencies

embedded-hal-nxp requires:
- [embedded-infra-lib].

## How to build the software

embedded-hal-nxp cannot be built by-itself, it must be built as part of a larger project. This paragraph describes how to add embedded-hal-nxp to a CMake build-system, using [embedded-infra-lib].

> CMakeLists.txt

```cmake
cmake_minimum_required(VERSION 3.21)

project(MyProject VERSION 1.0.0)

include(FetchContent)

FetchContent_Declare(
    emil
    GIT_REPOSITORY https://github.com/gabrielfrasantos/embedded-infra-lib.git
    GIT_TAG        embedded
)

FetchContent_Declare(
    halst
    GIT_REPOSITORY https://github.com/gabrielfrasantos/embedded-hal-nxp.git
    GIT_TAG        embedded
)

FetchContent_MakeAvailable(emil halst)

add_executable(myprogram Main.cpp)

target_link_libraries(myprogram PUBLIC
    infra.event
    hal_st.tiva
)

hal_ti_target_default_linker_scripts(myprogram)
hal_ti_target_default_init(myprogram)

```

## How to test the software

Due to the nature of embedded-hal-nxp: a HAL implementation, there are no included automated tests. Testing should be done in-context on the target hardware.

## Community

This project uses a [code-of-conduct](CODE_OF_CONDUCT.md) to define expected conduct in our community. Instances of abusive, harassing, or otherwise unacceptable behavior may be reported by contacting a project [maintainer](.github/CODEOWNERS)

## Changelog

See the [changelog](CHANGELOG.md) for more info on what's been changed.

## Contributing

Please refer to our [contributing](CONTRIBUTING.md) guide when you want to contribute to this project.

## License

embedded-hal-nxp is licensed under the [MIT](https://choosealicense.com/licenses/mit/) [license](LICENSE) except the files and/or directories named in the [notice](NOTICE) file.

[embedded-infra-lib]: https://github.com/gabrielfrasantos/embedded-infra-lib.git
