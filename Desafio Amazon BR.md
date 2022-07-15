# Desafio Amazon BR

##  Instruções

> Estou super feliz em saber que você está interessado em uma posição conosco. **Gostaríamos de convidá-lo para o próximo passo: Desafio de codificação.** Esse desafio medirá a capacidade de codificação e a adequação geral à Amazon. Você receberá um link externo de nosso fornecedor para que possa concluir a avaliação. Certifique-se de verificar sua pasta de **spam** , caso não encontre o e-mail. **É muito importante que você reserve um tempo para estudar antes do teste.** **Você tem uma semana para completá-lo** **, então você pode levar alguns dias para se preparar.** 
>
>  Aqui estão alguns links úteis para preencher antes de concluir a avaliação (+ o anexo): 
>

❌  https://www.hackerrank.com/challenges/tree-height-of-a-binary-tree

❌ https://www.hackerrank.com/challenges/tree-level-order-traversal

❌ https://www.hackerrank.com/challenges/balanced-brackets

➡️ https://www.hackerrank.com/challenges/contacts

➡️ https://www.hackerrank.com/challenges/find-the-running-median

➡️ https://www.hackerrank.com/challenges/swap-nodes-algo

🎥 Para notação Big O: [https://www.youtube.com/watch ](https://www.youtube.com/watch?v=v4cd1O4zkGw)[? ](https://www.youtube.com/watch?v=v4cd1O4zkGw)[v=v4cd1O4zkGw](https://www.youtube.com/watch?v=v4cd1O4zkGw)

📃 Programação dinâmica (DP): [https://www.geeksforgeeks.org/ ](https://www.geeksforgeeks.org/dynamic-programming/)[dynamic-programming/](https://www.geeksforgeeks.org/dynamic-programming/) e [https://www.youtube.com/watch? ](https://www.youtube.com/watch?v=vYquumk4nWw)[v=vYquumk4nWw](https://www.youtube.com/watch?v=vYquumk4nWw)

📃 Conceitos do algoritmo Flood Fill: [https://www.geeksforgeeks.org/ ](https://www.geeksforgeeks.org/flood-fill-algorithm-implement-fill-paint/)[flood-fill-algorithm- ](https://www.geeksforgeeks.org/flood-fill-algorithm-implement-fill-paint/)[implement-fill-paint/](https://www.geeksforgeeks.org/flood-fill-algorithm-implement-fill-paint/)

​	IMPORTANTE também estou convidando você para a nossa Info-sessão , onde os recrutadores vão contar um pouco mais sobre o processo e como se preparar melhor para a Avaliação Online. Realiza-se todas as **sextas-feiras às:**

- **17h30** (BRT) no seguinte link: https://chime.aws/5124068793 ou em
- **9h00** (GMT) / **12h00** **(** **GMT )** no seguinte link **:** https://chime.aws/1215571917 

Boa sorte, e **entre em contato comigo** se tiver alguma dúvida ou preocupação!

## Questões algorítmicas

### Árvore binária altura

```java
public static int height(Node root) {
    if (root.left == null && root.right == null) {
        return 0;
    }
    int altEsq = 0, altDir = 0;
    if (root.left != null) {
        altEsq = height(root.left);
    }
    if (root.right != null) {
        altDir = height(root.right);
    }
    return 1 + Math.max(altDir, altEsq);
}
```

### Árvore binária impressão ordenada

```java
void printLevelOrder() {
        Queue<Node> queue = new LinkedList<Node>();
        queue.add(root);
        while (!queue.isEmpty()) {
            Node tempNode = queue.poll();
            System.out.print(tempNode.data + " ");
            if (tempNode.left != null) {
                queue.add(tempNode.left);
            }
            if (tempNode.right != null) {
                queue.add(tempNode.right);
            }
        }
    }
```

### Balanceamento de expressões

```java
public static String isBalanced(String s) {
    Deque<Character> stack = new ArrayDeque<Character>();
    for (int i = 0; i < s.length(); i++) {
        char x = s.charAt(i);
        if (x == '(' || x == '[' || x == '{') {
            // Push the element in the stack
            stack.push(x);
            continue;
        }
        if (stack.isEmpty())
            return "NO";
        char check;
        switch (x) {
            case ')':
                check = stack.pop();
                if (check == '{' || check == '[')
                    return "NO";
                break;

            case '}':
                check = stack.pop();
                if (check == '(' || check == '[')
                    return "NO";
                break;

            case ']':
                check = stack.pop();
                if (check == '(' || check == '{')
                    return "NO";
                break;
        }
    }

    return "YES";

}
```

### Contacts

```java
```

