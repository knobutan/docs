---

copyright:
  years: 2015, 2016

---


{:shortdesc: .shortdesc} 
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

#Monitorando e criando logs com o Cloud Foundry
{: #monitoringandlogging}

Última atualização: 28 de outubro de 2016
{: .last-updated}

Ao monitorar seus apps e revisar logs, é possível seguir a execução do aplicativo e o fluxo de dados para obter um melhor entendimento de sua implementação. Além disso, é possível reduzir o tempo e o esforço necessários para localizar problemas e repará-los.
{:shortdesc}

Os aplicativos {{site.data.keyword.Bluemix}} podem ser amplamente distribuídos, aplicativos multi-instância, e a execução do aplicativo e seus dados pode ser compartilhada entre vários serviços. Nesse ambiente complexo, o monitoramento dos apps e a revisão dos logs é importante para o gerenciamento dos apps.

##Monitoramento e criação de log de aplicativos Cloud Foundry
{: #monitoring_logging_bluemix_apps}

O {{site.data.keyword.Bluemix_notm}} possui um mecanismo de criação de log integrado para produzir arquivos de log para seus apps enquanto estão sendo executados. Nos logs, é possível visualizar os erros, os avisos e as mensagens informativas produzidas para o app. Além disso, também é possível configurar o app para gravar mensagens de log para o arquivo de log. Para
obter mais informações sobre formatos de log e como visualizar os logs, consulte [Criação de log para aplicativos em execução no Cloud Foundry](#logging_for_bluemix_apps).

Monitorar o app permite ver e controlar a implementação do app. Com o monitoramento, é possível realizar as tarefas a seguir:

* Coletar e monitorar informações de desempenho para instâncias do app e verificar se elas são funcionais.
* Obter insight sobre operações do aplicativo, por exemplo, detectar os gargalos em potencial ou quando há necessidade de upgrades.
* Estimar uso do recurso e encargos.

Para operações estáveis de suas implementações na plataforma {{site.data.keyword.Bluemix_notm}}, você deseja detectar problemas rapidamente e determinar as causas de forma eficiente. Para realizar esse objetivo, mantenha a resolução de problemas em mente ao projetar seus apps e use serviços ou ferramentas para monitoramento e criação de log quando seu app for implementado no {{site.data.keyword.Bluemix_notm}}.

###Monitorando apps em execução no Cloud Foundry
{: #monitoring_bluemix_apps}

Quando você estiver usando a infraestrutura do Cloud Foundry para executar seus apps no {{site.data.keyword.Bluemix_notm}}, você desejará manter informações de desempenho, como status de funcionamento, uso de recursos e métricas de tráfego. Com essas informações de desempenho, será possível, então, tomar decisões ou executar ações adequadamente.

Para monitorar apps {{site.data.keyword.Bluemix_notm}}, use um dos métodos a seguir:

* Serviços {{site.data.keyword.Bluemix_notm}}. O Monitoring and Analytics oferece um serviço que pode ser usado para monitorar o desempenho do aplicativo. Além disso, esse serviço também fornece recursos analíticos, como análise de log. Para obter mais informações, consulte [Monitoring and
Analytics](../services/monana/index.html).
* Opções de terceiros. Por exemplo, [New Relic](http://newrelic.com/){:new_window}.

###Criação de log para apps em execução no Cloud Foundry
{: #logging_for_bluemix_apps}

Os arquivos de log são criados automaticamente quando se está usando a infraestrutura do Cloud Foundry para executar seus apps no {{site.data.keyword.Bluemix_notm}}. Ao encontrar erros em qualquer estágio de implementação no tempo de execução, é possível verificar os logs para obter pistas que podem ajudar a resolver seu problema.

###Retenção de log
{: #log_retention}

Em apps {{site.data.keyword.Bluemix_notm}} Public Cloud Foundry, os dados do log são armazenados por 7 dias, por padrão.

<!-- 2016.1.27: original shortdes: Log files are automatically created when you are using the Cloud Foundry infrastructure to run your apps on {{site.data.keyword.Bluemix_notm}}. You can view logs from the {{site.data.keyword.Bluemix_notm}} Dashboard, the cf command line interface, or external hosts. You can also filter the logs to see the parts that you are interested in. -->



###Formato do log
{: #log_format}

Os logs para aplicativos {{site.data.keyword.Bluemix_notm}} são exibidos em um formato fixo, semelhante ao padrão a seguir:

```
         1         2         3         4         5
12345678901234567890123456789012345678901234567890
--------------------------------------------------
aaaa-MM-ddTHH:mm:ss:SS-0500 [App/0]      OUT <message>
```
{:screen}

Toda entrada de log contém quatro campos. Consulte a lista a seguir para obter uma breve descrição de cada campo:

<dl>
<dt><strong>Registro de data e hora</strong></dt>
<dd>
<pre class="pre screen"><code>yyyy-MM-ddTHH:mm:ss:SS-0500</code></pre>
<p>Colunas: 1 – 27</p>
<p>O tempo da instrução de log. O registro de data e hora é definido até o milissegundo.</p>
</dd>

<dt><strong>Componente</strong></dt>
<dd>
<pre class="pre screen"><code>[App/0]</code></pre>
<p>Colunas: 29 – 40</p>
<p>O componente que produz logs. A lista a seguir fornece a definição para todos os componentes:</p>

<dl>
<dt><strong>AP
</strong></dt>
<dd>Aplicativo. O componente APP é seguido por uma barra e um dígito que indica a instância do aplicativo. Em que 0 é a primeira instância, 1 é a segunda e assim por diante.</dd>

<dt><strong>API</strong></dt>
<dd>API do Cloud Foundry.</dd>

<dt><strong>DEA</strong></dt>
<dd>Droplet Execution Agent.</dd>

<dt><strong>LGR</strong></dt>
<dd>Loggregator.</dd>

<dt><strong>RTR</strong></dt>
<dd>Roteador.</dd>

<dt><strong>STG</strong></dt>
<dd>Preparação.</dd>
</dl>
</dd>

<dt><strong>Stream
</strong></dt>
<dd>
<pre class="pre screen"><code>OUT </code></pre>
<p>Colunas: 42 – 44</p>
<p>O fluxo para o qual a mensagem de log é gravada. <samp class="ph codeph">OUT</samp> refere-se ao fluxo <samp class="ph codeph">stdout</samp> e <samp class="ph codeph">ERR</samp> refere-se ao fluxo <samp class="ph codeph">stderr</samp>.</p>
</dd>

<dt><strong>Mensagem</strong></dt>
<dd>
<pre class="pre screen"><code>&lt;<var class="keyword varname">Mensagem</var>&gt;</code></pre>
<p>Colunas: 46 – término da linha</p>
<p>A mensagem que é emitida pelo componente. A mensagem varia, dependendo do contexto.</p>
</dd>

</dl>

###Visualizando logs
{: #viewing_logs}

É possível visualizar os logs para seus apps do Cloud Foundry em três locais:

  * [O Painel do {{site.data.keyword.Bluemix_notm}}](#viewing_logs_UI){:new_window}
  * [Interface da Linha de Comandos](#viewing_logs_cli){:new_window}
  * [Hosts de logs externos](#thirdparty_logging){:new_window}

#### Visualizando logs do Painel do
{{site.data.keyword.Bluemix_notm}}
{: #viewing_logs_UI}

Para ver os logs de implementação ou de tempo de execução, conclua as etapas a seguir:
1. Efetue login no {{site.data.keyword.Bluemix_notm}} e, em seguida, clique no quadrado de seu app. A página de detalhes do app é exibida.
2. Na barra de navegação, clique em **Logs**.

No console de **Logs**, é possível visualizar os logs recentes para seu app ou acompanhar logs em tempo real. Além disso, é possível filtrar logs por tipo de log e canal.

**Notas:** logs não são persistidos entre travamentos e implementações de apps.



#### Visualizando logs a partir da interface da linha de comandos
{: #viewing_logs_cli}

Escolha entre as opções a seguir para visualizar logs a partir da interface da linha de comandos:

<ul>
<li>Ajustando logs ao implementar apps.
<p>Use o comando **cf logs** para exibir logs a partir de seu app e dos componentes do sistema que interagem com ele durante a implementação de apps no {{site.data.keyword.Bluemix_notm}}. É possível digitar os comandos a seguir na interface de linha de comandos cf. Para obter informações adicionais sobre cf logs, consulte <a href="http://docs.cloudfoundry.org/devguide/deploy-apps/streaming-logs.html" target="_blank">Tipos de log e suas mensagens no Cloud Foundry</a> </p>
<dl>
<dt><strong>cf logs <var class="keyword varname">appname</var> --recent</strong></dt>
<dd>Exibir logs do passado recente.</dd>

<dt><strong>cf logs <var class="keyword varname">appname</var></strong></dt>
<dd>Exiba logs que são gerados a partir do momento em que você executa este
comando.</dd>
</dl>
<div class="note tip"><span class="tiptitle">Dica:</span> ao executar o comando <span class="keyword cmdname">cf push</span> ou <span class="keyword cmdname">cf
start</span> em uma janela de linha de comandos, é possível inserir <samp class="ph codeph">cf
logs appname --recent</samp> em outra janela de linha de comandos para ver
os logs em tempo real. </div>
</li>

<li>Visualizando logs após a implementação dos apps.

<p>Se a criação de log do aplicativo estiver ativada, será possível visualizar os logs de aplicativo a seguir se você encontrar problemas com o app no tempo de execução. Os logs do aplicativo podem ajudar a determinar a causa do erro.</p>

<dl><strong>buildpack.log</strong></dt>
<dd>
<p>Esse arquivo de log registra eventos informativos de baixa granularidade para
depuração. É possível usar esse log para solucionar problemas de
execução de buildpack.</p>
<p>Para gerar dados para o arquivo <span class="ph filepath">buildpack.log</span>, deve-se ativar o rastreio do buildpack usando o comando a seguir:
   <pre class="pre">cf set-env <var class="keyword varname">appname</var> JBP_LOG_LEVEL DEBUG</pre>
<p>
<p>Para visualizar esse log, insira o comando a seguir:
<pre class="pre">cf files <var class="keyword varname">appname</var> app/.buildpack-diagnostics/buildpack.log</pre>
</p>
</dd>

<dt><strong>staging_task.log</strong></dt>
<dd><p>Esse arquivo de log registra mensagens depois das principais etapas da
tarefa de preparação. É possível usar esse log para solucionar problemas de preparação.</p>
<p>Para visualizar esse log, insira o comando a seguir:
<pre class="pre">cf files <var class="keyword varname">appname</var> logs/staging_task.log</pre>
</p>
</dd>
</dl>
</li></ul>


**Nota:** para obter informações sobre como ativar a criação de log do aplicativo, consulte [Depurando erros de tempo de execução](../debug/index.html#debugging-runtime-errors).




###Filtrando logs
{: #filtering_logs}

Para visualizar logs em que você está interessado ou excluir o conteúdo que você não deseja visualizar, é possível usar o comando **cf logs** com opções de filtragem, como **cut** e **grep** na interface de linha de comandos cf.

* Para visualizar uma parte, em vez dos logs detalhados completos, use a opção **cut**. Por exemplo, para exibir as informações do componente e da mensagem, use o comando a seguir:
```
cf logs appname --recent | cut -c 29-40,46- 
```

Para obter mais informações sobre a opção **grep**, digite cut --help.
* Para exibir entradas de log que contêm determinadas palavras-chave, use a opção **grep**. Por exemplo, para exibir entradas de log que contêm a palavra-chave `[APP`, é possível usar o comando a seguir:

```
cf logs appname --recent | grep '\[App'
```
Para obter mais informações sobre a opção **grep**, digite `grep --help`.



### Configurando hosts de logs externos
{: #thirdparty_logging}

O {{site.data.keyword.Bluemix_notm}} mantém
uma quantia limitada de informação de log na memória. Quando as informações são
registradas, as informações antigas são substituídas pelas informações mais novas. Para manter todas as informações de log, é possível salvar seus logs em um host de log externo, como um serviço de gerenciamento de log de terceiro ou outro host.

Para mover logs de seu app e do sistema para um host de log externo, conclua as etapas a seguir:

  1. Determine o terminal de criação de log. 
     
	 É possível enviar logs a um agregador de log de terceiro, como Papertrail, Splunk ou Sumologic. Também é possível enviar logs a um host de syslog, um host de syslog criptografado com TLS (Segurança da camada de transporte) ou um terminal HTTPS POST. Os métodos para obter terminais de criação de log variam para diferentes hosts de logs.

  2. Crie uma instância de serviço fornecida pelo usuário.
     
	 Use o comando `cf create-user-provided-service` (ou `cups`, uma versão curta do comando) para criar uma instância de serviço fornecido pelo
usuário: 
	 ```
	 cf create-user-provided-service <service_name> -l <logging_endpoint>
	 ```
	 &lt;service_name&gt;
	 
	 O nome da instância de serviço fornecida pelo usuário.
	 
	 &lt;logging_endpoint&gt;
	 
	 O terminal de criação de log para o qual o {{site.data.keyword.Bluemix_notm}} envia logs. Consulte a tabela a seguir para substituir *logging_endpoint* por seu valor:
	 
	 <table>
     <thead>
     <tr>
     <th>Terminal de criação de log</th>
     <th>Comando:</th>
	 <th>Notas</th>
     </tr>
     </thead>
     <tbody>
     <tr>
     <td>host syslog</td>
     <td>`cf cups my-logs -l syslog://HOST:PORT`</td>
	 <td>Por exemplo, para ativar a criação de log para Papertrail, digite `cf cups my-logs -l syslog://<papertrail-url>`. Substitua `<papertrail-url>` pela URL de seu terminal de criação de log a partir do Papertrail.</td>
     </tr>
	 <tr>
     <td>host syslog-tls</td>
     <td>`cf cups my-logs -l syslog-tls://HOST:PORT`</td>
	 <td>O certificado deve ser confiável por uma autoridade de certificação. Não use certificados autoassinados.</td>
     </tr>
	 <tr>
     <td>HTTPS POST</td>
     <td>`cf cups my-logs -l https://HOST:PORT`</td>
	 <td>Esse terminal deve estar na Internet pública e acessível pelo {{site.data.keyword.Bluemix_notm}}</td>
     </tr>
     </tbody>
     </table>	
  3. Ligue a instância de serviço ao seu app.

	 Use o comando a seguir para ligar a instância de serviço a seu app: 
	
	 ```
	 cf bind-service <appname> <service_name>
	 ```
	 &lt;appname&gt;
	 
	 O nome do seu app.
	 
	 &lt;service_name&gt;
	 
	 O nome da instância de serviço fornecida pelo usuário.
	 
  4. Remonte o app. 
     Digite `cf restage appname` para que as mudanças entrem em vigor. 

#### Visualizando logs de hosts externos
{: #viewing_logs_external}

	 
Quando os logs forem gerados, após um breve atraso, será possível visualizar mensagens em seu host do log externo semelhantes às mensagens visualizadas a partir da interface com o usuário do {{site.data.keyword.Bluemix_notm}} ou a partir da interface da linha de comandos cf.  Se você tiver várias instâncias de seu app, os logs serão agregados e será possível ver todos os logs de seu app. Além disso, os logs são persistidos entre travamentos e implementações de apps.

**Nota:** os logs visualizados na interface de linha de comandos não estão no formato syslog e podem não corresponder exatamente às mensagens exibidas em seu host do log externo. 

### Exemplo: transmitindo logs do aplicativo Cloud Foundry para o Splunk 
{: #splunk}

Neste exemplo, uma desenvolvedora chamada Jane cria um servidor virtual usando o IBM Virtual Servers Beta e a imagem do Ubuntu.  A Jane tenta transmitir logs do aplicativo Cloud Foundry a partir do
{{site.data.keyword.Bluemix_notm}} para o Splunk. 

  1. Para começar, a Jane configura o Splunk.

     a. A Jane faz download do Splunk Light a partir do [Site de Download Splunk Light](https://www.splunk.com/en_us/download/splunk-light.html){:new_window} e, em seguida,
o instala usando o comando a seguir. O software é instalado em */opt/splunk*. 
       
	    ```
        dpkg -i  ~/splunklight-6.3.0-aa7d4b1ccb80-linux-2.6-amd64.deb
        ```
	   
     b. A Jane instala e corrige o complemento de tecnologia de syslog RFC5424 para integrar com o {{site.data.keyword.Bluemix_notm}}. Para obter mais informações sobre as instruções para
instalar o complemento, consulte a [Diretriz do Cloud Foundry](https://docs.cloudfoundry.org/devguide/services/integrate-splunk.html){:new_window}.  

	    A Jane instala o complemento usando os comandos a seguir:
        
	    ```
        cd /opt/splunk/etc/apps
        tar xvfz ~/rfc5424-syslog_11.tgz
        ```
	   
        Em seguida, a Jane corrige o complemento substituindo */opt/splunk/etc/apps/rfc5424/default/transforms.conf* por um novo arquivo *transforms.conf* que consiste no
texto a seguir:
	   
	    ```
        [rfc5424_host]
        DEST_KEY = MetaData:Host
        REGEX = <\d+>\d{1}\s{1}\S+\s{1}(\S+)
        FORMAT = host::$1

        [rfc5424_header]
        REGEX = <(\d+)>\d{1}\s{1}\S+\s{1}\S+\s{1}(\S+)\s{1}(\S+)\s{1}(\S+)
        FORMAT = prival::$1 appname::$2 procid::$3 msgid::$4
        MV_ADD = true
        ```
        {:screen}	   

     c. Após o Splunk ser configurado, a Jane deve abrir algumas portas na máquina do Ubuntu para aceitar o dreno de syslog recebido (porta 5140) e a UI da World Wide Web do Splunk (porta 8000) porque
o servidor virtual {{site.data.keyword.Bluemix_notm}} possui o firewall configurado por padrão.
	   
	    **Nota:** A configuração de iptable é feita aqui para propósitos de avaliação da Jane e é provisória. Para definir a configuração de firewall no servidor virtual Bluemix em
produção, consulte a documentação de [Network Security Groups](https://new-console.ng.bluemix.net/docs/services/networksecuritygroups/index.html){:new_window}, para obter detalhes.
	 
	   ```
	   iptables -A INPUT -p tcp --dport 5140 -j ACCEPT
       iptables -A INPUT -p tcp --sport 5140 -j ACCEPT
       iptables -A INPUT -p tcp --dport 8000 -j ACCEPT
       iptables -A INPUT -p tcp --sport 8000 -j ACCEPT
	   ```
	   {:screen}	
	  
	   Em seguida, a Jane executa o Splunk usando o comando a seguir:

       ```
	   /opt/splunk/bin/splunk start --accept-license
       ```
		
  2. A Jane define as configurações do Splunk para aceitar o dreno de syslog a partir do {{site.data.keyword.Bluemix_notm}}. Ela deve criar uma entrada de dados para o dreno de syslog.

     a. A partir da interface da web do Splunk, a Jane clica em **Dados > Entradas de dados**. Uma lista de tipos de entrada que o Splunk suporta é exibida. 
	 
     b. Ela seleciona **TCP**, porque o dreno de syslog usa o protocolo TCP.
	 
     c. Na área de janela **TCP**, ela insere **5140** no campo **Porta**, deixa os campos restantes em branco e, em seguida, clica em
**Avançar**.
	 
     d. A partir da lista de **Tipos de Origem**, ela seleciona **Não categorizados > rfc5424_syslog**.
	 
     e. Para o tipo de **Método**, ela seleciona **IP**.
	 
     f. No campo de **Índice**, a Jane clica em **Criar um novo índice**. Ela nomeia o novo índice "bluemix" e, em seguida, clica em
**Salvar**.
	 
     g. Finalmente, na janela **Revisar**, a Jane confirma que a configuração está correta e, em seguida, clica em **Enviar** para ativar essa entrada de dados.

  3. Em {{site.data.keyword.Bluemix_notm}}, a Jane cria um serviço de dreno de syslog e liga o serviço a um aplicativo.

     a. A Jane cria um serviço de dreno de syslog usando o comando a seguir a partir da interface da linha de comandos de cf:
	 
     ```
     cf cups splunk -l syslog://dummyhost:5140
     ```
        
     **Nota:** *dummyhost* não é o nome real. Ele é usado para ocultar o nome do host real. 

     b. A Jane liga o serviço de dreno de syslog a um aplicativo em seu espaço e, em seguida, organiza novamente o aplicativo.
	 
	 ```
     cf bind-service myapp splunk
     cf restage myapp
     ```
		

A Jane testa o seu aplicativo e, em seguida, digita a sequência de consultas a seguir na interface da web do Splunk:

```
source="tcp:5140" index="bluemix" sourcetype="rfc5424_syslog"
```

A Jane vê um fluxo de logs em sua interface da web do Splunk. Embora o Splunk que a Jane instala seja o Splunk Light, ela ainda pode reter 500 MB de logs por dia.  




