We want to `read` a pin as input and if the pin is `pressed`, then we want to `blink an LED`.

In order to read a pin we can use `User's key` which is available in discovery board or we can use a special pin to do that.

To find the `User's key` pin we should see the `schematic` of discovery board and find the circuit which is implemented for that use. picture above show the circuit in our board :
 
 <p align="center">
  <img 
    src="../../images/s3/user_pin_scheme.png"
  >
</p>

As we can see the `User pin` is normally connected to `GND` and it has the value `0`, but when we press the key, it will be connect to `VCC` through key's path and changes to `1`.

In oder to write our code we can use code as bellow, considering that the `HAL_Delay(100);` used for software debouncing and we use `ReadPin` method to read the pin's `state`.

```c
 /* USER CODE BEGIN 2 */
	 int pin_state;
  /* USER CODE END 2 */

  /* Infinite loop */
  /* USER CODE BEGIN WHILE */
  while (1)
  {
    /* USER CODE END WHILE */

    /* USER CODE BEGIN 3 */
		
		pin_state = HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_0);
			if (pin_state == GPIO_PIN_SET){
				//DELAY FOR DEBOUNCING
				HAL_Delay(100);
				if (pin_state == GPIO_PIN_SET){
					HAL_GPIO_WritePin(GPIOG,GPIO_PIN_13,GPIO_PIN_SET);
					HAL_Delay(100);
					HAL_GPIO_WritePin(GPIOG,GPIO_PIN_13,GPIO_PIN_RESET);
					HAL_Delay(100);
				}
			}
  }
  /* USER CODE END 3 */
}
```
