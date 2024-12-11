# Roteiro de Aprendizagem 1 – Laboratório 4 – Exercício 1 – Implementar rótulos de confidencialidade com o Microsoft Entra ID Protection

Em sua função como Holly Dickson, nova Administradora do Microsoft 365 do Adatum, você tem o Microsoft 365 implantado em um ambiente de laboratório virtualizado. Ao trabalhar em seu projeto piloto do Microsoft 365, suas próximas etapas são implementar rótulos de confidencialidade com o Microsoft Entra ID Protection na Adatum. Neste laboratório, você criará e publicará um rótulo e testará um rótulo publicado. No entanto, ao fazer isso, você não testará o rótulo criado neste laboratório. Você testará um rótulo diferente.

**Importante:** Quando você publica um novo rótulo de confidencialidade e uma política de rótulo, pode demorar até 24 horas para propagar por meio do Microsoft 365. Sendo assim, você não conseguirá testar o rótulo criado neste laboratório. Em vez disso, você testará um rótulo de confidencialidade pré-existente chamado **Project – Falcon**. Esse rótulo pré-existente é quase idêntico ao rótulo que você criará, então você basicamente poderá ver os mesmos resultados se tivesse testado o rótulo que criou. 


### Tarefa 1 – Instalar o cliente da Proteção de Informações do Microsoft Purview

Para implementar Rótulos de confidencialidade como parte do projeto piloto na Adatum, primeiro instale o **cliente da Proteção de Informações do Microsoft Purview** no Centro de Download da Microsoft.

1. No final do laboratório anterior, você estava no LON-CL2. Alterne para **LON-CL1**.  <br/>

    Você ainda deve estar logado na LON-CL1 com a conta **adatum\administrador** e, no navegador Edge, ainda deve estar logado no Microsoft 365 como **Holly Dickson**. 

2. No **Microsoft Edge**, abra uma nova guia e insira (ou copie e cole) a seguinte URL na barra de endereços: **https://www.microsoft.com/en-us/download/confirmation.aspx?id=53018** <br/>

    Isso iniciará o download para o cliente da **Proteção de Informações do Microsoft Purview**.

3. Na janela **Downloads** que aparece no canto superior direito da página, você verá o arquivo **PurviewInfoProtection.exe** sendo baixado. Depois que o arquivo terminar de baixar, selecione o link **Abrir arquivo** que aparece abaixo do nome do arquivo.

4. O assistente da **Proteção de Informações do Microsoft Azure** será aberto. Se o assistente não for exibido na área de trabalho, selecione o ícone do assistente na barra de tarefas para exibir o assistente.

5. No assistente, na janela **Instalar o cliente da Proteção de Informações do Microsoft Purview** exibida, marque a caixa de seleção **Eu reconheço que o Suplemento AIP do Office será desinstalado (necessário)** e limpe (desmarque) a caixa de seleção **Ajudar a melhorar a Proteção de Informações do Microsoft Purview enviando estatísticas de uso para a Microsoft**. Em seguida, selecione o botão **Concordar**.

6. Quando a instalação for concluída, selecione **Fechar**.

Você instalou o **cliente da Proteção de Informações do Microsoft Purview** na VM LON-CL1.


### Tarefa 2 - Habilitar rótulos de confidencialidade para arquivos no SharePoint e no OneDrive

Neste exercício, você habilitará rótulos de confidencialidade para arquivos do Office com suporte e arquivos PDF no SharePoint e no OneDrive. Quando esse recurso está habilitado, os usuários veem o botão **Confidencialidade** na faixa de opções para que possam aplicar rótulos. Eles também veem qualquer nome de rótulo aplicado na barra de status. Para o SharePoint, os usuários também podem ver e aplicar rótulos de confidencialidade no painel de detalhes.

Habilitar esse recurso também faz com que o SharePoint e o OneDrive possam processar o conteúdo dos arquivos do Office e, opcionalmente, documentos PDF que foram criptografados usando um rótulo de confidencialidade. O rótulo pode ser aplicado no Office para a Web ou em aplicativos da área de trabalho do Office e carregado ou salvo no SharePoint e no OneDrive. Até habilitar esse recurso, esses serviços não poderão processar arquivos criptografados, o que significa que a coautoria, descoberta eletrônica, prevenção contra perda de dados, pesquisa e outros recursos colaborativos não funcionarão para esses arquivos.

Primeiro, você habilitará rótulos de confidencialidade para arquivos online do Office armazenados no SharePoint e no OneDrive. Em seguida, você habilitará o suporte para PDFs.

**Observação:** Assim como acontece com todas as alterações de configuração no nível do locatário para o SharePoint e o OneDrive, leva cerca de 15 minutos para que a alteração entre em vigor.

1. No LON-CL1, no navegador Edge, você deve continuar conectado no Microsoft 365 como **Holly Dickson**.

2. No navegador Edge, você ainda deve ter uma guia aberta para o **Centro de administração do Microsoft 365**. Caso contrário, abra uma nova guia e insira a seguinte URL: **https://admin.microsoft.com**.

