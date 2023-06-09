# Documentação (fiz com Turtlesim por não ter conseguido instalar o ambiente de simulação no meu Mac)

No projeto, mostro como controlar a movimentação da tartaruga do Turtlesim por meio de publicações nos tópicos do ROS. Fiz o desenho de labirinto, mostrando que tenho total controle sobre a movimentação da tartaruga.

Primeiramente, criei um ros2 workspace organizar melhor o ambiente de desenvolvimento. Depois criei uma package que movimenta a tartaruga. Nos próximos parágrafos está uma explicação mais detalhada do arquivo /ros2_ws/src/my_turtle_controller/my_turtle_controller/ros.py.

Este é um código Python que usa a biblioteca ROS (Robot Operating System) para criar, controlar e mover tartarugas virtuais no ambiente Turtlesim. O código começa importando as bibliotecas necessárias: rclpy, que é a biblioteca principal do ROS para Python; Node da biblioteca rclpy.node; Twist da biblioteca geometry_msgs.msg; time da biblioteca padrão Python; SetPen, TeleportAbsolute e Kill da biblioteca turtlesim.srv.

Em seguida, é definida a classe TurtleController que herda de Node. O construtor da classe recebe um parâmetro turtleName, que é o nome da tartaruga, e salva este nome em uma variável self.turtleName.

A classe TurtleController possui quatro métodos:

O método spawn_turtle cria a tartaruga virtual no ambiente Turtlesim, usando o serviço Spawn. Ele recebe dois parâmetros opcionais, x e y, que representam as coordenadas da tartaruga no ambiente. O método também cria um cliente para o serviço Kill, para que a tartaruga possa ser deletada depois que ela terminar de se mover.
O método move_turtle recebe seis parâmetros opcionais: x, y e z representam a velocidade linear da tartaruga nos eixos x, y e z, respectivamente; ax, ay e az representam a velocidade angular da tartaruga nos eixos x, y e z, respectivamente; e times representa o número de vezes que a tartaruga deve se mover. O método cria um objeto do tipo Twist para representar a mensagem Twist que será enviada para mover a tartaruga. Depois, o método publica esta mensagem no tópico "/{self.turtleName}/cmd_vel", que é o tópico que a tartaruga escuta para se mover.
O método pen_color define a cor da caneta da tartaruga virtual usando o serviço SetPen. Ele recebe dois parâmetros: rgb, que representa a cor da caneta em formato RGB (uma lista com três valores inteiros entre 0 e 255); e width, que representa a largura da caneta em pixels. O método cria um objeto do tipo SetPen.Request e preenche seus campos com os valores recebidos como parâmetro. Depois, o método chama o serviço SetPen com esta mensagem.
O método delete_turtle deleta a tartaruga virtual do ambiente Turtlesim, usando o serviço Kill. Ele não recebe parâmetros.

O método main inicia o ROS usando o método rclpy.init(), cria uma tartaruga que realiza as pinturas, e depois desliga o ROS usando o método rclpy.shutdown().

Link para o vídeo do projeto funcionando:
https://youtu.be/u-LGBtRo7Fo
