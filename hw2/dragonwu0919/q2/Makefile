SRC_DIR := src
BUILD_DIR := build
TEST_DIR := test

MODULE_NAME := angle
SUFFIX := cpython-312-x86_64-linux-gnu.so

TARGET := $(BUILD_DIR)/$(MODULE_NAME).$(SUFFIX)
SOURCES := $(SRC_DIR)/${MODULE_NAME}.cpp

.PHONY: all test clean

all: $(TARGET)

test: all
	@echo "doing test"
	@mkdir -p $(TEST_DIR)
	@cd $(TEST_DIR) && export PYTHONPATH=../build/ && pytest

clean:
	rm -rf $(BUILD_DIR)

$(TARGET): $(SRC_DIR)/${MODULE_NAME}.cpp 
	@mkdir -p $(BUILD_DIR)
	c++ -O3 -Wall -shared -std=c++11 -fPIC $$(python3 -m pybind11 --includes) ${SRC_DIR}/${MODULE_NAME}.cpp -o ${BUILD_DIR}/${MODULE_NAME}.${SUFFIX}



