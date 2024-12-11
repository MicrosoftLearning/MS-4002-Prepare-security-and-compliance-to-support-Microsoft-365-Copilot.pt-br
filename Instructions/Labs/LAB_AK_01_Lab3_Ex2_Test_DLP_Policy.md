# Roteiro de aprendizagem 1 – Laboratório 3 – Exercício 2 – Testar a política DLP

Holly Dickson agora chegou ao ponto do projeto piloto em que quer testar a política DLP relacionada a emails que contêm informações confidenciais que você criou no exercício de laboratório anterior. 

**OBSERVAÇÃO:** no passado, tivemos problemas intermitentes em que as políticas DLP e as dicas de política não funcionavam conforme o esperado neste exercício de laboratório. Isso ocorre devido a problemas de limitação que às vezes ocorrem entre nosso ambiente de laboratório de VM e o locatário de avaliação do Microsoft 365. Isso não é indicativo da experiência normal em ambientes de produção do Microsoft 365. Também não é indicativo da experiência normal de treinamento. Pedimos desculpas se você tiver esse problema durante este exercício de laboratório.

### Tarefa 1 – Testar a primeira regra da política DLP

No exercício anterior, você criou uma política DLP personalizada que pesquisa nos emails informações confidenciais relacionadas a endereços IP em seu locatário Adatum. Essa política incluía duas regras: uma que verificava emails contendo um único endereço IP e outra que verificava emails contendo dois ou mais endereços IP. 

Nesta tarefa, você enviará um email de Holly Dickson para Lynne Robbins que testará a primeira regra (endereço IP único). Quando essa regra for disparada, uma dica de política de email será exibida na caixa de correio do Outlook do remetente que informa ao remetente que o email contém dados confidenciais. O remetente também receberá uma notificação por email, mas o email ainda será enviado ao destinatário.

1. No LON-CL1, no navegador Edge, você deve continuar conectado no Microsoft 365 como **Holly Dickson**. 

2. Agora você enviará um e-mail de Holly para Lynne Robbins e incluirá um endereço IP no corpo do email. <br/>

    No **Microsoft Edge**, clique na guia **Página inicial | Microsoft 365** e clique no ícone do **Outlook** na coluna de ícones de aplicativos no lado esquerdo da tela. Quando o Outlook na Web abrir, o logon será feito automaticamente como Holly Dickson.  <br/>

    **Observação:** se o **Outlook na Web** já estiver aberto, verifique se o logon foi feito como **Holly** clicando no ícone do usuário no canto superior direito (o círculo **HD**). Se o Outlook estava aberto para qualquer outro usuário, feche a guia e repita as instruções nesta etapa para abrir o Outlook na Web para Holly.

3. No canto superior esquerdo da tela, selecione **Novo email**. 

4. No painel de mensagens que é exibido à direita da tela, insira as seguintes informações:

    - Para: digite **Lynne** e selecione **Lynne Robbins** na lista de usuários que aparece

    - Adicione um assunto: **Teste da política DLP 1**

    - Área de mensagem: **Hey Lynne – Vou configurar este endereço IP: 192.168.0.1**

    **Observação:** ao redigir este email com dados confidenciais (neste caso, um endereço IP), ele acionará a política de endereço IP que você criou anteriormente e, especificamente, a regra de endereço IP único. Dessa forma, uma **Dica de política** será exibida indicando que a mensagem de email viola uma política organizacional. Você ignorará essa dica de política e enviará o email de qualquer maneira para testar o restante da política DLP, que enviará um email de notificação para Holly.

5. Depois que a dica de política for exibida, selecione **Enviar.**

6. Selecione a pasta **Itens enviados** de Holly para verificar se o email foi enviado.

7. Selecione a pasta **Caixa de entrada** de Holly. Holly receberá um email do **Microsoft Outlook** com o assunto: **Notificação: Teste da Política DLP 1**. Selecione este email e revise o conteúdo. 

8. Alterne para **LON-CL2**. 

9. Se você precisar entrar na VM, a conta local **LON-CL2\admin** aparecerá por padrão, então insira **Pa55w.rd** no campo **Senha** para fazer login. 

10. Na barra de tarefas, clique no ícone do navegador **Edge**.

11. No navegador Edge, insira o seguinte URL: **https://outlook.office365.com**

12. Na janela **Escolher uma conta**, selecione a conta de Lynne Robbin (**LynneR@xxxxxZZZZZZ.onmicrosoft.com**, em que xxxxxZZZZZZ é o prefixo de locatário fornecido pelo provedor de hospedagem do seu laboratório). Na janela **Inserir senha**, insira a Nova Senha de usuário atribuída à conta de Lynne e clique em **Entrar**. 

13. Na janela **Permanecer conectado?**, marque a caixa de seleção **Não mostrar isso novamente** e depois selecione **Sim**.

