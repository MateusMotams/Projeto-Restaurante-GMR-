# Reserva de Mesas Para Restaurante



<p align="center">
    <a href="#sobre">Sobre </a> *
    <a href="#funções"> Funções </a> *
    <a href="#instalação"> Instalação </a> *
    <a href="#feedback"> Feedback </a> *
    <a href="#tecnologias"> Tecnologias </a> *
    <a href="#features"> Features </a> *
    <a href="#colaboradores"> Colaboradores </a> *
</P>

<h4 align="center">
    🚧 Projeto em Construção... 🚧
</h4>

# Sobre

Solução para reserva de mesas no comércio de varejo alimentício.

Metodologia usada para a criação da aplicação foi prototipagem rápida , que é uma coleção de técnicas formais e informais para desenvolvimento ,desmostração e avaliação do design de interfaces de úsuarios , que dá suporte a interações rápidas.
 


# Funções

<h3 align="center">Algumas funções implementadas na aplicação.</h3>


<h4>Chamada da função para verirficar se a mesa está livre .</h4>


```
 public static void reservarMesa(Mesa matMesa[][], int linha, int coluna){
        
        if(mesaLivre(matMesa, linha, coluna) == true){ 
            matMesa[linha][coluna].setReserva(true);
            matMesa[linha][coluna].setEstadoAtual(RESERVADA);
        }else{
            System.out.println("\nErro: A mesa nao pode ser reservada no momento!\n");
        }
    }
```
<h4 align="center">Função verirficar se a mesa está livre em execução.</h4>

<p align="center">
    <img align="center" src="https://user-images.githubusercontent.com/81472331/131894549-c52ca7b4-f1df-4866-be37-358f97ccbb40.gif">
    </img>
</p>

<h4>Chamada da função para a reserva de uma mesa .</h4>

```
public static void reservarMesa(Mesa matMesa[][], int linha, int coluna){
    
    if(mesaLivre(matMesa, linha, coluna) == true){ 
        matMesa[linha][coluna].setReserva(true);
        matMesa[linha][coluna].setEstadoAtual(RESERVADA);
    }else{
        System.out.println("\nErro: A mesa nao pode ser reservada no momento!\n");
    }
}

```
<h4 align="center">Função de reserva de mesa em excução.</h4>

<p align="center">
    <img src="https://user-images.githubusercontent.com/81472331/131895068-f7cd9b86-dc2f-4f36-85d3-1a74cde3ed93.gif">
</p>

<h4>Chamada da função que faz a principal função do codigo, promove distanciamento das mesas.</h4>


```
public static void distanciamentoMesa(Mesa matMesa[][], int numeroMesa){ 
        int i, j;
       
        if(numeroMesa >= 1 && numeroMesa <= 30){ // este if chega se o número da mesa está entre 1 e 30, caso não esteja uma mensagem de erro será mostrada
            for(i = 0; i < 5; i++){
                 for(j = 0; j < 6; j++){
                     
                     if (matMesa[i][j].getEstadoAtual() != SEGURANÇA && matMesa[i][j].getNumeroMesa() == numeroMesa){
                         
                        switch (j){
                            case 0:
                                if (matMesa[i][j].getNumeroMesa() == numeroMesa){
                                    
                                    if (numeroMesa == 1){ 
                                        matMesa[i][(j + 1)].setEstadoAtual(SEGURANÇA);//bloquear mesa seguinte
                                        matMesa[i+1][j].setEstadoAtual(SEGURANÇA);//bloquear mesa inferior
                                    }
                                    
                                    else if (numeroMesa == 25){
                                        matMesa[i-1][j].setEstadoAtual(SEGURANÇA);//bloquear mesa superior
                                        matMesa[i][j+1].setEstadoAtual(SEGURANÇA);//bloquear mesa seguinte
                                     
                                    } else {
                                        matMesa[i-1][j].setEstadoAtual(SEGURANÇA);//bloquear mesa superior
                                        matMesa[i][(j + 1)].setEstadoAtual(SEGURANÇA);//bloquear mesa seguinte
                                        matMesa[(i + 1)][j].setEstadoAtual(SEGURANÇA);//bloquear mesa inferior
                                    }
                                }
                                break;
                            case 5:
                                if (matMesa[i][j].getNumeroMesa() == numeroMesa){
                                    if (numeroMesa == 6){
                                        matMesa[i][(j - 1)].setEstadoAtual(SEGURANÇA);//bloquear mesa anterior
                                        matMesa[i+1][j].setEstadoAtual(SEGURANÇA);//bloquear mesa inferior
                                    }
                                    else if (numeroMesa == 30){
                                        matMesa[i-1][j].setEstadoAtual(SEGURANÇA);//bloquear mesa superior
                                        matMesa[i][j-1].setEstadoAtual(SEGURANÇA);//bloquear mesa anterior
                                    } else {
                                        matMesa[i-1][j].setEstadoAtual(SEGURANÇA);//bloquear mesa superior
                                        matMesa[i][(j + 1)].setEstadoAtual(SEGURANÇA);//bloquear mesa seguinte
                                        matMesa[(i + 1)][j].setEstadoAtual(SEGURANÇA);//bloquear mesa inferior
                                    }
                                }
                                break;
                        }
                        switch (i){
                            case 0:
                                if ((j > 0 && j < 5) && matMesa[i][j].getNumeroMesa() == numeroMesa){
                                    matMesa[i][j-1].setEstadoAtual(SEGURANÇA);
                                    matMesa[i+1][(j)].setEstadoAtual(SEGURANÇA);
                                    matMesa[i][j+1].setEstadoAtual(SEGURANÇA);
                                }
                                break;
                                // o mesmo acontece com a linha 4, com a diferença das posições das mesas
                            case 4:
                                if ((j > 0 && j < 5) && matMesa[i][j].getNumeroMesa() == numeroMesa){
                                    matMesa[i][j-1].setEstadoAtual(SEGURANÇA);
                                    matMesa[i-1][j].setEstadoAtual(SEGURANÇA);
                                    matMesa[i][j+1].setEstadoAtual(SEGURANÇA);
                                }
                                break;
                        }
                        if((j != 0 && j != 5) && (i != 0 && i != 4) && matMesa[i][j].getNumeroMesa() == numeroMesa){
                            matMesa[i][(j - 1)].setEstadoAtual(SEGURANÇA);
                            matMesa[i][(j + 1)].setEstadoAtual(SEGURANÇA);
                            matMesa[(i + 1)][j].setEstadoAtual(SEGURANÇA);
                            matMesa[(i - 1)][j].setEstadoAtual(SEGURANÇA);
                        }
                    }
                }
            }
        } else{
            System.out.println("\nErro: O numero de mesa digitado é invalido!\n");
        }
    } 

```
<h4 align="center">Após a função mesa ocupada ser chamada , principal função do codigo executada. </h4>

