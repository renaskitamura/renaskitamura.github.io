<!--
PALETTE: Matrix Emerald (Slate 950 bg, Emerald #10b981, Amber #f59e0b, Blue #3b82f6)
PLAN: Section 1: Intro to Mental Math. Section 2: Expanded Trade-Off Analysis (/17 to /30). Section 3: The Magic Number Method (Workflow). Section 4: The /24 Baseline Cheat Sheet. Section 5: LinkedIn Profile Link & Attribution.
CHOICES:
1. Networks vs Hosts Trade-off -> Goal: Compare -> Grouped Bar Chart with Logarithmic Scale (Chart.js). Justification: Shows the inverse relationship across a massive range (/17 to /30). Using a log scale allows us to see both thousands and single digits clearly. No SVG used.
2. Magic Number Flow -> Goal: Organize -> HTML/CSS Block Diagram. Justification: Sequential mental math steps are best shown in a clear top-down flow. No SVG used.
3. Profile Footer -> Goal: Inform -> Styled HTML/CSS anchor. Justification: Provides a clear call-to-action for networking. No SVG used.
CONFIRMATION: NEITHER Mermaid JS NOR SVG were used anywhere in the output.
-->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IPv4 Fast Subnetting Mastery</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 1000px;
            margin-left: auto;
            margin-right: auto;
            height: 400px;
            max-height: 500px;
        }
        @media (max-width: 768px) {
            .chart-container { height: 300px; }
        }
        body {
            background-color: #020617;
            color: #f8fafc;
        }
        .card {
            background-color: #0f172a;
            border: 1px solid #1e293b;
        }
    </style>
