
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>gnessac: Enterprise Anticheat & Digital Forensics</title>
    <!-- Custom Blue Transparent Favicon with matching (*> symbol -->
    <link rel="icon" type="image/svg+xml" href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 32 32%22><text x=%220%22 y=%2224%22 font-family=%22monospace%22 font-size=%2220%22 font-weight=%22bold%22 fill=%22%233A63EC%22>(*&gt;</text></svg>">
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap');
        
        body { 
            background-color: #09090b; 
            color: #ffffff; 
            overflow-x: hidden; 
            font-family: 'Inter', sans-serif; 
            margin: 0;
        }
        
        /* Matrix 0 and 1 Background Canvas */
        #matrixCanvas { 
            position: fixed; 
            top: 0; 
            left: 0;
            width: 100vw; 
            height: 100vh; 
            z-index: 0; 
            pointer-events: none; 
            opacity: 0.25;
        }
        
        /* Neon Button Effects */
        .neon-btn { 
            background-color: #2563eb; 
            box-shadow: 0 0 15px rgba(37, 99, 235, 0.4); 
            transition: all 0.3s ease; 
        }
        .neon-btn:hover { 
            background-color: #1d4ed8; 
            box-shadow: 0 0 25px rgba(37, 99, 235, 0.7); 
        }

        /* Page Section Isolation & Animations */
        .page-section {
            display: none;
            position: relative;
            z-index: 10;
            width: 100%;
            min-height: calc(100vh - 80px);
            animation: fadeIn 0.3s ease-in-out;
        }
        .page-section.active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Navigation Links */
        .nav-link { color: #9ca3af; border-bottom: 2px solid transparent; padding-bottom: 0.25rem; transition: all 0.2s; text-decoration: none; cursor: pointer; }
        .nav-link:hover { color: #ffffff; }
        .nav-link.active { color: #ffffff; border-bottom-color: #ffffff; }

        /* FAQ Accordion Styles */
        .faq-content { display: none; margin-top: 1rem; color: #9ca3af; font-size: 0.875rem; line-height: 1.5; }
        .faq-item.active .faq-content { display: block; }
        .faq-item.active .faq-icon { transform: rotate(180deg); }
        .faq-item.active h3 { color: #60a5fa; }
    </style>
</head>
<body>

    <!-- Matrix 0 and 1 Background Canvas -->
    <canvas id="matrixCanvas"></canvas>

    <!-- Header / Navbar -->
    <header class="relative z-20 w-full flex justify-between items-center py-6 px-10 md:px-14 border-b border-[#1f1f22] bg-[#09090b]/90 backdrop-blur-md">
        <div class="flex items-center gap-3 cursor-pointer py-2 transition" onclick="navigate('home')">
            <span class="font-bold text-2xl tracking-tight font-mono text-gray-100">(*> gness<span class="text-blue-500">ac</span></span>
        </div>
        
        <nav class="hidden md:flex gap-8 text-sm font-medium">
            <a class="nav-link active" onclick="navigate('home', this)">Features</a>
            <a class="nav-link" onclick="navigate('pricing', this)">Pricing</a>
            <a class="nav-link" onclick="navigate('docs', this)">Docs</a>
            <a class="nav-link" onclick="navigate('branding', this)">Branding</a>
            <a class="nav-link" onclick="navigate('terms', this)">Terms & Privacy</a>
            <a class="nav-link" onclick="navigate('faq', this)">FAQ</a>
            <a class="nav-link" onclick="navigate('home', this)">Download</a>
            <a href="https://discord.com/" target="_blank" class="nav-link">Discord</a>
        </nav>
        
        <div class="flex items-center gap-5">
            <a onclick="navigate('login', this)" class="nav-link text-sm font-medium hidden md:block">Log in</a>
            <button onclick="navigate('register', this)" class="neon-btn px-5 py-2 text-sm font-semibold rounded-md text-white cursor-pointer">Sign up</button>
        </div>
    </header>

    <!-- 1. HOME SECTION -->
    <main id="home" class="page-section active">
        <div class="flex flex-col justify-center h-full px-8 md:px-24 pt-20 lg:pt-28 max-w-5xl">
            <div class="mb-6">
                <span class="font-mono text-4xl font-extrabold text-white tracking-tighter">(*></span>
            </div>

            <h1 id="typewriterHeading" class="text-6xl md:text-[5.5rem] font-extrabold tracking-tight leading-[1.1] mb-6 text-white min-h-[140px] md:min-h-[200px]">
                <span id="typedText"></span><span id="cursor" class="animate-pulse text-blue-500">|</span>
            </h1>
            <p id="heroSub" class="text-xl md:text-2xl text-gray-300 mb-8 font-medium max-w-2xl">
                Cheaters bury the evidence. gnessac dives for it.
            </p>

            <!-- Detailed Corporate Content Expansion -->
            <div class="mb-12 max-w-4xl bg-[#121214] border border-[#27272a] rounded-xl shadow-xl overflow-hidden transition-all duration-300">
                <div onclick="toggleHomeAccordion(this)" class="p-6 cursor-pointer flex justify-between items-center select-none hover:bg-[#18181b] transition">
                    <h3 class="text-xl font-bold text-white tracking-wide">Comprehensive Overview of <span class="text-blue-500">gnessac Technologies</span>, Enterprise Services & Game Forensics</h3>
                    <span class="home-acc-icon text-gray-300 font-bold transition-transform duration-300">▼</span>
                </div>
                <div id="homeAccordionContent" style="display: block;" class="px-8 pb-8 pt-0 space-y-6 text-gray-200 text-base leading-relaxed border-t border-[#27272a] mt-2 pt-6">
                    <p>
                        In today's highly dynamic competitive gaming landscape, esports tournaments, and dedicated community multiplayer servers, bad actors continuously engineer sophisticated bypasses, obfuscated memory injectors, kernel-level hooks, and automated macro frameworks designed to compromise absolute fair-play integrity. Under the flagship <strong class="text-white">gnessac</strong> brand, our platform establishes an uncompromising gold standard for digital forensics by deploying advanced post-mortem analysis engines engineered to detect, isolate, and document illicit tampering across premier competitive titles with surgical cryptographic precision.
                    </p>
                    <p>
                        <strong>Core Architecture & Post-Mortem Digital Forensics:</strong> Our platform departs from conventional, intrusive background anti-cheat drivers by executing deep system telemetry verifications during active staff-supervised moderation and screening sessions. By thoroughly scrutinizing volatile RAM allocations, process image headers, prefetch logs, temporary execution directories, and system registry hives, server administrators receive unalterable evidentiary compliance reports within seconds of scan initialization.
                    </p>
                    <p>
                        <strong>Game-Specific Forensic Scanning Modules:</strong>
                        <ul class="list-disc pl-6 space-y-2 mt-3 text-gray-300">
                            <li><strong class="text-white">Minecraft Java Edition:</strong> Specialized deep-memory inspection for hacked clients, modified jar class loaders, DLL wrappers, reached/reach-spoofing injectors, and automated client automation modules across PvP and faction networks.</li>
                            <li><strong class="text-white">Grand Theft Auto V & FiveM Roleplay:</strong> Advanced detection protocols targeting unauthorized Lua script executors, menu injection frameworks, weapon damage modders, and custom resource bypasses on high-population RP servers.</li>
                            <li><strong class="text-white">San Andreas Multiplayer (SA-MP):</strong> Legacy memory verification, custom client DLL validation, and unalterable hook detection for classic community servers.</li>
                            <li><strong class="text-white">Rust & Survival Environments:</strong> Comprehensive memory mapping to uncover ESP overlays, silent aim vectors, recoil compensation scripts, and unauthorized asset tampering within volatile server sessions.</li>
                            <li><strong class="text-white">Counter-Strike 2 & Tactical Shooters:</strong> Heuristic behavioral input analysis evaluating mouse movement distributions, angular snap velocities, and unauthorized overlay hooks to guarantee uncompromised competitive ranking integrity.</li>
                        </ul>
                    </p>
                    <p>
                        <strong>Our Advanced Enterprise Services & Security Modules:</strong>
                        <ul class="list-disc pl-6 space-y-2 mt-3 text-gray-300">
                            <li><strong class="text-white">Real-Time Screenshare & Pin Verification:</strong> Secure staff pin generation enables rapid session linking, ensuring that clients execute diagnostic binaries under strict cryptographic supervision.</li>
                            <li><strong class="text-white">Memory Hook & DLL Integrity Inspection:</strong> Rigorous examination of running process virtual spaces to expose hidden injectors, spliced instruction hooks, and unauthorized runtime modifications.</li>
                            <li><strong class="text-white">Heuristic Macro & Input Behavioral Analysis:</strong> Algorithmic evaluation of input timing irregularities and mouse movement distributions to uncover automated assistance and macro software.</li>
                            <li><strong class="text-white">Automated Webhook & Discord Telemetry Streaming:</strong> Instantaneous dispatch of audit logs, hardware identification hashes (HWID), and compliance verification screenshots directly to private staff channels.</li>
                        </ul>
                    </p>
                    <p>
                        <strong>Absolute Data Sovereignty & Privacy Compliance:</strong> Engineered with strict international privacy regulations at its core, <strong class="text-white">gnessac</strong> guarantees that sensitive personal documents, private web browser histories, and confidential communications remain strictly untouched. We capture exclusively verified anti-cheat metadata and a single compliance screenshot at scan conclusion, purging all records automatically after 21 days to ensure absolute user confidentiality.
                    </p>
                </div>
            </div>

            <!-- Supported Platforms Badge Bar -->
            <div class="flex items-center gap-3 mb-12 text-sm text-gray-400 font-medium">
                <div class="flex items-center gap-2">
                    <svg class="w-4 h-4 text-white" viewBox="0 0 88 88" fill="currentColor">
                        <path d="M0 12.402l35.687-4.86v34.19H0V12.402zm35.687 35.688v35.485L0 78.713V48.09h35.687zm5.556-41.202L88 0v41.488H41.243V6.888zm46.757 41.201V88L41.243 81.39V48.09H88z"/>
                    </svg>
                    <span>Windows and Linux</span>
                </div>
            </div>

            <div class="flex flex-wrap items-center gap-4 mb-16">
                <button onclick="navigate('register')" class="neon-btn px-7 py-3 text-[15px] font-semibold rounded flex items-center gap-2 cursor-pointer">Start a scan</button>
                <button onclick="navigate('docs')" class="px-7 py-3 text-[15px] font-semibold border border-[#27272a] rounded hover:bg-[#18181b] transition cursor-pointer">Read the documentation</button>
            </div>

            <!-- Supported Games Bar (All Clickable) -->
            <div class="flex items-center gap-4 flex-wrap pb-12 border-t border-[#1f1f22] pt-8 text-sm">
                <span class="text-gray-400 font-semibold mr-2">Supported games</span>
                <span onclick="selectGameAndNavigate('Minecraft Java')" class="text-gray-300 font-medium hover:text-blue-400 cursor-pointer transition">Minecraft Java</span>
                <span onclick="selectGameAndNavigate('Grand Theft Auto V')" class="text-gray-400 hover:text-blue-400 cursor-pointer transition">Grand Theft Auto V</span>
                <span onclick="selectGameAndNavigate('San Andreas')" class="text-gray-400 hover:text-blue-400 cursor-pointer transition">San Andreas</span>
                <span onclick="selectGameAndNavigate('Roblox')" class="text-gray-400 hover:text-blue-400 cursor-pointer transition">Roblox</span>
                <span onclick="selectGameAndNavigate('RedM')" class="text-gray-400 hover:text-blue-400 cursor-pointer transition">RedM</span>
                <span onclick="selectGameAndNavigate('RageMP')" class="text-gray-400 hover:text-blue-400 cursor-pointer transition">RageMP</span>
                <span onclick="selectGameAndNavigate('Rust')" class="text-gray-400 hover:text-blue-400 cursor-pointer transition">Rust</span>
                <span onclick="selectGameAndNavigate('FiveM')" class="text-gray-400 hover:text-blue-400 cursor-pointer transition">FiveM</span>
                <span onclick="selectGameAndNavigate('alt:V')" class="text-gray-400 hover:text-blue-400 cursor-pointer transition">alt:V</span>
                <span onclick="selectGameAndNavigate('Call of Duty')" class="text-gray-400 hover:text-blue-400 cursor-pointer transition">Call of Duty</span>
                <span onclick="selectGameAndNavigate('Free Fire')" class="text-gray-400 hover:text-blue-400 cursor-pointer transition">Free Fire</span>
                <span onclick="selectGameAndNavigate('DayZ')" class="text-gray-400 hover:text-blue-400 cursor-pointer transition">DayZ</span>
                <span onclick="selectGameAndNavigate('SCUM')" class="text-gray-400 hover:text-blue-400 cursor-pointer transition">SCUM</span>
                <span onclick="selectGameAndNavigate('Metin2')" class="text-gray-400 hover:text-blue-400 cursor-pointer transition">Metin2</span>
                <span onclick="selectGameAndNavigate('Knight Online')" class="text-gray-400 hover:text-blue-400 cursor-pointer transition">Knight Online</span>
                <span onclick="selectGameAndNavigate('EVE Online')" class="text-gray-400 hover:text-blue-400 cursor-pointer transition">EVE Online</span>
                <span onclick="selectGameAndNavigate('Counter-Strike 2')" class="text-gray-400 hover:text-blue-400 cursor-pointer transition">Counter-Strike 2</span>
                <span onclick="selectGameAndNavigate('PUBG: Battlegrounds')" class="text-gray-400 hover:text-blue-400 cursor-pointer transition">PUBG: Battlegrounds</span>
            </div>

            <!-- Corporate Copyright Footer -->
            <div class="py-8 border-t border-[#1f1f22] text-center text-xs text-gray-500 font-medium tracking-wide flex flex-col sm:flex-row justify-center items-center gap-4">
                <span>Copyright © 2026 gnessac.org, All rights reserved.</span>
                <span class="text-gray-600 hidden sm:inline">|</span>
                <a onclick="navigate('terms')" class="hover:text-white cursor-pointer transition">Terms of Service & Privacy Policy</a>
            </div>
        </div>
    </main>

    <!-- 2. PRICING SECTION -->
    <main id="pricing" class="page-section">
        <div class="px-8 md:px-24 pt-16 pb-24">
            <div id="pricingTabs" class="flex gap-2 mb-16 flex-wrap pb-4">
                <button onclick="selectGame('Minecraft Java', this)" class="px-5 py-2 text-sm font-medium rounded bg-blue-600 text-white cursor-pointer transition">Minecraft Java</button>
                <button onclick="selectGame('Grand Theft Auto V', this)" class="px-5 py-2 text-sm font-medium rounded border border-[#27272a] hover:bg-[#18181b] text-gray-400 cursor-pointer transition">Grand Theft Auto V</button>
                <button onclick="selectGame('San Andreas', this)" class="px-5 py-2 text-sm font-medium rounded border border-[#27272a] hover:bg-[#18181b] text-gray-400 cursor-pointer transition">San Andreas</button>
                <button onclick="selectGame('Roblox', this)" class="px-5 py-2 text-sm font-medium rounded border border-[#27272a] hover:bg-[#18181b] text-gray-400 cursor-pointer transition">Roblox</button>
                <button onclick="selectGame('RedM', this)" class="px-5 py-2 text-sm font-medium rounded border border-[#27272a] hover:bg-[#18181b] text-gray-400 cursor-pointer transition">RedM</button>
                <button onclick="selectGame('RageMP', this)" class="px-5 py-2 text-sm font-medium rounded border border-[#27272a] hover:bg-[#18181b] text-gray-400 cursor-pointer transition">RageMP</button>
                <button onclick="selectGame('Rust', this)" class="px-5 py-2 text-sm font-medium rounded border border-[#27272a] hover:bg-[#18181b] text-gray-400 cursor-pointer transition">Rust</button>
                <button onclick="selectGame('FiveM', this)" class="px-5 py-2 text-sm font-medium rounded border border-[#27272a] hover:bg-[#18181b] text-gray-400 cursor-pointer transition">FiveM</button>
                <button onclick="selectGame('alt:V', this)" class="px-5 py-2 text-sm font-medium rounded border border-[#27272a] hover:bg-[#18181b] text-gray-400 cursor-pointer transition">alt:V</button>
                <button onclick="selectGame('Call of Duty', this)" class="px-5 py-2 text-sm font-medium rounded border border-[#27272a] hover:bg-[#18181b] text-gray-400 cursor-pointer transition">Call of Duty</button>
                <button onclick="selectGame('Free Fire', this)" class="px-5 py-2 text-sm font-medium rounded border border-[#27272a] hover:bg-[#18181b] text-gray-400 cursor-pointer transition">Free Fire</button>
                <button onclick="selectGame('DayZ', this)" class="px-5 py-2 text-sm font-medium rounded border border-[#27272a] hover:bg-[#18181b] text-gray-400 cursor-pointer transition">DayZ</button>
                <button onclick="selectGame('SCUM', this)" class="px-5 py-2 text-sm font-medium rounded border border-[#27272a] hover:bg-[#18181b] text-gray-400 cursor-pointer transition">SCUM</button>
                <button onclick="selectGame('Metin2', this)" class="px-5 py-2 text-sm font-medium rounded border border-[#27272a] hover:bg-[#18181b] text-gray-400 cursor-pointer transition">Metin2</button>
                <button onclick="selectGame('Knight Online', this)" class="px-5 py-2 text-sm font-medium rounded border border-[#27272a] hover:bg-[#18181b] text-gray-400 cursor-pointer transition">Knight Online</button>
                <button onclick="selectGame('EVE Online', this)" class="px-5 py-2 text-sm font-medium rounded border border-[#27272a] hover:bg-[#18181b] text-gray-400 cursor-pointer transition">EVE Online</button>
                <button onclick="selectGame('Counter-Strike 2', this)" class="px-5 py-2 text-sm font-medium rounded border border-[#27272a] hover:bg-[#18181b] text-gray-400 cursor-pointer transition">Counter-Strike 2</button>
                <button onclick="selectGame('PUBG: Battlegrounds', this)" class="px-5 py-2 text-sm font-medium rounded border border-[#27272a] hover:bg-[#18181b] text-gray-400 cursor-pointer transition">PUBG: Battlegrounds</button>
            </div>
            
            <h2 id="pricingTitle" class="text-3xl font-bold mb-10">Personal plans</h2>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <!-- Yearly Plan -->
                <div class="p-8 border border-[#27272a] bg-[#09090b]/50 rounded-xl hover:border-gray-600 transition flex flex-col justify-between">
                    <div>
                        <p class="text-sm text-gray-400 mb-2 font-medium">Personal use</p>
                        <h3 id="plan1Title" class="text-lg font-bold mb-2">gnessac (Minecraft) - Yearly Personal</h3>
                        <p id="plan1Desc" class="text-sm text-gray-500 mb-8">Screenshare scan for Minecraft Java.</p>
                        <div class="mb-8">
                            <span class="text-5xl font-extrabold">$79.99</span><br>
                            <span class="text-sm text-gray-500 font-medium mt-1 inline-block">Billed Yearly</span>
                        </div>
                        <ul class="space-y-3 mb-10 text-sm font-medium text-gray-300">
                            <li class="flex items-center gap-3"><span class="text-white">✓</span> 1 slot</li>
                            <li class="flex items-center gap-3"><span class="text-white">✓</span> Personal use</li>
                            <li class="flex items-center gap-3"><span class="text-white">✓</span> Full game access</li>
                            <li class="flex items-center gap-3"><span class="text-white">✓</span> Unlimited pin generation</li>
                        </ul>
                    </div>
                    <button onclick="handlePurchase('Yearly')" class="w-full py-3.5 bg-[#18181b] hover:bg-[#27272a] rounded text-sm font-semibold border border-[#27272a] transition cursor-pointer">Log in to Purchase</button>
                </div>
                
                <!-- 6 Month Plan -->
                <div class="p-8 border border-[#27272a] bg-[#09090b]/50 rounded-xl hover:border-gray-600 transition flex flex-col justify-between">
                    <div>
                        <p class="text-sm text-gray-400 mb-2 font-medium">Personal use</p>
                        <h3 id="plan2Title" class="text-lg font-bold mb-2">gnessac (Minecraft) - 6 Month Personal</h3>
                        <p id="plan2Desc" class="text-sm text-gray-500 mb-8">Screenshare scan for Minecraft Java.</p>
                        <div class="mb-8">
                            <span class="text-5xl font-extrabold">$44.99</span><br>
                            <span class="text-sm text-gray-500 font-medium mt-1 inline-block">Billed Every 6 Months</span>
                        </div>
                        <ul class="space-y-3 mb-10 text-sm font-medium text-gray-300">
                            <li class="flex items-center gap-3"><span class="text-white">✓</span> 1 slot</li>
                            <li class="flex items-center gap-3"><span class="text-white">✓</span> Personal use</li>
                        </ul>
                    </div>
                    <button onclick="handlePurchase('6 Month')" class="w-full py-3.5 bg-[#18181b] hover:bg-[#27272a] rounded text-sm font-semibold border border-[#27272a] transition cursor-pointer">Log in to Purchase</button>
                </div>
                
                <!-- Monthly Plan -->
                <div class="p-8 border border-[#27272a] bg-[#09090b]/50 rounded-xl hover:border-gray-600 transition flex flex-col justify-between">
                    <div>
                        <p class="text-sm text-gray-400 mb-2 font-medium">Personal use</p>
                        <h3 id="plan3Title" class="text-lg font-bold mb-2">gnessac (Minecraft) - Monthly Personal</h3>
                        <p id="plan3Desc" class="text-sm text-gray-500 mb-8">Screenshare scan for Minecraft Java.</p>
                        <div class="mb-8">
                            <span class="text-5xl font-extrabold">$10.00</span><br>
                            <span class="text-sm text-gray-500 font-medium mt-1 inline-block">Billed Monthly</span>
                        </div>
                        <ul class="space-y-3 mb-10 text-sm font-medium text-gray-300">
                            <li class="flex items-center gap-3"><span class="text-white">✓</span> 1 slot</li>
                            <li class="flex items-center gap-3"><span class="text-white">✓</span> Personal use</li>
                        </ul>
                    </div>
                    <button onclick="handlePurchase('Monthly')" class="w-full py-3.5 bg-[#18181b] hover:bg-[#27272a] rounded text-sm font-semibold border border-[#27272a] transition cursor-pointer">Log in to Purchase</button>
                </div>
            </div>
        </div>
    </main>

    <!-- 3. DOCUMENTATION SECTION -->
    <main id="docs" class="page-section">
        <div class="px-8 md:px-24 pt-16 flex flex-col lg:flex-row gap-16">
            <aside class="w-full lg:w-1/4">
                <div class="relative mb-8">
                    <input type="text" placeholder="Search..." class="w-full bg-[#121214] border border-[#27272a] rounded-md py-2.5 px-4 text-sm text-white focus:outline-none focus:border-blue-500">
                </div>
                <div class="text-xs font-bold text-gray-500 uppercase tracking-wider mb-4">DOCUMENTATION</div>
                <ul class="space-y-2 text-[15px] font-medium text-gray-400">
                    <li id="docNavOverview" onclick="switchDocTab('overview', this)" class="cursor-pointer text-white border-l-2 border-blue-500 pl-3 transition">Overview</li>
                    <li id="docNavDetections" onclick="switchDocTab('detections', this)" class="cursor-pointer hover:text-white flex justify-between items-center pl-3 py-1 transition">Detections <span class="text-xs">›</span></li>
                    <li id="docNavApi" onclick="switchDocTab('api', this)" class="cursor-pointer hover:text-white flex justify-between items-center pl-3 py-1 transition">API <span class="text-xs">›</span></li>
                </ul>
            </aside>
            <div class="w-full lg:w-3/4 max-w-3xl">
                <div id="docContentOverview" class="doc-content-pane space-y-8">
                    <h1 class="text-4xl font-extrabold mb-8 border-b border-[#27272a] pb-6">Exhaustive Architectural Overview & Enterprise Forensics Reference</h1>
                    <p class="text-gray-300 leading-relaxed text-base">
                        Welcome to the official, highly comprehensive enterprise documentation portal for <strong class="text-white">gnessac Solutions</strong>. In today's aggressively evolving competitive gaming landscape, community administrators, esports tournament organizers, and professional server networks face unprecedented challenges from malicious actors deploying highly obfuscated memory injectors, kernel-level hooks, automated macro frameworks, and customized hardware identification (HWID) spoofers. Maintaining absolute fair-play integrity requires a quantum leap beyond traditional signature-based detection mechanisms. Under the flagship <strong class="text-white">gnessac</strong> architecture, our platform establishes an uncompromised gold standard for digital forensics by deploying advanced post-mortem telemetry verification engines engineered to detect, isolate, and document illicit tampering with surgical cryptographic precision.
                    </p>
                    <p class="text-gray-300 leading-relaxed text-base">
                        <strong>Foundational Philosophy & Deep System Telemetry:</strong> Traditional anti-cheat implementations often rely on intrusive, persistent background drivers that consume excessive system resources and introduce potential attack vectors. In stark contrast, <strong class="text-white">gnessac</strong> operates on an on-demand, session-based forensic verification model. When initiated via a staff-generated cryptographic verification pin, our lightweight scanning binary executes a rigorous, multi-layered audit of volatile system RAM allocations, running process image headers, prefetch logs, temporary execution directories, and system registry hives. This ensures zero performance overhead during active gameplay while capturing unalterable evidentiary artifacts within seconds of initialization.
                    </p>
                    <p class="text-gray-300 leading-relaxed text-base">
                        <strong>Core Diagnostic Modules & Operational Workflow:</strong>
                        <ul class="list-disc pl-6 space-y-3 mt-3 text-gray-300">
                            <li><strong class="text-white">Real-Time Screenshare & Pin Verification Protocol:</strong> Secure staff pin generation enables instantaneous session linking between the moderator dashboard and the target client, ensuring that diagnostic binaries execute under strict cryptographic supervision.</li>
                            <li><strong class="text-white">Memory Hook & DLL Integrity Inspection:</strong> Rigorous examination of running process virtual spaces to expose hidden injectors, spliced instruction hooks, inline detours, and unauthorized runtime memory modifications.</li>
                            <li><strong class="text-white">File System Artifact & Trace Recovery:</strong> Deep scanning of prefetch files, recent document histories, temporary application directories, and registry hives to unearth remnants of deleted cheat loaders and spoofing tools.</li>
                            <li><strong class="text-white">Heuristic Macro & Input Behavioral Analysis:</strong> Algorithmic evaluation of input timing irregularities, click distribution patterns, and mouse movement trajectories to uncover automated assistance and macro software.</li>
                            <li><strong class="text-white">Automated Webhook & Discord Telemetry Streaming:</strong> Instantaneous dispatch of audit logs, hardware identification hashes (HWID), and compliance verification screenshots directly to private staff channels.</li>
                        </ul>
                    </p>
                    <p class="text-gray-300 leading-relaxed text-base">
                        <strong>Absolute Data Sovereignty & International Privacy Compliance:</strong> Engineered from the ground up with strict adherence to global privacy regulations (including GDPR and CCPA), <strong class="text-white">gnessac</strong> guarantees that sensitive personal documents, private web browser histories, financial statements, and confidential communications remain strictly untouched. We capture exclusively verified anti-cheat metadata and a single compliance screenshot at scan conclusion, purging all records automatically after 21 days to ensure absolute user confidentiality across Minecraft Java, FiveM, San Andreas, Rust, and Counter-Strike 2.
                    </p>
                    <p class="text-gray-300 leading-relaxed text-base mb-12">
                        This comprehensive documentation portal serves as an authoritative reference manual for server owners, community moderators, security analysts, and enterprise developers integrating our dashboards and APIs. Explore the sidebar navigation categories to review granular detection schemas, cryptographic hardware verification protocols, and secure cloud logging standards in detail.
                    </p>
                </div>

                <div id="docContentDetections" class="doc-content-pane space-y-8" style="display: none;">
                    <h1 class="text-4xl font-extrabold mb-8 border-b border-[#27272a] pb-6">Advanced Detections, Heuristics & Forensic Services</h1>
                    <p class="text-gray-300 leading-relaxed text-base">
                        gnessac provides industry-leading detection frameworks designed specifically to combat modern bypasses, obfuscated loaders, memory dumpers, and persistent cheat modifications. Our automated scan modules thoroughly examine runtime memory blocks, loaded assemblies, and suspended background processes to expose hidden toolsets instantly upon screening execution.
                    </p>
                    <p class="text-gray-300 leading-relaxed text-base">
                        <strong>Memory Integrity & Hook Verification:</strong> Our post-mortem engine inspects process image headers, exported function tables, and virtual memory allocations with rigorous scrutiny. Any unauthorized hooks, spliced instructions, inline detours, or injected payloads are immediately cataloged with high cryptographic confidence.
                    </p>
                    <p class="text-gray-300 leading-relaxed text-base">
                        <strong>File System & Artifact Tracing:</strong> Beyond active RAM inspection, gnessac scans prefetch files, recent document histories, temporary application directories, and registry hives to recover remnants of deleted cheat loaders, HWID spoofers, and macro software used during competitive sessions.
                    </p>
                    <p class="text-gray-300 leading-relaxed text-base">
                        <strong>Heuristic Macro & Input Analysis:</strong> Modern cheaters frequently rely on external hardware emulators and software macros. Our heuristic analysis algorithms evaluate input timing irregularities and mouse movement signatures to detect unauthorized automation frameworks effortlessly.
                    </p>
                    <p class="text-gray-300 leading-relaxed text-base mb-12">
                        Server moderators rely on our instant detection reports and cryptographic compliance screenshots to enforce fair-play standards with absolute certainty, ensuring competitive integrity across communities of all sizes.
                    </p>
                </div>

                <div id="docContentApi" class="doc-content-pane space-y-8" style="display: none;">
                    <h1 class="text-4xl font-extrabold mb-8 border-b border-[#27272a] pb-6">API & Enterprise Dashboard Integration Guide</h1>
                    <p class="text-gray-300 leading-relaxed text-base">
                        The gnessac API and enterprise administrative dashboards empower server networks, tournament organizers, and community developers to seamlessly automate moderation workflows, manage staff verification pins, and synchronize real-time anti-cheat telemetry directly with custom Discord bots, proprietary web panels, and internal ban databases.
                    </p>
                    <p class="text-gray-300 leading-relaxed text-base">
                        <strong>1. Authentication & API Header Standards:</strong> All REST API requests directed toward the gnessac enterprise gateway (<code class="text-blue-400 font-mono text-sm bg-[#121214] px-1.5 py-0.5 rounded border border-[#27272a]">https://api.gnessac.org/v2/</code>) must include a valid bearer token generated via your community dashboard. Include the following headers in every HTTP request:
                    </p>
                    <div class="bg-[#121214] border border-[#27272a] rounded-xl p-5 font-mono text-xs text-gray-300 space-y-1 overflow-x-auto">
                        <p class="text-blue-400">Authorization: Bearer gness_live_sec_998374a8bc1102ff</p>
                        <p class="text-gray-400">Content-Type: application/json</p>
                        <p class="text-gray-400">X-Community-ID: comm_minecraft_eu_01</p>
                    </div>
                    <p class="text-gray-300 leading-relaxed text-base">
                        <strong>2. Webhook Configuration & Real-Time Telemetry Streaming:</strong> Configure secure webhook endpoints to instantly broadcast scan results, hardware identification hashes (HWID), player timestamps, and compliance verification screenshots directly to your private staff channels the moment a screening session concludes. The following JSON payload schema is dispatched via HTTP POST:
                    </p>
                    <div class="bg-[#121214] border border-[#27272a] rounded-xl p-5 font-mono text-xs text-gray-300 space-y-1 overflow-x-auto">
                        <p class="text-gray-500">{</p>
                        <p class="pl-4 text-blue-400">"event": <span class="text-emerald-400">"scan_completed"</span>,</p>
                        <p class="pl-4 text-blue-400">"timestamp": <span class="text-amber-400">1783920194</span>,</p>
                        <p class="pl-4 text-blue-400">"player": <span class="text-emerald-400">"TargetUser_99"</span>,</p>
                        <p class="pl-4 text-blue-400">"hwid_hash": <span class="text-emerald-400">"a98f7c6e5d4b3a2f1e0"</span>,</p>
                        <p class="pl-4 text-blue-400">"status": <span class="text-emerald-400">"CLEAN_VERIFIED"</span>,</p>
                        <p class="pl-4 text-blue-400">"screenshot_url": <span class="text-emerald-400">"https://storage.gnessac.org/evidence/shot_8832.png"</span></p>
                        <p class="text-gray-500">}</p>
                    </div>
                    <p class="text-gray-300 leading-relaxed text-base">
                        <strong>3. Programmatic Pin Generation & Slot Management:</strong> Staff members can generate single-use verification pins programmatically via <code class="text-blue-400 font-mono text-sm bg-[#121214] px-1.5 py-0.5 rounded border border-[#27272a]">POST /v2/pins/generate</code>. The API returns an active numeric pin valid for 180 seconds, ensuring smooth queue management during peak tournament hours.
                    </p>
                    <p class="text-gray-300 leading-relaxed text-base mb-12">
                        Review our complete rate-limiting specifications (capped at 120 requests per minute per API key), error response codes, and SDK wrappers available in Python, Node.js, and C# to begin immediate integration with your infrastructure.
                    </p>
                </div>
            </div>
        </div>
    </main>

    <!-- 4. BRANDING SECTION -->
    <main id="branding" class="page-section">
        <div class="px-8 md:px-24 pt-16 pb-24 flex flex-col lg:flex-row gap-16">
            <aside class="w-full lg:w-1/4">
                <div class="text-xs font-bold text-gray-500 uppercase tracking-wider mb-4">On this page</div>
                <ul class="space-y-3 text-sm font-medium text-gray-400">
                    <li><a href="#brand-logo" class="hover:text-white transition">Logo</a></li>
                    <li><a href="#brand-color" class="hover:text-white transition">Color</a></li>
                    <li><a href="#brand-typography" class="hover:text-white transition">Typography</a></li>
                    <li><a href="#brand-spacing" class="hover:text-white transition">Spacing</a></li>
                    <li><a href="#brand-wallpapers" class="hover:text-white transition">Wallpapers</a></li>
                    <li><a href="#brand-naming" class="hover:text-white transition">Naming</a></li>
                </ul>
            </aside>

            <div class="w-full lg:w-3/4 max-w-4xl space-y-24">
                
                <section id="brand-logo" class="space-y-8">
                    <div class="flex justify-between items-center border-b border-[#27272a] pb-6">
                        <div>
                            <h2 class="text-3xl font-extrabold text-white mb-2">Logo</h2>
                            <p class="text-sm text-gray-400">Fixed aspect ratio. No distortion or effects. Same geometry across all backgrounds.</p>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                        <div class="bg-[#121214] border border-[#27272a] rounded-xl p-8 flex flex-col items-center justify-center min-h-[220px]">
                            <span class="font-mono text-3xl font-extrabold text-white tracking-tighter">(*></span>
                        </div>
                        <div class="bg-[#121214] border border-[#27272a] rounded-xl p-8 flex flex-col items-center justify-center min-h-[220px]">
                            <span class="font-mono text-2xl font-extrabold text-white tracking-tighter">}<(((((*></span>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 gap-4 text-xs font-semibold text-gray-400">
                        <div class="flex justify-between bg-[#121214]/60 border border-[#27272a] p-4 rounded-lg">
                            <span>Logo</span>
                            <div class="space-x-3"><a href="#" class="text-blue-400 hover:underline">SVG</a><a href="#" class="text-blue-400 hover:underline">PNG</a></div>
                        </div>
                        <div class="flex justify-between bg-[#121214]/60 border border-[#27272a] p-4 rounded-lg">
                            <span>Full logo</span>
                            <div class="space-x-3"><a href="#" class="text-blue-400 hover:underline">SVG</a><a href="#" class="text-blue-400 hover:underline">PNG</a></div>
                        </div>
                    </div>
                </section>

                <section id="brand-color" class="space-y-8">
                    <div class="border-b border-[#27272a] pb-6">
                        <h2 class="text-3xl font-extrabold text-white mb-2">Color</h2>
                        <p class="text-sm text-gray-400">Subtle blue-tinted neutrals and a single blue accent.</p>
                    </div>

                    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-4">
                        <div class="bg-[#121214] border border-[#27272a] rounded-xl p-4 flex flex-col justify-between h-48">
                            <div class="w-full h-24 rounded-lg bg-[#3A63EC]"></div>
                            <div>
                                <p class="text-xs font-bold text-white mt-3">Brand</p>
                                <p class="text-xs font-mono text-gray-400">#3A63EC</p>
                                <p class="text-[10px] text-gray-500 font-mono">rgb(58, 99, 236)</p>
                            </div>
                        </div>
                        <div class="bg-[#121214] border border-[#27272a] rounded-xl p-4 flex flex-col justify-between h-48">
                            <div class="w-full h-24 rounded-lg bg-[#090A0B] border border-gray-800"></div>
                            <div>
                                <p class="text-xs font-bold text-white mt-3">Background</p>
                                <p class="text-xs font-mono text-gray-400">#090A0B</p>
                                <p class="text-[10px] text-gray-500 font-mono">rgb(9, 10, 11)</p>
                            </div>
                        </div>
                        <div class="bg-[#121214] border border-[#27272a] rounded-xl p-4 flex flex-col justify-between h-48">
                            <div class="w-full h-24 rounded-lg bg-[#F6F7F8]"></div>
                            <div>
                                <p class="text-xs font-bold text-white mt-3">Text</p>
                                <p class="text-xs font-mono text-gray-400">#F6F7F8</p>
                                <p class="text-[10px] text-gray-500 font-mono">rgb(246, 247, 248)</p>
                            </div>
                        </div>
                        <div class="bg-[#121214] border border-[#27272a] rounded-xl p-4 flex flex-col justify-between h-48">
                            <div class="w-full h-24 rounded-lg bg-[#DFDFDF]"></div>
                            <div>
                                <p class="text-xs font-bold text-white mt-3">Logo</p>
                                <p class="text-xs font-mono text-gray-400">#DFDFDF</p>
                                <p class="text-[10px] text-gray-500 font-mono">rgb(223, 223, 223)</p>
                            </div>
                        </div>
                    </div>
                </section>

                <section id="brand-typography" class="space-y-8">
                    <div class="border-b border-[#27272a] pb-6">
                        <h2 class="text-3xl font-extrabold text-white mb-2">Typography</h2>
                        <p class="text-sm text-gray-400">Geist Sans for UI and communication, Geist Mono for data, Schibsted Grotesk for headings.</p>
                    </div>

                    <div class="bg-[#121214] border border-[#27272a] rounded-xl p-8 space-y-6">
                        <div class="text-5xl font-bold tracking-tight text-white">Aa</div>
                        <p class="text-lg font-medium text-gray-300 font-mono">gnessac - gnessac.org</p>
                    </div>

                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 text-sm">
                        <div class="bg-[#121214]/60 border border-[#27272a] p-5 rounded-lg">
                            <h4 class="font-bold text-white">Regular</h4>
                            <p class="text-xs text-gray-400 mt-1">400 · Body text</p>
                        </div>
                        <div class="bg-[#121214]/60 border border-[#27272a] p-5 rounded-lg">
                            <h4 class="font-bold text-white">Medium</h4>
                            <p class="text-xs text-gray-400 mt-1">500 · UI</p>
                        </div>
                        <div class="bg-[#121214]/60 border border-[#27272a] p-5 rounded-lg">
                            <h4 class="font-bold text-white">Semi-bold</h4>
                            <p class="text-xs text-gray-400 mt-1">600 · Subheadings</p>
                        </div>
                        <div class="bg-[#121214]/60 border border-[#27272a] p-5 rounded-lg">
                            <h4 class="font-bold text-white">Bold</h4>
                            <p class="text-xs text-gray-400 mt-1">700 · Headings</p>
                        </div>
                    </div>
                </section>

                <section id="brand-spacing" class="space-y-8">
                    <div class="border-b border-[#27272a] pb-6">
                        <h2 class="text-3xl font-extrabold text-white mb-2">Spacing</h2>
                        <p class="text-sm text-gray-400">The minimum spacing surrounding the symbol. Scales proportionally with the logo size.</p>
                    </div>
                    <div class="bg-[#121214] border border-[#27272a] rounded-xl p-8 flex items-center justify-center min-h-[185px]">
                        <span class="font-mono text-2xl font-bold text-white">(*></span>
                    </div>
                    <p class="text-xs text-gray-500 font-mono">Outer boundary = minimum clearance zone</p>
                </section>

                <section id="brand-wallpapers" class="space-y-8">
                    <div class="border-b border-[#27272a] pb-6">
                        <h2 class="text-3xl font-extrabold text-white mb-2">Wallpapers</h2>
                        <p class="text-sm text-gray-400">Official wallpapers for desktop and social media.</p>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                        <div class="bg-[#121214] border border-[#27272a] rounded-xl overflow-hidden flex flex-col justify-between">
                            <div class="p-8 h-48 bg-gradient-to-br from-[#18181b] to-[#09090b] flex flex-col items-center justify-center relative">
                                <div class="w-full max-w-[220px] bg-[#09090b] border border-[#27272a] rounded-lg p-3 shadow-xl font-mono text-[11px] space-y-2">
                                    <div class="flex justify-between items-center text-gray-400 border-b border-[#1f1f22] pb-1.5">
                                        <span class="text-blue-400 font-bold">(*> PC_SCAN</span>
                                        <span class="animate-pulse text-emerald-400">● LIVE</span>
                                    </div>
                                    <div class="space-y-1 text-gray-300">
                                        <div class="flex justify-between"><span>RAM_ALLOC:</span><span class="text-blue-400">PASSED</span></div>
                                        <div class="flex justify-between"><span>HOOK_DETECT:</span><span class="text-emerald-400">0 FOUND</span></div>
                                        <div class="w-full bg-[#1f1f22] h-1.5 rounded-full overflow-hidden mt-2">
                                            <div class="bg-blue-600 h-full animate-[pulse_1.5s_infinite]" style="width: 85%;"></div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <div class="p-5 flex justify-between items-center border-t border-[#27272a]">
                                <div>
                                    <p class="text-xs font-bold text-white">Desktop</p>
                                    <p class="text-[10px] text-gray-500 font-mono">1920x1080</p>
                                </div>
                                <a href="#" class="text-xs text-blue-400 font-semibold hover:underline">Download</a>
                            </div>
                        </div>

                        <div class="bg-[#121214] border border-[#27272a] rounded-xl overflow-hidden flex flex-col justify-between">
                            <div class="p-8 h-48 bg-gradient-to-br from-[#121214] to-[#000000] flex items-center justify-center relative">
                                <span class="font-mono text-3xl text-white font-bold">*</span>
                            </div>
                            <div class="p-5 flex justify-between items-center border-t border-[#27272a]">
                                <div>
                                    <p class="text-xs font-bold text-white">Desktop, animated (GIF)</p>
                                    <p class="text-[10px] text-gray-500 font-mono">1000x353</p>
                                </div>
                                <a href="#" class="text-xs text-blue-400 font-semibold hover:underline">Download</a>
                            </div>
                        </div>
                    </div>
                </section>

                <section id="brand-naming" class="space-y-8">
                    <div class="border-b border-[#27272a] pb-6">
                        <h2 class="text-3xl font-extrabold text-white mb-2">Naming</h2>
                        <p class="text-sm text-gray-400">Use the name consistently across communication and products.</p>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                        <div class="bg-[#121214] border border-[#27272a] rounded-xl p-6 space-y-4">
                            <h4 class="text-xs font-bold text-emerald-400 uppercase tracking-wider">Correct</h4>
                            <ul class="space-y-2 text-sm text-gray-300 font-medium">
                                <li>gnessac Anticheat</li>
                                <li>gnessac</li>
                                <li>gnessac.org</li>
                            </ul>
                        </div>
                        <div class="bg-[#121214] border border-[#27272a] rounded-xl p-6 space-y-4">
                            <h4 class="text-xs font-bold text-red-400 uppercase tracking-wider">Incorrect</h4>
                            <ul class="space-y-2 text-sm text-gray-400 font-medium line-through">
                                <li>GNESSAC ANTICHEAT</li>
                                <li>gnessacAC</li>
                                <li>gnessac Anti Cheat</li>
                            </ul>
                        </div>
                    </div>
                </section>

            </div>
        </div>
    </main>

    <!-- TERMS & PRIVACY POLICY SECTION -->
    <main id="terms" class="page-section">
        <div class="px-8 md:px-24 pt-16 pb-24 max-w-4xl mx-auto space-y-12">
            <div class="border-b border-[#27272a] pb-6">
                <h1 class="text-4xl font-extrabold text-white mb-2">Terms of Service & Privacy Policy</h1>
                <p class="text-sm text-gray-400">Last updated: November 2026 · gnessac.org Enterprise Compliance & Legal Framework</p>
            </div>

            <div class="space-y-10 text-gray-300 text-base leading-relaxed">
                <section class="space-y-4">
                    <h2 class="text-2xl font-bold text-white">1. Introduction, Jurisdiction, and Binding Agreement</h2>
                    <p>
                        Welcome to <strong class="text-white">gnessac Solutions</strong> (<span class="underline decoration-red-500 decoration-2 font-semibold text-white">"gnessac.org"</span>, <span class="underline decoration-red-500 decoration-2 font-semibold text-white">"we"</span>, <span class="underline decoration-red-500 decoration-2 font-semibold text-white">"our"</span>, or <span class="underline decoration-red-500 decoration-2 font-semibold text-white">"us"</span>). By accessing, downloading, installing, or otherwise utilizing any software applications, digital forensics modules, application programming interfaces (APIs), or online services provided on or through gnessac.org, you enter into a legally binding agreement governed by rigorous international corporate compliance standards.
                    </p>
                    <p>
                        Our anti-cheat and forensic auditing platform is meticulously engineered to protect competitive gaming ecosystems, esports tournaments, and dedicated community servers from malicious exploitation, unauthorized memory injections, and heuristic circumvention vectors. By deploying our infrastructure, you expressly warrant that you possess the legal authority to bind yourself or your corporate entity to these terms. <span class="underline decoration-red-500 decoration-2 font-semibold text-white">If you do not agree to every explicit covenant, restriction, and warranty disclaimer contained herein, you must immediately cease all access and permanently delete all gnessac binaries from your hardware.</span>
                    </p>
                </section>

                <section class="space-y-4">
                    <h2 class="text-2xl font-bold text-white">2. Scope of Digital Forensics & Anti-Cheat Infrastructure</h2>
                    <p>
                        The gnessac platform provides advanced post-mortem digital forensics and real-time screenshare verification services. Our proprietary scanning binaries inspect volatile system memory, running process image headers, prefetch logs, temporary execution directories, and pre-boot environments solely for the purpose of identifying illicit modifications, unauthorized macro automation, DLL injection frameworks, and kernel-level bypasses.
                    </p>
                    <p>
                        <span class="underline decoration-red-500 decoration-2 font-semibold text-white">Our diagnostic engine operates under strict operational boundaries designed to isolate cheating vectors without compromising core operating system stability.</span> Server administrators and community moderators utilizing our administrative dashboard are granted non-exclusive, revocable licenses to execute scans exclusively within authorized competitive environments. Any deployment of gnessac technology outside authorized gaming networks or for unauthorized surveillance is strictly prohibited.
                    </p>
                </section>

                <section class="space-y-4">
                    <h2 class="text-2xl font-bold text-white">3. Data Privacy, Telemetry Collection, and Information Handling</h2>
                    <p>
                        Protecting user confidentiality and personal privacy remains a foundational pillar of gnessac operations. When a diagnostic scan is initiated via an authenticated verification pin, our software collects strictly necessary anti-cheat telemetry, hardware identification hashes (<span class="underline decoration-red-500 decoration-2 font-semibold text-white">HWID</span>), and a single encrypted compliance screenshot captured at the exact conclusion of the screening session.
                    </p>
                    <p>
                        <span class="underline decoration-red-500 decoration-2 font-semibold text-white">We maintain an absolute zero-tolerance policy regarding the harvesting of personal documents, private web browsing histories, financial statements, and confidential communications.</span> All diagnostic logs and compliance screenshots transmitted to our secure cloud infrastructure are automatically purged after twenty-one (21) calendar days, ensuring complete adherence to international data protection regulations and privacy directives.
                    </p>
                </section>

                <section class="space-y-4">
                    <h2 class="text-2xl font-bold text-white">4. User Conduct, Security Covenants, and Prohibited Actions</h2>
                    <p>
                        Users and corporate clients agree to maintain the highest standards of professional conduct while interacting with our platform and client software. <span class="underline decoration-red-500 decoration-2 font-semibold text-white">Any attempt to decompile, reverse engineer, disassemble, debug, tamper with, or bypass the cryptographic protection routines and process integrity safeguards embedded within gnessac binaries is strictly prohibited.</span>
                    </p>
                    <p>
                        Engaging in unauthorized penetration testing, API stress flooding, credential harvesting, or exploitation of our staff moderation pins will result in immediate, permanent account termination, cryptographic hardware blacklisting, and potential legal prosecution under applicable cybercrime legislation.
                    </p>
                </section>

                <section class="space-y-4">
                    <h2 class="text-2xl font-bold text-white">5. Intellectual Property Rights and Trademark Protection</h2>
                    <p>
                        All software code, visual assets, documentation architectures, trademarked brand names (<span class="underline decoration-red-500 decoration-2 font-semibold text-white">gnessac</span>), logos, and proprietary scanning methodologies displayed across gnessac.org are the exclusive intellectual property of gnessac Solutions.
                    </p>
                    <p>
                        Nothing contained within these Terms of Service shall be construed as conferring any license or right under any gnessac patent, copyright, trademark, or trade secret. Unauthorized reproduction, redistribution, or commercial exploitation of our branding or source code is strictly prohibited by international intellectual property treaties.
                    </p>
                </section>

                <section class="space-y-4">
                    <h2 class="text-2xl font-bold text-white">6. Limitation of Liability and Comprehensive Warranty Disclaimers</h2>
                    <p>
                        The gnessac platform, software binaries, and associated APIs are provided on an <span class="underline decoration-red-500 decoration-2 font-semibold text-white">"AS IS"</span> and <span class="underline decoration-red-500 decoration-2 font-semibold text-white">"AS AVAILABLE"</span> basis without warranties of any kind, either express or implied, including but not limited to implied warranties of merchantability, fitness for a particular purpose, or non-infringement.
                    </p>
                    <p>
                        In no event shall gnessac, its executive officers, developers, or corporate affiliates be held liable for any direct, indirect, incidental, special, punitive, or consequential damages—including loss of data, revenue, or competitive standing—arising out of or in any way connected with the use, operational delay, or inability to use our anti-cheat infrastructure.
                    </p>
                </section>

                <section class="space-y-4">
                    <h2 class="text-2xl font-bold text-white">7. Modifications to Terms and Official Corporate Contact</h2>
                    <p>
                        gnessac reserves the right to modify, amend, or update these Terms of Service and Privacy Policy at any time at its sole discretion. Continued use of our platform following the posting of revised terms constitutes your explicit acceptance of such changes.
                    </p>
                    <p>
                        For all legal notices, compliance inquiries, data privacy requests, or enterprise support questions, please contact our administrative department directly via our official corporate email at <span class="underline decoration-red-500 decoration-2 font-mono text-white">gnesssoftware@outlook.com</span> or through our verified Discord community portal.
                    </p>
                </section>
            </div>
        </div>
    </main>

    <!-- 5. FAQ SECTION -->
    <main id="faq" class="page-section">
        <div class="px-8 md:px-24 pt-16 pb-24 flex flex-col lg:flex-row gap-16">
            <div class="lg:w-1/3">
                <h2 class="text-4xl font-extrabold mb-4 leading-tight">Frequently Asked Questions <span class="border-b-4 border-blue-600 pb-1 block w-max">about gnessac services</span></h2>
                <p class="text-gray-400 mt-6 text-sm">Need further assistance? <a href="https://discord.com/" target="_blank" class="text-white font-semibold hover:underline">Join our official Discord</a> or contact <span class="text-white font-mono">gnesssoftware@outlook.com</span>.</p>
            </div>
            <div class="lg:w-2/3 space-y-3">
                <div class="faq-item bg-[#121214]/80 rounded-lg p-5 cursor-pointer border border-[#27272a] hover:border-gray-600 transition" onclick="toggleFaq(this)">
                    <div class="flex justify-between items-center">
                        <h3 class="font-bold text-gray-200">1. What is gnessac and how does its forensic screenshare technology function?</h3>
                        <span class="faq-icon text-gray-500 transition-transform">▼</span>
                    </div>
                    <div class="faq-content">
                        gnessac is an advanced digital forensics and anti-cheat platform engineered to perform post-mortem integrity scans on client systems. When initialized via a staff-generated verification pin, gnessac inspects volatile memory states, loaded module headers, prefetch logs, and temporary storage artifacts to uncover hidden cheat software, DLL injectors, and kernel-level bypasses without compromising user privacy.
                    </div>
                </div>

                <div class="faq-item bg-[#121214]/80 rounded-lg p-5 cursor-pointer border border-[#27272a] hover:border-gray-600 transition" onclick="toggleFaq(this)">
                    <div class="flex justify-between items-center">
                        <h3 class="font-bold text-gray-200">2. Is gnessac free to use, and what are the limitations for unsupported games?</h3>
                        <span class="faq-icon text-gray-500 transition-transform">▼</span>
                    </div>
                    <div class="faq-content">
                        gnessac provides free screening access exclusively for Minecraft Java (up to three scans per day when linked with a verified Discord account, or one scan per day without linkage). All other supported gaming environments, including FiveM, GTA V, Rust, San Andreas, and Counter-Strike 2, require an active paid subscription tier with unlimited pin generation capabilities.
                    </div>
                </div>

                <div class="faq-item bg-[#121214]/80 rounded-lg p-5 cursor-pointer border border-[#27272a] hover:border-gray-600 transition" onclick="toggleFaq(this)">
                    <div class="flex justify-between items-center">
                        <h3 class="font-bold text-gray-200">3. Can a player prematurely terminate or close the gnessac client during an active scan?</h3>
                        <span class="faq-icon text-gray-500 transition-transform">▼</span>
                    </div>
                    <div class="faq-content">
                        No. Once initialized with a valid cryptographic staff pin, gnessac establishes strict process protection routines preventing premature termination via Task Manager or external process killers until the complete diagnostic sequence and compliance screenshot capture successfully conclude.
                    </div>
                </div>

                <div class="faq-item bg-[#121214]/80 rounded-lg p-5 cursor-pointer border border-[#27272a] hover:border-gray-600 transition" onclick="toggleFaq(this)">
                    <div class="flex justify-between items-center">
                        <h3 class="font-bold text-gray-200">4. What specific data is accessed, and how does gnessac comply with data privacy standards?</h3>
                        <span class="faq-icon text-gray-500 transition-transform">▼</span>
                    </div>
                    <div class="faq-content">
                        gnessac strictly limits data collection to anti-cheat diagnostic logs, hardware identification hashes (HWID), and a single desktop compliance screenshot captured at the end of the scan. Personal documents, private chat histories, web browser logs, and financial records are never accessed, indexed, or stored. All telemetry is purged automatically after 21 days.
                    </div>
                </div>

                <div class="faq-item bg-[#121214]/80 rounded-lg p-5 cursor-pointer border border-[#27272a] hover:border-gray-600 transition" onclick="toggleFaq(this)">
                    <div class="flex justify-between items-center">
                        <h3 class="font-bold text-gray-200">5. How quickly are scan results and detection telemetry delivered to community administrators?</h3>
                        <span class="faq-icon text-gray-500 transition-transform">▼</span>
                    </div>
                    <div class="faq-content">
                        Scan results and cryptographic verification reports are processed instantly upon completion (typically within 60 seconds) and securely streamed in real-time directly to the authorized staff dashboard or configured Discord webhook channels.
                    </div>
                </div>

                <div class="faq-item bg-[#121214]/80 rounded-lg p-5 cursor-pointer border border-[#27272a] hover:border-gray-600 transition" onclick="toggleFaq(this)">
                    <div class="flex justify-between items-center">
                        <h3 class="font-bold text-gray-200">6. Can server owners integrate gnessac logs with custom Discord bots and moderation panels?</h3>
                        <span class="faq-icon text-gray-500 transition-transform">▼</span>
                    </div>
                    <div class="faq-content">
                        Yes. Our enterprise tier and community dashboards support robust webhook configurations and REST API endpoints, enabling server networks to automatically broadcast scan outcomes, logs, and verification badges directly into private Discord staff channels.
                    </div>
                </div>

                <div class="faq-item bg-[#121214]/80 rounded-lg p-5 cursor-pointer border border-[#27272a] hover:border-gray-600 transition" onclick="toggleFaq(this)">
                    <div class="flex justify-between items-center">
                        <h3 class="font-bold text-gray-200">7. What happens if a subscription payment is completed but access is not granted?</h3>
                        <span class="faq-icon text-gray-500 transition-transform">▼</span>
                    </div>
                    <div class="faq-content">
                        If you encounter any licensing synchronization issues or active membership activation delays following checkout, please contact our administrative team immediately at gnesssoftware@outlook.com with your transaction details for prompt resolution.
                    </div>
                </div>

                <div class="faq-item bg-[#121214]/80 rounded-lg p-5 cursor-pointer border border-[#27272a] hover:border-gray-600 transition" onclick="toggleFaq(this)">
                    <div class="flex justify-between items-center">
                        <h3 class="font-bold text-gray-200">8. Does gnessac support behavioral and input macro detection alongside memory scans?</h3>
                        <span class="faq-icon text-gray-500 transition-transform">▼</span>
                    </div>
                    <div class="faq-content">
                        Yes. In addition to physical memory and file system artifact inspection, gnessac incorporates heuristic behavioral monitoring algorithms that analyze input timing distributions and execution anomalies to detect unauthorized macro tools and aim assistance software.
                    </div>
                </div>

                <div class="faq-item bg-[#121214]/80 rounded-lg p-5 cursor-pointer border border-[#27272a] hover:border-gray-600 transition" onclick="toggleFaq(this)">
                    <div class="flex justify-between items-center">
                        <h3 class="font-bold text-gray-200">9. What operating systems are officially supported by the gnessac client and infrastructure?</h3>
                        <span class="faq-icon text-gray-500 transition-transform">▼</span>
                    </div>
                    <div class="faq-content">
                        gnessac fully supports Windows (Windows 10, Windows 11 - 64-bit architectures) and Linux client environments, ensuring seamless compatibility across all major competitive gaming platforms and community server setups.
                    </div>
                </div>

                <div class="faq-item bg-[#121214]/80 rounded-lg p-5 cursor-pointer border border-[#27272a] hover:border-gray-600 transition" onclick="toggleFaq(this)">
                    <div class="flex justify-between items-center">
                        <h3 class="font-bold text-gray-200">10. How can server administrators obtain technical support or request custom integrations?</h3>
                        <span class="faq-icon text-gray-500 transition-transform">▼</span>
                    </div>
                    <div class="faq-content">
                        Administrators can access dedicated technical assistance through our official Discord community channels, comprehensive documentation portals, or by submitting direct inquiries to our corporate email at gnesssoftware@outlook.com.
                    </div>
                </div>
            </div>
        </div>
    </main>

    <!-- 6. LOGIN SECTION -->
    <main id="login" class="page-section">
        <div class="flex items-center justify-center min-h-[80vh] px-4">
            <div class="w-full max-w-md bg-[#121214] border border-[#27272a] rounded-xl p-8 shadow-2xl relative z-10">
                <div class="mb-6 font-mono text-xl text-white font-bold">(*></div>
                <h2 class="text-2xl font-bold text-white mb-2">Login</h2>
                <p class="text-sm text-gray-400 mb-6">Enter your credentials to access your account</p>
                
                <div id="loginAlert" class="hidden mb-6 p-4 bg-red-950/40 border border-red-800/60 rounded-lg text-sm text-red-300">
                    <p class="font-semibold mb-1">Active membership not found!</p>
                    <p class="text-xs text-red-400 leading-relaxed">No active subscription or membership was found for this account. Please contact support at <span class="text-white font-mono underline">gnesssoftware@outlook.com</span> for assistance.</p>
                </div>

                <form class="space-y-4" onsubmit="handleLogin(event)">
                    <div>
                        <input type="text" id="loginUser" placeholder="Email or Username" required class="w-full bg-[#09090b] border border-[#27272a] rounded p-3 text-sm focus:outline-none focus:border-blue-500 transition text-white">
                    </div>
                    <div class="relative">
                        <input type="password" id="loginPass" placeholder="Password" required class="w-full bg-[#09090b] border border-[#27272a] rounded p-3 text-sm focus:outline-none focus:border-blue-500 transition text-white">
                        <span class="absolute right-4 top-3.5 text-gray-500 cursor-pointer hover:text-white">👁</span>
                    </div>
                    <div class="text-right">
                        <a href="#" class="text-xs text-gray-400 hover:text-white">Forgot your password?</a>
                    </div>
                    <button type="submit" class="w-full neon-btn py-3.5 rounded-lg text-white font-bold flex justify-center items-center gap-2 mt-2 cursor-pointer">
                        <span>→]</span> Login
                    </button>
                    
                    <div class="relative flex py-6 items-center">
                        <div class="flex-grow border-t border-[#27272a]"></div>
                        <span class="flex-shrink-0 mx-4 text-gray-500 text-xs">Or continue with</span>
                        <div class="flex-grow border-t border-[#27272a]"></div>
                    </div>
                    
                    <div class="flex gap-4">
                        <button type="button" onclick="showLoginAlert()" class="w-1/2 py-2.5 border border-[#27272a] rounded hover:bg-[#27272a] text-sm font-semibold flex items-center justify-center gap-2 transition cursor-pointer">Discord</button>
                        <button type="button" onclick="showLoginAlert()" class="w-1/2 py-2.5 border border-[#27272a] rounded hover:bg-[#27272a] text-sm font-semibold flex items-center justify-center gap-2 transition cursor-pointer">Passkey</button>
                    </div>
                    
                    <div class="text-center mt-8 text-sm text-gray-400">
                        Don't have an account? <a onclick="navigate('register')" class="text-white font-bold hover:underline cursor-pointer">Register</a>
                    </div>
                </form>
            </div>
        </div>
    </main>

    <!-- 7. REGISTER SECTION -->
    <main id="register" class="page-section">
        <div class="flex items-center justify-center min-h-[80vh] px-4">
            <div class="w-full max-w-md bg-[#121214] border border-[#27272a] rounded-xl p-8 shadow-2xl relative z-10">
                <div class="mb-6 font-mono text-xl text-white font-bold">(*></div>
                <div class="flex items-center justify-between text-xs text-gray-500 font-bold mb-2 uppercase tracking-wide">
                    <span id="regStep1Indicator" class="text-blue-500">Username</span>
                    <span id="regStep2Indicator" class="text-gray-500">Email</span>
                    <span id="regStep3Indicator" class="text-gray-500">Password</span>
                </div>
                <div class="w-full h-1 bg-[#27272a] rounded-full mb-8 overflow-hidden">
                    <div id="regProgressBar" class="w-1/3 h-full bg-blue-600 transition-all duration-300"></div>
                </div>
                
                <div id="regStepLabel" class="text-xs text-blue-400 font-semibold mb-1">Step 1 of 3</div>
                <h2 id="regTitle" class="text-2xl font-bold text-white mb-2">Pick a username</h2>
                <p id="regDesc" class="text-sm text-gray-400 mb-6">Pick something unique and memorable</p>
                
                <div id="regSuccessAlert" class="hidden mb-6 p-4 bg-blue-950/40 border border-blue-800/60 rounded-lg text-sm text-blue-300">
                    <p class="font-semibold mb-1">Application Received Successfully</p>
                    <p class="text-xs text-blue-400 leading-relaxed">Your registration request has been successfully received. Our team will review your application and get back to you shortly.</p>
                </div>

                <form id="regForm" class="space-y-6" onsubmit="handleRegisterSubmit(event)">
                    <div id="regInputContainer">
                        <label id="regInputLabel" class="block text-xs font-semibold text-gray-400 mb-2">Username</label>
                        <input type="text" id="regInputField" placeholder="Enter your username" required class="w-full bg-[#09090b] border border-[#27272a] rounded p-3 text-sm focus:outline-none focus:border-blue-500 transition text-white">
                    </div>
                    <button type="submit" id="regSubmitBtn" class="w-full bg-blue-600/80 hover:bg-blue-600 py-3.5 rounded-lg text-white font-bold transition cursor-pointer">
                        Continue
                    </button>
                    <div class="text-center mt-6 text-sm text-gray-400">
                        Already have an account? <a onclick="navigate('login')" class="text-white font-bold hover:underline cursor-pointer">Log in</a>
                    </div>
                </form>
            </div>
        </div>
    </main>

    <!-- JavaScript Application Logic -->
    <script>
        // SPA Navigation Routing
        function navigate(viewId, navElement = null) {
            document.querySelectorAll('.page-section').forEach(el => {
                el.style.display = 'none';
                el.classList.remove('active');
            });
            
            const target = document.getElementById(viewId);
            if(target) {
                target.style.display = 'block';
                void target.offsetWidth;
                target.classList.add('active');
            }

            if (navElement && navElement.classList.contains('nav-link')) {
                document.querySelectorAll('.nav-link').forEach(link => link.classList.remove('active'));
                navElement.classList.add('active');
            } else if (viewId) {
                document.querySelectorAll('.nav-link').forEach(link => link.classList.remove('active'));
                const matchedLink = document.querySelector(`.nav-link[onclick*="navigate('${viewId}'"]`);
                if(matchedLink) matchedLink.classList.add('active');
            }
            
            const canvas = document.getElementById('matrixCanvas');
            if(viewId === 'login' || viewId === 'register') {
                canvas.style.opacity = '0.35';
            } else {
                canvas.style.opacity = '0.25';
            }
            window.scrollTo(0, 0);
        }

        function handleLogin(event) {
            event.preventDefault();
            showLoginAlert();
        }

        function showLoginAlert() {
            const alertBox = document.getElementById('loginAlert');
            alertBox.classList.remove('hidden');
            alertBox.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
        }

        function switchDocTab(tabId, clickedElement) {
            document.getElementById('docContentOverview').style.display = 'none';
            document.getElementById('docContentDetections').style.display = 'none';
            document.getElementById('docContentApi').style.display = 'none';

            document.getElementById('docNavOverview').className = "cursor-pointer hover:text-white flex justify-between items-center pl-3 py-1 transition";
            document.getElementById('docNavOverview').style.borderLeft = "none";
            document.getElementById('docNavOverview').style.color = "#9ca3af";

            document.getElementById('docNavDetections').className = "cursor-pointer hover:text-white flex justify-between items-center pl-3 py-1 transition";
            document.getElementById('docNavDetections').style.borderLeft = "none";
            document.getElementById('docNavDetections').style.color = "#9ca3af";

            document.getElementById('docNavApi').className = "cursor-pointer hover:text-white flex justify-between items-center pl-3 py-1 transition";
            document.getElementById('docNavApi').style.borderLeft = "none";
            document.getElementById('docNavApi').style.color = "#9ca3af";

            if (tabId === 'overview') {
                document.getElementById('docContentOverview').style.display = 'block';
                clickedElement.className = "cursor-pointer text-white pl-3 transition";
                clickedElement.style.borderLeft = "2px solid #3b82f6";
                clickedElement.style.color = "#ffffff";
            } else if (tabId === 'detections') {
                document.getElementById('docContentDetections').style.display = 'block';
                clickedElement.className = "cursor-pointer text-white flex justify-between items-center pl-3 py-1 transition";
                clickedElement.style.borderLeft = "2px solid #3b82f6";
                clickedElement.style.color = "#ffffff";
            } else if (tabId === 'api') {
                document.getElementById('docContentApi').style.display = 'block';
                clickedElement.className = "cursor-pointer text-white flex justify-between items-center pl-3 py-1 transition";
                clickedElement.style.borderLeft = "2px solid #3b82f6";
                clickedElement.style.color = "#ffffff";
            }
        }

        function selectGame(gameName, btnElement) {
            const buttons = document.querySelectorAll('#pricingTabs button');
            buttons.forEach(btn => {
                btn.className = "px-5 py-2 text-sm font-medium rounded border border-[#27272a] hover:bg-[#18181b] text-gray-400 cursor-pointer transition";
                if (btn.innerText.trim() === gameName) {
                    btn.className = "px-5 py-2 text-sm font-medium rounded bg-blue-600 text-white cursor-pointer transition";
                }
            });

            document.getElementById('plan1Title').innerText = `gnessac (${gameName}) - Yearly Personal`;
            document.getElementById('plan1Desc').innerText = `Screenshare scan for ${gameName}.`;

            document.getElementById('plan2Title').innerText = `gnessac (${gameName}) - 6 Month Personal`;
            document.getElementById('plan2Desc').innerText = `Screenshare scan for ${gameName}.`;

            document.getElementById('plan3Title').innerText = `gnessac (${gameName}) - Monthly Personal`;
            document.getElementById('plan3Desc').innerText = `Screenshare scan for ${gameName}.`;
        }

        function selectGameAndNavigate(gameName) {
            navigate('pricing');
            const buttons = document.querySelectorAll('#pricingTabs button');
            buttons.forEach(btn => {
                if (btn.innerText.trim() === gameName) {
                    selectGame(gameName, btn);
                }
            });
        }

        function handlePurchase(planType) {
            navigate('login');
        }

        let regData = { username: '', email: '', password: '' };
        let currentRegStep = 1;

        function handleRegisterSubmit(event) {
            event.preventDefault();
            const inputField = document.getElementById('regInputField');
            const val = inputField.value.trim();

            if (!val) return;

            if (currentRegStep === 1) {
                regData.username = val;
                currentRegStep = 2;
                document.getElementById('regStep1Indicator').className = "text-gray-400";
                document.getElementById('regStep2Indicator').className = "text-blue-500";
                document.getElementById('regProgressBar').style.width = "66%";
                document.getElementById('regStepLabel').innerText = "Step 2 of 3";
                document.getElementById('regTitle').innerText = "Enter your email";
                document.getElementById('regDesc').innerText = "We'll use this for account recovery and alerts";
                document.getElementById('regInputLabel').innerText = "Email Address";
                inputField.type = "email";
                inputField.placeholder = "Enter your email address";
                inputField.value = "";
                inputField.focus();
            } else if (currentRegStep === 2) {
                regData.email = val;
                currentRegStep = 3;
                document.getElementById('regStep2Indicator').className = "text-gray-400";
                document.getElementById('regStep3Indicator').className = "text-blue-500";
                document.getElementById('regProgressBar').style.width = "100%";
                document.getElementById('regStepLabel').innerText = "Step 3 of 3";
                document.getElementById('regTitle').innerText = "Create a password";
                document.getElementById('regDesc').innerText = "Protect your account with a secure password";
                document.getElementById('regInputLabel').innerText = "Password";
                inputField.type = "password";
                inputField.placeholder = "Enter your password";
                inputField.value = "";
                inputField.focus();
                document.getElementById('regSubmitBtn').innerText = "Complete Registration";
            } else if (currentRegStep === 3) {
                regData.password = val;
                document.getElementById('regForm').style.display = 'none';
                document.getElementById('regSuccessAlert').classList.remove('hidden');
                
                setTimeout(() => {
                    navigate('login');
                    currentRegStep = 1;
                    regData = { username: '', email: '', password: '' };
                    document.getElementById('regForm').style.display = 'block';
                    document.getElementById('regSuccessAlert').classList.add('hidden');
                    document.getElementById('regStep1Indicator').className = "text-blue-500";
                    document.getElementById('regStep2Indicator').className = "text-gray-500";
                    document.getElementById('regStep3Indicator').className = "text-gray-500";
                    document.getElementById('regProgressBar').style.width = "33%";
                    document.getElementById('regStepLabel').innerText = "Step 1 of 3";
                    document.getElementById('regTitle').innerText = "Pick a username";
                    document.getElementById('regDesc').innerText = "Pick something unique and memorable";
                    document.getElementById('regInputLabel').innerText = "Username";
                    inputField.type = "text";
                    inputField.placeholder = "Enter your username";
                    inputField.value = "";
                    document.getElementById('regSubmitBtn').innerText = "Continue";
                }, 3500);
            }
        }

        // FAQ Accordion Toggle
        function toggleFaq(element) {
            element.classList.toggle('active');
        }

        // Home Enterprise Accordion Toggle
        function toggleHomeAccordion(headerEl) {
            const content = document.getElementById('homeAccordionContent');
            const icon = headerEl.querySelector('.home-acc-icon');
            if (content.style.display === 'none') {
                content.style.display = 'block';
                icon.style.transform = 'rotate(180deg)';
            } else {
                content.style.display = 'none';
                icon.style.transform = 'rotate(0deg)';
            }
        }
    </script>

    <!-- Matrix 0 and 1 Background Canvas -->
    <script>
        const canvas = document.getElementById('matrixCanvas');
        const ctx = canvas.getContext('2d');
        
        let w = canvas.width = window.innerWidth;
        let h = canvas.height = window.innerHeight;
        
        window.addEventListener('resize', () => { 
            w = canvas.width = window.innerWidth; 
            h = canvas.height = window.innerHeight; 
            initMatrixColumns();
        });

        const fontSize = 18;
        let columns = 0;
        let drops = [];

        function initMatrixColumns() {
            columns = Math.floor(w / fontSize);
            drops = [];
            for (let i = 0; i < columns; i++) {
                drops[i] = Math.floor(Math.random() * -100);
            }
        }
        initMatrixColumns();

        function drawMatrix() {
            ctx.fillStyle = 'rgba(9, 9, 11, 0.12)';
            ctx.fillRect(0, 0, w, h);

            ctx.font = `700 ${fontSize}px monospace`;

            for (let i = 0; i < drops.length; i++) {
                const text = Math.random() > 0.5 ? '1' : '0';
                
                const rand = Math.random();
                if (rand > 0.85) {
                    ctx.fillStyle = '#818cf8';
                } else if (rand > 0.40) {
                    ctx.fillStyle = '#3b82f6';
                } else {
                    ctx.fillStyle = '#1e293b';
                }

                ctx.fillText(text, i * fontSize, drops[i] * fontSize);

                if (drops[i] * fontSize > h && Math.random() > 0.975) {
                    drops[i] = 0;
                }
                drops[i]++;
            }

            requestAnimationFrame(drawMatrix);
        }

        function startTypewriterLoop() {
            const part1 = "Forensic\n";
            const part2 = "screenshot";

            function runTypewriter() {
                const typedElement = document.getElementById('typedText');
                if (!typedElement) return;

                typedElement.innerHTML = "";
                let fullString = part1 + part2;
                let charIndex = 0;

                function typeChar() {
                    if (charIndex < fullString.length) {
                        let partial = fullString.substring(0, charIndex + 1);
                        
                        let formattedHTML = "";
                        if (charIndex < part1.length) {
                            formattedHTML = partial.replace('\n', '<br>');
                        } else {
                            let p1Formatted = part1.replace('\n', '<br>');
                            let p2Part = partial.substring(part1.length);
                            formattedHTML = p1Formatted + `<span class="text-blue-500">${p2Part}</span>`;
                        }

                        typedElement.innerHTML = formattedHTML;
                        charIndex++;
                        setTimeout(typeChar, 70);
                    } else {
                        setTimeout(runTypewriter, 3000);
                    }
                }
                typeChar();
            }
            runTypewriter();
        }

        window.onload = function() { 
            navigate('home');
            initMatrixColumns();
            drawMatrix();
            startTypewriterLoop();
        };

        // Mouse trailing anti-cheat code matrix effect
        let lastMouseX = 0;
        let lastMouseY = 0;
        let mouseMoveCounter = 0;

        document.addEventListener('mousemove', function(e) {
            lastMouseX = e.clientX;
            lastMouseY = e.clientY;
            mouseMoveCounter++;

            if (mouseMoveCounter % 4 === 0) {
                const anticheatNames = [
                    "Vanguard_Drv", 
                    "EasyAntiCheat", 
                    "BattlEye_Core",
                    "VAC_Secure", 
                    "TP_Memory_Scan", 
                    "XignCode3",
                    "GameGuard", 
                    "Ace_Kernel", 
                    "Kernel_Hook", 
                    "HWID_Guard"
                ];

                const container = document.body;
                const span = document.createElement('div');
                const randomName = anticheatNames[Math.floor(Math.random() * anticheatNames.length)];
                const randomHex = '0x' + Math.floor(Math.random()*16777215).toString(16).toUpperCase();
                
                span.innerText = `[TRACE] ${randomName}:${randomHex}`;
                span.style.position = 'fixed';
                span.style.left = (lastMouseX + 18) + 'px';
                span.style.top = (lastMouseY + 18) + 'px';
                span.style.fontFamily = 'monospace';
                span.style.fontSize = '10px';
                
                span.style.color = Math.random() > 0.5 ? '#ef4444' : '#ffffff';

                span.style.zIndex = '9999';
                span.style.pointerEvents = 'none';
                span.style.transition = 'all 0.8s ease-out';
                span.style.opacity = '0.95';

                container.appendChild(span);

                setTimeout(() => {
                    span.style.opacity = '0';
                    span.style.transform = `translate(${Math.random() * 60 - 30}px, ${Math.random() * -60 - 20}px) scale(0.85)`;
                }, 30);

                setTimeout(() => {
                    span.remove();
                }, 900);
            }
        });
    </script>
</body>
</html>
