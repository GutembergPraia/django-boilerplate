# 🇧🇷 Estados e Cidades do Brasil no Django

Este guia mostra como configurar modelos para estados e cidades do Brasil e carregar dados iniciais utilizando fixtures no Django.

---

## 1. Criar o app `utils`

Se ainda não existir:

```bash
python manage.py startapp utils
```

## 2. Criar os modelos `State` e `City`

No arquivo `utils/models.py`, adicione:
```bash
class State(models.Model):
    name = models.CharField(max_length=100, verbose_name="Nome do Estado")
    abbreviation = models.CharField(max_length=2, unique=True, verbose_name="UF")

    class Meta:
        verbose_name = "Estado"
        verbose_name_plural = "Estados"
        ordering = ['name']

    def __str__(self):
        return f"{self.name} ({self.abbreviation})"


class City(models.Model):
    name = models.CharField(max_length=100, verbose_name="Nome da Cidade")
    state = models.ForeignKey(State, on_delete=models.CASCADE, related_name='cities', verbose_name="Estado")

    class Meta:
        verbose_name = "Cidade"
        verbose_name_plural = "Cidades"
        ordering = ['name']

    def __str__(self):
        return f"{self.name} - {self.state.abbreviation}"

```

## 3. Criar e aplicar migrações

```bash
python manage.py makemigrations utils
python manage.py migrate
```

## 4. Adicionar a fixture com dados de estados e cidades

Coloque o arquivo `initial_brazil_locations.json` em:
```bash
utils/fixtures/initial_brazil_locations.json
```
Caso a pasta `fixtures` não exista, crie-a:
```bash
mkdir -p utils/fixtures
```

## 5. Carregar os dados

Execute:
```bash
python manage.py loaddata utils/fixtures/initial_brazil_locations.json
```
