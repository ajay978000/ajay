# 🎬 **COMPLETE MOVIEHUB - ALL CATEGORIES + LOGO + UPLOAD!**

## **🚀 ONE-FILE SOLUTION (Copy → LIVE!)**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MovieHub - All Categories + Upload</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        body { 
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #0a0a1e 0%, #1a1a3a 50%, #0f0f23 100%);
        }
        .glass { 
            backdrop-filter: blur(25px);
            background: rgba(255,255,255,0.08);
            border: 1px solid rgba(255,255,255,0.1);
        }
        .logo-gradient {
            background: linear-gradient(45deg, #00d4ff, #ff6b9d, #ffd93d);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
    </style>
</head>
<body class="text-white min-h-screen">
    
    <!-- Logo Favicon -->
    <link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>🎬</text></svg>">

    <!-- Header -->
    <nav class="fixed top-0 w-full glass z-50 p-4 shadow-2xl">
        <div class="max-w-7xl mx-auto flex justify-between items-center">
            <!-- LOGO -->
            <div class="flex items-center gap-3 p-3 rounded-2xl glass">
                <i class="fas fa-film text-3xl text-yellow-400"></i>
                <div>
                    <h1 class="text-2xl font-bold logo-gradient">MovieHub</h1>
                    <p class="text-xs opacity-75">Live + Custom Movies</p>
                </div>
            </div>

            <!-- Categories -->
            <div class="hidden md:flex gap-2 bg-black/20 px-4 py-2 rounded-full">
                <button onclick="loadCategory('now_playing')" class="cat-btn active">🎬 Now</button>
                <button onclick="loadCategory('upcoming')" class="cat-btn">📅 Upcoming</button>
                <button onclick="loadCategory('top_rated')" class="cat-btn">⭐ Top</button>
                <button onclick="loadCategory('popular')" class="cat-btn">🔥 Popular</button>
                <button onclick="loadCategory('action')" class="cat-btn">⚔️ Action</button>
                <button onclick="loadCategory('comedy')" class="cat-btn">😂 Comedy</button>
                <button onclick="loadCategory('drama')" class="cat-btn">🎭 Drama</button>
                <button onclick="loadCategory('horror')" class="cat-btn">👻 Horror</button>
                <button onclick="loadCategory('custom')" class="cat-btn">✨ Custom</button>
            </div>

            <!-- Search + Upload -->
            <div class="flex items-center gap-4">
                <div class="relative">
                    <i class="fas fa-search absolute left-4 top-1/2 -translate-y-1/2 text-gray-400"></i>
                    <input id="searchInput" type="text" placeholder="Search 10,000+ movies..." 
                           class="pl-12 pr-4 py-3 bg-white/10 rounded-full border-2 border-white/20 w-72 focus:border-cyan-400 focus:outline-none transition-all">
                </div>
                <button onclick="toggleUpload()" class="p-3 bg-gradient-to-r from-purple-500 to-pink-500 rounded-full hover:scale-110 transition-all">
                    <i class="fas fa-plus"></i>
                </button>
            </div>
        </div>
    </nav>

    <!-- Hero -->
    <section class="h-screen flex flex-col items-center justify-center text-center pt-24 px-8">
        <div class="glass p-12 rounded-3xl max-w-4xl mx-auto">
            <h1 class="text-7xl font-bold mb-6 logo-gradient">MovieHub</h1>
            <p class="text-2xl mb-8 opacity-90">All movie categories + upload your own movies</p>
            <div class="grid grid-cols-2 md:grid-cols-4 gap-8 mb-12">
                <div class="glass p-6 rounded-2xl"><i class="fas fa-infinity text-3xl text-cyan-400 mb-2 block"></i>Unlimited Categories</div>
                <div class="glass p-6 rounded-2xl"><i class="fas fa-upload text-3xl text-green-400 mb-2 block"></i>Upload Movies</div>
                <div class="glass p-6 rounded-2xl"><i class="fas fa-search text-3xl text-yellow-400 mb-2 block"></i>Live Search</div>
                <div class="glass p-6 rounded-2xl"><i class="fas fa-mobile-alt text-3xl text-pink-400 mb-2 block"></i>Mobile Ready</div>
            </div>
        </div>
    </section>

    <!-- Content -->
    <main class="max-w-7xl mx-auto p-8 pb-20">
        <!-- Movies Grid -->
        <div id="moviesGrid" class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 2xl:grid-cols-6 gap-6"></div>
        
        <!-- No Results -->
        <div id="noResults" class="text-center py-20 hidden">
            <i class="fas fa-search text-6xl text-gray-500 mb-6"></i>
            <h3 class="text-3xl font-bold mb-4">No movies found</h3>
            <p>Try different keywords or category</p>
        </div>
    </main>

    <!-- Upload Modal -->
    <div id="uploadModal" class="fixed inset-0 bg-black/80 z-50 flex items-center justify-center p-4 hidden">
        <div class="glass rounded-3xl max-w-md w-full p-8">
            <h3 class="text-2xl font-bold mb-6 flex items-center gap-3">
                <i class="fas fa-upload text-green-400"></i> Upload Movie
            </h3>
            <form id="uploadForm">
                <input type="text" id="movieTitle" placeholder="Movie Title" class="w-full p-4 bg-white/10 rounded-xl border-2 border-white/20 mb-4 focus:outline-none focus:border-green-400" required>
                <input type="text" id="movieYear" placeholder="Year (2024)" class="w-full p-4 bg-white/10 rounded-xl border-2 border-white/20 mb-4 focus:outline-none focus:border-green-400" required>
                <input type="number" id="movieRating" placeholder="Rating (8.5)" step="0.1" min="0" max="10" class="w-full p-4 bg-white/10 rounded-xl border-2 border-white/20 mb-6 focus:outline-none focus:border-green-400">
                <textarea id="movieDesc" placeholder="Description" class="w-full p-4 bg-white/10 rounded-xl border-2 border-white/20 h-24 resize-none focus:outline-none focus:border-green-400 mb-6"></textarea>
                <div class="flex gap-3">
                    <button type="submit" class="flex-1 bg-gradient-to-r from-green-500 to-emerald-500 p-4 rounded-xl font-bold hover:scale-105 transition-all">
                        <i class="fas fa-check mr-2"></i> Add Movie
                    </button>
                    <button type="button" onclick="toggleUpload()" class="flex-1 bg-white/20 p-4 rounded-xl hover:bg-white/30 transition-all">
                        Cancel
                    </button>
                </div>
            </form>
        </div>
    </div>

    <!-- Loading -->
    <div id="loading" class="fixed inset-0 bg-black/90 flex flex-col items-center justify-center z-40 hidden">
        <i class="fas fa-spinner fa-spin text-6xl text-cyan-400 mb-6"></i>
        <p class="text-2xl">Loading movies...</p>
    </div>

    <!-- Movie Modal -->
    <div id="movieModal" class="fixed inset-0 bg-black/90 z-[100] flex items-center justify-center p-4 hidden">
        <div class="glass rounded-3xl max-w-4xl w-full max-h-[90vh] overflow-y-auto p-8">
            <i id="closeMovie" class="fas fa-times text-3xl float-right cursor-pointer hover:text-red-400 mb-8"></i>
            <div id="movieDetails"></div>
        </div>
    </div>

    <script>
        // 🔥 TMDB Proxy API (No Key Needed)
        const API_BASE = 'https://api-proxy.tmdb.dev/3';
        
        // Custom Movies Storage
        let customMovies = JSON.parse(localStorage.getItem('customMovies')) || [];
        
        // Categories
        const categories = {
            now_playing: '/movie/now_playing?language=en-US&page=1',
            upcoming: '/movie/upcoming?language=en-US&page=1',
            top_rated: '/movie/top_rated?language=en-US&page=1',
            popular: '/movie/popular?language=en-US&page=1',
            action: '/discover/movie?with_genres=28&language=en-US&page=1',
            comedy: '/discover/movie?with_genres=35&language=en-US&page=1',
            drama: '/discover/movie?with_genres=18&language=en-US&page=1',
            horror: '/discover/movie?with_genres=27&language=en-US&page=1'
        };

        // Load movies by category
        async function loadCategory(cat) {
            document.getElementById('loading').classList.remove('hidden');
            document.getElementById('moviesGrid').innerHTML = '';
            
            // Update active button
            document.querySelectorAll('.cat-btn').forEach(btn => btn.classList.remove('active'));
            event?.target?.classList.add('active');
            
            if (cat === 'custom') {
                renderMovies(customMovies);
                document.getElementById('loading').classList.add('hidden');
                return;
            }
            
            try {
                const movies = await fetchMovies(categories[cat]);
                renderMovies(movies);
            } catch (e) {
                console.error(e);
            }
            
            document.getElementById('loading').classList.add('hidden');
        }

        // Fetch from TMDB
        async function fetchMovies(endpoint) {
            const res = await fetch(`${API_BASE}${endpoint}`);
            const data = await res.json();
            return data.results || [];
        }

        // Render movies
        function renderMovies(movies) {
            const grid = document.getElementById('moviesGrid');
            const noResults = document.getElementById('noResults');
            
            if (movies.length === 0) {
                grid.classList.add('hidden');
                noResults.classList.remove('hidden');
                return;
            }
            
            grid.classList.remove('hidden');
            noResults.classList.add('hidden');
            
            grid.innerHTML = movies.map(movie => `
                <div class="group cursor-pointer glass rounded-3xl p-6 hover:bg-white/20 transition-all duration-500 hover:-translate-y-4 hover:scale-[1.03] hover:shadow-2xl border border-white/20 overflow-hidden"
                     onclick="showMovieDetails('${movie.isCustom ? 'custom' : movie.id}')">
                    <div class="relative overflow-hidden rounded-2xl mb-6 h-64">
                        <img src="${movie.poster_path ? 'https://image.tmdb.org/t/p/w500' + movie.poster_path : movie.posterUrl || 'https://via.placeholder.com/300x450/333/666?text=Custom'}" 
                             alt="${movie.title}" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-700">
                        <div class="absolute inset-0 bg-gradient-to-t from-black/90 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-all duration-500 flex items-center justify-center">
                            <i class="fas fa-play text-4xl text-white drop-shadow-2xl"></i>
                        </div>
                    </div>
                    <div>
                        <h3 class="font-bold text-xl mb-3 line-clamp-2 leading-tight">${movie.title}</h3>
                        <div class="flex justify-between items-center text-lg mb-2">
                            <span class="opacity-75">${movie.release_date?.split('-')[0] || movie.year || 'TBA'}</span>
                            <span class="bg-gradient-to-r from-yellow-400 to-orange-500 px-4 py-2 rounded-full font-bold text-sm shadow-lg">
                                ⭐ ${movie.vote_average?.toFixed(1) || movie.rating || 'N/A'}
                            </span>
                        </div>
                        ${movie.overview ? `<p class="text-sm opacity-75 line-clamp-2">${movie.overview}</p>` : ''}
                        ${movie.isCustom ? '<span class="text-xs bg-purple-500/30 px-3 py-1 rounded-full">✨ Custom Upload</span>' : ''}
                    </div>
                </div>
            `).join('');
        }

        // Movie details
        async function showMovieDetails(id) {
            if (id === 'custom') return; // Custom movies don't have details
            
            document.getElementById('loading').classList.remove('hidden');
            try {
                const res = await fetch(`${API_BASE}/movie/${id}?language=en-US`);
                const movie = await res.json();
                renderMovieModal(movie);
            } catch (e) {
                console.error(e);
            }
            document.getElementById('loading').classList.add('hidden');
            document.getElementById('movieModal').classList.remove('hidden');
        }

        function renderMovieModal(movie) {
            document.getElementById('movieDetails').innerHTML = `
                <div class="grid lg:grid-cols-2 gap-12 items-start">
                    <img src="https://image.tmdb.org/t/p/w500${movie.poster_path}" alt="${movie.title}" 
                         class="w-full rounded-3xl shadow-2xl">
                    <div>
                        <h2 class="text-5xl font-bold mb-6">${movie.title}</h2>
                        <div class="flex flex-wrap gap-4 mb-8 text-xl">
                            <span class="bg-white/10 px-6 py-3 rounded-2xl">⭐ ${movie.vote_average?.toFixed(1)}</span>
                            <span class="bg-white/10 px-6 py-3 rounded-2xl">${movie.release_date}</span>
                            <span class="bg-white/10 px-6 py-3 rounded-2xl">${movie.runtime} min</span>
                        </div>
                        <p class="text-lg leading-relaxed mb-8 opacity-90">${movie.overview}</p>
                        <div class="flex gap-4">
                            <a href="https://www.themoviedb.org/movie/${movie.id}" target="_blank" 
                               class="bg-gradient-to-r from-cyan-500 to-blue-500 px-8 py-4 rounded-2xl font-bold text-lg hover:scale-105 transition-all shadow-xl">
                                <i class="fas fa-external-link-alt mr-2"></i>TMDB
                            </a>
                            <button onclick="shareMovie('${movie.title}')" 
                                    class="bg-gradient-to-r from-green-500 to-emerald-500 px-8 py-4 rounded-2xl font-bold text-lg hover:scale-105 transition-all shadow-xl">
                                <i class="fas fa-share mr-2"></i>Share
                            </button>
                        </div>
                    </div>
                </div>
            `;
        }

        // Upload movie
        document.getElementById('uploadForm').onsubmit = (e) => {
            e.preventDefault();
            const movie = {
                title: document.getElementById('movieTitle').value,
                year: document.getElementById('movieYear').value,
                rating: parseFloat(document.getElementById('movieRating').value),
                overview: document.getElementById('movieDesc').value,
                posterUrl: 'https://via.placeholder.com/300x450/4a5568/ffffff?text=' + encodeURIComponent(document.getElementById('movieTitle').value.slice(0,8)),
                isCustom: true
            };
            
            customMovies.unshift(movie);
            localStorage.setItem('customMovies', JSON.stringify(customMovies));
            
            // Show in custom category
            if (document.querySelector('.cat-btn.active')?.textContent.includes('Custom')) {
                renderMovies(customMovies);
            }
            
            toggleUpload();
            alert('🎉 Movie uploaded successfully!');
        };

        // Toggle upload
        function toggleUpload() {
            document.getElementById('uploadModal').classList.toggle('hidden');
        }

        // Search
        document.getElementById('searchInput').addEventListener('input', async (e) => {
            if (e.target.value.length < 3) return;
            
            document.getElementById('loading').classList.remove('hidden');
            try {
                const movies = await fetchMovies(`/search/movie?query=${e.target.value}&language=en-US&page=1`);
                renderMovies(movies);
            } catch (e) {
                console.error(e);
            }
            document.getElementById('loading').classList.add('hidden');
        });

        // Modals
        document.getElementById('closeMovie').onclick = () => document.getElementById('movieModal').classList.add('hidden');
        document.getElementById('uploadModal').onclick = (e) => { if(e.target.id==='uploadModal') toggleUpload(); };

        // Share
        function shareMovie(title) {
            if (navigator.share) {
                navigator.share({title: `Check out ${title} on MovieHub!`});
            } else {
                navigator.clipboard.writeText(window.location.href);
                alert('Link copied!');
            }
        }

        // CSS for buttons
        const style = document.create
