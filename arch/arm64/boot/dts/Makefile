# SPDX-License-Identifier: GPL-2.0
dts-dirs += actions
dts-dirs += al
dts-dirs += allwinner
dts-dirs += altera
dts-dirs += amd
dts-dirs += amlogic
dts-dirs += apm
dts-dirs += arm
dts-dirs += broadcom
dts-dirs += cavium
dts-dirs += exynos
dts-dirs += freescale
dts-dirs += hisilicon
dts-dirs += marvell
dts-dirs += mediatek
dts-dirs += nvidia
dts-dirs += qcom
dts-dirs += realtek
dts-dirs += renesas
dts-dirs += rockchip
dts-dirs += samsung
dts-dirs += socionext
dts-dirs += sprd
dts-dirs += xilinx
dts-dirs += lg
dts-dirs += zte

subdir-y	:= $(dts-dirs)

dtstree		:= $(srctree)/$(src)

dtb-$(CONFIG_OF_ALL_DTBS) := $(patsubst $(dtstree)/%.dts,%.dtb, $(foreach d,$(dts-dirs), $(wildcard $(dtstree)/$(d)/*.dts)))

dtb-y += exynos/exynos9610.dtb

dtbo-y += samsung/exynos9611-m21_swa_open_00.dtbo
dtbo-y += samsung/exynos9611-m21_swa_open_06.dtbo
dtbo-y += samsung/exynos9611-m31_eur_open_00.dtbo
dtbo-y += samsung/exynos9611-m31_eur_open_01.dtbo
dtbo-y += samsung/exynos9611-f41_swa_open_00.dtbo

always		:= $(dtb-y) $(dtbo-y)

targets += dtbs

DTB_NAMES := $(subst $\",,$(CONFIG_BUILD_ARM64_APPENDED_DTB_IMAGE_NAMES))
ifneq ($(DTB_NAMES),)
DTB_LIST := $(addsuffix .dtb,$(DTB_NAMES))
else
DTB_LIST := $(dtb-y) $(dtbo-y)
endif
targets += $(DTB_LIST)

dtbs: $(addprefix $(obj)/, $(DTB_LIST))

clean-files := dts/*.dtb *.dtb*
