# Мануал по blockchain Bostrom (загрузочный blockchain супер-интеллекта Cyber)

## Вместо предисловия

### Отказ от ответсвенности

Автор данного мануала не является разработчиком и не входит в команду проекта. Изложенное ниже является личным пониманием проекта и не обязательно отражает позицию его команды.

### Ссылки на официальные документы по Cyber от команды проекта

1. [Cyber whitepaper (english)](https://github.com/cybercongress/cyber/blob/master/computing-the-knowledge/computing-the-knowledge.md)
2. [Github репозиторий с описанием технической спецификации проекта (english)](https://github.com/cybercongress/cyber)
3. [Модель экономики проекта (english)](https://github.com/cybercongress/cybernomics/blob/main/bostrom/README.md)

### Подписка на обновления пособия

Подписаться на обновления данного учебного пособия можно:

1. В телеграм канале "Учим Cyber" https://t.me/CyberForever
2. На github https://github.com/learn-cyber-superintelligence/bostrom-ru

### Полезное по Bostrom

1. [Дашборд по Bostrom на данных нод, поддерживаемых командой проекта](https://cybernode.ai/grafana/d/cyber_stats/computer?orgId=2)
2. [Дашборд по Bostrom от валидатора Bro-n-Bro на данных ноды и внешних данных](https://monitor.bronbro.io/d/bostrom-stats/bostrom-stats?orgId=2&from=now-30d&to=now)
3. [Интро в cyber от Citizen Cosmos](https://github.com/citizen-cosmos/Staking/blob/main/Cyber.md)

### Приглашение соавторов

Буду рад, если знающие люди будут помогать дополнением документа. Делайте ваши pull request.

## Bostrom

[Bostrom](https://cyb.ai) - проект суперинтеллекта на основе blockchain (cosmos-sdk), консенсус-протокола Tendermint и механизма контент-адресации (с текущей имплементацией IPFS).

Bostrom - загрузочная сеть (bootloader) будущей сети blockchain Cyber.

### Назначение сети

Термин суперинтеллект введен в обращение современным философом Ником Бостромом (в честь которого назван blockcahin Bostrom). Ник Бостром определяет суперинтеллект как "интеллект, существенно превосходящий познавательный способности человеческого интеллекта во всех областях знаний". К примеру, сейчас существуют программы, которые играют в шахматы лучше любого человека, но эти программы не способны справляться с заданиями в других областях знаний. Предполагается, что суперинтеллект будет понимать различные области знаний.

Bostrom позволяет доказуемо пополнять knowledge graph (граф знаний) - ориентированный взвешенный граф между CIDs (контент-идентификаторами файлов, они же контент-адреса, IPFS-хеши, IPFS-ссылки).

Cyberlinks это ребра knowledge graph, CIDs - вершины knowledge graph.

Чтобы создавать cyberlinks в Bostrom, на аккаунте агентов (нейронов в терминах Bostrom) должны быть токены Вольты и Амперы.

Созданные cyberlinks по определению blockchain нельзя удалить. Это значит, что они всегда будут учитываться в cyberrank (до момента появления функции "забывания" или "прунинга").

### Механизм работы Bostrom (cyberlinks, IPFS)

Результаты выдачи в bostrom это файлы, хранящиеся в IPFS, на IPFS хеш которых при помощи cyberlink ссылается IPFS хеш файла из поисковой строки. 

В случае, если на hash текстового файла конкретного поискового запроса не создано cyberlinks, то в выдаче отображаются объекты прилинкованные по cyberlinks к хешу текстового файла с содержимым "0". 

Аватарка аккаунта это файл-картинка в IPFS, на hash которого при помощи cyberlink ссылается hash текстового файла "avatar".

Сообщение в ленте twitter конкретного аккаунта - это cyberlink между текстом "tweet" и IPFS hash файла сообщения. 

### Токены Bostrom

В сети Bostrom действуют следующие токены: BOOT, HYDROGEN, VOLT, AMPERE. Все токены имеют применение.

BOOT можно:

- `to stake` (делегировать токены валидатору), за что выплачиваются reward-s (как плата за риски); в обмен на застейканый BOOT 1 к 1 выпускаются токены HYDROGEN
- перевести кому-то (если находится в ликвидном состоянии)
- оплачивать транзакции в сети (платить за газ). Но сейчас многие валидаторы принимают транзакции бесплатно.

HYDROGEN можно:

- `to investmint` на ограниченный срок, чтобы выпустить VOLT и AMPERE токены
- обменять обратно на делегированные BOOT, чтобы перевести BOOT в ликвидное состояние
- перевести кому-то (если находится в ликвидном состоянии)

VOLT, AMPERE:

- нужны создавать cyberlinks, чтобы обучать Bostrom
- их можно передавать

BOOT токен своим названием символизирует "загрузочный" смысл сети Bostrom для будущей сети Cyber.

## Поощрение жалемоего поведения агентов (валидаторов и делегаторов)

Bostrom это proof-of-stake blockchain. Функционирование proof-of-stake blockchain обеспечивают валидаторы. Валидатор (hero, герой в терминах Bostrom) - это сервер с установленным програмным обеспечением (нодой) blockchain.

На каждой ноде хранится реплика blockchain (лог тразнакций), позволяющая рассчитать общее состояние в каждый блок (например, баланс аккаунтов). Ноды договариваются между собой о едином состоянии дел руководствуясь консенсус-протоколом Tendermint.

Bostrom устроен так, чтобы экономически поощрять (инцентивизировать) валидаторов и держателей токенов (neuron, нейронов в терминах Bostrom) выполнять полезные для системы функции.

Полезные функции валидаторов - обсчитывать каждый блок blockchain, проверять и подписывать сообщения о транзакциях от других нод (и тем приходить к консенсусу по поводу текущего состояния blockchain).

Полезные функции держателей токенов (нейронов):

- поддерживать желаемый баланс между токенами в состоянии `staked` и ликвидными
- распределять токены в состоянии `staked` на валидаторов, которые исправно справляются со своими функциями и тем не допускают `slashing`
- использовать токен H (HYDROGEN, ВОДОРД), который получается в обмен на `staked` BOOT, для инвестминтинга A и V токенов (и использовать A и V для создания сyberlinks, т.е. обучения Bostrom).

Механизм экономической инцентивизации героев и нейронов в Bostrom включает в себя награды (rewards) и штрафы (penalty).

Blockchain запрограммирован так, что для выплаты наград каждый блок выпускаются новые токены BOOT. Размер выпуска новых токенов определяется коэффициентом `inflation_rate`. Коэффициент `inflation_rate` зависит от доли BOOT в состоянии `staked`:

- если доля `staked` BOOT меньше 80% в системе - то коэффициент `inflation_rate` будет увеличиваться каждый блок, пока не достигнет значения `inflation_rate_max`. Чем выше `inflation_rate` тем больше наград приходит на `stake`.
- если доля `staked` BOOT больше 80% в системе - то коэффициент `inflation_rate` будет уменьшаться каждый блок, пока не достигнет значения `inflation_rate_min`, а значит что выпускается больше BOOT токенов, значит держать их в состоянии `staked` менее выгодно.

Новые токены распределяются среди делегаторов (нейронов, которые застейкали свои токены) и валидаторов (героев), пропорционально их токенам в состоянии `staked`.

Валидаторы получают установленную комиссию.

Делегаторы получают вознаграждение за то что делегируют (`to stake`) токены валидаторам и несут риски `slashing` (сокращения `stake` на величину penalty) и пропуска блоков без получения вознаграждения (пока валидатор находится в состоянии `jail`).

Риски делегаторов заключаются в том, что валидаторы, которым они делегировали токены совершат нарушения.

- Downtime (пропуск обсчета новых блоков)
- Double sign (ошибочная настройка второй ноды с уже использующимся приватным ключом)

`Slashing` это механизм обратной связи от blockchain валидаторам, т.к. заставляет делегаторов перераспределять свои `stake` в пользу валидаторов более исправно выполняющих свои функции.

Когда за конкретным валидатором blockchain фиксируется нарушение, тот валидатор переходитв в режим jail ("попадает в тюрьму") и тогда на делегированные ему токены не выпускаются награды.

Все нарушения и penalty прописаны в настройках blockchain и исполняются согласно консенсус протокола Tenderimnt.

На текущий момент (2022-01-14) в системе нет публично доступного сервиса мониторинга статистики нарушений по валидаторам, поэтому делегаторам приходится принимать решения опираясь лишь на свою статистику. Для этого можно использовать хак, когда на балансы валидаторов делегировать лишь круглые числа, и в таком случае, при наступлении `slashing` будет легче видеть, у какого валидатора этот `slashing` случился.

Также, чтобы хеджировать риски `slashing`, можно распределять `stake` на нескольких валидаторов.

Делегированные токены BOOT можно перераспределять между валидторами.

## Investminting

Чтобы получить ресурсные токены A (AMPERES, АМПЕРЫ) и V (VOLTS, ВОЛЬТЫ) нужно заинвестминтить H (HYDROGEN, ВОДОРОД). Понятие инвестминтинга объединяет в себе свойства минтинга (выпуска новых токенов) и инвестирования (размещения капитала на время для получения дохода с него).

После того как H токены investminted, баланс пополняется на число временно-неликвидных (до окончания периода инвестминтинга), но готовых к использованию A и V токенов.

В обмен на 1 V токен можно создать 1 cyberlink в сутки. Возможность создавать cyberlinks восстанавливается в течение суток.

Если сеть недозагружена, то cyberlinks можно создавать больше (вплоть до 4 cyberlinks на 1 V).

Cyberlinks будут ранжироваться выше, чем больше A-токенов на балансе аккаунтов, создавших эти cyberlinks. Cyberrank пересчитывается каждый блок, потому изменение количества A токенов, на балансе аккаунтов их создавших будет сразу учтено в cyberrank всего графа.

В инвестминтинге действуют следующие правила:

1. Период на который H токены investminted пропорционально влияет на количество полученных A и V токенов.
2. Число токенов H investminted пропорционально влияет на количество полученных A и V токенов.
3. Токены (H, A и V) становятся ликвидными после истечения investminting периода.
4. До того как токены разблокированы, они выполняют свою ресурсную функцию для аккаунта - A увеличивают ранк ссылок (очередность в выдаче), V - могут быть использованы для производства cyberlinks.
5. Максимальное время инвестминтинга (`investmint_max_period`) ограничено, но увеличивается каждые 547 дней (`horizon_period_init`)
6. Как много A и V можно инвестминтить в единицу времени определяется параметрами `ampere_mint_rate` и `volt_mint_rate`. Значение этих параметров сокращается вдвое каждые 547 дней (`ampere_base_halving_period`, `volt_base_halving_period`). В начале жизни сети можно заинвестминтитить больше A и V чем в конце.

A и V - конечны, не могут быть восполнены в случае если время инвестминтинга упущено. Каждые 567 дней для инвестминтинга токенов наступает халвинг: за единицу времени минтится вдвое меньше токенов, чем до халвинга.

## Идеи использования Cyber

1. Сyber можно сделать универсальным api - интерфейсом для публикации и query-ing данных. Потенциально, могут быть созданы приложения, которые будут получать данные по конкретным запросам, парсить и преобразовывать эти данные, чтобы дальше их можно было как-то использовать (например, строить bi с визуализациями).
