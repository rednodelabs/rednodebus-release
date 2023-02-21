# Copyright (c) 2022 RedNodeLabs

if(DEFINED CONFIG_REDNODEBUS)

  set(REDNODEBUS_RELEASE_DIR "${CMAKE_CURRENT_LIST_DIR}/lib_rnb" CACHE PATH "RedNodeBus release root directory")

  if(DEFINED CONFIG_REDNODEBUS_RANGING_DIAGNOSTIC_ENABLED)
    set(lib_rnb_rangingdiag_suffix "_rangingdiag")
  else()
    set(lib_rnb_rangingdiag_suffix "")
  endif()

  if(DEFINED CONFIG_REDNODERANGING)
    if(DEFINED CONFIG_REDNODERANGING_2W_ENABLED AND DEFINED CONFIG_REDNODERANGING_3W_ENABLED)
      set(lib_rnb_rnr_suffix "_rnr")
    elseif(DEFINED CONFIG_REDNODERANGING_2W_ENABLED)
      set(lib_rnb_rnr_suffix "_rnr2w")
    elseif(DEFINED CONFIG_REDNODERANGING_3W_ENABLED)
      set(lib_rnb_rnr_suffix "_rnr3w")
    endif()
  else()
    set(lib_rnb_rnr_suffix "")
  endif()

  if(DEFINED CONFIG_LOG)
    set(lib_rnb_debug_suffix "_debug")
  else()
    set(lib_rnb_debug_suffix "")
  endif()

  set(lib_rnb "lib_rnb_${CONFIG_SOC}${lib_rnb_rnr_suffix}${lib_rnb_rangingdiag_suffix}${lib_rnb_debug_suffix}")

  zephyr_library_import(${lib_rnb} "${REDNODEBUS_RELEASE_DIR}/${lib_rnb}.a")

endif()
