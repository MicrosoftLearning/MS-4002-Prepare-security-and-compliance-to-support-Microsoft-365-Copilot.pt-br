## Locatários do WWL – Termos de uso

Se você estiver recebendo um locatário como parte de uma entrega de treinamento com instrutor, observe que o locatário é disponibilizado com a finalidade de dar suporte aos laboratórios práticos no treinamento com instrutor. 

Os locatários não devem ser compartilhados ou usados para fins fora dos laboratórios práticos. O locatário usado neste curso é um locatário de avaliação e não pode ser usado ou acessado após o fim da aula e não está qualificado para extensão. 

Os locatários não podem ser convertidos em uma assinatura paga. Os locatários obtidos como parte deste curso permanecem a propriedade da Microsoft Corporation e reservamos o direito de obter acesso e a qualquer momento. 

# Roteiro de Aprendizagem 1 – Laboratório 1 – Exercício 1 – Inicializar seu locatário do Microsoft 365 

A Adatum Corporation é uma subsidiária da Contoso Electronics. A Adatum executa seus aplicativos herdados (como o Microsoft Exchange Server 2019) em uma implantação local. No entanto, a empresa fez recentemente uma assinatura do Microsoft 365, criando, assim, uma implantação híbrida na qual precisa sincronizar suas implantações no local e na nuvem. 

Como administrador do Microsoft 365 da Adatum, você foi encarregado de implantar o Microsoft 365 na implantação híbrida do Adatum usando um ambiente de laboratório virtualizado. Neste exercício, você vai configurar o locatário de avaliação do Microsoft 365 do Adatum e seu instrutor orientará você sobre como obter suas credenciais do Microsoft 365 em seu ambiente de laboratório hospedado. Você usará essas credenciais em todos os outros laboratórios deste curso. 

Em seu ambiente de laboratório, o provedor de hospedagem do laboratório já obteve um locatário de avaliação do Microsoft 365 para você. O provedor de laboratório também criou duas contas de administrador que você usará em seu ambiente de laboratório da VM: 

- Uma conta de administrador do AD DS para o ambiente local da Adatum (Adatum\Administrador).
- Uma conta padrão de administrador de locatário no Microsoft 365 (o nome de exibição dessa conta de usuário é MOD Administrator). 

Você fará login no Client 1 PC (LON-CL1) usando a conta Adatum\Administrator. Quando acessar o Microsoft 365 pela primeira vez, você fará login inicialmente usando a conta de administrador de locatário do Microsoft 365 (MOD Administrator). Em seguida, você atualizará o perfil organizacional do Microsoft 365 da Adatum e preparará o locatário para o Microsoft Entra ID e para os próximos laboratórios usando o Gerenciamento de Direitos de Informação, alertas de auditoria e o Microsoft Graph PowerShell.


### Tarefa 1 – Entre no Centro de administração do Microsoft 365

Ao longo dos laboratórios deste curso, você desempenhará o papel de Holly Dickson, a administradora do Microsoft 365 da Adatum. Como Holly, você será responsável por configurar o perfil da empresa para seu locatário de avaliação do Microsoft 365. Nesta tarefa, você configurará as opções necessárias para o locatário da Adatum. Como a Holly ainda não criou uma conta de usuário pessoal do Microsoft 365 para si mesma (o que será feito no próximo exercício de laboratório), ela entrará inicialmente no Microsoft 365 usando a conta de administrador de locatário padrão do Microsoft 365 e a senha que foi criada pelo seu provedor de hospedagem de laboratório. Essa conta é a MOD Administrator, cujo alias é "admin". O nome de usuário dessa conta é admin@xxxxxZZZZZZ.onmicrosoft.com (onde xxxxxZZZZZZ o prefixo do locatário atribuído pelo seu provedor de hospedagem de laboratório); o nome de exibição para essa conta será MOD Administrator.

