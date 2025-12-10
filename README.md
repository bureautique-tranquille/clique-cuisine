# clique-cuisine
site qui apprend la bureautique et la cuisine gourmande
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Clique & Cuisine - L'univers de Tony & Vaness</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #ff6b6b 100%);
            color: #333;
            line-height: 1.6;
        }

        body.dys-mode {
            font-family: 'OpenDyslexic', 'Arial', sans-serif;
            line-height: 2;
            letter-spacing: 1px;
            word-spacing: 3px;
        }

        body.dys-mode p, body.dys-mode li {
            font-size: 1.4rem;
        }

        /* Thèmes par âge */
        body.theme-petits {
            background: linear-gradient(135deg, #4299e1 0%, #48bb78 100%);
        }

        body.theme-enfants {
            background: linear-gradient(135deg, #f6ad55 0%, #fc8181 100%);
        }

        body.theme-ados {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }

        .accessibility-bar {
            background: #2d3748;
            padding: 1rem;
            text-align: center;
            position: sticky;
            top: 0;
            z-index: 1000;
            box-shadow: 0 2px 8px rgba(0,0,0,0.2);
        }

        .accessibility-buttons {
            display: flex;
            justify-content: center;
            gap: 1rem;
            flex-wrap: wrap;
        }

        .access-btn {
            background: white;
            color: #2d3748;
            border: none;
            padding: 0.8rem 1.5rem;
            border-radius: 25px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: bold;
            transition: all 0.3s ease;
        }

        .access-btn:hover {
            background: #667eea;
            color: white;
            transform: scale(1.05);
        }

        .access-btn.active {
            background: #48bb78;
            color: white;
        }

        header {
            background: white;
            padding: 2rem;
            text-align: center;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        .logo-container {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 2rem;
            margin-bottom: 1rem;
            flex-wrap: wrap;
        }

        .logo-dual {
            display: flex;
            gap: 0;
        }

        .logo-left {
            width: 100px;
            height: 100px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border-radius: 20px 0 0 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            box-shadow: -4px 4px 12px rgba(0,0,0,0.2);
        }

        .logo-right {
            width: 100px;
            height: 100px;
            background: linear-gradient(135deg, #ff6b6b 0%, #feca57 100%);
            border-radius: 0 20px 20px 0;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            box-shadow: 4px 4px 12px rgba(0,0,0,0.2);
        }

        h1 {
            font-size: 3rem;
            margin-bottom: 0.5rem;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
            font-weight: bold;
        }

        .brand-name {
            background: linear-gradient(90deg, #667eea 0%, #ff6b6b 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .subtitle {
            color: #666;
            font-size: 1.4rem;
            font-weight: normal;
        }

        nav {
            background: #2d3748;
            padding: 1rem;
            display: flex;
            justify-content: center;
            gap: 1rem;
            flex-wrap: wrap;
            box-shadow: 0 2px 8px rgba(0,0,0,0.2);
        }

        .nav-btn {
            background: white;
            color: #2d3748;
            border: none;
            padding: 1rem 2rem;
            border-radius: 25px;
            cursor: pointer;
            font-size: 1.1rem;
            font-weight: bold;
            transition: all 0.3s ease;
        }

        .nav-btn:hover {
            background: #ff6b6b;
            color: white;
            transform: scale(1.05);
        }

        .nav-btn.active {
            background: linear-gradient(90deg, #667eea 0%, #ff6b6b 100%);
            color: white;
        }

        .container {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 0 1rem;
        }

        .section {
            display: none;
        }

        .section.active {
            display: block;
        }

        /* Modal de sélection d'âge */
        .age-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.8);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 10000;
        }

        .age-modal.hidden {
            display: none;
        }

        .age-modal-content {
            background: white;
            padding: 3rem;
            border-radius: 30px;
            max-width: 900px;
            text-align: center;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
        }

        .age-modal h2 {
            font-size: 2.5rem;
            margin-bottom: 2rem;
            color: #667eea;
        }

        .age-options {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .age-card {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 2rem;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s ease;
            border: 4px solid transparent;
        }

        .age-card:hover {
            transform: scale(1.05);
            border-color: #ffd700;
        }

        .age-card.petits {
            background: linear-gradient(135deg, #4299e1 0%, #48bb78 100%);
        }

        .age-card.enfants {
            background: linear-gradient(135deg, #f6ad55 0%, #fc8181 100%);
        }

        .age-card.ados {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }

        .age-card.adultes {
            background: linear-gradient(135deg, #2d3748 0%, #4a5568 100%);
        }

        .age-icon {
            font-size: 4rem;
            margin-bottom: 1rem;
        }

        .age-card h3 {
            font-size: 1.8rem;
            margin-bottom: 0.5rem;
        }

        .intro {
            background: white;
            padding: 2rem;
            border-radius: 20px;
            margin-bottom: 2rem;
            box-shadow: 0 8px 16px rgba(0,0,0,0.2);
            text-align: center;
        }

        .intro p {
            font-size: 1.2rem;
            color: #555;
        }

        body.dys-mode .intro {
            background: #fffacd;
        }

        .hero {
            background: white;
            padding: 3rem;
            border-radius: 20px;
            margin-bottom: 2rem;
            box-shadow: 0 8px 16px rgba(0,0,0,0.2);
            text-align: center;
        }

        .hero h2 {
            font-size: 2.5rem;
            margin-bottom: 1rem;
            background: linear-gradient(90deg, #667eea 0%, #ff6b6b 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .founders {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .founder-card {
            background: white;
            padding: 2rem;
            border-radius: 20px;
            box-shadow: 0 8px 16px rgba(0,0,0,0.2);
            text-align: center;
        }

        .founder-card.tony {
            border-top: 5px solid #667eea;
        }

        .founder-card.vaness {
            border-top: 5px solid #ff6b6b;
        }

        .founder-avatar {
            font-size: 5rem;
            margin-bottom: 1rem;
        }

        .cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .card {
            background: white;
            padding: 2rem;
            border-radius: 20px;
            box-shadow: 0 8px 16px rgba(0,0,0,0.2);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            cursor: pointer;
        }

        body.dys-mode .card {
            background: #f0f8ff;
            border: 3px solid #667eea;
        }

        .card:hover {
            transform: translateY(-10px);
            box-shadow: 0 12px 24px rgba(0,0,0,0.3);
        }

        .card-icon {
            font-size: 4rem;
            margin-bottom: 1rem;
            text-align: center;
        }

        .card h2 {
            color: #667eea;
            font-size: 1.8rem;
            margin-bottom: 1rem;
            text-align: center;
        }

        .card p {
            color: #666;
            font-size: 1.1rem;
            text-align: center;
        }

        body.dys-mode .card p {
            color: #000;
        }

        /* Personnages */
        .character-box {
            background: white;
            padding: 2rem;
            border-radius: 20px;
            margin-bottom: 2rem;
            box-shadow: 0 8px 16px rgba(0,0,0,0.2);
            display: flex;
            align-items: center;
            gap: 2rem;
        }

        .character-avatar {
            font-size: 6rem;
            animation: bounce 2s infinite;
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }

        .character-speech {
            flex: 1;
            background: #f7fafc;
            padding: 1.5rem;
            border-radius: 15px;
            position: relative;
            font-size: 1.2rem;
        }

        .character-speech::before {
            content: '';
            position: absolute;
            left: -15px;
            top: 50%;
            transform: translateY(-50%);
            width: 0;
            height: 0;
            border-top: 15px solid transparent;
            border-bottom: 15px solid transparent;
            border-right: 15px solid #f7fafc;
        }

        .exercise-box {
            background: white;
            padding: 2rem;
            border-radius: 20px;
            margin-bottom: 2rem;
            box-shadow: 0 8px 16px rgba(0,0,0,0.2);
        }

        body.dys-mode .exercise-box {
            background: #fffacd;
        }

        .exercise-box h3 {
            color: #667eea;
            margin-bottom: 1rem;
            font-size: 1.8rem;
        }

        .syllable {
            display: inline-block;
            padding: 0.5rem 1rem;
            margin: 0.2rem;
            font-size: 1.8rem;
            font-weight: bold;
            border-radius: 10px;
        }

        .syllable.red {
            color: #e53e3e;
            background: #fed7d7;
        }

        .syllable.blue {
            color: #3182ce;
            background: #bee3f8;
        }

        .syllable.green {
            color: #38a169;
            background: #c6f6d5;
        }

        .game-area {
            background: #f7fafc;
            padding: 2rem;
            border-radius: 15px;
            margin: 1rem 0;
            min-height: 300px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }

        .btn {
            display: inline-block;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 1rem 2rem;
            border-radius: 50px;
            text-decoration: none;
            margin: 0.5rem;
            transition: all 0.3s ease;
            font-size: 1.2rem;
            border: none;
            cursor: pointer;
            font-weight: bold;
        }

        .btn:hover {
            transform: scale(1.05);
            box-shadow: 0 8px 16px rgba(0,0,0,0.3);
        }

        .btn-big {
            font-size: 1.5rem;
            padding: 1.5rem 3rem;
        }

        .score-display {
            background: #48bb78;
            color: white;
            padding: 1rem 2rem;
            border-radius: 50px;
            font-size: 1.5rem;
            font-weight: bold;
            text-align: center;
            margin: 1rem 0;
            display: inline-block;
        }

        .stars {
            font-size: 2.5rem;
            text-align: center;
            margin: 1rem 0;
        }

        .number-grid {
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            gap: 1rem;
            margin: 2rem 0;
            max-width: 600px;
        }

        .number-card {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 2rem;
            border-radius: 15px;
            text-align: center;
            cursor: pointer;
            transition: transform 0.2s ease;
            font-size: 2rem;
            font-weight: bold;
        }

        .number-card:hover {
            transform: scale(1.1);
        }

        .number-card.correct {
            background: linear-gradient(135deg, #48bb78 0%, #38a169 100%);
            animation: pulse 0.5s;
        }

        .number-card.disabled {
            opacity: 0.3;
            cursor: not-allowed;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.2); }
        }

        .level-card {
            background: white;
            padding: 2rem;
            border-radius: 20px;
            margin-bottom: 2rem;
            box-shadow: 0 8px 16px rgba(0,0,0,0.2);
            border-left: 8px solid #667eea;
        }

        .level-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1rem;
            flex-wrap: wrap;
            gap: 1rem;
        }

        .level-header h3 {
            color: #667eea;
            font-size: 2rem;
        }

        .level-badge {
            background: linear-gradient(135deg, #ffd700 0%, #ffed4e 100%);
            padding: 0.5rem 1.5rem;
            border-radius: 25px;
            font-weight: bold;
            font-size: 1.1rem;
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
        }

        .recipe-to-type {
            background: #f0f8ff;
            padding: 1.5rem;
            border-radius: 15px;
            margin: 1rem 0;
            border: 3px dashed #667eea;
        }

        .recipe-to-type h4 {
            color: #ff6b6b;
            margin-bottom: 1rem;
        }

        .progress-bar {
            background: #e2e8f0;
            height: 30px;
            border-radius: 15px;
            overflow: hidden;
            margin: 1rem 0;
        }

        .progress-fill {
            background: linear-gradient(90deg, #667eea 0%, #ff6b6b 100%);
            height: 100%;
            transition: width 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
        }

        footer {
            background: white;
            padding: 2rem;
            text-align: center;
            margin-top: 3rem;
            color: #666;
        }

        @media (max-width: 768px) {
            h1 {
                font-size: 2rem;
            }
            
            .nav-btn {
                padding: 0.8rem 1.2rem;
                font-size: 0.9rem;
            }

            .number-grid {
                grid-template-columns: repeat(3, 1fr);
            }

            .character-box {
                flex-direction: column;
                text-align: center;
            }

            .character-speech::before {
                display: none;
            }
        }
    </style>
</head>
<body>
    <!-- Modal de sélection d'âge -->
    <div class="age-modal" id="ageModal">
        <div class="age-modal-content">
            <h2>👋 Bienvenue ! Choisis ton univers :</h2>
            <p style="font-size: 1.2rem; margin-bottom: 2rem;">Pour une expérience personnalisée, dis-nous ton âge !</p>
            
            <div class="age-options">
                <div class="age-card petits" onclick="selectAge('petits')">
                    <div class="age-icon">🐶</div>
                    <h3>3-6 ans</h3>
                    <p>Univers Pat Patrouille</p>
                    <p style="font-size: 0.9rem; margin-top: 0.5rem;">Chase et ses amis !</p>
                </div>

                <div class="age-card enfants" onclick="selectAge('enfants')">
                    <div class="age-icon">⚡</div>
                    <h3>7-10 ans</h3>
                    <p>Univers Pokémon</p>
                    <p style="font-size: 0.9rem; margin-top: 0.5rem;">Pikachu et Évoli !</p>
                </div>

                <div class="age-card ados" onclick="selectAge('ados')">
                    <div class="age-icon">🏴‍☠️</div>
                    <h3>11-14 ans</h3>
                    <p>Univers One Piece</p>
                    <p style="font-size: 0.9rem; margin-top: 0.5rem;">Luffy et l'équipage !</p>
                </div>

                <div class="age-card adultes" onclick="selectAge('adultes')">
                    <div class="age-icon">💼</div>
                    <h3>15+ ans</h3>
                    <p>Mode Professionnel</p>
                    <p style="font-size: 0.9rem; margin-top: 0.5rem;">Design épuré</p>
                </div>
            </div>
        </div>
    </div>

    <div class="accessibility-bar">
        <div class="accessibility-buttons">
            <button class="access-btn" onclick="toggleDysMode()" id="dysBtn">
                👁️ Mode DYS
            </button>
            <button class="access-btn" onclick="increaseFontSize()">
                🔍+ Agrandir
            </button>
            <button class="access-btn" onclick="decreaseFontSize()">
                🔍- Réduire
            </button>
            <button class="access-btn" onclick="showAgeModal()">
                🎨 Changer d'univers
            </button>
        </div>
    </div>

    <header>
        <div class="logo-container">
            <div class="logo-dual">
                <div class="logo-left">💻</div>
                <div class="logo-right">🍰</div>
            </div>
            <div>
                <h1><span class="brand-name">Clique & Cuisine</span></h1>
                <p class="subtitle">L'univers de Tony & Vaness</p>
            </div>
        </div>
    </header>

    <nav>
        <button class="nav-btn active" onclick="showSection('accueil')">🏠 Accueil</button>
        <button class="nav-btn" onclick="showSection('apprendre')">📝 Apprendre en Tapant</button>
        <button class="nav-btn" onclick="showSection('dys')">🎯 Exercices DYS</button>
        <button class="nav-btn" onclick="showSection('recettes')">🍰 Recettes Vaness</button>
    </nav>

    <div class="container">
        <!-- SECTION ACCUEIL -->
        <div id="accueil" class="section active">
            <div class="hero">
                <h2>Bienvenue dans notre univers !</h2>
                <p style="font-size: 1.3rem; margin: 1rem 0;">Où l'informatique rencontre la gourmandise 🖱️✨🍰</p>
                <p style="font-size: 1.1rem; color: #666;">Apprenez la bureautique en tapant de vraies recettes ! Une méthode unique, pratique et délicieuse.</p>
            </div>

            <div class="founders">
                <div class="founder-card tony">
                    <div class="founder-avatar">👨‍💻</div>
                    <h3 style="color: #667eea; font-size: 2rem;">Tony</h3>
                    <p style="font-size: 1.1rem;">Passionné d'informatique, je rends la bureautique accessible à tous. Mon objectif : que chacun soit autonome avec son ordinateur !</p>
                </div>

                <div class="founder-card vaness">
                    <div class="founder-avatar">👩‍🍳</div>
                    <h3 style="color: #ff6b6b; font-size: 2rem;">Vaness</h3>
                    <p style="font-size: 1.1rem;">Pâtissière et cuisinière passionnée, je partage mes recettes maison et le secret de mes gourmandises françaises !</p>
                </div>
            </div>

            <div class="intro" style="margin-top: 2rem;">
                <h3 style="color: #667eea; font-size: 2rem; margin-bottom: 1rem;">🎯 Notre concept unique</h3>
                <p>Apprenez la bureautique en tapant de VRAIES recettes ! Vous progressez en informatique tout en créant votre propre livre de recettes numérique. Pratique, motivant et gourmand !</p>
            </div>

            <div class="cards">
                <div class="card" onclick="showSection('apprendre')">
                    <div class="card-icon">📝🍰</div>
                    <h2>Apprendre en Tapant</h2>
                    <p>Tapez des recettes pour apprendre le traitement de texte, la mise en forme, et créez votre livre de cuisine numérique !</p>
                </div>

                <div class="card" onclick="showSection('dys')">
                    <div class="card-icon">🎮</div>
                    <h2>Exercices DYS Gratuits</h2>
                    <p>Exercices ludiques inspirés des orthophonistes et ergothérapeutes. Pour la dyslexie et dyscalculie.</p>
                </div>

                <div class="card" onclick="showSection('recettes')">
                    <div class="card-icon">🍰</div>
                    <h2>Recettes de Vaness</h2>
                    <p>Toutes les recettes en version complète, avec photos et vidéos YouTube à venir !</p>
                </div>
            </div>
        </div>

        <!-- SECTION APPRENDRE EN TAPANT -->
        <div id="apprendre" class="section">
            <div class="intro">
                <h2 style="color: #667eea; font-size: 2.5rem;">📝 Apprendre la Bureautique en Tapant des Recettes</h2>
                <p>Une méthode révolutionnaire : apprenez en créant quelque chose d'utile ! Chaque niveau vous fait progresser tout en construisant votre livre de recettes personnel.</p>
            </div>

            <div class="level-card">
                <div class="level-header">
                    <h3>🌱 Niveau 1 : Première Recette</h3>
                    <div class="level-badge">⭐ Débutant</div>
                </div>
                <div class="progress-bar">
                    <div class="progress-fill" style="width: 0%" id="level1Progress">0%</div>
                </div>
                <p style="font-size: 1.2rem; margin: 1rem 0;"><strong>Objectif :</strong> Ouvrir un document et taper votre première recette complète</p>
                
                <div class="recipe-to-type">
                    <h4>📋 Recette à taper : Gâteau au Chocolat de Vaness</h4>
                    <p><strong>Ingrédients :</strong></p>
                    <ul>
                        <li>200g de chocolat noir</li>
                        <li>150g de beurre</li>
                        <li>150g de sucre</li>
                        <li>4 œufs</li>
                        <li>50g de farine</li>
                    </ul>
                </div>
                
                <p style="margin: 1rem 0;">✨ <strong>Ce que vous apprenez :</strong> Ouvrir un document, taper du texte, sauvegarder</p>
                <p style="margin: 1rem 0;">🏆 <strong>Récompense :</strong> Badge "Premier Chef Numérique" + Recette imprimable</p>
                <button class="btn btn-big" onclick="startLevel(1)">Commencer le Niveau 1</button>
            </div>

            <div class="level-card">
                <div class="level-header">
                    <h3>🎨 Niveau 2 : Mise en Forme</h3>
                    <div class="level-badge">⭐⭐ Intermédiaire</div>
                </div>
                <p style="font-size: 1.2rem; margin: 1rem 0;"><strong>Objectif :</strong> Embellir votre recette avec de la mise en forme</p>
                <button class="btn" onclick="startLevel(2)">Commencer le Niveau 2</button>
            </div>

            <div class="level-card">
                <div class="level-header">
                    <h3>📚 Niveau 3 : Le Livre de Recettes</h3>
                    <div class="level-badge">⭐⭐⭐ Avancé</div>
                </div>
                <p style="font-size: 1.2rem; margin: 1rem 0;"><strong>Objectif :</strong> Créer un vrai livre de recettes professionnel</p>
                <button class="btn" onclick="startLevel(3)">Commencer le Niveau 3</button>
            </div>
        </div>

        <!-- SECTION EXERCICES DYS -->
        <div id="dys" class="section">
            <div class="intro">
                <h2 style="color: #667eea; font-size: 2.5rem;">🎯 Exercices DYS avec tes héros !</h2>
                <p>Apprends avec tes personnages préférés ! Exercices inspirés des orthophonistes et ergothérapeutes.</p>
            </div
