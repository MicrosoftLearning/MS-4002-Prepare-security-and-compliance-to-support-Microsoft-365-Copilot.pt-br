# Roteiro de Aprendizagem 1 – Laboratório 2 – Exercício 1 – Gerenciar o acesso seguro do usuário 

As organizações devem garantir que o acesso aos dados da empresa no Microsoft 365 esteja sempre seguro. O Microsoft 365 costuma mostrar dados sensíveis e confidenciais, incluindo emails, documentos, informações do cliente e propriedade intelectual. Um acesso não autorizado ao Microsoft 365 pode levar a violações de dados, roubo de identidade e outras atividades mal-intencionadas. Ao proteger o acesso do usuário, as organizações podem impedir que pessoas não autorizadas acessem e possivelmente façam um uso indevido ou vazem dados da empresa ao trabalhar no Microsoft 365.

No exercício de laboratório a seguir, você continuará representando seu papel de Holly Dickson,a nova Administradora do Microsoft 365 da Adatum. Você executará várias funções de gerenciamento de usuários e grupos no Microsoft 365. Você vai começar criando uma conta de usuário do Microsoft 365 para a Holly, que receberá a função de Administrador Global do Microsoft 365. Você criará vários grupos do Microsoft 365 e atribuirá usuários existentes do Microsoft 365 como membros desses grupos. Em seguida, você excluirá um dos grupos e usará o Windows PowerShell para recuperar o grupo excluído.

**Observação:** O ambiente de VM fornecido pelo provedor de hospedagem do seu laboratório vem com mais de 20 contas de usuário do Microsoft 365 existentes, além de um grande número de contas de usuário locais existentes. Várias das contas de usuário do Microsoft 365 existentes serão usadas ao longo dos laboratórios neste curso. Embora a conta do Administrador MOD tenha sido criada pelo provedor de hospedagem do seu laboratório, você ainda precisará criar a conta de usuário para Holly Dickson, já que a boa prática é atribuir a função de Administrador Global do Microsoft 365 a mais de um usuário. Com isso, você também terá a experiência de criar uma conta de usuário do Microsoft 365, caso ainda não conheça o processo.

Holly foi então solicitada pelo CTO da Adatum para implantar a MFA (Autenticação Multifator do Microsoft Entra) e o Microsoft Entra Smart Lockout. Esses recursos ajudarão a fortalecer o gerenciamento de senhas em toda a organização em preparação para o Copilot para Microsoft 365. Para o Bloqueio Inteligente, você o implantará usando o Gerenciamento de Política de Grupo. 


### Tarefa 1: Criar uma Conta de Usuário para o Administrador do Microsoft 365 da Adatum

Holly Dickson é a nova Administradora do Microsoft 365 da Adatum. Já que uma conta de usuário do Microsoft 365 ainda não foi configurada para ela, ela inicialmente entrou no Microsoft 365 com a conta do Administrador MOD (o administrador Global padrão) do laboratório anterior. Durante essa tarefa, em que você continuará conectado como o Administrador MOD, você criará uma conta de usuário do Microsoft 365 para a Holly. Você também atribuirá a função de Administrador Global do Microsoft 365 à conta da Holly. Essa função fornecerá a Holly as permissões necessárias para executar todas as funções administrativas no Microsoft 365. Após essa tarefa, você fará login usando a nova conta da Holly e executará todos os laboratórios restantes usando a persona da Holly. 

**Observação sobre a licença:** Antes de criar a conta da Holly, primeiro você irá verificará o número de licenças disponíveis. Ao fazer isso, você observará que, embora o seu locatário de laboratório forneça 20 licenças do Microsoft 365 E5 (sem Teams) e 20 licenças do Microsoft Teams Enterprise, todas essas licenças já foram atribuídas às contas de usuário existentes criadas pelo provedor de hospedagem do laboratório. Consequentemente, primeiro você precisará cancelar a atribuição de uma licença de cada tipo de um usuário existente para poder atribuí-la à Holly.

**Importante:** Uma boa prática para a sua implantação do mundo real é sempre anotar as credenciais da primeira conta de administrador Global (nesse laboratório, é a conta do Administrador MOD, cujo nome de usuário é admin@xxxxxZZZZZZ.onmicrosoft.com, em que xxxxxZZZZZZ é o prefixo de locatário atribuído pelo provedor de hospedagem do seu laboratório). Você deve guardar essas informações de conta em um lugar à parte por motivos de segurança. **Essa conta deve ser uma identidade NÃO personalizada** que possui os privilégios mais altos possíveis em um locatário. **Não** deve ser ativada por MFA porque não é personalizada. Como o nome de usuário e a senha dessa primeira conta de administrador Global costumam ser compartilhados entre vários usuários, essa conta é um alvo perfeito para os ataques e, portanto, é sempre recomendável que as organizações criem contas de administrador de serviço personalizadas (por exemplo, um administrador do Exchange, um administrador do SharePoint e assim por diante) e mantenham o menor número possível de administradores Globais pessoais. No caso dos administradores Globais pessoais que você cria em sua implantação do mundo real, cada um deles deve ser mapeado para um único usuário (como a Holly Dickson), e cada um deles deve ter a Autenticação Multifator (MFA) do Microsoft Entra implementada.  

1. Na VM **LON-CL1**, o **centro de administração do Microsoft 365** ainda deve estar aberto no navegador Microsoft Edge do exercício do laboratório anterior. Você precisa estar conectado no Microsoft 365 como o **Administrador MOD**. 

2. Já que você está adicionando um novo usuário, você deve começar verificando a disponibilidade de licença antes de adicionar a conta de usuário. No painel de navegação do **centro de administração do Microsoft 365**, selecione **Cobrança** para expandir o grupo Cobrança e, em seguida, selecione **Licenças**. 

