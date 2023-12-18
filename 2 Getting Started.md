2 Início

Este capítulo irá familiarizá-lo com o framework que usaremos ao longo do livro para pensar no design e análise de algoritmos. Ele é autocontido, mas inclui várias referências a material que introduziremos nos Capítulos 3 e 4. (Também contém várias somatórias, que o Apêndice A mostra como resolver.)

Começamos examinando o algoritmo de ordenação por inserção para resolver o problema de ordenação apresentado no Capítulo 1. Definimos um "pseudocódigo" que deve ser familiar se você já programou em computadores, e o usamos para mostrar como especificaremos nossos algoritmos. Após especificar o algoritmo de ordenação por inserção, argumentamos que ele ordena corretamente e analisamos seu tempo de execução. A análise introduz uma notação que se concentra em como esse tempo aumenta com o número de itens a serem ordenados. Após nossa discussão sobre a ordenação por inserção, introduzimos a abordagem de dividir e conquistar para o design de algoritmos e a usamos para desenvolver um algoritmo chamado merge sort. Terminamos com uma análise do tempo de execução do merge sort.

Entrada: Uma sequência de n números (a1, a2, ..., an).

Saída: Uma permutação (reorganização) (a'1, a'2, ..., a'n) da sequência de entrada, tal que a'1  <= a'2 <= ... <= a'n.

Os números que desejamos ordenar também são conhecidos como chaves. Embora conceitualmente estejamos ordenando uma sequência, a entrada nos é fornecida na forma de um array com n elementos.
Neste livro, geralmente descreveremos algoritmos como programas escritos em um pseudocódigo que é semelhante em muitos aspectos a C, C++, Java, Python ou Pascal. Se você foi apresentado a alguma dessas linguagens, não terá dificuldade em ler nossos algoritmos. O que separa o pseudocódigo do código "real" é que, no pseudocódigo, empregamos o método expressivo mais claro e conciso para especificar um determinado algoritmo. Às vezes, o método mais claro é o inglês, então não se surpreenda se encontrar uma frase ou sentença em inglês incorporada a uma seção de código "real". Outra diferença entre pseudocódigo e código real é que o pseudocódigo geralmente não se preocupa com questões de engenharia de software. Questões de abstração de dados, modularidade e tratamento de erros muitas vezes são ignoradas para transmitir a essência do algoritmo de forma mais concisa.

Começamos com a ordenação por inserção, que é um algoritmo eficiente para ordenar um pequeno número de elementos. A ordenação por inserção funciona da maneira como muitas pessoas ordenam um conjunto de cartas. Começamos com uma mão esquerda vazia e as cartas viradas para baixo na mesa. Em seguida, removemos uma carta de cada vez da mesa e a inserimos na posição correta na mão esquerda. Para encontrar a posição correta de uma carta, a comparamos com cada uma das cartas já na mão, da direita para a esquerda, conforme ilustrado na Figura 2.1. Em todos os momentos, as cartas mantidas na mão esquerda estão ordenadas, e essas cartas eram originalmente as cartas superiores da pilha na mesa.

Apresentamos nosso pseudocódigo para a ordenação por inserção como um procedimento chamado INSERTIONSORT, que recebe como parâmetro um array A[1..n] contendo uma sequência de comprimento n que deve ser ordenada. (No código, o número n de elementos em A é denotado por A.length.) O algoritmo ordena os números de entrada no local: rearranja os números dentro do array A, com no máximo um número constante deles armazenados fora do array a qualquer momento. O array de entrada A contém a sequência de saída ordenada quando o procedimento INSERTION-SORT é concluído.

```pseudo
Insertion-Sort(a)
1 for j = 2 to A.Length
2    key := A[j]
3    // Insere A[j] na sequência classificada A[1..j-1]
4    i = j - 1
5    while i > 0 and A[i] > key
6      A[i + 1] = A[i]
7      i = i - 1
8    A[i + 1] = key
```

