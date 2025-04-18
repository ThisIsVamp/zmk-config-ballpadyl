# Copyright (c) 2021, Basalte bv
#
# SPDX-License-Identifier: Apache-2.0

if(CONFIG_NANOPB)

  set(NANOPB_DIR ${ZEPHYR_CURRENT_MODULE_DIR})

  zephyr_library()
  zephyr_library_sources(
    ${NANOPB_DIR}/pb_common.c
    ${NANOPB_DIR}/pb_encode.c
    ${NANOPB_DIR}/pb_decode.c
  )

  zephyr_include_directories(${NANOPB_DIR})

  zephyr_compile_definitions(
    PB_MAX_REQUIRED_FIELDS=${CONFIG_NANOPB_MAX_REQUIRED_FIELDS})

  zephyr_compile_definitions_ifdef(
    CONFIG_NANOPB_ENABLE_MALLOC
    PB_ENABLE_MALLOC
  )

  zephyr_compile_definitions_ifdef(
    CONFIG_NANOPB_NO_ERRMSG
    PB_NO_ERRMSG
  )

  zephyr_compile_definitions_ifdef(
    CONFIG_NANOPB_BUFFER_ONLY
    PB_BUFFER_ONLY
  )

  zephyr_compile_definitions_ifdef(
    CONFIG_NANOPB_WITHOUT_64BIT
    PB_WITHOUT_64BIT
  )

  zephyr_compile_definitions_ifdef(
    CONFIG_NANOPB_NO_ENCODE_SIZE_CHECK
    PB_NO_ENCODE_SIZE_CHECK
  )

  zephyr_compile_definitions_ifdef(
    CONFIG_NANOPB_ENCODE_ARRAYS_UNPACKED
    PB_ENCODE_ARRAYS_UNPACKED
  )

  zephyr_compile_definitions_ifdef(
    CONFIG_NANOPB_VALIDATE_UTF8
    PB_VALIDATE_UTF8
  )

endif()
