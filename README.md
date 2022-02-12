# dls_project_nmt

Итоговый проект, тема - "Neural Machine Translation".

На всякий случай приведу данные о себе: ФИО - Семенов Владислав Юрьевич, Stepik-ID - 273574954.

В данном проекте решалась задача перевода английских текстов на берберский язык. Использовалась архитектура Transformer из статьи Attention is All You Need (https://arxiv.org/pdf/1706.03762.pdf). Были выполнены первые две части проекта:
- обучены BPE-токенизатор и word2vec;
- обучен трансформер.

К сожалению, на реализацию третьей части проекта (прунинг голов) не хватило времени.

BLEU для даннной модели оказлся чуть выше 22, при этом применение word2vec в качестве предобученных весов трансформера не дало ощутимых изменений. Предполагаю, что низкий BLEU связан с глубокими различиями английского и берберского языков. Тем не менее модель переводит английские выражения более-менее толково.

![image](https://user-images.githubusercontent.com/74904348/153703351-98412bca-2511-49ba-806b-ac749524d68f.png)

Теперь подробнее о реализации трансформера:
- датасет для обучения я взял отсюда: http://www.manythings.org/anki/
- ббб



В данном проекте решалась задача генерации фасадов зданий по их сегментированным изображениям. Использовалась архитектура pix2pix. К сожалению, из-за нехватки времени (а также из-за того, что в первую половину проекта я пытался генерировать не фасады, а обувь по контурам) мне не удалось реализовать полноценную нейросеть: на сгенерированных изображениях видны неточности и многочисленные артефакты. Да еще и собственную задачу я выбрать не успел. Тем не менее обучение модели и интерфейс для генерации более-менее работают.
