### 🔧 Configurando variável de ambiente JAVA no WSL

Em teoria a JDK no windows deveria ser a mesma usada no WSL, porém é necessário fazer 
uma ponte da váriável de ambiente do windows para as envs no Lunix. Isso pode gerar 
alguns bugs além de ser um pouco trabalhoso e confuso. Então a melhor opção é baixar
uma nova JDK que terá seu prórpio caminho e uso exclusivo no WSL. A mesma regra se 
aplicaria para o maven, mas não é caso.

Abre o terminal WSL e o primeiro passo é instalar a JDK de qualquer versão (de preferência 8+):

1. Instalar a JDK no WSL
```
sudo apt-get install openjdk-8-jdk
```

2. Verificar caminho onde foi instalada a JDK
```
readlink -f $(which java)
```
**Retorno:** /usr/lib/jvm/java-8-openjdk-amd64

3. Settar variável de ambiente de acordo com o caminho listado no comando anterior
```
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
```
- Caminho alternativo **(Opcional, mas caso não faça o caminho alternativo será necessário settar a variável de ambiente todas as vezes que um terminal novo é aberto):**
- Alterar o arquivo .bashrc
```
vi ~/.bashrc
```
- Colocar no arquivo
```
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
```
- Depois de salvar o arquivo execute o comando
```
source ~/.bashrc
```
4. Verificar se a variável de ambiente está no caminho settado anteriormente rodando o 
comando
```
echo $JAVA_HOME
```