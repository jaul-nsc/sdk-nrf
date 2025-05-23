#
# Copyright (c) 2024-2025 Nordic Semiconductor
#
# SPDX-License-Identifier: LicenseRef-Nordic-5-Clause
#

# The sample uses the sysbuild/configuration/<board> scheme for the sysbuild configuration files.
set(SB_APPLICATION_CONFIG_DIR
    "${CMAKE_CURRENT_LIST_DIR}/configuration/\${NORMALIZED_BOARD_TARGET}")

find_package(Sysbuild REQUIRED HINTS $ENV{ZEPHYR_BASE})

project(sysbuild LANGUAGES)

if(SB_CONFIG_MCUBOOT_SIGNATURE_USING_KMU)
  message(WARNING "
          ------------------------------------------------------------------------------
          --- WARNING: MCUboot uses KMU stored keys for signature verification. Make ---
          --- sure to use `west ncs-provision` to manually provision the bootloader. ---
          --- Application would fail to boot if MCUboot is not provisioned. For more ---
          --- details, see the `Building and running` section from the Fast Pair     ---
          --- Locator Tag Readme documentation.                                      ---
          ------------------------------------------------------------------------------
          ")
endif()
