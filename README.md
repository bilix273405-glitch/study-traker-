<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no, viewport-fit=cover">
    <title>PCB Master Tracker 2027</title>
    <!-- Tailwind CSS for UI -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        /* Mobile App Native Feel Styles */
        body {
            -webkit-tap-highlight-color: transparent;
            user-select: none;
            -webkit-user-select: none;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
        }
        .scrollbar-hide::-webkit-scrollbar {
            display: none;
        }
        .scrollbar-hide {
            -ms-overflow-style: none;
            scrollbar-width: none;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(8px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .animate-fade-in {
            animation: fadeIn 0.25s ease-out forwards;
        }
    </style>
</head>
<body class="bg-slate-50 dark:bg-gray-900 text-slate-800 dark:text-slate-100 min-h-screen flex justify-center">

    <!-- Main Container (Looks like an Android App) -->
    <div id="app" class="w-full max-w-md h-screen flex flex-col relative bg-white dark:bg-gray-900 shadow-2xl overflow-hidden">
        
        <!-- TOP STATUS BAR (Native Feel Header) -->
        <header class="bg-white dark:bg-gray-800 border-b border-slate-100 dark:border-slate-700 px-4 py-3 flex items-center justify-between sticky top-0 z-50">
            <div class="flex items-center space-x-3">
                <div id="back-btn" class="hidden p-1 rounded-full hover:bg-slate-100 dark:hover:bg-slate-700 cursor-pointer">
                    <i data-lucide="arrow-left" class="w-6 h-6"></i>
                </div>
                <div id="app-logo-container" class="w-8 h-8 rounded-full bg-blue-600 flex items-center justify-center text-white font-bold text-sm overflow-hidden">
                    <span id="app-logo-text">PCB</span>
                </div>
                <h1 id="screen-title" class="font-bold text-lg">PCB Master 2027</h1>
            </div>
            <button class="p-1 rounded-full hover:bg-slate-100 dark:hover:bg-slate-700 relative">
                <i data-lucide="bell" class="w-5 h-5"></i>
                <span class="absolute top-1 right-1 w-2 h-2 bg-red-500 rounded-full"></span>
            </button>
        </header>

        <!-- MAIN CONTENT SCROLL AREA -->
        <main class="flex-1 overflow-y-auto pb-24 scrollbar-hide px-4 py-3">
            
            <!-- SCREEN 1: DASHBOARD -->
            <div id="screen-dashboard" class="space-y-5 animate-fade-in">
                <!-- Welcome Card -->
                <div class="flex justify-between items-end">
                    <div>
                        <p class="text-xs text-slate-500 font-medium">UP Board Class 12</p>
                        <h2 class="text-2xl font-black text-blue-600 dark:text-blue-400">Namaste, Student!</h2>
                    </div>
                    <div class="bg-red-500 text-white px-3 py-1.5 rounded-full text-xs font-bold shadow-md">
                        <span id="countdown-timer">275</span> Days Left
                    </div>
                </div>

                <!-- Motivation -->
                <div class="bg-gradient-to-r from-blue-600 to-indigo-600 text-white p-4 rounded-2xl shadow-md">
                    <p class="italic text-sm">"Mehnat tab tak karo jab tak tumhara score card tumhara introduction na ban jaye!"</p>
                </div>

                <!-- Daily Target Progress -->
                <div class="bg-slate-50 dark:bg-slate-800/50 border border-slate-100 dark:border-slate-700 p-4 rounded-2xl shadow-sm">
                    <div class="flex justify-between items-center mb-2">
                        <h3 class="font-bold text-sm">Today's Target Progress</h3>
                        <span class="text-xs font-bold text-blue-600" id="target-percentage">0%</span>
                    </div>
                    <div class="w-full h-3 bg-slate-200 dark:bg-slate-700 rounded-full overflow-hidden">
                        <div id="target-progress-bar" class="h-full bg-blue-600 transition-all duration-500" style="width: 0%"></div>
                    </div>
                </div>

                <!-- Subject Quick Links -->
                <div>
                    <h3 class="font-bold text-sm mb-3">Core Subjects</h3>
                    <div class="grid grid-cols-3 gap-3">
                        <div onclick="openSubject('Physics', '#3b82f6')" class="bg-blue-50 dark:bg-blue-900/20 p-4 rounded-xl text-center border border-blue-100 dark:border-blue-800 cursor-pointer">
                            <i data-lucide="atom" class="w-8 h-8 text-blue-600 mx-auto mb-1"></i>
                            <span class="text-xs font-bold block">Physics</span>
                        </div>
                        <div onclick="openSubject('Chemistry', '#10b981')" class="bg-emerald-50 dark:bg-emerald-900/20 p-4 rounded-xl text-center border border-emerald-100 dark:border-emerald-800 cursor-pointer">
                            <i data-lucide="flame" class="w-8 h-8 text-emerald-600 mx-auto mb-1"></i>
                            <span class="text-xs font-bold block">Chemistry</span>
                        </div>
                        <div onclick="openSubject('Biology', '#8b5cf6')" class="bg-purple-50 dark:bg-purple-900/20 p-4 rounded-xl text-center border border-purple-100 dark:border-purple-800 cursor-pointer">
                            <i data-lucide="dna" class="w-8 h-8 text-purple-600 mx-auto mb-1"></i>
                            <span class="text-xs font-bold block">Biology</span>
                        </div>
                    </div>
                </div>
            </div>

            <!-- SCREEN 2: SUBJECT DETAIL (HIDDEN BY DEFAULT) -->
            <div id="screen-subject" class="hidden space-y-4 animate-fade-in">
                <div id="subject-header-card" class="p-5 rounded-2xl text-white shadow-md relative overflow-hidden">
                    <h2 id="subject-title" class="text-2xl font-black">Physics</h2>
                    <p class="text-xs opacity-90">Syllabus Completion Tracker</p>
                </div>

                <!-- Chapters List -->
                <div class="space-y-2">
                    <h3 class="font-bold text-sm">Chapter Checklists</h3>
                    <div class="flex space-x-2">
                        <input id="new-chapter-input" type="text" placeholder="Add new chapter..." class="flex-1 bg-slate-100 dark:bg-slate-800 border-none outline-none rounded-xl px-4 py-2 text-sm">
                        <button onclick="addNewChapter()" class="bg-blue-600 text-white p-2 rounded-xl"><i data-lucide="plus" class="w-5 h-5"></i></button>
                    </div>
                    <div id="chapters-list-container" class="space-y-2 pt-2">
                        <!-- Chapters inject via JS -->
                    </div>
                </div>
            </div>

            <!-- SCREEN 3: PLANNER (HIDDEN) -->
            <div id="screen-planner" class="hidden space-y-4 animate-fade-in">
                <h2 class="text-xl font-bold">Daily Study Planner</h2>
                <div class="bg-slate-100 dark:bg-slate-800 p-3 rounded-xl flex space-x-2">
                    <input id="new-task-input" type="text" placeholder="Write study task..." class="flex-1 bg-transparent border-none outline-none text-sm">
                    <button onclick="addTask()" class="text-blue-600 font-bold"><i data-lucide="plus" class="w-6 h-6"></i></button>
                </div>
                <div id="planner-tasks-container" class="space-y-2">
                    <!-- Tasks inject via JS -->
                </div>
            </div>

            <!-- SCREEN 4: JOURNAL (HIDDEN) -->
            <div id="screen-journal" class="hidden space-y-4 animate-fade-in">
                <h2 class="text-xl font-bold">Daily Study Status</h2>
                <div class="bg-white dark:bg-gray-800 border border-slate-100 dark:border-slate-700 p-4 rounded-xl space-y-3">
                    <div>
                        <label class="text-xs font-semibold text-slate-500">Study Hours Today</label>
                        <input id="journal-hours" type="number" placeholder="How many hours?" class="w-full p-2 bg-slate-50 dark:bg-slate-900 rounded-lg text-sm border-none outline-none mt-1">
                    </div>
                    <div>
                        <label class="text-xs font-semibold text-slate-500">Mood</label>
                        <select id="journal-mood" class="w-full p-2 bg-slate-50 dark:bg-slate-900 rounded-lg text-sm border-none outline-none mt-1">
                            <option>Highly Motivated</option>
                            <option>Good</option>
                            <option>Average</option>
                            <option>Stressed/Tired</option>
                        </select>
                    </div>
                    <div>
                        <label class="text-xs font-semibold text-slate-500">What did you complete?</label>
                        <textarea id="journal-text" rows="3" placeholder="Physics chapter 1 complete, etc." class="w-full p-2 bg-slate-50 dark:bg-slate-900 rounded-lg text-sm border-none outline-none mt-1 resize-none"></textarea>
                    </div>
                    <button onclick="saveJournal()" class="w-full bg-blue-600 text-white py-2.5 rounded-xl font-bold">Save Entry</button>
                </div>
            </div>

            <!-- SCREEN 5: SETTINGS (HIDDEN) -->
            <div id="screen-settings" class="hidden space-y-4 animate-fade-in">
                <h2 class="text-xl font-bold">Settings & Profile</h2>
                <div class="bg-slate-50 dark:bg-slate-800/50 p-4 rounded-2xl space-y-3">
                    <input id="profile-name" type="text" placeholder="Your Name" class="w-full p-2 bg-white dark:bg-gray-900 rounded-lg text-sm outline-none border border-slate-200 dark:border-slate-700">
                    <input id="profile-board" type="text" placeholder="Board" value="UP Board Class 12" class="w-full p-2 bg-white dark:bg-gray-900 rounded-lg text-sm outline-none border border-slate-200 dark:border-slate-700">
                    <button onclick="saveProfile()" class="w-full bg-slate-800 dark:bg-slate-700 text-white py-2 rounded-lg text-sm font-bold">Save Settings</button>
                </div>
            </div>

        </main>

        <!-- BOTTOM NAV BAR -->
        <nav class="absolute bottom-0 w-full bg-white dark:bg-gray-800 border-t border-slate-100 dark:border-slate-700 flex justify-around p-3 z-50">
            <button onclick="switchTab('dashboard')" class="nav-item text-blue-600 flex flex-col items-center">
                <i data-lucide="home" class="w-6 h-6"></i>
                <span class="text-[10px] font-medium mt-1">Home</span>
            </button>
            <button onclick="switchTab('planner')" class="nav-item text-slate-400 flex flex-col items-center">
                <i data-lucide="calendar" class="w-6 h-6"></i>
                <span class="text-[10px] font-medium mt-1">Planner</span>
            </button>
            <button onclick="switchTab('journal')" class="nav-item text-slate-400 flex flex-col items-center">
                <i data-lucide="edit-3" class="w-6 h-6"></i>
                <span class="text-[10px] font-medium mt-1">Journal</span>
            </button>
            <button onclick="switchTab('settings')" class="nav-item text-slate-400 flex flex-col items-center">
                <i data-lucide="settings" class="w-6 h-6"></i>
                <span class="text-[10px] font-medium mt-1">Settings</span>
            </button>
        </nav>

    </div>

    <!-- APP JAVASCRIPT LOGIC -->
    <script>
        // --- DATABASE LOGIC (Local Storage) ---
        let db = {
            chapters: JSON.parse(localStorage.getItem('pcb_chaps')) || [
                { id: 1, subject: 'Physics', title: 'Electrostatics', status: 'In Progress' },
                { id: 2, subject: 'Physics', title: 'Current Electricity', status: 'Not Started' },
                { id: 3, subject: 'Chemistry', title: 'Solutions', status: 'Completed' },
                { id: 4, subject: 'Biology', title: 'Sexual Reproduction in Flowering Plants', status: 'Completed' }
            ],
            tasks: JSON.parse(localStorage.getItem('pcb_tasks')) || [
                { id: 1, text: 'Solve Physics NCERT Chapter 1 Numerical', completed: false },
                { id: 2, text: 'Revise Chemistry Reactions', completed: true }
            ],
            profile: JSON.parse(localStorage.getItem('pcb_profile')) || {
                name: 'PCB Master',
                board: 'UP Board Class 12'
            }
        };

        let currentSubject = 'Physics';
        let currentSubjectColor = '#3b82f6';

        function saveDB() {
            localStorage.setItem('pcb_chaps', JSON.stringify(db.chapters));
            localStorage.setItem('pcb_tasks', JSON.stringify(db.tasks));
            localStorage.setItem('pcb_profile', JSON.stringify(db.profile));
            updateDashboardMetrics();
        }

        // --- NAVIGATION CONTROLLER ---
        function switchTab(tabName) {
            document.querySelectorAll('main > div').forEach(el => el.classList.add('hidden'));
            document.getElementById(`screen-${tabName}`).classList.remove('hidden');

            document.querySelectorAll('.nav-item').forEach(el => {
                el.classList.remove('text-blue-600');
                el.classList.add('text-slate-400');
            });
            event.currentTarget.classList.add('text-blue-600');
            event.currentTarget.classList.remove('text-slate-400');

            document.getElementById('back-btn').classList.add('hidden');
            document.getElementById('screen-title').innerText = tabName === 'dashboard' ? 'PCB Master 2027' : tabName.toUpperCase();
        }

        function openSubject(subName, color) {
            currentSubject = subName;
            currentSubjectColor = color;
            document.querySelectorAll('main > div').forEach(el => el.classList.add('hidden'));
            document.getElementById('screen-subject').classList.remove('hidden');

            const header = document.getElementById('subject-header-card');
            header.style.backgroundColor = color;
            document.getElementById('subject-title').innerText = subName;

            document.getElementById('back-btn').classList.remove('hidden');
            document.getElementById('screen-title').innerText = subName;

            renderChapters();
        }

        document.getElementById('back-btn').addEventListener('click', () => {
            switchTab('dashboard');
        });

        // --- RENDER CHAPTER TRACKER ---
        function renderChapters() {
            const container = document.getElementById('chapters-list-container');
            container.innerHTML = '';
            const filtered = db.chapters.filter(c => c.subject === currentSubject);

            filtered.forEach(chap => {
                const item = document.createElement('div');
                item.className = "bg-slate-50 dark:bg-slate-800 p-3 rounded-xl flex justify-between items-center border border-slate-100 dark:border-slate-700";
                
                let statusBadgeColor = 'bg-slate-200 text-slate-700';
                if(chap.status === 'In Progress') statusBadgeColor = 'bg-blue-100 text-blue-700';
                if(chap.status === 'Completed') statusBadgeColor = 'bg-emerald-100 text-emerald-700';

                item.innerHTML = `
                    <span class="text-sm font-semibold">${chap.title}</span>
                    <button onclick="cycleStatus(${chap.id})" class="text-xs font-bold px-3 py-1.5 rounded-full ${statusBadgeColor}">${chap.status}</button>
                `;
                container.appendChild(item);
            });
        }

        function addNewChapter() {
            const input = document.getElementById('new-chapter-input');
            if(input.value.trim() !== '') {
                db.chapters.push({
                    id: Date.now(),
                    subject: currentSubject,
                    title: input.value.trim(),
                    status: 'Not Started'
                });
                input.value = '';
                saveDB();
                renderChapters();
            }
        }

        function cycleStatus(id) {
            const chap = db.chapters.find(c => c.id === id);
            const statuses = ['Not Started', 'In Progress', 'Completed'];
            let nextIndex = (statuses.indexOf(chap.status) + 1) % statuses.length;
            chap.status = statuses[nextIndex];
            saveDB();
            renderChapters();
        }

        // --- PLANNER CONTROLLER ---
        function renderPlanner() {
            const container = document.getElementById('planner-tasks-container');
            container.innerHTML = '';
            db.tasks.forEach(task => {
                const item = document.createElement('div');
                item.className = "bg-slate-50 dark:bg-slate-800 p-3 rounded-xl flex items-center justify-between";
                item.innerHTML = `
                    <div class="flex items-center space-x-3 cursor-pointer" onclick="toggleTask(${task.id})">
                        <i data-lucide="${task.completed ? 'check-circle' : 'circle'}" class="w-5 h-5 ${task.completed ? 'text-emerald-500' : 'text-slate-400'}"></i>
                        <span class="text-sm ${task.completed ? 'line-through text-slate-400' : ''}">${task.text}</span>
                    </div>
                    <button onclick="deleteTask(${task.id})" class="text-red-500"><i data-lucide="trash-2" class="w-4 h-4"></i></button>
                `;
                container.appendChild(item);
            });
            lucide.createIcons();
        }

        function addTask() {
            const input = document.getElementById('new-task-input');
            if(input.value.trim() !== '') {
                db.tasks.push({ id: Date.now(), text: input.value.trim(), completed: false });
                input.value = '';
                saveDB();
                renderPlanner();
            }
        }

        function toggleTask(id) {
            const task = db.tasks.find(t => t.id === id);
            task.completed = !task.completed;
            saveDB();
            renderPlanner();
        }

        function deleteTask(id) {
            db.tasks = db.tasks.filter(t => t.id !== id);
            saveDB();
            renderPlanner();
        }

        // --- METRICS & ENGINE UTILS ---
        function updateDashboardMetrics() {
            const totalTasks = db.tasks.length;
            const completed = db.tasks.filter(t => t.completed).length;
            const percentage = totalTasks ? Math.round((completed / totalTasks) * 100) : 0;
            
            document.getElementById('target-percentage').innerText = `${percentage}%`;
            document.getElementById('target-progress-bar').style.width = `${percentage}%`;
        }

        function saveJournal() {
            alert('Journal Entry Saved Successfully!');
            document.getElementById('journal-hours').value = '';
            document.getElementById('journal-text').value = '';
        }

        function saveProfile() {
            const nameInput = document.getElementById('profile-name').value;
            db.profile.name = nameInput;
            saveDB();
            alert('Profile Settings Saved!');
        }

        // Initialize Core System
        window.# study-traker-