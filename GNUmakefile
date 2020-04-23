CC = x86_64-w64-mingw32-gcc
RC = x86_64-w64-mingw32-windres

.PHONY: all
all: Launcher.exe $(patsubst %,%.exe,$(notdir $(shell ls -d res/*)))

.PHONY: clean
clean:
	$(RM) *.exe *.o res/*/*.o

Launcher.exe: main.o
	$(CC) -o $@ $< -lshlwapi

%.exe: main.o res/%/res.o
	$(CC) -o $@ $^ -lshlwapi

main.o: main.c parenttl.h scanf_s.h version.h wsld.h
	$(CC) $(CFLAGS) -std=c99 --static -include scanf_s.h -c $<

res/%/res.o: res/%/res.rc res/%/icon.ico
	$(RC) -o $@ $<
