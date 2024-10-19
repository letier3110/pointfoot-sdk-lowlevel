# Інструкція з використання LimX SDK

## 1. Налаштування середовища розробки

На комп'ютері розробника алгоритмів ми рекомендуємо створити середовище розробки алгоритмів на базі ROS Noetic на операційній системі Ubuntu 20.04. ROS надає ряд інструментів та бібліотек, таких як основні бібліотеки, комунікаційні бібліотеки та інструменти симуляції (наприклад, Gazebo), що значно полегшує розробку, тестування та розгортання алгоритмів для роботів. Ці ресурси забезпечують користувачів багатим і повним середовищем для розробки алгоритмів.

Звичайно, навіть якщо у вас немає ROS, ви можете розробляти власні алгоритми керування рухом у інших середовищах. Ми надаємо інтерфейс для розробки алгоритмів керування рухом, який є SDK на основі стандартного C++11 і Python та не має залежностей. Він підтримує виклики на різних операційних системах і платформах, надаючи розробникам більш гнучкі можливості.

Для установки ROS Noetic зверніться до документації: https://wiki.ros.org/noetic/Installation/Ubuntu та виберіть “ros-noetic-desktop-full” для встановлення. Після завершення установки ROS Noetic введіть наступні команди Shell у терміналі Bash для встановлення бібліотек, від яких залежить середовище розробки:

```
sudo apt-get update
sudo apt install ros-noetic-urdf \
                 ros-noetic-kdl-parser \
                 ros-noetic-urdf-parser-plugin \
                 ros-noetic-hardware-interface \
                 ros-noetic-controller-manager \
                 ros-noetic-controller-interface \
                 ros-noetic-controller-manager-msgs \
                 ros-noetic-control-msgs \
                 ros-noetic-ros-control \
                 ros-noetic-gazebo-* \
                 ros-noetic-rqt-gui \
                 ros-noetic-rqt-controller-manager \
                 ros-noetic-plotjuggler* \
                 cmake build-essential libpcl-dev libeigen3-dev libopencv-dev libmatio-dev \
                 python3-pip libboost-all-dev libtbb-dev liburdfdom-dev liborocos-kdl-dev -y
```

## 2. Створення робочого простору

Ви можете створити робочий простір для розробки алгоритмів, виконавши наступні кроки:

- Відкрийте термінал Bash.

- Створіть нову директорію для зберігання робочого простору. Наприклад, ви можете створити директорію під назвою “limx_ws” у домашній директорії користувача:

  ```
  mkdir -p ~/limx_ws/src
  ```

- Завантажте інтерфейс для розробки алгоритмів керування рухом:

  ```
  cd ~/limx_ws/src
  git clone https://github.com/limxdynamics/pointfoot-sdk-lowlevel.git
  ```

- Завантажте симулятор Gazebo:

  ```
  cd ~/limx_ws/src
  git clone https://github.com/limxdynamics/pointfoot-gazebo-ros.git
  ```

- Завантажте файли опису моделі робота:

  ```
  cd ~/limx_ws/src
  git clone https://github.com/limxdynamics/robot-description.git
  ```

- Завантажте інструменти для візуалізації та налагодження

  ```
  cd ~/limx_ws/src
  git clone https://github.com/limxdynamics/robot-visualization.git
  ```

- Скомпілюйте проект:

  ```
  cd ~/limx_ws
  catkin_make install
  ```


## 3. Інтерфейс для розробки алгоритмів керування рухом на Python

### 3.1 Огляд

Ми надаємо [інтерфейс для розробки алгоритмів керування рухом на Python](https://github.com/limxdynamics/pointfoot-sdk-lowlevel/tree/master/python3), що має ті самі функції, що і інтерфейс на C++, що дозволяє розробникам, які не знайомі з мовою програмування C++, використовувати Python для розробки алгоритмів керування рухом. Мова програмування Python легко вивчити, вона має простий і зрозумілий синтаксис та багатий набір сторонніх бібліотек, що дозволяє розробникам швидше освоїтися і швидко реалізувати алгоритми. Завдяки інтерфейсу на Python розробники можуть використовувати динамічні властивості Python для швидкого прототипування та верифікації, прискорюючи процес ітерації та оптимізації алгоритмів. Крім того, крос-платформеність та потужна екосистема Python підтримують ширше застосування алгоритмів керування рухом на різних платформах та в різних середовищах. Крім того, швидке розгортання моделей RL (підкріпленого навчання) у симуляційних та реальних середовищах також завдячує гнучкості Python, що дозволяє розробникам легко інтегрувати моделі RL у різні симуляційні платформи та реальне обладнання, здійснюючи швидку ітерацію та верифікацію продуктивності алгоритмів.

### 3.2 Установлення бібліотеки для розробки алгоритмів керування рухом

Використовуйте відповідні команди залежно від операційної системи:

- Платформа Linux x86_64

  ```Bash
  pip install python3/amd64/limxsdk-*-py3-none-any.whl
  ```

- Платформа Linux aarch64

  ```Bash
  pip install python3/aarch64/limxsdk-*-py3-none-any.whl
  ```

- Платформа Windows

  ```Bash
  pip install python3/win/limxsdk-*-py3-none-any.whl
  ```

### 3.3 Приклад використання

Приклад використання інтерфейсу на Python: https://github.com/limxdynamics/pointfoot-sdk-lowlevel/blob/master/python3/amd64/example.py