3. Na página **Licenças**, a guia **Assinaturas** é exibida por padrão. Na lista de assinaturas, observe que as assinaturas do **Microsoft 365 E5 (sem Teams)** e **Microsoft Teams Enterprise** não têm licenças disponíveis. Seu locatário de laboratório fornece 20 licenças para cada assinatura, mas todas as 40 licenças foram atribuídas. Como você deve atribuir a Holly tanto uma licença do **Microsoft 365 E5 (sem Teams)** quanto uma licença do **Microsoft Teams Enterprise**, primeiro você deve cancelar a atribuição das licenças de uma conta de usuário existente para disponibilizá-las para Holly. 

4. No painel de navegação do **centro de administração do Microsoft 365**, selecione **Usuários** e, em seguida, selecione **Usuários ativos**. Na lista **Usuários ativos**, você verá as contas de usuário existentes que foram criadas pelo provedor de hospedagem do seu laboratório. Como Christie Cline mudará para uma nova função na empresa e não fará mais parte do projeto piloto do Microsoft 365, você cancelará a atribuição das licenças do **Microsoft 365 E5 (sem Teams)** e **Microsoft Teams Enterprise** de sua conta para que você possa reatribuí-las à nova conta de Holly Dickson.

5. Na página **Usuários Ativos**, na lista de usuários, selecione **Christie Cline** (selecione o nome de Christie com o hiperlink, não a caixa de seleção ao lado de nome dela).

6. No painel **Christie Cline** que aparece, a guia **Conta** é exibida por padrão. Selecione a guia **Licenças e aplicativos**. Em **Licenças (2)**, clique nas caixas de seleção ao lado de **Microsoft 365 E5 (sem Teams)** e **Microsoft Teams Enterprise** para desmarcá-las e selecione **Salvar alterações**. Após as alterações serem salvas, feche o painel **Christie Cline**. 

7. Agora está tudo pronto para você criar uma conta de usuário para Holly Dickson, que é a nova Administradora do Microsoft 365 da Adatum. Ao fazê-lo, você irá atribuir à Holly a função de Administrador Global do Microsoft 365, que fornece à Holly acesso global à maioria dos recursos de gerenciamento e dados nos serviços online da Microsoft. Você também atribuirá à Holly as duas licenças cuja atribuição à Christie Cline você acabou de cancelar. <br/>

    Na janela **Usuários Ativos**, selecione a opção **Adicionar um usuário** que aparece na barra de menus acima da lista de usuários ativos, para iniciar o assistente **Adicionar um usuário**.

8. Na página **Configurar o básico** do assistente **Adicionar um usuário**, insira as seguintes informações:

    - Nome: **Holly**

    - Sobrenome: **Dickson** 

    - Nome de exibição: Quando você acessa esse campo, o nome **Holly Dickson** vai aparecer.

    - Nome de usuário: **Holly** <br/>
    
        **IMPORTANTE:** À direita do campo **Nome de usuário** temos o campo do domínio, que estará preenchido previamente com o domínio de nuvem **xxxxxZZZZZZ.onmicrosoft.com** (em que xxxxxZZZZZZ é o prefixo do locatário fornecido pelo provedor de hospedagem do seu laboratório).<br/>
    
    - Desmarque (desmarque) a caixa de seleção **Criar automaticamente uma senha**, que exibirá um novo campo para inserir uma senha definida pelo administrador.

    - Digite a Nova Senha Administrativa no campo **Senha** que aparece (esta é a **Nova Senha Administrativa** solitada para você criar no início do Laboratório 1, Exercício 1)

    - Limpe (desmarque) a caixa de seleção **Exigir que esse usuário altere sua senha ao entrar pela primeira vez** 

9. Selecione **Avançar**. Se uma caixa de diálogo **Salvar senha** aparecer na parte superior da tela, selecione **Nunca**.

10. Na página **Atribuir licenças de produto**, insira as seguintes informações: <br/>

    - Selecione o local: **Estados Unidos**

    - Licenças: Na opção **Atribuir ao usuário uma licença de produto**, selecione as caixas de seleção **Microsoft 365 E5 (sem Teams)** e **Microsoft Teams Enterprise**

11. Selecione **Avançar**.

12. Na página **Configurações opcionais**, selecione a seta suspensa à direita de **Funções**. 

13. Na seção **Funções**, selecione a opção **Acesso ao centro de administração**. Ao selecionar essa opção, as funções de administrador mais comumente usadas do Microsoft 365 estarão habilitadas abaixo dela.  <br/>

    **Observação:** Todas as funções de administrador serão exibidas se você selecionar a opção **Mostrar tudo por categoria**, que aparece após a última função mais comum. No caso da Holly, você não precisa ver todas as funções de administrador por categoria porque a Holly receberá a função de Administrador Global que aparece na lista de funções comumente usadas.

14. Marque a caixa de seleção **Administrador Global**. <br/>

    **Observação:** Uma mensagem de aviso será exibida indicando que a Adatum já tem 7 administradores globais. Em um ambiente normal, isso seria excessivo e não recomendado. Para os fins desse laboratório, o provedor de hospedagem do seu laboratório atribuiu a função de administrador Global ao Administrador MOD e a outras seis contas de usuário, algo que você não veria normalmente em uma implantação do mundo real. No entanto, para os fins desse laboratório no seu ambiente fictício do laboratório da Adatum, ignore essa mensagem. **Dito isto, uma diretriz de boa prática que você deve seguir é ter de dois a quatro Administradores Globais nas suas implantações do Microsoft 365 no mundo real.** 

15. Selecione **Avançar**.

16. Na janela **Revisar e concluir**, reveja suas seleções. Se alguma coisa precisar ser alterada, selecione o link **Editar** apropriado e faça as alterações necessárias. Caso contrário, se tudo estiver correto, selecione **Terminar de adicionar**. 

