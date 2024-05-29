# ponderada_turtlebot_teleop_pt2

Este é um programa Python com uma interface em HTML e visão computacional com o acesso a WebCam para controlar um TurtleBot3 usando o ROS 2 (Robot Operating System). O programa permite controlar o robô usando o teclado os botões dispostos na tela, ajustando a velocidade linear e angular em tempo real e podendo ver a quantidade de FPS e a Latência da comunicação.

# Movimentação do Robô

O controle será feito, tanto pelas teclas de seta como pelos botões no HTML:

Seta para cima: Robo vai para frente 
Seta para baixo: Robo vai para trás 
Seta para direita: Robo gira em torno do seu eixo para a direita 
Seta para esquerda: Robo gira em torno do seu eixo para a esquerda

E na página HTML temos setas também onde pode-se clicar nelas e conseguir movimentar o robo:
![seta para cima](https://github.com/MuriloDeSouza/ponderada_turtlebot_teleop_pt2/blob/main/front/seta-cima.png)
![seta para baixo](https://github.com/MuriloDeSouza/ponderada_turtlebot_teleop_pt2/blob/main/front/seta-baixo.png)
![seta para direita](https://github.com/MuriloDeSouza/ponderada_turtlebot_teleop_pt2/blob/main/front/seta-direita.png)
![seta para esquerda](https://github.com/MuriloDeSouza/ponderada_turtlebot_teleop_pt2/blob/main/front/seta-esquerda.png)

# Pré Requisitos

Certifique-se de ter o ROS 2 instalado no seu sistema. Além disso, é necessário preparar a área de trabalho para trabalhar com o ROS 2.

1. Instale o ROS seguindo as instruções no site oficial: [ROS Installation](http://wiki.ros.org/Installation).

2. Rode esses comando para poder preparar a área do seu pc para funcionar:
(Esse comando serve para poder rodar o WEBOTS que é um ambiente virtual para testar os códigos no Robô)
```cmd
ros2 launch webots_ros2_turtlebot robot_launch.py
```
3. Para poder utilizar o WebSockets e o RosBridge(é uma interface de JSON para ROS. Com ele, é possível usar um servidor de websockets que mapeia toda a sua rede ROS local para ficar disponível em um endpoint com uma API em json.) temos que rodar esse outro comando:
```cmd
sudo apt install ros-humble-rosbridge-suite
```
4. Para rodar o servidor websocket, rode:
```cmd
ros2 launch rosbridge_server rosbridge_websocket_launch.xml
```
5. Para poder instalar todas as dependências do arquivo "requirements.txt" temos que passar o comando abaixo:
```cmd
pip install -r requirements.txt
```

## Instalação do WeBots (ambiente virtual para testes do robô)

Para usar o WeBots, é necessário preparar o ambiente executando os seguintes comandos:

1. Abra o terminal e rode os comandos a seguir:

```bash
sudo apt install ros-humble-navigation2 ros-humble-nav2-bringup ros-humble-turtlebot3*

sudo apt install ros-humble-rmw-cyclonedds-cpp

echo "export RMW_IMPLEMENTATION=rmw_cyclonedds_cpp" >> ~/.bashrc
```
2. Depois de rodar esses comandos:

```bash
sudo mkdir -p /etc/apt/keyrings
cd /etc/apt/keyrings
sudo wget -q https://cyberbotics.com/Cyberbotics.asc
echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/Cyberbotics.asc] https://cyberbotics.com/debian binary-amd64/" | sudo tee /etc/apt/sources.list.d/Cyberbotics.list
```

```bash
sudo apt update
sudo apt install webots
sudo apt install ros-humble-webots-ros2
```

## Executando o Programa

Após preparar o ambiente, você pode executar o programa para controlar a tartaruga no Turtlesim. Execute o seguinte comando no terminal:
(É bem importante estar no local da pasta certa que é (\ponderada_turtlebot_teleop_pt2\back))
```cmd
python3 sender.py
```
Com esse comando você irá conseguir rodar o programa para poder obter a visualização da câmera, seja do robô ou seja da webcam do seu notebook.
Em paralelo a esse cmd, temos que rodar outro para que aconteça as publicações nos tópicos através do WebSockets:
```cmd
ros2 launch rosbridge_server rosbridge_websocket_launch.xml
```
E por fim, podemos rodar a página de HTML no VScode com o auxílio da extensão "Live Share", é só entrar na aba do código, cujo caminhho é: 
(\ponderada_turtlebot_teleop_pt2\front\index.html) e clicar no ícone do LiveShare e logo terá a página de visualização que é identica a essa abaixo:
![Imagem da tela]()

