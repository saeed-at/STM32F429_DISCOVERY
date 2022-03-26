We want to read the resistance of a `ldr` and then according to that `resistance` decide to do something. till now we can read the voltage with adc, so we use a `constant resistor`
and `ldr` in `series` and we `read` the voltage of `constant resistor`, then according to `voltage divider` formula, we can specify the resistance of `ldr`.

Also we know that `resistance of ldr` increase when the light intensity decreese and vice versa. The code is as below :

```c
int value;
float voltage,res;
/* USER CODE END PV */

/* Private function prototypes -----------------------------------------------*/
void SystemClock_Config(void);
static void MX_GPIO_Init(void);
static void MX_ADC1_Init(void);
/* USER CODE BEGIN PFP */

/* USER CODE END PFP */

/* Private user code ---------------------------------------------------------*/
/* USER CODE BEGIN 0 */

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
		voltage = (value*3.3)/4096.0;
		res = (32.44/voltage)-9.83;
    
		HAL_ADC_Stop(&hadc1);
			
		HAL_Delay(200);
  }
  /* USER CODE END 3 */
}
```
