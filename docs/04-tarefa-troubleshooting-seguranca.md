# Etapa 4: Troubleshooting e Redes no VirtualBox

## 🎯 Objetivo
Solucionar travamentos comuns do VirtualBox ao lidar com sistemas legados e mitigar riscos de segurança através do isolamento de placas de rede virtuais.

---

## 📑 Roteiro de Execução

1.  **Troubleshooting de Integração (Se necessário):**
    *   Se o mouse travar ou sumir após a instalação, vá nas configurações da VM no VirtualBox, aba **Sistema** -> **Dispositivo de Apontamento** e mude de `Multi-touch Tablet` para `Mouse PS/2`.
2.  **Configuração de Rede Segura (Isolamento de Vulnerabilidades):**
    *   O Windows XP é vulnerável a ataques modernos de rede distribuída (como o exploit *EternalBlue* / *WannaCry*).
    *   Abra as configurações da VM no VirtualBox com ela desligada. Vá na aba **Rede**.
    *   No campo **Conectado a:** altere a opção padrão `NAT` para **Não Conectado** ou **Rede Interna (Internal Network)**.
    *   Isso garante que o sistema compartilhe arquivos com outras VMs do laboratório (se necessário), mas fique totalmente blindado e invisível contra varreduras e ataques vindos da Internet real.

---

## 📝 Entregáveis desta Etapa

### 📸 [EVIDÊNCIA]
*Insira uma captura de tela da aba "Rede" do painel de controle do VirtualBox da sua VM demonstrando a modificação e isolamento do adaptador de rede para o modo seguro.*
<img width="785" height="497" alt="image" src="https://github.com/user-attachments/assets/719c8a57-f51d-48c2-8f77-01d392c6d7f7" />

### ❓ [QUESTÃO 4]
Se mantivéssemos o adaptador de rede da máquina virtual do Windows XP configurado no modo "Placa em modo Bridge (Bridged Adapter)" conectada à rede Wi-Fi/cabeada pública da instituição, quais seriam as consequências imediatas em termos de segurança cibernética para o laboratório e para a VM?

**Sua Resposta:**
> Ao configurar a máquina virtual no modo Bridged, você faz com que ela se comporte como um dispositivo físico independente conectado diretamente à rede da instituição, possuindo seu próprio endereço IP na mesma sub-rede que os outros computadores do laboratório.

A consequência imediata para a VM do Windows XP é a exposição total e direta a ataques. Por ser um sistema operacional antigo e sem atualizações de segurança, o Windows XP possui inúmeras vulnerabilidades críticas, como as que permitem a execução remota de código (ex: EternalBlue). Sem o "escudo" do NAT fornecido pelo software de virtualização, qualquer agente mal-intencionado ou malware presente na rede pública pode escanear e invadir a VM em questão de minutos, explorando portas abertas que não possuem proteção.

Para o laboratório, a VM se torna um "ponto de apoio" ou "ponte" para um ataque de movimentação lateral. Se a VM for comprometida (o que é extremamente provável no Windows XP exposto), o invasor pode utilizá-la para farejar o tráfego da rede da instituição (sniffing), tentar infectar outras máquinas modernas do laboratório através da rede local ou realizar ataques de negação de serviço (DoS) usando a infraestrutura da instituição. Em suma, você remove a barreira de isolamento, transformando uma ferramenta de estudo em uma ameaça ativa e vulnerável dentro do perímetro de segurança da rede pública.

---
### 🏁 FIM DA ATIVIDADE
Com todas as seções preenchidas e imagens anexadas à pasta `/assets` do seu repositório local, execute os comandos do Git para registrar e subir sua atividade:

```bash
git add .
git commit -m "feat: conclusao do laboratorio de instalacao do winxp no virtualbox"
git push origin main