3. No **Centro de administração do Microsoft 365**, se necessário, selecione **... Mostrar tudo **. Selecione **Conformidade** no grupo **Centros de administração**. Isso abre o portal do Microsoft Purview em uma nova guia.

4. Você começará habilitando rótulos de confidencialidade para arquivos online do Office armazenados no SharePoint e no OneDrive. <br/>

    No portal do **Microsoft Purview**, na seção **Soluções** no painel de navegação, selecione **Proteção de informações** e selecione **Rótulos de confidencialidade**.

5. Na página **Rótulos de confidencialidade**, a seguinte mensagem aparecerá no meio da página: **Sua organização não habilitou o processamento de conteúdo em arquivos online do Office com rótulos de confidencialidade criptografados aplicados e que estão armazenados no OneDrive e no SharePoint. Você pode ativar aqui, mas configuração adicional é necessária para ambientes multigeográficos.** <br/>

    Abaixo desta mensagem está um botão **Ativar agora**. Selecione esse botão.  <br/>

    **Observação:** O comando é executado imediatamente e, quando a página for atualizada, você não verá mais a mensagem ou o botão.

6. Agora você habilitará a proteção em PDF para arquivos no SharePoint e no OneDrive. <br/>

    No portal do **Microsoft Purview**, no grupo **Proteção de informações** do painel de navegação, selecione **Rotulagem Automática**.

7. Na página **Rotulagem Automática**, você deverá ver a faixa **Proteger PDFs com Rotulagem Automática** no meio da página. Selecione o título **Proteger PDFs com Rotulagem Automática** para ativar a proteção em PDF para arquivos no SharePoint e no OneDrive. 

8. Na caixa de diálogo **Políticas de rotulagem automática** exibida, clique em **Confirmar** para confirmar se deseja ativar a proteção em PDF para arquivos no SharePoint e no OneDrive. 

    **Observação:** O comando é executado imediatamente e, quando a página for atualizada em seguida, você não verá mais a faixa **Proteger PDFs com Rotulagem Automática**.

9. Deixe o navegador Edge aberto junto com todas as guias. 


### Tarefa 2 - Criar um rótulo de confidencialidade

Neste exercício, você criará um Rótulo de Confidencialidade e o adicionará à política padrão para que ele seja válido para todos os usuários do locatário do Adatum.

1. No LON-CL1, no navegador Edge, você deve continuar conectado no Microsoft 365 como **Holly Dickson**.

2. No seu navegador Edge, você ainda deve ter uma guia aberta para o portal **Microsoft Purview** da tarefa anterior. No portal do **Microsoft Purview**, no grupo **Proteção de informações** do painel de navegação, selecione **Rótulos de confidencialidade**. 

3. Na página **Rótulos de confidencialidade**, clique na opção **+Criar um rótulo** que aparece na barra de menus no meio da tela. Isso inicia o assistente **Novo rótulo de confidencialidade**.

4. No assistente **Novo rótulo de confidencialidade**, na página **Fornecer detalhes básicos para esse rótulo**, insira as seguintes informações:

    - Nome: **PII**
    
    - Nome de exibição: **PII**

    - Descrição para usuários: **Documentos, arquivos e emails com PII**

    - Descrição para administradores: **Documentos, arquivos e emails com PII**

    - Cor do rótulo: selecione uma das cores que você deseja atribuir aos seus rótulos de confidencialidade

5. Selecione **Avançar**.

6. Na página **Definir o escopo deste rótulo**, verifique se a caixa de seleção **Itens** está marcada, bem como as caixas de seleção **Arquivos**, **Emails** e **Reuniões** abaixo dela (marque as quatro caixas de seleção agora, se necessário). Essas caixas de seleção permitem que você defina onde esse rótulo de confidencialidade será usado para que você possa definir as configurações de proteção aplicáveis. Selecione **Avançar**.

7. Na página **Escolher configurações de proteção para os tipos de itens selecionados**, você pode iniciar o processo de usar configurações de criptografia para restringir o acesso ao conteúdo ao qual o rótulo será aplicado. Quando um documento, email ou convite para reunião é criptografado, o acesso ao conteúdo fica restrito, de modo que:  <br/>

    - Ele só pode ser descriptografado por usuários autorizados com base nas configurações de criptografia do rótulo.
    - Ele permanece criptografado, independentemente de onde for mantido (dentro ou fora da sua organização), e mesmo que o arquivo seja renomeado.
    - Ele seja criptografado em repouso (por exemplo, em uma conta do OneDrive) e em trânsito (por exemplo, uma mensagem de email que passa pela Internet).

   Holly deseja definir as configurações de criptografia, portanto, na página **Escolher configurações de proteção para os tipos de itens selecionados**, marque a caixa de seleção **Controlar acesso**. Marque também a caixa de seleção **Aplicar marcação de conteúdo** para que você possa definir posteriormente as configurações de cabeçalho, rodapé e marca d'água. Selecione **Avançar**.

