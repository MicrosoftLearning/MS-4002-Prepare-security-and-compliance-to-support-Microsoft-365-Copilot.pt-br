# Roteiro de aprendizagem 1 – Laboratório 3 – Exercício 1 – Gerenciar políticas de DLP  

Em sua função como Holly Dickson, nova Administradora do Microsoft 365 do Adatum, você tem o Microsoft 365 implantado em um ambiente de laboratório virtualizado. Ao trabalhar em seu projeto piloto do Microsoft 365, as próximas etapas são implementar políticas DLP (Prevenção contra perda de dados) no Adatum. Você começará criando uma política DLP personalizada neste exercício e, em seguida, testará as políticas DLP relacionadas a arquivamento de mensagens de email e emails com dados confidenciais. 

### Tarefa 1 – Criar uma política DLP com configurações personalizadas

Nesta tarefa, você criará uma política de Prevenção contra perda de dados no portal do Microsoft Purview para proteger dados confidenciais de serem compartilhados pelos usuários. A política DLP que você criar informará aos usuários se eles quiserem compartilhar conteúdo que contenha endereços IP. 

A política conterá duas regras ou ações, cada uma delas depende do número de endereços IP na mensagem. Se a mensagem contiver um endereço IP, a política notificará as pessoas com uma dica de política e ainda enviará a mensagem por email. No entanto, se o conteúdo contiver dois ou mais endereços IP, a mensagem será bloqueada, um email de incidente com um alto nível de confidencialidade será enviado ao remetente e uma dica de política será exibida, permitindo que o remetente substitua o bloqueio de email se o remetente fornecer uma justificativa comercial na dica de política.

1. No LON-CL1, no navegador Edge, você deve continuar conectado no Microsoft 365 como **Holly Dickson**. 

2. No **Microsoft Edge**, o portal do Microsoft Purview ainda deverá estar aberto; se não estiver, abra uma nova guia e navegue até **https://compliance.microsoft.com**.

3. No portal do **Microsoft Purview**, selecione **Soluções** no painel de navegação, **Prevenção contra perda de dados** e, em seguida, selecione **Políticas**.

4. Na página **Políticas**, clique na opção **+Criar política** na barra de menus para iniciar o assistente **Criar política**.

5. Na página **Iniciar com um modelo ou criar uma política personalizada**, a coluna **Categorias** exibirá as categorias de política. Cada categoria de política fornece modelos que podem ser usados para criar esse tipo de política, exceto para a categoria **Personalizada**. Esta categoria não fornece nenhum modelo específico, mas permite que as organizações criem políticas personalizadas do zero. Quando você seleciona uma categoria, é exibida a coluna **Modelos**, que exibe os modelos disponíveis para escolher para a categoria selecionada. Quando você seleciona um modelo, outra coluna aparece exibindo o tipo de informação protegida nesse modelo. <br/> 

    Por exemplo, selecione **Financeiro** no painel lateral e role pelos vários modelos que você pode escolher na coluna **Modelos**. Selecione um ou dois dos modelos para ver que tipo de informação ele protege. Se desejar, selecione cada uma das categorias restantes para ver que tipo de modelos são fornecidos. 
  
6. Para a finalidade deste laboratório, você criará uma política DLP personalizada. Selecione **Personalizada** na coluna **Categorias**, selecione o modelo **Política personalizado** na coluna **Modelos** e clique em **Avançar**.

7. Na página **Nomear política DLP**, insira as seguintes informações e clique em **Avançar**:  <br/>

      - Nome: **Política DLP de endereço IP**
      - Descrição: **essa política detecta a presença de endereços IP em emails. Os usuários finais recebem uma notificação sobre a detecção e os administradores recebem uma notificação. Emails com dois ou mais endereços IP são impedidos de serem enviados.**

8. Na página **Atribuir unidades administrativas**, clique em **Avançar**. 

