## 1 Вопрос

В вашей компании используется CI/CD-система, которая автоматически развертывает приложение на основе Git-тегов. Вам необходимо создать новый релиз ѵ2.5.0, который должен соответствовать следующим требованиям:
1. Тег должен содержать подробное описание изменений в релизе.
2. Тег должен быть создан для определенного коммита с хешем a7d3f1c, а не для HEAD.
3. Тег должен быть доступен всем разработчикам через удаленный
репозиторий.
4. В системе должна сохраниться информация о том, кто и когда создал этот
тег.
Какая последовательность команд Git корректно выполнит все эти требования?

- [ ] git tag -s v2.5.0 a7d3f1c -m "Release v2.5.0" && git push-follow-tags
- [ ] git checkout a7d3f1c && git tag v2.5.0 && git push origin v2.5.0
- [ ] git checkout a7d3f1c && git tag -s v2.5.0 -m "Release v2.5.0" && git push -tags
- [x] git tag -a v2.5.0 a7d3f1c -m "Release v2.5.0" && git push origin v2.5.0

---

## 2 Вопрос

Какой из следующих подходов наиболее эффективен для интеграции внешнего репозитория, когда требуется сохранить полную историю изменений внешнего проекта и иметь возможность вносить локальные изменения, не затрагивая основной репозиторий?
Использование git submodule с последующим форком подмодуля

- [ ] Копирование файлов вручную и добавление их в gitignore
- [ ] Использование git submodule с настройкой shallow clone
- [x] Использование git subtree без опции -squash
- [ ] Использование git subtree с опцией --squash

---

## 3 Вопрос

Разработчик случайно выполнил git reset-hard HEAD-3, удалив последние три коммита, которые еще не были отправлены в удаленный репозиторий. Какая последовательность команд позволит восстановить потерянные коммиты и создать новую ветку с этими изменениями?

- [ ]
1 git reflog
2 git reset --hard HEAD@{3}
3 git checkout -b recovery-branch

- [ ]
1 git log-all
2 git cherry-pick <commit-hash>
3 git push origin recovery-branch

- [x]
1 git reflog show
2 git checkout HEAD@{3}
3 git checkout -b recovery-branch

---

## 4 Вопрос

В проекте с микросервисной архитектурой обнаружена критическая уязвимость безопасности, внесенная коммитом abc123 два месяца назад. Этот коммит затрагивает общую библиотеку аутентификации, используемую во всех сервисах. Ситуация осложняется следующими факторами:
1. После проблемного коммита было сделано более 200 коммитов в основной
ветке.
2. От основной ветки было создано пять релизных веток, в которых также есть
этот коммит.
3. Несколько команд разработчиков создали feature-ветки от разных точек истории.
4. Некоторые последующие коммиты в основной ветке частично исправляют проблему, но не полностью.
5. Все затронутые ветки уже развернуты в различных средах (тестовой, препродакшен, продакшен).
Какая стратегия будет эффективной для устранения уязвимости во всех ветках с минимальным риском нарушения работы проекта?

- [ ] Создать единый исправляющий коммит с помощью git revert abc123 в основной ветке и затем выполнить cherry-pick этого коммита во все релизные ветки
- [ ] Создать серию revert-коммитов для проблемного коммита и всех коммитов, которые частично его исправляли, затем создать новый коммит с полным исправлением
- [x] Создать hotfix-ветку от точки до проблемного коммита, внести исправления и выполнить слияние этой ветки со всеми затронутыми ветками
- [ ] Использовать git rebase -1 для редактирования проблемного коммита в каждой ветке, с последующим принудительным обновлением (force-push)
- [ ] Использовать git bisect для точного определения проблемного кода, создать патч и применить его ко всем веткам с помощью git am

---

## 5 Вопрос

Вы работаете над проектом. В ветке feature/mvp у вас есть несколько коммитов, и Вы хотите исправить последние три коммита, включая текущий. В одном из них есть ошибка, которую вы хотите исправить, а в другом - неудачное
название. Вы хотите изменить порядок коммитов, исправить ошибку и изменить название коммита, чтобы улучшить историю проекта перед push изменений в основную ветку.
Какую команду в Git надо использовать, чтобы выполнить всё это в интерактивном режиме?

- [ ] git cherry-pick HEAD~3
- [ ] git pull --rebase -i HEAD~3
- [ ] git merge --no-ff feature/mvp
- [x] git rebase -i HEAD~3
- [ ] git reset -1 HEAD~3
  
---

## 6 Вопрос