1. O provedor de hospedagem do laboratório fornecerá duas senhas que são usadas com as contas de usuário fictícias em seu locatário de avaliação do Microsoft 365. A conta Administrador MOD, que é o administrador padrão do locatário, recebeu a **Senha Administrativa**. Todos os outros usuários, mesmo aqueles a quem foi atribuída uma função de administrador, receberam a **Senha de Usuário**. <br>

    Por motivos de segurança, a Microsoft configurou o locatário de avaliação de modo que todos os usuários predefinidos tenham de alterar a senha na próxima entrada. <br>
 
    **Importante:** alguns provedores de hospedagem de laboratório podem fornecer os seguintes novos campos de senha que serão usados para armazenar as novas senhas que você atribuirá aos usuários na primeira vez que eles entrarem: <br>

    - **Nova senha administrativa** – Esta é a nova senha que você atribuirá ao administrador do MOD e Holly Dickson
    - **Nova senha de usuário** – Esta é a nova senha que você atribuirá a todos os outros usuários.

    Se esses dois novos campos de senha aparecerem em sua VM, insira uma nova senha para cada um deles. Esses novos valores de senha serão armazenados na VM e exibidos nas instruções do laboratório. <br>
 
    Outros provedores de hospedagem de laboratório podem não fornecer esses novos campos de senha. Nesses ambientes, é necessário anotar manualmente a nova senha que você planeja atribuir aos usuários que entrarem. <br>

    Ao criar suas novas senhas, tenha em mente as diretrizes de senha da Microsoft: <br>

    - Comprimento mínimo de 8 caracteres, com pelo menos:
       - 1 caractere maiúsculo
       - 1 caractere minúsculo
       - 1 caractere especial As senhas não serão validadas de acordo com os requisitos da Microsoft até que você altere a senha antiga na próxima entrada do usuário.

3. Ao abrir o ambiente de Máquina Virtual do provedor de hospedagem de laboratório, você precisa começar com a Client 1 VM (LON-CL1). Se o ambiente da VM abrir com uma das outras máquinas (como LON-DC1), então mude para **LON-CL1** agora.

4. Faça login na **LON-CL1** com a conta de **Administrador** que foi criada pelo provedor de hospedagem do laboratório com a senha **Pa55w.rd**. 

5. Na barra de tarefas localizada na parte inferior da tela, selecione o ícone do **Microsoft Edge**. Se for necessário, maximize a janela do navegador quando ela abrir.

6. No seu navegador Edge, vá para a página inicial do **Microsoft 365** inserindo a seguinte URL na barra de endereços: **https://portal.office.com** 

7. Na caixa de diálogo **Entrar**, insira o **Nome de Usuário Administrativo** fornecido pelo provedor de hospedagem do laboratório (esta é a conta de Administrador MOD) para o locatário de avaliação do Microsoft 365. O nome de usuário deve estar no formato de **admin@xxxxxZZZZZZ.onmicrosoft.com**, onde xxxxxZZZZZZ é o prefixo do locatário atribuído pelo seu provedor de hospedagem de laboratório. Selecione **Avançar**. <br/>

    **Observação:** Nas instruções de laboratório que aparecem em seu ambiente de laboratório de VM, seu provedor de hospedagem de laboratório pode fornecer a capacidade de selecionar um botão **Digitar texto** (ou equivalente) ao lado dos dados do recurso, como nomes de usuário, senhas, comandos do PowerShell e outros dados que devem ser inseridos ao longo desses laboratórios. Outros provedores de hospedagem de laboratório podem fornecer um método alternativo, como a possibilidade de copiar e colar essas informações. Aproveite essa funcionalidade para não ter que inserir manualmente essas informações. 

8. Na caixa de diálogo **Inserir senha**, insira a **Senha Administrativa** predefinida fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**. 