9. Na página **Escolha onde atribuir a política**, verifique se a alternância **Status** está definida como **Ativada** para os seguintes locais (se algum desses locais não estiver definido como **Ativado** por padrão, defina-o como **Ativado** agora): <br/>

    - **Email do Exchange**
    - **Sites do SharePoint**
    - **Contas do OneDrive**
    - **Chats do Teams e mensagens de canal**

    Defina todos os outros locais como **Desativado** e clique em **Avançar**.

10. Na página **Definir configurações de política**, a opção **Criar ou personalizar regras DLP avançadas** deve ser definida por padrão (se ainda não estiver selecionada por padrão, selecione-a agora) e, em seguida, selecione **Avançar**. 

11. Na página **Personalizar regras DLP avançadas**, clique na opção **+ Criar regra** na barra de menus.

12. Na página **Criar regra**, insira as seguintes informações:
    
      - Nome: **Regra de endereço IP único**
    
      - Descrição: **O email contém um endereço IP**
    
      - Na seção **Condições**, selecione **+Adicionar condição** e, em seguida, selecione **O conteúdo contém** no menu suspenso exibido. Depois, insira as seguintes configurações de condição:
    
        - No campo **O conteúdo contém**, clique no menu suspenso **Adicionar** e em **Tipos de informações confidenciais**.
        
        - No painel **Tipos de informações confidenciais**, digite **IP** dentro do campo **Pesquisar** e pressione Enter.
        
        - Nos resultados da pesquisa, marque a caixa de seleção **Endereço IP** e clique em **Adicionar**.
        
     - Role até a seção **Notificações do usuário** e defina o botão de alternância **Usar notificações para informar os usuários e ajudar a instruí-los sobre o uso adequado de informações confidenciais** como **Ativado**.

    - Marque a caixa de seleção **Notificar usuários no serviço do Office 365 com uma dica de política**. Na seção **Dicas de política**, marque a caixa de seleção **Personalizar o texto da dica de política**. 

        - Holly quer que você personalize a mensagem de Dica de Política, então digite o seguinte texto neste campo: **ATENÇÃO! Você inseriu informações confidenciais (um endereço IP) nesta mensagem. Não impediremos que você envie esta mensagem, mas verifique se os destinatários estão autorizados a ver esses dados confidenciais.** 

    - Marque a caixa de seleção **Mostrar a dica de política como uma caixa de diálogo para o usuário final antes do envio (disponível somente para carga de trabalho do Exchange)**. 
    
    - Na seção **Relatórios de incidentes**, verifique se o botão de alternância **Enviar um alerta aos administradores quando ocorrer uma correspondência de regra** está definido como **Ativado** (se necessário, defina-o como **Ativado**)

    - Selecione o botão **Salvar** na parte inferior da página.

13. Na página **Personalizar regras DLP avançadas**, a **regra de Endereço IP único** que você acabou de criar agora aparecerá. Selecione a opção **+Criar regra** para criar a segunda regra DLP. 

