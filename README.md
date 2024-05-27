# PROJECTS
```
 #include "main.h"
 #include"stdbool.h"
 bool pushbutton;
 void SystemClock_Config(void);
 static void MX_GPIO_Init(void);
 int main(void)
 {
  HAL_Init();
  SystemClock_Config();
  MX_GPIO_Init();
  while (1)
  {
  pushbutton=HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_13);
        if(pushbutton==0){
        HAL_GPIO_WritePin(GPIOA,GPIO_PIN_5,GPIO_PIN_SET);
        HAL_Delay(2000);
        HAL_GPIO_WritePin(GPIOA,GPIO_PIN_5,GPIO_PIN_RESET);
        HAL_Delay(2000);
        }
        else{
        HAL_GPIO_WritePin(GPIOA,GPIO_PIN_5,GPIO_PIN_RESET);
        HAL_Delay(2000);
        }
  }
 }

```
```
#include "main.h"
#include "stdbool.h"
bool button;
void blink_Led();
void SystemClock_Config(void);
static void MX_GPIO_Init(void);
int main(void)
{
  HAL_Init();
  SystemClock_Config();
  MX_GPIO_Init();
  while (1)
  {
	 blink_Led();
  }
}
void blink_Led()
{
	button=HAL_GPIO_ReadPin(GPIOA,GPIO_PIN_0);
	if(button==0)
	{
		HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
		HAL_Delay(1000);
		HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
		HAL_Delay(1000);
	}
	else
	{
		HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
				HAL_Delay(1000);
	}
}
```
```
#include "main.h"
#include "lcd.h"
void SystemClock_Config(void);
static void MX_GPIO_Init(void);
int main(void)
{
  HAL_Init();
  SystemClock_Config();
  MX_GPIO_Init();
  Lcd_PortType ports[] = { GPIOA, GPIOA, GPIOA, GPIOA };
     Lcd_PinType pins[] = {GPIO_PIN_3, GPIO_PIN_2, GPIO_PIN_1, GPIO_PIN_0};
     Lcd_HandleTypeDef lcd;
     lcd = Lcd_create(ports, pins, GPIOB, GPIO_PIN_0, GPIOB, GPIO_PIN_1, LCD_4_BIT_MODE);
     Lcd_cursor(&lcd, 0,1);
     Lcd_string(&lcd, "Saravana kumar M");
 
  while (1)
  {
	  for ( int x = 1; x <= 200 ; x++ )
	  	   	 	  {
	  	   		  Lcd_cursor(&lcd, 1,7);
	  	   	 	  Lcd_int(&lcd, x);
	  	   	 	  HAL_Delay (1000);
	  	   	 	  }
  }
}
```
```
#include "main.h"
#include <stdbool.h>
#include "lcd.h"

bool col1,col2,col3,col4;
void key();
void SystemClock_Config(void);
static void MX_GPIO_Init(void);
int main(void)
{
  HAL_Init();
  SystemClock_Config();
  MX_GPIO_Init();
  while (1)
  {
	  key();
	  HAL_Delay(500);

  }
}
void key()
{
	Lcd_PortType ports[] = { GPIOA, GPIOA, GPIOA, GPIOA };
	Lcd_PinType pins[] = {GPIO_PIN_3, GPIO_PIN_2, GPIO_PIN_1, GPIO_PIN_0};
	Lcd_HandleTypeDef lcd;
	lcd = Lcd_create(ports, pins, GPIOB, GPIO_PIN_0, GPIOB, GPIO_PIN_1, LCD_4_BIT_MODE);

	HAL_GPIO_WritePin(GPIOC,GPIO_PIN_0,GPIO_PIN_RESET);
	HAL_GPIO_WritePin(GPIOC,GPIO_PIN_1,GPIO_PIN_SET);
	HAL_GPIO_WritePin(GPIOC,GPIO_PIN_2,GPIO_PIN_SET);
	HAL_GPIO_WritePin(GPIOC,GPIO_PIN_3,GPIO_PIN_SET);

	col1 =HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_4);
	col2 =HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_5);
	col3 =HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_6);
	col4 =HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_7);

 	if(!col1)
	{
		Lcd_cursor(&lcd,0,1);
		Lcd_string(&lcd, "key7\n");
		col1=1;
	}
	if(!col2)
		{
			Lcd_cursor(&lcd,0,1);
			Lcd_string(&lcd, "key8\n");
			col2=1;
		}
	if(!col3)
		{
			Lcd_cursor(&lcd,0,1);
			Lcd_string(&lcd, "key9\n");
			col3=1;
		}
	if(!col4)
		{
			Lcd_cursor(&lcd,0,1);
			Lcd_string(&lcd, "key/\n");
			col4=1;
		}

	HAL_GPIO_WritePin(GPIOC,GPIO_PIN_0,GPIO_PIN_SET);
		HAL_GPIO_WritePin(GPIOC,GPIO_PIN_1,GPIO_PIN_RESET);
		HAL_GPIO_WritePin(GPIOC,GPIO_PIN_2,GPIO_PIN_SET);
		HAL_GPIO_WritePin(GPIOC,GPIO_PIN_3,GPIO_PIN_SET);
		col1 =HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_4);
		col2 =HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_5);
		col3 =HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_6);
		col4 =HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_7);

		if(!col1)
		{
			Lcd_cursor(&lcd,0,1);
			Lcd_string(&lcd, "key4\n");
			col1=1;
		}
		if(!col2)
			{
				Lcd_cursor(&lcd,0,1);
				Lcd_string(&lcd, "key5\n");
				col2=1;
			}
		if(!col3)
			{
				Lcd_cursor(&lcd,0,1);
				Lcd_string(&lcd, "key6\n");
				col3=1;
			}
		if(!col4)
			{
				Lcd_cursor(&lcd,0,1);
				Lcd_string(&lcd, "key*\n");
				col4=1;
			}
 		HAL_GPIO_WritePin(GPIOC,GPIO_PIN_0,GPIO_PIN_SET);
				HAL_GPIO_WritePin(GPIOC,GPIO_PIN_1,GPIO_PIN_SET);
				HAL_GPIO_WritePin(GPIOC,GPIO_PIN_2,GPIO_PIN_RESET);
				HAL_GPIO_WritePin(GPIOC,GPIO_PIN_3,GPIO_PIN_SET);

				col1 =HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_4);
				col2 =HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_5);
				col3 =HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_6);
				col4 =HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_7);

				if(!col1)
				{
					Lcd_cursor(&lcd,0,1);
					Lcd_string(&lcd, "key1\n");
					col1=1;
				}
				if(!col2)
					{
						Lcd_cursor(&lcd,0,1);
						Lcd_string(&lcd, "key2\n");
						col2=1;
					}
				if(!col3)
					{
						Lcd_cursor(&lcd,0,1);
						Lcd_string(&lcd, "key3\n");
						col3=1;
					}
				if(!col4)
					{
						Lcd_cursor(&lcd,0,1);
						Lcd_string(&lcd, "key-\n");
						col4=1;
					}
 				HAL_GPIO_WritePin(GPIOC,GPIO_PIN_0,GPIO_PIN_SET);
						HAL_GPIO_WritePin(GPIOC,GPIO_PIN_1,GPIO_PIN_SET);
						HAL_GPIO_WritePin(GPIOC,GPIO_PIN_2,GPIO_PIN_SET);
						HAL_GPIO_WritePin(GPIOC,GPIO_PIN_3,GPIO_PIN_RESET);

						col1 =HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_4);
						col2 =HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_5);
						col3 =HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_6);
						col4 =HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_7);
						if(!col1)
						{
							Lcd_cursor(&lcd,0,1);
							Lcd_string(&lcd, "keyON/ac\n");
							col1=1;
						}
						if(!col2)
							{
								Lcd_cursor(&lcd,0,1);
								Lcd_string(&lcd, "key0\n");
								col2=1;
							}
						if(!col3)
							{
								Lcd_cursor(&lcd,0,1);
								Lcd_string(&lcd, "key=\n");
								col3=1;
							}
						if(!col4)
							{
								Lcd_cursor(&lcd,0,1);
								Lcd_string(&lcd, "key+\n");
								col4=1;
							}
						HAL_Delay(500);

}
```
```
#include "main.h"
TIM_HandleTypeDef htim2;
void SystemClock_Config(void);
static void MX_GPIO_Init(void);
static void MX_TIM2_Init(void);
int main(void)
{
  HAL_Init();
  SystemClock_Config();
  MX_GPIO_Init();
  MX_TIM2_Init();
  HAL_TIM_Base_Start(&htim2);
    HAL_TIM_PWM_Init(&htim2);
    HAL_TIM_PWM_Start(&htim2,TIM_CHANNEL_1);
  while (1)
  {
   
  }
 
}

void SystemClock_Config(void)
{
  RCC_OscInitTypeDef RCC_OscInitStruct = {0};
  RCC_ClkInitTypeDef RCC_ClkInitStruct = {0};
  __HAL_RCC_PWR_CLK_ENABLE();
  __HAL_PWR_VOLTAGESCALING_CONFIG(PWR_REGULATOR_VOLTAGE_SCALE2);

  RCC_OscInitStruct.OscillatorType = RCC_OSCILLATORTYPE_HSI;
  RCC_OscInitStruct.HSIState = RCC_HSI_ON;
  RCC_OscInitStruct.HSICalibrationValue = RCC_HSICALIBRATION_DEFAULT;
  RCC_OscInitStruct.PLL.PLLState = RCC_PLL_NONE;
  if (HAL_RCC_OscConfig(&RCC_OscInitStruct) != HAL_OK)
  {
    Error_Handler();
  }

  RCC_ClkInitStruct.ClockType = RCC_CLOCKTYPE_HCLK|RCC_CLOCKTYPE_SYSCLK
                              |RCC_CLOCKTYPE_PCLK1|RCC_CLOCKTYPE_PCLK2;
  RCC_ClkInitStruct.SYSCLKSource = RCC_SYSCLKSOURCE_HSI;
  RCC_ClkInitStruct.AHBCLKDivider = RCC_SYSCLK_DIV1;
  RCC_ClkInitStruct.APB1CLKDivider = RCC_HCLK_DIV1;
  RCC_ClkInitStruct.APB2CLKDivider = RCC_HCLK_DIV1;

  if (HAL_RCC_ClockConfig(&RCC_ClkInitStruct, FLASH_LATENCY_0) != HAL_OK)
  {
    Error_Handler();
  }
}
static void MX_TIM2_Init(void)
{
  TIM_ClockConfigTypeDef sClockSourceConfig = {0};
  TIM_MasterConfigTypeDef sMasterConfig = {0};
  TIM_OC_InitTypeDef sConfigOC = {0};
  htim2.Instance = TIM2;
  htim2.Init.Prescaler = 0;
  htim2.Init.CounterMode = TIM_COUNTERMODE_UP;
  htim2.Init.Period = 10000;
  htim2.Init.ClockDivision = TIM_CLOCKDIVISION_DIV1;
  htim2.Init.AutoReloadPreload = TIM_AUTORELOAD_PRELOAD_ENABLE;
  if (HAL_TIM_Base_Init(&htim2) != HAL_OK)
  {
    Error_Handler();
  }
  sClockSourceConfig.ClockSource = TIM_CLOCKSOURCE_INTERNAL;
  if (HAL_TIM_ConfigClockSource(&htim2, &sClockSourceConfig) != HAL_OK)
  {
    Error_Handler();
  }
  if (HAL_TIM_PWM_Init(&htim2) != HAL_OK)
  {
    Error_Handler();
  }
  sMasterConfig.MasterOutputTrigger = TIM_TRGO_RESET;
  sMasterConfig.MasterSlaveMode = TIM_MASTERSLAVEMODE_DISABLE;
  if (HAL_TIMEx_MasterConfigSynchronization(&htim2, &sMasterConfig) != HAL_OK)
  {
    Error_Handler();
  }
  sConfigOC.OCMode = TIM_OCMODE_PWM1;
  sConfigOC.Pulse = 2500;
  sConfigOC.OCPolarity = TIM_OCPOLARITY_HIGH;
  sConfigOC.OCFastMode = TIM_OCFAST_DISABLE;
  if (HAL_TIM_PWM_ConfigChannel(&htim2, &sConfigOC, TIM_CHANNEL_1) != HAL_OK)
  {
    Error_Handler();
  }

  HAL_TIM_MspPostInit(&htim2);

}

```
```
#include "main.h"
#include "stdbool.h"
#include "lcd.h"
bool row1,row2,row3,row4;
void key();

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

 int main(void)
{
    HAL_Init();
  SystemClock_Config();

   MX_GPIO_Init();

  while (1)
  {
    	  key();
	HAL_Delay(500);

    /* USER CODE BEGIN 3 */
  }
  /* USER CODE END 3 */
}
void key()
{
	Lcd_PortType ports[] = { GPIOA, GPIOA, GPIOA, GPIOA };
	Lcd_PinType pins[] = {GPIO_PIN_3, GPIO_PIN_2, GPIO_PIN_1, GPIO_PIN_0};
	Lcd_HandleTypeDef lcd;
	lcd = Lcd_create(ports, pins, GPIOB, GPIO_PIN_0, GPIOB, GPIO_PIN_1, LCD_4_BIT_MODE);

	HAL_GPIO_WritePin(GPIOC,GPIO_PIN_4,GPIO_PIN_SET);
	HAL_GPIO_WritePin(GPIOC,GPIO_PIN_5,GPIO_PIN_SET);
	HAL_GPIO_WritePin(GPIOC,GPIO_PIN_6,GPIO_PIN_SET);
	HAL_GPIO_WritePin(GPIOC,GPIO_PIN_7,GPIO_PIN_RESET);

	row1 =HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_0);
	row2 =HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_1);
	row3 =HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_2);
	row4 =HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_3);

 	if(!row1)
	{
		Lcd_cursor(&lcd,0,1);
		Lcd_string(&lcd, "key/\n");
		row1=1;
	}
	if(!row2)
		{
			Lcd_cursor(&lcd,0,1);
			Lcd_string(&lcd, "key*\n");
			row2=1;
		}
	if(!row3)
		{
			Lcd_cursor(&lcd,0,1);
			Lcd_string(&lcd, "key+\n");
			row3=1;
		}
	if(!row4)
		{
			Lcd_cursor(&lcd,0,1);
			Lcd_string(&lcd, "key - \n");
			row4=1;
		}
	HAL_Delay(500);

}
```