17. Na página **Holly Dickson adicionada aos usuários ativos**, na seção **Detalhes do usuário**, clique na opção **Mostrar** para verificar se a senha de Holly é a mesma **Nova Senha Administrativa**, cuja criação foi solicitada a você no início do Laboratório 1, Exercício 1.  <br/>

    **Observação:** Se você inseriu uma senha diferente acidentalmente, depois de retornar à página **Usuários Ativos** você precisará selecionar o ícone **Redefinir uma senha** (o ícone de chave que aparece quando você passa o mouse sobre a conta da Holly) para alterar a senha dela para o valor correto.

18. Selecione **Fechar**.

19. Permaneça conectado à VM do Cliente 1 (LON-CL1) com o centro de administração do Microsoft 365 aberto no navegador para a próxima tarefa.


### Tarefa 2 – Atualizar o grupo de projetos piloto do Microsoft 365

Após concluir a tarefa anterior, você ainda deverá estar conectado ao **centro de administração do Microsoft 365** como a conta do **Administrador MOD**. Nessa tarefa, você começará a implementar o projeto piloto do Microsoft 365 da Adatum no papel de Holly Dickson, a nova Administradora do Microsoft 365 da Adatum. Portanto, você começará essa tarefa fazendo logon no Microsoft 365 como administrador MOD e fará logon novamente como Holly. 

Em uma tarefa anterior, você criou um grupo do Microsoft 365 para os membros da equipe de projeto piloto do Adatum para que você pudesse criar um tema personalizado para esse grupo. Nesta tarefa, você adicionará Holly a este grupo. 

1. Na VM LON-CL1, o **centro de administração do Microsoft 365** ainda deve estar aberto no navegador Microsoft Edge da tarefa anterior. Você precisa estar conectado no Microsoft 365 como o **Administrador MOD**. <br/>

    Na guia **centro de administração do Microsoft 365**, no canto superior direito da tela, observe que ele exibe o nome e o ícone de megafone do Administrador MOD. O nome é exibido devido ao tema personalizado que você criou no exercício de laboratório anterior, associado a um grupo de usuários do projeto piloto do Microsoft 365 que incluía o Administrador MOD. Tenha isso em mente quando fizer login como Holly Dickson. <br/>

    Selecione o ícone de usuário ou o círculo com as iniciais "MA" para o **Administrador MOD** no canto superior direito do navegador. Na janela **Administrador MOD** que aparece, selecione **Sair**. <br/>
    
    **Importante:** Ao sair de uma conta de usuário e entrar com outra, você deve fechar todas as guias do seu navegador, exceto a guia **Sair**. Essa é uma boa prática que ajuda a evitar qualquer confusão ao fechar as janelas associadas ao usuário anterior. Após sair da conta do Administrador MOD, reserve um momento para fechar todas as outras guias do navegador, exceto a guia **Sair**. 
    
2. No seu navegador Microsoft Edge, na guia **Sair**, insira a seguinte URL na barra de endereços para entrar novamente no Microsoft 365: **https://portal.office.com**. 

3. Na janela **Escolher uma conta**, aparece somente a conta de administrador de locatário do Administrador MOD (a conta de admin@xxxxxZZZZZZ.onmicrosoft.com) da qual você acabou de sair. Selecione **Usar outra conta**. 

4. Na janela **Entrar**, insira **Holly@xxxxxZZZZZZ.onmicrosoft.com** (em que xxxxxZZZZZZ é o prefixo do locatário fornecido pelo provedor de hospedagem do seu laboratório). Selecione **Avançar**.

5. Na janela **Inserir senha**, insira a Nova Senha Administrativa atribuída à conta de Holly e, em seguida, selecione **Entrar**. 

6. Se uma caixa de diálogo **Permanecer conectado?** aparecer, marque a caixa de seleção **Não mostrar isso novamente** e, a seguir, selecione **Sim**. 

7. Se uma caixa de diálogo **Bem-vindo ao Microsoft 365** aparecer no meio da tela, não existirá uma opção para fechá-la. Em vez disso, à direita da janela, selecione o ícone de seta para a frente (**>**) duas vezes e, em seguida, selecione o ícone de marca de seleção para avançar pelos slides nessa janela de mensagens. 

8. Se uma janela **Criar com o Microsoft 365** aparecer, selecione o **X** no canto superior da janela para fechá-la. 

9. A página **Bem-vindo ao Microsoft 365** aparece no seu navegador Edge, na guia **Página Inicial | Microsoft 365**. Essa é a página inicial do Microsoft 365 da Holly. Observe que as iniciais de Holly aparecem no canto superior direito da tela; o nome de Holly, no entanto, não é exibido. Isso ocorre porque a conta da Holly não existia no momento em que você adicionou os usuários do projeto piloto do Microsoft 365 ao grupo associado ao tema personalizado no exercício de laboratório anterior. Já que a Holly quer ver seu nome na parte superior de cada janela do Microsoft 365 quando estiver conectada ao sistema, ela primeiro vai querer adicionar sua conta ao grupo de usuários do projeto piloto do Microsoft 365. <br>

    Na coluna de ícones de aplicativo que aparece no painel de navegação na lateral da tela, selecione **Administrador**. Isso abre o **centro de administração do Microsoft 365** em uma nova guia do navegador. 

10. No **centro de administração do Microsoft 365**, selecione **Equipes e grupos** no painel de navegação e, em seguida, selecione no painel **Equipes e grupos ativos**. 

11. Na página **Equipes e grupos ativos**, temos uma guia para você conferir cada tipo de grupo. A guia **Equipes e Grupos do Microsoft 365** é exibida por padrão. Nessa guia, selecione **Projeto piloto do M365**.

12. No painel do **projeto piloto do M365** que aparece, a guia **Geral** é exibida por padrão. Selecione a guia **Filiação**.

