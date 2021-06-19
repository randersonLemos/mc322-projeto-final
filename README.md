# Corridinha da Massa

Corrida da massa é um jogo de corrida em que o jogador personifica um piloto que
participa de uma competição de corrida com obstáculos. Mas essa não é uma
corrida normal, pois a vida do piloto depende dele completar o circuito
que é imprevisível e cheio de perigos. No circuito há obstáculos, sendo alguns
apenas muros intransponíveis enquanto outros labaredas de fogo mortais.
Há também, no circuito, porções mágicas que dotam o carro de habilidades
especiais e que podem ser essenciais para a sobrevivência do piloto.

![Capa](assets/capa.gif)

# Equipe Peixonauta
Pablo Areia Delgado. R.: 223037

Randerson Araújo de Lemos. RA.: 103897

# Vídeos do Projeto
## Vídeo da Prévia
[vídeo](https://www.youtube.com/watch?v=wtWPpYuzdb8)

## Vídeo do Jogo
[vídeo](https://youtu.be/vfONENL0wm4)

# Slides do Projeto
## Slides da Prévia
[apresentação](./assets/previa)

## Slides da Apresentação Final
[apresentação](./assets/final)

# Relatório de Evolução
Relotório de evolução, descrevendo as ecoluções do design do projeto,
dificuldades enfretadas, mudanças de rumo, melhorias e lições aprendidas.
Referênias aos diagramas e recortes de mudanças são bem-vindas

# Destaques de Código
<Escolha trechos relevantes e/ou de destaque do seu código. Apresente
um recorte (você pode usar reticências para remover partes menos importantes).
Veja como foi usado o highlight de Java para o código.>

# Destaques de Pattern
Destaques de patterns adotados pela equipe. Sugestẽs de estutura

## Diagrama do Pattern
Diagrama do pattern dentro do contexto da aplicação

## Código de Pattern
Colocar código e explicação de como o Patterns foi adotado

# Conclusão e Trabalhos Futuros
<Apresente aqui as conclusões do projeto e propostas de trabalho futuro.
Esta é a oportunidade em que você pode indicar melhorias no projeto a partir
de lições aprendidas e conhecimentos adquiridos durante a realização do projeto,
mas que não puderam ser implementadas por questões de tempo. Por exemplo,
há design patterns aprendidos no final do curso que provavelmente não puderam
ser implementados no jogo -- este é o espaço onde você pode apresentar como
oaplicaria o pattern no futuro para melhorar o jogo.>

# Documentação
## Diagramas
### Diagrama Geral do Projeto

![Arquitetura](assets/arquitetura.png)

## Diagrama Geral dos Componentes

## Componente `Painel`

![Painel](assets/Componente_Painel.jpg)

**Ficha Técnica**
item | detalhamento
----- | -----
Classe | [Classe Painel](src/src/mc322/lab07/view/painel/Painel.java)
Autores | `<Pablo e Randerson>`
Interfaces | IPainelConstrutor <br> IPainelControle <br> IRCircuitoPainel <br> IRPilotoPainel

~~~java
public interface IPainel extends
  IPainelConstrutor
, IPainelControle
, IRCircuitoPainel
, IRPilotoPainel
{
}
~~~
## Componente `Elemento`

![Elemento](assets/Componente_Elemento.jpg)

**Ficha Técnica**
item | detalhamento
----- | -----
Classe | [Classe Elemento](src/src/mc322/lab07/model/elemento/Elemento.java)
Autores | `<Pablo e Randerson>`
Interfaces |  IPilotoControle <br> IPilotoConstrutor <br> IPilotoPainel <br> IRCircuitoPiloto

~~~java
public interface IPiloto extends
  IPilotoControle
, IPilotoConstrutor
, IPilotoPainel
, IRCircuitoPiloto
{
}
~~~
## Componente `Circuito`

![Circuito](assets/Componente_Circuito.jpg)

**Ficha Técnica**
item | detalhamento
----- | -----
Classe | [Classe Circuito](src/src/mc322/lab07/model/circuito/Circuito.java)
Autores | `<Pablo e Randerson>`
Interfaces | ICircuitoContrutor <br> ICircuitoControle <br> ICircuitoPainel <br>  ICircuitoPiloto

~~~java
public interface ICircuito extends
  ICircuitoConstrutor
, ICircuitoControle
, ICircuitoPainel
, ICircuitoPiloto{
}
~~~
## Componente `Controle`

![Controle](assets/Componente_Controle.jpg)

**Ficha Técnica**
item | detalhamento
----- | -----
Classe | [Classe Controle](src/src/mc322/lab07/control/controle/Controle.java)
Autores | `<Pablo e Randerson>`
Interfaces | IControleConstrutor <br> IRCircuitoControle <br> IRPilotoControle <br> IRPainelControle

~~~java
public interface IControle extends
  IControleConstrutor
, IRCircuitoControle
, IRPilotoControle
, IRPainelControle
{
	public void comecarJogo();
}
~~~
## Componente `Construtor`

![Construtor](assets/Componente_Construtor.jpg)

**Ficha Técnica**
item | detalhamento
----- | -----
Classe | [Classe Construtor](src/src/mc322/lab07/control/construtor/Construtor.java)
Autores | `<Pablo e Randerson>`
Interfaces | IRCircuitoConstrutor <br> IRControleConstrutor <br> IRPilotoConstrutor <br> IRPainelConstrutor

~~~java
public interface IConstrutor extends
  IRCircuitoConstrutor
, IRControleConstrutor
, IRPilotoConstrutor
, IRPainelConstrutor
{
	public void construir(int maxLin, int maxCol);
}
~~~
## Detalhamento das Interfaces

### Interface `IControleConstrutor`
~~~java
public interface IControleConstrutor {
	Elemento geradorAleatorioDeElementosSemPiloto(int lin, int col);
}
~~~
Método | Objetivo
-------| --------
`geradorAleatorioDeElementosSemPiloto` | Gera um Elemento seguindo certas probabilidades <br> Possibilidades: Asfalto, Muro, Fogo ou Poção

### Interface `ICircuitoContrutor`
Construtor poder criar a matriz do Objeto Circuito (matriz back-end)
~~~java
public interface ICircuitoConstrutor
{
	void setMatriz(int maxLin, int maxCol, Elemento matriz[][]);
}
~~~
Método | Objetivo
-------| --------
`setMatriz` | Atualiza a matriz Circuito

### Interface `ICircuitoControle`
Controle ter acesso a informações sobre a matriz e poder atualizá-la
~~~java
public interface ICircuitoControle {
	public int getMaxLin();
	public int getMaxCol();
	void setElemento(Elemento elemento);
	public Elemento getElemento(int lin, int col);

}
~~~
Método | Objetivo
-------| --------
`getMaxLin` | Acessa o numero de linhas da matriz Circuito
`getMaxCol` | Acessa o numero de colunas da matriz Circuito
`setElemento` | Atualiza uma posição da matriz Circuito (ou seja, um Elemento)
`getElemento` | Acessa uma posição da matriz Circuito (ou seja, um Elemento)

### Interface `ICircuitoPainel`
Interligar as matrizes back-end e front-end
~~~java
public interface ICircuitoPainel
{
	public int getMaxLin();
	public int getMaxCol();
	public Elemento getElemento(int lin, int col);
}
~~~
Método | Objetivo
-------| --------
`getMaxLin` | Acessa o numero de linhas da matriz Circuito
`getMaxCol` | Acessa o numero de colunas da matriz Circuito
`getElemento` | Acessa uma posição da matriz Circuito (ou seja, um Elemento)

### Interface `ICircuitoPiloto`
Piloto e Circuito são independentes no código, o objeto Piloto sabe onde ele está, mas precisa de informações do Circuito para conhecer os arredores
~~~java
public interface ICircuitoPiloto
{
	public int getMaxLin();
	public int getMaxCol();
	public Elemento getElemento(int lin, int col);
}
~~~
Método | Objetivo
-------| --------
`getMaxLin` | Acessa o numero de linhas da matriz Circuito
`getMaxCol` | Acessa o numero de colunas da matriz Circuito
`getElemento` | Acessa uma posição da matriz Circuito (ou seja, um Elemento)

### Interface `IPilotoConstrutor`
Construtor poder criar o Objeto Piloto
~~~java
public interface IPilotoConstrutor {
	public void setPosicao(int lin, int col);
}
~~~
Método | Objetivo
-------| --------
`setPosicao` | Atualiza a posição do piloto (essa informação é guardada no Piloto)

### Interface `IPilotoControle`
Controle poder ter as informações do piloto e poder atualizá-lo
~~~java
public interface IPilotoControle {
	public void moverParaCima();
	public void moverParaBaixo();
	public void moverParaEsquerda();
	public void moverParaDireita();
	public int getLin();
	public int getCol();
	public void setImagemIcon1();
	public void setImagemIcon2();
	public void setImagemIcon3();
	public void setPosicao(int lin, int col);
	public void setPoderzin(int valor);
	public int getPoderzin();
}
~~~
Método | Objetivo
-------| --------
`moverParaCima` | Move o piloto para cima se possível
`moverParaBaixo` | Move o piloto para baixo se possível
`moverParaEsquerda` | Move o piloto para esquerda se possível
`moverParaDireita` | Move o piloto para direita se possível
`getLin` | Acessa a linha que o Elemento está
`getCol` | Acessa a coluna que o Elemento está
`setImagemIcon1,2,3` | Acessam imagens específicas (1,2 ou 3) (arquivos de imagem que serão incrementados na interface gráfica)
`setPosicao` | Atualiza a posição do piloto (essa informação é guardada no Piloto)
`setPoderzin` | Dispara o tempo de duração da poção -> tempo = x;
`getPoderzin` | Acessa o tempo atual restante de duração da poção

### Interface `IPilotoPainel`
O piloto só está inserido na matriz front-end, Painel pega suas informações e atualiza a matriz
~~~java
public interface IPilotoPainel
{
	public int getLin();
	public int getCol();
	public ImageIcon getImageIcon();
}
~~~
Método | Objetivo
-------| --------
`getLin` | Acessa a linha que o Elemento está
`getCol` | Acessa a coluna que o Elemento está
`getImageIcon` | Acessa a imagem de um Elemento (arquivo de imagem que será incrementado na interface gráfica)

### Interface `IPainelConstrutor`
Construtor cria o Objeto Painel (matriz front-end) sobre as condições iniciais do objeto Circuito
~~~java
public interface IPainelConstrutor
{
	public void setMatriz(int maxLin, int maxCol, JLabel matriz[][]);
}
~~~
Método | Objetivo
-------| --------
`setMatriz` | Atualiza a matriz Painel

### Interface `IPainelControle`
Controle ser capaz de atualizar a interface gráfica a cada iteração
~~~java
public interface IPainelControle
{
	public void atualizarPainel();
	public void mostrarPainel();
	public void atualizarImagemCircuitoPainel();
	public void atualizarImagemPilotoPainel();
	public void addPlayActionListener(ActionListener I);
	public void addPlayKeyListener(KeyListener I);
	public void atualizarScore(int valor);
	public void atualizarStatus(String mensagem);
}
~~~
Método | Objetivo
-------| --------
`atualizarPainel` | atualiza o estado do Painel (o que o player vai ver)
`mostrarPainel` | manda mostrar o Painel em seu estado atualizado
`atualizarImagemCircuitoPainel` | atualiza o circuito mostrado do Painel (matirz front-end) a partir do objeto Circuito (matriz back-end)
`atualizarImagemPilotoPainel` | atualiza a posição do Piloto no Painel
`addPlayActionListener` | cria um observador
`addPlayKeyListener` | cria um observador que dispara um evento quando uma tecla é apertada
`atualizarScore` | Atualiza a pontuação do player mostrado no painel
`atualizarStatus` | Atualiza o status do jogo mostrado no painel

## Plano de Exceções

![Hierarquia Exceções](assets/Excecoes.jpg)

## Descrição das classes de exceção

Classe | Descrição
----- | -----
Excecoes | Engloba todas as exceções de divisões não aceitas.
LimiteCircuito | Indica que há acesso a posoções inválidas da matriz
ArquivoImagem | Indica que está recebendo um arquivo de imagem inválido
