# Penn TotalRecall -  An easy-to-use tool for quickly annotating audio files #

[![Build Status](http://ci.yuvimasory.com/job/Penn-TotalRecall/badge/icon)](http://ci.yuvimasory.com/job/Penn-TotalRecall/)


## Overview ##
TotalRecall is designed for precise scoring and timing of participant responses during verbal tasks, especially Free Recall.
However, it can be used for many kinds of audio annotation. TotalRecall displays an audio recording as a self-scrolling waveform that automatically keeps up with audio playback.

TotalRecall is used on a daily basis by many in the Computational Memory Lab. Support and maintenance will continue indefinitely with new features being added as needed.

## Homepage ##
`<http://memory.psych.upenn.edu/TotalRecall>`

## Compile ##

    

Install JDK 

    sudo apt-get install default-jdk
 


Install Apache Ant

    sudo apt-get install ant
 


Install development headers for foreign architecture

    sudo apt-get install libc6-dev-i386  #if on 64-bit machine
    sudo apt-get install libc6-dev-amd64 #if on 32-bit machine
 

Issue: does not install on ubuntu 20.04 (I have libc6-dev installed)

Compile/install the native libraries

    ant install_native
 

Issue: 

    compile_native:
     [echo] CALLING NATIVE make OR vcbuild TO COMPILE AUDIO SYSTEM
     [exec] mkdir -p ../../../../tmp
     [exec] gcc -shared -Wall -O3 -std=c99 -pedantic -pthread -fPIC -m32 -o ../../../../tmp/libpenntotalrecall.so ../../src/libpenntotalrecall.c -lfmodex-4.32.03 -L../../lib/linux32/
     [exec] In file included from ../../src/libpenntotalrecall.c:30:
     [exec] ../../src/../inc/wincompat.h:11:10: fatal error: sys/time.h: No such file or directory
     [exec]    11 | #include <sys/time.h>
     [exec]       |          ^~~~~~~~~~~~
     [exec] compilation terminated.
     [exec] make: *** [Makefile:71: Darwin_all] Error 1



Compile the Java portion into a jar

    ant package_jar
 


Run the program

java -jar dist/PennTotalRecall.jar
 


## Bugs: ##

* crashes when trying to play file:

"Cannot load audio system."

    java.lang.UnsatisfiedLinkError: Unable to load library 'penntotalrecall64': libpenntotalrecall64.so: cannot open shared object file: No such file or directory