8. Como você selecionou a opção **Controlar acesso** na página anterior, a página **Controle de acesso** agora é exibida. Esta página permite que você configure como o rótulo aplica criptografia. Você pode optar por:  <br/>

    - **Remover configurações de controle de acesso se já estiverem aplicadas a itens:** quando você seleciona essa opção, a aplicação do rótulo remove a criptografia existente, mesmo que ela tenha sido aplicada independentemente de um rótulo de confidencialidade. É importante entender que essa configuração pode resultar em um rótulo de confidencialidade que os usuários podem não conseguir aplicar quando não tiverem permissões suficientes para remover a criptografia existente.  
    - **Definir configurações de controle de acesso:** essa opção ativa a criptografia com o gerenciamento de direitos. Ela também torna visíveis as seguintes configurações: <br/>
        - Atribuir permissões agora ou permitir que os usuários decidam?
        - O acesso do usuário ao conteúdo expira
        - Permitir acesso offline

    **Observação:** é uma estratégia de implantação comum configurar inicialmente rótulos de confidencialidade para não aplicar criptografia e, posteriormente, editar alguns dos rótulos existentes para aplicar criptografia. Esta é a abordagem que Holly quer adotar. <br/>

    Dessa forma, clique na opção **Remover configurações de controle de acesso se já tiver sido aplicada aos itens** e selecione **Avançar**.

9. Como você selecionou a opção **Aplicar marcação de conteúdo** na página anterior, a página **Marcação de conteúdo** agora será exibida. Defina o botão de alternância de **Marcação de conteúdo** como **Ativado**. Isso exibe três opções que permitem personalizar como deseja marcar arquivos e emails. <br/>

    Selecione todas as três caixas de seleção. Em cada configuração, selecione **Personalizar texto**. Isso abre um painel para personalizar essa configuração específica. Insira as seguintes informações no painel **Personalizar** para cada opção (selecione **Salvar** depois de inserir as configurações de cada opção): <br/>

    - **Adicionar uma marca d’água** 
        - Texto de marca d'água: **Confidencial – Não Compartilhar** (Dica: depois de inserir esse valor, copie-o (Ctrl+C) para que você possa colá-lo (Ctrl+V) nas outras duas configurações de texto)
        - Tamanho da fonte: **25**
        - Cor da fonte: **Azul**
        - Layout de texto: **Diagonal**
            
    - **Adicionar um cabeçalho** 
        - Cabeçalho texto: **Confidencial – não compartilhar**
        - tamanho da fonte: **25**
        - Cor da fonte: **Vermelho**
        - Alinhar texto: **Centro**
            
    - **Adicionar um rodapé**
        - Texto do rodapé: **Confidencial – não compartilhar**
        - tamanho da fonte: **25**
        - Cor da fonte: **Vermelho**
        - Alinhar texto: **Centro**

10. Na página **Marcação de conteúdo**, selecione **Próximo**. 

11. Na página **Rotulagem automática de arquivos e emails**, defina a **Rotulagem automática de arquivos e emails** como **Ativada**. Isso habilita uma série de opções que você atualizará nas próximas etapas.

12. Em **Detectar conteúdo que corresponda a essas condições** selecione **+ Adicionar condição** e depois selecione **Conteúdo contém**.

13. Na janela **Conteúdo contém**, selecione a seta suspensa **Adicionar** e selecione **Tipos de informações confidenciais**.

14. Na janela **Tipos de informações confidenciais**, passe o mouse à esquerda do título da coluna **Nome**. Marque a caixa de seleção exibida, que seleciona automaticamente todos os tipos de informações confidenciais. Selecione **Adicionar**, que adicionará todos esses tipos de informações confidenciais ao seu rótulo.

15. Na página **Rotulagem automática de arquivos e emails**, todos os tipos de informação confidencial selecionados serão exibidos. Role até a parte inferior da janela e atualize as seguintes configurações:

    - Quando o conteúdo corresponder a essas condições: selecione **Aplicar rótulo automaticamente**

    - Exiba esta mensagem aos usuários quando o rótulo for aplicado: insira **Conteúdo confidencial foi detectado e será criptografado**.
        
16. Selecione **Avançar**.

17. Na página **Definir configurações de proteção para grupos e sites**, deixe as caixas de seleção em branco e selecione **Próximo**.

18. Na página **Rotulagem automática de ativos de dados esquematizados (versão prévia)**, não habilite a rotulagem automática para ativos de dados esquematizados (versão prévia). Selecione **Avançar**. 

19. Na página **Examinar suas configurações e concluir**, analise as informações inseridas. Se alguma configuração precisar ser corrigida, selecione a opção **Editar** correspondente e faça as alterações necessárias. Quando todas as informações estiverem corretas, selecione **Criar rótulo**.

20. Uma caixa de diálogo **Erro do Cliente** deve aparecer, indicando que o blob de regras gerado para o rótulo que você está tentando criar é muito longo. O tamanho máximo de seleções de tipo de informações confidenciais que você pode fazer ao mesmo tempo por regra é **49.152**. Ao selecionar todos os tipos de informações confidenciais como você fez na janela **Tipos de informações confidenciais** algumas etapas atrás, você excedeu esse limite. <br/>

    **OBSERVAÇÃO: De forma intencional, fizemos com que você selecionasse todos os tipos de informações confidenciais para receber esse erro.** Queríamos que você recebesse esse erro para que, se isso acontecer em seus ambientes de produção, você saiba por que recebeu o erro e como pode corrigi-lo.  <br/>

    Para corrigir esse problema, selecione **OK** na caixa de diálogo **Erro do Cliente** e, na página **Examinar as configurações e concluir**, role para baixo até a seção **Rotulagem automática de arquivos e emails** e selecione **Editar**.
    
