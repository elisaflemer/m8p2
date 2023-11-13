# ponderada 2, módulo 8

Este repositório contém um pacote ROS2 desenvolvido como parte da segunda ponderada do módulo 8 do curso de Engenharia da Computação. O objetivo desta atividade é realizar mapeamento e navegação em um ambiente simulado no Gazebo, utilizando o Nav2.

## Conteúdo do workspace

### Pacote "mapear"

Este pacote contém o lançador para realizar o mapeamento, utilizando nós e lançadores preexistentes para teleop, Rviz e Gazebo. Nenhuma implementação adicional foi feita neste pacote.

### Pacote "andar"

O pacote "andar" é responsável por lançar quatro nós para controle e navegação programática do robô, além do Gazebo e Rviz. Os nós incluem:

1. `init_pose`: Inicializa a pose no Nav2.
2. `terminal_pontos`: Permite o envio de pontos para navegação.
3. `fila`: Implementa um nó de fila para gerenciar a ordem dos pontos a serem percorridos.
4. `navegador`: Utiliza o Simple Commander para controlar o robô programaticamente.

## Como Rodar

Siga as instruções abaixo para clonar o repositório, construir o workspace e executar as funcionalidades de mapeamento e navegação.

1. Clone o repositório:

    ```bash
    git clone https://github.com/elisaflemer/m8p2
    ```

2. Construa o workspace:

    ```bash
    cd ws
    colcon build
    source install/setup.bash
    ```

### Para Mapear

3. Execute o lançador para mapeamento:

    ```bash
    ros2 launch mapear map_launch.py
    ```

4. Após realizar o mapeamento, salve o mapa com o seguinte comando, em outro terminal:

    ```bash
    ros2 run nav2_map_server map_saver_cli -f caminho/para/salvar/mapa
    ```

### Para Navegar

5. Adicione o mapa gerado na pasta do lançador com os nomes `map.yaml` e `map.pgm`.

6. Execute o lançador para navegação:

    ```bash
    ros2 launch andar navigator_launch.py
    ```

Agora o robô deverá navegar pelo ambiente simulado utilizando o mapa previamente gerado. Envie os pontos pelo terminal aberto.

## Demo

Um vídeo está disponível neste repo com o nome "p2.mp4"
