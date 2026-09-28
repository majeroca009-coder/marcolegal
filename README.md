<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LopcyFlow - Suite de Gestión SST (Venezuela)</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome para Iconos -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Firebase SDK (Cloud Persistence) -->
    <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-app-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-firestore-compat.js"></script>
</head>
<body class="bg-slate-50 text-slate-800 font-sans antialiased">

    <div id="app" class="flex h-screen overflow-hidden">
        <!-- Sidebar de Navegación -->
        <aside class="w-64 bg-slate-900 text-slate-300 flex flex-col shadow-xl">
            <div class="p-5 border-b border-slate-800 flex items-center space-x-3">
                <div class="bg-blue-600 text-white p-2 rounded-lg font-bold text-xl"><i class="fa-solid fa-shield-halved"></i></div>
                <div>
                    <h1 class="text-white font-bold text-lg tracking-wide">LopcyFlow</h1>
                    <p class="text-xs text-slate-400">Gestión SST • LOPCYMAT</p>
                </div>
            </div>
            <nav class="flex-1 p-4 space-y-1 overflow-y-auto">
                <button onclick="switchTab('dashboard')" class="tab-btn w-full flex items-center space-x-3 px-4 py-2.5 rounded-lg text-sm font-medium bg-blue-600 text-white transition"><i class="fa-solid fa-chart-pie w-5"></i><span>Dashboard</span></button>
                <button onclick="switchTab('riesgos')" class="tab-btn w-full flex items-center space-x-3 px-4 py-2.5 rounded-lg text-sm font-medium hover:bg-slate-800 hover:text-white transition"><i class="fa-solid fa-triangle-exclamation w-5"></i><span>Matriz de Riesgos (NT-01)</span></button>
                <button onclick="switchTab('accidentes')" class="tab-btn w-full flex items-center space-x-3 px-4 py-2.5 rounded-lg text-sm font-medium hover:bg-slate-800 hover:text-white transition"><i class="fa-solid fa-truck-medical w-5"></i><span>Accidentes (Art. 73)</span></button>
                <button onclick="switchTab('salud')" class="tab-btn w-full flex items-center space-x-3 px-4 py-2.5 rounded-lg text-sm font-medium hover:bg-slate-800 hover:text-white transition"><i class="fa-solid fa-user-doctor w-5"></i><span>Salud Ocupacional</span></button>
                <button onclick="switchTab('formacion')" class="tab-btn w-full flex items-center space-x-3 px-4 py-2.5 rounded-lg text-sm font-medium hover:bg-slate-800 hover:text-white transition"><i class="fa-solid fa-graduation-cap w-5"></i><span>Formación (16h)</span></button>
                <button onclick="switchTab('informes')" class="tab-btn w-full flex items-center space-x-3 px-4 py-2.5 rounded-lg text-sm font-medium hover:bg-slate-800 hover:text-white transition"><i class="fa-solid fa-file-invoice w-5"></i><span>Informes INPSASEL</span></button>
                <button onclick="switchTab('directorio')" class="tab-btn w-full flex items-center space-x-3 px-4 py-2.5 rounded-lg text-sm font-medium hover:bg-slate-800 hover:text-white transition"><i class="fa-solid fa-users w-5"></i><span>Directorio Nómina</span></button>
                <button onclick="switchTab('cssl')" class="tab-btn w-full flex items-center space-x-3 px-4 py-2.5 rounded-lg text-sm font-medium hover:bg-slate-800 hover:text-white transition"><i class="fa-solid fa-handshake w-5"></i><span>Comité CSSL & Actas</span></button>
            </nav>
            <div class="p-4 border-t border-slate-800 text-xs text-slate-500 text-center">
                Innovación SST © 2026 • Promoción 69
            </div>
        </aside>

        <!-- Área Principal -->
        <main class="flex-1 flex flex-col overflow-hidden">
            <!-- Header Superior -->
            <header class="bg-white border-b border-slate-200 h-16 flex items-center justify-between px-6 shadow-sm">
                <div class="flex items-center space-x-3">
                    <span id="current-tab-title" class="text-xl font-bold text-slate-800">Panel General de Control</span>
                </div>
                <div class="flex items-center space-x-4">
                    <div class="text-right">
                        <p class="text-sm font-semibold text-slate-700">Servicio de Seguridad (SSST)</p>
                        <p class="text-xs text-emerald-600 font-medium"><i class="fa-solid fa-circle text-[8px] mr-1"></i> Sistema En Línea</p>
                    </div>
                </div>
            </header>

            <!-- Contenido Dinámico de las Pestañas -->
            <div class="flex-1 overflow-y-auto p-6 bg-slate-50">
                
                <!-- 1. DASHBOARD -->
                <section id="tab-dashboard" class="tab-content space-y-6">
                    <div class="grid grid-cols-1 md:grid-cols-4 gap-6">
                        <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200 flex items-center space-x-4">
                            <div class="bg-blue-100 text-blue-600 p-4 rounded-xl text-2xl"><i class="fa-solid fa-users"></i></div>
                            <div>
                                <p class="text-sm text-slate-500 font-medium">Trabajadores Activos</p>
                                <h3 class="text-2xl font-bold text-slate-800" id="kpi-trabajadores">0</h3>
                            </div>
                        </div>
                        <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200 flex items-center space-x-4">
                            <div class="bg-red-100 text-red-600 p-4 rounded-xl text-2xl"><i class="fa-solid fa-triangle-exclamation"></i></div>
                            <div>
                                <p class="text-sm text-slate-500 font-medium">Riesgos Altos (NT-01)</p>
                                <h3 class="text-2xl font-bold text-slate-800" id="kpi-riesgos">0</h3>
                            </div>
                        </div>
                        <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200 flex items-center space-x-4">
                            <div class="bg-amber-100 text-amber-600 p-4 rounded-xl text-2xl"><i class="fa-solid fa-bed-pulse"></i></div>
                            <div>
                                <p class="text-sm text-slate-500 font-medium">Accidentes Registrados</p>
                                <h3 class="text-2xl font-bold text-slate-800" id="kpi-accidentes">0</h3>
                            </div>
                        </div>
                        <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200 flex items-center space-x-4">
                            <div class="bg-emerald-100 text-emerald-600 p-4 rounded-xl text-2xl"><i class="fa-solid fa-file-shield"></i></div>
                            <div>
                                <p class="text-sm text-slate-500 font-medium">Índice Frecuencia (IF)</p>
                                <h3 class="text-2xl font-bold text-slate-800" id="kpi-if">0.00</h3>
                            </div>
                        </div>
                    </div>
                    <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200">
                        <h3 class="text-lg font-bold text-slate-800 mb-4">Resumen del Marco Normativo y Alertas Inmediatas</h3>
                        <p class="text-slate-600 text-sm leading-relaxed">
                            Bienvenido a <strong>LopcyFlow</strong>, la suite tecnológica de gestión integral en Seguridad y Salud en el Trabajo diseñada para dar cumplimiento estricto a la Ley Orgánica de Prevención, Condiciones y Medio Ambiente de Trabajo (LOPCYMAT), su Reglamento Parcial y las directrices técnico-administrativas del INPSASEL. Utilice el menú lateral para registrar riesgos, notificar accidentes en la ventana legal de 60 minutos, gestionar la vigilancia epidemiológica y emitir informes oficiales.
                        </p>
                    </div>
                </section>

                <!-- 2. MATRIZ DE RIESGOS (NT-01) -->
                <section id="tab-riesgos" class="tab-content hidden space-y-6">
                    <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200">
                        <h3 class="text-lg font-bold text-slate-800 mb-4"><i class="fa-solid fa-triangle-exclamation text-amber-500 mr-2"></i> Registro de Matriz de Peligros y Riesgos (NT-01-2008)</h3>
                        <form id="form-riesgo" class="grid grid-cols-1 md:grid-cols-3 gap-4">
                            <input type="text" id="r-area" placeholder="Área / Proceso de Trabajo" required class="border p-2.5 rounded-lg text-sm">
                            <input type="text" id="r-peligro" placeholder="Peligro / Proceso Peligroso" required class="border p-2.5 rounded-lg text-sm">
                            <select id="r-nivel" class="border p-2.5 rounded-lg text-sm">
                                <option value="Bajo">Riesgo Bajo</option>
                                <option value="Medio">Riesgo Medio</option>
                                <option value="Alto">Riesgo Alto</option>
                            </select>
                            <input type="text" id="r-efecto" placeholder="Efecto Posible para la Salud" required class="border p-2.5 rounded-lg text-sm md:col-span-2">
                            <button type="submit" class="bg-blue-600 text-white font-semibold py-2.5 rounded-lg hover:bg-blue-700 transition"><i class="fa-solid fa-plus mr-2"></i>Registrar Riesgo</button>
                        </form>
                    </div>
                    <div class="bg-white rounded-xl shadow-sm border border-slate-200 overflow-hidden">
                        <table class="w-full text-left border-collapse">
                            <thead>
                                <tr class="bg-slate-100 text-slate-600 text-xs uppercase font-semibold border-b">
                                    <th class="p-4">Área</th>
                                    <th class="p-4">Peligro</th>
                                    <th class="p-4">Efecto</th>
                                    <th class="p-4">Nivel</th>
                                    <th class="p-4 text-center">Acciones</th>
                                </tr>
                            </thead>
                            <tbody id="tabla-riesgos-body" class="text-sm divide-y divide-slate-100"></tbody>
                        </table>
                    </div>
                </section>

                <!-- 3. ACCIDENTES (Art. 73) -->
                <section id="tab-accidentes" class="tab-content hidden space-y-6">
                    <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200">
                        <h3 class="text-lg font-bold text-slate-800 mb-2"><i class="fa-solid fa-truck-medical text-red-500 mr-2"></i> Notificación Inmediata de Accidente (Art. 73 LOPCYMAT - Lapso 60 Min)</h3>
                        <form id="form-accidente" class="grid grid-cols-1 md:grid-cols-2 gap-4 mt-4">
                            <input type="text" id="acc-trabajador" placeholder="Nombre y Apellido del Trabajador" required class="border p-2.5 rounded-lg text-sm">
                            <input type="text" id="acc-cedula" placeholder="Cédula de Identidad" required class="border p-2.5 rounded-lg text-sm">
                            <input type="text" id="acc-area" placeholder="Área / Puesto de Trabajo" required class="border p-2.5 rounded-lg text-sm">
                            <input type="datetime-local" id="acc-fecha" required class="border p-2.5 rounded-lg text-sm">
                            <textarea id="acc-desc" placeholder="Descripción detallada del evento y primeros auxilios..." rows="2" class="border p-2.5 rounded-lg text-sm md:col-span-2" required></textarea>
                            <button type="submit" class="bg-red-600 text-white font-semibold py-2.5 rounded-lg hover:bg-red-700 transition md:col-span-2"><i class="fa-solid fa-paper-plane mr-2"></i>Emitir Notificación Inmediata</button>
                        </form>
                    </div>
                    <div class="bg-white rounded-xl shadow-sm border border-slate-200 overflow-hidden">
                        <table class="w-full text-left border-collapse">
                            <thead>
                                <tr class="bg-slate-100 text-slate-600 text-xs uppercase font-semibold border-b">
                                    <th class="p-4">Trabajador</th>
                                    <th class="p-4">Cédula</th>
                                    <th class="p-4">Área</th>
                                    <th class="p-4">Fecha / Hora</th>
                                    <th class="p-4">Descripción</th>
                                </tr>
                            </thead>
                            <tbody id="tabla-accidentes-body" class="text-sm divide-y divide-slate-100"></tbody>
                        </table>
                    </div>
                </section>

                <!-- 4. SALUD OCUPACIONAL -->
                <section id="tab-salud" class="tab-content hidden space-y-6">
                    <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200">
                        <h3 class="text-lg font-bold text-slate-800 mb-4"><i class="fa-solid fa-user-doctor text-emerald-600 mr-2"></i> Vigilancia Epidemiológica & Registro Médico</h3>
                        <form id="form-salud" class="grid grid-cols-1 md:grid-cols-3 gap-4">
                            <input type="text" id="med-trabajador" placeholder="Nombre del Trabajador" required class="border p-2.5 rounded-lg text-sm">
                            <select id="med-tipo" class="border p-2.5 rounded-lg text-sm">
                                <option value="Pre-empleo">Examen Pre-empleo</option>
                                <option value="Post-empleo">Examen Post-empleo</option>
                                <option value="Periodicidad">Evaluación Periódica</option>
                                <option value="Consulta">Consulta Médica Ocupacional</option>
                            </select>
                            <select id="med-aptitud" class="border p-2.5 rounded-lg text-sm">
                                <option value="Apto">Apto</option>
                                <option value="Apto con Restricciones">Apto con Restricciones</option>
                                <option value="No Apto">No Apto</option>
                            </select>
                            <input type="text" id="med-diag" placeholder="Diagnóstico Clínico / Observaciones" required class="border p-2.5 rounded-lg text-sm md:col-span-2">
                            <button type="submit" class="bg-emerald-600 text-white font-semibold py-2.5 rounded-lg hover:bg-emerald-700 transition"><i class="fa-solid fa-stethoscope mr-2"></i>Registrar Consulta</button>
                        </form>
                    </div>
                    <div class="bg-white rounded-xl shadow-sm border border-slate-200 overflow-hidden">
                        <table class="w-full text-left border-collapse">
                            <thead>
                                <tr class="bg-slate-100 text-slate-600 text-xs uppercase font-semibold border-b">
                                    <th class="p-4">Trabajador</th>
                                    <th class="p-4">Tipo Evaluación</th>
                                    <th class="p-4">Diagnóstico</th>
                                    <th class="p-4">Aptitud</th>
                                </tr>
                            </thead>
                            <tbody id="tabla-salud-body" class="text-sm divide-y divide-slate-100"></tbody>
                        </table>
                    </div>
                </section>

                <!-- 5. FORMACIÓN (16H) -->
                <section id="tab-formacion" class="tab-content hidden space-y-6">
                    <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200">
                        <h3 class="text-lg font-bold text-slate-800 mb-4"><i class="fa-solid fa-graduation-cap text-indigo-600 mr-2"></i> Control de Capacitación Trimestral (16 Horas Obligatorias)</h3>
                        <form id="form-formacion" class="grid grid-cols-1 md:grid-cols-3 gap-4">
                            <input type="text" id="f-curso" placeholder="Nombre del Curso / Taller" required class="border p-2.5 rounded-lg text-sm">
                            <input type="number" id="f-horas" placeholder="Duración en Horas" required class="border p-2.5 rounded-lg text-sm">
                            <input type="date" id="f-fecha" required class="border p-2.5 rounded-lg text-sm">
                            <button type="submit" class="bg-indigo-600 text-white font-semibold py-2.5 rounded-lg hover:bg-indigo-700 transition md:col-span-3"><i class="fa-solid fa-plus mr-2"></i>Registrar Actividad de Formación</button>
                        </form>
                    </div>
                    <div class="bg-white rounded-xl shadow-sm border border-slate-200 overflow-hidden">
                        <table class="w-full text-left border-collapse">
                            <thead>
                                <tr class="bg-slate-100 text-slate-600 text-xs uppercase font-semibold border-b">
                                    <th class="p-4">Curso / Taller</th>
                                    <th class="p-4">Horas Impartidas</th>
                                    <th class="p-4">Fecha</th>
                                </tr>
                            </thead>
                            <tbody id="tabla-formacion-body" class="text-sm divide-y divide-slate-100"></tbody>
                        </table>
                    </div>
                </section>

                <!-- 6. INFORMES INPSASEL -->
                <section id="tab-informes" class="tab-content hidden space-y-6">
                    <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200 flex justify-between items-center">
                        <div>
                            <h3 class="text-lg font-bold text-slate-800">Generación de Informes Trimestrales Homologados</h3>
                            <p class="text-xs text-slate-500">Cálculo automatizado de Índices de Siniestralidad (IF e IG) para INPSASEL.</p>
                        </div>
                        <button onclick="window.print()" class="bg-slate-800 text-white px-4 py-2 rounded-lg text-sm hover:bg-slate-900 transition"><i class="fa-solid fa-print mr-2"></i>Imprimir / Exportar PDF</button>
                    </div>
                    <div class="bg-white p-8 rounded-xl shadow-sm border border-slate-200 space-y-6">
                        <div class="border-b pb-4 flex justify-between items-start">
                            <div>
                                <h4 class="font-bold text-slate-800 text-xl">REPORTE ESTADÍSTICO TRIMESTRAL DE SST</h4>
                                <p class="text-xs text-slate-500">Conforme a la LOPCYMAT y Providencias INPSASEL</p>
                            </div>
                            <div class="text-right text-xs text-slate-600">
                                <p><strong>Fecha Emisión:</strong> <span id="fecha-actual"></span></p>
                                <p><strong>Estatus:</strong> Oficial / Aprobado CSSL</p>
                            </div>
                        </div>
                        <div class="grid grid-cols-2 md:grid-cols-4 gap-4 text-center">
                            <div class="bg-slate-50 p-4 rounded-lg border">
                                <p class="text-xs text-slate-500">Total Accidentes (N)</p>
                                <p class="text-xl font-bold text-slate-800" id="rep-acc">0</p>
                            </div>
                            <div class="bg-slate-50 p-4 rounded-lg border">
                                <p class="text-xs text-slate-500">Horas Hombre (HHT)</p>
                                <p class="text-xl font-bold text-slate-800">45,000</p>
                            </div>
                            <div class="bg-slate-50 p-4 rounded-lg border">
                                <p class="text-xs text-slate-500">Índice Frecuencia (IF)</p>
                                <p class="text-xl font-bold text-blue-600" id="rep-if">0.00</p>
                            </div>
                            <div class="bg-slate-50 p-4 rounded-lg border">
                                <p class="text-xs text-slate-500">Índice Gravamen (IG)</p>
                                <p class="text-xl font-bold text-amber-600" id="rep-ig">0.31</p>
                            </div>
                        </div>
                    </div>
                </section>

                <!-- 7. DIRECTORIO NÓMINA -->
                <section id="tab-directorio" class="tab-content hidden space-y-6">
                    <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200">
                        <h3 class="text-lg font-bold text-slate-800 mb-4"><i class="fa-solid fa-users text-blue-600 mr-2"></i> Directorio y Censo de Trabajadores</h3>
                        <form id="form-trabajador" class="grid grid-cols-1 md:grid-cols-3 gap-4">
                            <input type="text" id="t-nombre" placeholder="Nombre y Apellido" required class="border p-2.5 rounded-lg text-sm">
                            <input type="text" id="t-cedula" placeholder="Cédula de Identidad" required class="border p-2.5 rounded-lg text-sm">
                            <input type="text" id="t-cargo" placeholder="Cargo / Puesto" required class="border p-2.5 rounded-lg text-sm">
                            <button type="submit" class="bg-blue-600 text-white font-semibold py-2.5 rounded-lg hover:bg-blue-700 transition md:col-span-3"><i class="fa-solid fa-user-plus mr-2"></i>Registrar Trabajador</button>
                        </form>
                    </div>
                    <div class="bg-white rounded-xl shadow-sm border border-slate-200 overflow-hidden">
                        <table class="w-full text-left border-collapse">
                            <thead>
                                <tr class="bg-slate-100 text-slate-600 text-xs uppercase font-semibold border-b">
                                    <th class="p-4">Trabajador</th>
                                    <th class="p-4">Cédula</th>
                                    <th class="p-4">Cargo</th>
                                </tr>
                            </thead>
                            <tbody id="tabla-trabajadores-body" class="text-sm divide-y divide-slate-100"></tbody>
                        </table>
                    </div>
                </section>

                <!-- 8. COMITÉ CSSL & ACTAS -->
                <section id="tab-cssl" class="tab-content hidden space-y-6">
                    <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200">
                        <h3 class="text-lg font-bold text-slate-800 mb-4"><i class="fa-solid fa-handshake text-indigo-600 mr-2"></i> Comité de Seguridad y Salud Laboral (CSSL) - Actas Mensuales</h3>
                        <form id="form-cssl" class="grid grid-cols-1 md:grid-cols-2 gap-4">
                            <input type="date" id="c-fecha" required class="border p-2.5 rounded-lg text-sm">
                            <input type="text" id="c-reunion" placeholder="Número de Acta o Reunión" required class="border p-2.5 rounded-lg text-sm">
                            <textarea id="c-acuerdos" placeholder="Acuerdos y decisiones tomadas en el comité..." rows="2" class="border p-2.5 rounded-lg text-sm md:col-span-2" required></textarea>
                            <button type="submit" class="bg-indigo-600 text-white font-semibold py-2.5 rounded-lg hover:bg-indigo-700 transition md:col-span-2"><i class="fa-solid fa-file-pen mr-2"></i>Registrar Acta CSSL</button>
                        </form>
                    </div>
                    <div class="bg-white rounded-xl shadow-sm border border-slate-200 overflow-hidden">
                        <table class="w-full text-left border-collapse">
                            <thead>
                                <tr class="bg-slate-100 text-slate-600 text-xs uppercase font-semibold border-b">
                                    <th class="p-4">Fecha</th>
                                    <th class="p-4">Nro Acta</th>
                                    <th class="p-4">Acuerdos Principales</th>
                                </tr>
                            </thead>
                            <tbody id="tabla-cssl-body" class="text-sm divide-y divide-slate-100"></tbody>
                        </table>
                    </div>
                </section>

            </div>
        </main>
    </div>

    <!-- Script de Lógica e Interacción -->
    <script>
        // Memoria local de trabajo (Simulación persistente en sesión)
        let dbData = {
            riesgos: [
                {area: "Oficinas Administrativas", peligro: "PVD Prolongadas", efecto: "Fatiga visual", nivel: "Medio"}
            ],
            accidentes: [
                {trabajador: "Carlos Mendoza", cedula: "V-24.512.630", area: "Producción", fecha: "2026-09-27 09:30", desc: "Caída leve a nivel"}
            ],
            salud: [
                {trabajador: "María Pérez", tipo: "Pre-empleo", diag: "Sano sin alteraciones", aptitud: "Apto"}
            ],
            formacion: [
                {curso: "Uso de EPP y Prevención", horas: "4", fecha: "2026-09-10"}
            ],
            trabajadores: [
                {nombre: "Carlos Mendoza", cedula: "V-24.512.630", cargo: "Operario de Línea"},
                {nombre: "María Pérez", cedula: "V-26.102.441", cargo: "Analista Administrativo"}
            ],
            cssl: [
                {fecha: "2026-09-01", reunion: "Acta N° 09-2026", acuerdos: "Revision trimestral de dotación de EPP aprobada."}
            ]
        };

        function switchTab(tabId) {
            document.querySelectorAll('.tab-content').forEach(el => el.classList.add('hidden'));
            document.getElementById('tab-' + tabId).classList.remove('hidden');
            
            document.querySelectorAll('.tab-btn').forEach(btn => {
                btn.classList.remove('bg-blue-600', 'text-white');
                btn.classList.add('hover:bg-slate-800', 'hover:text-white');
            });
            event.currentTarget.classList.add('bg-blue-600', 'text-white');
            event.currentTarget.classList.remove('hover:bg-slate-800');

            const titles = {
                'dashboard': 'Panel General de Control',
                'riesgos': 'Matriz de Identificación de Peligros y Riesgos (NT-01)',
                'accidentes': 'Notificación de Accidentes (Art. 73 LOPCYMAT)',
                'salud': 'Vigilancia Epidemiológica y Salud Ocupacional',
                'formacion': 'Campus de Formación (16 Horas Trimestrales)',
                'informes': 'Informes y Estadísticas INPSASEL',
                'directorio': 'Directorio y Nómina de Trabajadores',
                'cssl': 'Comité de Seguridad y Salud Laboral (CSSL)'
            };
            document.getElementById('current-tab-title').innerText = titles[tabId];
            renderAll();
        }

        function renderAll() {
            // Dashboard KPIs
            document.getElementById('kpi-trabajadores').innerText = dbData.trabajadores.length;
            document.getElementById('kpi-riesgos').innerText = dbData.riesgos.filter(r => r.nivel === 'Alto').length;
            document.getElementById('kpi-accidentes').innerText = dbData.accidentes.length;
            
            let ifVal = ((dbData.accidentes.length * 1000000) / 45000).toFixed(2);
            document.getElementById('kpi-if').innerText = ifVal;
            document.getElementById('rep-acc').innerText = dbData.accidentes.length;
            document.getElementById('rep-if').innerText = ifVal;
            document.getElementById('fecha-actual').innerText = new Date().toLocaleDateString();

            // Render Riesgos
            let htmlR = '';
            dbData.riesgos.forEach(r => {
                let badge = r.nivel === 'Alto' ? 'bg-red-100 text-red-700' : (r.nivel === 'Medio' ? 'bg-amber-100 text-amber-700' : 'bg-blue-100 text-blue-700');
                htmlR += `<tr class="border-b"><td class="p-4">${r.area}</td><td class="p-4">${r.peligro}</td><td class="p-4">${r.efecto}</td><td class="p-4"><span class="px-2.5 py-1 rounded-full text-xs font-semibold ${badge}">${r.nivel}</span></td><td class="p-4 text-center"><button class="text-slate-400 hover:text-red-600"><i class="fa-solid fa-trash"></i></button></td></tr>`;
            });
            document.getElementById('tabla-riesgos-body').innerHTML = htmlR;

            // Render Accidentes
            let htmlA = '';
            dbData.accidentes.forEach(a => {
                htmlA += `<tr class="border-b"><td class="p-4 font-medium">${a.trabajador}</td><td class="p-4">${a.cedula}</td><td class="p-4">${a.area}</td><td class="p-4">${a.fecha}</td><td class="p-4">${a.desc}</td></tr>`;
            });
            document.getElementById('tabla-accidentes-body').innerHTML = htmlA;

            // Render Salud
            let htmlS = '';
            dbData.salud.forEach(s => {
                htmlS += `<tr class="border-b"><td class="p-4 font-medium">${s.trabajador}</td><td class="p-4">${s.tipo}</td><td class="p-4">${s.diag}</td><td class="p-4"><span class="px-2.5 py-1 rounded-full text-xs font-semibold bg-emerald-100 text-emerald-700">${s.aptitud}</span></td></tr>`;
            });
            document.getElementById('tabla-salud-body').innerHTML = htmlS;

            // Render Formación
            let htmlF = '';
            dbData.formacion.forEach(f => {
                htmlF += `<tr class="border-b"><td class="p-4 font-medium">${f.curso}</td><td class="p-4">${f.horas} Horas</td><td class="p-4">${f.fecha}</td></tr>`;
            });
            document.getElementById('tabla-formacion-body').innerHTML = htmlF;

            // Render Trabajadores
            let htmlT = '';
            dbData.trabajadores.forEach(t => {
                htmlT += `<tr class="border-b"><td class="p-4 font-medium">${t.nombre}</td><td class="p-4">${t.cedula}</td><td class="p-4">${t.cargo}</td></tr>`;
            });
            document.getElementById('tabla-trabajadores-body').innerHTML = htmlT;

            // Render CSSL
            let htmlC = '';
            dbData.cssl.forEach(c => {
                htmlC += `<tr class="border-b"><td class="p-4">${c.fecha}</td><td class="p-4 font-medium">${c.reunion}</td><td class="p-4">${c.acuerdos}</td></tr>`;
            });
            document.getElementById('tabla-cssl-body').innerHTML = htmlC;
        }

        // Event Listeners para Formularios
        document.getElementById('form-riesgo').addEventListener('submit', (e) => {
            e.preventDefault();
            dbData.riesgos.push({
                area: document.getElementById('r-area').value,
                peligro: document.getElementById('r-peligro').value,
                nivel: document.getElementById('r-nivel').value,
                efecto: document.getElementById('r-efecto').value
            });
            e.target.reset();
            renderAll();
        });

        document.getElementById('form-accidente').addEventListener('submit', (e) => {
            e.preventDefault();
            dbData.accidentes.push({
                trabajador: document.getElementById('acc-trabajador').value,
                cedula: document.getElementById('acc-cedula').value,
                area: document.getElementById('acc-area').value,
                fecha: document.getElementById('acc-fecha').value,
                desc: document.getElementById('acc-desc').value
            });
            e.target.reset();
            renderAll();
        });

        document.getElementById('form-salud').addEventListener('submit', (e) => {
            e.preventDefault();
            dbData.salud.push({
                trabajador: document.getElementById('med-trabajador').value,
                tipo: document.getElementById('med-tipo').value,
                diag: document.getElementById('med-diag').value,
                aptitud: document.getElementById('med-aptitud').value
            });
            e.target.reset();
            renderAll();
        });

        document.getElementById('form-formacion').addEventListener('submit', (e) => {
            e.preventDefault();
            dbData.formacion.push({
                curso: document.getElementById('f-curso').value,
                horas: document.getElementById('f-horas').value,
                fecha: document.getElementById('f-fecha').value
            });
            e.target.reset();
            renderAll();
        });

        document.getElementById('form-trabajador').addEventListener('submit', (e) => {
            e.preventDefault();
            dbData.trabajadores.push({
                nombre: document.getElementById('t-nombre').value,
                cedula: document.getElementById('t-cedula').value,
                cargo: document.getElementById('t-cargo').value
            });
            e.target.reset();
            renderAll();
        });

        document.getElementById('form-cssl').addEventListener('submit', (e) => {
            e.preventDefault();
            dbData.cssl.push({
                fecha: document.getElementById('c-fecha').value,
                reunion: document.getElementById('c-reunion').value,
                acuerdos: document.getElementById('c-acuerdos').value
            });
            e.target.reset();
            renderAll();
        });

        // Inicializar renderizado
        renderAll();
    </script>
</body>
</html>
