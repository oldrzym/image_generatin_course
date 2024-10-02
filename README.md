# Обработка и генерация изображений
## Репозиторий Китаева Сергея

### Задача
**ДЗ 2. Имплементация GAN с изображениями 128x128**

Датасет: **CelebA**

Ссылка на Kaggle-ноутбук: [https://www.kaggle.com/code/sergeykit/dcgan](https://www.kaggle.com/code/sergeykit/dcgan)

### Выполнено:
1. Имплементирован **CSPup** блок.
2. Имплементирован **генератор GAN** по заданной архитектурной схеме.
3. Обучен имплементированный **GAN**.
4. Проведены эксперименты с целью улучшить сходимость.

### Эксперименты для улучшения сходимости:
- Замена **BCELoss** на **BCEWithLogitsLoss**: `output2`
![image](https://github.com/user-attachments/assets/6528c32b-0255-44f6-ac9d-9f54a70c2ec3)

- Обучение дискриминатора **не на каждой итерации**: `output3`
![image](https://github.com/user-attachments/assets/90452369-3d64-49e2-aecf-b2cf9a414d30)

- Уменьшение количества сверток в дискриминаторе: `output4`
![image](https://github.com/user-attachments/assets/35d349f7-ce67-4c28-b22f-346996cab53b)

- Замена в **CSPup** блока **ReLU** на **LeakyReLU**: `output5`
![image](https://github.com/user-attachments/assets/d68e093d-4b6d-4b2b-bc99-9c2da6f05c61)

- Изменение **batch size**: `output6`
![image](https://github.com/user-attachments/assets/7ad0660d-d86e-4d13-b9c1-135eeeb7f13a)
![image](https://github.com/user-attachments/assets/543ab8ad-2787-4206-98d9-8a122dc107d8)

### Результаты:
- Успешное обучение GAN.
- Улучшение сходимости за счет перечисленных изменений.

### Исправления:
#### Имплементация CSPup блока

```python
import torch.nn as nn

class CSPup(nn.Module):
    def __init__(self, in_channels, out_channels, kernel_size=4, stride=2, padding=1):
        super(CSPup, self).__init__()
        self.kernel_size = kernel_size
        self.stride = stride
        self.padding = padding
        self.in_channels = in_channels
        self.out_channels = out_channels
        self.split_channels = self.in_channels // 2
        
        self.left = nn.Sequential(
            nn.ConvTranspose2d(self.split_channels, self.out_channels, self.kernel_size, self.stride, self.padding, bias=False)
        )
        
        self.right = nn.Sequential(
            nn.Conv2d(self.split_channels, self.out_channels, 1, 1, 0),
            nn.ReLU(),
            nn.ConvTranspose2d(self.out_channels, self.out_channels, self.kernel_size, self.stride, self.padding, bias=False),
            nn.Conv2d(self.out_channels, self.out_channels, 3, 1, 0),
            nn.ReLU(),
            nn.Conv2d(self.out_channels, self.out_channels, 3, 1, 0),
        )
    
    def forward(self, x):
        x1, x2 = x.chunk(2, dim=1)
        y = self.left(x1) + self.right(x2)
        return y

### Вывод
Эксперименты и изменения, внесённые в архитектуру GAN, улучшили сходимость модели и качество генерации изображений. Итоговый код включает CSPup блок и настройки, оптимизированные для обучения GAN на изображениях разрешением 128x128.

