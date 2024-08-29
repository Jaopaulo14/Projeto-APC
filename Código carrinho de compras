#include <stdio.h>
#include <string.h>

/* Struct que irá conter as informações do produto para realizar as operações*/

struct produto{
  char nome [100];
  double preco;
  int quantidade;
};

typedef struct produto produto;

int compra(produto carrinho[1001],int indice_carrinho, double saldo){

  produto item;
  int i,a,comparacao,qtd_prod_removidos;


  scanf("%s",item.nome);
  getchar();
  scanf("%lf",&item.preco);
  getchar();
  scanf("%d",&item.quantidade);
  getchar();
  /*Vai ler as informações do produto que queremos*/

  /* Vamos verificar primeiro se não está extrapolando o saldo.
  Nesse caso vamos comprar o máximo de produtos que der */

  //printf("%.2lf\n",(saldo - (item.quantidade * item.preco)));

  if((saldo - (item.quantidade * item.preco)) < 0){

    /* Vamos verificar o máximo de produtos que podemos retirar até o saldo poder cobrir*/
    for(i = 0, qtd_prod_removidos = 1; i < item.quantidade; i++){

      //printf("O saldo eh %.2lf\n",saldo);
      //printf("diminuindo o preco do produto:%.2lf\n",(saldo - item.preco * (item.quantidade - qtd_prod_removidos)));

      if((saldo - item.preco * (item.quantidade - qtd_prod_removidos)) < 0){

        qtd_prod_removidos++;

       }
    }
  }else{
    qtd_prod_removidos = 0;
    /* caso não precise remover produtos*/
  }

  /* Agora que temos a quantidade máxima de produtos que foram removidos, vamos
  atualizar nas informações do produto*/
 // printf("vamos remover %d",qtd_prod_removidos);
  item.quantidade = item.quantidade - qtd_prod_removidos;

  /* se quantidade de produtos adicionados der zero, não vamos remover nada */

  if(item.quantidade > 0){

    /* Esse for ira verificar se exite algum produto semelhante no carrinho,
    caso houver a varivavel 'a' será incrementada*/
    for(i = 0, a = 0; i < indice_carrinho; i++){

        comparacao = strcmp(item.nome,carrinho[i].nome);

        if(comparacao == 0){
          a++;
          break;
          /* Com isso já vamos ter o indice do produto igual que ficar em 'i'*/
        }

    }

    /* Vamos agora verificar o valor de 'a' se ele for difente de zero 
    significa que há algum item semelhante vamos somente alterar sua quantidade */
    if(a != 0){

      carrinho[i].quantidade = carrinho[i].quantidade + item.quantidade;

    }else{

      /* se nao houver semelhante vamos adicionar ao carrinho*/

      strcpy(carrinho[indice_carrinho].nome,item.nome);
      carrinho[indice_carrinho].preco = item.preco;
      carrinho[indice_carrinho].quantidade = item.quantidade;
      /* Vai colocar o produto no carrinho junto com suas informações */

      indice_carrinho++;
      /* vai para o próximo indice que está vazio esperar por outra compra */

    }
  }

  return indice_carrinho;
}


void mostra(produto carrinho [1001],int indice_carrinho){

  int i, k,l;
  produto aux;
  double total;

  /* Temos que imprimir em ordem alfábetica então vamos comparar a 
  primeira coluna do nome de cada item  e trocar eles de lugar no carrinho*/

  for(i = 0; i < indice_carrinho; i++){

    for(k = i+1; k < indice_carrinho; k++){

      for(l = 0; l < strlen(carrinho[i].nome); l++){
        if(carrinho[i].nome[l] != carrinho[k].nome[l]){
          break;
        }
      }
      if(carrinho[i].nome[l] > carrinho[k].nome[l]){

        /* bota o produto no aux*/
        strcpy(aux.nome,carrinho[i].nome);
        aux.preco = carrinho[i].preco;
        aux.quantidade = carrinho[i].quantidade;
        /* troca de lugar */
        strcpy(carrinho[i].nome,carrinho[k].nome);
        carrinho[i].preco = carrinho[k].preco;
        carrinho[i].quantidade = carrinho[k].quantidade;
        /* bota o produto do aux no que foi trocado */
        strcpy(carrinho[k].nome,aux.nome);
        carrinho[k].preco = aux.preco;
        carrinho[k].quantidade = aux.quantidade;

      }
    }
  }

  /*com o carrinho ordenado em ordem alfabética só imprimir*/

  for(i = 0; i < indice_carrinho; i++){

    printf("%s ",carrinho[i].nome);
    printf("%d x ",carrinho[i].quantidade);
    printf("%.2lf = ",carrinho[i].preco);
    printf("%.2lf\n",carrinho[i].preco * carrinho[i].quantidade);

  }
  for(i = 0, total = 0; i < indice_carrinho; i++){

    total = total + carrinho[i].preco * carrinho[i].quantidade;

  }
  printf("TOTAL: %.2lf\n",total);
}

