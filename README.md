def calculator_decorator(func):

    def wrapper(expression):
    
        try:
        
            # Проверяем, что выражение содержит только допустимые символы
            
            allowed_chars = "0123456789+-*/(). "
            
            if not all(char in allowed_chars for char in expression):
            
                raise ValueError("В выражении есть недопустимые символы.")

            # Выполняем расчет
            
            result = func(expression)
            
            return f"Результат: {result}"

        except ZeroDivisionError:
        
            return "Ошибка: деление на ноль."
            
        except SyntaxError:
        
            return "Ошибка: синтаксическая ошибка в выражении."
            
        except Exception as e:
        
            return f"Ошибка: {str(e)}"

    return wrapper


@calculator_decorator

def calculate(expression):

    return eval(expression)


# Пример использования

print(calculate("10 + 5 * 2"))

print(calculate("10 / 0"))

print(calculate("10 + (5 * 2"))

print(calculate("10 + 5 * abc"))
