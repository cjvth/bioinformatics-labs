# Домашнее задание 2

### Изучение представленности генов в таксонах

## Разминочные вопросы

1. Какой ближайший таксон объединяет:
    - человека и мышь: Euarchontoglires
    - человека и бабочку: Nephrozoa
    - человека и дрожжи: Заднежгутиковые
    - человека и капусту: Эукариоты

2. Ближе всего к человеку находится амёба, относящаяся, как и грибы, к заднежгутиковым. Остальные 3 организма, согласно схеме, разошлись с человеком ещё на этапе эукариотов, а значит, одинаково от него удалены.

## Название выбранного гена

LCTL - lactase-like

## С помощью NCBI BLAST найти не менее 10 (десяти) гомологичных генов в других видах.

Сначала возникла проблема, что я не мог сделать запрос с геном LCLT по всем хордовым - писало, что я израсходовал лимит CPU. Работало только по приматам. С геном из прошлой работы, CCR5, всё работало, потому что он в 3 раза короче. Но в итоге я смог запустить полный LCLT, исключив из поиска *Homo sapiens* и выбрав обычный Megablast вместо Discontigious Megablast. Но вот, когда поиск шёл выше плацентарных, пришлось поставить меньше точность.

Но дальше возникла другая проблема. Даже ограниченный 5000 результатами, даёт 95% приматов. Поэтому придётся делать несколько запросов руками. На первом шаге исключаем человека и смотрим, что вышло. Если почти все результаты принадлежат одному таксону, сохраняем эти результаты, а на следующем шаге исключаем и его. Так повторяем много раз, в какой-то момент исключим млекопитающих.

Из других параметров я только увеличивил количество результатов поиска до 1000.

Среди найденных результатов BLAST предлагал целые хромосомы организмов и предположительные их деления на гены. Я скачивал только последние, поскольку они не занимают много места. Но их минус в том, что они на порядок короче оригинальной последовательности человека и, возможно, совпадают с различными её фрагментами частями. Посмотрим, что будет при множественном выравнивании.

В большинстве результатов predicted ген также назывался "LCLT". Ещё в нескольких случаях "zwilch kinetochore protein (ZWILCH)". Вроде как это не случайность, ZWILCH встречался и очень близко к человеку. Но вроде и не то же самое.