21. Isso deve retornar você à página **Escolher configurações de proteção para itens rotulados** no assistente. Selecione **Próximo** nesta página, selecione **Próximo** na página **Criptografia** e selecione **Próximo** na página **Marcação de Conteúdo**. Isso levará você para a página **Rotulagem automática de arquivos e emails**. 

22. Na página **Rotulagem automática de arquivos e emails**, à direita da condição **Conteúdo contém**, selecione o **ícone de lixeira**. Isso removerá a condição **Conteúdo contém** existente para o rótulo **PII** que você criou. <br/>

    Nas etapas restantes, você adicionará uma nova condição que contém apenas dois tipos de informações de confidencialidade em vez de todos os tipos de informações de confidencialidade como você fez originalmente.

23. Na página **Rotulagem automática de arquivos e emails**, em **Detectar conteúdo que corresponda a essas condições**, selecione **+ Adicionar condição** e depois selecione **Conteúdo contém**.

24. Na janela **Conteúdo contém**, selecione a seta suspensa **Adicionar** e selecione **Tipos de informações confidenciais**.

25. Na janela **Tipos de informações confidenciais**, na lista de tipos de informações confidenciais, selecione apenas as caixas de seleção **número de roteamento ABA** e ** Número do seguro social (SSN) dos EUA**, e depois selecione **Adicionar**. De volta à página **Rotulagem automática de arquivos e emails**, ambos os tipos de informações confidenciais serão exibidos. Selecione **Avançar**.

26. Na página **Definir configurações de proteção para grupos e sites**, deixe as duas caixas de seleção em branco e selecione **Próximo**.

27. Na página **Rotulagem automática de ativos de dados esquematizados (versão prévia)**, não habilite a rotulagem automática de colunas de banco de dados. Selecione **Avançar**.

28. Na página **Examinar suas configurações e concluir**, selecione **Criar rótulo**.

29. Na página **Seu rótulo de confidencialidade foi criado**, selecione a opção **Não criar uma política ainda** e selecione **Concluído**. Isso o leva de volta à página **Rótulos**.

30. Agora é hora de publicar o rótulo **PII**. Na página **Rótulos**, se o rótulo **PII** não aparecer na lista de rótulos, selecione **Atualizar** na barra de menus. Depois que o rótulo **PII** for exibido, marque a caixa de seleção que aparece à esquerda dele. 

31. Selecione a opção **Publicar rótulo** que aparece na barra de menus acima da lista de rótulos. Isso inicia um assistente **Criar política**.

32. No assistente **Criar política**, na página **Escolher rótulos de confidencialidade para publicar**, o rótulo **PII** já está listado, portanto, selecione **Próximo**. 

33. Na página **Atribuir unidades de administrador**, selecione **Próximo**, pois você atribuirá essa política de PII ao diretório completo do Adatum em vez de apenas um grupo selecionado de unidades de administração.

34. Na página **Publicar em usuários e grupos**, você pode escolher se deseja disponibilizar sua política para todos os usuários e grupos ou pode limitar a política a usuários e grupos selecionados. Para este laboratório, você deseja disponibilizar a política para todos. A opção **Usuários e grupos** já está selecionada por padrão (caso contrário, selecione-a agora). Isso disponibilizará sua política para todos os usuários e grupos. Selecione **Avançar**.  <br/>

    **Observação:** Ao fazer isso em sua implantação real, se você quiser limitar sua política a um número selecionado de usuários ou grupos, selecione **Editar** e faça essas seleções. 

35. Na página **Configurações de política**, marque a caixa de seleção **Os usuários devem fornecer uma justificativa para remover um rótulo ou diminuir sua classificação** e depois selecione **Próximo**. 

36. Na página **Aplicar um rótulo padrão a documentos**, selecione **PII** no menu suspenso exibido e selecione **Próximo**.

37. Na página **Aplicar um rótulo padrão a emails**, selecione **PII** no menu suspenso exibido e selecione **Próximo**.

38. Na página **Aplicar um rótulo padrão a eventos de calendário e reuniões**, selecione **PII** no menu suspenso exibido e selecione **Próximo**.

39. Na página **Aplicar um rótulo padrão a conteúdo do Fabric e do Power BI**, selecione **PII** no menu suspenso exibido e selecione **Próximo**.

40. Na página **Nomeie sua política**, insira **Política de PII** no campo **Nome** e insira (ou copie e cole) a seguinte descrição para essa política de rótulo de confidencialidade: **A finalidade dessa política é detectar informações confidenciais, como números de roteamento bancário ABA e números do seguro social dos EUA em emails e documentos, e criptografar essas informações quando forem descobertas. O usuário deve fornecer uma explicação para remover o rótulo de classificação.** Selecione **Avançar**.

41. Na página **Examinar e concluir**, analise as informações inseridas. Se algo precisar ser corrigido, selecione a opção **Editar** correspondente e faça as correções necessárias. Quando todas as informações estiverem corretas, selecione **Enviar**.

