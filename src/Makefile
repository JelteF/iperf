ifeq ($(RTE_SDK),)
$(error "Please define RTE_SDK environment variable")
endif

ifeq ($(RTE_ANS),)
$(error "Please define RTE_ANS environment variable")
endif

# Default target, can be overriden by command line or environment
RTE_TARGET ?= x86_64-native-linuxapp-gcc

include $(RTE_SDK)/mk/rte.vars.mk

ODP_PATH = $(RTE_ANS)

CFLAGS += -I$(ODP_PATH)/librte_ans/include
CFLAGS += -I$(ODP_PATH)/librte_anssock/include

LDLIBS += $(ODP_PATH)/librte_anssock/librte_anssock.a

# binary name
APP = iperf3

# all source are stored in SRCS-y
SRCS-y := cjson.c iperf_client_api.c iperf_locale.c iperf_server_api.c \
	iperf_udp.c main.c tcp_info.c timer.c units.c iperf_api.c iperf_error.c \
	iperf_tcp.c iperf_util.c net.c tcp_window_size.c


CFLAGS += -O3 -g --std=gnu99
#CFLAGS += $(WERROR_FLAGS)
CFLAGS += -I$(ODP_PATH)/include

include $(RTE_SDK)/mk/rte.extapp.mk
