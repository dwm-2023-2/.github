# DWM - 2023.2

Grupo da disciplina de Desenvolvimento WebMobile - Turma B do curso Ciência da Computação da Universidade Federal do Tocantins.

**Projeto:** Diário Online

## Requisitos do Sistema

| Nº | Requisito | Descrição |
|---|---|---|
| 1 | Registro e Autenticação | Os usuários devem se registrar e criar uma conta. |
| 2 | Registro e Autenticação | Os usuários devem poder fazer login com segurança em suas contas. |
| 3 | Registro e Autenticação | Recuperação de senha deve estar disponível para usuários que esqueceram suas senhas. |
| 4 | Criação de Diário | Os usuários podem criar múltiplos diários. |
| 5 | Criação de Diário | Cada diário deve ter um nome e uma descrição opcionais. |
| 6 | Criação de Diário | Os diários podem ser definidos como públicos, privados ou compartilhados com outros usuários. |
| 7 | Criação de Diário | Os diários podem ser editados ou excluídos pelo proprietário. |
| 8 | Registros Diários | Os usuários podem criar registros diários. |
| 9 | Registros Diários | Cada registro deve incluir um título, data e conteúdo de texto. |
| 10 | Registros Diários | Os usuários podem anexar imagens, vídeos ou outros tipos de mídia aos registros. |
| 11 | Registros Diários | Os registros podem ser editados ou excluídos pelo autor. |
| 12 | Registros Diários | Os registros podem ser classificados por data e pesquisados por palavras-chave. |
| 13 | Privacidade e Compartilhamento | Os usuários podem definir as configurações de privacidade de cada registro, escolhendo entre público, privado ou compartilhado com contatos específicos. |
| 14 | Privacidade e Compartilhamento | Os registros compartilhados podem ser visualizados por usuários autorizados. |
| 15 | Privacidade e Compartilhamento | A plataforma deve garantir a segurança dos dados e a privacidade dos usuários. |
| 16 | Notificações | Os usuários podem configurar lembretes para escrever em seus diários diariamente ou em intervalos personalizados. |
| 17 | Notificações | Os lembretes podem ser enviados por e-mail ou notificações push. |
| 18 | Acesso Multiplataforma | A plataforma deve ser acessível por meio de um site responsivo. |
| 19 | Acesso Multiplataforma | Deve ser desenvolvida uma versão do aplicativo móvel para sistemas iOS e Android. |

## Entidades e Atributos

    Usuário
        Atributos:
            ID (Chave Primária)
            Nome (Texto)
            Email (Texto)
            Senha (Texto)
        Relacionamento: Um usuário pode criar múltiplos diários.

    Diário
        Atributos:
            ID (Chave Primária)
            Nome (Texto)
            Descrição (Texto)
            Privacidade (Enum: Público, Privado, Compartilhado)
            Proprietário (Chave Estrangeira: ID do Usuário)
        Relacionamento:
            Um diário pertence a um único usuário.
            Um diário pode conter múltiplos registros diários.

    Registro Diário
        Atributos:
            ID (Chave Primária)
            Título (Texto)
            Data (Data/Hora)
            Conteúdo (Texto)
            Tipo de Mídia (Enum: Texto, Imagem, Vídeo, Outro)
            Arquivo de Mídia (Binário, para armazenar imagens, vídeos, etc.)
            Privacidade (Enum: Público, Privado, Compartilhado)
            Autor (Chave Estrangeira: ID do Usuário)
            Diário Associado (Chave Estrangeira: ID do Diário)
        Relacionamento:
            Um registro diário pertence a um único diário.
            Um registro diário é escrito por um único usuário.

    Compartilhamento
        Atributos:
            ID (Chave Primária)
            Tipo de Compartilhamento (Enum: Usuário Específico, Grupo)
            Usuário Compartilhado (Chave Estrangeira: ID do Usuário)
            Diário Compartilhado (Chave Estrangeira: ID do Diário)
        Relacionamento:
            Um compartilhamento pode ser de um diário com um usuário específico ou com um grupo de usuários.