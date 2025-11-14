<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistema de Orçamento - Móveis</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css">
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            background-color: #f4f7f6;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            color: #333;
        }

        #dashboardLayout {
            display: flex;
            width: 100%;
            max-width: 1200px;
            background-color: #ffffff;
            border-radius: 12px;
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1); /* Softer shadow */
            padding: 0;
            min-height: 80vh;
            overflow: hidden;
        }

        #sidebar {
            width: 220px;
            background-color: #2c3e50;
            padding: 20px;
            border-radius: 12px 0 0 12px;
            display: flex;
            flex-direction: column;
            flex-shrink: 0;
        }

        .sidebar-header {
            text-align: center;
            margin-bottom: 30px;
            padding-bottom: 15px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        .sidebar-header h2 {
            color: #ffffff;
            margin: 0;
            font-size: 1.6em;
            font-weight: 600; /* Slightly bolder */
        }

        #sidebar ul {
            list-style: none;
            padding: 0;
            margin: 0;
            flex-grow: 1;
        }

        #sidebar li a {
            display: flex; /* Use flex for icon alignment */
            align-items: center;
            padding: 10px 15px;
            margin-bottom: 8px;
            color: #ffffff;
            text-decoration: none;
            border-radius: 5px;
            transition: background-color 0.2s ease, transform 0.2s ease, border-left 0.2s ease; /* Add border transition */
        }
        #sidebar li a i {
            margin-right: 10px; /* Space between icon and text */
        }

        #sidebar li a:hover {
            background-color: #34495e;
            transform: translateX(3px);
        }

        #sidebar li a.active {
            background-color: #3498db; /* A slightly different shade of blue for active */
            font-weight: bold;
            border-left: 5px solid #2ecc71; /* Stronger active indicator */
            padding-left: 10px; /* Adjust padding due to border */
        }

        #mainContentArea {
            flex-grow: 1;
            padding: 40px;
            display: flex;
            flex-direction: column;
        }

        .header {
            text-align: center;
            color: #2c3e50;
            border-bottom: 1px solid #eee;
            padding-bottom: 20px;
            margin-bottom: 20px;
        }
        .header h1 {
            margin: 0;
            font-size: 2.2em;
        }
        .overview-section {
            display: flex;
            gap: 30px;
            flex-wrap: wrap;
            justify-content: center;
            align-items: stretch;
        }
        .card {
            background-color: #fcfcfc;
            border: 1px solid #e0e0e0;
            border-radius: 8px;
            padding: 25px;
            flex: 1;
            min-width: 280px;
            max-width: 45%;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            transition: transform 0.2s ease, box-shadow 0.2s ease;
        }
        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.1);
        }
        .card h2 {
            margin-top: 0;
            color: #34495e;
            font-size: 1.5em;
            border-bottom: 2px solid #2980b9;
            padding-bottom: 10px;
            margin-bottom: 20px;
        }
        .card p {
            font-size: 1em;
            line-height: 1.6;
            color: #555;
        }
        .central-element {
            background-color: #21618C; /* Azul no meio - darker shade */
            color: #ffffff;
            border-radius: 12px;
            padding: 30px;
            text-align: center;
            flex: 2;
            min-width: 300px;
            max-width: 50%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            box-shadow: 0 8px 25px rgba(52, 152, 219, 0.3);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .central-element:hover {
            transform: scale(1.02);
            box-shadow: 0 10px 30px rgba(52, 152, 219, 0.4);
        }
        .central-element h2 {
            font-size: 1.8em;
            margin-bottom: 15px;
            color: #ffffff;
        }
        .central-element .button {
            background-color: #2ecc71;
            color: #ffffff;
            border: none;
            padding: 12px 25px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1.1em;
            transition: background-color 0.3s ease, transform 0.2s ease;
            text-decoration: none;
            display: inline-block;
            margin-top: 20px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2); /* Added shadow for professional look */
        }
        .central-element .button:hover {
            background-color: #27ae60;
            transform: translateY(-2px);
        }
        /* Professional button style for general purpose buttons */
        .button {
            background-color: #3498db; /* Default blue for buttons */
            color: #ffffff;
            border: none;
            padding: 10px 20px; /* Adjusted padding */
            border-radius: 5px; /* Slightly rounded corners */
            cursor: pointer;
            font-size: 1em;
            transition: background-color 0.3s ease, transform 0.2s ease, box-shadow 0.2s ease; /* Added box-shadow transition */
            text-decoration: none;
            display: inline-block;
            margin-top: 15px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15); /* Added subtle shadow */
        }
        .button:hover {
            background-color: #2980b9; /* Darker blue on hover */
            transform: translateY(-2px); /* Lift effect on hover */
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.25); /* Enhanced shadow on hover */
        }

        .footer {
            text-align: center;
            margin-top: auto;
            padding-top: 20px;
            color: #888;
            font-size: 0.9em;
            border-top: 1px solid #eee;
        }
        .form-section {
            background-color: #fcfcfc;
            border: 1px solid #e0e0e0;
            border-radius: 8px;
            padding: 25px;
            margin-top: 20px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
        }
        .form-section h2 {
            margin-top: 0;
            color: #34495e;
            font-size: 1.5em;
            border-bottom: 2px solid #2980b9;
            padding-bottom: 10px;
            margin-bottom: 20px;
        }
        .form-group {
            margin-bottom: 15px;
        }
        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
            color: #555;
        }
        .form-group input, .form-group select {
            width: calc(100% - 22px);
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 4px;
            font-size: 1em;
            box-sizing: border-box;
            transition: border-color 0.2s ease, box-shadow 0.2s ease;
        }
        .form-group input:focus, .form-group select:focus {
            border-color: #3498db; /* Highlight border on focus */
            box-shadow: 0 0 5px rgba(52, 152, 219, 0.5); /* Subtle shadow on focus */
            outline: none;
        }
        .pecas-form.editing-form .form-group input,
        .pecas-form.editing-form .form-group select {
            background-color: #fffacd;
        }
        .material-form.editing-form .form-group input,
        .material-form.editing-form .form-group select {
            background-color: #fffacd; /* A light yellow color for material edit */
        }
        .form-row {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
            margin-bottom: 15px;
        }
        .form-row .form-group {
            flex: 1;
            margin-bottom: 0;
            min-width: 150px;
        }
        /* Specific width adjustments for cadastro form fields */
        #cadastroContentSection .form-row .form-group:nth-child(1) { /* Nome */
            flex-basis: 50%; /* Wider */
            min-width: 180px;
        }
        #cadastroContentSection .form-row .form-group:nth-child(2) { /* Unidade */
            flex-basis: 20%; /* Smaller */
            min-width: 100px;
        }
        #cadastroContentSection .form-row .form-group:nth-child(3) { /* Valor */
            flex-basis: 20%; /* Smaller */
            min-width: 100px;
            max-width: 120px; /* Ensure it's not too wide */
        }

        .pieces-table-section {
            margin-top: 30px;
            background-color: #ffffff;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
            padding: 20px;
        }
        .pieces-table-section h2 {
            margin-top: 0;
            color: #34495e;
            font-size: 1.5em;
            border-bottom: 2px solid #2980b9;
            padding-bottom: 10px;
            margin-bottom: 20px;
        }
        .pieces-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }
        .pieces-table th, .pieces-table td {
            border: 1px solid #ddd;
            padding: 10px;
            text-align: left;
        }
        .pieces-table th {
            background-color: #f2f2f2;
            font-weight: bold;
            color: #333;
        }
        .summary-info p {
            margin: 5px 0;
            font-size: 1.1em;
            color: #555;
        }
        .action-button {
            background: none;
            border: none;
            cursor: pointer;
            font-size: 1.1em;
            margin: 0 5px;
            color: #3498db;
        }
        .action-button.delete {
            color: #e74c3c;
        }
        .action-button:hover {
            opacity: 0.7;
        }
        .form-group select option[disabled][selected] {
            color: #a0a0a0; /* Lighter color for placeholder */
        }
        .form-group select:not(:valid) {
            color: #a0a0a0; /* Apply lighter color when placeholder is selected */
        }

        @media (max-width: 768px) {
            #dashboardLayout {
                flex-direction: column;
                padding: 0;
            }
            #sidebar {
                width: 100%;
                border-radius: 12px 12px 0 0;
                margin-bottom: 0;
                padding: 15px;
            }
            .sidebar-header {
                margin-bottom: 15px;
            }
            #sidebar ul li a {
                padding: 8px 12px;
                margin-bottom: 5px;
            }
            #mainContentArea {
                padding: 20px;
                padding-top: 25px;
                border-radius: 0 0 12px 12px;
                margin-top: -1px;
                border-top: 1px solid #eee;
            }
            .overview-section {
                flex-direction: column;
                align-items: center;
            }
            .card, .central-element {
                max-width: 90%;
                width: 100%;
            }
            .form-row {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <div id="dashboardLayout">
        <nav id="sidebar">
            <div class="sidebar-header">
                <h2>Menu</h2>
            </div>
            <ul>
                <li><a href="#" id="showOverview"><i class="fas fa-home"></i> Página Inicial</a></li>
                <li><a href="#" id="showPecas"><i class="fas fa-boxes"></i> Peças</a></li>
                <li><a href="#" id="showCadastro"><i class="fas fa-tools"></i> Cadastro de Materiais e Componentes</a></li>
            </ul>
        </nav>

        <div id="mainContentArea">
            <div class="header">
                <h1>Sistema de Orçamento de Móveis</h1>
                <p>Gerencie seus projetos de forma eficiente.</p>
            </div>

            <div id="overviewSection" class="overview-section" style="display: none;">
                <div class="card">
                    <h2><i class="icon fas fa-folder-open"></i> Projetos Recentes</h2>
                    <p>Acompanhe o andamento dos seus últimos orçamentos e projetos em andamento.</p>
                    <p><span>Orçamento #101 - Cliente A</span><br/><span>Orçamento #100 - Cliente B</span></p>
                </div>
                <div class="central-element">
                    <h2>Crie um Novo Orçamento</h2>
                    <p>Comece um novo projeto para seu cliente com facilidade e rapidez.</p>
                    <a href="#" class="button" id="startButton">Iniciar Orçamento</a>
                </div>
                <div class="card">
                    <h2><i class="icon fas fa-chart-line"></i> Relatórios e Análises</h2>
                    <p>Visualize métricas importantes e tome decisões baseadas em dados.</p>
                    <p><span>Total de Vendas: R$ 150.000</span><br/><span>Projetos Ativos: 12</span></p>
                </div>
            </div>

            <div id="pecasContentSection" style="display: none;">
                <div id="pecasForm" class="form-section pecas-form">
                    <h2>Detalhes das Peças</h2>
                    <form id="addPieceForm">
                        <input type="hidden" id="editingRowIndex" value="-1">
                        <div class="form-group">
                            <label for="materialType">Tipo de material:</label>
                            <select id="materialType" name="materialType">
                                <option value="mdf">MDF</option>
                                <option value="mdp">MDP</option>
                                <option value="compensado">Compensado</option>
                            </select>
                        </div>
                        <div class="form-row">
                            <div class="form-group">
                                <label for="length">Comprimento (mm):</label>
                                <input type="number" id="length" name="length" placeholder="Ex: 1200" min="0">
                            </div>
                            <div class="form-group">
                                <label for="width">Largura (mm):</label>
                                <input type="number" id="width" name="width" placeholder="Ex: 600" min="0">
                            </div>
                            <div class="form-group">
                                <label for="quantity">Quantidade:</label>
                                <input type="number" id="quantity" name="quantity" placeholder="Ex: 1" min="1">
                            </div>
                        </div>
                        <div class="form-row">
                            <div class="form-group">
                                <label for="pecasItemName">Nome:</label>
                                <input type="text" id="pecasItemName" name="pecasItemName" placeholder="Ex: Porta armário">
                            </div>
                            <div class="form-group">
                                <label for="tapeType">Tipo de fita:</label>
                                <input type="text" id="tapeType" name="tapeType" placeholder="Ex: PVC">
                            </div>
                            <div class="form-group">
                                <label for="tapeLetter">Letra da Fita:</label>
                                <input type="text" id="tapeLetter" name="tapeLetter" placeholder="Ex: A">
                            </div>
                        </div>
                        <button type="submit" class="button" id="savePieceButton">Adicionar Peça</button>
                    </form>
                </div>

                <div id="addedPiecesSection" class="pieces-table-section">
                    <h2>Peças Adicionadas</h2>
                    <table class="pieces-table">
                        <thead>
                            <tr>
                                <th>Material</th>
                                <th>Comp.</th>
                                <th>Larg.</th>
                                <th>Quant.</th>
                                <th>Nome</th>
                                <th>Tipo Fita</th>
                                <th>Letra Fita</th>
                                <th>Editar</th>
                                <th>Remover</th>
                            </tr>
                        </thead>
                        <tbody id="piecesTableBody">
                            <!-- Piece rows will be added here -->
                        </tbody>
                    </table>
                </div>

                <div id="summarySection" class="pieces-table-section">
                    <h2>Resumo do Orçamento</h2>
                    <div id="globalSummary" class="summary-info">
                        <p>Área Total: <span id="totalArea">0 m²</span></p>
                        <p>Perímetro Total: <span id="totalPerimeter">0 m</span></p>
                    </div>
                    <div id="tapeSummary" class="summary-info">
                        <h3>Resumo de Fitas por Cor</h3>
                        <!-- Tape summaries will be added dynamically here -->
                    </div>
                    <div id="financialSummary" class="summary-info">
                        <h3>Resumo Financeiro</h3>
                        <p>Total de Materiais: <span id="totalMaterialCost">R$ 0.00</span></p>
                        <p>Total de Componentes: <span id="totalComponentCost">R$ 0.00</span></p>
                        <p>Total de Fitas: <span id="totalTapeCost">R$ 0.00</span></p>
                        <p>Custo Total do Projeto: <span id="totalProjectCost">R$ 0.00</span></p>
                    </div>
                    <div id="materialSummary" class="summary-info">
                        <!-- Material-specific summaries will be added dynamically here -->
                    </div>
                </div>
            </div>
            <!-- Placeholder for Cadastro de Materiais e Componentes -->
            <div id="cadastroContentSection" style="display: none;">
                <h2>Cadastro de Materiais e Componentes</h2>
                <div id="generalItemForm" class="form-section material-form">
                    <form id="addItemForm">
                        <input type="hidden" id="editingGeneralItemIndex" value="-1">
                        <div class="form-group">
                            <label for="itemType">Tipo:</label>
                            <select id="itemType" name="itemType" required>
                                <option value="" selected disabled hidden>selecione o tipo</option>
                                <option value="material">Material</n>
                                <option value="componente">Componente</option>
                            </select>
                        </div>
                        <div class="form-row">
                            <div class="form-group">
                                <label for="itemName">Nome:</label>
                                <input type="text" id="itemName" name="itemName" placeholder="Ex: MDF Branco" required>
                            </div>
                            <div class="form-group">
                                <label for="itemUnit">Unidade:</label>
                                <select id="itemUnit" name="itemUnit" required>
                                    <option value="" selected disabled hidden>selecione a unidade</option>
                                    <option value="unidade">unidade</option>
                                    <option value="m">m</option>
                                    <option value="m2">m²</option>
                                    <option value="par">par</option>
                                    <option value="kg">kg</option>
                                    <option value="L">L</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label for="itemValue">Valor:</label>
                                <input type="number" id="itemValue" name="itemValue" placeholder="Ex: 150.50" min="0" step="0.01" required>
                            </div>
                        </div>
                        <button type="submit" class="button" id="saveGeneralItemButton">Adicionar Item</button>
                    </form>
                </div>

                <div id="addedMaterialsSection" class="pieces-table-section">
                    <h2>Materiais Cadastrados</h2>
                    <table id="materialsTable" class="pieces-table">
                        <thead>
                            <tr>
                                <th>Nome</th>
                                <th>Unidade</th>
                                <th>Valor</th>
                                <th>Ações</th>
                            </tr>
                        </thead>
                        <tbody id="materialsTableBody">
                            <!-- Material rows will be added here -->
                        </tbody>
                    </table>
                </div>

                <div id="addedComponentsSection" class="pieces-table-section">
                    <h2>Componentes Cadastrados</h2>
                    <table id="componentsTable" class="pieces-table">
                        <thead>
                            <tr>
                                <th>Nome</th>
                                <th>Unidade</th>
                                <th>Valor</th>
                                <th>Ações</th>
                            </tr>
                        </thead>
                        <tbody id="componentsTableBody">
                            <!-- Component rows will be added here -->
                        </tbody>
                    </table>
                </div>
            </div>

            <div class="footer">
                &copy; 2023 Sua Empresa de Móveis. Todos os direitos reservados.
            </div>
        </div>
    </div>

    <script>
        const startButton = document.getElementById('startButton');
        const showOverviewLink = document.getElementById('showOverview');
        const showPecasLink = document.getElementById('showPecas');
        const showCadastroLink = document.getElementById('showCadastro');
        const overviewSection = document.getElementById('overviewSection');
        const pecasContentSection = document.getElementById('pecasContentSection');
        const cadastroContentSection = document.getElementById('cadastroContentSection');
        const pecasMaterialTypeDropdown = document.getElementById('materialType'); // Reference to the dropdown
        const pecasForm = document.getElementById('pecasForm');
        const summarySection = document.getElementById('summarySection');
        const addedPiecesSection = document.getElementById('addedPiecesSection');

        const savePieceButton = document.getElementById('savePieceButton');
        const editingRowIndexInput = document.getElementById('editingRowIndex');
        const piecesTableBody = document.getElementById('piecesTableBody');
        const materialSummaryDiv = document.getElementById('materialSummary');
        const tapeSummaryDiv = document.getElementById('tapeSummary');
        const financialSummaryDiv = document.getElementById('financialSummary'); // New element

        let globalTotalArea = 0;
        let globalTotalPerimeter = 0;
        const materialTotals = {
            mdf: { area: 0, perimeter: 0 },
            mdp: { area: 0, perimeter: 0 },
            compensado: { area: 0, perimeter: 0 }
        };
        const materialNames = {
            mdf: 'MDF',
            mdp: 'MDP',
            compensado: 'Compensado'
        };

        let tapeTotals = {}; // Initialize tapeTotals object
        let totalMaterialCost = 0; // New cost variable
        let totalComponentCost = 0; // New cost variable
        let totalTapeCost = 0; // New cost variable

        function updateSummaryDisplay() {
            document.getElementById('totalArea').textContent = (globalTotalArea / 1000000).toFixed(2) + ' m²'; // Convert mm² to m²
            document.getElementById('totalPerimeter').textContent = (globalTotalPerimeter / 1000).toFixed(2) + ' m'; // Convert mm to m

            materialSummaryDiv.innerHTML = '';

            const currentMaterialsInPecas = registeredMaterials.filter(item => item.type === 'material').map(m => m.name);
            const allMaterialTypes = new Set([...Object.keys(materialTotals), ...currentMaterialsInPecas]);

            for (const materialType of allMaterialTypes) {
                if (!materialTotals[materialType]) {
                    materialTotals[materialType] = { area: 0, perimeter: 0 };
                    if (!materialNames[materialType]) {
                        materialNames[materialType] = materialType;
                    }
                }

                if (materialTotals[materialType].area > 0 || materialTotals[materialType].perimeter > 0) {
                    const p = document.createElement('p');
                    p.id = materialType + 'SummaryLine';
                    p.innerHTML = `${materialNames[materialType]} - Área Total: <span id="${materialType}Area">${(materialTotals[materialType].area / 1000000).toFixed(2)} m²</span> | Perímetro Total: <span id="${materialType}Perimeter">${(materialTotals[materialType].perimeter / 1000).toFixed(2)} m</span>`;
                    materialSummaryDiv.appendChild(p);
                }
            }

            // Update tape summary display
            tapeSummaryDiv.innerHTML = '<h3>Resumo de Fitas por Cor</h3>';
            for (const color in tapeTotals) {
                if (tapeTotals[color] > 0) {
                    const p = document.createElement('p');
                    p.innerHTML = `Fita ${color}: <span id="${color}TapeTotal">${(tapeTotals[color] / 1000).toFixed(2)} m</span>`; // Convert mm to m
                    tapeSummaryDiv.appendChild(p);
                }
            }

            // Recalculate financial summary
            totalMaterialCost = 0;
            totalComponentCost = 0;
            totalTapeCost = 0;

            for (let i = 0; i < piecesTableBody.rows.length; i++) {
                const pieceData = JSON.parse(piecesTableBody.rows[i].dataset.pieceData);
                totalMaterialCost += pieceData.pieceMaterialCost || 0;
                totalTapeCost += pieceData.pieceTapeCost || 0;
            }

            // Sum costs of all registered components. Assuming 'unidade' or other units mean direct cost.
            // This part might need refinement based on how components are _used_ in a project.
            registeredComponents.forEach(comp => {
                totalComponentCost += comp.value; // For simplicity, sum up value of all registered components
            });

            // Update financial summary display
            document.getElementById('totalMaterialCost').textContent = `R$ ${totalMaterialCost.toFixed(2)}`;
            document.getElementById('totalComponentCost').textContent = `R$ ${totalComponentCost.toFixed(2)}`;
            document.getElementById('totalTapeCost').textContent = `R$ ${totalTapeCost.toFixed(2)}`;
            document.getElementById('totalProjectCost').textContent = `R$ ${(totalMaterialCost + totalComponentCost + totalTapeCost).toFixed(2)}`;
        }

        function clearForm() {
            document.getElementById('length').value = '';
            document.getElementById('width').value = '';
            document.getElementById('quantity').value = '';
            document.getElementById('pecasItemName').value = '';
            document.getElementById('tapeType').value = '';
            document.getElementById('tapeLetter').value = '';
            pecasMaterialTypeDropdown.value = 'mdf'; // Reset to default
            editingRowIndexInput.value = -1;
            savePieceButton.textContent = 'Adicionar Peça';
            savePieceButton.style.backgroundColor = '#3498db';
            pecasForm.classList.remove('editing-form');
            clearGeneralItemForm(); // Call new function to clear general item form
        }

        function updateMaterialTypeDropdown() {
            const currentSelection = pecasMaterialTypeDropdown.value;
            pecasMaterialTypeDropdown.innerHTML = '';
            const defaultMaterials = [
                { name: 'MDF', value: 'mdf' },
                { name: 'MDP', value: 'mdp' },
                { name: 'Compensado', value: 'compensado' }
            ];
            defaultMaterials.forEach(mat => {
                const option = document.createElement('option');
                option.value = mat.value;
                option.textContent = mat.name;
                pecasMaterialTypeDropdown.appendChild(option);
            });

            registeredMaterials.filter(item => item.type === 'material').forEach(mat => {
                const option = document.createElement('option');
                option.value = mat.name;
                option.textContent = mat.name;
                pecasMaterialTypeDropdown.appendChild(option);
            });

            if ([...pecasMaterialTypeDropdown.options].some(option => option.value === currentSelection)) {
                pecasMaterialTypeDropdown.value = currentSelection;
            } else {
                pecasMaterialTypeDropdown.value = 'mdf'; // Fallback to default
            }
        }

        function showSection(sectionToShow, activeLink) {
            overviewSection.style.display = 'none';
            pecasContentSection.style.display = 'none';
            cadastroContentSection.style.display = 'none';

            document.querySelectorAll('#sidebar ul li a').forEach(link => {
                link.classList.remove('active');
            });

            sectionToShow.style.display = 'block';
            if (activeLink) {
                activeLink.classList.add('active');
            }
            clearForm();
            if (sectionToShow === pecasContentSection) {
                updateMaterialTypeDropdown();
            }
            if (sectionToShow === cadastroContentSection) {
                renderMaterialsTable();
                renderComponentsTable();
            }
            updateSummaryDisplay(); // Always update summary when section changes
        }

        // Event listener for the 'Iniciar Orçamento' button within the overview
        if (startButton) {
            startButton.addEventListener('click', function(event) {
                event.preventDefault();
                showSection(pecasContentSection, showPecasLink);
                updateSummaryDisplay();
            });
        }

        // Event listeners for sidebar navigation
        if (showOverviewLink) {
            showOverviewLink.addEventListener('click', function(event) {
                event.preventDefault();
                showSection(overviewSection, showOverviewLink);
            });
        }

        if (showPecasLink) {
            showPecasLink.addEventListener('click', function(event) {
                event.preventDefault();
                showSection(pecasContentSection, showPecasLink);
                updateSummaryDisplay();
            });
        }

        if (showCadastroLink) {
            showCadastroLink.addEventListener('click', function(event) {
                event.preventDefault();
                showSection(cadastroContentSection, showCadastroLink);
            });
        }

        if (savePieceButton && piecesTableBody) {
            savePieceButton.addEventListener('click', function(event) {
                event.preventDefault();

                const materialType = pecasMaterialTypeDropdown.value;
                const length = parseFloat(document.getElementById('length').value);
                const width = parseFloat(document.getElementById('width').value);
                const quantity = parseInt(document.getElementById('quantity').value);
                const pecasItemName = document.getElementById('pecasItemName').value;
                const tapeType = document.getElementById('tapeType').value;
                const tapeLetter = document.getElementById('tapeLetter').value;
                const editingRowIndex = parseInt(editingRowIndexInput.value);

                if (isNaN(length) || isNaN(width) || isNaN(quantity) || length <= 0 || width <= 0 || quantity <= 0) {
                    alert('Por favor, insira valores válidos para Comprimento, Largura e Quantidade.');
                    return;
                }

                const pieceArea = length * width * quantity; // Calculated in mm²
                const piecePerimeter = (2 * (length + width)) * quantity; // Calculated in mm

                let tapeLength = 0;
                if (tapeLetter) {
                    switch (tapeLetter.toUpperCase()) {
                        case 'O': tapeLength = (2* (length + width)); break;
                        case 'I': tapeLength = length; break;
                        case 'U': tapeLength = (2 * length + width); break;
                        case 'C': tapeLength = (2 * width + length); break;
                        case 'H': tapeLength = (2 * length); break;
                        case 'L': tapeLength = (length + width); break;
                        default: tapeLength = 0;
                    }
                    tapeLength *= quantity;
                }

                // Get material and tape unit costs from registered items
                let materialUnitCost = 0;
                let tapeUnitCost = 0;

                const foundMaterial = registeredMaterials.find(mat => mat.name === materialType && mat.type === 'material');
                if (foundMaterial) {
                    materialUnitCost = foundMaterial.unit === 'm2' ? foundMaterial.value : 0; // Assuming cost is per m²
                } else if (materialType === 'mdf' || materialType === 'mdp' || materialType === 'compensado') {
                    // For default materials, we don't have a specific cost, so it remains 0 unless added in cadastro.
                    // This can be extended to have default costs later.
                }

                const foundTape = registeredComponents.find(comp => comp.name === tapeType && comp.type === 'componente' && comp.unit === 'm');
                if (foundTape) {
                    tapeUnitCost = foundTape.value; // Assuming cost is per m
                }

                const pieceMaterialCost = (pieceArea / 1000000) * materialUnitCost; // Convert mm² to m²
                const pieceTapeCost = (tapeLength / 1000) * tapeUnitCost; // Convert mm to m

                const pieceData = {
                    materialType: materialType,
                    length: length,
                    width: width,
                    quantity: quantity,
                    itemName: pecasItemName,
                    tapeType: tapeType,
                    tapeLetter: tapeLetter,
                    area: pieceArea,
                    perimeter: piecePerimeter,
                    tapeLength: tapeLength,
                    pieceMaterialCost: pieceMaterialCost,
                    pieceTapeCost: pieceTapeCost
                };

                if (editingRowIndex !== -1) {
                    const oldRow = piecesTableBody.rows[editingRowIndex];
                    const oldPieceData = JSON.parse(oldRow.dataset.pieceData);

                    globalTotalArea -= oldPieceData.area;
                    globalTotalPerimeter -= oldPieceData.perimeter;
                    if (materialTotals[oldPieceData.materialType]) {
                        materialTotals[oldPieceData.materialType].area -= oldPieceData.area;
                        materialTotals[oldPieceData.materialType].perimeter -= oldPieceData.perimeter;
                    }
                    if (oldPieceData.tapeType && tapeTotals[oldPieceData.tapeType]) {
                        tapeTotals[oldPieceData.tapeType] -= oldPieceData.tapeLength;
                    }

                    oldRow.cells[0].textContent = materialType;
                    oldRow.cells[1].textContent = length;
                    oldRow.cells[2].textContent = width;
                    oldRow.cells[3].textContent = quantity;
                    oldRow.cells[4].textContent = pecasItemName;
                    oldRow.cells[5].textContent = tapeType;
                    oldRow.cells[6].textContent = tapeLetter;
                    oldRow.dataset.pieceData = JSON.stringify(pieceData);

                } else {
                    const newRow = piecesTableBody.insertRow();
                    newRow.dataset.pieceData = JSON.stringify(pieceData);

                    newRow.insertCell().textContent = materialType;
                    newRow.insertCell().textContent = length;
                    newRow.insertCell().textContent = width;
                    newRow.insertCell().textContent = quantity;
                    newRow.insertCell().textContent = pecasItemName;
                    newRow.insertCell().textContent = tapeType;
                    newRow.insertCell().textContent = tapeLetter;

                    const editCell = newRow.insertCell();
                    const editButton = document.createElement('button');
                    editButton.className = 'action-button';
                    editButton.innerHTML = '<i class="fas fa-pencil-alt"></i>';
                    editButton.title = 'Editar Peça';
                    editButton.addEventListener('click', function() {
                        const rowIndex = newRow.rowIndex - 1;
                        editingRowIndexInput.value = rowIndex;
                        savePieceButton.textContent = 'Salvar Edição';
                        savePieceButton.style.backgroundColor = '#2ecc71';
                        pecasForm.classList.add('editing-form');

                        pecasMaterialTypeDropdown.value = pieceData.materialType;
                        document.getElementById('length').value = pieceData.length;
                        document.getElementById('width').value = pieceData.width;
                        document.getElementById('quantity').value = pieceData.quantity;
                        document.getElementById('pecasItemName').value = pieceData.itemName;
                        document.getElementById('tapeType').value = pieceData.tapeType;
                        document.getElementById('tapeLetter').value = pieceData.tapeLetter;
                    });
                    editCell.appendChild(editButton);

                    const removeCell = newRow.insertCell();
                    const removeButton = document.createElement('button');
                    removeButton.className = 'action-button delete';
                    removeButton.innerHTML = '<i class="fas fa-trash-alt"></i>';
                    removeButton.title = 'Remover Peça';
                    removeButton.addEventListener('click', function() {
                        const rowPieceData = JSON.parse(newRow.dataset.pieceData);

                        globalTotalArea -= rowPieceData.area;
                        globalTotalPerimeter -= rowPieceData.perimeter;
                        if (materialTotals[rowPieceData.materialType]) {
                            materialTotals[rowPieceData.materialType].area -= rowPieceData.area;
                            materialTotals[rowPieceData.materialType].perimeter -= rowPieceData.perimeter;
                        }
                        if (rowPieceData.tapeType && tapeTotals[rowPieceData.tapeType]) {
                            tapeTotals[rowPieceData.tapeType] -= rowPieceData.tapeLength;
                        }

                        newRow.remove();

                        updateSummaryDisplay();
                        clearForm();
                        saveDataToLocalStorage();
                    });
                    removeCell.appendChild(removeButton);
                }

                if (!materialTotals[materialType]) {
                    materialTotals[materialType] = { area: 0, perimeter: 0 };
                    materialNames[materialType] = materialType;
                }

                globalTotalArea += pieceArea;
                globalTotalPerimeter += piecePerimeter;

                materialTotals[materialType].area += pieceArea;
                materialTotals[materialType].perimeter += piecePerimeter;

                if (tapeType) {
                    if (!tapeTotals[tapeType]) {
                        tapeTotals[tapeType] = 0;
                    }
                    tapeTotals[tapeType] += tapeLength;
                }

                updateSummaryDisplay();
                clearForm();
                saveDataToLocalStorage();
            });
        }

        // Material & Component Management JavaScript
        const generalItemForm = document.getElementById('generalItemForm');
        const addItemForm = document.getElementById('addItemForm');
        const itemTypeInput = document.getElementById('itemType');
        const itemNameInput = document.getElementById('itemName');
        const itemUnitInput = document.getElementById('itemUnit');
        const itemValueInput = document.getElementById('itemValue');
        const saveGeneralItemButton = document.getElementById('saveGeneralItemButton');
        const editingGeneralItemIndexInput = document.getElementById('editingGeneralItemIndex');
        const materialsTableBody = document.getElementById('materialsTableBody');
        const componentsTableBody = document.getElementById('componentsTableBody');

        let registeredMaterials = [];
        let registeredComponents = [];

        function clearGeneralItemForm() {
            itemTypeInput.value = '';
            itemNameInput.value = '';
            itemUnitInput.value = '';
            itemValueInput.value = '';
            editingGeneralItemIndexInput.value = -1;
            saveGeneralItemButton.textContent = 'Adicionar Item';
            saveGeneralItemButton.style.backgroundColor = '#3498db';
            generalItemForm.classList.remove('editing-form');
        }

        function renderMaterialsTable() {
            materialsTableBody.innerHTML = '';
            registeredMaterials.forEach((item, index) => {
                const newRow = materialsTableBody.insertRow();
                newRow.insertCell().textContent = item.name;
                newRow.insertCell().textContent = item.unit;
                newRow.insertCell().textContent = `R$ ${item.value.toFixed(2)}`;

                const actionsCell = newRow.insertCell();
                const editButton = document.createElement('button');
                editButton.className = 'action-button';
                editButton.innerHTML = '<i class="fas fa-pencil-alt"></i>';
                editButton.title = 'Editar Item';
                editButton.addEventListener('click', function() {
                    itemTypeInput.value = 'material';
                    itemNameInput.value = item.name;
                    itemUnitInput.value = item.unit;
                    itemValueInput.value = item.value;
                    editingGeneralItemIndexInput.value = index;
                    saveGeneralItemButton.textContent = 'Salvar Edição';
                    saveGeneralItemButton.style.backgroundColor = '#2ecc71';
                    generalItemForm.classList.add('editing-form');
                });
                actionsCell.appendChild(editButton);

                const removeButton = document.createElement('button');
                removeButton.className = 'action-button delete';
                removeButton.innerHTML = '<i class="fas fa-trash-alt"></i>';
                removeButton.title = 'Remover Item';
                removeButton.addEventListener('click', function() {
                    registeredMaterials.splice(index, 1);
                    renderMaterialsTable();
                    updateMaterialTypeDropdown();
                    clearGeneralItemForm();
                    saveDataToLocalStorage();
                    updateSummaryDisplay(); // Update costs after removing material
                });
                actionsCell.appendChild(removeButton);
            });
        }

        function renderComponentsTable() {
            componentsTableBody.innerHTML = '';
            registeredComponents.forEach((item, index) => {
                const newRow = componentsTableBody.insertRow();
                newRow.insertCell().textContent = item.name;
                newRow.insertCell().textContent = item.unit;
                newRow.insertCell().textContent = `R$ ${item.value.toFixed(2)}`;

                const actionsCell = newRow.insertCell();
                const editButton = document.createElement('button');
                editButton.className = 'action-button';
                editButton.innerHTML = '<i class="fas fa-pencil-alt"></i>';
                editButton.title = 'Editar Item';
                editButton.addEventListener('click', function() {
                    itemTypeInput.value = 'componente';
                    itemNameInput.value = item.name;
                    itemUnitInput.value = item.unit;
                    itemValueInput.value = item.value;
                    editingGeneralItemIndexInput.value = index;
                    saveGeneralItemButton.textContent = 'Salvar Edição';
                    saveGeneralItemButton.style.backgroundColor = '#2ecc71';
                    generalItemForm.classList.add('editing-form');
                });
                actionsCell.appendChild(editButton);

                const removeButton = document.createElement('button');
                removeButton.className = 'action-button delete';
                removeButton.innerHTML = '<i class="fas fa-trash-alt"></i>';
                removeButton.title = 'Remover Item';
                removeButton.addEventListener('click', function() {
                    registeredComponents.splice(index, 1);
                    renderComponentsTable();
                    clearGeneralItemForm();
                    saveDataToLocalStorage();
                    updateSummaryDisplay(); // Update costs after removing component
                });
                actionsCell.appendChild(removeButton);
            });
        }

        if (saveGeneralItemButton) {
            saveGeneralItemButton.addEventListener('click', function(event) {
                event.preventDefault();

                const itemType = itemTypeInput.value;
                const itemName = itemNameInput.value.trim();
                const itemUnit = itemUnitInput.value.trim();
                const itemValue = parseFloat(itemValueInput.value);
                const editingIndex = parseInt(editingGeneralItemIndexInput.value);

                if (!itemName || itemUnit === '' || isNaN(itemValue) || itemValue <= 0) {
                    alert('Por favor, preencha todos os campos e insira um valor positivo para o item.');
                    return;
                }

                const newItemData = {
                    type: itemType,
                    name: itemName,
                    unit: itemUnit,
                    value: itemValue
                };

                if (itemType === 'material') {
                    if (editingIndex !== -1) {
                        registeredMaterials[editingIndex] = newItemData;
                    } else {
                        registeredMaterials.push(newItemData);
                    }
                    renderMaterialsTable();
                } else if (itemType === 'componente') {
                    if (editingIndex !== -1) {
                        registeredComponents[editingIndex] = newItemData;
                    } else {
                        registeredComponents.push(newItemData);
                    }
                    renderComponentsTable();
                }

                updateMaterialTypeDropdown();
                clearGeneralItemForm();
                saveDataToLocalStorage();
                updateSummaryDisplay(); // Update costs after add/edit general item
            });
        }

        // --- Data Persistence (Local Storage) --- //
        function saveDataToLocalStorage() {
            localStorage.setItem('registeredMaterials', JSON.stringify(registeredMaterials));
            localStorage.setItem('registeredComponents', JSON.stringify(registeredComponents));
            localStorage.setItem('tapeTotals', JSON.stringify(tapeTotals));

            const pieces = [];
            for (let i = 0; i < piecesTableBody.rows.length; i++) {
                const row = piecesTableBody.rows[i];
                if (row.dataset.pieceData) {
                    pieces.push(JSON.parse(row.dataset.pieceData));
                }
            }
            localStorage.setItem('piecesData', JSON.stringify(pieces));
        }

        function loadDataFromLocalStorage() {
            const storedMaterials = localStorage.getItem('registeredMaterials');
            if (storedMaterials) {
                registeredMaterials = JSON.parse(storedMaterials);
            }
            const storedComponents = localStorage.getItem('registeredComponents');
            if (storedComponents) {
                registeredComponents = JSON.parse(storedComponents);
            }
            const storedTapeTotals = localStorage.getItem('tapeTotals');
            if (storedTapeTotals) {
                tapeTotals = JSON.parse(storedTapeTotals);
            } else {
                tapeTotals = {};
            }

            const storedPieces = localStorage.getItem('piecesData');
            if (storedPieces) {
                const piecesData = JSON.parse(storedPieces);
                piecesData.forEach(pieceData => {
                    globalTotalArea += pieceData.area;
                    globalTotalPerimeter += pieceData.perimeter;

                    if (!materialTotals[pieceData.materialType]) {
                        materialTotals[pieceData.materialType] = { area: 0, perimeter: 0 };
                        if (!materialNames[pieceData.materialType]) {
                            materialNames[pieceData.materialType] = pieceData.materialType;
                        }
                    }
                    materialTotals[pieceData.materialType].area += pieceData.area;
                    materialTotals[pieceData.materialType].perimeter += pieceData.perimeter;

                    const newRow = piecesTableBody.insertRow();
                    newRow.dataset.pieceData = JSON.stringify(pieceData);

                    newRow.insertCell().textContent = pieceData.materialType;
                    newRow.insertCell().textContent = pieceData.length;
                    newRow.insertCell().textContent = pieceData.width;
                    newRow.insertCell().textContent = pieceData.quantity;
                    newRow.insertCell().textContent = pieceData.itemName;
                    newRow.insertCell().textContent = pieceData.tapeType;
                    newRow.insertCell().textContent = pieceData.tapeLetter;

                    const editCell = newRow.insertCell();
                    const editButton = document.createElement('button');
                    editButton.className = 'action-button';
                    editButton.innerHTML = '<i class="fas fa-pencil-alt"></i>';
                    editButton.title = 'Editar Peça';
                    editButton.addEventListener('click', function() {
                        const rowIndex = newRow.rowIndex - 1;
                        editingRowIndexInput.value = rowIndex;
                        savePieceButton.textContent = 'Salvar Edição';
                        savePieceButton.style.backgroundColor = '#2ecc71';
                        pecasForm.classList.add('editing-form');

                        pecasMaterialTypeDropdown.value = pieceData.materialType;
                        document.getElementById('length').value = pieceData.length;
                        document.getElementById('width').value = pieceData.width;
                        document.getElementById('quantity').value = pieceData.quantity;
                        document.getElementById('pecasItemName').value = pieceData.itemName;
                        document.getElementById('tapeType').value = pieceData.tapeType;
                        document.getElementById('tapeLetter').value = pieceData.tapeLetter;
                    });
                    editCell.appendChild(editButton);

                    const removeCell = newRow.insertCell();
                    const removeButton = document.createElement('button');
                    removeButton.className = 'action-button delete';
                    removeButton.innerHTML = '<i class="fas fa-trash-alt"></i>';
                    removeButton.title = 'Remover Peça';
                    removeButton.addEventListener('click', function() {
                        const rowPieceData = JSON.parse(newRow.dataset.pieceData);

                        globalTotalArea -= rowPieceData.area;
                        globalTotalPerimeter -= rowPieceData.perimeter;

                        if (materialTotals[rowPieceData.materialType]) {
                            materialTotals[rowPieceData.materialType].area -= rowPieceData.area;
                            materialTotals[rowPieceData.materialType].perimeter -= rowPieceData.perimeter;
                        }
                        if (rowPieceData.tapeType && tapeTotals[rowPieceData.tapeType]) {
                            tapeTotals[rowPieceData.tapeType] -= rowPieceData.tapeLength;
                        }

                        newRow.remove();

                        updateSummaryDisplay();
                        clearForm();
                        saveDataToLocalStorage();
                    });
                    removeCell.appendChild(removeButton);
                });
            }
            renderMaterialsTable();
            renderComponentsTable();
            updateMaterialTypeDropdown();
            updateSummaryDisplay(); // Call updateSummaryDisplay to show initial summary including financial
        }

        // Event listener to automatically set tapeType based on materialType
        pecasMaterialTypeDropdown.addEventListener('change', function() {
            const selectedMaterial = this.value; // e.g., 'mdf' or 'MDF Branco'
            let tapeType = '';

            const patterns = [
                'branco', 'white',
                'preto', 'black',
                'cinza', 'grey', 'gray',
                'amadeirado', 'woodgrain', 'carvalho', 'maple', 'cerejeira', 'nogueira',
                'verde', 'green',
                'rosa', 'pink',
                'azul', 'blue',
                'vermelho', 'red',
                'amarelo', 'yellow',
                'laranja', 'orange',
                'marrom', 'brown',
                'bege', 'beige',
                'transparente', 'transparent',
                'brilhante', 'glossy', 'brilho',
                'fosco', 'matte'
            ];

            const nameLower = selectedMaterial.toLowerCase();

            for (const pattern of patterns) {
                if (nameLower.includes(pattern)) {
                    tapeType = pattern.charAt(0).toUpperCase() + pattern.slice(1);
                    if (pattern === 'amadeirado') tapeType = 'Amadeirado';
                    break;
                }
            }
            document.getElementById('tapeType').value = tapeType;
        });

        // Initial display state: show overview section by default
        showSection(overviewSection, showOverviewLink);
        // Load data on initial page load
        loadDataFromLocalStorage();
    </script>
</body>
</html>