9. O provedor de hospedagem do laboratório pode ou não ter configurado a conta MOD de Administrador para exigir uma nova senha na entrada. Se for o caso, será exibida uma caixa de diálogo **Atualizar sua senha**. Se isso ocorrer, insira a **Senha Administrativa** fornecida pelo provedor de hospedagem do laboratório no campo **Senha atual** e, em seguida, insira a Nova Senha Administrativa nos campos **Nova senha** e **Confirmar senha**.

10. Se uma caixa de diálogo **Permanecer conectado?** aparecer, marque a caixa de seleção **Não mostrar isso novamente** e, a seguir, selecione **Sim**. 

11. Se uma caixa de diálogo **Bem-vindo ao Microsoft 365** aparecer no meio da tela, não existirá uma opção para fechá-la. Em vez disso, à direita da janela, selecione o ícone de seta para a frente (**>**) duas vezes e, em seguida, selecione o ícone de marca de seleção para avançar pelos slides nessa janela de mensagens. 

12. Se aparecer uma caixa de diálogo **Encontrar mais aplicativos** ou uma caixa de diálogo **Criar com o Microsoft 365**, selecione **X** no canto superior das caixas para fechá-las. Da mesma forma, se aparecer uma caixa de diálogo Entrar no Microsoft Edge, clique no botão **Não, obrigado**.

13. A página de **Boas-vindas ao Microsoft 365** aparece no navegador Edge na guia **Página Inicial | Microsoft 365**. Esta é a página inicial do Microsoft 365 do MOD Administrator. <br/>

    Observe que um ícone ou um círculo com "MA" (as iniciais de Administrador MOD) aparece no canto superior direito da tela. Alguns locatários de teste mostram um ícone; outros mostram as iniciais "MA" em um círculo; tudo depende de o provedor de hospedagem do laboratório ter adicionado um ícone à conta do Administrador MOD. O ícone ou as iniciais representam a conta **Administrador MOD**, que é a conta de administrador de locatário criada pelo provedor de hospedagem de laboratório com a qual você acabou de entrar. Se alguma das contas de usuário existentes do Microsoft 365 criadas pelo provedor de hospedagem de laboratório tiver uma imagem associada à conta, a imagem do usuário será exibida em vez das iniciais do usuário quando você entrar no Microsoft 365 como esse usuário. No entanto, quando um usuário, como o Administrador MOD, não tem uma foto atribuída, ou as iniciais do usuário são exibidas no lugar da foto, ou um ícone é exibido se um tiver sido atribuído à conta pelo seu provedor de hospedagem de laboratório. <br/>

    Na página **Bem-vindo ao Microsoft 365**, na lista de ícones de aplicativos que aparece no painel de navegação, selecione **Administrador**; isso abrirá o **Centro de administração do Microsoft 365** em uma nova guia do navegador. 

14. No **Centro de administração do Microsoft 365**, selecione **Mostrar tudo** no painel de navegação. Isso exibirá todas as opções de navegação do Centro de administração do Microsoft 365.

15. Permaneça conectado à **LON-CL1** com o Microsoft Edge aberto no **Centro de administração do Microsoft 365** para realizar a próxima tarefa.

### Tarefa 2: criar um tema personalizado para a equipe do projeto piloto da Adatum

Na tarefa anterior, você aprendeu que, quando alguém está conectado ao Microsoft 365, o sistema exibirá a fotografia dessa pessoa (se fornecida) ou suas iniciais, caso não haja foto. Holly Dickson, administradora do Microsoft 365 da Adatum, não está satisfeita em ver apenas uma imagem ou as iniciais do usuário conectado. Ela quer criar um tema personalizado para os membros de sua equipe do projeto piloto, para que o nome do usuário conectado também seja exibido. Ao final do projeto piloto, se os membros da equipe de projeto piloto preferirem esse design, ela configurará essa mesma opção no tema padrão para que seja aplicado a todos os usuários. 

