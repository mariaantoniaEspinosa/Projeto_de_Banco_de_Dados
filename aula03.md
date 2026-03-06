# Revisão da Última Aula
## Estrutura de Dados
- Físicas: variáveis das linguagens de programação: int, float, char, string, vetores, matrizes, ...
- Abstratas:
    - Lista
      - C++ -> vector
      - Java -> List, ArrayList, LinkedList
      - C# -> List, ArrayList
      - Python -> List
    -  Pilha
    -  Fila
    -  Arvore
    -  Grafo
  - algoritmos de gestão de memória: guardar/armazenar e buscar/pesquisar da melhor forma possivel (eficiência)
    - operações clássicas:
      - inserir
        - C++ -> push_back()
        - Java -> add
        - C# -> add
        - Python -> append()
      - remover pela posição ou pelo elemento
        - C++ -> pop_back(), erase()
        - Java -> remove()
        - C# -> Remove()
        - Python -> remove()
      - verificar tamanho de estrutura
        - C++ -> size()
        - Java -> size()
        - C# -> count
        - Python -> len()
      - se está vazia
        - se o tamanho for igual a zero
        - empty() ou isEmpty()
      - localizar
         - vetor [5, 9, 7, 2, 5]
         - TAM = 5
        
          ### C
        ```    
        numero = 5
        encontrado = false
        for(int i =0; i<5; i++{
          if(numero == vetor[i]){
              encontrado = true;
            break;
          }
        }
          if(encontrado{
              printf("Numero encontrado");
          } else {
              print("Numero não encontrado")
          }
        ```
          ### Python
        ```
        vetor =  [5, 9, 7, 2, 5]
        numero = 5
        if numero in vetor:
          print("Encontrado")
        else:
          print("Não encontrado")
        ```

          ### Java
        ```
        vetor =  [5, 9, 7, 2, 5]
        numero = 5
        if vetor.contains(numero){
          System.out.println("Encontrado");
        } else {
          System.out.prinyln("Não econtrado");

        ```
        
          ### C#
        ```
        vetor =  [5, 9, 7, 2, 5]
        numero = 5
        if vetor.Contains(numero){
          Console.write("Encontrado");
        } else {
          Console.write("Não econtrado");
        ```

          ### Exercício em Python
        ```
        from biblioteca import popular_lista_aleatoria, exibir_lista, copiar_lista_sem_replicados
        #declarando uma lista em python
        lista_numeros = []
        
        #recebendo a quantidade de números a serem gerados aleatoriamente
        quantiadade_numeros = int (input("Digite quantos numeros gostaria de armazenar: "))
        
        #definindo a faixa de intervalo dos numeros a serem sorteados 
        faixa_inicial = 10
        faixa_final = 50
        
        popular_lista_aleatoria(lista_numeros, quantiadade_numeros, faixa_inicial, faixa_final)
        
        exibir_lista(lista_numeros)
        
        lista_resultado = []
        copiar_lista_sem_replicados(lista_numeros, lista_resultado)
        lista_resultado.sort()
         exibir_lista(lista_resultado)
        ```
          ### Biblioteca do Exercício em Python
        ```
        import random
        
        def popular_lista_aleatoria(lista, quantidade, faixa_inicial, faixa_final):
            """metodo que popula uma lista com numeros inteiros e aleatorios dentro de uma faixa 
        
            Args:
                lista (int): armazena numeros inteiros e aleatorios 
                quantidade (int): total de numeros inteiros a serem inseridos
                faixa_inicial (int): numero inicial da faixa 
                faixa_final (int): numero final da faixa
            """
            pass
        
            for i in range(quantidade):
                lista.append(random.randint(faixa_inicial, faixa_final))
        
        
         def exibir_lista(lista):
            """metodo que recebe uma lista e a exibe, elementos um abaixo do outro
        
            Args:
                lista (int): lista contando numeros inteiros
            """
            for item in lista:
                print(item)
        
            print("------------")
            print("Total de elementos: ", len(lista))
        
            pass
        
        
         def copiar_lista_sem_replicados(lista_origem, lista_destino):
            """metodo que copia o conteudo da lista origem para dentro da lista destino retirando os replicados
        
            Args:
                lista_origem (int): _lista original contendo todos os numeros
                lista_destino (int): contendo apenas os numeros nao replicados
            """
        
            for item in lista_origem:
                if item not in lista_destino:
                lista_destino.append(item)
        ```
        ### Exercício em C++
        ```
                #include <iostream>
        #include <cstdlib>
        #include <vector> // para a lista
        
        using namespace std;
        
        #include "biblioteca.h"
        
        int main(){
            
            //declarando uma lista
            vector<int> listaNumero;
        
        
            int quantidadeNumeros;
            int faixaInicial=10, faixaFinal=50;
            vector<int> listaResultados;
        
            cout << "Digite quantos numeros quer gerar: ";
            cin >> quantidadeNumeros;
        
            popularListaAleatoria(listaNumero, quantidadeNumeros, faixaInicial, faixaFinal);
            exibirLista(listaNumero);
            copiarListaSemReplicados(listaNumero, listaResultados);
        
            cout << "\nLista sem numeros repetidos:\n";
            exibirLista(listaResultados);
        
            return 1;
        }
        ```
        ### Biblioteca do Exercício em C++
        ```
          #include <iostream>
          #include <cstdlib>
          #include <vector> // para a lista
          #include <ctime>
          
          
          using namespace std;
          
          /**
           * @brief método que popula uma lista com numeros inteiros aleatorios dentro de uma faixa
           * 
           * @param lista contem os numeros aleatorios gerados 
           * @param quantidadeNumeros contem quantos numeros se deseja inserir na lista
           * @param faixaInicial contem o numero inicial da faixa
           * @param faixaFinal  contem o numero final da faixa
           */
          
          void popularListaAleatoria(vector<int> &lista, int quantidadeNumeros,  int faixaInicial, int faixaFinal){
              //&: se houver alteração na lista, é preciso utilizar o simbolo de endereçamento 
              srand(time(NULL));
              int numeroSorteado;
              for(int i = 0; i<quantidadeNumeros; i++){
                  numeroSorteado = faixaInicial + (rand() % faixaFinal);
                  lista.push_back(numeroSorteado);
              }
          
          }
          
          /**
           * @brief metodo que exibe um conteudo de uma lista de inteiros, elemento abaixo de elemento
           * 
           * @param lista lista contem os numeros inteiros
           */
          
          void exibirLista(vector<int> lista){
              for(int i = 0; i<lista.size(); i++){
                  cout << lista[i] << "\n";
              }
              cout << "------------";
              cout << "\n";
              cout << "Total de elementos: " << lista.size() << "\n";
          
          }
          
          void copiarListaSemReplicados(vector<int> listaOrigem, vector<int> &listaDestino){
                  for(int i = 0; i < listaOrigem.size(); i++){
                      int elemento = listaOrigem[i];
                      int j;
                      for(j = 0; j< listaDestino.size(); j++){
                          if(listaDestino[j]==elemento){
                              break;
                          }
                      }
                      if(j==listaDestino.size()){
                          listaDestino.push_back(elemento);
                      }
                  }
          
          }
        ```
