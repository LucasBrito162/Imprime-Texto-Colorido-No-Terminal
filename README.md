# Imprime-Texto-Colorido-No-Terminal
Todos estão acostumados a programas que imprimem a saída em um terminal que rola conforme o novo texto aparece, mas isso não é tudo o que você pode fazer: seu programa pode colorir seu texto. 





Os códigos de escape Ansi mais básicos são aqueles envolvidos na renderização de texto. 
Eles permitem que você adicione decorações como Cores , Cores de fundo ou outras Decorações ao 
seu texto impresso, mas não fazem nada extravagante. O texto que você imprimir ainda terminará 
na parte inferior do terminal e ainda fará o seu terminal rolar, mas agora será um texto colorido 
em vez do esquema de cores padrão preto/branco que seu terminal possui.

cores
A coisa mais básica que você pode fazer no seu texto é colori-lo. Todas as cores Ansi se parecem

**Vermelho :\u001b[31m
**Reiniciar :\u001b[0m

Este \u001b personagem é o personagem especial que inicia a maioria das fugas de Ansi; 
a maioria das linguagens permite esta sintaxe para representar caracteres especiais, 
por exemplo, Java, Python e Javascript permitem a \u001bsintaxe.




Por exemplo, aqui está imprimindo a string "Hello World", mas em vermelho:

      print u"\u001b[31mHelloWorld"


![image](https://user-images.githubusercontent.com/123842272/230732542-ab4a38b0-ecf1-489d-97ed-3831ba484418.png)


Veja como a cor vermelha, partindo do impresso Hello World, acaba se espalhando no >>>prompt. Na verdade, qualquer código que digitarmos nesse prompt também será colorido em vermelho, assim como qualquer saída subsequente! É assim que as cores Ansi funcionam: depois que você imprime o código especial que habilita uma cor, a cor persiste para sempre até que outra pessoa imprima o código para uma cor diferente ou imprima o código Reset para desativá- la .

Podemos desativá-lo imprimindo o código **Reset:  print u"\u001b[0m"

        print u"\u001b[0m"


![image](https://user-images.githubusercontent.com/123842272/230732549-2c34fba6-5e22-4674-931b-c28c980ad9f7.png)


E podemos ver que o prompt volta a ficar branco. Em geral, você deve sempre se lembrar de terminar qualquer sequência colorida que estiver imprimindo com um **Reset /**, para garantir que não acidentalmente

Para evitar isso, precisamos ter certeza de terminar nossa string colorida com o código **Reset :

        print u"\u001b[31mHelloWorld\u001b[0m"

![image](https://user-images.githubusercontent.com/123842272/230732556-7835f800-1493-4b54-912f-d01c62059710.png)

O que redefine corretamente a cor após a impressão da string. Você também pode **Redefinir/** no meio da corda para tornar a segunda metade sem cor:

        print u"\u001b[31mHello\u001b[0mWorld"

![image](https://user-images.githubusercontent.com/123842272/230732559-d08fbf2e-88f1-4475-878d-4003d44fdef6.png)


                        8 cores
                     
Vimos como **Red/** e **Reset /** funcionam. Os terminais mais básicos possuem um conjunto de 8 cores diferentes:

**Preto :\u001b[30m
  Vermelho :\u001b[31m
  Verde :\u001b[32m
  Amarelo :\u001b[33m
  Azul :\u001b[34m
  Magenta :\u001b[35m
  Ciano :\u001b[36m
  Branco :\u001b[37m
  Reiniciar :\u001b[0m 

O que podemos demonstrar imprimindo uma letra de cada cor, seguida de um **Reset :

    print u"\u001b[30m A \u001b[31m B \u001b[32m C \u001b[33m D \u001b[0m"
    print u"\u001b[34m E \u001b[35m F \u001b[36m G \u001b[37m H \u001b[0m"


![image](https://user-images.githubusercontent.com/123842272/230732574-62ac3e27-7b0a-44b2-8d97-6cfc4adc6025.png)



Observe como o preto A é totalmente invisível no terminal preto, enquanto o branco H parece igual ao texto normal. Se escolhêssemos um esquema de cores diferente para nosso terminal, seria o oposto:

    print u"\u001b[30;1m A \u001b[31;1m B \u001b[32;1m C \u001b[33;1m D \u001b[0m"
    print u"\u001b[34;1m E \u001b[35;1m F \u001b[36;1m G \u001b[37;1m H \u001b[0m"

![image](https://user-images.githubusercontent.com/123842272/230732589-f53ad8e2-230b-4854-8cf7-5c08d4a92f57.png)


Com o preto **A?** sendo óbvio e o branco H sendo difícil de distinguir.

                                16 cores
                                
A maioria dos terminais, além do conjunto básico de 8 cores, também suporta as cores "brilhantes" ou "negritas". Estes têm seu próprio conjunto de códigos, espelhando as cores normais, mas com um adicional ;1 em seus códigos:

**Preto Brilhante :\u001b[30;1m
  Vermelho Brilhante :\u001b[31;1m
  Verde brilhante :\u001b[32;1m
  Amarelo brilhante :\u001b[33;1m
  Azul brilhante :\u001b[34;1m
  Magenta brilhante :\u001b[35;1m
  Ciano brilhante :\u001b[36;1m
  Branco Brilhante :\u001b[37;1m
  Reiniciar :\u001b[0m

Observe que **Redefinir/** é o mesmo: este é o código de redefinição que redefine todas as cores e efeitos de texto.

Podemos imprimir essas cores brilhantes e ver seus efeitos:

![image](https://user-images.githubusercontent.com/123842272/230732597-65313cea-ead5-40d7-8bd7-0a0ef724deb9.png)

E veja que eles são, de fato, muito mais brilhantes que o conjunto básico de 8 cores. Até mesmo o preto A agora é brilhante o suficiente para ser um cinza visível no fundo preto, e o branco Hagora é ainda mais brilhante do que a cor padrão do texto.

            
            
                                256 cores

Por fim, após as 16 cores, alguns terminais suportam um conjunto de cores estendido de 256 cores.

Estes são da forma

**\u001b[38;5;${ID}m

              import sys
                for i in range(0, 16):
                   for j in range(0, 16):
                      code = str(i * 16 + j)
                      sys.stdout.write(u"\u001b[38;5;" + code + "m " + code.ljust(4))
                   print u"\u001b[0m"
    

![image](https://user-images.githubusercontent.com/123842272/230732655-8d3c4cc5-7488-4a7c-a5c5-2f7513a9e30e.png)


Aqui usamos **sys.stdout.writeem /** vez de **print /** para que possamos imprimir vários itens na mesma linha, mas fora isso é bem autoexplicativo. Cada código de 0 a 255 corresponde a uma cor específica.


                            Cores de fundo

Os códigos de escape Ansi permitem que você defina a cor do fundo do texto da mesma forma que permite definir a cor do primeiro plano. Por exemplo, as 8 cores de fundo correspondem aos códigos:

**Fundo preto :\u001b[40m
  Fundo vermelho :\u001b[41m
  Fundo Verde :\u001b[42m
  Fundo amarelo :\u001b[43m
  Fundo Azul :\u001b[44m
  Fundo Magenta :\u001b[45m
  Fundo Ciano :\u001b[46m
  Fundo Branco :\u001b[47m
  
  Com as versões brilhantes sendo:

**Fundo preto brilhante :\u001b[40;1m
  Fundo Vermelho Brilhante :\u001b[41;1m
  Fundo Verde Brilhante :\u001b[42;1m
  Fundo amarelo brilhante :\u001b[43;1m
  Fundo Azul Brilhante :\u001b[44;1m
  Fundo Magenta Brilhante :\u001b[45;1m
  Fundo Ciano Brilhante :\u001b[46;1m
  Fundo Branco Brilhante :\u001b[47;1m
  
  E redefinir é o mesmo:

**Reiniciar :\u001b[0m

Podemos imprimi-los e vê-los funcionar

      print u"\u001b[40m A \u001b[41m B \u001b[42m C \u001b[43m D \u001b[0m"
      print u"\u001b[44m A \u001b[45m B \u001b[46m C \u001b[47m D \u001b[0m"
      print u"\u001b[40;1m A \u001b[41;1m B \u001b[42;1m C \u001b[43;1m D \u001b[0m"
      print u"\u001b[44;1m A \u001b[45;1m B \u001b[46;1m C \u001b[47;1m D \u001b[0m"

![image](https://user-images.githubusercontent.com/123842272/230732687-4e8d2b6c-e330-4d68-8e6f-ae753c7674fd.png)



Observe que as versões brilhantes das cores do plano de fundo não alteram o plano de fundo, mas tornam o texto do primeiro plano mais claro. Isso não é intuitivo, mas é assim que funciona.

Planos de fundo de 256 cores também funcionam:

        import sys
        for i in range(0, 16):
            for j in range(0, 16):
               code = str(i * 16 + j)
               sys.stdout.write(u"\u001b[48;5;" + code + "m " + code.ljust(4))
            print u"\u001b[0m"

![image](https://user-images.githubusercontent.com/123842272/230732714-bc4e83df-a88b-45b1-b7f7-c2fe0567c832.png)



**Decorações

Além das cores e cores de fundo, os códigos de escape Ansi também permitem decorações no texto:

**Negrito :\u001b[1m
  Sublinhe :\u001b[4m
  Invertida :\u001b[7m
  
  Que podem ser usados individualmente:

      print u"\u001b[1m BOLD \u001b[0m\u001b[4m Underline \u001b[0m\u001b[7m Reversed \u001b[0m"

![image](https://user-images.githubusercontent.com/123842272/230732733-7e388464-3103-4279-a49c-aeefb4c22dec.png)

Ou juntos

    print u"\u001b[1m\u001b[4m\u001b[7m BOLD Underline Reversed \u001b[0m"


E pode ser usado em conjunto com cores de foreground e background:

        print u"\u001b[1m\u001b[31m Red Bold \u001b[0m"
        print u"\u001b[4m\u001b[44m Blue Background Underline \u001b[0m"




![image](https://user-images.githubusercontent.com/123842272/230732489-0097b4de-2b2e-40a4-b71d-1693a270711c.png)