Os temas personalizados devem ser associados a um ou mais grupos do Microsoft 365. Assim, para implementar essa alteração, Holly deve primeiro criar um grupo do Microsoft 365 para os membros da equipe do projeto piloto. Então, ela poderá criar um tema personalizado associado a esse grupo que permita a configuração de mostrar o nome do usuário conectado. Nesta tarefa, você criará um grupo do Microsoft 365 para os membros da equipe que participarão do projeto piloto do Microsoft 365 da Adatum. Em seguida, você criará um tema personalizado que exibe o nome do usuário conectado e atribuirá a equipe do projeto piloto a este tema. Você também verá outras opções que podem ser configuradas com temas personalizados e poderá fazer as alterações de cores que desejar.

**Importante:** No final desta tarefa, você tentará salvar o tema personalizado que você criou. Existe um problema de plataforma conhecido no centro de administração da Microsoft 365, em que, algumas vezes, o tema personalizado é salvo sem nenhum problema, mas outras vezes retorna uma mensagem que diz "Desculpe, não foi possível salvar seu tema". Tente novamente mais tarde.” Se receber essa mensagem, não há nada que você possa fazer além de seguir em frente. Tentar salvar o tema em um momento posterior geralmente irá retornar o mesmo erro. Esse problema não afetará nenhum laboratório futuro, a não ser que não irá exibir o nome do usuário ao lado do respectivo ícone ou iniciais de usuário na linha de título. Apesar desse problema conhecido, continuamos querendo que você execute essa tarefa para ganhar experiência na criação de um tema, mesmo que não seja salvo no seu locatário de avaliação.

1. Você ainda deve estar logado na LON-CL1 com a conta **adatum\administrador** e, no navegador Edge, ainda deve estar logado no Microsoft 365 como **Administrador MOD**. 

2. No **centro de administração do Microsoft 365**, selecione **Equipes e grupos** no painel de navegação e, em seguida, selecione no painel **Equipes e grupos ativos**. 

3. Na página **Equipes e grupos ativos**, temos uma guia para você conferir cada tipo de grupo. A guia **Equipes e grupos do Microsoft 365** é exibida por padrão. Essa guia mostra os grupos do Microsoft 365 existentes.  <br/>

    Selecione a opção **+Adicionar um grupo do Microsoft 365** que aparece na barra de menu acima da lista de grupos do Teams e do Microsoft 365. Isso inicia o assistente **Adicionar um grupo do Microsoft 365**. 

4. No assistente **Adicionar um grupo do Microsoft 365**, na página **Configurar o básico**, insira **Projeto piloto do M365** no campo **Nome**, e depois insira os **Membros da equipe do projeto piloto do Microsoft 365** no campo **Descrição** (observação: mesmo que você não insira uma descrição, ainda precisará selecionar este campo para habilitar o botão **Próximo**). Selecione **Avançar**.

5. Agora você atribuirá o MOD Administrator como proprietário do grupo **Projeto piloto do M365**. Na janela **Atribuir proprietários**, selecione **+Atribuir proprietários**.
    
6. No painel **Atribuir proprietários** que aparece, marque a caixa ao lado de **MOD Administrator** e selecione o botão **Adicionar (1)** na parte inferior do painel.

7. Na página **Atribuir proprietários**, o MOD Administrator deve aparecer como proprietário do grupo. Selecione **Avançar**.

8. Agora você vai adicionar membros ao grupo do projeto piloto do M365. Na página **Adicionar membros**, selecione **+Adicionar membros**.

9. No painel **Adicionar membros** que surge, marque as caixas de seleção ao lado dos seguintes usuários (em ordem alfabética): **Alex Wilber**, **Allan Deyoung**, **Diego Siciliani**, **Isaiah Langer**, **Joni Sherman**, **Lynne Robbins**, **Megan Bowen**, **MOD Administrator**, **Nestor Wilke**, e **Patti Fernandez**. Depois, selecione o botão **Adicionar (10)** na parte inferior do painel.

