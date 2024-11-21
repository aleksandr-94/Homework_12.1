# Homework_12.1



import re

def delete_html_tags(html_file, result_file="cleaned.txt"):
    """
    Удаляет HTML-теги из файла и сохраняет результат в новый файл.
    
    :param html_file: Имя исходного файла с HTML-кодом.
    :param result_file: Имя файла, куда будет записан очищенный текст.
    """
    try:
        # Чтение исходного файла
        with open(html_file, 'r', encoding='utf-8') as file:
            html_content = file.read()
        
        # Удаление HTML-тегов
        cleaned_content = re.sub(r'<.*?>', '', html_content)
        
        # Удаление пустых строк
        cleaned_content = "\n".join([line for line in cleaned_content.splitlines() if line.strip()])
        
        # Запись результата в новый файл
        with open(result_file, 'w', encoding='utf-8') as file:
            file.write(cleaned_content)
        
        print(f"Файл успешно очищен и сохранен в {result_file}")
    except FileNotFoundError:
        print(f"Файл {html_file} не найден.")
    except Exception as e:
        print(f"Произошла ошибка: {e}")

delete_html_tags("draft.html")
