# Interfacing a 4x4 matrix keypad

## Aim: 
To simulate the interface of a 4x4 matrix keypad to ARM controller and display the output on 16X2 LCD for arithmetic operation only.

## Components required: 
STM32 CUBE IDE, Proteus 8 simulator .

## Keypad layout

![image](https://github.com/user-attachments/assets/c24e7e27-7b0f-4904-becd-307fbf7dcba8)


## CIRCUIT DIAGRAM 
![image](https://github.com/user-attachments/assets/596c321a-9baf-477b-beec-5244738afbf8)

## Program
```
#include "main.h"
#include <stdbool.h>
#include "lcd.h"

bool col1,col2,col3,col4;
void key();

/* Private includes ----------------------------------------------------------*/
/* USER CODE BEGIN Includes */

/* USER CODE END Includes */

/* Private typedef -----------------------------------------------------------*/
/* USER CODE BEGIN PTD */

/* USER CODE END PTD */

/* Private define ------------------------------------------------------------*/
/* USER CODE BEGIN PD */
/* USER CODE END PD */

/* Private macro -------------------------------------------------------------*/
/* USER CODE BEGIN PM */

/* USER CODE END PM */

/* Private variables ---------------------------------------------------------*/

/* USER CODE BEGIN PV */

/* USER CODE END PV */

/* Private function prototypes -----------------------------------------------*/
void SystemClock_Config(void);
static void MX_GPIO_Init(void);
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
  /* USER CODE BEGIN 2 */

  /* USER CODE END 2 */

  /* Infinite loop */
  /* USER CODE BEGIN WHILE */
  while (1)
  {
    /* USER CODE END WHILE */
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
## Output screen shots of proteus
![image](https://github.com/user-attachments/assets/d694bfa1-a722-4ec9-bd43-8893c3e5518c)

## Result :
Thus,Interfaced a 4x4 matrix keypad with ARM microcontroller and displayed the output on 16X2 LCD in simulation successfully.
