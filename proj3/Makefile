# Makefile for Proj2/proj2

# Compiler and flags
CXX      = g++
CXXFLAGS = -std=c++17 -I./include/
LDFLAGS  = -lgtest -lgtest_main -pthread -L/usr/local/lib -I/usr/local/include \
           -L/opt/homebrew/opt/expat/lib -I/opt/homebrew/opt/expat/include -lexpat

# Directories
SRC_DIR  = src
TEST_DIR = testsrc
OBJ_DIR  = obj
BIN_DIR  = bin

###############################################################################
# Define source and test files for each executable target
###############################################################################

# teststrutils: link string utils and its tests
STRUTIL_SRC       = $(SRC_DIR)/StringUtils.cpp
STRUTIL_TEST      = $(TEST_DIR)/StringUtilsTest.cpp
STRUTIL_OBJS      = $(OBJ_DIR)/StringUtils.o $(OBJ_DIR)/StringUtilsTest.o
EXEC_STRUTIL      = $(BIN_DIR)/teststrutils

# teststrdatasource: link StringDataSource and its test
STRDSRC_SRC       = $(SRC_DIR)/StringDataSource.cpp
STRDSRC_TEST      = $(TEST_DIR)/StringDataSourceTest.cpp
STRDSRC_OBJS      = $(OBJ_DIR)/StringDataSource.o $(OBJ_DIR)/StringDataSourceTest.o
EXEC_STRDSRC      = $(BIN_DIR)/teststrdatasource

# teststrdatasink: link StringDataSink and its test
STRDSINK_SRC      = $(SRC_DIR)/StringDataSink.cpp
STRDSINK_TEST     = $(TEST_DIR)/StringDataSinkTest.cpp
STRDSINK_OBJS     = $(OBJ_DIR)/StringDataSink.o $(OBJ_DIR)/StringDataSinkTest.o
EXEC_STRDSINK     = $(BIN_DIR)/teststrdatasink

# testdsv: link DSV reader/writer and their tests
DSV_SRCS          = $(SRC_DIR)/DSVReader.cpp $(SRC_DIR)/DSVWriter.cpp
DSV_TESTS         = $(TEST_DIR)/DSVReaderTest.cpp $(TEST_DIR)/DSVWriterTest.cpp
DSV_OBJS          = $(OBJ_DIR)/DSVReader.o $(OBJ_DIR)/DSVWriter.o \
                    $(OBJ_DIR)/DSVReaderTest.o $(OBJ_DIR)/DSVWriterTest.o
EXEC_DSV          = $(BIN_DIR)/testdsv

# testxml: link XML reader/writer and its test
XML_SRCS          = $(SRC_DIR)/XMLReader.cpp $(SRC_DIR)/XMLWriter.cpp
XML_TEST          = $(TEST_DIR)/XMLTest.cpp
XML_OBJS          = $(OBJ_DIR)/XMLReader.o $(OBJ_DIR)/XMLWriter.o $(OBJ_DIR)/XMLTest.o
EXEC_XML          = $(BIN_DIR)/testxml

# testcsvbs: link CSVBusSystem and its test
CSVBS_SRC         = $(SRC_DIR)/CSVBusSystem.cpp
CSVBS_TEST        = $(TEST_DIR)/CSVBusSystemTest.cpp
CSVBS_OBJS        = $(OBJ_DIR)/CSVBusSystem.o $(OBJ_DIR)/CSVBusSystemTest.o
EXEC_CSVBS        = $(BIN_DIR)/testcsvbs

# testosm: link OpenStreetMap and its test
OSM_SRC           = $(SRC_DIR)/OpenStreetMap.cpp
OSM_TEST          = $(TEST_DIR)/OpenStreetMapTest.cpp
OSM_OBJS          = $(OBJ_DIR)/OpenStreetMap.o $(OBJ_DIR)/OpenStreetMapTest.o
EXEC_OSM          = $(BIN_DIR)/testosm

###############################################################################
# Default target: build all executables then run them
###############################################################################

all: dir $(EXEC_STRUTIL) $(EXEC_STRDSRC) $(EXEC_STRDSINK) $(EXEC_DSV) \
     $(EXEC_XML) $(EXEC_CSVBS) $(EXEC_OSM) run

###############################################################################
# Create obj and bin directories if they don't exist
###############################################################################

dir:
	@mkdir -p $(OBJ_DIR)
	@mkdir -p $(BIN_DIR)

###############################################################################
# Pattern rules to compile .cpp files into .o files
###############################################################################

# For source files in SRC_DIR
$(OBJ_DIR)/%.o: $(SRC_DIR)/%.cpp
	$(CXX) $(CXXFLAGS) -c $< -o $@

# For test files in TEST_DIR
$(OBJ_DIR)/%.o: $(TEST_DIR)/%.cpp
	$(CXX) $(CXXFLAGS) -c $< -o $@

###############################################################################
# Linking rules: link object files to create executables
###############################################################################

$(EXEC_STRUTIL): $(STRUTIL_OBJS)
	$(CXX) $(STRUTIL_OBJS) $(LDFLAGS) -o $(EXEC_STRUTIL)

$(EXEC_STRDSRC): $(STRDSRC_OBJS)
	$(CXX) $(STRDSRC_OBJS) $(LDFLAGS) -o $(EXEC_STRDSRC)

$(EXEC_STRDSINK): $(STRDSINK_OBJS)
	$(CXX) $(STRDSINK_OBJS) $(LDFLAGS) -o $(EXEC_STRDSINK)

$(EXEC_DSV): $(DSV_OBJS)
	$(CXX) $(DSV_OBJS) $(LDFLAGS) -o $(EXEC_DSV)

$(EXEC_XML): $(XML_OBJS)
	$(CXX) $(XML_OBJS) $(LDFLAGS) -o $(EXEC_XML)

$(EXEC_CSVBS): $(CSVBS_OBJS)
	$(CXX) $(CSVBS_OBJS) $(LDFLAGS) -o $(EXEC_CSVBS)

$(EXEC_OSM): $(OSM_OBJS)
	$(CXX) $(OSM_OBJS) $(LDFLAGS) -o $(EXEC_OSM)

###############################################################################
# Run all test executables
###############################################################################

run:
	@echo "Running teststrutils..."
	./$(EXEC_STRUTIL)
	@echo "Running teststrdatasource..."
	./$(EXEC_STRDSRC)
	@echo "Running teststrdatasink..."
	./$(EXEC_STRDSINK)
	@echo "Running testdsv..."
	./$(EXEC_DSV)
	@echo "Running testxml..."
	./$(EXEC_XML)
	@echo "Running testcsvbs..."
	./$(EXEC_CSVBS)
	@echo "Running testosm..."
	./$(EXEC_OSM)

###############################################################################
# Clean target: remove the obj and bin directories
###############################################################################

clean:
	rm -rf $(OBJ_DIR) $(BIN_DIR)
