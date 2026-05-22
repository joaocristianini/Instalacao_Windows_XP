# Etapa 3: Pós-Instalação e Integração com o VirtualBox

## 🎯 Objetivo
Instalar os drivers de virtualização do pacote Guest Additions do VirtualBox para habilitar aceleração de vídeo, redimensionamento de tela automática e integração nativa do mouse.

---

## 📑 Roteiro de Execução

1.  **Instalação dos Adicionais de Convidado (VirtualBox Guest Additions):**
    *   Com a máquina virtual do Windows XP ligada e logada na área de trabalho, vá até o menu superior da janela do VirtualBox e clique em **Dispositivos** -> **Inserir Imagem de CD dos Adicionais de Convidado...**.
    *   Se a execução automática não abrir, clique no Menu Iniciar do Windows XP, abra o **Meu Computador** e dê dois cliques no drive de `CD-ROM (D:) VirtualBox Guest Additions`.
    *   O assistente de instalação será iniciado. Clique em **Next** em todas as etapas.
    *   Durante a instalação, o Windows XP exibirá janelas de aviso informando que o software que está sendo instalado "Não passou no teste de logotipo do Windows" (falta de assinatura digital retrô). Clique em **Continuar assim mesmo** em todas as notificações que surgirem.
    *   Certifique-se de que a opção de instalar suporte experimental a Direct3D/Aceleração Gráfica seja marcada se for solicitada.
    *   Ao concluir, selecione a opção `Reboot Now` e clique em **Finish** para reiniciar a VM.

2.  **Otimização Gráfica e de Desempenho:**
    *   Após o reinício, verifique se a tela da VM pode ser redimensionada livremente ou se o mouse se desloca para fora da tela da VM sem travar.
    *   Vá em `Painel de Controle` -> `Vídeo` -> `Configurações` e ajuste a resolução para pelo menos `1024x768` com qualidade de cor em `Máxima (32 bits)`.
    *   Clique com o botão direito em `Meu Computador` -> `Propriedades` -> aba `Avançado` -> Seção Desempenho clique em `Configurações` -> Escolha **Ajustar para obter um melhor desempenho** para otimizar o consumo de ciclos de CPU do sistema hospedeiro.

---

## 📝 Entregáveis desta Etapa

### 📸 [EVIDÊNCIA]
*Insira aqui uma captura de tela do Windows XP em "Modo Janela Redimensionada" ou em "Tela Cheia" dentro do VirtualBox, demonstrando que os drivers de vídeo e integração do mouse estão ativos de forma fluida.*
<img width="1919" height="1033" alt="image" src="https://github.com/user-attachments/assets/7e3de716-7ada-4d6a-b4eb-61e2ed8f3d68" />

### ❓ [QUESTÃO 3]
Quais recursos técnicos específicos passam a funcionar entre o sistema operacional real (hospedeiro) e a máquina virtual do Windows XP (convidado) após a instalação correta dos "Adicionais de Convidado" (Guest Additions)?

**Sua Resposta:**
> Após a instalação correta dos Adicionais de Convidado (Guest Additions) em uma VM com Windows XP, diversos recursos de integração técnica são ativados para otimizar a comunicação entre o hardware virtualizado e o sistema hospedeiro. O principal deles é o suporte a Drivers de Vídeo Otimizados, que permite o redimensionamento automático da janela da VM e melhora o desempenho gráfico, habilitando inclusive a aceleração 2D e 3D. Outro recurso essencial é a Integração do Ponteiro do Mouse, que elimina a necessidade de "capturar" e "liberar" o cursor manualmente, permitindo que ele flua livremente entre as telas.

Além disso, o sistema passa a suportar a Área de Transferência Compartilhada (copiar e colar textos ou arquivos) e o recurso de Arrastar e Soltar (drag-and-drop) entre as duas máquinas. No campo da conectividade, tornam-se funcionais as Pastas Compartilhadas, que permitem mapear diretórios do computador real como unidades de rede dentro do Windows XP. Por fim, ocorre a Sincronização de Horário, garantindo que o relógio da VM esteja sempre alinhado com o do hospedeiro, e a habilitação do Modo Seamless (Integração de Tela), onde as janelas do Windows XP podem flutuar diretamente na área de trabalho do seu sistema principal, como se fossem programas nativos.

---
[⬅️ Voltar para a Etapa 2](02-tarefa-instalacao.md) | [Ir para a Etapa 4 ➡️](04-tarefa-troubleshooting-seguranca.md)