10. Na página **Adicionar membros**, confira se esses 10 usuários estão listados como membros do grupo. Se faltar alguém, selecione **+Adicionar membros** e adicione qualquer um dos 10 usuários que não foram incluídos anteriormente. Quando todos os 10 usuários aparecerem nesta página, selecione **Próximo**.

11. Na página **Editar configurações**, preencha as informações a seguir: <br/>

    - Insira **m365pilotproject** no campo **Endereço de email do grupo**.
    - No campo **Privacidade**, selecione **Privado**.
    - Na seção **Adicionar o Microsoft Teams ao seu grupo**, verifique se a caixa de seleção **Criar uma equipe para esse grupo** está marcada (maque-a se estiver em branco) e selecione **Próximo**.

12. Na página **Revisar e finalizar adição do grupo**, verifique as informações que você inseriu. Se precisar corrigir alguma coisa, selecione **Editar** na área específica, faça as correções necessárias e selecione **Próximo** para voltar à página. Depois que tudo estiver certo, selecione **Criar grupo**.

13. Quando a janela **Grupo do projeto piloto M365 criado** aparecer, veja o comentário no topo da página informando que pode levar até 5 minutos para o novo grupo aparecer na lista de Grupos ativos.  </br>

    Selecione **Fechar**. Isso te levará de volta à página **Equipes e grupos ativos**, que deve mostrar a guia **Grupos do Microsoft 365 e Teams**. Como o grupo do projeto piloto do M365 é um grupo do Microsoft 365, ele deverá aparecer nesta guia em algum momento. Se necessário, selecione a opção **Atualizar** na barra de menu até que o grupo apareça na lista de grupos do Microsoft 365 e Teams.

14. No **centro de administração do Microsoft 365**, selecione **Configurações** no painel de navegação e, a seguir, **Configurações**. 

15. Na janela **Configurações da organização**, a guia **Serviços** é exibida por padrão. Selecione a guia **Perfil da organização**.

16. A guia **Perfil da Organização** mostra a lista de dados do perfil da organização. Na lista de dados, selecione **Temas personalizados**.

17. No painel **Personalizar o Microsoft 365 para sua organização** que aparece, você pode personalizar o tema padrão que os usuários veem ao entrar no Microsoft 365 e adicionar mais temas personalizados. Você vai querer criar um novo tema personalizado que se aplique somente aos membros do grupo do **projeto piloto do M365** que você criou anteriormente, então selecione a opção **+Adicionar tema**.

18. No painel **Novo tema do grupo** que surge, a guia **Geral** é mostrada por padrão. Insira **Tema do projeto piloto do M365** no campo **Nome**.

19. Selecione o campo **Grupos**. Na lista de grupos que aparece, selecione **Projeto piloto do M365** se ele estiver na lista. <br/>

    **Observação:** Se **Projeto piloto M365** não estiver na lista de grupos, então insira **M365** no campo **Grupos**. Uma caixa de resultados da pesquisa deve aparecer mostrando o grupo **Projeto piloto do M365**. Selecione **Projeto piloto do M365**. 

20. Marque a caixa de seleção **Mostrar o nome de exibição do usuário**. Essa é a configuração que Holly quer personalizar para os membros da equipe do projeto piloto do M365. Essa opção mostra o nome do usuário conectado ao lado das respectivas iniciais em cada cabeçalho de janela.
 
21. Selecione a guia **Logotipos** e reserve algum tempo para avaliar suas opções. Faça o mesmo para a guia **Cores**. Observe as várias opções de tema e identidade visual que estão disponíveis para você atualizar. <br/>

    Para os fins deste laboratório, você pode alterar qualquer uma das opções ou deixar os valores padrão como estão. Por exemplo, no seu ambiente do mundo real, você pode adicionar o logotipo da sua empresa e definir a imagem em segundo plano como o padrão para todos os seus usuários. Para este laboratório, fique à vontade para alterar as cores do painel de navegação, a cor do texto, a cor do ícone e a cor dos detalhes. <br/>

    **Vá em frente e explore as diferentes opções para esse tema que serão usadas pelos membros da equipe do projeto piloto do Microsoft 365. Faça todas as alterações que quiser.** <br/>

    **Dica:** Alguns padrões de cor distraem os usuários esteticamente. Se você alterar qualquer cor, recomendamos que evite usar cores em alto contraste juntas, como cores de néon e cores em alta resolução como rosa brilhante e branco.

