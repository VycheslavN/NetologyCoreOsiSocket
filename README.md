# Задача "Клиент-серверное приложение"
Описание
После выполнения этого задания вы научитесь создавать сервер, способный принимать подключения.
А также клиента, который будет подключаться к подобному серверу.

Создайте сервер с использованием ServerSocket.
При входящем соединении на сервер, примите его, прочитайте из него строку. Выведите её на экран вместе с номером порта, с которого это соединение пришло.

Вместе с этим в другом методе (это может быть другой класс со вторым main методом или отдельный поток) подключитесь к этому серверу и отправьте ему одну строку.

Реализация
Запускаем сервер на определенном порту и принимаем соединение:

ServerSocket serverSocket = new ServerSocket(port); // порт можете выбрать любой в доступном диапазоне 0-65536. Но чтобы не нарваться на уже занятый - рекомендуем использовать около 8080
Socket clientSocket = serverSocket.accept(); // ждем подключения
PrintWriter out = new PrintWriter(clientSocket.getOutputStream(), true);
BufferedReader in = new BufferedReader(new InputStreamReader(clientSocket.getInputStream()));
Читаем строку и выводим её на экран вместе с номером порта клиента, с которого пришло соединение:

System.out.println("New connection accepted");

final String name = in.readLine();

out.println(String.format("Hi %s, your port is %d", name, clientSocket.getPort()));
Далее пишем клиента по примеру из презентации. Клиентом должна быть другая программа (просто ещё один метод main в другом классе, запускаемый параллельно, во время работы сервера) или второй поток. Обратите внимание, что хостом подключения будет localhost - это зарезервированный адрес для подключения к текущему компьютеру (то есть это ваш компьютер - там, где запущена программа). Также можно использовать 127.0.0.1 - это ip адрес, соответствующий доменному имени localhost

При проблемах связывайтесь с преподавателем и желаем вам успехов! ;)
