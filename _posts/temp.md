```C
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
  /* USER CODE BEGIN 2 */

  /* USER CODE END 2 */

  /* Infinite loop */
  /* USER CODE BEGIN WHILE */
	GPIO_PinState buttonState = GPIO_PIN_RESET;
  GPIO_PinState previousButtonState = GPIO_PIN_RESET;
  uint32_t previousTick = 0;
  while (1)
  {
    /* USER CODE END WHILE */
		HAL_GPIO_TogglePin(L1_GPIO_Port, L1_Pin);
		HAL_Delay(500);
		buttonState = HAL_GPIO_ReadPin(K1_GPIO_Port, K1_Pin);
    if (buttonState == GPIO_PIN_SET && previousButtonState == GPIO_PIN_RESET)
    {
        HAL_GPIO_WritePin(L1_GPIO_Port, L1_Pin, GPIO_PIN_SET);//按键按下
    }
    else if (buttonState == GPIO_PIN_RESET && previousButtonState == GPIO_PIN_SET)
    {

        HAL_GPIO_WritePin(L1_GPIO_Port, L1_Pin, GPIO_PIN_RESET);//按键释放
    }
    previousButtonState = buttonState;
    uint32_t currentTick = HAL_GetTick();
    uint32_t elapsedTime = currentTick - previousTick;
    previousTick = currentTick;

    if (buttonState == GPIO_PIN_RESET && elapsedTime >= 500)
    {
        HAL_GPIO_TogglePin(L1_GPIO_Port, L1_Pin);
        previousTick = currentTick;
    }
		
    /* USER CODE BEGIN 3 */
  }
  /* USER CODE END 3 */
}
```

HAL_GPIO_TogglePin(L1_GPIO_Port, L1_Pin);
				HAL_Delay(500);
				HAL_GPIO_TogglePin(L2_GPIO_Port, L2_Pin);
				HAL_Delay(500);
				HAL_GPIO_TogglePin(L3_GPIO_Port, L3_Pin);
				HAL_Delay(500);
				HAL_GPIO_TogglePin(L4_GPIO_Port, L4_Pin);
				HAL_Delay(500);
				HAL_GPIO_TogglePin(L5_GPIO_Port, L5_Pin);
				HAL_Delay(500);
				HAL_GPIO_TogglePin(L6_GPIO_Port, L6_Pin);
				HAL_Delay(500);
				HAL_GPIO_TogglePin(L7_GPIO_Port, L7_Pin);
				HAL_Delay(500);
				HAL_GPIO_TogglePin(L8_GPIO_Port, L8_Pin);
				HAL_Delay(500);