Для чего используется Git Submodules?

- [ ] Для удаления веток из другого репозитория
- [ ] Для работы с несколькими независимыми репозиториями в одном проекте
- [ ] Для синхронизации версий файлов между несколькими проектами
- [ ] Для объединения нескольких репозиториев в один, чтобы они работали как единое целое
- [x] Для отслеживания изменений в другом репозитории как части вашего текущего проекта

---

## 7 Вопрос

Объясните, как технически работает Git LFS и какие преимущества он предоставляет по сравнению со стандартным Git при работе с большими файлами.

- [ ] Git LFS создает отдельный репозиторий для больших файлов и автоматически синхронизирует его с основным репозиторием при выполнении команд push и pull, это уменьшает размер основного репозитория
- [ ] Git LFS использует специальный алгоритм сжатия для больших файлов, который эффективнее стандартного алгоритма Git, это позволяет хранить большие файлы с меньшими затратами дискового пространства
- [x] Git LFS заменяет большие файлы в репозитории на текстовые указатели (pointer files), содержащие ЅHA-256 хеш и метаданные, а сами файлы хранятся на отдельном LFS- сервере, это ускоряет операции клонирования и извлечения
- [ ] Git LFS автоматически разбивает большие файлы на фрагменты и хранит только изменившиеся фрагменты при каждом коммите, это позволяет эффективно отслеживать изменения в бинарных файлах
- [ ] Git LFS позволяет подключать внешнее хранилище через Git remote и хранить большие файлы отдельно от основного репозитория, но с теми же идентификаторами коммитов

---

## 8 Вопрос

Ваш коллега, работая над коммитами в ветке main, заметил: история коммитов в ней содержит коммит 325b012 с очень большим файлом debug. log и другими изменениями. Этот файл уже удален из репозитория в коммите 8dd9645, но всё еще существует в истории и усложняет работу с репозиторием. Он выполнил какую- то операцию с деревом коммитов и удалил этот файл из всех предыдущих
коммитов.
Начальное состояние ветки - вывод git log --oneline:

    1 f1fe759 (HEAD -> main) Fixed documentation and comments
    2 8dd9645 Removed debug.log
    3 c60f0ed Finished main feature
    4 325b012 Added model implementation
    5 e21d3cc Initial commit

Итоговое состояние ветки (вывод git log --oneline):

1 62db399 (HEAD -> main) Fixed documentation and comments
2 af98fe5 Removed debug. log
3 f7048f0 Finished main feature
4 4d1dde5 Added model implementation
5 e21d3cc Initial commit

Какую операцию из перечисленных выполнил ваш коллега?

- [ ] Выполнил git commit amend, удалив файл вручную, а затем перезаписал историю командой git push-force
- [ ] Выполнил git filter-branch -index-filter "git rm-cached debug1.log" -- --all
- [x] Выполнил git filter-branch-tree-filter "rm -f debug.log" -- --all
- [ ] Выполнил git rebase -i для редактирования коммита и удаления файла
- [ ] Выполнил git cherry-pick для удаления файла и пересоздал коммиты вручную

---

## 9 Вопрос

Вы обнаружили ошибку в текущей версии проекта и хотите использовать команду git bisect для поиска коммита, который создал эту ошибку.
Вы знаете, что ошибка не воспроизводится в коммите с хешем 9989c09, а хеш коммита текущей версии проекта - c1e97f1.
Какую команду надо выполнить для начала работы с git bisect?

- [x] git bisect start 99a9c09 c1e97f1
- [ ] git bisect reset
- [ ] git bisect bad c1e97f1
- [ ] git bisect start cle97f1 99a9c09
- [ ] git, bisect good 99a9c09

---

## 10 Вопрос

