# Ferramentas de Build: Apache Ant

Material para o seminário "Explorando Ferramentas de Build", da matéria Gerência de Configuração de Software, do curso de Engenharia de Software na PUC Minas. O **Apache Ant** é a ferramenta escolhida para análise, uma ferramenta de automação de build para Java que descreve o processo em um arquivo XML.

## Organização dos arquivos

| Caminho | Conteúdo |
|---|---|
| [demonstracao/HelloAnt.java/](demonstracao/HelloAnt.java) | Projeto de exemplo usado na demo |
| [demonstracao/build.xml](demonstracao/build.xml/) | 

## Rodando a demo (hello-ant)

Requisitos: JDK 8 ou superior e Apache Ant 1.10.x no `PATH`. Testado com Ant 1.10.15 e Java 21.

```sh
cd demonstracao/hello-ant
ant                      # executa compile e depois jar (target padrão)
jar tf dist/hello.jar    # mostra o conteúdo do artefato
java -jar dist/hello.jar # imprime "Ola, turma! Build feito com Apache Ant."
ant                      # segunda vez: nada é recompilado
ant clean                # apaga build/ e dist/
```

Targets disponíveis no `build.xml`: `clean`, `compile`, `jar` (padrão) e `run`.