22. Selecione **Salvar**. 

    **Observação:** conforme mencionado anteriormente no início desta tarefa, existe um problema de plataforma conhecido no centro de administração da Microsoft 365, em que, algumas vezes, o tema personalizado é salvo sem nenhum problema, mas outras vezes retorna uma mensagem que diz "Desculpe, não foi possível salvar seu tema". Tente novamente mais tarde.” Se você receber essa mensagem, isso não afetará nenhum laboratório futuro. Como o tema personalizado não foi salvo, o sistema simplesmente não exibirá o nome do usuário ao lado do respectivo ícone ou iniciais do usuário na linha de título (além de que as alterações de cor que você tiver feito não aparecerão). Continuamos pedindo que você execute esta tarefa, mesmo podendo receber essa mensagem, para ganhar experiência ao criar um tema como esse. Se você receber esse erro, ignore a próxima etapa, que irá testar o tema personalizado. No entanto, você continua podendo executar as etapas restantes após a próxima etapa para aprender o que é o tema Padrão. Independentemente de o tema personalizado ter sido salvo ou não, feche o painel do **tema do projeto piloto do M365**.

23. Se seu tema personalizado não tiver sido salvo, prossiga para a próxima etapa. No entanto, se seu tema personalizado tiver sido salvo, clique no ícone **Atualizar** na parte superior da tela, ao lado da barra de endereços. Após a tela ter sido atualizada, observe como o nome do **Administrador MOD** aparece ao lado do círculo com as iniciais MA ou do ícone selecionado para essa conta pelo provedor de hospedagem do seu laboratório. Quando os membros da equipe do projeto piloto do Microsoft 365 fizerem login no Microsoft 365, esse tema personalizado exibirá o nome de usuário de cada um, da mesma forma que o nome de Administrador MOD aparece aqui. 

24. Na lista de dados do perfil da organização, selecione **Temas personalizados**.

25. No painel **Personalizar o Microsoft 365 para a sua organização** que aparece, veja como são mostrados o **tema Padrão** e o **tema do projeto piloto do M365** (se o tema tiver sido salvo na etapa anterior). Selecione o **Tema padrão**. 

26. No painel **Tema padrão**, perceba como a opção **Mostrar o nome de exibição do usuário** não está selecionada para o tema padrão. Se a Holly decidir mais tarde tornar a opção **Mostrar o nome de exibição do usuário** uma funcionalidade permanente, ela selecionará essa opção no painel **Tema padrão** para que se aplique a todos os usuários da Adatum, e excluirá o **Tema do projeto piloto do M365**. <br/>

    **Observação:** se você recebeu a mensagem de erro "Desculpe, não foi possível salvar seu tema" Tente novamente mais tarde.” quando tentou salvar seu tema personalizado anteriormente, selecione a opção **Mostrar o nome de exibição do usuário** no tema Padrão e, a seguir, selecione **Salvar**. Queremos que você veja o que acontece quando essa opção é selecionada, mesmo que você não tenha conseguido salvar seu tema personalizado. Se você definir essa opção no tema Padrão, selecione o ícone **Atualizar** na parte superior da tela, à esquerda da barra de endereços. Após a tela ter sido atualizada, observe como o nome do **Administrador MOD** aparece à esquerda do círculo com as iniciais MA ou do ícone selecionado para essa conta pelo provedor de hospedagem do seu laboratório.
 
27. Feche o painel do **tema Padrão**.