Вы работаете в команде, использующей расширенную методологию Git Flow с дополнительными типами веток. 
Ваш проект имеет следующую структуру веток:

    • main (стабильные релизы) develop (текущая разработка)
    • release/* (подготовка релизов) hotfix/* (срочные исправления) feature/* (новые функции)
    • experimental/* (экспериментальные функции)
    • refactor/* (рефакторинг кода)

Один из ваших коллег выполнил следующие действия:

    • Создал ветку refactor/db-constraints от develop
    • Сделал в ней 15 небольших коммитов, каждый из которых рефакторит отдельную часть кода БД
    • Выполнил слияние ветки refactor/db-constraints в develop командой: git merge --squash refactor/db-constraints
    • Создал новый коммит в develop с подробным описанием всех изменений
    • Не удалил ветку refactor/db-constraints после слияния

Какой из следующих выводов отражает последствия таких действий с точки зрения расширенного Git Flow и управления историей изменений?

- [ ] Полностью не соответствует, так как в Git Flow всегда требуется использовать стандартное слияние (git merge --no-ff ) для сохранения всей истории изменений, включая промежуточные коммиты даже для веток рефакторинга
- [ ] Не соответствует, так как ветки refactor/* не предусмотрены в стандартной Git Flow, их следовало оформить как feature/*
- [ ] Частично соответствует, но коллега должен был использовать git rebase перед слиянием, чтобы создать линейную историю, а затем выполнить fast-forward merge
- [x] Соответствует для веток рефакторинга, так как объединение множества мелких изменений в один логический коммит с помощью -squash упрощает историю develop, при этом полная детализация изменений остается доступной в исходной ветке
- [ ] Не соответствует, так как после слияния с флагом -squash ветка refactor/db-constraints должна быть немедленно удалена, потому что ее история больше не имеет значения

---

## 11 Вопрос

Вы работаете в ветке feature/new-customer-model, которая была создана командой git checkout -b feature/new-customer-model. После завершения разработки вы пытаетесь отправить изменения в удаленный репозиторий origin и выполняете команду git push origin
- [ ] Какой результат вы получите и почему?
- [ ] Команда успешно завершится, а в удаленном репозитории будет создана новая ветка
- [ ] Команда завершится с ошибкой, так как origin не может быть именем удаленного репозитория
- [ ] Команда завершится с ошибкой, так как перед push необходимо подписать коммиты с помощью git push -s
- [ ] Команда завершится успешно, но с предупреждением о том, что была создана новая ветка
- [x] Команда завершится с ошибкой, так как локальная ветка еще не связана с удаленным репозиторием

---

## 12 Вопрос

Команда разработчиков решила хранить большие бинарные файлы (изображения, видео и 3D-модели) в репозитории Git. Все изменения в них фиксируются напрямую в коммитах. Репозиторий уже содержит 2 ГБ исходного кода и документации. Ежедневно добавляется около 200 МБ новых бинарных файлов с незначительными изменениями.
Оцените, насколько правильно использовать Git в таком сценарии, и объясните, как это повлияет на производительность и размер репозитория в долгосрочной перспективе.

- Это некорректно: Git будет сохранять полные копии файлов при каждом изменении, это приведет к росту размера репозитория и замедлению операций
- Это допустимо, если использовать shallow clone с глубиной не более 10 коммитов при работе с репозиторием: тогда операции будут достаточно быстрыми
- Это допустимо при условии регулярного выполнения git go aggressive для оптимизации хранилища объектов и удаления избыточных данных
- Это нормальная практика: Git использует дельта-сжатие для всех типов файлов, поэтому размер репозитория будет расти линейно, а не экспоненциально
- Это некорректно, так как Git не умеет работать с файлами в кодировке, отличной от UTF-

---

## 13 Вопрос

Вы работаете над проектом и замечаете, что изменения, которые касаются
исправления ошибки в форме в ветке feature/data-form, исчезли, хотя раньше они
точно были.

Вы выполняете команду git log и видите следующий вывод:
    1 commit 1c69684
    2 Author: Some Developer
    3 Date: Mon Dec 10 10:00:00 2024
    4 Initial implementation of form functionality

    1 commit 5f62b1c
    2 Author: Some Developer
    3 Date: Mon Dec 9 18:30:00 2024
    4 Added database connection

После этого вы выполняете команду git reflog, чтобы посмотреть журнал
операций с объектами в Git, и видите такой вывод:
    1 5f62b1c HEAD@{0}: reset: moving to HEAD~1
    2 a2f3143 HEAD@{1}: commit: Fix for form functionality
    3 5f62b1c HEAD@{2}: commit: Initial implementation of form functionality

- [ ] Выполнена git rebase, из-за которой коммит а2f3143 был потерян, а для восстановления надо выполнить git stash pop
- [x] Выполнена git reset --hard, которая удалила коммит а2f3143, а для восстановления надо выполнить git cherry-pick a2f3143
- [ ] Выполнена git revert, отменившая изменения из коммита a2f3143, а для восстановления надо выполнить git revert HEAD
- [ ] Выполнена git reset -soft, которая удалила коммит a2f3143 и перенесла изменения в staging area, а для восстановления надо выполнить git commit
- [ ] Выполнена дgit reset --mixed, которая удалила коммит а2f3143 и оставила изменения в рабочей директории, а для восстановления надо выполнить git commit