Есть ещё несколько интересных находок, вряд ли связанных с геном человека:
- Микросателлиты коралла длины 664 с E value 3e-25 и морского огурца длины 366 с 4e-62, а также несколько таких же плохих совпадений у первичноротых. 
- Можно посмотреть на predicted-подписи к генам. У двух улиток она "lactase-phlorizin hydrolase-like". E value там порядков -11 и -4.
- А у двух комаров и двух бабочек есть короткие последовательности генов, близкие к одному и тому же участку гена человека. У комара он даже [подписан](https://www.ncbi.nlm.nih.gov/nucleotide/XM_050237616.1) "lactase-like protein". У других организмов там всегда стояло "lactase like (LCTL)". Может быть, этот ген эволюционно выработался, чтобы кусать нас.

## Построить единое множественное выравнивание полученных последовательностей

Файл с выравниванием: [lab2/clustalo-lctl.aln-clustal_num](./clustalo-lctl.aln-clustal_num)

Таблица видов в таком же порядке, как сделало выравнивание

| Ген            | Систематическое название   | Русское название                |
|----------------|----------------------------|---------------------------------|
| XM_053272017.1 | Hemicordylus capensis      | Ложноопоясанная ящерица         |
| XM_022579847.2 | Delphinapterus leucas      | Белуха                          |
| XM_037833619.1 | Choloepus didactylus       | Двупалый ленивец                |
| XM_045541484.1 | Lemur catta                | Кошачий лемур                   |
| XM_015142531.2 | Macaca mulatta             | Макака-резус                    |
| XM_063716020.1 | Pongo abelii               | Суматранский орангутан          |
| AK144007.1     | Mus musculus               | Домовая мышь                    |
| XR_001184173.2 | Heterocephalus glaber      | Голый землекоп                  |
| XM_035820328.1 | Branchiostoma floridae     | Флоридский ланцетник            |
| XM_032945155.1 | Petromyzon marinus         | Морская минога                  |
| XM_039912189.1 | Ornithorhynchus anatinus   | Утконос                         |
| XM_055661354.1 | Leucoraja erinacea         | Ежовый скат                     |
| NC_000015..... | Homo sapiens               | Человек разумный                |
| XM_062206188.1 | Lepus europaeus            | Заяц-русак                      |
| XM_055129622.1 | Sorex araneus              | Обыкновенная бурозубка          |
| XM_001376075.4 | Monodelphis domestica      | Домовый опоссум                 |
| XM_020982918.1 | Phascolarctos cinereus     | Коала                           |
| XM_006153486.3 | Tupaia chinensis           | Китайская тупайя                |
| XM_038581114.1 | Canis lupus familiaris     | Собака                          |
| XM_059697536.1 | Myotis daubentonii         | Водяная ночница                 |
| XM_063090359.1 | Cynocephalus volans        | Филиппинский шерстокрыл         |
| XM_046426476.2 | Marmota monax              | Лесной сурок                    |
| XM_001497027.4 | Equus caballus             | Домашняя лошадь                 |
| XM_064267377.1 | Loxodonta africana         | Саванный слон                   |
| XM_045689661.1 | Salmo salar                | Атлантический лосось            |
| XM_053464309.1 | Spea bombifrons            | Равнинный лопатоног             |
| XM_044077870.1 | Protopterus annectens      | Бурый протоптер                 |
| XM_040706977.1 | Gallus gallus              | Банкивская джунглевая курица    |
| XM_049812191.1 | Accipiter gentilis         | Ястреб-тетеревятник             |
| XM_013946435.1 | Apteryx australis          | Южный киви                      |
| XM_063345383.1 | Chroicocephalus ridibundus | Озёрная чайка                   |
| XM_019533191.1 | Crocodylus porosus         | Гребнистый крокодил             |
| XM_024205611.1 | Terrapene carolina         | Каролинская коробчатая черепаха |

## Проанализировать полученное выравнивание 

Алгоритм отсортировал входные последовательности, сумев сгруппировать их по типам. В начале идут все те 6 последовательностей, которые кодируют протеин ZWILCH. Становится очевидно, что он не то же самое, что и LCTL. Согласно [схеме Genomic context](https://www.ncbi.nlm.nih.gov/gene/197021), ZWILH находится прямо слева от LCTL. Видимо, учёные неточно порезали хромосомы некоторых организмов, и поэтому BLAST выдал лишние результаты.

Дальше идут две записи, которые на сайте были указаны как неизвестные - мышь и землекоп.

Все оставшиеся последовательности кодируют ген LCTL (в одной LCT). И тут алгоритм показывает, что он может почти идеально группировать и животных в группы по родству.

1. Сначала идёт лансцетник, самый дальний их хордовых. Вторым идёт следующий по удалённости организм - минога. Только эти двое не являются челюстноротыми. Затем идёт ежовый скат - хрящевая рыба. Только эти три организма не лопастепёрые рыбы. И как-то между ними затесался утконос.
2. Дальше идут млекопитающие, первый из которых человек. Рядом с нами правильно поставили зайца, правильно поставили рядом сумчатых. Но в целом какой-либо систематики в пределах млекопитающих не наблюдается. Заканчивает эту группу слоняра.
3. Дальше идут оставшиеся не амниоты: лучепёрая рыба, лягушка и двоякодышащая рыба.
4. Завершают список заврии. Сначала птицы, потом близкий к ним крокодил и, наконец, черепаха.

## Консервативные участки

В [файле с выравниванием](./clustalo-lctl.aln-clustal_num) можно увидеть консервативные участки. Три последовательности (их можно чётко заметить на строках 6754-6752), скорее всего, плохо обрезаны. На их основе не будем делать выводы

- В блоках, где человек "NC_000015.10:c66565998-66547532" занимает строки 7261 и 7296 видны участки, которые сохранили млекопитающие и рыбы, но потеряли рептилии и птицы. Только киви, удалённые от остальных птиц, смогли их сохранить.
- 7366: все млекопитающие потеряли 4 нуклеотида
- 7401: слева потеряли все млекопитающие, а справа только утконос сохранил
- 7471: все млекопитающие потеряли. А человек приобрёл в этом месте что-то новое
- 7506: все млекопитающие, кроме утконоса, добавили буквы. На человеке выравнивание сломалось.
- 7541: почти ничего не произошло. Бурозубка потеряла немного. И можно заметить, что сразу после пробела все плацентарные поменяли T на G.
- 7646: почему у человека 18 тиминов подряд?
- 7961: наконец-то всё идеально

## Объединяющий таксон

Все рассмотренные организмы относятся к типу Хордовых (Chordata). Это вторичноротые, у которых по линии между этими двумя ртами идёт каркас тела - хорда, дальше превратившаяся в позвоночник.