28. Permaneça conectado à **LON-CL1** com o Microsoft Edge aberto no **Centro de administração do Microsoft 365** para realizar a próxima tarefa.


### Tarefa 3: Instalar o PowerShell do Microsoft Graph 

O Microsoft Graph PowerShell é necessário para realizar várias tarefas de configuração durante a instalação do Microsoft 365. Como os próximos exercícios de laboratório farão uso do Windows PowerShell para executar essas tarefas, o primeiro passo é instalar o módulo do Microsoft Graph PowerShell. Este módulo permite que você realize várias tarefas de administração de usuários e da organização do Microsoft 365 através do PowerShell. É ótimo para tarefas em massa, como redefinições de senha, políticas de senha, gerenciamento de licenças e relatórios, entre outros.  

1. Na LON-CL1, você ainda deve estar conectado como a conta **adatum\administrador**. Para instalar o Microsoft Graph PowerShell, você precisa abrir uma instância elevada do **Windows PowerShell**. Clique com o botão direito do mouse no ícone **Windows (Iniciar)** no canto inferior esquerdo da barra de tarefas e, em seguida, clique em **Windows PowerShell (Admin)**.

2. Maximize sua janela do PowerShell. No **Windows PowerShell**, digite o comando a seguir no prompt de comando para instalar o módulo do Microsoft Graph PowerShell na Galeria do PowerShell e pressione Enter: <br/>

        Install-Module Microsoft.Graph -Scope CurrentUser

3. Você será solicitado a confirmar se deseja instalar o módulo de um repositório não confiável (PSGallery). Insira **A** para selecionar **[A] Sim para Todos** e pressione Enter.  <br/>

    **Observação:** sua resposta iniciará a instalação de todos os submódulos do Microsoft Graph. Após as mensagens de instalação de cada submódulo serem exibidas, ainda levará cerca de 5 a 10 minutos adicionais para concluir a instalação do Microsoft Graph PowerShell. Durante esse tempo, o cursor continuará piscando abaixo da mensagem de repositório não confiável. <br/>

    **Este pode ser um bom momento para fazer uma pausa.**

4. Um prompt de comando aparecerá assim que o Microsoft Graph PowerShell for instalado. Agora você verá a lista de sub-módulos que foram instalados. Para fazer isso, execute o comando a seguir:

        Get-InstalledModule Microsoft.Graph.* | select *name*

5. Verifique se a lista inclui os três submódulos a seguir, que serão usados nos próximos exercícios de laboratório: 

    - Microsoft.Graph.Groups
    - Microsoft.Graph.Identity.DirectoryManagement
    - Microsoft.Graph.Users
    
    Se todos os três sub-módulos estiverem presentes na lista, prossiga para a próxima etapa. No entanto, se algum um desses três sub-módulos não aparecer na lista, execute o seguinte comando do PowerShell para instalar manualmente o sub-módulo que está faltando:

        Install-Module -Name <module name> -Scope CurrentUser

    Por exemplo, se o módulo Microsoft.Graph.Identity.DirectoryManagement não foi instalado, você deverá executar o seguinte comando:

        Install-Module -Name Microsoft.Graph.Identity.DirectoryManagement

6. As configurações de política de execução do PowerShell determinam quais scripts do PowerShell podem ser executados em um sistema Windows. Definir essa política como **Irrestrita** permite que Holly carregue todos os arquivos de configuração e execute todos os scripts. No prompt de comando, digite o seguinte comando e pressione Enter:   <br/>

        Set-ExecutionPolicy RemoteSigned

    ‎Se for solicitado que você confirme se deseja alterar a política de execução, insira **A** para selecionar **[A] Sim para Todos.** 

7. Deixe a janela do PowerShell aberta, pois você a usará na próxima tarefa.


Parabéns! Você concluiu todas as etapas para inicializar seu locatário de laboratório. Você já pode realizar os exercícios do laboratório restantes.

# Fim do Laboratório 1
