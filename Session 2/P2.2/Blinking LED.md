For this practice we setup a new project according to `Turn_LED_ON`, and then we write `main.c` code as bellow :
 - We use `GPIO_PIN_SET` to `turn on` LED. 
 - We ue  `GPIO_PIN_RESET` to `to turn off` LED.

 ```c
   while (1)
  {
    /* USER CODE END WHILE */

    /* USER CODE BEGIN 3 */
		
		/* P2.2 : Blinking LED*/
		HAL_GPIO_WritePin(GPIOG,GPIO_PIN_13,GPIO_PIN_SET);
		HAL_Delay(1000);
		HAL_GPIO_WritePin(GPIOG,GPIO_PIN_13,GPIO_PIN_RESET);
		HAL_Delay(1000);
		
  }
  ```
