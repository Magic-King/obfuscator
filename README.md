# O-LLVM

based on LLVM 9.0.0 and clang 9.0.0

flag : -mllvm -fla  ,there is a bug

log is here:

```sh
Stack dump:
0.	Program arguments: /home/sc/m/build/bin/clang-9 -cc1 -triple x86_64-unknown-linux-gnu -emit-obj -mrelax-all -disable-free -disable-llvm-verifier -discard-value-names -main-file-name test.c -mrelocation-model static -mthread-model posix -mdisable-fp-elim -fmath-errno -masm-verbose -mconstructor-aliases -munwind-tables -fuse-init-array -target-cpu x86-64 -dwarf-column-info -debugger-tuning=gdb -resource-dir /home/sc/m/build/lib/clang/9.0.0 -internal-isystem /usr/local/include -internal-isystem /home/sc/m/build/lib/clang/9.0.0/include -internal-externc-isystem /usr/include/x86_64-linux-gnu -internal-externc-isystem /include -internal-externc-isystem /usr/include -fdebug-compilation-dir /home/sc/m/test -ferror-limit 19 -fmessage-length 0 -fobjc-runtime=gcc -fdiagnostics-show-option -fcolor-diagnostics -mllvm -fla -faddrsig -o /tmp/test-00558f.o -x c test.c 
1.	<eof> parser at end of file
2.	Per-module optimization passes
3.	Running pass 'Function Pass Manager' on module 'test.c'.
4.	Running pass 'Call graph flattening' on function '@main'
 #0 0x0000555b7b5deb1a llvm::sys::PrintStackTrace(llvm::raw_ostream&) (/home/sc/m/build/bin/clang-9+0x274fb1a)
 #1 0x0000555b7b5dc8e4 llvm::sys::RunSignalHandlers() (/home/sc/m/build/bin/clang-9+0x274d8e4)
 #2 0x0000555b7b5dca22 SignalHandler(int) (/home/sc/m/build/bin/clang-9+0x274da22)
 #3 0x00007f8c44a86890 __restore_rt (/lib/x86_64-linux-gnu/libpthread.so.0+0x12890)
 #4 0x0000555b7b6b5bd8 (anonymous namespace)::LowerSwitch::runOnFunction(llvm::Function&) (/home/sc/m/build/bin/clang-9+0x2826bd8)
 #5 0x0000555b7c376d57 (anonymous namespace)::Flattening::runOnFunction(llvm::Function&) (/home/sc/m/build/bin/clang-9+0x34e7d57)
 #6 0x0000555b7afd3d58 llvm::FPPassManager::runOnFunction(llvm::Function&) (/home/sc/m/build/bin/clang-9+0x2144d58)
 #7 0x0000555b7afd3e13 llvm::FPPassManager::runOnModule(llvm::Module&) (/home/sc/m/build/bin/clang-9+0x2144e13)
 #8 0x0000555b7afd30b1 llvm::legacy::PassManagerImpl::run(llvm::Module&) (/home/sc/m/build/bin/clang-9+0x21440b1)
 #9 0x0000555b7b8024e1 (anonymous namespace)::EmitAssemblyHelper::EmitAssembly(clang::BackendAction, std::unique_ptr<llvm::raw_pwrite_stream, std::default_delete<llvm::raw_pwrite_stream> >) (/home/sc/m/build/bin/clang-9+0x29734e1)
#10 0x0000555b7b80419b clang::EmitBackendOutput(clang::DiagnosticsEngine&, clang::HeaderSearchOptions const&, clang::CodeGenOptions const&, clang::TargetOptions const&, clang::LangOptions const&, llvm::DataLayout const&, llvm::Module*, clang::BackendAction, std::unique_ptr<llvm::raw_pwrite_stream, std::default_delete<llvm::raw_pwrite_stream> >) (/home/sc/m/build/bin/clang-9+0x297519b)
#11 0x0000555b7c20b5d1 clang::BackendConsumer::HandleTranslationUnit(clang::ASTContext&) (/home/sc/m/build/bin/clang-9+0x337c5d1)
#12 0x0000555b7cc87409 clang::ParseAST(clang::Sema&, bool, bool) (/home/sc/m/build/bin/clang-9+0x3df8409)
#13 0x0000555b7c209027 clang::CodeGenAction::ExecuteAction() (/home/sc/m/build/bin/clang-9+0x337a027)
#14 0x0000555b7bcaef69 clang::FrontendAction::Execute() (/home/sc/m/build/bin/clang-9+0x2e1ff69)
#15 0x0000555b7bc72405 clang::CompilerInstance::ExecuteAction(clang::FrontendAction&) (/home/sc/m/build/bin/clang-9+0x2de3405)
#16 0x0000555b7bd71c53 clang::ExecuteCompilerInvocation(clang::CompilerInstance*) (/home/sc/m/build/bin/clang-9+0x2ee2c53)
#17 0x0000555b79b179c3 cc1_main(llvm::ArrayRef<char const*>, char const*, void*) (/home/sc/m/build/bin/clang-9+0xc889c3)
#18 0x0000555b79a81419 main (/home/sc/m/build/bin/clang-9+0xbf2419)
#19 0x00007f8c4371ab97 __libc_start_main /build/glibc-OTsEL5/glibc-2.27/csu/../csu/libc-start.c:344:0
#20 0x0000555b79b1508a _start (/home/sc/m/build/bin/clang-9+0xc8608a)
clang-9: error: unable to execute command: Segmentation fault (core dumped)
clang-9: error: clang frontend command failed due to signal (use -v to see invocation)
Obfuscator-LLVM clang version 9.0.0 (tags/RELEASE_900/final) (based on Obfuscator-LLVM 9.0.0)
Target: x86_64-unknown-linux-gnu
Thread model: posix
InstalledDir: /home/sc/m/test/../build/bin
clang-9: note: diagnostic msg: PLEASE submit a bug report to https://o-llvm.org/ and include the crash backtrace, preprocessed source, and associated run script.
clang-9: note: diagnostic msg: 
********************

PLEASE ATTACH THE FOLLOWING FILES TO THE BUG REPORT:
Preprocessed source(s) and associated run script(s) are located at:
clang-9: note: diagnostic msg: /tmp/test-6bef2e.c
clang-9: note: diagnostic msg: /tmp/test-6bef2e.sh
clang-9: note: diagnostic msg: 

********************

```











