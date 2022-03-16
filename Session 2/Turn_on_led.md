Before installing everything install `JAVARuntime` v1.8 or above. After that you need to install `STMCUBEMX`, `KEIL` and `STLINK`.

There are `3` steps to turn on LED(which is connected to `PG13` in `stm32f429zi` discovery board):
 - 1 . Run `STM32CubeMX` and choose MCU selector, and search the board that you are using.( I'm using STM32F429)
 - 2 . On the `Clock Configuration` tab, set the the `HCLK`, this can be set up to `180 MHz` in stm32f429.
 - 3 . Then click on `Generate code` button and then in the new window(which will popup after clicking) set the path and name of the project and finally
 set the `Toolchain / IDE` to `MKD-ARM V5`.
 
 After these steps a window will popup and you can choose `Open project` to move your setup configurations to  `Keil`.
