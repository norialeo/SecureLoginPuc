🔐 Sistema de Login Seguro - SecureLogin PUC (Spring Boot)
Aplicação web desenvolvida em Java com Spring Boot para autenticação e controle de acesso, utilizando Spring Security para login, cadastro e recuperação de senha, com páginas renderizadas via Thymeleaf e perfis de acesso (USER e ADMIN).

👥 Integrantes (Dupla)

* Integrante 1: [Leonardo Gonzaga]
* Integrante 2: [João Pedro Oliveira]

💻 Código-Fonte Completo
O projeto está organizado na seguinte estrutura padrão de pacotes do Spring Boot:

```
src/
└── main/
    ├── java/
    │   └── com/
    │       └── example/
    │           └── SecureLoginPUC/
    │               ├── application/
    │               │   └── SecureLoginPUCApplication.java
    │               ├── config/
    │               │   ├── SecurityConfig.java
    │               │   └── UserConfig.java
    │               └── controller/
    │                   └── SecureLoginController.java
    └── resources/
        ├── static/
        │   ├── css/
        │   │   ├── login.css
        │   │   ├── register.css
        │   │   └── style.css
        │   └── images/
        ├── templates/
        │   ├── login.html
        │   ├── register.html
        │   ├── recoverpassword.html
        │   ├── home.html
        │   ├── admin.html
        │   └── error.html
        └── application.properties
```

📦 Dependências Utilizadas
As dependências do projeto estão gerenciadas via Maven (pom.xml):

Java 17

Spring Boot 3.3.5

Spring Web (spring-boot-starter-web): Para criação dos endpoints e controllers da aplicação.

Spring Security (spring-boot-starter-security): Para autenticação, autorização por perfil (USER/ADMIN) e proteção das rotas.

Thymeleaf (spring-boot-starter-thymeleaf): Para renderização das páginas HTML (login, cadastro, home, admin, etc.).

Spring Boot Starter Test: Para suporte a testes unitários/integração.

🔑 Orientações para Configuração de Usuários
Observação: Esta aplicação não consome nenhuma API externa, portanto não é necessária nenhuma API Key.
Os usuários de teste são configurados no arquivo application.properties e carregados em memória (InMemoryUserDetailsManager), com a senha automaticamente criptografada via BCrypt na inicialização:

```
app.user.username=joao
app.user.password=4321
app.admin.username=admin
app.admin.password=1234
```

Para alterar as credenciais de teste, basta editar esses valores em src/main/resources/application.properties antes de subir a aplicação.

🌐 Documentação dos Endpoints

| Endpoint | Método | Descrição |
|---|---|---|
| /login | GET | Exibe a página de login |
| /login | POST | Processa a autenticação (Spring Security); redireciona para /home (USER) ou /admin (ADMIN) |
| /register | GET | Exibe a página de cadastro |
| /register | POST | Processa o cadastro e redireciona para /login |
| /recoverpassword | GET | Exibe a página de recuperação de senha |
| /recoverpassword | POST | Processa a recuperação e redireciona para /login |
| /home | GET | Página inicial do usuário autenticado (requer login) |
| /admin | GET | Área administrativa (requer perfil ADMIN) |
| /error | GET | Página exibida em caso de falha no login |
| /logout | POST | Encerra a sessão e redireciona para /login |

▶️ Instruções para Executar a Aplicação Localmente
Pré-requisitos
JDK 17 instalado e configurado nas variáveis de ambiente.

Git instalado.

IDE de sua preferência (VS Code, IntelliJ IDEA, Eclipse).

Passo a Passo
1 - Clonar o repositório: git clone https://github.com/norialeo/SecurityLogin_Puc.git

2 - Compilar e baixar dependências:
  ./mvnw clean install
  (no Windows: mvnw.cmd clean install)

3 - Executar a aplicação:
  Via Terminal: ./mvnw spring-boot:run
  (no Windows: mvnw.cmd spring-boot:run)

4 - Testar a aplicação:
Abra o navegador e acesse: http://localhost:8080/login
Utilize as credenciais padrão (joao/4321 para usuário comum ou admin/1234 para administrador) configuradas em application.properties.
