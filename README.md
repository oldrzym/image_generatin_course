# Обработка и генерация изображений
\
### Задача
**ДЗ 4. Обучение Stable Diffusion 1.5 методом Dreambooth**

### Датасет и обучение:
- Собран датасет и обучен **U-Net**.
- Параметры для обучения:

  - `--instance_prompt="a photo of sks man face"` — токен, на который мы хотим обучить персонажа.
  - `--class_prompt="a photo of man face"` — промт для регуляризации.

#### Скриншоты результатов:
![image](https://github.com/user-attachments/assets/96606c63-84df-4fb8-a022-173f04116cc3)
![image](https://github.com/user-attachments/assets/c60ff3d3-d631-4d02-8803-d56ee544b8d2)
![image](https://github.com/user-attachments/assets/52c14127-23a6-46b3-9228-bf6abf6dd80f)
![image](https://github.com/user-attachments/assets/1c11da3a-69f0-478a-824f-aa4a59117a58)
![image](https://github.com/user-attachments/assets/839d249a-c2a6-486e-bd97-92e1d45d1557)


---

### Обучение LoRA и эксперименты:

#### Пример 1:
- **Rank**: 4
- **Learning Rate**: `8e-5`

#### Скриншоты:
![image](https://github.com/user-attachments/assets/65fe4df6-eaf2-469b-915c-a2b1609b066c)
![image](https://github.com/user-attachments/assets/9cdeb177-914c-43cb-b118-35e87e7fb6d0)
![image](https://github.com/user-attachments/assets/edf97304-b68b-4323-b641-855e5102c5ec)
![image](https://github.com/user-attachments/assets/423f53b3-17af-4aac-94d8-71fde30d006f)
![image](https://github.com/user-attachments/assets/784827ef-bc2a-4640-8eaf-e058c5536c7c)


#### Пример 2:
- **Rank**: 8
- **Learning Rate**: `8e-5`

#### Скриншоты:
![image](https://github.com/user-attachments/assets/3c0c4ce5-9161-4546-9fc6-07e2f4001482)
![image](https://github.com/user-attachments/assets/5b8bcf8a-9dcb-4114-8eaa-ade2abf225bd)
![image](https://github.com/user-attachments/assets/dd0ec169-122c-4ba0-8506-608b7afd1b82)
![image](https://github.com/user-attachments/assets/fabecf96-ce2b-4fb4-90e3-8552e1605300)
![image](https://github.com/user-attachments/assets/714b06fc-3667-4c96-8863-cd22086848d9)
![image](https://github.com/user-attachments/assets/917ffa59-6486-4a26-a458-0baf27cd11ac)

---

### ControlNet:

- Эксперимент с использованием **ControlNet**:
![image](https://github.com/user-attachments/assets/02039fbb-c185-436f-a23b-ad5683eddc66)
![Uploading image.png…]()

---

### Вывод:
Обучение Stable Diffusion 1.5 методом Dreambooth с использованием токенов и промтов для регуляризации дало успешные результаты. Обученные модели и LoRA (Low-Rank Adaptation) показали хорошие результаты на разных конфигурациях ранга и learning rate. ControlNet был протестирован для дальнейшего управления генерацией изображений.
