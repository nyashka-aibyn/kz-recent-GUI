# Rental CRUD GUI

PostgreSQL дерекқорымен жұмыс істейтін Java Swing қосымшасы. Жоба жылжымайтын мүлікті жалға беру жүйесінің негізгі деректерін басқаруға арналған.

## Мүмкіндіктері

- Меншік иелерін басқару (CRUD)
- Жылжымайтын мүлік нысандарын басқару
- Жалға алушыларды басқару
- Жалға беру келісімшарттарын басқару
- PostgreSQL дерекқорымен байланыс
- Java Swing интерфейсі және FlatLaf дизайны

## Қолданылатын технологиялар

- Java 17+
- Maven
- PostgreSQL
- JDBC
- Swing
- FlatLaf

## Қажетті бағдарламалар

1. JDK 17 немесе одан жоғары нұсқа.
2. PostgreSQL.
3. Maven (немесе IntelliJ IDEA ішіндегі Maven қолдауы).

## Орнату және іске қосу

### 1. Репозиторийді жүктеу

```bash
git clone https://github.com/USERNAME/REPOSITORY.git
cd 2-rental-crud-gui
```

`USERNAME/REPOSITORY` орнына өз GitHub аккаунтыңыз бен репозиторий атауын жазыңыз.

### 2. Дерекқорды дайындау

PostgreSQL серверін іске қосыңыз. Егер серверіңіз `5433` портында жұмыс істесе, төмендегі URL өзгеріссіз қалады.

Алдымен PostgreSQL ішінде `rental_db` дерекқорын жасаңыз:

```sql
CREATE DATABASE rental_db;
```

Содан кейін `sql/schema.sql` файлын `rental_db` дерекқорына қосылып орындаңыз.

**Маңызды:** `schema.sql` скриптінің басында `DROP TABLE IF EXISTS` командалары бар. Оны орындау бұрыннан бар `contracts`, `properties`, `tenants`, `owners` кестелерін және олардың ішіндегі деректерді жояды. Жаңа/тест дерекқорында ғана орындаңыз.

### 3. Қосылу параметрлерін орнату

Қосымша құпиясөзді GitHub-қа сақтамайды. PostgreSQL параметрлері орта айнымалылары арқылы беріледі:

- `RENTAL_DB_URL` — әдепкі мәні `jdbc:postgresql://localhost:5433/rental_db`
- `RENTAL_DB_USER` — әдепкі мәні `postgres`
- `RENTAL_DB_PASSWORD` — PostgreSQL құпиясөзі (міндетті)

**Windows PowerShell** ішінде іске қоспас бұрын:

```powershell
$env:RENTAL_DB_URL = "jdbc:postgresql://localhost:5433/rental_db"
$env:RENTAL_DB_USER = "postgres"
$env:RENTAL_DB_PASSWORD = "YOUR_POSTGRES_PASSWORD"
```

`YOUR_POSTGRES_PASSWORD` орнына өз құпиясөзіңізді енгізіңіз. Оны кодқа немесе GitHub репозиторийіне жазбаңыз.

### 4. Maven арқылы іске қосу

```bash
mvn clean compile
mvn exec:java -Dexec.mainClass="kz.rental.Main"
```

Егер `exec:java` командасы Maven-де қолжетімсіз болса, IntelliJ IDEA-да жобаны ашып, Maven тәуелділіктерін жүктеңіз де, `kz.rental.Main` класын іске қосыңыз.

## Жоба құрылымы

```text
2-rental-crud-gui/
├── pom.xml
├── README.md
├── .gitignore
├── sql/
│   └── schema.sql
└── src/
    └── main/
        └── java/
            └── kz/rental/
                ├── Main.java
                ├── Dashboard.java
                ├── DBConnection.java
                ├── Owner.java
                ├── OwnerDAO.java
                ├── OwnerPanel.java
                ├── Property.java
                ├── PropertyDAO.java
                ├── PropertyPanel.java
                ├── Tenant.java
                ├── TenantDAO.java
                ├── TenantPanel.java
                ├── Contract.java
                ├── ContractDAO.java
                └── ContractPanel.java
```

## GitHub-қа жүктеу

Git Bash немесе терминалда жоба бумасының ішінде:

```bash
git init
git add .
git commit -m "Initial commit: Rental CRUD GUI"
git branch -M main
git remote add origin https://github.com/USERNAME/REPOSITORY.git
git push -u origin main
```

Егер GitHub-та репозиторийді алдын ала бос күйде ашсаңыз, `USERNAME/REPOSITORY` мәндерін өз репозиторийіңізге ауыстырыңыз.

## Ескерту

Бұл оқу жобасы. Дерекқорға қосылу параметрлері әр компьютерде жеке орнатылады. Нақты парольдер мен басқа құпия деректерді репозиторийге қоспаңыз.