13. Na guia **Afiliação**, a subguia **Proprietários** é exibida por padrão no painel de navegação que aparece no lado esquerdo do painel. Selecione a subguia **Membros** que aparece abaixo dela.

14. Na sub-guia **Membros**, selecione **+Adicionar membros**.

15. No painel **Adicionar membros do grupo ao projeto piloto do M365** que aparece, selecione dentro do campo **Pesquisar por nome ou endereço de email**. Na lista de usuários que aparece, role para baixo e selecione **Holly Dickson**. Selecione o botão **Adicionar (1)** e, a seguir, feche o painel **Adicionar membros do grupo ao projeto piloto do M365** assim que a Holly for adicionada ao grupo.

16. Permaneça conectado no LON-CL1 com o **centro de administração do Microsoft 365** aberto no seu navegador para a próxima tarefa.


### Tarefa 3: Criar uma política de Acesso Condicional para implementar a MFA

Como seu treinamento indicou, existem três maneiras de implementar a MFA: com políticas de Acesso Condicional, com padrões de segurança e com a MFA por usuário herdada (não recomendada para organizações maiores). Nesse exercício, você vai habilitar a MFA por meio de uma política de Acesso Condicional, que é o método recomendado pela Microsoft. 

O Adatum orientou Holly a habilitar a MFA para todos os seus usuários do Microsoft 365 - internos e externos. No entanto, para testar a implementação do projeto piloto do Microsoft 365 da Adatum, a Holly quer isentar os membros do grupo do projeto piloto da M365 da exigência de usar MFA para entrar. Após concluir o projeto piloto, Holly planeja atualizar a política removendo a exclusão desse grupo do requisito da MFA. A política também incluirá duas outras exigências. Exigirá a MFA para todos os aplicativos de nuvem e exigirá a MFA mesmo que um usuário faça login a partir de um local confiável. 

1. No exercício de laboratório anterior, você estava trabalhando na LON-DC1. Nesta tarefa, você voltará a trabalhar na máquina Client 1. <br/>

    Alterne para **LON-CL1**.

2. Na VM LON-CL1, o **centro de administração do Microsoft 365** ainda estará aberto no navegador Microsoft Edge da tarefa anterior. Você deve estar conectado ao Microsoft 365 como **Holly Dickson**.
   
3. No **centro de administração do Microsoft 365**, na seção **Centros de administração** no painel de navegação, selecione **Identidade**. Isso abre o centro de administração do Microsoft Entra em uma nova guia do navegador. Se uma janela **Escolher uma conta** for exibida, selecione **conta de Holly Dickson**.

4. No **centro de administração do Microsoft Entra**, selecione **Proteção** no painel de navegação e, a seguir, selecione **Acesso Condicional**.

5. Na página **Acesso Condicional | Visão geral**, selecione **Políticas** no painel de navegação do meio.

6. Na página **Acesso condicional | Políticas**, na barra de menus na parte superior da página, selecione **+ Criar nova política**.

7. Na janela **Nova Política de Acesso Condicional**, insira **MFA para todos os usuários do Microsoft 365** no campo **Nome**.

8. Você começará por definir a exigência de MFA para os usuários. No grupo **Usuários**, selecione **0 usuários e grupos selecionados**. Fazer isso irá exibir duas guias: **Incluir** e **Isentar**.

9. Na guia **Incluir**, selecione **Todos os usuários**. Observe a mensagem de aviso que aparece. Você abordará isso nas próximas duas etapas.

10. Selecione a guia **Isentar**. Para evitar o bloqueio do sistema, como a mensagem de aviso anterior indicou, você vai querer isentar seus administradores globais — nesse caso, a Holly. Durante os testes, a Holly também vai querer isentar os outros membros do grupo do projeto piloto do Microsoft 365, por uma questão de conveniência. Depois que o Microsoft 365 entrar em operação no Adatum, Holly removerá o grupo de projetos piloto da lista Excluir nesta política de Acesso Condicional e simplesmente se excluirá, o Administrador MOD e alguns outros administradores globais. Mas por enquanto, Holly quer excluir todo o grupo de projetos piloto. <br/>

    Para fazer isso, marque a caixa de seleção **Usuários e grupos**. 

11. Na janela **Selecionar usuários e grupos excluídos** que aparece, você deseja selecionar o grupo de projetos piloto do Microsoft 365. A guia **Todos** é exibida por padrão. Para localizar o grupo do projeto piloto rapidamente, selecione a guia **Grupos**. Na lista de grupos ativos, marque a caixa de seleção ao lado do grupo **Projeto piloto do M365** e, em seguida, selecione o botão **Selecionar** na parte inferior da janela. De volta à janela **Nova Política de Acesso Condicional**, observe a mensagem que aparece na seção **Usuários**. 

12. Agora, você vai definir a exigência de MFA para todos os aplicativos de nuvem. Na seção **Recursos de destino**, selecione **Nenhum recurso de destino selecionado**. Fazer isso irá exibir duas guias: **Incluir** e **Isentar**.

13. Selecione o menu suspenso **Selecione a que se aplica essa política** para ver as várias opções no menu suspenso. Selecione **Recursos (anteriormente aplicativos de nuvem).** 

14. Na guia **Incluir**, observe que a configuração padrão é **Nenhum**. Se você não alterou essa configuração, nenhum aplicativo de nuvem exigiria MFA - e isso inclui o Microsoft 365. Portanto, mesmo que você criasse essa política e selecionasse a opção de exigir MFA para todos os usuários, mas deixasse essa configuração de **Recursos de destino** como **Nenhum**, nenhum usuário que entrasse no Microsoft 365 precisaria usar a MFA. <br/>

    Na guia **Incluir**, clique na opção **Selecionar recursos**. Isso exibe duas seções: **Editar filtro** e **Selecionar**. Na seção **Selecionar**, selecione **Nenhum**. 

