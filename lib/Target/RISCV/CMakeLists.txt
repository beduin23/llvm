set(LLVM_TARGET_DEFINITIONS RISCV.td)

tablegen(LLVM RISCVGenRegisterInfo.inc -gen-register-info)
tablegen(LLVM RISCVGenInstrInfo.inc -gen-instr-info)
tablegen(LLVM RISCVGenMCCodeEmitter.inc -gen-emitter)
tablegen(LLVM RISCVGenAsmMatcher.inc -gen-asm-matcher)

add_public_tablegen_target(RISCVCommonTableGen)

add_llvm_target(RISCVCodeGen
  RISCVTargetMachine.cpp
  )

add_subdirectory(AsmParser)
add_subdirectory(TargetInfo)
add_subdirectory(MCTargetDesc)
