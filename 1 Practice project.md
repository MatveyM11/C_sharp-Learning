Программа должна содержать класс EntityRepository в котором есть список объектов класса Entity.
Entity имеют свойство Vector3 Position, string Name и bool HasChanged, Изменение первых двух свойств должно выставить HasChanged в true
У ER есть метод Update, который проходится по всему списку, и если видит HasChanged у Entity то вызывает метод Serialize - он пускай возвращает строку, которая описывает значения свойств и номер этой Entity. После этого HasChanged возвращает в false.
Все эти строки метод Update возвращает в виде листа
Метод Update сам принимает список таких строк.
После того как он прошёлся по всем объектам в списке и узнал изменения и записал в возвращаемый список, он проходится по списку который получил внутрь, и согласно номер в строке ищет Entity в списке. Если не находит - создаёт пустую. Если создал или нашёл - вызывает метод Deserialize - она должна распарсить строку и обновить значения. 


В Main ты создашь два инстанса EntityRepository, назовём их server и client
В Server ты создаёшь несколько Entity и пихаешь их в список.

Ты запускаешь цикл, который вызывает Update у server, получает строки, и вызывает Update client - пихает туда строки.
Ты читаешь с консоли строку - номер сущности и команду типа left, right, up, down - в зависимости от неё ты находишь в server сущность и меняешь Position

После этого выводишь в консоль построчно состояние server сущностей и client сущностей
