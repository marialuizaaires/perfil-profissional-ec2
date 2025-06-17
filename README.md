# Deploy de Perfil Profissional na AWS EC2

Este projeto demonstra a criação e configuração de uma instância EC2 na AWS para hospedar uma página web com meu perfil profissional. Abaixo estão todas as etapas e comandos utilizados.

---

## Objetivo

Publicar uma página HTML estática com informações profissionais utilizando uma instância EC2 (Ubuntu) na AWS e um servidor web simples.

---

## Link da Instância (Acesso Público)

[http://3.145.201.159/](http://3.145.201.159/)

---

## Estrutura da Página

A página contém:
- Foto de perfil
- Nome completo
- Experiências profissionais
- Formação acadêmica
- Tecnologias dominadas
- Links para GitHub e LinkedIn
- Estilo visual com CSS

---

## Etapas Realizadas

### 1. Criação da Instância EC2
- Sistema operacional: Ubuntu Server
- Tipo de instância: t2.micro (elegível para o Free Tier)
- Par de chaves: `perfpro.pem` (baixado e guardado localmente)
- Regras de Segurança:
  - Porta 22 (SSH) — Acesso remoto
  - Porta 80 (HTTP) — Para acessar o site via navegador
  - Porta 8080 (opcional)

---

### 2. Acesso via SSH

```bash
chmod 400 ~/Downloads/perfpro.pem
ssh -i ~/Downloads/perfpro.pem ubuntu@3.145.201.159
```

---

### 3. Configuração do Servidor Web

#### Dentro da EC2:

```bash
sudo apt update
sudo apt install python3 -y
mkdir meu-perfil
cd meu-perfil
```

---

### 4. Transferência dos Arquivos para a Instância

#### Do computador local para a EC2:

```bash
scp -i ~/Downloads/perfpro.pem ~/Downloads/meu-perfil/index.html ~/Downloads/meu-perfil/style.css ~/Downloads/meu-perfil/foto.jpg ubuntu@3.145.201.159:/home/ubuntu/meu-perfil
```

---

### 5. Iniciar o servidor web

#### Ainda na EC2, na pasta com os arquivos:

```bash
cd ~/meu-perfil
sudo python3 -m http.server 80
```

---

## Evidências para a Apresentação

- Link público acessível: [http://3.145.201.159/](http://3.145.201.159/)
- Comando rodando o servidor web: `python3 -m http.server 80`
- Arquivos hospedados:
  - `index.html`
  - `style.css`
  - `foto.jpg`
- Captura de tela do navegador com IP público no topo

  <img width="400" alt="image" src="https://github.com/user-attachments/assets/8d3fe60c-c13a-4fa6-b9af-975aad049df8" />
- Captura de tela do terminal com upload (`scp`) e servidor iniciado
  
<img width="700" alt="image" src="https://github.com/user-attachments/assets/ecdb0750-01e0-4396-8a06-e5f8d04dd55d" />
<br><br>
<img width="400" alt="image" src="https://github.com/user-attachments/assets/f158ba69-6b08-406f-b3d2-d117d81a0427" />


