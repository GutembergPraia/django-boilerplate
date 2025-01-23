# Django Starter Guide

## **Passo a Passo para Criar um Novo Projeto Django**

### 1. Criar o ambiente virtual

```bash
python -m venv .venv
```
## 1.1 Ativar maquina virtual
#Linux
```bash
source .venv/bin/activate  # Linux/Mac
```
#Windows
É usado para definir a política de execução de scripts apenas para o processo atual do PowerShell (ou seja, a sessão em execução). Ele altera a política temporariamente, sem impactar o sistema inteiro ou outros usuários.
```bash
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```
```bash
.venv\Scripts\activate
```

### 2. Instalar o Django

```bash
pip install django
```

### 3. Criar o projeto

```bash
django-admin startproject nome_do_projeto .
```

### 4. Criar o aplicativo

```bash
python manage.py startapp nome_do_app
```

### 5. Configurar o app no `settings.py`

No arquivo `settings.py`, adicionar o nome do app na lista `INSTALLED_APPS`:

```python
INSTALLED_APPS = [
    # outros apps padrão
    'nome_do_app',
]
```

### 6. Criar o banco de dados

```bash
python manage.py migrate
```

### 7. Criar o superusuário

```bash
python manage.py createsuperuser
```

### 8. Rodar o servidor

```bash
python manage.py runserver
```

---

## **Extras**

### Instalar bibliotecas comuns

```bash
pip install djangorestframework django-environ psycopg2-binary
```

### Configuração inicial para o PostgreSQL

No `settings.py`:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'nome_do_banco',
        'USER': 'usuario',
        'PASSWORD': 'senha',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```

### Requisitos do projeto

Gerar o arquivo `requirements.txt` para documentar as dependências:

```bash
pip freeze > requirements.txt
```

### Comandos úteis

- **Rodar as migrações:**

  ```bash
  python manage.py makemigrations
  python manage.py migrate
  ```

- **Testar o projeto:**

  ```bash
  python manage.py test
  ```

- **Limpar o cache (abrir o shell do Django):**

  ```bash
  python manage.py shell
  ```

---
