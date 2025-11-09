<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Site de Estudo - Revisão de Conteúdos</title>
    <style>
        :root {
            --matematica: #3498db;
            --portugues: #e74c3c;
            --ciencias: #2ecc71;
            --destaque: #f1c40f;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f9f9f9;
            color: #333;
            line-height: 1.6;
        }
        
        header {
            background: linear-gradient(135deg, var(--matematica), var(--portugues), var(--ciencias));
            color: white;
            text-align: center;
            padding: 2rem 1rem;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }
        
        h1 {
            font-size: 2.5rem;
            margin-bottom: 0.5rem;
        }
        
        .subtitle {
            font-size: 1.2rem;
            opacity: 0.9;
        }
        
        nav {
            background-color: white;
            padding: 1rem;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        .nav-container {
            display: flex;
            justify-content: center;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .nav-btn {
            padding: 0.8rem 1.5rem;
            margin: 0 0.5rem;
            border: none;
            border-radius: 50px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .nav-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
        }
        
        .nav-btn.matematica {
            background-color: var(--matematica);
            color: white;
        }
        
        .nav-btn.portugues {
            background-color: var(--portugues);
            color: white;
        }
        
        .nav-btn.ciencias {
            background-color: var(--ciencias);
            color: white;
        }
        
        main {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 0 1rem;
        }
        
        .materia-section {
            display: none;
            background-color: white;
            border-radius: 10px;
            padding: 2rem;
            margin-bottom: 2rem;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }
        
        .materia-section.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .materia-header {
            display: flex;
            align-items: center;
            margin-bottom: 1.5rem;
            padding-bottom: 1rem;
            border-bottom: 2px solid;
        }
        
        .materia-matematica .materia-header {
            border-color: var(--matematica);
        }
        
        .materia-portugues .materia-header {
            border-color: var(--portugues);
        }
        
        .materia-ciencias .materia-header {
            border-color: var(--ciencias);
        }
        
        .materia-icon {
            font-size: 2rem;
            margin-right: 1rem;
        }
        
        .materia-title {
            font-size: 1.8rem;
        }
        
        .topics-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 1.5rem;
        }
        
        .topic-card {
            background-color: #f8f9fa;
            border-radius: 8px;
            padding: 1.5rem;
            transition: all 0.3s ease;
            border-left: 4px solid;
        }
        
        .topic-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 6px 12px rgba(0,0,0,0.1);
        }
        
        .matematica .topic-card {
            border-left-color: var(--matematica);
        }
        
        .portugues .topic-card {
            border-left-color: var(--portugues);
        }
        
        .ciencias .topic-card {
            border-left-color: var(--ciencias);
        }
        
        .topic-title {
            font-size: 1.2rem;
            margin-bottom: 0.8rem;
            color: #2c3e50;
        }
        
        .topic-content {
            color: #555;
        }
        
        .exercicios {
            margin-top: 2rem;
            padding-top: 1.5rem;
            border-top: 1px solid #eee;
        }
        
        .exercicio {
            background-color: #f8f9fa;
            border-radius: 8px;
            padding: 1.5rem;
            margin-bottom: 1rem;
        }
        
        .exercicio h3 {
            margin-bottom: 1rem;
        }
        
        .alternativas {
            margin: 1rem 0;
        }
        
        .alternativa {
            margin-bottom: 0.5rem;
        }
        
        .btn-verificar {
            background-color: var(--destaque);
            color: #333;
            border: none;
            padding: 0.7rem 1.5rem;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s ease;
        }
        
        .btn-verificar:hover {
            background-color: #f39c12;
        }
        
        .resultado {
            margin-top: 1rem;
            padding: 0.8rem;
            border-radius: 5px;
            display: none;
        }
        
        .correto {
            background-color: #d4edda;
            color: #155724;
            border: 1px solid #c3e6cb;
        }
        
        .incorreto {
            background-color: #f8d7da;
            color: #721c24;
            border: 1px solid #f5c6cb;
        }
        
        footer {
            background-color: #2c3e50;
            color: white;
            text-align: center;
            padding: 1.5rem;
            margin-top: 2rem;
        }
        
        @media (max-width: 768px) {
            .nav-container {
                flex-direction: column;
                align-items: center;
            }
            
            .nav-btn {
                width: 80%;
                margin: 0.3rem 0;
            }
            
            .topics-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <header>
        <h1>Site de Estudo</h1>
        <p class="subtitle">Revisão de Matemática, Português e Ciências</p>
    </header>
    
    <nav>
        <div class="nav-container">
            <button class="nav-btn matematica" onclick="mostrarMateria('matematica')">Matemática</button>
            <button class="nav-btn portugues" onclick="mostrarMateria('portugues')">Português</button>
            <button class="nav-btn ciencias" onclick="mostrarMateria('ciencias')">Ciências</button>
        </div>
    </nav>
    
    <main>
        <!-- Seção de Matemática -->
        <section id="matematica" class="materia-section materia-matematica active">
            <div class="materia-header">
                <div class="materia-icon">➗</div>
                <h2 class="materia-title">Matemática</h2>
            </div>
            
            <div class="topics-grid matematica">
                <div class="topic-card">
                    <h3 class="topic-title">Operações Básicas</h3>
                    <div class="topic-content">
                        <p>As quatro operações fundamentais: adição, subtração, multiplicação e divisão.</p>
                        <p><strong>Exemplo:</strong> 15 + 7 = 22, 9 × 6 = 54</p>
                    </div>
                </div>
                
                <div class="topic-card">
                    <h3 class="topic-title">Frações</h3>
                    <div class="topic-content">
                        <p>Representação de partes de um todo. Soma: denominadores iguais.</p>
                        <p><strong>Exemplo:</strong> 1/2 + 1/4 = 2/4 + 1/4 = 3/4</p>
                    </div>
                </div>
                
                <div class="topic-card">
                    <h3 class="topic-title">Porcentagem</h3>
                    <div class="topic-content">
                        <p>Razão com denominador 100. Para calcular: valor × porcentagem ÷ 100.</p>
                        <p><strong>Exemplo:</strong> 20% de 80 = 80 × 20 ÷ 100 = 16</p>
                    </div>
                </div>
                
                <div class="topic-card">
                    <h3 class="topic-title">Geometria Básica</h3>
                    <div class="topic-content">
                        <p>Área do quadrado: lado × lado. Área do retângulo: base × altura.</p>
                        <p><strong>Exemplo:</strong> Quadrado de lado 5cm: área = 5 × 5 = 25cm²</p>
                    </div>
                </div>
            </div>
            
            <div class="exercicios">
                <h3>Exercícios de Matemática</h3>
                
                <div class="exercicio">
                    <p>Qual é o resultado de 45 ÷ 9 + 7 × 2?</p>
                    <div class="alternativas">
                        <div class="alternativa">
                            <input type="radio" name="math1" value="a"> a) 15
                        </div>
                        <div class="alternativa">
                            <input type="radio" name="math1" value="b"> b) 19
                        </div>
                        <div class="alternativa">
                            <input type="radio" name="math1" value="c"> c) 23
                        </div>
                    </div>
                    <button class="btn-verificar" onclick="verificarResposta('math1', 'b')">Verificar Resposta</button>
                    <div class="resultado" id="resultado-math1"></div>
                </div>
                
                <div class="exercicio">
                    <p>Se um produto custa R$ 80,00 e tem 15% de desconto, qual será o novo preço?</p>
                    <div class="alternativas">
                        <div class="alternativa">
                            <input type="radio" name="math2" value="a"> a) R$ 65,00
                        </div>
                        <div class="alternativa">
                            <input type="radio" name="math2" value="b"> b) R$ 68,00
                        </div>
                        <div class="alternativa">
                            <input type="radio" name="math2" value="c"> c) R$ 72,00
                        </div>
                    </div>
                    <button class="btn-verificar" onclick="verificarResposta('math2', 'b')">Verificar Resposta</button>
                    <div class="resultado" id="resultado-math2"></div>
                </div>
            </div>
        </section>
        
        <!-- Seção de Português -->
        <section id="portugues" class="materia-section materia-portugues">
            <div class="materia-header">
                <div class="materia-icon">📚</div>
                <h2 class="materia-title">Português</h2>
            </div>
            
            <div class="topics-grid portugues">
                <div class="topic-card">
                    <h3 class="topic-title">Classes Gramaticais</h3>
                    <div class="topic-content">
                        <p>Substantivo: nome de seres, objetos, etc. Verbo: indica ação, estado.</p>
                        <p><strong>Exemplo:</strong> "Casa" (substantivo), "correr" (verbo)</p>
                    </div>
                </div>
                
                <div class="topic-card">
                    <h3 class="topic-title">Sujeito e Predicado</h3>
                    <div class="topic-content">
                        <p>Sujeito: de quem se fala. Predicado: o que se diz sobre o sujeito.</p>
                        <p><strong>Exemplo:</strong> "O menino (sujeito) brinca no parque (predicado)"</p>
                    </div>
                </div>
                
                <div class="topic-card">
                    <h3 class="topic-title">Concordância Verbal</h3>
                    <div class="topic-content">
                        <p>Verbo concorda em número e pessoa com o sujeito.</p>
                        <p><strong>Exemplo:</strong> "Eu estudo" / "Nós estudamos"</p>
                    </div>
                </div>
                
                <div class="topic-card">
                    <h3 class="topic-title">Pontuação</h3>
                    <div class="topic-content">
                        <p>Vírgula separa elementos. Ponto final encerra frases.</p>
                        <p><strong>Exemplo:</strong> "Ana, Pedro e Maria foram ao cinema."</p>
                    </div>
                </div>
            </div>
            
            <div class="exercicios">
                <h3>Exercícios de Português</h3>
                
                <div class="exercicio">
                    <p>Qual alternativa apresenta sujeito composto?</p>
                    <div class="alternativas">
                        <div class="alternativa">
                            <input type="radio" name="port1" value="a"> a) O cachorro late.
                        </div>
                        <div class="alternativa">
                            <input type="radio" name="port1" value="b"> b) Maria e João estudam.
                        </div>
                        <div class="alternativa">
                            <input type="radio" name="port1" value="c"> c) Choveu muito.
                        </div>
                    </div>
                    <button class="btn-verificar" onclick="verificarResposta('port1', 'b')">Verificar Resposta</button>
                    <div class="resultado" id="resultado-port1"></div>
                </div>
                
                <div class="exercicio">
                    <p>Assinale a frase com concordância verbal correta:</p>
                    <div class="alternativas">
                        <div class="alternativa">
                            <input type="radio" name="port2" value="a"> a) Os alunos faz a prova.
                        </div>
                        <div class="alternativa">
                            <input type="radio" name="port2" value="b"> b) Os alunos fazem a prova.
                        </div>
                        <div class="alternativa">
                            <input type="radio" name="port2" value="c"> c) Os alunos fazemos a prova.
                        </div>
                    </div>
                    <button class="btn-verificar" onclick="verificarResposta('port2', 'b')">Verificar Resposta</button>
                    <div class="resultado" id="resultado-port2"></div>
                </div>
            </div>
        </section>
        
        <!-- Seção de Ciências -->
        <section id="ciencias" class="materia-section materia-ciencias">
            <div class="materia-header">
                <div class="materia-icon">🔬</div>
                <h2 class="materia-title">Ciências</h2>
            </div>
            
            <div class="topics-grid ciencias">
                <div class="topic-card">
                    <h3 class="topic-title">Sistema Solar</h3>
                    <div class="topic-content">
                        <p>Conjunto de planetas que orbitam o Sol. Terra: 3º planeta.</p>
                        <p><strong>Exemplo:</strong> Mercúrio, Vênus, Terra, Marte, Júpiter, Saturno, Urano, Netuno</p>
                    </div>
                </div>
                
                <div class="topic-card">
                    <h3 class="topic-title">Cadeia Alimentar</h3>
                    <div class="topic-content">
                        <p>Relação de alimentação entre seres vivos. Produtores → consumidores.</p>
                        <p><strong>Exemplo:</strong> Planta → coelho → raposa</p>
                    </div>
                </div>
                
                <div class="topic-card">
                    <h3 class="topic-title">Estados da Matéria</h3>
                    <div class="topic-content">
                        <p>Sólido: forma definida. Líquido: forma do recipiente. Gasoso: sem forma.</p>
                        <p><strong>Exemplo:</strong> Gelo (sólido), água (líquido), vapor (gasoso)</p>
                    </div>
                </div>
                
                <div class="topic-card">
                    <h3 class="topic-title">Sistema Digestório</h3>
                    <div class="topic-content">
                        <p>Processa alimentos. Boca → esôfago → estômago → intestinos.</p>
                        <p><strong>Exemplo:</strong> Digestão começa na boca com a saliva.</p>
                    </div>
                </div>
            </div>
            
            <div class="exercicios">
                <h3>Exercícios de Ciências</h3>
                
                <div class="exercicio">
                    <p>Qual é o planeta conhecido como "planeta vermelho"?</p>
                    <div class="alternativas">
                        <div class="alternativa">
                            <input type="radio" name="cien1" value="a"> a) Vênus
                        </div>
                        <div class="alternativa">
                            <input type="radio" name="cien1" value="b"> b) Marte
                        </div>
                        <div class="alternativa">
                            <input type="radio" name="cien1" value="c"> c) Júpiter
                        </div>
                    </div>
                    <button class="btn-verificar" onclick="verificarResposta('cien1', 'b')">Verificar Resposta</button>
                    <div class="resultado" id="resultado-cien1"></div>
                </div>
                
                <div class="exercicio">
                    <p>Na cadeia alimentar, as plantas são consideradas:</p>
                    <div class="alternativas">
                        <div class="alternativa">
                            <input type="radio" name="cien2" value="a"> a) Consumidores
                        </div>
                        <div class="alternativa">
                            <input type="radio" name="cien2" value="b"> b) Produtores
                        </div>
                        <div class="alternativa">
                            <input type="radio" name="cien2" value="c"> c) Decompositores
                        </div>
                    </div>
                    <button class="btn-verificar" onclick="verificarResposta('cien2', 'b')">Verificar Resposta</button>
                    <div class="resultado" id="resultado-cien2"></div>
                </div>
            </div>
        </section>
    </main>
    
    <footer>
        <p>Site de Estudo - Revisão de Conteúdos &copy; 2023</p>
    </footer>
    
    <script>
        function mostrarMateria(materia) {
            // Esconde todas as seções
            document.querySelectorAll('.materia-section').forEach(section => {
                section.classList.remove('active');
            });
            
            // Mostra a seção selecionada
            document.getElementById(materia).classList.add('active');
        }
        
        function verificarResposta(perguntaId, respostaCorreta) {
            const opcoes = document.getElementsByName(perguntaId);
            let respostaSelecionada = '';
            
            // Encontra a resposta selecionada
            for (const op