<p align="center">
    <img src="https://user-images.githubusercontent.com/81472331/131895548-1b819e4e-f011-4050-967b-f09be4124024.gif">
</p>

<h4>Chamada da função que faz a ocupação da mesa desejada.</h4>

```
public static void ocuparMesa(Mesa matMesa[][], int numeroMesa){
        int i, j;
        
        if(numeroMesa >= 1 && numeroMesa <= 30){ 
            for(i = 0; i < 5; i++){
                for(j = 0; j < 6; j++){

                    if(matMesa[i][j].getNumeroMesa() == numeroMesa){
                        if(mesaLivre(matMesa, i, j) == true){
                            matMesa[i][j].setEstadoAtual(OCUPADA);
                            distanciamentoMesa(matMesa, numeroMesa);
                            break;

                        } else if (matMesa[i][j].isReserva() == true){
                            matMesa[i][j].setEstadoAtual(OCUPADA);
                            matMesa[i][j].setReserva(false);
                            distanciamentoMesa(matMesa, numeroMesa);

                        } else {
                            System.out.println("\nErro: A mesa solicitada não pode ser ocupada no momento! Por favor, verique se ela não está OCUPADA, RESERVADA, bloqueada por SEGURANÇA ou se é para DESINFECTAR.");
                        }
                    }
                }
            }
        }else{
            System.out.println("\nErro: O numero de mesa digitado é invalido!\n");
        }
    }
```
<h4 align="center">Função em execução </h4>

<p align="center">
    <img src="https://user-images.githubusercontent.com/81472331/131895781-d931b533-24f0-47b7-aacb-15365662b4b3.gif">
</p>

# Instalação

<h3>Como o java de sua maquina atualizado , basta ir até a aplicação após o download e fazer o duplo click no arquivo , java na pasta principal.</h3>

# Feedback

# Tecnologias
<div>
    <img align="center" height="70" width="70" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/java/java-original-wordmark.svg">
</div>

# Features
- [x] Cliente
- [x] Gerenciamento de mesa
- [x] Mesa
- [x] Interface gráfica

# Colaboradores

Raniery Vasconcelos <a href = "mailto:raniery_vasconcelos@alu.ufc.br"><img src="https://img.shields.io/badge/-Gmail-%23333?style=for-the-badge&logo=gmail&logoColor=white" target="_blank"></a>

Dominique <a href = "mailto:kossidominique@alu.ufc.br"><img src="https://img.shields.io/badge/-Gmail-%23333?style=for-the-badge&logo=gmail&logoColor=white" target="_blank"></a>

Luan Gomes <a href = "mailto:luangomes@alu.ufc.br"><img src="https://img.shields.io/badge/-Gmail-%23333?style=for-the-badge&logo=gmail&logoColor=white" target="_blank"></a>

Mateus Mota <a href = "mailto:mateusms@alu.ufc.br"><img src="https://img.shields.io/badge/-Gmail-%23333?style=for-the-badge&logo=gmail&logoColor=white" target="_blank"></a>

Yara Braga <a href = "mailto:yrbraga@alu.ufc.br"><img src="https://img.shields.io/badge/-Gmail-%23333?style=for-the-badge&logo=gmail&logoColor=white" target="_blank"></a>

Kenedy <a href = "mailto:kenedyr14@alu.ufc.br"><img src="https://img.shields.io/badge/-Gmail-%23333?style=for-the-badge&logo=gmail&logoColor=white" target="_blank"></a>