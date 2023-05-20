# dzROS
Домашняя работа по ROS. Носов, Макрушин, Смирнов.
# Запуск модели
1. Скачанный zip-файл распаковать в папку ~/catkin_ws/src
2. Так как управление симулятором робота осуществляется с помощью пакета turtlebot3_teleop, необходимо клонировать репозиторий в ~/catkin_ws/src, введя следующие команды в терминал:

`cd ~/catkin_ws/src`

`git clone https://github.com/ROBOTIS-GIT/turtlebot3`

 А также выполнить следующую команду:

`sudo apt-get install ros-noetic-turtlebot3-msgs`

3. Открыть в текстовом редакторе файл по следующему пути: ~/catkin_ws/src/turtlebot3/turtlebot3_teleop/nodes/turtlebot3_teleop_key.py

4. В первой строке кода внести следующие правки:

было:
`#!/usr/bin/env python`

должно стать после правки:
`#!/usr/bin/env python3`

5. В терминале ввести следующие команды, чтобы скомпилировать пакет, после внесения изменений:

`cd ~/catkin_ws`

`catkin_make`

6. Открыть новую вкладку в терминале, запустить ros, выполнив следующую команду:

`roscore`

7. Открыть новую вкладку в терминале, выполнить запуск управления симулятором робота с помощью команды:

`export TURTLEBOT3_MODEL=waffle; roslaunch turtlebot3_teleop  turtlebot3_teleop_key.launch`

8. Открыть новую вкладку в терминале, выполнить запуск узла для симуляции дифференциального робота:

`rosrun differential_robot dif_sim_node.py`

9. Открыть новую вкладку в терминале, выполнить запуск среды моделирования rviz:

`rosrun rviz rviz`

10. Для подключения отрисовки траектории в rviz необходимо выполнить следующие шаги: в левом нижнем углу нажать кнопку `Add`, в появившемся окне выбрать вкладку `By topic`, в ней выбрать Path во вкладке /path, в разделе `Global Options` во вкладке `Fixed Frames` заменить значение `map` на значение `path`.

# Работа с моделью

 Управление моделью производится через вкладку терминала, в которой выполнялся пункт 7 прошлого раздела. При этом в rviz отрисовывается траектория движения робота, а во вкладке терминала, в которой выполнялся пункт 8 прошлого раздела, выводятся показания энкодеров и координаты робота. Также данные энкодеров публикуются в топик `encoder_val`, а данные одометрии в топик `odom`.
 
 Скрин рабочего пространства среды rviz с отрисованной траекторией:
 
 ![Рабочее окно rviz](https://github.com/SnarBrigada8/dzROS/blob/main/rviz.png)
