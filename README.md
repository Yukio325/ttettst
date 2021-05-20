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
$$\begin{bmatrix}
x_1\\ y_1\\ 1\\
\end{bmatrix}=\begin{bmatrix}
1 & 0 & dx\\ 0 & 1 & dy\\ 0 & 0 & 1\\
\end{bmatrix}\cdot\begin{bmatrix}
x_0\\ y_0\\ 1\\
\end{bmatrix}$$
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
$$x'=\begin{bmatrix}
cos(θ)\\
sen(θ)\\
\end{bmatrix},\space\space
y'=\begin{bmatrix}
-sen(θ)\\
cos(θ)\\
\end{bmatrix}\space e\space\space z' = z$$
#### Matriz de rotação do eixo z:
$$R_z(θ) = \begin{bmatrix}
cos(θ) & -sen(θ)\\
sen(θ) & cos(θ)\\
\end{bmatrix}$$
ou
$$\begin{bmatrix}
x_1\\ y_1\\ z_1\\ 1\\
\end{bmatrix} = \begin{bmatrix}
cos\gamma & -sen\gamma & 0 & 0\\
sen\gamma & cos\gamma & 0 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1\\
\end{bmatrix}\cdot
\begin{bmatrix}
x_0\\ y_0\\ z_0\\ 1\\
\end{bmatrix}$$
#### Matriz de rotação do eixo x:
$$\begin{bmatrix}
x_1\\ y_1\\ z_1\\ 1\\
\end{bmatrix} =
\begin{bmatrix}
1 & 0 & 0 & 0\\
0 & \cos\alpha & - \sin\alpha & 0\\
0 & \sin\alpha & \cos\alpha & 0\\
0 & 0 & 0 & 1\\
\end{bmatrix}\cdot
\begin{bmatrix}
x_0\\ y_0\\ z_0\\ 1\\
\end{bmatrix}$$
#### Matriz de rotação do eixo y:

$$\begin{bmatrix}
x_1\\ y_1\\ z_1\\ 1\\
\end{bmatrix} = \begin{bmatrix}
\cos\beta & 0 & \sin\beta & 0\\
0 & 1 & 0 & 0\\
-\sin\beta & 0 & \cos\beta & 0\\
0 & 0 & 0 & 1\\
\end{bmatrix}\cdot
\begin{bmatrix}
x_0\\ y_0\\ z_0\\ 1\\
\end{bmatrix}$$
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
- Velocidades angulares das duas rodas ($w_l, w_r$) ;
- Distância entre as rodas e o eixo ($L$);
- O raio da roda ($r$);

O robô será representado como um único ponto (corpo rígido) que, para facilitar, será coincidente com o ponto médio do eixo das rodas.

Por convenção, definimos os eixos x e z, respectivamente, alinhados com a frente do robô e com o eixo z do frame inercial.

### Propriedades do ponto
Deslocamentos Translacional e Rotacional que resultam, respectivamente, nas velocidades **linear** (alocado ao eixo x do robô)
e **angular** (realizada unicamente pelo eixo z, que permanece estático durante a rotação).

Ambas as velocidades são relacionadas entre si pela expressão:   $\space v = R\cdot w$

A velocidade linear do robô, isoladamente, ocorrerá quando as velocidades de ambas as rodas forem iguais.

Já a velocidade angular do robô, ocorrerá quando as velocidades das rodas forem diferentes.

Por sua vez, a velocidade do ponto médio será a média aritmética da velocidade das rodas: $$v = \dfrac{r}{2}\cdot(w_r+w_l)$$
E a velocidade angular do ponto médio se dá pela relação: $$w = \dfrac r{2\cdot L}\cdot(w_r-w_l)$$

### Estratégias de controle
1. **Planejar primeiro as velocidades independentes das rodas e depois combiná-las para obter as velocidades do robô.**
2. **Planejar as velocidades do robô logo de início, e depois convertê-la para as rodas de forma que o motor aja de acordo.**

### Conversão de velocidades para o frame inercial/global
Esse processo ocorre por meio da decomposição vetorial do frame do robô em relação ao frame inercial, de acordo com sua orientação (θ),
ou seja:
$$\begin{bmatrix}
vx\\ vy\\ w\\
\end{bmatrix}=
\begin{bmatrix}
v\cdot\cos\theta\\ v\cdot\sin\theta\\ w\\
\end{bmatrix}$$	
Observe que a velocidade angular permanece a mesma, uma vez que o eixo z do robô sempre está alinhado com o eixo z inercial.

Reescrevendo as equações, temos:
$$V=P'=\begin{bmatrix}
\dot{X}_i \\ \dot{Y}_i \\ \dot{\theta}_i \\
\end{bmatrix}=
\begin{bmatrix}
\cos\theta_i & 0\\ \sin\theta_i & 0\\ 0 & 1\\
\end{bmatrix}\cdot
\begin{bmatrix}
v\\ w\\
\end{bmatrix}$$
### Obtendo a posição a partir da velocidade
Decompondo as velocidades do frame inicial, temos:
$$V_t=\dot{P}_t=\begin{bmatrix}
V_{x,t}\\ V_{y,t}\\ w_t\\
\end{bmatrix}=\begin{bmatrix}
v\cdot\cos\theta_{t-1}\\ v\cdot\sin\theta_{t-1}\\ w_t\\
\end{bmatrix}$$
E então é feita a integração (soma) de cada componente no robô:
$$P_t=P{t-1}+\dot{P}_t\times dt$$