42. Na página **Nova política criada**, selecione **Concluído**.

43. Deixe o navegador Edge aberto junto com todas as guias. 


### Tarefa 3 - Atribuir um rótulo de confidencialidade pré-existente a um documento

Conforme descrito nas instruções no início deste laboratório, não é possível testar imediatamente o rótulo de confidencialidade e a política de rótulo que você criou na tarefa anterior. Isso ocorre porque demora até 24 horas para que uma nova política de rótulo seja propagada por meio do Microsoft 365 e para que seu rótulo fique visível em aplicativos como o Microsoft Word e o Outlook.

Em vez disso, você testará um dos rótulos de confidencialidade pré-existente do Microsoft 365. Para este laboratório, você usará o rótulo de confidencialidade **Project – Falcon**, que é um rótulo Altamente Confidencial. Esse rótulo é semelhante ao rótulo que você criou na tarefa anterior. A única exceção é que ele não inclui um cabeçalho ou rodapé. Usar esse rótulo pré-existente mostrará como o rótulo criado funcionaria no Adatum.

1. No LON-CL1, no navegador Edge, você deve continuar conectado no Microsoft 365 como **Holly Dickson**.

2. Você primeiro revisará o rótulo de confidencialidade do **Project-Falcon** que aplicará a um documento nessa tarefa.  No seu navegador Edge, você ainda deve ter uma guia aberta para o portal **Microsoft Purview** da tarefa anterior. No portal do **Microsoft Purview**, no grupo **Proteção de informações** do painel de navegação, selecione **Rótulos**. 

3. Na página **Rótulos**, na lista de rótulos, selecione a seta para a direita (**>**) ao lado de **Altamente Confidencial** para mostrar os sub-rótulos sob esse rótulo. Fazer isso exibe o rótulo **Project - Falcon** pré-existente.

4. Selecione o rótulo **Projeto - Falcon** (não a caixa de seleção; selecione o nome do rótulo). Fazer isso abre um painel de detalhes **Projeto - Falcon**. Revise as informações definidas para esse rótulo e feche o painel quando terminar.  

5. Agora você atribuirá o rótulo de confidencialidade do **Project-Falcon** a um documento. Selecione a guia **Página Inicial | Microsoft 365** no navegador para retornar à página inicial do Microsoft 365. Selecione o ícone **Aplicativos** no lado esquerdo da tela. Na página **Aplicativos** que aparece, clique com o botão direito do mouse no bloco **Word** e selecione **Abrir em nova guia**. 

6. Na guia **Word | Microsoft 365**, na seção **Criar** na parte superior da página, selecione **Documento em branco**.

7. Se uma janela **Sua opção de privacidade** aparecer, selecione **Fechar**.

8. Se a faixa de opções do Word exibir ícones para cada recurso, mas não dividir os ícones por grupo, selecione a seta para baixo no lado direito da faixa de opções e, em seguida, no **Layout da faixa de opções**, selecione **Faixa de opções clássica**. Isso mudará a faixa de opções para o estilo tradicional que é dividido por grupo de recursos (como Desfazer, Área de Transferência, Fonte, Parágrafo, Estilos e assim por diante).

9. No documento do **Word**, digite o seguinte texto: **Testar um rótulo de confidencialidade em um documento com informações de identificação pessoal (PII); nesse caso, um número do seguro social dos EUA: 111-11-1111.**

10. Como você habilitou rótulos de Confidencialidade no início deste exercício, **Word** deve exibir um grupo de **Confidencialidade** na faixa de opções na parte superior da página. Selecione a seta para baixo no grupo de **Confidencialidade**. No menu suspenso exibido, ele deve exibir a lista de tipos de rótulo de confidencialidade. Selecione **Altamente Confidencial** e, no submenu exibido, selecione **Project – Falcon**. <br/>

    **Observação:** Após 24 horas, o rótulo que você criou na tarefa anterior aparecerá no submenu Altamente Confidencial, próximo ao rótulo Project-Falcon. Mas, por enquanto, você usará o rótulo **Project – Falcon** em seu lugar.

11. No documento, observe como o rótulo aplicou uma marca d'água **CONFIDENCIAL – ProjectFalcon** na parte superior do documento. O rótulo Project – Falcon foi configurado exatamente como o rótulo que você criou, onde a marca d'água deveria aparecer de forma diagonal no meio da página. Então, por que ela aparece na parte superior da página? A resposta é que você está usando o **Word para a web**, que por padrão a exibe como você vê aqui. Para ver como ela será exibida para alguém que está lendo o documento, você deve ver o documento no **Modo de Exibição de Leitura**, o que você fará agora. <br/>

    Selecione a guia **Exibir** e, na faixa de opções do Word, selecione **Modo de Exibição de Leitura**. Observe como a marca d'água aparece de forma diagonal no meio do documento. É assim que a marca d'água aparecerá para alguém lendo o documento. Observe que, se você usar o aplicativo do Word para área de trabalho, ele exibirá a marca d'água como designada pelo rótulo, que nesse caso seria exatamente como você a vê aqui no Modo de Exibição de Leitura. <br/>

    Para sair do Modo de Exibição de Leitura, selecione **Editar Documento** na barra de menus na parte superior da página. No menu suspenso exibido, selecione **Editar**.

