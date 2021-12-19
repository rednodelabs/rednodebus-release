# Copyright (c) 2022 RedNodeLabs

set(REDNODEBUS_RELEASE_DIR "${CMAKE_CURRENT_LIST_DIR}/lib_rnb" CACHE PATH "RedNodeBus release root directory")

set(lib_rnb "lib_rnb_${BOARD}")

zephyr_library_import(${lib_rnb} "${REDNODEBUS_RELEASE_DIR}/${lib_rnb}.a")