15. No painel **Selecionar recursos** que aparece, role pela lista de aplicativos para ver todos os diferentes aplicativos para os quais você poderia exigir a MFA. **NÃO selecione nenhum dos aplicativos.** Estamos fazendo você percorrer essa lista apenas para ter uma ideia de quão granular você pode obter ao exigir MFA caso decida limitar a MFA a determinados aplicativos em suas implantações do mundo real.  <br/>

    No caso da Adatum, a Holly quer exigir a MFA para todos os aplicativos de nuvem, o que costuma ser um cenário corporativo mais comum do que selecionar aplicativos específicos. Na guia **Incluir**, clique na opção **Todos os recursos (antes "Todos os aplicativos de nuvem")**. A Adatum não irá isentar nenhum aplicativo de nuvem da autenticação multifator (MFA). Você pode selecionar a guia **Excluir** se quiser ver as opções que ela fornece. Ele funciona basicamente da mesma forma que a guia **Incluir**. Você pode exibir essa guia, mas NÃO selecione nenhum aplicativo de nuvem para exclusão. 

16. Para terminar, você vai definir a exigência de MFA para todos os locais de login do usuário. Em alguns cenários, as organizações talvez só exijam a MFA se um usuário fizer login a partir de um local não confiável. No entanto, o Adatum deseja exigir MFA para todos os usuários incluídos, independentemente do local de onde eles entram. <br/>

    Em **Condições**, selecione **0 condições selecionadas**. Fazer isso vai exibir uma lista de possíveis condições que a política irá verificar. Para esse exercício de laboratório, na condição **Locais**, selecione **Não configurados**. Fazer isso vai exibir um botão de alternância para **Configurar** e duas guias: **Incluir** e **Isentar**. Ambas as guias estão desabilitadas no momento.

17. Defina botão de alternância **Configurar** como **Sim**, o que habilita as duas guias. 

18. Na guia **Incluir**, verifique se **qualquer rede ou local** está selecionado (selecione-o, se necessário). Selecione a guia **Isentar**. Se a sua organização reconhecer endereços ou intervalos de endereços IP específicos como "confiáveis", você poderá excluir a exigência de MFA se um usuário fizer login a partir de um desses locais. No entanto, o Adatum deseja exigir MFA para todas as tentativas de entrada do usuário, independentemente de sua localização. Isso incluirá tanto os logins de usuários internos quanto externos. Verifique se a opção **Redes e locais selecionados** está selecionada e, na seção **Selecionar**, verifique se ela diz **Nenhuma**. Ao especificar que nenhum local está selecionado, essa configuração garante que nenhum local fique isento da MFA. 

19. Na seção **Controles de acesso**, no grupo **Conceder**, selecione **0 controles selecionados**. Fazer isso irá exibir um painel **Conceder**.

20. No painel **Conceder** que aparece, verifique se a opção **Conceder acesso** está selecionada (você pode selecioná-la, se necessário). Observe todos os controles de acesso disponíveis que podem ser habilitados com essa política. Essa política exigirá apenas MFA, portanto, marque a caixa de seleção **Exigir autenticação multifator**. Selecione o botão **Selecionar** na parte inferior do painel **Conceder**, que fechará o painel. 

21. Na parte inferior da janela **Nova Política de Acesso Condicional**, no campo **Habilitar política**, selecione **Ativar**.

22. Observe a mensagem de aviso e as opções que aparecem na parte inferior da página que avisam para você não se bloquear. Selecione a opção **Eu entendo que minha conta será afetada por essa política. Continuar assim mesmo.** Na verdade, a Holly não será afetada, já que faz parte do grupo do projeto piloto do M365, que é isento dessa política.

23. Selecione o botão **Criar** para criar a política.

24. Na janela **Acesso Condicional | Políticas** que aparece, verifique se a política **MFA para todos os usuários do Microsoft 365** aparece e se seu **Estado** está definido como **Habilitada**.

25. Permaneça conectado ao LON-CL1 com todas as guias do seu navegador Microsoft Edge abertas para a próxima tarefa.


### Tarefa 4: Testar a MFA para um usuário incluído e isento

Para testar a política de Acesso Condicional que você acabou de criar, você sairá do Microsoft 365 como Holly e entrará novamente como Adele Vance. A Adele não é membro do grupo do projeto piloto do M365 e, portanto, o Microsoft Entra deverá exigir que use MFA no login. Após ter entrado como Adele e verificar que a MFA está funcionando, você vai sair como Adele e, em seguida, entrar novamente como Holly. Já que a Holly é um membro do grupo do projeto piloto do M365 e está isenta do uso da MFA na política de Acesso Condicional, você não deve precisar usar a MFA quando entrar como Holly. Da mesma forma, você não precisará usar a MFA quando entrar como os vários membros do grupo de projetos piloto M365 nos laboratórios restantes neste curso.

**Importante:** Para implementar a MFA, você deve usar seu telefone celular para receber um código de verificação para que possa inseri-lo em seu locatário como uma segunda forma de autenticação. Se não tiver um celular, ainda assim você poderá testar sua política de Acesso Condicional. Para alunos sem telefone, quando você entrar como Adele Vance, o sistema exigirá que você entre com uma segunda forma de autenticação. Nesse ponto, você pode simplesmente cancelar seu login e, em seguida, entrar novamente como a Holly, que não terá a exigência da MFA. Embora você não conclua a entrada de MFA para Adele, você ainda pode verificar se o sistema força você a usá-lo ao tentar entrar.

1. Na VM LON-CL1, o **centro de administração do Microsoft 365** ainda deve estar aberto no navegador Microsoft Edge da tarefa anterior. Você deve estar conectado ao Microsoft 365 como **Holly Dickson**. Você vai começar saindo do Microsoft 365. Na guia **centro de administração do Microsoft 365**, selecione o nome da Holly no canto superior direito do seu navegador. Na janela **Holly Dickson** que aparece, selecione **Sair**. 
    