12. Neste primeiro teste de validação, você removerá esse rótulo de confidencialidade de ser aplicado a este documento. Uma das opções de política de rótulo exige que os usuários forneçam justificativa para remover um rótulo ou selecionar um rótulo de classificação inferior. Agora você verificará se essa configuração está funcionando corretamente. <br/>

    No grupo de **Confidencialidade** na faixa de opções do Word, selecione a seta para baixo. No menu suspenso exibido, observe que uma marca de seleção aparece ao lado de **Altamente Confidencial**. Mantenha o mouse sobre **Altamente Confidencial** para ver o submenu. Observe como uma marca de seleção aparece ao lado de **Project – Falcon**. As marcas de seleção identificam o rótulo atual que está sendo aplicado ao documento.  <br/>
 
    Para remover o rótulo deste documento, selecione o rótulo **Project – Falcon** que aparece neste menu suspenso.
    
13. Na janela exibida **Justificativa necessária**, selecione a opção **Outro (explicar)**. No campo **Explicar por que você está alterando esse rótulo**, insira **Testando o que acontece quando um rótulo é removido de um documento** e selecione **Alterar**.

14. Observe como a marca d'água no documento desapareceu. No grupo de **Confidencialidade** na faixa de opções do Word, selecione a seta para baixo. No menu suspenso exibido, observe que, embora **Altamente confidencial** > **Project – Falcon** seja exibido, nenhuma marca de seleção será exibida ao lado deles. Isso indica que o rótulo de confidencialidade não está mais sendo aplicado a este documento.  

15. Para aplicar novamente o rótulo de confidencialidade ao documento, selecione **Altamente Confidencial** > **Project – Falcon** no menu suspenso. Observe como a marca d'água reapareceu no documento.

16. Agora você salvará o documento para poder compartilhá-lo na próxima tarefa. Um campo de nome de documento que contém uma seta suspensa aparece no canto superior esquerdo da página, à direita do ícone do Word (o Word pode exibir **Documento** ou **Documento1** como o nome do arquivo temporário). Selecione a seta suspensa. No menu suspenso exibido, garanta que no arquivo **Localização** esteja escrito **Holly Dickson > Documentos**. <br/>

    No campo **Nome do Arquivo**, renomeie o arquivo para **DocumentoProtegido1** e selecione fora desse menu de nome de arquivo (selecione dentro do documento). Observe que o novo nome atribuído ao arquivo aparece na barra de título. 

17. Deixe a guia **DocumentoProtegido1** aberta mostrando o documento. Você retornará a este documento na próxima tarefa para compartilhar o documento com Joni Sherman.

Você acabou de criar com sucesso um documento do Word contendo o rótulo Altamente Confidencial intitulado **Projeto - Falcon**. 


### Tarefa 4 - Proteger um documento usando a Proteção de Informações do Microsoft Purview

Na tarefa anterior, você criou um documento do Word e o protegeu com o rótulo de confidencialidade **Project – Falcon**. Esse rótulo inseriu uma marca d'água no documento. Nesta tarefa, você compartilhará o documento criado com Joni Sherman e restringirá Joni à permissão "Somente exibição". Isso permitirá que você veja como a Proteção de Informações do Microsoft Purview protege o documento com base nos parâmetros configurados.

Para verificar se a proteção atribuída ao documento funciona, envie primeiro o documento por email para duas pessoas: para Joni Sherman e para seu endereço de email pessoal. Em seguida, você verificará se Joni só pode ver o documento e não editá-lo, e se você não pode acessar o documento, pois ele não foi compartilhado com você. Por fim, você alterará a permissão no documento para que Joni possa editá-lo e enviará este documento atualizado por email para ela para teste. A finalidade dos dois emails para Joni, um com um link de documento que fornece acesso somente leitura e outro com um link de documento que fornece a capacidade de editar o documento, é ver como o Microsoft Entra ID Protection pode fornecer vários níveis de proteção de documentos. 

1. No LON-CL1, no navegador Edge, você deve continuar conectado no Microsoft 365 como **Holly Dickson** na tarefa anterior com a guia **Word** aberta.

2. No navegador Edge, selecione a guia **Aplicativos | Microsoft 365**. 

3. Na página **Aplicativos**, clique com o botão direito do mouse no bloco **Outlook** e selecione **Abrir em nova guia**. Isso abre a caixa de correio da Holly no Outlook na web em uma nova guia do navegador. 

4. No **Outlook na Web**, selecione **Novo email** na parte superior da tela.

5. Insira as seguintes informações no formulário do email:

    - Para: Insira **Joni** e selecione **Joni Sherman** na lista de usuários. 

    - CC: Insira seu endereço de email pessoal (não insira o endereço de email da Holly; em vez disso, insira seu endereço de email pessoal) e selecione a mensagem **Use este endereço: <your email address>** que é exibida

    - Adicione um assunto: **Teste de Documento Protegido – Permissão de Somente exibição**

    - Corpo da mensagem: insira **Abra o documento protegido anexado a este email e tente alterá-lo.**

