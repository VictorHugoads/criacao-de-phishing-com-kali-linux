# Criação de phishing com kali linux

Configurações: 

Antes de iniciar o setoolkit, precisamos realizar algumas configurações para utilizá-lo com o apache2. Por default, as configurações do setoolkit ficam no arquivo set.config no path -> /etc/setoolkit/set.config/ .

![image](https://github.com/user-attachments/assets/affa30e4-82dd-4b62-bb60-5f0752da35ea)

Vamos abrir o arquivo com um editor de texto e editar as linhas sublinhadas nas imagens a seguir, deixando da forma como estão exibidas neste exemplo:

![image](https://github.com/user-attachments/assets/8f5d92c3-e693-492e-812d-8e9c38edef16)

![image](https://github.com/user-attachments/assets/ffc15ef4-75e8-4735-9768-3363a9fc8a83)

![image](https://github.com/user-attachments/assets/774f3fde-4dde-401e-8ee2-3d95a750ddee)

OBS: Caso você tenha definido outro diretório raiz para o Apache que não seja o padrão, acrescente esse path no lugar do caminho /var/www/html/ .


Passo 1:


Com as configurações previamente realizadas, abra seu terminal como root e execute o seguinte comando:

```bash
$ setoolkit
```

Selecione a primeira opção na tela que será exibida, "Social-Engineering Attacks".

![image](https://github.com/user-attachments/assets/a3babe04-6b7d-4e71-aef4-acbc52d22202)

Passo 2:

Selecione a segunda opção, "Website Attack Vectors".

![image](https://github.com/user-attachments/assets/c94946ba-8e9a-4b7a-88d8-1eb5319354b3)

Passo 3:

Selecione a terceira opção, "Credential Harvester Attack Method".

![image](https://github.com/user-attachments/assets/d904a81b-9fe1-422e-9edf-7e4abd1ce4b7)


Passo 4:

Selecione a segunda opção, "Site Cloner".

![image](https://github.com/user-attachments/assets/2ed32e26-dc00-4474-9a66-2a6e92e50f95)

Essa opção possibilita a criação de uma página estática falsa, clonando qualquer página que utilize formulários com método POST e executando-a em um servidor privado. Caso o usuário preencha os dados no formulário falso, os valores inseridos serão capturados, e o usuário será redirecionado para a página original que ele estava tentando acessar (a página clonada).


Passo 5:

Nesta etapa, é preciso informar o IP hospedeiro da página fake e o site a ser clonado via protocolo HTTP. O setoolkit já sugere o ip do host no momento da seleção da ferramenta Site Cloner. Basta pressionar Enter caso queira utilizar o IP sugerido ou adicionar outro de sua preferência (Atenção para manter as mesmas configurações no apache2. As portas também precisam ser as mesmas no apache2 e no setoolkit, que escutam na porta 80 por default). Em seguida, é preciso inserir a URL do site que será clonado via HTTP. O processo pode demorar alguns minutos.


![image](https://github.com/user-attachments/assets/0715dc12-002b-4bc9-9c45-38c6de6241c1)


Passo 6:

Após o fim do processo, é possível que o terminal nos informe que o service do apache2 pode não estar rodando e se queremos que o setoolkit o inicie para nós. Vamos confirmar com a letra y.

![image](https://github.com/user-attachments/assets/393a1b7e-6fca-44f6-a4e6-84fa13b14761)


Onde os logs serão salvos?

Logo após a cópia do site ter sido concluída, somos informados que o serviço já está no ar e que os logs serão salvos no diretório raiz do apache, sob o nome de harvester seguido das informações da data e no formato .txt.

![image](https://github.com/user-attachments/assets/34113021-ee10-435f-8c37-e4477da5dde0)


Acessando a página clonada:

Agora, ao inserirmos o IP na barra de endereços do navegador, será exibida uma versão falsa da página clonada. Depois de preecher o formulário e submeter, a pessoa será redirecionada ao site original e poderemos ter acesso aos dados inseridos no formulário.

![image](https://github.com/user-attachments/assets/e2de7882-d221-478f-809e-4125570f79d9)


Resultado:

Pronto! Se tudo foi configurado corretamente, os valores inseridos no formulário estarão armazenados no local especificado pelo setoolkit, que, neste exemplo, corresponde ao diretório raiz do Apache2: /var/www/html.

Ao abrir o terminal e navegar até esse diretório, será possível visualizar o arquivo harvester_DATADEUSO.txt.


![image](https://github.com/user-attachments/assets/68b0e0b6-8eee-4f97-998f-c2a34856f2b6)

Utilizando o comando cat para exibir o conteúdo do arquivo ou simplesmente abrindo com um editor de texto, podemos ver o registro dos valores inseridos pela pessoa no formulário.


![image](https://github.com/user-attachments/assets/e7bf6f05-066d-4828-bb55-1d50c7a4c7c2)





ATENÇÂO: Este conhecimento deve ser utilizado com responsabilidade e ética. Ferramentas como esta foram criadas para fins educativos e de segurança, como a realização de testes em ambientes autorizados. O uso indevido, especialmente para prejudicar terceiros, pode ter sérias consequências legais e éticas. Lembre-se: inteligência é saber quando e como usar o que você aprende para o bem.
