2. Depois de sair do Microsoft 365 como Holly, feche a sessão do navegador para limpar o cache. Em seguida, selecione o ícone do **Edge** na barra de tarefas para abrir uma nova sessão do navegador. No navegador, acesse a página **Inicial do Microsoft 365** inserindo a seguinte URL na barra de endereços: **https://portal.office.com/** 

3. Na janela **Escolher uma conta** exibida, selecione **Usar outra conta**. 

4. Na janela **Entrar**, insira **AdeleV@xxxxxZZZZZZ.onmicrosoft.com** (em que xxxxxZZZZZZ é o prefixo de locatário fornecido pelo provedor de hospedagem do seu laboratório) e selecione **Avançar**. Na janela **Digite a senha**, digite a **Senha do usuário** fornecida pelo seu provedor de hospedagem de laboratório e selecione **Entrar**.

5. Como a MFA está habilitada para todos os usuários, exceto para os membros do grupo do projeto piloto do M365 (do qual a Adele não faz parte), uma janela **Mais informações necessárias** irá aparecer e Selecione **Avançar**. retornar você para a página do **Microsoft Authenticator**, que é o ponto de partida para entrar com a MFA. <br/>

    **Importante:** Se não tiver um celular, você não poderá ir mais longe quando tentar entrar como Adele. Mesmo que não consiga concluir o login, você terá verificado que a primeira parte da sua política de Acesso Condicional está funcionando, já que exigiu que a Adele entrasse usando a MFA. Neste ponto, pule para a etapa 18 para que você possa entrar novamente como Holly.

6. Na página **Microsoft Authenticator** que aparece, você pode baixar esse aplicativo móvel ou usar um método diferente para a verificação da MFA. Para fins deste laboratório, recomendamos que você use seu telefone celular para não precisar ter tempo para instalar o aplicativo Microsoft Authenticator que talvez não use novamente após essa aula de treinamento. Selecione a opção **Quero configurar um método diferente** na parte inferior da página (**Importante:** NÃO confunda esse link com a opção **Quero usar um aplicativo de autenticação diferente** que aparece acima dele). 

7. Na caixa de diálogo **Escolher um método** diferente que aparece, selecione a seta suspensa no campo **Qual método você deseja usar?** Selecione **Telefone** e, em seguida, selecione **Confirmar**. 

8. Na janela **Telefone** que aparece, no campo **Qual número de telefone você gostaria de usar?**, selecione seu país ou região e, em seguida, no campo ao lado, insira seu número de telefone (use a formatação específica do seu país). Verifique se a opção **Receber um código** está selecionada e, a seguir, selecione **Avançar**.

9. Recupere o código de verificação da mensagem de texto enviada para o seu celular.

10. Na janela **Telefone**, insira o código de verificação de 6 dígitos no campo de código e selecione **Avançar**. Quando a janela **Telefone** mostrar uma mensagem indicando que seu número de celular foi registrado com sucesso, selecione **Avançar**.

11. Na página **Sucesso!**, selecione **Concluído**.

12. A Microsoft implementou uma nova política de segurança nos locatários de avaliação que são usados em seus laboratórios de treinamento. Todas as contas de usuário de teste predefinidas são configuradas para que os alunos alterem a senha inicial na próxima entrada. Você deve fazer isso agora com Adele. <br>

    Na janela **Atualizar sua senha** exibida, insira a **Senha do Usuário** fornecida pelo provedor de hospedagem do laboratório no campo **Senha atual**. Em seguida, nos campos **Nova senha** e **Confirmar senha**, insira a Nova Senha de Usuário que você definiu para todos os usuários de teste no início do laboratório. Selecione **Entrar**.

13. Se uma caixa de diálogo **Permanecer conectado?** aparecer, marque a caixa de seleção **Não mostrar isso novamente** e, a seguir, selecione **Sim**. 

14. Se uma caixa de diálogo **Bem-vindo ao Microsoft 365** for exibida, selecione a seta para a direita duas vezes e marque a marca de seleção.

15. Se uma janela **Criar com o Microsoft 365** for exibida, selecione o **X** para fechá-lo.

16. Na página **Boas-vindas ao Microsoft 365**, clique no ícone do **Inicializador de aplicativos** e selecione **Word**. Isso abre o **Microsoft Word Online**. Fazer isso irá validar que você pode acessar um aplicativo do Microsoft 365 após entrar usando a MFA.  <br/>

    **Importante:** Agora você verificou que a primeira parte da política de Acesso Condicional que você criou está funcionando. A política requer que um usuário que não seja membro da equipe do projeto piloto do Microsoft 365 faça login usando a MFA. Você verificou que isso funciona quando fez login como Adele. Agora, você sairá como Adele e entrará novamente como Holly, processo durante o qual você vai verificar se a segunda parte da política de Acesso Condicional também está funcionando. Você NÃO deve precisar usar a MFA ao entrar como Holly, já que ela é membro do grupo o projeto piloto do M365 e está isenta da exigência de MFA na política de Acesso Condicional.

17. Na guia **centro de administração do Microsoft 365**, selecione o ícone da conta da Adele no canto superior direito do seu navegador. Na janela **Adele Vance** que aparecer, selecione **Sair**. <br/>
    
18. Feche a sessão do navegador para limpar o cache. Selecione o ícone do **Edge** na barra de tarefas para abrir uma nova sessão do navegador. No navegador, acesse a página **Inicial do Microsoft 365** inserindo a seguinte URL na barra de endereços: **https://portal.office.com/** 

