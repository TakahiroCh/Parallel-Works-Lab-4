# Parallel-Works-Lab-4 Приложение akka предназначенное для удаленного тестирования JS приложений. (Готов для проверки)

Примеры запросов :
Запуск производится в IntelliJ IDEA Через Application, где основной класс - WebServer.

Потом отправляю запросы в командной строке ->

Запрос на запуск теста

curl --header "Content-Type: application/json" --request POST --data '{ "packageId":11, "jsScript":"var divideFn = function(a,b) { return a/b} ", "functionName":"divideFn", "tests": [ {"testName":"test1", "expectedResult":"2.0", "params":[2,1] },{"testName":"test2","expectedResult":"2.0","params":[4,2]}, {"testName":"test2","expectedResult":"8.0","params":[4,2]},{"testName":"test2","expectedResult":"8.0","params":[16,2]}] }' 127.0.0.1:8080


Запрос на получение результатов

curl -X GET "127.0.0.1:8080/?packageId=11"


Результат

{"packageId":11,"test":[{"expectedResult":"2.0","params":[4,2],"testName":"test2","result":true},{"expectedResult":"2.0","params":[2,1],"testName":"test1","result":true},{"expectedResult":"8.0","params":[4,2],"testName":"test2","result":false},{"expectedResult":"8.0","params":[16,2],"testName":"test2","result":true}]}