14. Na Caixa de entrada de Lynne, verifique se ela recebeu o email de Holly Dickson com a linha de assunto: **Teste da Política DLP 1**. Selecione a mensagem para verificar se o conteúdo que contém o endereço IP não foi removido. 

15. Deixe a guia do Outlook aberta no navegador Edge para a próxima tarefa.

16. Volte para **LON-CL1**.

    
### Tarefa 2 – Testar a segunda regra da política DLP

No exercício anterior, você criou uma política DLP personalizada que pesquisa nos emails informações confidenciais relacionadas a endereços IP em seu locatário Adatum. Essa política incluía duas regras: uma que verificava emails contendo um único endereço IP e outra que verificava emails contendo dois ou mais endereços IP. 
    
Nesta tarefa, você enviará um email de Holly Dickson para Lynne Robbins que testará a segunda regra (vários endereços IP). Quando essa regra for disparada, uma dica de política de email será exibida na caixa de correio do Outlook do remetente que informa ao remetente que o email contém dados confidenciais. O email será bloqueado, mas o remetente pode substituir o email bloqueado e permitir que ele seja enviado.  

1. No LON-CL1, no navegador Edge, você deve continuar conectado no Microsoft 365 como **Holly Dickson**. 
    
2. Agora você enviará uma segunda mensagem de Holly para Lynne que contém vários endereços IP. Repita o processo como antes para criar um email para Lynne Robbins com as seguintes informações: 

    - Adicione um assunto: **Teste da política DLP 2**

    - Área de mensagem: **Oi, Lynne. Vou testar os endereços IP 192.168.0.1 e 172.16.0.1**

    **Observação:** ao redigir este email com dados confidenciais (neste caso, vários endereços IP), ele acionará a política de endereço IP que você criou anteriormente e, especificamente, a regra de vários endereços IP. Dessa forma, uma **Dica de política** será exibida indicando que a mensagem de email viola uma política organizacional. Você ignorará essa dica de política e enviará o email para testar o restante da política DLP, o que bloqueará o email. Depois de testar o bloqueio de email, você substituirá o bloqueio inserindo uma justificativa comercial para enviar esses dados confidenciais e, em seguida, tentará enviar o email novamente.

3. Depois que a dica de política for exibida, selecione **Enviar**. Você receberá imediatamente uma caixa de diálogo **Enviar bloqueio** que indica que a mensagem inclui um ou mais destinatários sem autorização para receber informações confidenciais. Selecione **OK**. <br/>

    **Dica:** normalmente, você substituiria o bloco antes de enviá-lo, mas, neste caso, queríamos que você testasse o bloco para ver como ele funciona. Nas próximas etapas, você substituirá o bloqueio e tentará reenviar o email.

4. Selecione a pasta **Itens enviados** de Holly para verificar se o email não foi enviado.

5. Selecione a pasta **Caixa de entrada** de Holly. Observe que a mensagem de email não é mais exibida. Selecione a pasta **Rascunhos** de Holly, que contém uma cópia do email. Selecione o email.

6. Para enviar este email, você deve substituir o bloqueio ANTES de clicar no botão o **Enviar**. Para substituir o bloqueio, na dica de política que aparece na parte superior da mensagem, clique em **Mostrar detalhes**.

7. Na mensagem de detalhes exibida na dica de política, clique em **Substituir**.

8. Na caixa de diálogo exibida, a opção **Tenho uma justificativa comercial** é selecionada por padrão. Deixe esta opção selecionada e digite **Lynne deve saber dos endereços IP que estou testando** no campo **Digite a explicação aqui**. Selecione **Substituir**. <br/>

    Observe como a mensagem de dica de política foi alterada para indicar que você optou por enviar a mensagem, mesmo que ela pareça conter informações confidenciais.

9. Selecione a pasta **Itens enviados** de Holly para verificar se o email foi enviado.

10. Selecione a pasta **Caixa de entrada** de Holly. Holly receberá um email do **Microsoft Outlook** com o assunto: **Notificação: Teste da Política DLP 2**. Selecione este email e revise o conteúdo.
    
11. Alterne para **LON-CL2**. 

12. Você ainda deve estar conectado ao **Outlook na Web** na VM LON-CL2 como **Lynne Robbins**. No navegador **Edge**, a caixa de correio de Lynne ainda estará aberta no **Outlook na Web** da última vez que você a usou na tarefa anterior.

13. Na Caixa de Entrada de Lynne, verifique se ela recebeu o email de Holly Dickson que tem a linha de assunto: **Teste da Política DLP 2**. Selecione a mensagem para verificar se o conteúdo que contém os endereços IP não foi removido. 

14. Deixe a guia do Outlook aberta no navegador Edge para a próxima tarefa.

15. Volte para **LON-CL1**.

    
# Fim do laboratório 3
