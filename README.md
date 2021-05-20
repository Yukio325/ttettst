# Documentação Robótica Móvel

Se amanhã alguém entrar no **VSSS**, o que ele precisa saber?
## Introdução

### História da Robótica
- Como foi a evolução da robótica?
- Conhecer os erros do passado.
- Bonecas Karakuri
- Contos do Gigante Talos

#### Sensores
**Proprioceptivos e Exteroceptivos**
Como:
- Encoder,
- Giroscópio,
- Acelerômetro,
- GPS, 
- Sensores de distância(sonares e a laser).

#### Meios de locomoção
Como: 
- Rodas,
- Pernas,
- Esteiras
-  Hélices.

### Onde se insere a robótica
Contexto de Automação;
Frederick Taylor;
Henry Ford;
Unimate.

## Aula 1
### Sistemas de coordenadas (referencial)
**Frame:** ``sistema de coordenadas geométricas usadas como referência.``

**Regra da mão direita:**``indica um plano tridimensional (três frames).``

É o movimento de sistemas de coordenadas através do espaço, já que os objetos serão generalizados por um sistema de coordenadas.

### Ferramentas utilizadas para a movimentação dos objetos:

#### Translação
Deslocamento de um frame pelo espaço sem que ocorra a alteração da orientação de seus eixos, ou a adição de uma "quantidade" no eixo em que o movimento é desejado.

#### Aplicação de matrizes na robótica:
**Sistema matricial**:

