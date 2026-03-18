Как узнать местонахождение посылки 
 rospack find roscpp
Чтобы перейти к пакету
 roscd roscpp
 roscd roscpp/cmake
 журнал roscd
Как узнать содержимое посылки
 rosls roscpp_tutorials
Чтобы создать рабочее пространство
 catkin_init_workspace
  
Чтобы найти доступные пакеты
 apt-cache search ros-indigo
  
Чтобы создать пакет
 catkin_create_pkg <имя_пакета> [depend1] [depend2] [depend3]
 catkin_create_pkg beginner_tutorials std_msgs rospy roscpp
Для создания пакета
 кошачий мейк
Поиск нового встроенного пакета
 . ~/catkin_ws/devel/setup.bash
Проверка зависимостей пакета
 rospack зависит от1 beginner_tutorials 
  
Ошибка при запуске roscore. Измените права доступа к папке ros, как показано ниже
 sudo chown -R <your_username> ~/.ros

Перечислите все узлы ROS
 список rosnode
Получение информации об узле
 Информация о rosnode /rosout
Rosrun позволяет использовать имя пакета для непосредственного запуска узла внутри пакета 
 rosrun turtlesim turtlesim_node
 rosrun turtlesim turtle_teleop_key
Запущенный узел с пользовательским именем 
 rosrun turtlesim turtlesim_node __name:=my_turtle 
Проверка доступности узла с помощью ping
 rosnode ping my_turtle
  
Установка графика RQT
 sudo apt-get install ros-indego-rqt
Работающий график
 rosrun rqt_graph rqt_graph
  
Помощь в Ростопике
 ростопик -х
 rostopic list -h
Подписка на rostopic 
 rostopic echo /turtle1/cmd_vel
Проверка типа ростовика
 rostopic type /turtle1/cmd_vel
Просмотр деталей сообщения
 rosmsg show geometry_msgs/Twist
Чтобы отобразить тип и сообщение
 rostopic type /turtle1/cmd_vel | rosmsg show

ПУБЛИКАЦИЯ пользовательского сообщения
 rostopic pub [тема] [тип_сообщения] [аргументы]
 rostopic pub -1 /turtle1/cmd_vel geometry_msgs/Twist -- '[2.0, 0.0, 0.0]' '[0.0, 0.0, 1.8]'
  
Публикуйте посты с периодичностью 1 раз в час, чтобы не сбавлять темп
 rostopic pub /turtle1/cmd_vel geometry_msgs/Twist -r 1 -- '[2.0, 0.0, 0.0]' '[0.0, 0.0, -1.8]'
Как быстро узел публикует данные
 rostopic hz /turtle1/pose
Построение графика на основе ростопических данных
 rosrun rqt_plot rqt_plot
  
Список Россервисов
 список россервисов
 россервис - помощь
 вызов /очистить rosservice
 rosservice call /spawn 2 2 0.2 ""
 rosservice type /spawn| rossrv show
  
Rosparam позволяет хранить данные на сервере параметров ROS и управлять ими. Для синтаксиса используется YAML 
 роспарам - справка
 rosparam set /background_r 150
 вызов /очистить rosservice
Список всех данных на сервере rosparam
 роспарам получаем /
 rosparam dump params.yaml
 rosparam загружает файл params.yaml
Загрузка в другое пространство имен и использование 
 rosparam load params.yaml copy
 rosparam get /copy/background_b
  
Запущенная консоль
 rosrun rqt_console rqt_console
 rosrun rqt_logger_level rqt_logger_level
Удар об стену для имитации ошибки
 rostopic pub /turtle1/cmd_vel geometry_msgs/Twist -r 1 -- '{linear: {x: 2.0, y: 0.0, z: 0.0}, angular: {x: 0.0,y: 0.0,z: 0.0}}'
  
Все инструменты rqt
 rqt
Только график
 rq_граф
  
msg: файлы msg — это простые текстовые файлы, в которых описываются поля сообщений ROS. Они используются для генерации исходного кода для сообщений на разных языках.
srv: файл srv описывает сервис. Он состоит из двух частей: запроса и ответа. 

Копирование сервиса из другого пакета в рабочий пакет
 roscp rospy_tutorials AddTwoInts.srv srv/AddTwoInts.srv
  
Отображение сведений о сервисе
 rossrv show <тип услуги>
 rossrv show beinner_tutorials/AddTwoInts
 rossrv show AddTwoInts

Справка по сообщениям ros
 rosmsg -h

Если вы создаете узлы на C++, использующие новые сообщения, вам также нужно будет указать зависимость между узлом и сообщением, как описано в документации по сборке catkin msg/srv.  

Запись опубликованных сообщений
 mkdir ~/файлы пакетов
 cd ~/ файлы пакетов
 rosbag record -a

Получение информации о записанных сообщениях
 Информация о сумке rosbag, имя файла
Воспроизведение сообщений 
 Сумка rosbag play bagfilename 

Использование пакета
роскор
rosrun sound_play soundplay_node.py
rosrun sound_play say.py 'Привет, мир' 
  
echo $ROS_PACKAGE_PATH покажет пути, по которым установлены пакеты ROS
