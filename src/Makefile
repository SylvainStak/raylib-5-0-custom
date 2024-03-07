#******************************************************************************
#
#   raylib makefile
#
#   This file supports building raylib library for the following platforms:
#
#     > PLATFORM_DESKTOP (GLFW backend):
#         - Windows (Win32, Win64)
#         - Linux (X11)
#
#   Copyright (c) 2013-2023 Ramon Santamaria (@raysan5)
#
#   This software is provided "as-is", without any express or implied warranty. In no event
#   will the authors be held liable for any damages arising from the use of this software.
#
#   Permission is granted to anyone to use this software for any purpose, including commercial
#   applications, and to alter it and redistribute it freely, subject to the following restrictions:
#
#     1. The origin of this software must not be misrepresented; you must not claim that you
#     wrote the original software. If you use this software in a product, an acknowledgment
#     in the product documentation would be appreciated but is not required.
#
#     2. Altered source versions must be plainly marked as such, and must not be misrepresented
#     as being the original software.
#
#     3. This notice may not be removed or altered from any source distribution.
#
#**************************************************************************************************

.PHONY: all clean

CC = gcc
CFLAGS = -std=c99 -O1 -Wall -D_GNU_SOURCE -DPLATFORM_DESKTOP -DGRAPHICS_API_OPENGL_33 -Wno-missing-braces -Werror=pointer-arith -fno-strict-aliasing -Werror=implicit-function-declaration
IFLAGS = -I. -Iexternal/glfw/include -Iexternal/glfw/deps/mingw
OBJS = rcore.o rshapes.o rtextures.o rtext.o utils.o rglfw.o rmodels.o raudio.o

all: raylib

clean:
	rm -fv *.o ../libraylib.a

raylib: $(OBJS)
	ar rcs ../libraylib.a $(OBJS)
	@echo "raylib static library generated libraylib.a!"

rcore.o : rcore.c raylib.h rlgl.h utils.h raymath.h rcamera.h rgestures.h
	$(CC) -c $< $(CFLAGS) $(IFLAGS)

rglfw.o : rglfw.c
	$(CC) -c $< $(CFLAGS) $(IFLAGS)

rshapes.o : rshapes.c raylib.h rlgl.h
	$(CC) -c $< $(CFLAGS) $(IFLAGS)

rtextures.o : rtextures.c raylib.h rlgl.h utils.h
	$(CC) -c $< $(CFLAGS) $(IFLAGS)

rtext.o : rtext.c raylib.h utils.h
	$(CC) -c $< $(CFLAGS) $(IFLAGS)

utils.o : utils.c utils.h
	$(CC) -c $< $(CFLAGS) $(IFLAGS)

rmodels.o : rmodels.c raylib.h rlgl.h raymath.h
	$(CC) -c $< $(CFLAGS) $(IFLAGS)

raudio.o : raudio.c raylib.h
	$(CC) -c $< $(CFLAGS) $(IFLAGS)