6. No corpo da mensagem, no texto que você adicionou na etapa anterior, você anexará um link ao documento criado na tarefa anterior. No entanto, para fazer isso, primeiro você deve compartilhar o documento com Joni Sherman e, ao fazer isso, aplicará permissões restritas de **Somente exibição**. Para fazer isso, você deve deixar este email e retornar ao seu documento e compartilhá-lo com Joni. Depois de copiar o link criado durante o processo de compartilhamento, você retornará a esse email e colará no link. <br/>

    No navegador Edge, selecione a guia **DocumentoProtegido1**, que ainda deve exibir o documento que você criou na tarefa anterior. No lado superior direito da página, abaixo do nome e das iniciais de Holly Dickson, selecione o botão **Compartilhar**. No menu suspenso exibido, selecione **Compartilhar**.

7. Na janela **Compartilhar "DocumentoProtegido1"** exibida, selecione o ícone de engrenagem (**Configurações de link**) que aparece ao lado do botão **Copiar link**. 

8. Na janela **Configurações de link** exibida, selecione a opção **Pessoas selecionadas**.
    
9. Em **Mais configurações**, a opção atual é **Pode editar**. Você planeja compartilhar este documento com Joni Sherman, mas só quer que Joni veja o documento. Para alterar essas permissões, selecione **Pode editar**. No menu exibido, analise as opções disponíveis. Você pode ver que **Pode editar** tem uma marca de seleção ao lado dela, o que indica que essa é a configuração atual. Para limitar Joni à permissão de somente leitura, selecione **Pode exibir** e selecione **Aplicar**.

10. Isso retorna você para a janela **Compartilhar "DocumentoProtegido1"**. Insira **Joni** no campo **Adicionar um nome, grupo ou email**. Uma lista de usuários cujo nome começa com **Joni** deve aparecer. Selecione **Joni Sherman**.

11. Na janela **Compartilhar "DocumentoProtegido1"**, passe o mouse sobre o ícone de olho que aparece à direita do nome de Joni. Isso deve mostrar **Pode exibir**, que é a configuração atual atribuída a ela para este documento. O ícone de olho é a designação para "Pode exibir". Selecione o botão **Copiar link**. 

12. Depois que a mensagem **Link copiado** for exibida na parte inferior da janela **Compartilhar "DocumentoProtegido1"**, selecione o X no canto superior da janela para fechá-la.

13. No navegador Edge, selecione a guia **Email – Holly Dickson – Outlook** para retornar à sua mensagem de email. No corpo da mensagem, no texto que você adicionou anteriormente, cole (Ctrl+V) no link para o documento compartilhado que você acabou de copiar para sua área de transferência. Um link para o arquivo chamado **DocumentoProtegido1.docx** deve aparecer. 

14. Selecione **Enviar**.

15. Uma mensagem **Destinatários não podem acessar links** deve aparecer. Essa mensagem é resultado do Microsoft Entra ID Protection reconhecendo o fato de que você incluiu seu endereço de email pessoal no email, que não tem permissão para acessar o documento. Para fins deste teste de laboratório, selecione **Enviar de qualquer maneira**.

16. Alterne para **LON-CL2**. 

17. No **LON-CL2**, você deve estar conectado ao **Outlook na web** como **Lynne Robbins** do exercício de laboratório anterior. Saia como Lynne.

18. No navegador Edge, feche todas as guias, exceto a guia **Sair**. Nesta guia, insira a seguinte URL na barra de endereços: **https://outlook.office365.com** 

19. Na janela **Escolher uma conta**, selecione **Usar outra conta**.

20. Na janela **Entrar**, insira **JoniS@xxxxxZZZZZZ.onmicrosoft** (em que xxxxxZZZZZZ é o prefixo de locatário fornecido pelo provedor de hospedagem do seu laboratório) e selecione **Avançar**.

21. Na janela **Inserir senha**, insira a Nova Senha de Usuário que você atribuiu anteriormente à conta do Joni e selecione **Entrar**. 

22. Se uma janela **Bem-vindo** aparecer, selecione o X para fechá-lo.

23. Na caixa de entrada de **Joni** no **Outlook na web**, você deverá ver o email que Holly acabou de enviar cuja linha de Assunto indica que o documento tem permissão de Somente Exibição. Abra este email.

24. No email, selecione o arquivo anexado para abri-lo.

25. Na janela **Sua opção de privacidade** que aparece, selecione **Fechar**. O documento é aberto no **Word na web** em uma nova guia do navegador intitulada **DocumentoProtegido1.docx**. Observe como o documento aparece no Modo de Exibição de Leitura no **Word na web**. Esta é a indicação de Joni de que ela tem permissão de Somente Exibição e não pode editar o documento. Para verificar isso, tente selecionar no documento. Observe a mensagem de aviso que aparece indicando: **Somente leitura. O documento é somente leitura.** Observe a marca d'água especificada na política **Project – Falcon**. <br/>

    Depois de concluir a revisão do documento, feche a guia **DocumentoProtegido1.docx**. 

