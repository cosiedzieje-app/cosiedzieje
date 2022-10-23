# CoSięDzieje

## Pełna aplikacja

### Spis treści

1. [Wymagania](#wymagania)
2. [Instrukcja uruchamiania](#instrukcja-uruchamiania)

### Wymagania

- [Node.js](https://nodejs.org)
- [Yarn](https://yarnpkg.org)
- [Rustup](https://rustup.rs)
- Lokalna instancja systemu bazodanowego MySQL

### Instrukcja uruchamiania

1. Utwórz użytkownika wewnątrz systemu MySQL. Będzie nam potrzebny później.
2. Zaimportuj plik `structure.sql`, znajdujący się wewnątrz katalogu `sql`, do systemu MySQL.
3. Przyznaj uprawnienia swojemu użytkownikowi do wykonywania operacji na bazie danych. Możesz wykorzystać do tego komendę:
```
GRANT ALL PRIVILEGES ON `somsiad`.* TO '<nazwa użytkownika>'@'localhost';
FLUSH PRIVILEGES;
```
4. W głównym katalogu repozytorium utwórz plik `.env`.
5. W pliku `.env` zawrzyj zmienną `DATABASE_URL`, zawierającą link do naszej bazy danych. Przykład:
```
DATABASE_URL="mysql://nazwaużytkownika:hasło@localhost/somsiad";
```
6. Utwórz plik `Rocket.toml`
7. Wewnątrz pliku `Rocket.toml` dodaj następujące informacje:
```
[default]
secret_key = "<wartość>"
```
gdzie `<wartość>` to 256-bitowy klucz w formacie base64, który możesz wygenerować komendą `openssl rand -base64 32`
8. Uruchom program komendą `cargo run --release`.
9. Strona będzie dostępna pod adresem `http://localhost:8000`
