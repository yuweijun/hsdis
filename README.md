# hsdis

Hotspot disassembler extracted from openjdk.

# Precondition on linux

To build hsdis on linux you need to make sure you have the standard build tools:

```bash
apt-get install build-essential
```

# Usage

```bash
git clone https://github.com/liuzhengyang/hsdis
cd hsdis
tar -zxvf binutils-2.26.tar.gz
make BINUTILS=binutils-2.26 ARCH=amd64
```
And then copy hsdis build file to the target folder in JDK.

### OSX

```bash
sudo cp build/macosx-amd64/hsdis-amd64.dylib $(/usr/libexec/java_home -v 1.8)/jre/lib/server/
```

### Linux

```bash
sudo cp build/linux-amd64/hsdis-amd64.so /usr/lib/jvm/java-8-oracle/jre/lib/amd64/server/
```

After that, you could add `-XX:+UnlockDiagnosticVMOptions -XX:+PrintAssembly` in the Java Run Param to see the program's assebmle code.

Examples:

```bash
java -server -Xcomp -XX:CompileThreshold=1 -XX:+UnlockDiagnosticVMOptions -XX:+DebugNonSafepoints -XX:+TraceClassLoading -XX:+PrintAssembly -XX:+LogCompilation -XX:LogFile=assembly.log com.example.lang.PrintAssemblyVolatile

```

There is already a prebuild hsdis-amd64 for OSX 64 in `build/macosx-amd64/hsdis-amd64.dylib.dylib` and for linux in `build/linux-amd64/hsdis-amd64.so` and was build for/with Unbuntu 18.04

