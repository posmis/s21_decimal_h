TARGET=s21_decimal.a

CC=gcc -Wall -Werror -Wextra -std=c11
CPP_FLAGS=--enable=all --suppress=missingIncludeSystem
SYSTEM:=$(shell uname -s)

ifeq ($(SYSTEM), Linux)
	TEST_FLAGS=-lcheck -lm -lsubunit
else ifeq ($(SYSTEM), Apple)
	TEST_FLAGS=-lcheck
endif

MAIN_PATH=./main/
TEST_PATH=./tests/

all: $(TARGET)

$(TARGET):
	$(CC) -c $(MAIN_PATH)*.c
	ar rc $(TARGET) *.o
	rm *.o

clang_i:
	clang-format -i -style=Google $(MAIN_PATH)*.c $(TEST_PATH)*.c *.h

clang_n:
	clang-format -n -style=Google $(MAIN_PATH)*.c $(TEST_PATH)*.c *.h

cpp:
	cppcheck $(CPP_FLAGS) *.h $(MAIN_PATH)*.c

clean:
	rm -rf $(TARGET) *.o *.out *.gcno *.gcda *.info ./coverage.out *.gcov ./coverage_html.info ./coverage_html