19. Na janela **Escolher uma conta**, selecione **Holly@xxxxxZZZZZZ.onmicrosoft.com** (em que xxxxxZZZZZZ é o prefixo de locatário fornecido pelo provedor de hospedagem do seu laboratório) e selecione **Avançar**. Na janela **Inserir senha**, insira a nova Senha Administrativa que você definiu para todos os usuários de teste no início do laboratório e, posteriormente, atribuída à conta de Holly. Selecione **Entrar**.

20. Como a MFA é obrigatória para todos os usuários, exceto para os membros da equipe do projeto piloto do M365 (da qual Holly faz parte), a MFA não será necessária. Como a MFA não é necessária, o sistema exibe a página **Inicial do Microsoft 365** na **Página Inicial | Guia Microsoft 365**. 

21. Se uma caixa de diálogo **Bem-vindo ao Microsoft 365** for exibida, selecione a seta para a direita duas vezes e marque a marca de seleção.

22. Se uma janela **Criar com o Microsoft 365** for exibida, selecione o **X** para fechá-lo.

23. Na página **Bem-vindo ao Microsoft 365**, selecione o ícone **Administrador** no painel lateral para navegar até o **centro de administração do Microsoft 365**. <br/>

    **Importante:** Agora você verificou que a segunda parte da política de Acesso Condicional que você criou está funcionando. A política isenta os membros do grupo do projeto piloto do Microsoft 365 da exigência de fazer login usando a MFA. Holly é membro desse grupo e não precisou entrar usando a MFA.

24. Permaneça conectado ao LON-CL1 com o **Centro de administração do Microsoft 365** aberto no navegador.


### Tarefa 5: Implantar o Bloqueio Inteligente do Microsoft Entra

O Diretor de Tecnologia da Adatum pediu para você implantar o Bloqueio Inteligente do Microsoft Entra, que ajuda a bloquear atores mal-intencionados que tentam adivinhar as senhas dos seus usuários ou usam métodos de força bruta para serem aceitos na sua rede. O Bloqueio Inteligente pode reconhecer os logins provenientes de usuários válidos e tratá-los diferentemente dos logins de invasores e outras origens desconhecidas. 

O Diretor de Tecnologia está ansioso para implementar o Bloqueio Inteligente porque o recurso bloqueará os invasores e, ao mesmo tempo, permitirá que os usuários da Adatum continuem a acessar suas contas e a ser produtivos. O Diretor de Tecnologia pediu à Holly para configurar o Bloqueio Inteligente para que os usuários não possam usar a mesma senha mais de uma vez, além de não poderem usar senhas consideradas muito simplistas ou muito comuns. 

**Observação:** você pode fazer a manutenção das configurações da Política de Bloqueio de Contas no Editor de Gerenciamento de Política de Grupo e no Microsoft Entra por meio do seu recurso de Bloqueio Inteligente. Essa tarefa do laboratório mostra como acessar cada método, mesmo considerando que você só irá atualizar as configurações do Bloqueio Inteligente no Microsoft Entra. Você precisa usar o controlador de domínio da empresa (LON-DC1) para acessar o Editor de Gerenciamento de Política de Grupo. 

1. Na LON-DC1, clique no ícone do **Gerenciador do Servidor** na barra de tarefas se ela já estiver aberta; se não estiver, abra-a.

2. No **Gerenciador do Servidor**, selecione **Ferramentas** na barra de menus do canto superior direito e, no menu suspenso, selecione **Gerenciamento de Política de Grupo**.

3. Maximize a janela **Gerenciamento de Política de Grupo**.

4. Você vai querer editar a política de grupo que inclui a política de bloqueio de conta da sua organização. Se necessário, na árvore de console raiz no painel do lado esquerdo, expanda **Forest:Adatum.com**, expanda **Domínios**e, a seguir, expanda **Adatum.com**.  <br/>

    Em **Adatum.com**, clique com o botão direito do mouse na **Política de Domínio Padrão** e selecione **Editar** no menu.

5. Maximize a janela **Editor de Gerenciamento de Política de Grupo** que aparece.

6. Na árvore **Política de Domínio Padrão** no painel lateral, em **Configuração do Computador**, expanda **Políticas**, expanda **Configurações do Windows**, expanda **Configurações de Segurança** e, a seguir, expanda **Políticas de Conta**.

7. Na pasta **Políticas de Contas**, selecione **Política de Bloqueio de Contas**.

8. Como você pode ver no painel de detalhes do meio, nenhum dos parâmetros do bloqueio inteligente foi definido. Em vez de fazer a manutenção desses parâmetros de bloqueio no Editor de Gerenciamento de Política de Grupo, você vai usar o centro de administração do Microsoft Entra. Embora você possa usar o Editor de Gerenciamento de Política de Grupo, esse método costuma ser mais usado em ambientes locais do Active Directory. Mostramos esse editor para que você pudesse ver essa alternativa. No entanto, para as organizações que usam estritamente serviços baseados em nuvem como o Microsoft 365, ou que acham que usar o centro de administração do Microsoft Entra é muito mais fácil do que acessar o Editor de Gerenciamento de Política de Grupo, pode ser preferível usar o **centro de administração do Microsoft Entra** para atribuir os valores correspondentes no contexto do Entra ID. <br/>  

    Lembre-se também de que o comportamento do bloqueio e as opções de personalização dos dois métodos são diferentes. Com o Editor de Gerenciamento de Política de Grupo, você tem um controle mais granular sobre as configurações das políticas, incluindo o Limite de Bloqueios de Conta, a Duração do Bloqueio e Redefinir o Contador do Bloqueio de Conta Após. No entanto, usar esse método requer familiaridade com Políticas de Grupo e a administração do Active Directory. A Política de Bloqueio de Contas no Microsoft Entra, por outro lado, não pode ser personalizada tão amplamente mas é mais fácil de usar, embora não tenha algumas das opções de ajuste fino disponíveis na Política de Grupo. <br/>

    No caso da Adatum, a Holly optou por usar o centro de administração do Microsoft Entra para configurar a política de Bloqueio de Contas da empresa. Na barra de tarefas na parte inferior da tela, clique no ícone do **Microsoft Edge**, que exibirá o **centro de administração do Microsoft Entra**. 