</head>
<body class="antialiased selection:bg-emerald-500 selection:text-slate-900">

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
        
        <header class="text-center mb-20">
            <!-- Increased margin-bottom (mb-12) and added padding-bottom (pb-2) to prevent descender clipping -->
            <h1 class="text-4xl md:text-5xl font-extrabold tracking-tight mb-12 pb-2 leading-tight text-transparent bg-clip-text bg-gradient-to-r from-emerald-400 to-blue-500">
                IPv4 Subnetting: Mental Math Mastery
            </h1>
            <p class="text-xl text-slate-400 max-w-3xl mx-auto leading-relaxed">
                Time is the primary constraint on the CCNA. By mastering the <strong>Magic Number</strong> method and internalizing common boundaries, you can solve subnetting problems in seconds without a calculator.
            </p>
        </header>

        <section class="mb-12 grid grid-cols-1 md:grid-cols-3 gap-6 text-center">
            <div class="card p-6 rounded-xl shadow-lg border-t-4 border-t-emerald-500">
                <div class="text-lg text-slate-300 mb-2 uppercase tracking-wide font-bold">The Golden Rule</div>
                <div class="text-2xl font-black text-emerald-400">Total = 32 Bits</div>
                <div class="text-slate-400 text-sm mt-2">Network Bits + Host Bits = 32. Understanding this balance is the key to identifying host capacity instantly.</div>
            </div>
            <div class="card p-6 rounded-xl shadow-lg border-t-4 border-t-amber-500">
                <div class="text-lg text-slate-300 mb-2 uppercase tracking-wide font-bold">Usable Hosts Formula</div>
                <div class="text-2xl font-black text-amber-400">2<sup class="text-lg">h</sup> - 2</div>
                <div class="text-slate-400 text-sm mt-2">Always subtract 2: one for the Network ID (all 0s in host bits) and one for the Broadcast (all 1s).</div>
            </div>
            <div class="card p-6 rounded-xl shadow-lg border-t-4 border-t-blue-500">
                <div class="text-lg text-slate-300 mb-2 uppercase tracking-wide font-bold">The Constant</div>
                <div class="text-2xl font-black text-blue-400">256</div>
                <div class="text-slate-400 text-sm mt-2">256 is the magic ceiling of a single octet. It is the anchor for all mental subtraction and block size calculation.</div>
            </div>
        </section>

        <section class="card p-8 rounded-2xl shadow-xl mb-12">
            <h2 class="text-2xl font-bold text-white mb-2">The Trade-Off: Subnets vs. Hosts (/17 to /30)</h2>
            <p class="text-slate-400 mb-8 text-sm">
                This visualization demonstrates the inverse relationship between network count and host capacity across two octets. Note: This chart uses a <strong>Logarithmic Scale</strong> to accurately represent values ranging from 2 to over 32,000 on the same axis.
            </p>
            <div class="chart-container">
                <canvas id="tradeOffChart"></canvas>
            </div>
            <div class="mt-6 text-center text-slate-500 text-xs italic">
                *Subnet count is calculated based on a Class B (/16) baseline for /17-/23 and a Class C (/24) baseline for /25-/30.
            </div>
        </section>

        <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 mb-12">
            
            <section class="card p-8 rounded-2xl shadow-xl border border-emerald-500/30">
                <h2 class="text-2xl font-bold text-emerald-400 mb-4">Fast Trick #1: The "Magic Number" Method</h2>
                <p class="text-slate-400 mb-8 text-sm">
                    This is the fastest mental math approach. If you are given <span class="text-white font-mono bg-slate-800 px-2 py-0.5 rounded">172.16.50.100/27</span>, solve it without writing a single bit:
                </p>

                <div class="space-y-6">
                    <div class="flex items-start">
                        <div class="bg-blue-500 text-white font-bold rounded-full min-w-[2rem] h-8 flex items-center justify-center mr-4">1</div>
                        <div>
                            <h4 class="text-blue-400 font-bold">Convert CIDR to Mask</h4>
                            <p class="text-slate-300 text-sm">A /27 is 3 bits into the octet. <span class="text-white font-mono">128+64+32 = 224</span>.</p>
                        </div>
                    </div>
                    <div class="flex items-start">
                        <div class="bg-amber-500 text-white font-bold rounded-full min-w-[2rem] h-8 flex items-center justify-center mr-4">2</div>
                        <div>
                            <h4 class="text-amber-400 font-bold">Find the Magic Number</h4>
                            <p class="text-slate-300 text-sm">Subtract from 256. <span class="text-white font-mono">256 - 224 = 32</span>. This is your block size.</p>
                        </div>
                    </div>
                    <div class="flex items-start">
                        <div class="bg-emerald-500 text-white font-bold rounded-full min-w-[2rem] h-8 flex items-center justify-center mr-4">3</div>
                        <div>
                            <h4 class="text-emerald-400 font-bold">Identify the Range</h4>
                            <p class="text-slate-300 text-sm">Find the multiple of 32 closest to 100 without going over. <span class="text-white font-mono">0, 32, 64, 96</span>. The network is <strong>.96</strong>.</p>
                        </div>
                    </div>
                </div>
            </section>

            <section class="card p-8 rounded-2xl shadow-xl">
                <h2 class="text-2xl font-bold text-blue-400 mb-4">Fast Trick #2: The /24 Anchor</h2>
                <p class="text-slate-400 mb-6 text-sm">
                    Memorize these common values. In the exam, most questions occur in the 4th octet. Being able to recall these instantly saves minutes.
                </p>
                <div class="overflow-hidden rounded-lg border border-slate-700">
                    <table class="w-full text-left text-xs font-mono">
                        <thead>
                            <tr class="bg-slate-800 text-slate-300">
                                <th class="p-3 border-b border-slate-700">CIDR</th>
                                <th class="p-3 border-b border-slate-700">Mask</th>
                                <th class="p-3 border-b border-slate-700">Hosts</th>
                            </tr>
                        </thead>
                        <tbody class="text-slate-400">
                            <tr class="border-b border-slate-700 hover:bg-slate-800/40">
                                <td class="p-3 font-bold text-blue-400">/25</td>
                                <td class="p-3">.128</td>
                                <td class="p-3 text-emerald-400">126</td>
                            </tr>
                            <tr class="border-b border-slate-700 hover:bg-slate-800/40">
                                <td class="p-3 font-bold text-blue-400">/26</td>
                                <td class="p-3">.192</td>
                                <td class="p-3 text-emerald-400">62</td>
                            </tr>
                            <tr class="border-b border-slate-700 hover:bg-slate-800/40">
                                <td class="p-3 font-bold text-blue-400">/27</td>
                                <td class="p-3">.224</td>
                                <td class="p-3 text-emerald-400">30</td>
                            </tr>
                            <tr class="border-b border-slate-700 hover:bg-slate-800/40">
                                <td class="p-3 font-bold text-blue-400">/28</td>
                                <td class="p-3">.240</td>
                                <td class="p-3 text-emerald-400">14</td>
                            </tr>
                            <tr class="border-b border-slate-700 hover:bg-slate-800/40">
                                <td class="p-3 font-bold text-blue-400">/29</td>
                                <td class="p-3">.248</td>
                                <td class="p-3 text-emerald-400">6</td>
                            </tr>
                            <tr class="hover:bg-slate-800/40">
                                <td class="p-3 font-bold text-blue-400">/30</td>
                                <td class="p-3">.252</td>
                                <td class="p-3 text-emerald-400">2</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </section>

        </div>

        <footer class="mt-12">
            <div class="card p-6 rounded-2xl shadow-xl border border-blue-500/30 text-center">
                <h3 class="text-xl font-bold text-white mb-2">Study Sessions & Networking</h3>
                <p class="text-slate-400 mb-6 text-sm">Found this useful? Let's connect and keep the CCNA momentum going.</p>
                <a href="https://www.linkedin.com/in/renatokitamura/" class="inline-flex items-center px-6 py-3 bg-blue-600 hover:bg-blue-500 text-white font-bold rounded-lg transition-colors duration-200">
                    <span class="mr-2">Connect on LinkedIn</span>
                    <span class="text-xl font-light">→</span>
                </a>
                <p class="text-slate-500 text-xs mt-6 font-medium tracking-wide">
                    Made by Renato Kitamura Morao using Gemini
                </p>
            </div>
        </footer>

    </div>

    <script>
        const wrapLabel = (label) => {
            if (label.length <= 16) return label;
            const words = label.split(' ');
            let lines = [];
            let currentLine = '';
            words.forEach(word => {
                if ((currentLine + word).length > 16) {
                    if (currentLine) lines.push(currentLine.trim());
                    currentLine = word + ' ';
                } else {
                    currentLine += word + ' ';
                }
            });
            if (currentLine) lines.push(currentLine.trim());
            return lines;
        };

        const commonTooltipConfig = {
            callbacks: {
                title: function(tooltipItems) {
                    const item = tooltipItems[0];
                    let label = item.chart.data.labels[item.dataIndex];
                    if (Array.isArray(label)) {
                        return label.join(' ');
                    } else {
                        return label;
                    }
                }
            }
        };

        const tradeCtx = document.getElementById('tradeOffChart').getContext('2d');
        const labels = ['/17', '/18', '/19', '/20', '/21', '/22', '/23', '/24', '/25', '/26', '/27', '/28', '/29', '/30'];
        
        const subnets = [2, 4, 8, 16, 32, 64, 128, 1, 2, 4, 8, 16, 32, 64];
        const hosts = [32766, 16382, 8190, 4094, 2046, 1022, 510, 254, 126, 62, 30, 14, 6, 2];

        new Chart(tradeCtx, {
            type: 'bar',
            data: {
                labels: labels,
                datasets: [
                    {
                        label: 'Created Subnets',
                        data: subnets,
                        backgroundColor: '#3b82f6',
                        borderRadius: 4,
                        borderWidth: 1,
                        borderColor: '#1d4ed8'
                    },
                    {
                        label: 'Usable Hosts Per Subnet',
                        data: hosts,
                        backgroundColor: '#10b981',
                        borderRadius: 4,
                        borderWidth: 1,
                        borderColor: '#047857'
                    }
                ]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                color: '#f8fafc',
                scales: {
                    x: {
                        grid: { display: false },
                        ticks: { color: '#94a3b8', font: { family: 'monospace', size: 11 } }
                    },
                    y: {
                        type: 'logarithmic',
                        min: 1,
                        grid: { color: '#1e293b' },
                        ticks: { 
                            color: '#64748b',
                            callback: function(value) {
                                if (value === 1 || value === 10 || value === 100 || value === 1000 || value === 10000 || value === 100000) {
                                    return value;
                                }
                                return null;
                            }
                        }
                    }
                },
                plugins: {
                    tooltip: commonTooltipConfig,
                    legend: {
                        position: 'top',
                        labels: { 
                            color: '#cbd5e1',
                            font: { size: 12 },
                            padding: 20
                        }
                    }
                }
            }
        });
    </script>
</body>
</html>
