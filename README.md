# Ferramentas de Build: Apache Ant

Material para o seminário "Explorando Ferramentas de Build", da matéria Gerência de Configuração de Software, do curso de Engenharia de Software na PUC Minas. O **Apache Ant** é a ferramenta escolhida para análise, uma ferramenta de automação de build para Java que descreve o processo em um arquivo XML.

## Organização dos arquivos

| Caminho | Conteúdo |
|---|---|
| [demonstracao/src/HelloAnt.java](demonstracao/src/HelloAnt.java) | Classe Java de exemplo usada na demo |
| [demonstracao/build.xml](demonstracao/build.xml) | Script de build do Ant, com os targets da demo |
| [demonstracao/Dockerfile](demonstracao/Dockerfile) | Imagem com JDK 21 e Ant 1.10.15, para rodar a demo sem instalar nada na máquina |
| [demonstracao/compose.yaml](demonstracao/compose.yaml) | Sobe o container com a pasta da demo montada em `/demo` |

As pastas `demonstracao/build/` (classes compiladas) e `demonstracao/dist/` (JAR) são geradas pelo build e não são versionadas.

## Como executar

Requisitos: 
- Git
- Docker Desktop
- JDK 8 (Sanado pelo Docker)
- Ant 1.10.x (Sanado pelo Docker)

1. Clone o repositório e entre na pasta da demo:

   ```sh
   git clone https://github.com/eversbrehh/hello-ant.git
   cd hello-ant/demonstracao
   ```

2. Abra o Docker Desktop e espere ele indicar que o motor está em execução.

3. Monte a imagem **(se não exisitr)**

   ```sh
   docker compose build
   ```

4. Abra um terminal dentro do container, já na pasta `/demo`:

   ```sh
   docker compose run --rm demo
   ```

5. Dentro do container, compile, empacote e execute o programa:

   ```sh
   ant run
   ```

   A saída esperada termina assim:

   ```text
   run:
        [java] Ola, Mundo! Build feito com Apache Ant.

   BUILD SUCCESSFUL
   ```

6. Para sair do container, digite `exit`.

Se o Docker responder com erro 500 ou 502, o motor ainda está iniciando ou a máquina está com pouca memória livre: feche outros programas, espere alguns segundos e repita o comando.

## Rodando a demo passo a passo (hello-ant)

```sh
ant -p                   # lista os targets e suas descrições
ant                      # executa compile e depois jar (target padrão)
jar tf dist/hello.jar    # mostra o conteúdo do artefato
java -jar dist/hello.jar # imprime "Ola, Mundo! Build feito com Apache Ant."
ant                      # segunda vez: nada é recompilado
ant clean                # apaga build/ e dist/
exit                     # sai do container
```

Targets disponíveis no `build.xml`: `clean`, `compile`, `jar` (padrão) e `run`.
Conferir `ant -version` e `java -version` e rodar `ant clean` para começar sem artefatos antigos.