![equation](https://latex.codecogs.com/gif.latex?%5Ccolor%7BCyan%7D%20%5Cbegin%7Bbmatrix%7D%20x_1%5C%5C%20y_1%5C%5C%201%5C%5C%20%5Cend%7Bbmatrix%7D%3D%5Cbegin%7Bbmatrix%7D%201%20%26%200%20%26%20dx%5C%5C%200%20%26%201%20%26%20dy%5C%5C%200%20%26%200%20%26%201%5C%5C%20%5Cend%7Bbmatrix%7D%5Ccdot%5Cbegin%7Bbmatrix%7D%20x_0%5C%5C%20y_0%5C%5C%201%5C%5C%20%5Cend%7Bbmatrix%7D)
#### Rotação
Operações matemáticas de mudança de orientação nos eixos cartesianos do sistema de referência sem mudar
a posição do eixo de referência.

Três tipos de rotação:
	 **Roll**(x), **Pitch**(y), **Yaw**(z).

Ocorre ao **"Segurar"** um dos eixos e provocar uma **"torção"** nele de modo que a origem e o eixo de rotação permanecem no mesmo lugar, enquanto os outros eixos mudam de posição.

#### Sentido da Rotação

**Regra da mão direita rotacional:** 
Sentidos Positivo (*Anti-horário*) e Negativo (*Horário*).

Após a rotação obtemos que:

![equation](https://latex.codecogs.com/gif.latex?%5Ccolor%7BCyan%7D%20x%27%3D%5Cbegin%7Bbmatrix%7D%20cos%28%5Ctheta%29%5C%5C%20sen%28%5Ctheta%29%5C%5C%20%5Cend%7Bbmatrix%7D%2C%20%5C%20y%27%3D%5Cbegin%7Bbmatrix%7D%20-sen%28%5Ctheta%29%5C%5C%20cos%28%5Ctheta%29%5C%5C%20%5Cend%7Bbmatrix%7D%20e%20%5C%20z%27%20%3D%20z)
#### Matriz de rotação do eixo z:

![equation](https://latex.codecogs.com/gif.latex?%5Ccolor%7BCyan%7D%20R_z%28%5Ctheta%29%20%3D%20%5Cbegin%7Bbmatrix%7D%20cos%28%5Ctheta%29%20%26%20-sen%28%5Ctheta%29%5C%5C%20sen%28%5Ctheta%29%20%26%20cos%28%5Ctheta%29%5C%5C%20%5Cend%7Bbmatrix%7D)

ou

![equation](https://latex.codecogs.com/gif.latex?%5Ccolor%7BCyan%7D%20%5Cbegin%7Bbmatrix%7D%20x_1%5C%5C%20y_1%5C%5C%20z_1%5C%5C%201%5C%5C%20%5Cend%7Bbmatrix%7D%20%3D%20%5Cbegin%7Bbmatrix%7D%20cos%5Cgamma%20%26%20-sen%5Cgamma%20%26%200%20%26%200%5C%5C%20sen%5Cgamma%20%26%20cos%5Cgamma%20%26%200%20%26%200%5C%5C%200%20%26%200%20%26%201%20%26%200%5C%5C%200%20%26%200%20%26%200%20%26%201%5C%5C%20%5Cend%7Bbmatrix%7D%5Ccdot%20%5Cbegin%7Bbmatrix%7D%20x_0%5C%5C%20y_0%5C%5C%20z_0%5C%5C%201%5C%5C%20%5Cend%7Bbmatrix%7D)
#### Matriz de rotação do eixo x:

![equation](https://latex.codecogs.com/gif.latex?%5Ccolor%7BCyan%7D%20%5Cbegin%7Bbmatrix%7D%20x_1%5C%5C%20y_1%5C%5C%20z_1%5C%5C%201%5C%5C%20%5Cend%7Bbmatrix%7D%20%3D%20%5Cbegin%7Bbmatrix%7D%201%20%26%200%20%26%200%20%26%200%5C%5C%200%20%26%20%5Ccos%5Calpha%20%26%20-%20%5Csin%5Calpha%20%26%200%5C%5C%200%20%26%20%5Csin%5Calpha%20%26%20%5Ccos%5Calpha%20%26%200%5C%5C%200%20%26%200%20%26%200%20%26%201%5C%5C%20%5Cend%7Bbmatrix%7D%5Ccdot%20%5Cbegin%7Bbmatrix%7D%20x_0%5C%5C%20y_0%5C%5C%20z_0%5C%5C%201%5C%5C%20%5Cend%7Bbmatrix%7D)
#### Matriz de rotação do eixo y:

![equation](https://latex.codecogs.com/gif.latex?%5Ccolor%7BCyan%7D%20%5Cbegin%7Bbmatrix%7D%20x_1%5C%5C%20y_1%5C%5C%20z_1%5C%5C%201%5C%5C%20%5Cend%7Bbmatrix%7D%20%3D%20%5Cbegin%7Bbmatrix%7D%20%5Ccos%5Cbeta%20%26%200%20%26%20%5Csin%5Cbeta%20%26%200%5C%5C%200%20%26%201%20%26%200%20%26%200%5C%5C%20-%5Csin%5Cbeta%20%26%200%20%26%20%5Ccos%5Cbeta%20%26%200%5C%5C%200%20%26%200%20%26%200%20%26%201%5C%5C%20%5Cend%7Bbmatrix%7D%5Ccdot%20%5Cbegin%7Bbmatrix%7D%20x_0%5C%5C%20y_0%5C%5C%20z_0%5C%5C%201%5C%5C%20%5Cend%7Bbmatrix%7D)
# Aula 2
## Tipos de robôs
- Modelo de Ackerman
- ### Robô Diferencial
**Exemplos**: VSSS, Robótica Assistiva, Robótica de Exploração (Esteiras).

Possui duas rodas motorizadas e independentes e uma roda não motorizada cuja função é a sustentação e estabilidade estática.

Representação por planta baixa (visão superior/2D).

Sua posição é definida pelas coordenadas nos eixos x e y.

É importante definir sua orientação! (Relativa ao seu frame inercial).
### Parâmetros do robô
- Velocidades angulares das duas rodas (wl, wr) ;
- Distância entre as rodas e o eixo (L);
- O raio da roda (r);

O robô será representado como um único ponto (corpo rígido) que, para facilitar, será coincidente com o ponto médio do eixo das rodas.

Por convenção, definimos os eixos x e z, respectivamente, alinhados com a frente do robô e com o eixo z do frame inercial.

### Propriedades do ponto
Deslocamentos Translacional e Rotacional que resultam, respectivamente, nas velocidades **linear** (alocado ao eixo x do robô)
e **angular** (realizada unicamente pelo eixo z, que permanece estático durante a rotação).

Ambas as velocidades são relacionadas entre si pela expressão:   ![equation](https://latex.codecogs.com/gif.latex?%5Ccolor%7BCyan%7D%20%5Cspace%20v%20%3D%20R%5Ccdot%20w)

A velocidade linear do robô, isoladamente, ocorrerá quando as velocidades de ambas as rodas forem iguais.

Já a velocidade angular do robô, ocorrerá quando as velocidades das rodas forem diferentes.

Por sua vez, a velocidade do ponto médio será a média aritmética da velocidade das rodas:

![equation](https://latex.codecogs.com/gif.latex?%5Ccolor%7BCyan%7D%20v%20%3D%20%5Cdfrac%7Br%7D%7B2%7D%5Ccdot%28w_r&plus;w_l%29)

E a velocidade angular do ponto médio se dá pela relação:

![equation](https://latex.codecogs.com/gif.latex?%5Ccolor%7BCyan%7D%20w%20%3D%20%5Cdfrac%20r%7B2%5Ccdot%20L%7D%5Ccdot%28w_r-w_l%29)
### Estratégias de controle
1. **Planejar primeiro as velocidades independentes das rodas e depois combiná-las para obter as velocidades do robô.**
2. **Planejar as velocidades do robô logo de início, e depois convertê-la para as rodas de forma que o motor aja de acordo.**

### Conversão de velocidades para o frame inercial/global
Esse processo ocorre por meio da decomposição vetorial do frame do robô em relação ao frame inercial, de acordo com sua orientação (θ),
ou seja:

![equation](https://latex.codecogs.com/gif.latex?%5Ccolor%7BCyan%7D%20%5Cbegin%7Bbmatrix%7D%20vx%5C%5C%20vy%5C%5C%20w%5C%5C%20%5Cend%7Bbmatrix%7D%3D%20%5Cbegin%7Bbmatrix%7D%20v%5Ccdot%5Ccos%5Ctheta%5C%5C%20v%5Ccdot%5Csin%5Ctheta%5C%5C%20w%5C%5C%20%5Cend%7Bbmatrix%7D)

Observe que a velocidade angular permanece a mesma, uma vez que o eixo z do robô sempre está alinhado com o eixo z inercial.

Reescrevendo as equações, temos:

![equation](https://latex.codecogs.com/gif.latex?%5Ccolor%7BCyan%7D%20V%3D%5Cdot%7BP%7D%3D%5Cbegin%7Bbmatrix%7D%20%5Cdot%7BX%7D_i%20%5C%5C%20%5Cdot%7BY%7D_i%20%5C%5C%20%5Cdot%7B%5Ctheta%7D_i%20%5C%5C%20%5Cend%7Bbmatrix%7D%3D%20%5Cbegin%7Bbmatrix%7D%20%5Ccos%5Ctheta_i%20%26%200%5C%5C%20%5Csin%5Ctheta_i%20%26%200%5C%5C%200%20%26%201%5C%5C%20%5Cend%7Bbmatrix%7D%5Ccdot%20%5Cbegin%7Bbmatrix%7D%20v%5C%5C%20w%5C%5C%20%5Cend%7Bbmatrix%7D)
### Obtendo a posição a partir da velocidade
Decompondo as velocidades do frame inicial, temos:

![equation](https://latex.codecogs.com/gif.latex?%5Ccolor%7BCyan%7D%20V_t%3D%5Cdot%7BP%7D_t%3D%5Cbegin%7Bbmatrix%7D%20V_%7Bx%2Ct%7D%5C%5C%20V_%7By%2Ct%7D%5C%5C%20w_t%5C%5C%20%5Cend%7Bbmatrix%7D%3D%5Cbegin%7Bbmatrix%7D%20v%5Ccdot%5Ccos%5Ctheta_%7Bt-1%7D%5C%5C%20v%5Ccdot%5Csin%5Ctheta_%7Bt-1%7D%5C%5C%20w_t%5C%5C%20%5Cend%7Bbmatrix%7D)

E então é feita a integração (soma) de cada componente no robô:

![equation](https://latex.codecogs.com/gif.latex?%5Ccolor%7BCyan%7D%20P_t%3DP_%7Bt-1%7D&plus;%5Cdot%7BP%7D_t%5Ctimes%20dt)