26. Agora você testará o que acontece quando tentar abrir o documento que foi enviado para seu endereço de email pessoal. Use seu celular ou computador de sala de aula para acessar sua caixa de correio pessoal. Abra o email que Holly acabou de enviar para seu endereço de email pessoal e tente abrir o arquivo anexado. 

27. Como você não tem permissão para acessar o documento, uma janela **Escolher uma conta** deve aparecer. Em um cenário do mundo real, opcionalmente, você pode entrar com uma conta que tenha permissão para acessar o arquivo ou solicitar acesso da conta **Holly@xxxxxZZZZZZ.onmicrosoft.com**. <br/>

    Para fins deste teste, você acabou de verificar se não pode acessar o arquivo porque ele não foi compartilhado com você. Você também verificou que Joni só conseguiu exibir o arquivo, mas não editá-lo. Agora você alterará as permissões de compartilhamento no arquivo, permitindo que Joni o edite. Você fará isso para ver como essa experiência difere daquela que você acabou de concluir. 

28. Alterne para **LON-CL1**. 

29. No LON-CL1, no navegador Edge, você deve continuar conectado no Microsoft 365 como **Holly Dickson** e você deve abrir as guias **Word** e **Outlook**. Selecione a guia **Email – Holly Dickson – Outlook**. 

30. Na caixa de correio de Holly, crie outro email para Joni Sherman. NÃO inclua seu endereço de email pessoal na linha CC. Insira as seguintes informações no formulário do email:

    - Para: Insira **Joni** e selecione **Joni Sherman** na lista de usuários. 

    - CC: deixe em branco

    - Adicione um assunto: **Teste de Documento Protegido – Permissão de Edição**

    - Corpo da mensagem: insira **Abra o documento protegido anexado a este email e tente alterá-lo.**

31. Assim como no email anterior, agora você deve compartilhar o documento com Joni, mas desta vez com a permissão Editar. Para isso, execute as seguintes etapas: <br/>

    - Selecione a guia **DocumentoProtegido1** no navegador e, no lado direito da barra de menus, selecione o botão **Compartilhar**. No menu suspenso exibido, selecione **Compartilhar**. 
    - Na janela **Compartilhar "DocumentoProtegido1"**, insira **Joni** no campo **Adicionar um nome, grupo ou email** e selecione **Joni Sherman**.
    - À direita do nome de Joni está um ícone de lápis (**Pode editar**). Essa é a permissão padrão ao compartilhar um documento. Selecione o botão **Copiar link** para ver o que acontece.
    - Observe a mensagem **Link copiado** exibida. A mensagem indica que qualquer pessoa pode editar o documento, mesmo que você tenha especificado o nome de Joni. Não é isso que você quer, que é limitar Joni como a única pessoa que pode editá-lo. Para colocar essa restrição em prática, selecione o ícone de engrenagem (**Configurações de link**) ao lado do botão **Copiar link**. 
    - Na janela **Configurações de link** exibida, selecione a opção **Pessoas selecionadas**. Essa opção é a chave para limitar a permissão para usuários selecionados. 
    - Em **Mais configurações**, se **Pode editar** aparecer, selecione **Aplicar**. No entanto, se **Pode exibir** aparecer, selecione **Pode exibir** e, no menu exibido, selecione **Pode editar** e selecione **Aplicar**. 
    - Na janela **Compartilhar "DocumentoProtegido1"**, selecione o botão **Copiar link**.
    - Observe a mensagem **Link copiado** exibida. Desta vez, a mensagem indica que somente as pessoas especificadas podem editar o documento. Nesse caso, a edição será limitada à Joni, já que ela é a única pessoa que você especificou. 
    - Selecione a guia **Email – Holly Dickson – Outlook** no navegador e cole o link no corpo da mensagem de email. 

32. Selecione **Enviar**.

33. Alterne para **LON-CL2**. 

34. No **LON-CL2**, você ainda deve estar conectado ao **Outlook na web** como **Joni Sherman**. Na **caixa de entrada** de Joni, você deverá ver o email que a Holly acabou de enviar cuja linha de Assunto indica que o documento tem permissão de Edição. Abra este email.

35. No email, selecione o arquivo anexado para abri-lo.

36. Quando Joni tinha permissão de Somente Exibição, o documento foi aberto no painel Modo de Exibição de Leitura. Dessa forma, Joni não pôde editar o documento. Esta versão do documento fornece permissão de Edição à Joni, portanto, desta vez, o documento deve ser aberto no modo de edição normal do Word. Verifique se você pode inserir texto no documento. 

    **Observação:**  Nesta tarefa, você acabou de verificar se a Proteção de Informações do Microsoft Purview protegeu o documento com base nos parâmetros de política de PII que você configurou. Quando Joni recebeu a permissão de Somente Exibição, o documento foi aberto no modo de exibição Leitura e ela não pôde alterá-lo. Quando Joni recebeu a permissão de Edição, o documento foi aberto no Word e ela pôde alterá-lo. E como Holly não compartilhou o documento com você, você não pôde abri-lo quando ela enviou o documento por email para sua caixa de correio pessoal. 

## Fim do laboratório 4


# Parabéns! Você acabou de concluir o laboratório final neste curso.
