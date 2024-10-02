# Обработка и генерация изображений

### Задача
**ДЗ 3. Sampling в латентном пространстве StyleGAN**

### Найдены проекции изображений в пространстве StyleGAN:
1. С помощью среднего вектора латентного пространства.
2. С помощью лосса между выходами энкодера.
![image](https://github.com/user-attachments/assets/27e1ce3f-3ff0-4803-a8a4-a996887ba765)

#### Пример изображений:
Исходные изображения | (1) | (2)

### Оптимальные гиперпараметры:
- `w_avg_samples = 10000`
- `regularize_noise_weight = 5e5`
- `rec_weight = 0.5`
- `lpips_weight = 1`

---

### Style Transfer

Исходный стиль и его отображение в латентном пространстве:

- Для трансфера стиля использовался вектор W+, беря последние индексы (интервал от 9 до 18), так как первые индексы сильно меняют атрибуты и форму лица.
![image](https://github.com/user-attachments/assets/b5be4332-44b8-4edf-8599-3478a9d8e033)

#### Пример:
![image](https://github.com/user-attachments/assets/eb147e90-82cc-41f0-9ed7-d56e5af388a5)

Исходный стиль | Трансфер стиля
![image](https://github.com/user-attachments/assets/b8445f16-ae1b-4e62-850f-69009a54b52d)
![image](https://github.com/user-attachments/assets/b520174b-21e0-4361-9a4a-af13c9fbd085)

- Исходное изображение и его отображение в латентном пространстве:

![Исходный стиль](image_path)
![image](https://github.com/user-attachments/assets/36f3852b-4d6a-4166-bcb2-27453d19ad90)

- Трансфер стиля:

![Трансфер стиля](image_path)
![image](https://github.com/user-attachments/assets/37730be3-7020-4455-b649-feb65d6e6cba)

![image](https://github.com/user-attachments/assets/f8b0e8f1-c8fd-4ffe-a845-820f1f799eef)

---

### Expression Transfer

Изменение выражений лица в латентном пространстве на основе индексов:

- **Улыбка** — индексы от 0 до 5.
![image](https://github.com/user-attachments/assets/4641e758-b794-46b9-a6ca-66274855bcde)

  ![Улыбка](image_path)

- **Возраст** — индексы от 0 до 9.
![image](https://github.com/user-attachments/assets/0f22c5d4-c726-40bf-b954-eb96f3f8b2fe)

  ![Возраст](image_path)

- **Поворот головы** — индексы от 0 до 6.
![image](https://github.com/user-attachments/assets/100d66ae-30b7-490b-abcf-9520f82c5bba)

  ![Поворот головы](image_path)

---

### FaceSwap

Процесс обмена лицами (FaceSwap) между различными персонажами:

- EMerphy - LDCaprio - Stethem.
![image](https://github.com/user-attachments/assets/99659bbd-06e0-41d5-a4c6-cb479168bfa9)

  ![FaceSwap](image_path)

---

### Вывод:
Были проведены эксперименты с Sampling в латентном пространстве StyleGAN, включая трансфер стиля и выражений лица. Оптимальные гиперпараметры и индексы позволяют контролировать различные аспекты лица, такие как выражения, возраст и стиль.

Результаты показали, что изменение различных частей вектора W+ по-разному влияет на форму лица и атрибуты, что позволяет эффективно использовать латентное пространство для редактирования изображений.
