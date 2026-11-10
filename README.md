# Reproducer: mlir-aie SequentialPlacer non-termination

`aie.mlir` + `attn_flash_step.o` in one directory, then:

```
aiecc aie.mlir --unified --peano=<peano install dir> --get-npu-insts
# never finishes: stuck at the placement step (killed after 600+ s)

aiecc aie.mlir --unified --peano=<peano install dir> --get-npu-insts --aiecc-options=--placer=sa_placer
# finishes; placement ~1.5 s
```

Details: https://github.com/Xilinx/mlir-aie/issues/<TBD>