9. No **centro de administração do Microsoft Entra**, selecione **Proteção** no painel de navegação e, a seguir, selecione **Métodos de autenticação** 

10. Na página **Métodos de Autenticação | Políticas**, no painel do meio, na seção **Gerenciar**, selecione **Proteção por senha**.

11. Na janela **Métodos de autenticação | Proteção de senha**, no painel de detalhes no lado direito, insira as seguintes informações:

    - Na seção **Bloqueio inteligente personalizado**:

        - **Limite de bloqueios:** esse campo indica quantos logins com falha são permitidos em uma conta antes de ser bloqueada pela primeira vez. O padrão é 10. Para fins de teste, a Adatum solicitou que você o definisse como **3**.

        - **Duração do bloqueio em segundos**: Essa é a duração em segundos de cada bloqueio. O padrão é 60 segundos (um minuto). A Adatum solicitou que você alterasse isso para **90** segundos.

    - Na seção **Senhas proibidas personalizadas**:

        - **Implementar lista personalizada**: selecione **Sim**

        - **Lista de senhas proibidas personalizadas:** Insira os seguintes valores (pressione Enter após inserir cada valor para que cada valor fique em uma linha separada):

            - **Password01**

            - **F00tball01**

            - **Se@Hawks1**

            - **Never4get!!**

    - Na seção **Modo**, selecione **Implementado**

12. Selecione **Salvar** na barra de menus na parte superior da página.

13. Agora, você deve testar a funcionalidade de senha proibida. Selecione o ícone de usuário da Holly Dickson no canto superior direito da tela e, no menu que aparece, selecione **Ver conta**. 

14. Na janela **Minha conta** que aparece, no bloco **Senha**, selecione **ALTERAR SENHA**.

15. Uma nova guia será aberta mostrando a janela **Alterar senha**. No campo **Senha antiga**, insira a senha existente de Holly, que é a Nova Senha Administrativa. <br/>

    Insira **Never4get!!** nos campos **Criar nova senha** e **Confirmar nova senha** e, em seguida, selecione **Enviar**. Observe a mensagem de erro que você receber.

16. No seu navegador, feche a guia **Alterar senha**. 

17. Agora você vai testar a funcionalidade de limite de bloqueio. Você vai fazer isso usando a conta de Laura Atkin, que você criou em um exercício de laboratório anterior. Selecione o ícone de usuário da Holly Dickson no canto superior direito da tela e, no menu que aparece, selecione **Sair**.  

18. Após ter saído como Holly, a janela **Escolher uma conta** aparecerá na guia **Entrar no Microsoft Entra**. Como boa prática, ao sair de um serviço online da Microsoft como um usuário e entrar novamente como outro, feche todas as guias do seu navegador, exceto as guias **Sair** ou **Entrar**. Nesse caso, feche as outras guias agora e deixe a guia **Entrar** aberta.  <br/>

    Na janela **Escolher uma conta**, selecione **Usar outra conta**. 

19. Na janela **Entrar**, insira**laura@xxxxxZZZZZZ.onmicrosoft.com**(em que xxxxxZZZZZZ é o prefixo de locatário atribuído a você pelo provedor de hospedagem de laboratório) e selecione **Avançar**. 

20. Na janela **Inserir senha**, insira qualquer combinação aleatória de letras e números e selecione **Entrar**. Observe a mensagem de erro de senha inválida que aparece. 

    Repita essa etapa mais duas vezes. 
    
    Já que definiu o **Limite de bloqueios** como **3**, você deve receber uma mensagem de erro indicando que essa conta está bloqueada após a terceira tentativa de login com falha. <br/>

    **Observação:** Se você não receber essa mensagem de bloqueio após a terceira tentativa, isso significa que o sistema ainda não terminou de propagar essa alteração do limite de bloqueios no serviço inteiro. Pode levar vários minutos para que as alterações entrem em vigor. Aguarde alguns minutos e entre novamente com uma senha falsa. Os testes desse laboratório têm apresentado resultados variados. Às vezes, a alteração é propagada quase imediatamente para que sua conta seja bloqueada após a terceira tentativa de login. Outras vezes, pode levar de 5 a 10 minutos antes que a mensagem de bloqueio seja exibida. Continue esse processo até receber a mensagem de bloqueio, quando a conta de Laura será temporariamente bloqueada para impedir o acesso não autorizado.

21. Você não conseguirá fazer login novamente como Laura até que a **duração do bloqueio de 90 segundos** definida anteriormente expire. <br/>

    Após sua conta ter sido bloqueada, aguarde 90 segundos e entre novamente como **laura@xxxxxZZZZZZ.onmicrosoft.com** (em que xxxxxZZZZZZ é o prefixo de locatário atribuído a você pelo provedor de hospedagem do seu laboratório). No campo **Senha**, digite a senha de Laura, que é a Nova Senha de Usuário que você atribuiu à conta de Laura ao criá-la. 

22. Como a MFA está habilitada para todos os usuários, exceto para os membros do grupo do projeto piloto do M365 (do qual Laura não faz parte), uma janela **Mais informações necessárias** irá aparecer para você concluir o processo da MFA para Laura. Esta é a verificação de que sua tentativa de login usando a senha real de Laura foi bem-sucedida.  <br>

    **Observação:** você NÃO precisa concluir o processo da MFA para Laura, pois este é seu último exercício de laboratório usando o controlador de domínio LON-DC1. Você pode fechar todos os aplicativos no LON-DC1.

# Prosseguir para o Laboratório 2, Exercício 2
