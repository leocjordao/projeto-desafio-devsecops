# Desafio DevSecOps — Gerenciador de Tarefas

## Sobre o Projeto
Este repositório faz parte do desafio prático do módulo de DevSecOps da ADA Tech.
Você receberá este projeto com vulnerabilidades propositais e uma pipeline incompleta.
Seu objetivo é **implementar a pipeline de segurança** e **corrigir as vulnerabilidades**.

## Estado atual
A pipeline está **incompleta**. Os steps de segurança precisam ser implementados por você.

## Sua missão
1. Implementar os steps de segurança no `pipeline.yml`
2. Fazer a pipeline **quebrar** ao detectar os problemas
3. Corrigir as vulnerabilidades encontradas
4. Fazer a pipeline **passar** com tudo verde ✅
5. Documentar o funcionamento da pipeline neste README

## O que implementar
- [ ] Secrets Scanning com **Gitleaks**
- [ ] SAST com **Semgrep**
- [ ] SCA com **Grype**
- [ ] Deploy com **GitHub Pages**

## Como a pipeline funciona
> Step 1: Checkout do código
   Baixa o código para o ambiente onde a pipeline será executada para que os próximos passos possam acessar o código.
> Step 2: Build
   Verifica e lista os arquivos da pasta src
> Step 3: Secret Scanning
   Detecta informações sensíveis presentes no código
   Foi utilizada a ferramenta Gitleaks para percorrer o código e identificar padrões conhecidos de credenciais, incluindo chaves de API e senhas, e caso encontre algum desses padrões a execução falha e a pipeline é interrompida.
> Step 4: SAST (semgrep)
   Detecta vulnerabilidades no código fonte
   Foi utilizado semgrep para analisar os arquivos e identificar padrões de código inseguros, como por exemplo SQL Injection, command injection, ausência de validações, etc. Caso encontra alguma potencial vulnerabilidade, a execução falha e a pipelina é interrompida.
> Step 5: SCA (grype)
   Detecta vulnerabilidades nas depedências do projeto
   O SCA verifica as bibliotecas externas utilizadas na aplicação, grype identifica todas as dependências do projeto em relação aos CVEs. Caso existam bibliotecas com vulnerabilidades iguais ou superiores ao nível definido (neste caso, medium), a execução falha e a pipeline é interrompida.
> Step 6: Deploy
   Publica a aplicação
   O deploy só acontece se todas as etapas anteriores foram executadas sem falhas, ou seja, que não foram encontrados problemas de segurança no código.

## URL de Produção
> https://leocjordao.github.io/projeto-desafio-devsecops/
