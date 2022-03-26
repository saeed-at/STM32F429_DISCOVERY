We want to read voltage from `lm35` and then convert it to `temprature`. fisrt we connect `5v` to `lm35` and then we read with `PA6` through adc and then we just need to divide the volatge in `mv` to 100 and the result is `temprature`, the whole code is as below :

```c
int value;
float voltage,temp;

/* USER CODE END 0 */

/**
  * @brief  The application entry point.
  * @retval int
  */
int main(void)
{
  /* USER CODE BEGIN 1 */

  /* USER CODE END 1 */
  

  /* MCU Configuration--------------------------------------------------------*/

  /* Reset of all peripherals, Initializes the Flash interface and the Systick. */
  HAL_Init();

  /* USER CODE BEGIN Init */

  /* USER CODE END Init */

  /* Configure the system clock */
  SystemClock_Config();

  /* USER CODE BEGIN SysInit */

  /* USER CODE END SysInit */

  /* Initialize all configured peripherals */
  MX_GPIO_Init();
  MX_ADC1_Init();
  /* USER CODE BEGIN 2 */

  /* USER CODE END 2 */

  /* Infinite loop */
  /* USER CODE BEGIN WHILE */
  while (1)
  {
    /* USER CODE END WHILE */

    /* USER CODE BEGIN 3 */
		HAL_ADC_Start(&hadc1);
		
		value = HAL_ADC_GetValue(&hadc1);
		voltage = (value * 3.3)/4096.0;
		
		temp = (voltage*100)-6;
		
		HAL_Delay(500);
  }
  /* USER CODE END 3 */
}
```
