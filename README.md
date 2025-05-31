# Malvinas
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Documental: Guerra de las Malvinas</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #1a2a6c, #2c3e50, #4a235a);
            color: #f0f0f0;
            min-height: 100vh;
            padding: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        
        .container {
            max-width: 1200px;
            width: 100%;
            margin: 0 auto;
        }
        
        header {
            text-align: center;
            padding: 20px 0;
            margin-bottom: 30px;
            border-bottom: 2px solid rgba(255, 255, 255, 0.1);
        }
        
        h1 {
            font-size: 2.8rem;
            margin-bottom: 10px;
            text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
            background: linear-gradient(to right, #ff7e5f, #feb47b);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .subtitle {
            font-size: 1.2rem;
            opacity: 0.9;
            max-width: 800px;
            margin: 0 auto;
        }
        
        .documentary-container {
            display: flex;
            gap: 30px;
            margin-bottom: 40px;
            flex-wrap: wrap;
        }
        
        .video-section {
            flex: 1;
            min-width: 300px;
            background: rgba(0, 0, 0, 0.5);
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
        }
        
        .video-player {
            position: relative;
            background: #000;
            height: 0;
            padding-bottom: 56.25%; /* 16:9 Aspect Ratio */
        }
        
        .video-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(rgba(0, 0, 0, 0.3), rgba(0, 0, 0, 0.7)), 
                        url('https://upload.wikimedia.org/wikipedia/commons/thumb/4/42/Bundesarchiv_Bild_183-1982-0406-016%2C_Falklandkrieg%2C_versenkter_Zerst%C3%B6rer.jpg/800px-Bundesarchiv_Bild_183-1982-0406-016%2C_Falklandkrieg%2C_versenkter_Zerst%C3%B6rer.jpg');
            background-size: cover;
            background-position: center;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            color: white;
            padding: 20px;
        }
        
        .play-button {
            width: 80px;
            height: 80px;
            background: rgba(255, 0, 0, 0.8);
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            transition: all 0.3s;
            margin-bottom: 20px;
            animation: pulse 2s infinite;
        }
        
        .play-button:hover {
            transform: scale(1.1);
            background: rgba(255, 0, 0, 1);
        }
        
        .play-button i {
            font-size: 40px;
            margin-left: 5px;
        }
        
        .video-title {
            font-size: 1.8rem;
            text-align: center;
            margin-bottom: 10px;
            font-weight: bold;
        }
        
        .video-duration {
            font-size: 1rem;
            opacity: 0.8;
        }
        
        .video-controls {
            display: flex;
            justify-content: space-between;
            padding: 15px;
            background: rgba(0, 0, 0, 0.7);
        }
        
        .control-group {
            display: flex;
            gap: 15px;
        }
        
        .control-btn {
            background: none;
            border: none;
            color: #f0f0f0;
            font-size: 1.2rem;
            cursor: pointer;
            opacity: 0.8;
            transition: opacity 0.3s;
        }
        
        .control-btn:hover {
            opacity: 1;
        }
        
        .progress-container {
            flex-grow: 1;
            background: rgba(255, 255, 255, 0.1);
            height: 6px;
            border-radius: 3px;
            margin: 0 15px;
            align-self: center;
            cursor: pointer;
            position: relative;
        }
        
        .progress-bar {
            height: 100%;
            width: 35%;
            background: linear-gradient(to right, #ff7e5f, #feb47b);
            border-radius: 3px;
        }
        
        .info-section {
            flex: 1;
            min-width: 300px;
            background: rgba(0, 0, 0, 0.5);
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
        }
        
        .section-title {
            font-size: 1.8rem;
            margin-bottom: 20px;
            color: #feb47b;
            border-bottom: 2px solid rgba(255, 255, 255, 0.1);
            padding-bottom: 10px;
        }
        
        .timeline {
            position: relative;
            padding-left: 30px;
            margin-bottom: 30px;
        }
        
        .timeline::before {
            content: '';
            position: absolute;
            left: 0;
            top: 0;
            height: 100%;
            width: 4px;
            background: linear-gradient(to bottom, #ff7e5f, #feb47b);
        }
        
        .timeline-item {
            position: relative;
            margin-bottom: 25px;
        }
        
        .timeline-item::before {
            content: '';
            position: absolute;
            left: -34px;
            top: 5px;
            width: 16px;
            height: 16px;
            border-radius: 50%;
            background: #ff7e5f;
        }
        
        .timeline-date {
            font-weight: bold;
            color: #feb47b;
            margin-bottom: 5px;
        }
        
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 15px;
            margin: 25px 0;
        }
        
        .stat-card {
            background: rgba(255, 255, 255, 0.1);
            padding: 15px;
            border-radius: 10px;
            text-align: center;
            transition: transform 0.3s;
        }
        
        .stat-card:hover {
            transform: translateY(-5px);
            background: rgba(255, 255, 255, 0.15);
        }
        
        .stat-value {
            font-size: 2rem;
            font-weight: bold;
            color: #ff7e5f;
            margin: 10px 0;
        }
        
        .stat-label {
            font-size: 0.9rem;
            opacity: 0.8;
        }
        
        .footer-note {
            text-align: center;
            margin-top: 40px;
            padding-top: 20px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            font-size: 0.9rem;
            opacity: 0.7;
        }
        
        @keyframes pulse {
            0% { box-shadow: 0 0 0 0 rgba(255, 126, 95, 0.7); }
            70% { box-shadow: 0 0 0 15px rgba(255, 126, 95, 0); }
            100% { box-shadow: 0 0 0 0 rgba(255, 126, 95, 0); }
        }
        
        @media (max-width: 768px) {
            .documentary-container {
                flex-direction: column;
            }
            
            h1 {
                font-size: 2.2rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>GUERRA DE LAS MALVINAS</h1>
            <p class="subtitle">Conflicto armado entre Argentina y el Reino Unido en 1982 por la soberanía de las islas Malvinas, Georgias del Sur y Sandwich del Sur</p>
        </header>
        
        <div class="documentary-container">
            <div class="video-section">
                <div class="video-player">
                    <div class="video-overlay">
                        <div class="play-button">
                            <i class="fas fa-play"></i>
                        </div>
                        <h2 class="video-title">Documental: La Guerra del Atlántico Sur</h2>
                        <p class="video-duration">Duración: 47:22</p>
                    </div>
                </div>
                <div class="video-controls">
                    <div class="control-group">
                        <button class="control-btn"><i class="fas fa-backward"></i></button>
                        <button class="control-btn"><i class="fas fa-play"></i></button>
                        <button class="control-btn"><i class="fas fa-forward"></i></button>
                    </div>
                    <div class="progress-container">
                        <div class="progress-bar"></div>
                    </div>
                    <div class="control-group">
                        <button class="control-btn"><i class="fas fa-volume-up"></i></button>
                        <button class="control-btn"><i class="fas fa-expand"></i></button>
                    </div>
                </div>
            </div>
            
            <div class="info-section">
                <h2 class="section-title">Cronología del Conflicto</h2>
                
                <div class="timeline">
                    <div class="timeline-item">
                        <div class="timeline-date">2 de abril de 1982</div>
                        <p>Fuerzas militares argentinas desembarcan en las islas Malvinas, tomando el control de Puerto Stanley (rebautizado Puerto Argentino).</p>
                    </div>
                    <div class="timeline-item">
                        <div class="timeline-date">5 de abril de 1982</div>
                        <p>El Reino Unido envía una fuerza naval masiva hacia el Atlántico Sur, liderada por los portaaviones HMS Hermes y HMS Invincible.</p>
                    </div>
                    <div class="timeline-item">
                        <div class="timeline-date">25 de abril de 1982</div>
                        <p>Las fuerzas británicas recuperan las islas Georgias del Sur.</p>
                    </div>
                    <div class="timeline-item">
                        <div class="timeline-date">1-2 de mayo de 1982</div>
                        <p>Comienza la campaña aérea y naval británica. El submarino nuclear HMS Conqueror hunde el crucero ARA General Belgrano.</p>
                    </div>
                    <div class="timeline-item">
                        <div class="timeline-date">21 de mayo de 1982</div>
                        <p>Desembarco británico en San Carlos, en la isla Soledad.</p>
                    </div>
                    <div class="timeline-item">
                        <div class="timeline-date">14 de junio de 1982</div>
                        <p>Las fuerzas argentinas en Puerto Argentino se rinden. Fin de las hostilidades.</p>
                    </div>
                </div>
                
                <h2 class="section-title">Estadísticas del Conflicto</h2>
                
                <div class="stats-grid">
                    <div class="stat-card">
                        <div class="stat-value">74</div>
                        <div class="stat-label">Días de conflicto</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-value">649</div>
                        <div class="stat-label">Muertos argentinos</div>
                    </div>
                    <div class="stat-card">
                        <
