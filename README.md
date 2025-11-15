## 📖 Manual de Uso - MoveOn (Versão MVP com Navbar Centralizada e Links Redundantes Removidos)

Este manual descreve o uso e as funcionalidades implementadas no seu protótipo MoveOn, incluindo as melhorias de navegação e a estrutura da gamificação.

---

### 1. Estrutura Geral e Interface

O aplicativo foi projetado para simular um aplicativo móvel (visão de smartphone) com uma largura máxima de 480px.

| Componente | Função | Localização |
| :--- | :--- | :--- |
| **`Top Bar`** | Título da tela, ou saudação/link de Perfil na Home. | Canto superior. |
| **`Bottom Nav`** | **Novo Menu de Navegação principal e fixo.** Permite acesso rápido entre as 4 principais telas e o registro de atividade. **Está centralizado.** | Fundo da tela. |
| **`Screens`** | O conteúdo das páginas (Home, Histórico, etc.). | Área central de rolagem. |

---

### 2. Fluxo de Navegação Principal

O fluxo de login/cadastro é simulado, levando o usuário para a `Home` (Início) após a conclusão. A navegação entre as telas é realizada pela barra de navegação no rodapé (`bottom-nav`).

#### 2.1. Telas Principais (via `Bottom Nav`)

| Botão | Ícone | Tela | Ações Principais |
| :--- | :--- | :--- | :--- |
| **Início** | <i class="fas fa-home"></i> | `screen-home` | Acompanhamento do Nível, XP e Atividades Recentes. |
| **Histórico** | <i class="fas fa-history"></i> | `screen-history` | Lista de todos os treinos registrados. |
| **Registrar** | <i class="fas fa-plus"></i> (Botão Flutuante) | `screen-add-activity` | Início do formulário de registro de atividade. |
| **Ranking** | <i class="fas fa-trophy"></i> | `screen-ranking` | Visualização do Ranking Global (XP Total). |
| **Medalhas** | <i class="fas fa-medal"></i> | `screen-medals` | Visualização das Conquistas Desbloqueadas. |

---

### 3. Principais Alterações de Usabilidade (UX)

As alterações solicitadas foram implementadas para melhorar a coesão visual e funcional:

* **Centralização da Navbar:** O elemento `.bottom-nav` está agora perfeitamente centralizado na largura máxima do aplicativo (480px), garantindo consistência visual.
* **Remoção de Links "Home":** Todos os links de texto "Home" na `top-bar` das telas secundárias (`screen-history`, `screen-medals`, `screen-ranking`, `screen-profile`) foram removidos, já que a navegação principal é feita pelo ícone "Início" na barra inferior.
    * **Exceções:**
        * Em `screen-add-activity`, o link de retorno foi renomeado para **"Cancelar"**.
        * Em `screen-summary`, o link de retorno foi renomeado para **"Início"** (para confirmar o fluxo de conclusão).
        * Em `screen-activity-detail`, o link de retorno foi renomeado para **"Voltar"** (para o Histórico).

---

### 4. Funcionamento da Gamificação

A gamificação é baseada no registro de atividades, que são convertidas em Pontos de Experiência (XP).

#### 4.1. Cálculo de XP

A fórmula de XP (detalhada na tela de Resumo) é:

$$XP = (Tempo_{min} \times Fator_{Tipo} \times Fator_{Intensidade}) + Bônus_{Duração}$$

| Variável | Fatores |
| :--- | :--- |
| **$Fator_{Tipo}$** | Cardio (1.2), Funcional (1.3), Musculação (1.5), Outro (1.0). |
| **$Fator_{Intensidade}$** | Leve (1.0), Moderada (1.5), Alta (2.0). |
| **$Bônus_{Duração}$** | +10 XP se o treino for $\ge 30$ minutos. |

#### 4.2. Progressão de Nível

O nível é determinado pelo XP Total acumulado:

| Nível | XP Total Necessário |
| :--- | :--- |
| **1** | 0 XP |
| **2** | 500 XP |
| **3** | 1.500 XP |
| **4** | 3.000 XP |
| **5** | 5.000 XP |

#### 4.3. Medalhas (Conquistas)

As medalhas são desbloqueadas com base em marcos de uso:

* **Primeira Atividade:** Registrar 1 treino.
* **Hábito:** Registrar atividades em 7 dias diferentes.
* **Maratona:** Acumular 300 minutos de treino total.
* **Mil XP:** Alcançar 1000 XP total.
* **Versatilidade:** Usar 3 ou mais tipos de atividade.
* **Cardio King:** Registrar 5 treinos de Cardio.
* **Powerlifter:** Registrar 5 treinos de Musculação.
* **Alta Performance:** Registrar 5 treinos de Alta Intensidade.

---

### 5. Configuração e Inicialização

1.  **Acesso:** O código é executado em um navegador.
2.  **Início:** O aplicativo começa em `screen-onb1`.
3.  **Configuração:** Clique em **"Criar conta"** (`screen-signup`). O nome de usuário e email fornecidos serão salvos no `state` e usados nas telas `Home` e `Perfil`.
4.  **Uso:** Após o cadastro, você será direcionado para `screen-home` (Início). Use o botão central **<i class="fas fa-plus"></i>** para registrar uma nova atividade.