14. Na página **Criar regra**, insira as seguintes informações:
    
    - Nome: **Regra de vários endereços IP**
    
    - Descrição: **O email contém dois ou mais endereços IP**
    
    - Na seção **Condições**, selecione **+Adicionar condição** e, em seguida, selecione **O conteúdo contém** no menu suspenso exibido. Depois, insira as seguintes configurações de condição:
    
        - No campo **O conteúdo contém**, clique no menu suspenso **Adicionar** e em **Tipos de informações confidenciais**.
        
        - No painel **Tipos de informações confidenciais**, digite **IP** dentro do campo **Pesquisar** e pressione Enter.
        
        - Marque a caixa de seleção **Endereço UP** e depois selecione **Adicionar**.

        - Na seção **Tipos de informações confidenciais**, o tipo de informação **Endereço IP** é exibido. No lado direito da linha Endereço IP, a configuração **Contagem de instâncias** é definida de **1** para **Qualquer**. Altere o valor do primeiro campo de 1 para **2**. Ao fazer essa alteração, essa regra só será aplicada se dois ou mais endereços IP aparecerem no email. 
    
    - Na seção **Ações**, selecione **+ Adicionar uma ação**. No menu suspenso exibido, selecione **Restringir o acesso ou criptografar o conteúdo em locais do Microsoft 365**. Em seguida, insira as seguintes configurações de ação:

    - Se nenhuma opção aparecer na seção **Restringir o acesso ou criptografar o conteúdo em locais do Microsoft 365**, selecione-a agora para expandir esta seção. Esta seção exibirá a opção **Impedir que os usuários recebam emails ou acessem arquivos compartilhados do SharePoint, OneDrive e Teams**, que é selecionada por padrão. Mantenha esta opção selecionada.

    - Na opção **Impedir que os usuários recebam emails ou acessem arquivos compartilhados do SharePoint, OneDrive e Teams**, selecione a opção **Bloquear todos**.
    
    - Na seção **Notificações do usuário**, defina o botão de alternância **Usar notificações para informar os usuários e ajudar a instruí-los sobre o uso adequado de informações confidenciais**, e como **Ativado**. 

    - Marque a caixa de seleção **Notificar usuários no serviço do Office 365 com uma dica de política**. Na seção **Dicas de política**, marque a caixa de seleção **Personalizar o texto da dica de política**. 

        - Holly quer que você personalize a mensagem de Dica de Política, então digite o seguinte texto neste campo: **ATENÇÃO! Você inseriu informações confidenciais (vários endereços IP) nesta mensagem. Bloquearemos você se tentar enviar esta mensagem. Substituir esse bloqueio indica que você autorizou o envio desses dados confidenciais aos destinatários.** 

    - Marque a caixa de seleção **Mostrar a dica de política como uma caixa de diálogo para o usuário final antes do envio (disponível somente para carga de trabalho do Exchange)**. 
    
    - Na seção **Substituições do usuário**, marque a caixa de seleção **Permitir substituições de arquivos do Microsoft 365 e itens do Microsoft Fabric**. Isso permite configurações adicionais que indicam como as substituições serão tratadas. Marque cada uma das caixas de seleção para as duas opções a seguir:

        - **Exigir que uma justificativa comercial seja substituída**
        - **Substituir a regra automaticamente se for reportada como um falso positivo**
    
    - Na seção **Relatórios de incidentes**, verifique se o botão de alternância **Enviar um alerta aos administradores quando ocorrer uma correspondência de regra** está definido como **Ativado** (se necessário, defina-o como **Ativado**).

    - Selecione o botão **Salvar** na parte inferior da página.

15. Na página **Personalizar regras DLP avançadas**, a regra **Endereço IP único** e a regra de **Endereço IP múltiplo** serão exibidas. Selecione **Avançar**.

16. Na página **Modo de política**, clique na opção **Ativar a política imediatamente** e em **Avançar**.

17. Na página **Revisar e concluir**, revise a política que você acabou de criar. Se algo precisar ser corrigido, selecione a opção **Editar** apropriada e faça as correções. Quando estiver tudo certo, clique em **Enviar**.

18. Pode levar cerca de um minuto para que a página **Nova política criada** apareça. Quando ela aparecer, clique em **Concluído**.

19. Deixe o navegador Edge aberto. Não feche nenhuma das guias.


Você criou uma política DLP que verifica endereços IP em emails e documentos enviados ou compartilhados em sua organização.


### Tarefa 2 – Desativar o recurso Enviar para o Kindle que ignora políticas DLP

Holly Dickson, administradora do Microsoft 365 da Adatum, descobriu recentemente sobre um recurso **Enviar para o Kindle** no Microsoft 365 que permite enviar documentos do Microsoft Word diretamente para a biblioteca do Kindle em poucos minutos. Um arquivo transferido pode aparecer como um livro Kindle com tamanhos de fonte ajustáveis ou como um documento impresso com layouts fixos para preservar a formatação do design da página. 

