# Progetto-NETMED
Progetto di TESI
NetflixTeleMedicina/
├── server.js                # Entry point Express
├── package.json             # Dipendenze npm + script (start, test)
├── package-lock.json        # Versioni bloccate delle dipendenze
├── Dockerfile               # Build image dell'app
├── docker-compose.yml       # Orchestrazione app + db
├── .env.example             # Template delle variabili d'ambiente
├── .gitignore
├── .dockerignore
│
├── config/                  # Configurazioni condivise
│   └── security.js          # Gestione centralizzata di JWT_SECRET
│
├── middleware/              # Middleware Express
│   ├── authMiddleware.js    # Verifica JWT su rotte protette
│   ├── creatorMiddleware.js # Blocca chi non e' creator
│   └── rateLimit.js         # Anti brute-force su login
│
├── routes/                  # Rotte REST divise per ruolo
│   ├── auth.js              # /register, /login
│   ├── userRoutes.js        # API utente comune
│   ├── creatorRoutes.js     # API riservate ai creator
│   └── adminRoutes.js       # API riservate agli admin
│
├── services/                # Logica di dominio riusabile
│   ├── email.js             # Invio email di conferma
│   └── passwordPolicy.js    # Regole di robustezza password
│
├── db/                      # Accesso al database
│   ├── db.js                # Pool di connessione Postgres
│   └── notifications.js     # Helper best-effort per creare notifiche
│
├── db-init/                 # SQL eseguito al primo avvio del container
│   └── 01_schema.sql        # Schema (tabelle, indici, CHECK, UNIQUE)
│
├── scripts/                 # Script utility standalone
│   ├── createAdmin.js       # Crea un utente admin da CLI
│   └── init-db.js           # Popola il DB con dati di esempio
│
├── test/                    # Test automatici (Mocha)
│   ├── helpers.js           # Utility riusate dai test
│   ├── test-admin-api.js
│   ├── test-creator-api.js
│   └── test-utente-api.js
│
└── public/                  # File serviti al browser
    ├── *.html               # Pagine (index, home, login, ecc.)
    ├── css/                 # Fogli di stile
    │   ├── admin/           #   -> stili pannello admin
    │   ├── user/            #   -> stili pagine utente
    │   └── *.css            #   -> stili condivisi (footer, responsive)
    ├── js/                  # JavaScript client
    │   ├── admin/           #   -> logica pannello admin
    │   ├── user/            #   -> logica pagine utente
    │   └── *.js             #   -> script condivisi (i18n, cookie)
    └── img/                 # Immagini (loghi, favicon, hero)
