# CreateUrlLambda - Encurtador de URL Serverless  

## ✨ Visão Geral  
CreateUrlLambda é um encurtador de URLs baseado em **AWS Lambda**, oferecendo uma solução serverless escalável e eficiente para transformar URLs longas em links curtos e compartilháveis. Utilizando serviços como **Amazon API Gateway e S3**, este projeto elimina a necessidade de servidores tradicionais e reduz os custos de infraestrutura.  

## 🛠️ Funcionalidades  
- **Geração de URLs curtas** para facilitar o compartilhamento.  
- **Armazenamento persistente** via **Amazon S3** para garantir disponibilidade e confiabilidade.  
- **Expiração configurável**, permitindo URLs temporárias.  
- **Escalabilidade** automática sem necessidade de gestão manual de servidores.  
- **Segurança aprimorada** com controle de acesso e validação de URLs.  
- **Integração com API Gateway** para acesso fácil via HTTP.  

## 📝 Arquitetura  
A aplicação é baseada em uma arquitetura **serverless** e utiliza os seguintes serviços da AWS:

- **AWS Lambda**: Processamento de requisições sem servidores.  
- **Amazon API Gateway**: Exposição dos endpoints HTTP.  
- **Amazon S3**: Armazenamento dos mapeamentos entre URLs longas e curtas.  
- **AWS IAM**: Controle de permissões e segurança.  

## 📁 Estrutura do Projeto  
```
CreateUrlLambda/
├── src/main/java/com/matheusmaciel/createUrlShortener/
│   ├── Main.java                 # Handler do AWS Lambda
│   ├── UrlData.java              # Modelo de dados das URLs
│
├── pom.xml                       # Configuração do Maven
├── README.md                     # Documentação do projeto
└── .gitignore                    # Arquivo de exclusão do Git
```

## 🛠️ Requisitos  
- **Java 21+**  
- **Maven**  
- **AWS CLI** configurado com permissões adequadas  
- **Conta AWS** com acesso a Lambda, API Gateway e S3  

## 🛠️ Instalação e Deploy  
### 1. Clonar o Repositório  
```bash
git clone https://github.com/srmatheusmaciel/CreateUrlLambda.git
cd CreateUrlLambda
```

### 2. Compilar o Projeto  
```bash
mvn clean package
```



### 4. Configurar API Gateway  
- Criar uma API REST no **AWS API Gateway**  
- Definir os recursos e métodos HTTP  
- Integrar a API ao Lambda  
- Implantar para um estágio

### 5. Configurar Amazon S3  
- Criar um **bucket** para armazenar os mapeamentos de URLs.  
- Garantir que o Lambda tenha permissão para acessar o bucket.

## 📊 Endpoints da API  
### Criar uma URL Encurtada  
**Requisição:**  
```http
POST /url
Content-Type: application/json

{
  "originalUrl": "https://example.com/uma/url/muito/longa",
  "expirationTime": "3600"
}
```

**Resposta:**  
```json
{
  "shortUrl": "https://short.domain/abc123",
  "originalUrl": "https://example.com/uma/url/muito/longa",
  "expiresIn": "3600"
}
```

### Acessar uma URL Encurtada  
**Requisição:**  
```http
GET /{shortUrlId}
```

**Resposta:**  
- Redirecionamento **HTTP 302** para a URL original.

## 🔒 Configuração  
O comportamento do Lambda pode ser ajustado via variáveis de ambiente:  
- `S3_BUCKET_NAME`: Nome do bucket para armazenamento das URLs.  
- `URL_EXPIRATION`: Tempo padrão de expiração das URLs curtas.  

## 🔍 Monitoramento e Logs  
- **AWS CloudWatch** para logs automáticos das execuções do Lambda.  
- **Métricas do CloudWatch** para acompanhar:
  - Número de URLs geradas.
  - Quantidade de acessos aos links encurtados.
  - Taxa de erro e latência da API.

## 🚫 Segurança  
- **Validação de entrada** para evitar URLs maliciosas.  
- **Controle de acesso via IAM** para restringir permissões do Lambda.  


## 👥 Contribuição  
1. Faça um **fork** do repositório.  
2. Crie um branch (`git checkout -b feature/minha-feature`).  
3. Faça as alterações e commit (`git commit -m 'Nova feature'`).  
4. Envie para o branch (`git push origin feature/minha-feature`).  
5. Abra um **Pull Request** para revisão.

## 📚 Licença  
Este projeto está licenciado sob a **MIT License**. Consulte o arquivo `LICENSE` para mais detalhes.  

## 👤 Autor  
- **Matheus Maciel** - [GitHub](https://github.com/srmatheusmaciel)  

---  
Desenvolvido com ❤️ para a comunidade!

