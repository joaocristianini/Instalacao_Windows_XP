# Etapa 1: Planejamento e Preparação no VirtualBox

## 🎯 Objetivo
Configurar a máquina virtual no Oracle VM VirtualBox de forma compatível com a arquitetura do Windows XP, mitigando erros de controladora e otimizando o boot.

---

## 🛠️ Materiais Disponibilizados no Laboratório
*   Arquivo de imagem ISO: `Windows_XP_Prof_SP3_BR.iso`
*   Software Oracle VM VirtualBox (Versão 6.x ou 7.x) instalado.

---

## 📑 Roteiro de Execução

1.  **Criação da Máquina Virtual (VM) no VirtualBox:**
    *   Abra o VirtualBox e clique no botão **Novo** (ícone de estrela azul).
    *   **Nome:** Digite `Lab-WinXP-SeuNome`.
    *   **Tipo:** Selecione `Microsoft Windows`.
    *   **Versão:** Selecione obrigatoriamente `Windows XP (32-bit)`. *(Nota: Isso configura automaticamente perfis de hardware compatíveis).*
2.  **Dimensionamento de Recursos:**
    *   **Memória RAM:** Aloque **512 MB** (Não ultrapasse 1024 MB para evitar instabilidades com o instalador clássico).
    *   **Disco Rígido:** Selecione `Criar um novo disco rígido virtual agora`. Escolha o tipo **VDI (VirtualBox Disk Image)** e marque como **Dinamicamente Alocado**. Defina o tamanho como **20 GB**.
3.  **Configuração de Armazenamento e Ajuste de Controladora:**
    *   Com a VM selecionada, clique em **Configurações** (ícone de engrenagem) e vá até a aba **Armazenamento**.
    *   Por padrão, o VirtualBox cria uma controladora SATA. O Windows XP nativo não possui o driver `AHCI/SATA`.
    *   **Ação Obrigatória:** Clique com o botão direito sobre a controladora SATA e selecione `Remover Controladora`.
    *   Clique no ícone de adicionar nova controladora (canto inferior) e selecione **Adicionar Controladora IDE**.
    *   Na Controladora IDE recém-criada, adicione o disco rígido virtual (`.vdi`) e, no canal secundário, monte a ISO do Windows XP clicando no ícone do CD azul e escolhendo o arquivo `Windows_XP_Prof_SP3_BR.iso`.
4.  **Ordem de Inicialização (Boot):**
    *   Acesse a aba **Sistema** -> **Placa-mãe**. Certifique-se de que **Óptico** esteja acima de **Disco Rígido** na lista de *Ordem de Boot*.

---

## 📝 Entregáveis desta Etapa

### 📸 [EVIDÊNCIA]
*Insira aqui uma captura de tela da aba "Armazenamento" do VirtualBox, mostrando a árvore de dispositivos com a Controladora IDE, o arquivo VDI e a ISO do XP montada.*

### ❓ [QUESTÃO 1]
O VirtualBox permite o uso de controladoras do tipo SATA, IDE, SCSI e SAS. Por que para sistemas operacionais modernos (como Windows 11) a controladora SATA/NVMe é o padrão, enquanto para o Windows XP fomos obrigados a criar manualmente uma controladora IDE?

**Sua Resposta:**
> Os sistemas operacionais modernos, como o Windows 11, utilizam SATA ou NVMe como padrão porque essas tecnologias são mais rápidas, eficientes e possuem suporte nativo aos hardwares atuais, especialmente SSDs. Elas oferecem melhor desempenho e maior velocidade de transferência de dados.

Já o Windows XP é um sistema antigo, criado em uma época em que o padrão mais utilizado era o IDE. Por isso, ele não possui drivers nativos para reconhecer automaticamente controladoras SATA modernas no Oracle VM VirtualBox. Assim, foi necessário criar manualmente uma controladora IDE para que o sistema detectasse o disco rígido corretamente durante a instalação.

---
[⬅️ Voltar para o Sumário](../README.md) | [Ir para a Etapa 2 ➡️](02-tarefa-instalacao.md)