```
1.

#include "main.h"
int main(void)
{
  HAL_Init();
  SystemClock_Config();
  MX_GPIO_Init();
  for(int i=0;i<5;i++)
  {
HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
HAL_Delay(500);
HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
HAL_Delay(500);
}
while
{
}

  }
```
```
2.#include "main.h"


int main(void)
{
  HAL_Init();
  SystemClock_Config();
  MX_GPIO_Init();
  HAL_TIM_Base_Start(&htim2);
  HAL_TIM_PWM_Init(&htim2);
  HAL_TIM_PWM_Start(&htim2,TIM_CHANNEL_1);
while
{
}
}
```
```
3.
#include "main.h"
#include "stdbool.h"
bool pushbutton;
int main(void)
{
  HAL_Init();
  SystemClock_Config();
  MX_GPIO_Init();

while (1)
  {
    pushbutton=HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_13);
    if(pushbutton==0)
    {
    	HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
    	HAL_Delay(2000);
    	
    }
    else
    {
    	HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
    	HAL_Delay(2000);
    }
  }
```
```

4.
#include "main.h"
#include "stdbool.h"
bool pushbutton;
int main(void)
{
  HAL_Init();
  SystemClock_Config();
  MX_GPIO_Init();

while (1)
  {
    pushbutton=HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_13);
    if(pushbutton==0)
    {
    	HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
    	HAL_Delay(2000);
    	HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
    	HAL_Delay(2000);
    }
    else
    {
    	HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
    	HAL_Delay(2000);
    }
  }
```
```
5.simulation-stm32f401rb

#include "main.h"
#include "stdbool.h"
bool pushbutton;
int main(void)
{
  HAL_Init();
  SystemClock_Config();
  MX_GPIO_Init();

while (1)
  {
    pushbutton=HAL_GPIO_ReadPin(GPIOA,GPIO_PIN_0);
    if(pushbutton==0)
    {
    	HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
    	HAL_Delay(2000);
    	HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
    	HAL_Delay(2000);
    }
    else
    {
    	HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
    	HAL_Delay(2000);
    }
  }



```