int remover(produto carrinho[1001],int indice_carrinho){

  int i,qtd_removidas,aux,k;
  char nome_do_pdt[100], existe_produto;

  scanf("%s",nome_do_pdt);
  getchar();
  scanf("%d",&qtd_removidas);
  getchar();

  aux = 1;
  /* vamos comparar o nome do produto que queremos remover com os que estão no carrinho*/
  for(i = 0; i < indice_carrinho; i++){

    aux = strcmp(nome_do_pdt,carrinho[i].nome);

    if(aux == 0){

      /* vai pegar o indice do produto que queremos revomer*/
      break;
    }
    /* se aux = 0 existe algum item compativel*/
  }


  if(aux == 0){
    existe_produto = 's';
  }else{
    existe_produto = 'n';
  }

  /* com isso vamos saber se existe um produto compativel ou não*/

  if(existe_produto == 's'){

    /* nesse caso existe um produto então vamos remover as quantidades que queremos */

    /* se a quantidade dos produtos depois da remoção for 0, então temos que tirar ele do carrinho 
    para isso vamo mover ele para o último indice e decrementa o indice_carrinho*/

    if((carrinho[i].quantidade - qtd_removidas) <= 0){

      for(k = i+1 ; k < indice_carrinho; k++, i++){

        /*vamos copiar o que está no indice da frente no anterior*/
        strcpy(carrinho[i].nome,carrinho[k].nome);
        carrinho[i].preco = carrinho[k].preco;
        carrinho[i].quantidade = carrinho[k].quantidade;

      }
      indice_carrinho--;
      /* decrementamos o indice para preencher ele depois em caso de compra ou n imprimir repetido */
    }else{

      carrinho[i].quantidade = carrinho[i].quantidade - qtd_removidas;

    }

  }else{

    /*não tem como remover um produto que não está no carrinho */
    printf("ERRO: O produto %s nao esta no carrinho\n",nome_do_pdt);

  }    

  /* como decrementamos vamos retornar o novo valo do indice*/
  return indice_carrinho;
}

