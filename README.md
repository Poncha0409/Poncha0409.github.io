<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gobernanza de Calidad 360° | Azure DevOps Pitch</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        body { font-family: 'Segoe UI', sans-serif; overflow: hidden; }
        
        /* Azure Colors */
        .az-blue { color: #0078D4; }
        .bg-az-blue { background-color: #0078D4; }
        .az-dark { background-color: #252423; }
        
        /* Custom Scrollbar */
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-thumb { background: #cbd5e1; border-radius: 3px; }

        /* Animations */
        .slide-in { animation: slideIn 0.4s cubic-bezier(0.16, 1, 0.3, 1); }
        @keyframes slideIn { from { opacity: 0; transform: translateX(20px); } to { opacity: 1; transform: translateX(0); } }

        /* Vertical Pipeline Connector */
        .pipeline-line { position: absolute; left: 24px; top: 40px; bottom: -20px; width: 2px; background: #e5e7eb; z-index: 0; }
        .step-active .pipeline-line { background: #10b981; }
    </style>
</head>
<body class="bg-gray-100 text-gray-800 h-screen flex">

    <aside class="w-72 bg-white shadow-xl flex flex-col z-20 h-full">
        <div class="p-6 border-b border-gray-100">
            <div class="flex items-center gap-2 mb-1">
                <i class="fa-solid fa-infinity text-2xl text-blue-600"></i>
                <h1 class="font-bold text-lg tracking-tight">Azure DevOps</h1>
            </div>
            <p class="text-xs text-gray-500 font-medium">Gobernanza de Calidad 360°</p>
        </div>

        <nav class="flex-1 overflow-y-auto py-4 space-y-1" id="nav-container">
            </nav>

        <div class="p-4 bg-gray-50 border-t border-gray-200">
            <button onclick="nextStep()" class="w-full bg-blue-600 hover:bg-blue-700 text-white font-semibold py-2 px-4 rounded shadow transition-colors">
                Siguiente Paso <i class="fa-solid fa-arrow-right ml-2"></i>
            </button>
        </div>
    </aside>

    <main class="flex-1 flex flex-col h-full relative overflow-hidden">
        
        <header class="bg-white p-6 shadow-sm z-10 flex justify-between items-center">
            <div>
                <span class="text-xs font-bold text-blue-600 uppercase tracking-wider" id="header-subtitle">INTRODUCCIÓN</span>
                <h2 class="text-3xl font-extrabold text-gray-900 mt-1" id="header-title">Del Caos al Control</h2>
            </div>
            <div class="text-right hidden md:block">
                <p class="text-sm text-gray-400">Presentación para Clientes</p>
                <p class="text-xs font-mono text-gray-300">v2.0.5 Release</p>
            </div>
        </header>

        <div class="flex-1 p-8 overflow-y-auto bg-slate-50 relative">
            <div id="content-stage" class="max-w-7xl mx-auto grid grid-cols-1 lg:grid-cols-12 gap-8 h-full">
                </div>
        </div>
    </main>

    <script>
        // --- DATA STRUCTURE: EL GUIÓN ---
        const steps = [
            {
                id: 0,
                short: "0. La Apertura",
                subtitle: "Paso 0: El Dolor del Cliente",
                title: "Desconexión Costosa",
                script: "Las empresas pierden dinero por desconexión. Requisitos en Word, Código en Git, Bugs en Excel. Es insostenible. ¿Cuántas veces han retrasado un lanzamiento por no saber el estado real de la calidad?",
                render: () => `
                    <div class="lg:col-span-5 flex flex-col justify-center space-y-6">
                        <div class="bg-red-50 border-l-4 border-red-500 p-4 rounded shadow-sm">
                            <h3 class="font-bold text-red-700"><i class="fa-solid fa-triangle-exclamation mr-2"></i>El Problema Actual</h3>
                            <ul class="mt-2 space-y-2 text-sm text-red-600">
                                <li><i class="fa-regular fa-file-word w-5"></i> Requisitos estáticos en .docx</li>
                                <li><i class="fa-brands fa-github w-5"></i> Código aislado en Repos</li>
                                <li><i class="fa-regular fa-file-excel w-5"></i> Bugs perdidos en hojas de cálculo</li>
                            </ul>
                        </div>
                        <p class="text-gray-600 text-lg leading-relaxed">${steps[0].script}</p>
                    </div>
                    <div class="lg:col-span-7 bg-white rounded-xl shadow-2xl border border-gray-200 overflow-hidden flex flex-col slide-in">
                        <div class="bg-gray-100 p-3 border-b flex gap-2 items-center">
                            <div class="flex gap-1"><div class="w-3 h-3 rounded-full bg-red-400"></div><div class="w-3 h-3 rounded-full bg-yellow-400"></div><div class="w-3 h-3 rounded-full bg-green-400"></div></div>
                            <span class="text-xs text-gray-500 font-mono ml-2">project-overview.az</span>
                        </div>
                        <div class="p-8 flex-1 flex items-center justify-center bg-slate-50">
                            <div class="text-center">
                                <h1 class="text-4xl font-extrabold text-slate-800 mb-2">Project <span class="text-blue-600">Titan</span></h1>
                                <p class="text-gray-400 mb-8">Estado actual: <span class="bg-red-100 text-red-600 px-2 py-1 rounded text-xs font-bold">RIESGO ALTO</span></p>
                                <div class="grid grid-cols-3 gap-4 text-left">
                                    <div class="bg-white p-4 rounded shadow border-t-4 border-blue-500">
                                        <div class="text-2xl font-bold">42</div>
                                        <div class="text-xs text-gray-500 uppercase">Work Items</div>
                                    </div>
                                    <div class="bg-white p-4 rounded shadow border-t-4 border-red-500">
                                        <div class="text-2xl font-bold">15</div>
                                        <div class="text-xs text-gray-500 uppercase">Critical Bugs</div>
                                    </div>
                                    <div class="bg-white p-4 rounded shadow border-t-4 border-orange-500">
                                        <div class="text-2xl font-bold">7 Days</div>
                                        <div class="text-xs text-gray-500 uppercase">Overdue</div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                `
            },
            {
                id: 1,
                short: "1. Flexibilidad",
                subtitle: "Paso 1: Modelos de Desarrollo",
                title: "Agnóstico a tu Proceso",
                script: "Azure DevOps no te obliga a trabajar de una sola forma. ¿Necesitas Sprints rápidos (Scrum)? Hecho. ¿Necesitas fases estrictas y auditoría (V-Model/CMMI)? También hecho. Soporta tu transición digital sin romper tus procesos.",
                render: () => `
                    <div class="lg:col-span-4 flex flex-col justify-center">
                        <p class="text-gray-600 text-lg mb-6">${steps[1].script}</p>
                        <div class="bg-blue-50 p-4 rounded-lg border border-blue-100">
                            <h4 class="font-bold text-blue-800 text-sm mb-2">Selecciona tu vista:</h4>
                            <div class="flex gap-2">
                                <button onclick="switchMethodology('agile')" id="btn-agile" class="flex-1 bg-white shadow py-2 px-3 text-sm font-bold text-blue-600 rounded border border-blue-200">Agile / Scrum</button>
                                <button onclick="switchMethodology('waterfall')" id="btn-waterfall" class="flex-1 bg-transparent py-2 px-3 text-sm font-medium text-gray-500 rounded hover:bg-white hover:shadow transition">Waterfall / Gantt</button>
                            </div>
                        </div>
                    </div>
                    <div class="lg:col-span-8 bg-gray-100 rounded-xl p-4 shadow-inner overflow-hidden relative slide-in">
                        <div id="methodology-visual" class="h-full">
                            </div>
                    </div>
                `
            },
            {
                id: 2,
                short: "2. Trazabilidad",
                subtitle: "Paso 2: Organización de Pruebas",
                title: "El Hilo Dorado",
                script: "Si el negocio cambia un requisito hoy, ¿cómo saben qué pruebas actualizar? Azure conecta todo automáticamente: Requisito ↔ Test Case ↔ Bug. Si el requisito cambia, el test se marca como 'Sospechoso'.",
                render: () => `
                    <div class="lg:col-span-12 mb-4">
                         <p class="text-gray-600 max-w-3xl">${steps[2].script}</p>
                    </div>
                    <div class="lg:col-span-12 flex flex-col md:flex-row gap-4 items-center justify-center py-10 slide-in">
                        
                        <div class="bg-white w-full md:w-1/3 p-6 rounded-lg shadow-lg border-l-4 border-blue-500 relative group cursor-pointer hover:-translate-y-1 transition">
                            <div class="absolute -right-3 top-1/2 bg-gray-300 text-gray-600 rounded-full w-6 h-6 flex items-center justify-center z-10 hidden md:flex"><i class="fa-solid fa-link"></i></div>
                            <div class="text-xs text-blue-600 font-bold uppercase mb-2"><i class="fa-solid fa-book-open mr-1"></i> User Story 452</div>
                            <h3 class="font-bold text-gray-800">Checkout Process Update</h3>
                            <p class="text-sm text-gray-500 mt-2">Como usuario, quiero pagar con PayPal...</p>
                            <div class="mt-4 flex items-center gap-2">
                                <img src="https://i.pravatar.cc/150?u=a" class="w-6 h-6 rounded-full">
                                <span class="text-xs text-gray-400">Changed 2h ago</span>
                            </div>
                        </div>

                        <div class="bg-white w-full md:w-1/3 p-6 rounded-lg shadow-lg border-l-4 border-orange-500 relative group cursor-pointer hover:-translate-y-1 transition">
                            <div class="absolute -right-3 top-1/2 bg-gray-300 text-gray-600 rounded-full w-6 h-6 flex items-center justify-center z-10 hidden md:flex"><i class="fa-solid fa-link"></i></div>
                            <div class="text-xs text-orange-600 font-bold uppercase mb-2 flex justify-between">
                                <span><i class="fa-solid fa-vial mr-1"></i> Test Case 99</span>
                                <span class="bg-yellow-100 text-yellow-700 px-1 rounded animate-pulse">Suspect</span>
                            </div>
                            <h3 class="font-bold text-gray-800">Verify PayPal Redirect</h3>
                            <p class="text-sm text-gray-500 mt-2">Steps to reproduce payment flow...</p>
                             <div class="mt-4 flex items-center gap-2">
                                <span class="text-xs bg-gray-100 px-2 py-1 rounded">Linked to US-452</span>
                            </div>
                        </div>

                        <div class="bg-white w-full md:w-1/3 p-6 rounded-lg shadow-lg border-l-4 border-red-500 group cursor-pointer hover:-translate-y-1 transition">
                            <div class="text-xs text-red-600 font-bold uppercase mb-2"><i class="fa-solid fa-bug mr-1"></i> Bug 1024</div>
                            <h3 class="font-bold text-gray-800">404 on Gateway Return</h3>
                            <p class="text-sm text-gray-500 mt-2">System crashes when returning from PayPal.</p>
                            <div class="mt-4 border-t pt-2 text-xs text-gray-400">
                                <i class="fa-brands fa-github mr-1"></i> Fix PR #202 linked
                            </div>
                        </div>
                    </div>
                `
            },
            {
                id: 3,
                short: "3. Cobertura",
                subtitle: "Paso 3: Niveles y Tipos de Pruebas",
                title: "Calidad en Cada Capa",
                script: "¿Cómo aseguramos que el código no rompe lo funcional? 'Pipelines' protege el código (Caja Blanca/Unitarias) y 'Test Plans' protege el negocio (Caja Negra/Manuales).",
                render: () => `
                    <div class="lg:col-span-4 flex flex-col gap-4">
                        <p class="text-gray-600 mb-4">${steps[3].script}</p>
                        
                        <div class="space-y-2">
                            <div onclick="showCoverage('whitebox')" class="cursor-pointer p-4 rounded border-2 border-blue-500 bg-blue-50 hover:bg-blue-100 transition">
                                <div class="font-bold text-blue-800">Caja Blanca (Automático)</div>
                                <div class="text-xs text-blue-600">Unit Tests & Integration (Pipelines)</div>
                            </div>
                            <div onclick="showCoverage('blackbox')" class="cursor-pointer p-4 rounded border border-gray-200 bg-white hover:border-orange-300 hover:bg-orange-50 transition">
                                <div class="font-bold text-gray-800">Caja Negra (Humano)</div>
                                <div class="text-xs text-gray-500">UAT & Exploratory (Test Plans)</div>
                            </div>
                        </div>
                    </div>

                    <div class="lg:col-span-8 bg-white border border-gray-200 rounded-xl p-6 shadow-lg slide-in relative overflow-hidden" id="coverage-visual">
                         <h3 class="font-bold text-lg mb-6 border-b pb-2">CI/CD Pipeline Result</h3>
                         
                         <div class="relative ml-4 space-y-8">
                            <div class="absolute left-[15px] top-4 bottom-4 w-0.5 bg-gray-200 -z-10"></div>
                            
                            <div class="flex items-start gap-4">
                                <div class="w-8 h-8 rounded-full bg-blue-600 text-white flex items-center justify-center shrink-0 shadow-md z-10"><i class="fa-solid fa-code-branch text-sm"></i></div>
                                <div>
                                    <h4 class="font-bold text-gray-800">Code</h4>
                                    <p class="text-sm text-gray-500">PackageFramework <span class="font-mono text-xs bg-gray-100 px-1">master</span></p>
                                    <p class="text-xs text-gray-400 mt-1">Pushed 5 min ago</p>
                                </div>
                            </div>

                            <div class="flex items-start gap-4">
                                <div class="w-8 h-8 rounded-full bg-blue-600 text-white flex items-center justify-center shrink-0 shadow-md z-10"><i class="fa-solid fa-layer-group text-sm"></i></div>
                                <div class="w-full">
                                    <div class="flex justify-between items-center w-full">
                                        <h4 class="font-bold text-gray-800">Build</h4>
                                        <span class="text-xs text-green-600 font-bold">Succeeded</span>
                                    </div>
                                    <p class="text-sm text-gray-500">mobile-tests</p>
                                    <div class="mt-2 bg-gray-900 text-green-400 font-mono text-xs p-2 rounded">
                                        > Tests passed: 154 (100%)<br>
                                        > Coverage: 92%
                                    </div>
                                </div>
                            </div>

                            <div class="flex items-start gap-4">
                                <div class="w-8 h-8 rounded-full bg-blue-600 text-white flex items-center justify-center shrink-0 shadow-md z-10 animate-pulse"><i class="fa-solid fa-globe text-sm"></i></div>
                                <div>
                                    <h4 class="font-bold text-gray-800">Production</h4>
                                    <p class="text-sm text-gray-500">web-deploy</p>
                                    <p class="text-xs text-blue-500 mt-1 font-bold">In Progress...</p>
                                </div>
                            </div>
                         </div>
                    </div>
                `
            },
            {
                id: 4,
                short: "4. Planificación",
                subtitle: "Paso 4: Predicción del Futuro",
                title: "Capacidad vs Realidad",
                script: "Dejen de adivinar. ¿Saben exactamente si su equipo tiene capacidad para probar todo antes del viernes? Azure calcula la capacidad vs la estimación en tiempo real basándose en datos históricos.",
                render: () => `
                    <div class="lg:col-span-12">
                        <p class="text-gray-600 mb-6 text-center max-w-2xl mx-auto">${steps[4].script}</p>
                    </div>
                    
                    <div class="lg:col-span-12 bg-white p-6 rounded-xl shadow border border-gray-200 slide-in">
                        <div class="flex justify-between items-end mb-6 border-b pb-4">
                            <div>
                                <h3 class="text-xl font-bold">Sprint 24 Planning</h3>
                                <p class="text-sm text-gray-400">Oct 14 - Oct 28</p>
                            </div>
                            <div class="text-right">
                                <div class="text-2xl font-bold text-gray-800">124h <span class="text-sm font-normal text-gray-400">/ 160h Total Capacity</span></div>
                            </div>
                        </div>

                        <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                            <div class="bg-gray-50 p-4 rounded-lg">
                                <div class="flex items-center gap-3 mb-2">
                                    <div class="w-10 h-10 rounded-full bg-purple-100 flex items-center justify-center text-purple-600 font-bold">SA</div>
                                    <div>
                                        <div class="font-bold">Santiago Alcaraz</div>
                                        <div class="text-xs text-gray-500">QA Lead</div>
                                    </div>
                                </div>
                                <div class="w-full bg-gray-200 rounded-full h-4 mb-1">
                                    <div class="bg-green-500 h-4 rounded-full" style="width: 75%"></div>
                                </div>
                                <div class="flex justify-between text-xs font-bold text-gray-600">
                                    <span>30h Assigned</span>
                                    <span>40h Capacity</span>
                                </div>
                            </div>

                            <div class="bg-red-50 p-4 rounded-lg border border-red-100">
                                <div class="flex items-center gap-3 mb-2">
                                    <div class="w-10 h-10 rounded-full bg-blue-100 flex items-center justify-center text-blue-600 font-bold">JD</div>
                                    <div>
                                        <div class="font-bold">John Doe</div>
                                        <div class="text-xs text-gray-500">Developer</div>
                                    </div>
                                </div>
                                <div class="w-full bg-gray-200 rounded-full h-4 mb-1 relative">
                                    <div class="bg-green-500 h-4 rounded-l-full absolute" style="width: 80%"></div>
                                    <div class="bg-red-500 h-4 rounded-r-full absolute right-0" style="width: 20%"></div>
                                </div>
                                <div class="flex justify-between text-xs font-bold text-red-600">
                                    <span>52h Assigned (!! Sobrecarga !!)</span>
                                    <span>40h Capacity</span>
                                </div>
                            </div>
                        </div>

                        <div class="mt-8 bg-blue-50 p-4 rounded text-sm text-blue-800 flex items-center gap-2">
                            <i class="fa-solid fa-lightbulb text-yellow-500"></i>
                            <strong>Insight:</strong> Reasignar 12h de John Doe a Santiago equilibrará el Sprint.
                        </div>
                    </div>
                `
            },
            {
                id: 5,
                short: "5. Ejecución",
                subtitle: "Paso 5: Gestión de Incidencias",
                title: "Ejecución Inteligente",
                script: "No más 'en mi máquina funciona'. Cuando un test falla, Azure captura todo. Mira esto: Simulamos la ejecución y creamos el bug al instante.",
                render: () => `
                    <div class="lg:col-span-4">
                        <p class="text-gray-600 mb-4">${steps[5].script}</p>
                        <div class="bg-white p-4 rounded border shadow-sm">
                            <h4 class="font-bold text-sm mb-3">Acciones:</h4>
                            <button onclick="runTestSimulation()" class="w-full bg-green-600 hover:bg-green-700 text-white font-bold py-2 px-4 rounded mb-2 transition flex justify-between items-center">
                                <span><i class="fa-solid fa-play mr-2"></i> Ejecutar Test</span>
                            </button>
                            <p class="text-xs text-gray-400 mt-2">*Simula el fallo en el paso 3</p>
                        </div>
                    </div>

                    <div class="lg:col-span-8 relative slide-in">
                        <div class="bg-white rounded-xl shadow-2xl border border-gray-200 overflow-hidden min-h-[400px]">
                            <div class="bg-gray-800 text-white p-3 flex justify-between items-center">
                                <span class="font-mono text-sm">Microsoft Test Runner</span>
                                <div class="flex gap-2">
                                    <i class="fa-solid fa-camera cursor-pointer hover:text-blue-400"></i>
                                    <i class="fa-solid fa-video cursor-pointer hover:text-blue-400"></i>
                                </div>
                            </div>

                            <div class="p-6 relative">
                                <div class="absolute left-[45px] top-[40px] bottom-[40px] w-0.5 bg-gray-200 z-0"></div>

                                <div class="relative z-10 bg-white p-4 rounded shadow-sm border border-gray-100 mb-4 flex items-center justify-between group step-item">
                                    <div class="flex items-center gap-4">
                                        <div class="w-8 h-8 rounded-full bg-gray-200 text-gray-600 font-bold flex items-center justify-center transition-colors duration-500" id="step-1-icon">1</div>
                                        <span class="text-gray-700 font-medium">Navigate to homepage and log in</span>
                                    </div>
                                    <i class="fa-solid fa-circle-check text-green-500 opacity-0 transition-opacity duration-500" id="step-1-check"></i>
                                </div>

                                <div class="relative z-10 bg-white p-4 rounded shadow-sm border border-gray-100 mb-4 flex items-center justify-between group step-item">
                                    <div class="flex items-center gap-4">
                                        <div class="w-8 h-8 rounded-full bg-gray-200 text-gray-600 font-bold flex items-center justify-center transition-colors duration-500" id="step-2-icon">2</div>
                                        <span class="text-gray-700 font-medium">Navigate to product and add to cart</span>
                                    </div>
                                    <i class="fa-solid fa-circle-check text-green-500 opacity-0 transition-opacity duration-500" id="step-2-check"></i>
                                </div>

                                <div class="relative z-10 bg-white p-4 rounded shadow-sm border border-gray-100 mb-4 flex items-center justify-between group step-item">
                                    <div class="flex items-center gap-4">
                                        <div class="w-8 h-8 rounded-full bg-gray-200 text-gray-600 font-bold flex items-center justify-center transition-colors duration-500" id="step-3-icon">3</div>
                                        <span class="text-gray-700 font-medium" id="step-3-text">Check if cart is populated with Item</span>
                                    </div>
                                    <i class="fa-solid fa-circle-xmark text-red-500 text-xl opacity-0 transition-opacity duration-500" id="step-3-fail"></i>
                                </div>

                                <div id="bug-modal" class="hidden mt-4 bg-red-50 border border-red-200 rounded p-4 slide-in">
                                    <div class="flex items-start gap-3">
                                        <img src="https://i.pravatar.cc/150?u=qa" class="w-10 h-10 rounded-full border-2 border-white shadow">
                                        <div class="flex-1">
                                            <h5 class="font-bold text-red-800 text-sm">Create Bug</h5>
                                            <p class="text-xs text-red-600 mb-2">This results in a 404 once you try to navigate to shopping cart.</p>
                                            <div class="bg-white p-2 text-xs font-mono text-gray-500 border rounded mb-2">
                                                System Info Included: <br>
                                                > Browser: Chrome 119<br>
                                                > OS: Windows 11<br>
                                                > Screenshot: Attached (auto)
                                            </div>
                                            <button class="bg-red-600 text-white text-xs font-bold px-3 py-1 rounded hover:bg-red-700">Save Bug</button>
                                        </div>
                                    </div>
                                </div>

                            </div>
                        </div>
                    </div>
                `
            },
            {
                id: 6,
                short: "6. Dashboard",
                subtitle: "Paso 6: Control de Mando",
                title: "Visibilidad Ejecutiva",
                script: "¿Cuál es el mayor riesgo? Salir a producción con requisitos no probados. Este Dashboard nos dice qué falta probar antes de liberar. Riesgos controlados.",
                render: () => `
                     <div class="lg:col-span-3 flex flex-col justify-center">
                        <p class="text-gray-600 text-sm mb-4">${steps[6].script}</p>
                        <div class="bg-white p-4 shadow rounded border-l-4 border-yellow-400">
                            <div class="text-xs font-bold text-gray-400 uppercase">Alerts</div>
                            <div class="font-bold text-yellow-600 text-lg mt-1">5 Requirements without Tests</div>
                        </div>
                    </div>

                    <div class="lg:col-span-9 grid grid-cols-2 gap-4 slide-in">
                        <div class="bg-white p-4 rounded shadow border border-gray-200 flex flex-col items-center">
                            <h4 class="font-bold text-gray-700 text-sm mb-4 w-full text-left">Test Execution Status</h4>
                            <div class="w-40 h-40 rounded-full border-[16px] border-green-500 border-r-red-500 border-b-gray-200 rotate-45"></div>
                            <div class="flex gap-4 mt-4 text-xs">
                                <span class="flex items-center gap-1"><div class="w-2 h-2 bg-green-500 rounded-full"></div> Passed (70%)</span>
                                <span class="flex items-center gap-1"><div class="w-2 h-2 bg-red-500 rounded-full"></div> Failed (10%)</span>
                                <span class="flex items-center gap-1"><div class="w-2 h-2 bg-gray-300 rounded-full"></div> Not Run (20%)</span>
                            </div>
                        </div>

                        <div class="bg-white p-4 rounded shadow border border-gray-200">
                             <div class="flex justify-between items-center mb-4">
                                <h4 class="font-bold text-gray-700 text-sm">Code Scanning (Security)</h4>
                                <span class="bg-red-100 text-red-600 text-xs px-2 py-1 rounded font-bold">7 High</span>
                             </div>
                             <div class="space-y-3">
                                <div class="flex justify-between items-center text-xs border-b pb-2">
                                    <span class="font-bold text-red-700">Cross-site scripting (XSS)</span>
                                    <span class="text-gray-400">Monday</span>
                                </div>
                                <div class="flex justify-between items-center text-xs border-b pb-2">
                                    <span class="font-bold text-red-700">XML Injection</span>
                                    <span class="text-gray-400">Monday</span>
                                </div>
                                <div class="flex justify-between items-center text-xs border-b pb-2">
                                    <span class="font-bold text-red-700">SQL Injection (Stored)</span>
                                    <span class="text-gray-400">Monday</span>
                                </div>
                                <div class="flex justify-between items-center text-xs pb-2">
                                    <span class="font-bold text-red-700">Insecure Randomness</span>
                                    <span class="text-gray-400">Monday</span>
                                </div>
                             </div>
                        </div>
                    </div>
                `
            }
        ];

        // --- STATE MANAGEMENT ---
        let currentStep = 0;

        // Initialize
        function init() {
            renderSidebar();
            loadStep(0);
        }

        function renderSidebar() {
            const container = document.getElementById('nav-container');
            container.innerHTML = steps.map((s, index) => `
                <button onclick="loadStep(${index})" class="w-full text-left px-6 py-3 text-sm font-medium transition-colors flex items-center justify-between group hover:bg-gray-50 ${index === currentStep ? 'bg-blue-50 border-r-4 border-blue-600 text-blue-700' : 'text-gray-600 border-r-4 border-transparent'}">
                    <span>${s.short}</span>
                    ${index === currentStep ? '<i class="fa-solid fa-chevron-right text-xs"></i>' : ''}
                </button>
            `).join('');
            
            // Add Closing Link
            container.innerHTML += `
                 <button onclick="loadClosing()" id="closing-btn" class="w-full text-left px-6 py-3 text-sm font-bold text-green-700 hover:bg-green-50 transition-colors border-t border-gray-200 mt-2">
                    <i class="fa-solid fa-check-circle mr-2"></i> Cierre
                </button>
            `;
        }

        function loadStep(index) {
            currentStep = index;
            const step = steps[index];
            
            // Update Header
            document.getElementById('header-subtitle').innerText = step.subtitle;
            document.getElementById('header-title').innerText = step.title;
            
            // Update Sidebar Active State
            renderSidebar();

            // Render Content
            document.getElementById('content-stage').innerHTML = step.render();

            // Post-Render Logic (if any specific inits needed)
            if (index === 1) switchMethodology('agile'); // Default for step 1
        }

        function nextStep() {
            if (currentStep < steps.length - 1) {
                loadStep(currentStep + 1);
            } else {
                loadClosing();
            }
        }

        function loadClosing() {
            // Remove active state from sidebar nums
            currentStep = -1; 
            renderSidebar();
            document.getElementById('closing-btn').classList.add('bg-green-100');

            document.getElementById('header-subtitle').innerText = "RESUMEN";
            document.getElementById('header-title').innerText = "La Calidad es una Inversión";
            
            document.getElementById('content-stage').innerHTML = `
                <div class="lg:col-span-12 flex flex-col items-center justify-center text-center h-full slide-in">
                    <div class="w-24 h-24 bg-green-100 text-green-600 rounded-full flex items-center justify-center text-5xl mb-6">
                        <i class="fa-solid fa-shield-halved"></i>
                    </div>
                    <h2 class="text-4xl font-bold mb-4">Gobernanza 360°</h2>
                    <p class="text-xl text-gray-500 max-w-2xl mb-8">
                        Hemos visto cómo cubrir todo el temario (desde modelos hasta riesgos) en una sola plataforma.
                        <br><br>
                        <strong class="text-gray-800">"La calidad no es cara, lo caro es corregir errores en producción."</strong>
                    </p>
                    <button class="bg-blue-600 hover:bg-blue-700 text-white font-bold py-4 px-10 rounded-full shadow-lg transform hover:scale-105 transition">
                        Iniciar Prueba de Concepto (Azure DevOps)
                    </button>
                </div>
            `;
        }

        // --- SPECIFIC LOGIC FUNCTIONS ---

        // Step 1: Methodology Switcher
        function switchMethodology(type) {
            const container = document.getElementById('methodology-visual');
            const btnAgile = document.getElementById('btn-agile');
            const btnWaterfall = document.getElementById('btn-waterfall');

            if (type === 'agile') {
                btnAgile.classList.replace('bg-transparent', 'bg-white');
                btnAgile.classList.replace('text-gray-500', 'text-blue-600');
                btnAgile.classList.add('shadow', 'border-blue-200');
                
                btnWaterfall.classList.replace('bg-white', 'bg-transparent');
                btnWaterfall.classList.replace('text-blue-600', 'text-gray-500');
                btnWaterfall.classList.remove('shadow', 'border-blue-200');

                // Render Kanban
                container.innerHTML = `
                    <div class="flex gap-4 h-full p-2 overflow-x-auto">
                        <div class="w-64 bg-gray-200 rounded p-2 flex flex-col gap-2 shrink-0">
                            <span class="font-bold text-gray-500 text-xs">TO DO</span>
                            <div class="bg-white p-3 rounded shadow-sm border-l-4 border-blue-400 cursor-move">Login Feature</div>
                            <div class="bg-white p-3 rounded shadow-sm border-l-4 border-orange-400 cursor-move">Fix API Timeout</div>
                        </div>
                        <div class="w-64 bg-gray-200 rounded p-2 flex flex-col gap-2 shrink-0">
                            <span class="font-bold text-gray-500 text-xs">IN PROGRESS</span>
                             <div class="bg-white p-3 rounded shadow-sm border-l-4 border-blue-400 cursor-move">
                                Payment Gateway
                                <div class="flex justify-between mt-2"><div class="w-5 h-5 rounded-full bg-purple-200 text-xs flex items-center justify-center">SA</div></div>
                            </div>
                        </div>
                        <div class="w-64 bg-gray-200 rounded p-2 flex flex-col gap-2 shrink-0">
                            <span class="font-bold text-gray-500 text-xs">DONE</span>
                            <div class="bg-white p-3 rounded shadow-sm border-l-4 border-green-400 opacity-70">Setup Repo</div>
                        </div>
                    </div>
                `;
            } else {
                btnWaterfall.classList.replace('bg-transparent', 'bg-white');
                btnWaterfall.classList.replace('text-gray-500', 'text-blue-600');
                btnWaterfall.classList.add('shadow', 'border-blue-200');
                
                btnAgile.classList.replace('bg-white', 'bg-transparent');
                btnAgile.classList.replace('text-blue-600', 'text-gray-500');
                btnAgile.classList.remove('shadow', 'border-blue-200');

                // Render Gantt
                container.innerHTML = `
                    <div class="h-full p-4 overflow-y-auto">
                        <div class="flex border-b pb-2 mb-2 font-bold text-xs text-gray-400">
                            <div class="w-1/3">Task</div>
                            <div class="w-2/3">Timeline (Q4 2025)</div>
                        </div>
                        <div class="flex items-center mb-4">
                            <div class="w-1/3 text-sm font-bold text-gray-700">1. Analysis</div>
                            <div class="w-2/3 bg-gray-200 h-6 rounded relative">
                                <div class="absolute left-0 w-1/3 bg-blue-600 h-full rounded text-white text-xs flex items-center pl-2">Completed</div>
                            </div>
                        </div>
                         <div class="flex items-center mb-4">
                            <div class="w-1/3 text-sm font-bold text-gray-700">2. Development</div>
                            <div class="w-2/3 bg-gray-200 h-6 rounded relative">
                                <div class="absolute left-1/4 w-1/2 bg-blue-400 h-full rounded text-white text-xs flex items-center pl-2">In Progress</div>
                            </div>
                        </div>
                         <div class="flex items-center mb-4">
                            <div class="w-1/3 text-sm font-bold text-gray-700">3. Testing</div>
                            <div class="w-2/3 bg-gray-200 h-6 rounded relative">
                                <div class="absolute left-3/4 w-1/4 bg-gray-400 h-full rounded opacity-50"></div>
                            </div>
                        </div>
                    </div>
                `;
            }
        }

        // Step 3: Coverage Switcher
        function showCoverage(type) {
            const container = document.getElementById('coverage-visual');
            
            if(type === 'blackbox') {
                container.innerHTML = `
                    <h3 class="font-bold text-lg mb-6 border-b pb-2">Manual Test Plan (Human Validation)</h3>
                    <div class="space-y-4">
                        <div class="flex justify-between items-center bg-gray-50 p-3 rounded border border-gray-100">
                            <span class="font-bold text-gray-700">Test Suite: User Acceptance</span>
                            <span class="text-xs bg-blue-100 text-blue-800 px-2 py-1 rounded">Active</span>
                        </div>
                        
                        <div class="pl-4 border-l-2 border-gray-200 space-y-3">
                             <div class="flex gap-3 items-center">
                                <input type="checkbox" checked class="w-5 h-5 text-blue-600">
                                <span class="text-gray-600 line-through">Verify Login Page loads</span>
                             </div>
                             <div class="flex gap-3 items-center">
                                <input type="checkbox" class="w-5 h-5 text-blue-600">
                                <span class="text-gray-800 font-bold">Verify 'Forgot Password' email trigger</span>
                             </div>
                             <div class="bg-yellow-50 p-3 rounded text-sm text-gray-600">
                                <i class="fa-solid fa-comment-dots text-yellow-500 mr-2"></i> Note for Tester: Check spam folder too.
                             </div>
                        </div>
                    </div>
                `;
            } else {
                // Restore Whitebox (The Pipeline)
                // Simply reloading the step logic for ease
                container.innerHTML = `
                    <h3 class="font-bold text-lg mb-6 border-b pb-2">CI/CD Pipeline Result</h3>
                         <div class="relative ml-4 space-y-8">
                            <div class="absolute left-[15px] top-4 bottom-4 w-0.5 bg-gray-200 -z-10"></div>
                            <div class="flex items-start gap-4">
                                <div class="w-8 h-8 rounded-full bg-blue-600 text-white flex items-center justify-center shrink-0 shadow-md z-10"><i class="fa-solid fa-code-branch text-sm"></i></div>
                                <div>
                                    <h4 class="font-bold text-gray-800">Code</h4>
                                    <p class="text-sm text-gray-500">PackageFramework <span class="font-mono text-xs bg-gray-100 px-1">master</span></p>
                                </div>
                            </div>
                            <div class="flex items-start gap-4">
                                <div class="w-8 h-8 rounded-full bg-blue-600 text-white flex items-center justify-center shrink-0 shadow-md z-10"><i class="fa-solid fa-layer-group text-sm"></i></div>
                                <div class="w-full">
                                    <div class="flex justify-between items-center w-full">
                                        <h4 class="font-bold text-gray-800">Build</h4>
                                        <span class="text-xs text-green-600 font-bold">Succeeded</span>
                                    </div>
                                    <div class="mt-2 bg-gray-900 text-green-400 font-mono text-xs p-2 rounded">
                                        > Tests passed: 154 (100%)
                                    </div>
                                </div>
                            </div>
                            <div class="flex items-start gap-4">
                                <div class="w-8 h-8 rounded-full bg-blue-600 text-white flex items-center justify-center shrink-0 shadow-md z-10 animate-pulse"><i class="fa-solid fa-globe text-sm"></i></div>
                                <div>
                                    <h4 class="font-bold text-gray-800">Production</h4>
                                    <p class="text-xs text-blue-500 mt-1 font-bold">In Progress...</p>
                                </div>
                            </div>
                         </div>
                `;
            }
        }

        // Step 5: Test Runner Simulation
        function runTestSimulation() {
            // Step 1 pass
            setTimeout(() => {
                document.getElementById('step-1-icon').classList.replace('bg-gray-200', 'bg-green-100');
                document.getElementById('step-1-icon').classList.replace('text-gray-600', 'text-green-600');
                document.getElementById('step-1-icon').innerHTML = '<i class="fa-solid fa-check"></i>';
                document.getElementById('step-1-check').classList.replace('opacity-0', 'opacity-100');
            }, 500);

            // Step 2 pass
            setTimeout(() => {
                document.getElementById('step-2-icon').classList.replace('bg-gray-200', 'bg-green-100');
                document.getElementById('step-2-icon').classList.replace('text-gray-600', 'text-green-600');
                document.getElementById('step-2-icon').innerHTML = '<i class="fa-solid fa-check"></i>';
                document.getElementById('step-2-check').classList.replace('opacity-0', 'opacity-100');
            }, 1200);

            // Step 3 FAIL
            setTimeout(() => {
                document.getElementById('step-3-icon').classList.replace('bg-gray-200', 'bg-red-100');
                document.getElementById('step-3-icon').classList.replace('text-gray-600', 'text-red-600');
                document.getElementById('step-3-icon').innerHTML = '<i class="fa-solid fa-xmark"></i>';
                document.getElementById('step-3-fail').classList.replace('opacity-0', 'opacity-100');
                document.getElementById('step-3-text').classList.add('text-red-600', 'font-bold');
            }, 2000);

            // Open Bug Modal
            setTimeout(() => {
                document.getElementById('bug-modal').classList.remove('hidden');
            }, 2500);
        }

        // Start App
        init();

    </script>
</body>
</html>
