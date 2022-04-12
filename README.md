# InstalandoChocolatey
Como instalar o chocolatey local

Olá, hoje gostaria de compartilhar uma experiência de instalação do chocolatey para testes usando o K6.
Para iniciar, precisamos verificar as politicas de execução do powershell.
Para isso, use a seguinte linha de comando:<br />

**@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "[System.Net.ServicePointManager]::SecurityProtocol = 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"**
<br />
Se você não ver nenhum erro, você está pronto para usar o Chocolatey! Digite choco ou choco -?<br />

**Get-ExecutionPolicy**
Se o powershell retornar a mensagem *"Restricted"*, use o seguinte comando para verificar a lista de politicas de execução:
**Get-ExecutionPolicy -List**, com isso você irá visualizar o seguinte retorno:

 Scope ExecutionPolicy<br />
        ----- ---------------<br />
MachinePolicy       Undefined<br />
   UserPolicy       Undefined<br />
      Process       Undefined<br />
  CurrentUser       Undefined<br />
 LocalMachine       Undefined<br />

Então execute:
**Set-ExecutionPolicy AllSigned**<br />

Você receberá a seguinte mensagem:<br />
*Alteração da Política de Execução
A política de execução ajuda a proteger contra scripts não confiáveis. A alteração da política de execução pode
implicar exposição aos riscos de segurança descritos no tópico da ajuda about_Execution_Policies em
https://go.microsoft.com/fwlink/?LinkID=135170. Deseja alterar a política de execução?
[S] Sim  [A] Sim para Todos  [N] Não  [T] Não para Todos  [U] Suspender  [?] Ajuda (o padrão é "N"):* <br />

Nesse momento, você pode responder Sim para todos [A]<br />
Logo, execute o comando: *Get-ExecutionPolicy* - Então você irá visualizar o retorno AllSigned<br />

Nesse momento, para confirmar a instalação do chocolatey, execute o comando *choco -?* e você irá visualizar a versão instalada do chocolatey!<br />
**Chocolatey v0.11.3** (essa versão foi a versão instalada no momento que estava sendo escrito esse documento)

Logo, o objetivo era para efetuar a instalação do K6 para testes de performance, nesse momento, com o chocolatey instalado, será possivel instalar o K6 na sua máquina:<br />
**choco install k6**<br />

Obrigado pela leitura!

*Referência:<br />
https://docs.chocolatey.org/en-us/choco/setup*
 
