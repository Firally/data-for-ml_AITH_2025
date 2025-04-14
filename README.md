# Data for ML - Сбор и разметка данных для машинного обучения
### Никитина Алина Андреевна
______________________________________

## Модуль 3. Разметка данных

### Проект: Разметка окон на фасадах зданий

**Задача:**   
  
Городская служба осуществляет мониторинг фасадов зданий, чтобы следить за соответствием проектной документации (количество и расположение окон в проекте должно совпадать с фактическими) и контролировать любые изменения. Если мы научим модель находить окна на фотографии фасада с высокой точностью, то сможем автоматически контролировать факт внесения изменений в фасад (в т.ч. количество окон) без необходимости каждый раз вручную проверять здание. При появлении/исчезновении окон с фасада (в сравнении со старой фотографией или проектной документацией) система сможет это «подсветить» специалистам для детального осмотра. На следующих этапах, по этим данным будет проводиться и оценка качества окон.

**Датасет:**   
  
Датасет состоит из изображений фасадов зданий

<img width="1415" alt="image" src="https://github.com/user-attachments/assets/a69fbd46-b6c7-4521-becf-799b988c84eb" />

<img width="1412" alt="image" src="https://github.com/user-attachments/assets/9b6c5df1-9c82-4492-892b-bd029df7fa05" />

На данных изображениях необходимо разметить окна. Инструкция для разметки находится [тут](https://lynxfai.yonote.ru/share/6a96edb4-74ce-45bc-8e35-a5f98a2da3cb)

Для разметки изображений был создан проект в системе CVAT. Для валидации был составлен Golden Set

<img width="1504" alt="image" src="https://github.com/user-attachments/assets/19ba2e7c-7947-46df-94a1-32768b6aa7ce" />

Аннотатор данных - Юлия Овчинникова.
Получившаяся точность разметки (mAP50-95) - **92,5%**

Обратная связь от Юлии:
```
Инструкция по разметке понятная, понравилось, что было много примеров с разметкой. При этом датасет очень разнообразный на вид окон, и все равно возникало чувство "а правильно ли я выделяю" :)

Еще появлялось чувство безысходности, когда на картинке было несколько зданий с маленькими окнами. Невозможность исполнения задачи ))))

Сложности были в быстром освоении инструмента, для нового человека, можно добавить прям пошагово, как им пользоваться, хотя бы основные кнопки.

Спасибо за интересное задание)
```

Полученный отзыв обратил мое внимание на несколько проблем:
1. Отсутствие объяснения по работе с CVAT в инструкции для разметки
2. Некоторые моменты объяснены были не полностью

Ранее на рабочих проектах я не писала инструкций по работе с конкретной системой разметки, но в данном случае действительно было бы не лишним это описать. В случае рабочих проектов, асессоры уже знают про то, как проходит разметка в системе, поэтому данный этап не требуется.  

Хочется отметить, что при постановке задачи ML-инженеру нужно просмотреть хотя бы небольшой пул данных для того, чтобы определить, какие могут возникнуть трудности при разметке и описать такие случаи. Кроме того, нужно отмечать, что сложные примеры асессору лучше пропустить, чтобы не допустить ошибки и не "запутать" модель при обучении. Если сложные примеры действительно нужны для обучения, лучше отправить их более опытным разметчикам.  
  
И немаловажно упомянуть о важности валидации разметки (использование Golden Set | метрик согласованности и т.д.), так как часто тестирование модели проводится на размеченных асессорами данных. В таком случае, нужно знать и точность, с которой асессор разметил датасет, т.к. в ином случае будет сложно говорить о точности самой модели. Также метрики позволяют понять, какой асессор с какими задачами лучше всего справляется (сегментация / детекция / классификация и т.д.) для того, чтобы иметь возможность отправлять асессора на более подходящие ему задачи.
