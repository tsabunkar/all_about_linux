# Lenovo -> dont have nerve sense (where we can toggle Laptop Turbo boost Fans) | so work around C code to toggle the fan

- Compile the extreme_cooling.c file to byte code
- \$ gcc extreme_cooling.c -o extreme_cooling
- To start Fan : \$ sudo ./extreme_cooling start
- To Stop Fan : \$ sudo ./extreme_cooling stop
