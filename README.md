для роботи rpintf потрібно було додати в проект файл syscalls.c та оприділити слабко(__weak) зв'язану функцію int __io_putchar(int ch) {
	while (huart1.gState != HAL_UART_STATE_READY); // will overwrite the buffer otherwise, (needs a timeout and error handling)
	HAL_UART_Transmit_IT(&huart1, (uint8_t *)&ch, 1);
//	HAL_UART_Transmit(&huart1, (uint8_t *)&ch, 1, 0xFFFF);
	return ch;
	}
