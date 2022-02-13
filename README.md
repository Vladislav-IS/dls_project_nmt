# dls_project_nmt

Итоговый проект, тема - "Neural Machine Translation".

На всякий случай приведу данные о себе: ФИО - Семенов Владислав Юрьевич, Stepik-ID - 273574954.

В данном проекте решалась задача перевода английских текстов на берберский язык. Использовалась архитектура Transformer из статьи Attention is All You Need (https://arxiv.org/pdf/1706.03762.pdf). Были выполнены первые две части проекта:
- обучены BPE-токенизатор и word2vec;
- обучен трансформер.

К сожалению, на реализацию третьей части проекта (прунинг голов) не хватило времени.

BLEU для даннной модели оказлся чуть выше 22, при этом применение word2vec в качестве предобученных весов трансформера не дало ощутимых изменений. Предполагаю, что низкий BLEU связан с глубокими различиями английского и берберского языков. К тому же объём данных для обучения был маловат (англо-берберский перевод, видимо, относится к числу не очень востребованных задач). Тем не менее модель переводит английские выражения более-менее толково (хотя перевод часто зависит от точки в конце предложения, см. ниже).

![image](https://user-images.githubusercontent.com/74904348/153703833-ae3ad9bf-24df-42f4-b71c-eb461932eb4c.png)

Модель с предобученными весами из word2vec реализована в блокноте with_word2vec.ipynb, модель без весов - в блокноте attention_transformer.ipynb (конечно, можно было обойтись одним из этих блокнотов, но, пожалуй, я приведу оба, хоть и разница между ними минимальна). В блокноте translations.ipynb содержится "интерфейс" для осуществления перевода, нужно только запустить ячейки. Там же приведена реализация телеграм-бота (ник бота: @eng_ber_bot).

![image](https://user-images.githubusercontent.com/74904348/153749953-afac3136-3b61-4938-9eff-17376382f52c.png)

Помимо перевода бот также может вывести полученный в ходе обучения BLEU (через команду /bleu). Однако, чтобы бот работал, всё равно необходимо запустить блокнот translations.ipynb.

Насчёт того, нужны ли в репозитории какие-то дополнительные файлы, не было никаких указаний. Тем не менее в папку other я добавил файлы, необходимые для осуществления перевода:
- обученная модель токенизатора для английского языка (bpe_en.bin);
- веса трансформера (best-val-model.pt и last-val-model.pt). При этом в модель были загружены веса, полученные на последней эпохе обучения (то есть last-val-model.pt), а не те, которые соответствовали минимуму валидационного лосса. Дело в том, что лосс весьма неточно отражал реальную ситуацию обучения (BLEU при минимуме валидационного лосса не был максимальным).
- словари souce- и target-языков (src_vocab.pth и trg_vocab.pth).

Все эти файлы можно загрузить в Google.Colab при запуске блокнота translations.ipynb.

Теперь подробнее об источниках и ссылках. Датасет для обучения я нашёл здесь: http://www.manythings.org/anki/. При написании модели я опирался на семинар по трансформерам (функции для перевода и подсчёта BLEU взял прямо оттуда) и на следующие ресурсы:
- https://sungwookyoo.github.io/tips/study/Multihead_Attention/ (маски для nn.MultiheadAttention);
- https://pytorch.org/tutorials/beginner/transformer_tutorial.html (PositionalEncoding);
- https://pocketadmin.tech/ru/telegram-bot-на-python/#bot (телеграм-бот).