double atualizar(produto carrinho[1001], int indice_carrinho, double saldo){

  int i,aux,qtd_prod_removidos,k;
  char nome[100], existe_produto;
  double novo_preco,novo_saldo;
  produto aux_Prod;

  aux = 1;

  scanf("%s",nome);
  getchar();
  scanf("%lf",&novo_preco);
  getchar();

  /*vamos verificar se o item está no carrinho comparando os nomes */
  for(i = 0; i < indice_carrinho; i++){
    aux = strcmp(nome,carrinho[i].nome);

    if(aux == 0){
      /* vai pegar o indice do produto que queremos atualizar*/
      break;
    }
    /* se aux = 0 existe algum item compativel*/
  }

  /* vamos armazenar a diferença de preço entre os dois*/
  novo_saldo = carrinho[i].preco - novo_preco;

  if(aux == 0){
    /* se tiver o produto */
    existe_produto = 's';
  }else{
    /* se não tiver o produto */
    existe_produto = 'n';
  }

  if(existe_produto == 's'){

    /* vamos devolver as quantidades para o saldo atualizar o preco e ver quantos novos cabem*/

    saldo = saldo + carrinho[i].preco * carrinho[i].quantidade;

    carrinho[i].preco = novo_preco;

    /* Vamos verificar primeiro se não está extrapolando o saldo.
    Nesse caso vamos comprar o máximo de produtos que der */
    if((saldo - (carrinho[i].quantidade * carrinho[i].preco)) < 0){

      /* Vamos verificar o máximo de produtos que podemos retirar até o saldo poder cobrir*/        
      for(k = 0, qtd_prod_removidos = 1; k < carrinho[i].quantidade; k++){

        if((saldo - carrinho[i].preco * (carrinho[i].quantidade - qtd_prod_removidos)) < 0){

          qtd_prod_removidos++;
        }
      }
    }else{
      qtd_prod_removidos = 0;
      /* caso não precise remover produtos*/
    }

    /* Agora que temos a quantidade máxima de produtos que foram removidos, vamos
    atualizar nas informações do produto*/

    //printf("a quantidade antes do A eh: %d\n",carrinho[i].quantidade);
    carrinho[i].quantidade = carrinho[i].quantidade - qtd_prod_removidos;
    //printf("a quantidade de %s depois do A eh: %d\n",carrinho[i].nome,carrinho[i].quantidade);
    /* se depois da remocao a quantidade for zero entao temos que tiralo do carrinho*/
    if(carrinho[i].quantidade == 0){

      /* vamos passa ele para o ultimo indice para depois remover*/
      //printf("o id eh %d\n",indice_carrinho);
      for(k = i+1 ; k < indice_carrinho; k++, i++){
        
        //printf("o i eh %d eh e o k %d eh\n",i,k);
        /*vamos copiar o que está no indice da frente no anterior*/
        
        strcpy(aux_Prod.nome,carrinho[i].nome);
        aux_Prod.preco = carrinho[i].preco;
        aux_Prod.quantidade = carrinho[i].quantidade;

        strcpy(carrinho[i].nome,carrinho[k].nome);
        carrinho[i].preco = carrinho[k].preco;
        carrinho[i].quantidade = carrinho[k].quantidade;

        strcpy(carrinho[k].nome,aux_Prod.nome);
        carrinho[k].preco = aux_Prod.preco;
        carrinho[k].quantidade = aux_Prod.quantidade;
        
      } 
      //printf("q eh %d\n",carrinho[k-1].quantidade);
    }
    /* se quantidade de produtos adicionados der zero, não vamos adicionar nada */
    /*agora vamos atualizar o saldo*/
    saldo = saldo - carrinho[i].preco * carrinho[i].quantidade;

    /* vamos retornar o novo saldo depois da troca de preco*/      
    return saldo;

  }else{
    printf("ERRO: O produto %s nao esta no carrinho\n",nome);
    return saldo;
  }

}

int main() {

  int Q,i,indice_carrinho,k;
  double dinheiro_disponivel;
  char operacao;

  produto carrinho [1001];
  /* Vai ser o carrinho em que vamos fazer as operacoes*/

  indice_carrinho = 0;
  /* Vai controlar em que indice do vetor carrinho estamos para adicionar produtos em outras palavras
  irá mostrar quantos itens tem no carrinho*/

  scanf("%d %lf",&Q,&dinheiro_disponivel);
  getchar();
  /* Lendo a quantidade de operações a ser feita e o saldo disponivel para compras */


  for(i = 0; i < Q; i++){

    scanf("%c",&operacao);
    getchar();
    /* Vai ler a operção que vai ser feita */

    /* depois de ler a operação vamos ver qual executar */

    if(operacao == 'C'){

      indice_carrinho = compra(carrinho,indice_carrinho,dinheiro_disponivel);

      /* em casos de não adicionar nehnum item por conta do saldo pra ele não subtrair o valor do item anterior*/
      if((dinheiro_disponivel - carrinho[indice_carrinho -1].preco * carrinho[indice_carrinho-1].quantidade) >= 0){

        dinheiro_disponivel = dinheiro_disponivel - carrinho[indice_carrinho -1].preco * carrinho[indice_carrinho-1].quantidade;

        // printf("O saldo eh na main %.2lf\n",dinheiro_disponivel);
      }
    }
    if(operacao == 'M'){

      mostra(carrinho,indice_carrinho);

    }
    if(operacao == 'R'){

      indice_carrinho = remover(carrinho,indice_carrinho);
     // printf("o indice eh %d\n",indice_carrinho);

      /* atualizamos o saldo disponivel */
      dinheiro_disponivel = dinheiro_disponivel + carrinho[indice_carrinho + 1].preco * carrinho[indice_carrinho + 1].quantidade;

    }
    if(operacao == 'A'){

      dinheiro_disponivel =  atualizar(carrinho,indice_carrinho,dinheiro_disponivel);

      /*para o caso de que tenha que remover o item do carrinho, como ja passamos
      ele para o ultimo indice so decrementar o indice_carrinho*/
      //printf("tem %s quantidades\n",carrinho[].nome);
      for(k = 0; k < indice_carrinho; k++){
        if(carrinho[k].quantidade == 0){
          indice_carrinho--;
          //printf("no A eh %d\n",indice_carrinho);
        }
      }
    }
  }
  return 0;
}