O problema com esse recurso é que as políticas DLP não levam em consideração o compartilhamento de arquivos do Word com o Kindle, o que, na verdade, ignora os controles DLP. Como o Adatum não usará esse recurso **Enviar para o Kindle**, Holly quer desativá-lo para evitar qualquer possibilidade de os usuários ignorarem as políticas DLP da empresa. 

Para desativar essa configuração, você deve criar uma política para aplicativos do Office no centro de administração Microsoft Intune. Na política criada, você adicionará a configuração **Desativar Enviar para o Kindle** à política e, em seguida, ativará essa configuração. Ativar essa configuração na política desativará o recurso **Enviar para o Kindle** assim que você terminar de criar a política. A partir de então, os usuários não poderão mais enviar documentos do Word para a biblioteca do Kindle.

**Observação:** esse problema é algo que você deve considerar abordar em suas implantações reais do Microsoft 365. Para mais informações sobre o recurso **Enviar para o Kindle**, consulte https://support.microsoft.com/office/send-to-kindle-a53d880d-9952-4bf1-abc5-6bce8db5a273.

1. No LON-CL1, no navegador Edge, você deve continuar conectado no Microsoft 365 como **Holly Dickson**. 

2. No navegador Edge, localize a guia **Centro de administração do Microsoft 365**. No painel de navegação do Centro de administração do Microsoft 365, no grupo **Centros de administração**, selecione **Endpoint Manager**.

3. No **centro de administração do Microsoft Intune** aberto em uma nova guia, clique em **Aplicativos** no painel de navegação.

4. Na página **Aplicativos | Visão geral**, no painel de navegação do meio, clique em **Políticas para aplicativos do Office** na seção **Política**.

5. Na página **Aplicativos | Políticas para aplicativos do Office**, clique no botão **Criar**. Isso iniciará o assistente para criar uma nova política. Nas etapas restantes, você ativará a configuração **Desativar Enviar para o Kindle** nesta política.

6. Na página **Iniciar com o básico**, insira a configuração **Desativar Enviar para o Kindle** no campo **Nome** e clique em **Avançar**.

7. Na página **Escolher o escopo**, clique na opção **Esta configuração de política se aplica a todos os usuários** e, em seguida, selecione **Avançar**.

8. Na página **Definir configurações**, observe as métricas exibidas acima da lista de configurações. Há mais de 2.200 configurações de aplicativo do Office para sua configuração de locatário. Para localizar rapidamente essa configuração, digite **Kindle** no campo **Pesquisar** e pressione **Enter**. Isso exibirá todas as políticas que tiverem **Kindle** no nome.

9. Como você pode ver, há apenas uma configuração do Kindle, que é **Desativar Enviar para o Kindle**. Selecione essa configuração, que abrirá o painel **Desativar Enviar para o Kindle**.

10. No painel **Desativar Enviar para o Kindle**, as plataformas e os aplicativos aos quais essa configuração se aplica são exibidos. Na descrição, clique na opção **Mostrar mais**. Termine de ler a descrição completa dessa configuração.

11. Clique na seta suspensa no campo **Definição de configuração**. No menu suspenso exibido, clique em **Ativado**.

12. Clique no botão **Aplicar** na parte inferior do painel.

13. Na página **Definir configurações**, a política **Desativar Enviar para o Kindle** aparecerá e o **Status** estará definido como **Configurado**. Selecione **Avançar**.

14. Na página **Revisar configuração e criar**, clique no botão **Criar**. 

15. Na página **Configuração de política criada**, selecione **Concluído**.
 
16. Deixe o navegador Edge aberto. Não feche nenhuma das guias.


Ao ativar essa configuração **Desativar Enviar para o Kindle** na nova política que você acabou de criar, você desativou o recurso **Enviar para o Kindle**. Isso impedirá que os usuários do Adatum enviem documentos do Word para a biblioteca do Kindle, o que ignora as políticas DLP da empresa.


# Prossiga para o Laboratório 3 – Exercício 2 
