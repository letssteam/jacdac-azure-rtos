# Copyright (c) Microsoft Corporation.
# Licensed under the MIT License.

set(SOURCES
    autogen/sl_board_default_init.c
    autogen/sl_device_init_clocks.c
    autogen/sl_event_handler.c
    autogen/sl_iostream_handles.c
    autogen/sl_iostream_init_usart_instances.c
    autogen/sl_simple_led_instances.c
    autogen/sl_i2cspm_init.c
    hardware/board/src/sl_board_control_gpio.c
    hardware/board/src/sl_board_init.c
    hardware/driver/mx25_flash_shutdown/src/sl_mx25_flash_shutdown.c
    hardware/driver/si70xx/src/sl_si70xx.c
    platform/driver/leddrv/src/sl_led.c
    platform/driver/leddrv/src/sl_simple_led.c
    platform/driver/i2cspm/src/sl_i2cspm.c
    platform/emdrv/dmadrv/src/dmadrv.c
    platform/emdrv/dmadrv/src/dmactrl.c
    platform/emdrv/spidrv/src/spidrv.c
    platform/emlib/src/em_acmp.c
    platform/emlib/src/em_adc.c
    platform/emlib/src/em_aes.c
    platform/emlib/src/em_assert.c
    platform/emlib/src/em_burtc.c
    platform/emlib/src/em_can.c
    platform/emlib/src/em_cmu.c
    platform/emlib/src/em_core.c
    platform/emlib/src/em_cryotimer.c
    platform/emlib/src/em_crypto.c
    platform/emlib/src/em_csen.c
    platform/emlib/src/em_dac.c
    platform/emlib/src/em_dbg.c
    platform/emlib/src/em_dma.c
    platform/emlib/src/em_ebi.c
    platform/emlib/src/em_emu.c
    platform/emlib/src/em_eusart.c
    platform/emlib/src/em_gpcrc.c
    platform/emlib/src/em_gpio.c
    platform/emlib/src/em_i2c.c
    platform/emlib/src/em_iadc.c
    platform/emlib/src/em_idac.c
    platform/emlib/src/em_lcd.c
    platform/emlib/src/em_ldma.c
    platform/emlib/src/em_lesense.c
    platform/emlib/src/em_letimer.c
    platform/emlib/src/em_leuart.c
    platform/emlib/src/em_msc.c
    platform/emlib/src/em_opamp.c
    platform/emlib/src/em_pcnt.c
    platform/emlib/src/em_pdm.c
    platform/emlib/src/em_prs.c
    platform/emlib/src/em_qspi.c
    platform/emlib/src/em_rmu.c
    platform/emlib/src/em_rtc.c
    platform/emlib/src/em_rtcc.c
    platform/emlib/src/em_se.c
    platform/emlib/src/em_system.c
    platform/emlib/src/em_timer.c
    platform/emlib/src/em_usart.c
    platform/emlib/src/em_vcmp.c
    platform/emlib/src/em_vdac.c
    platform/emlib/src/em_wdog.c
    platform/radio/wifi/wfx_fmac_driver/bus/sl_wfx_bus.c
    platform/radio/wifi/wfx_fmac_driver/sl_wfx.c
    platform/service/device_init/src/sl_device_init_dcdc_s1.c
    platform/service/device_init/src/sl_device_init_emu_s1.c
    platform/service/device_init/src/sl_device_init_hfxo_s1.c
    platform/service/device_init/src/sl_device_init_lfxo_s1.c
    platform/service/iostream/src/sl_iostream_uart.c
    platform/service/iostream/src/sl_iostream_usart.c
    platform/service/iostream/src/sl_iostream.c
    platform/service/system/src/sl_system_init.c
    platform/service/system/src/sl_system_kernel.c
    platform/service/udelay/src/sl_udelay.c
    platform/service/udelay/src/sl_udelay_armv6m_gcc.S
    platform/service/sleeptimer/src/sl_sleeptimer.c
    platform/service/sleeptimer/src/sl_sleeptimer_hal_rtcc.c
)

set(TARGET gecko_sdk_3.0.0_efr32mg12)

add_library(${TARGET} OBJECT
    ${SOURCES}
)

target_link_libraries(${TARGET}
    azrtos::threadx
)

target_compile_definitions(${TARGET}
    PUBLIC
        DEBUG_EFM
        EFR32MG12P432F1024GL125
        SL_COMPONENT_CATALOG_PRESENT
)

target_include_directories(${TARGET} 
    PUBLIC
         autogen
         config/emdrv
         config/hardware/board/brd4161a_brd4001a
         config/service/device_init
         config/service/sleeptimer
         hardware/board/inc
         hardware/driver/mx25_flash_shutdown/inc
         hardware/driver/si70xx/inc
         platform/CMSIS/Include
         platform/common/inc
         platform/common/toolchain/inc
         platform/Device/SiliconLabs/EFR32MG12P/Include
         platform/driver/leddrv/inc
         platform/emdrv/common/inc
         platform/emdrv/dmadrv/inc
         platform/emdrv/spidrv/inc
         platform/driver/i2cspm/inc
         platform/emlib/inc
         platform/radio/wifi/wfx_fmac_driver
         platform/radio/wifi/wfx_fmac_driver/firmware
         platform/service/device_init/inc
         platform/service/iostream/inc
         platform/service/system/inc
         platform/service/udelay/inc
         platform/service/sleeptimer/inc
)
