# TFI-BANISA
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Movies App</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f3f3f3;
        }
        header {
            background-color: #1c1c1c;
            color: white;
            padding: 1rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        header h1 {
            margin: 0;
        }
        .search-bar {
            padding: 0.5rem;
            border-radius: 5px;
            border: none;
            width: 50%;
        }
        .main-content {
            padding: 2rem;
        }
        .movies-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 1rem;
        }
        .movie-card {
            background-color: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            transition: transform 0.2s;
        }
        .movie-card:hover {
            transform: scale(1.05);
        }
        .movie-card img {
            width: 100%;
            height: 300px;
            object-fit: cover;
        }
        .movie-card .info {
            padding: 1rem;
        }
        .movie-card .info h3 {
            margin: 0;
            font-size: 1.2rem;
        }
        .movie-card .info p {
            margin: 0.5rem 0;
            font-size: 0.9rem;
            color: #666;
        }
        .movie-details {
            display: flex;
            gap: 2rem;
            margin-top: 2rem;
            background-color: white;
            padding: 2rem;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        .movie-details img {
            width: 300px;
            border-radius: 10px;
        }
        .movie-details .details {
            flex: 1;
        }
        .movie-details .details h1 {
            margin-top: 0;
        }
        .admin-dashboard {
            margin-top: 2rem;
            background-color: white;
            padding: 2rem;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        .admin-dashboard table {
            width: 100%;
            border-collapse: collapse;
        }
        .admin-dashboard table th, .admin-dashboard table td {
            padding: 1rem;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }
        .admin-dashboard table th {
            background-color: #f4f4f4;
        }
        .edit-form, .upload-form {
            margin-top: 2rem;
            background-color: white;
            padding: 2rem;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        .edit-form label, .upload-form label {
            display: block;
            margin: 1rem 0 0.5rem;
        }
        .edit-form input, .edit-form textarea, .upload-form input, .upload-form textarea {
            width: 100%;
            padding: 0.5rem;
            border: 1px solid #ddd;
            border-radius: 5px;
            margin-bottom: 1rem;
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <h1>Movies App</h1>
        <input class="search-bar" type="text" placeholder="Search movies...">
    </header>

    <!-- Main Content -->
    <div class="main-content">
        <div class="movies-grid">
            <div class="movie-card">
                <img src="https://via.placeholder.com/200x300" alt="Movie Poster">
                <div class="info">
                    <h3>Movie Title</h3>
                    <p>Genre | Rating</p>
                </div>
            </div>
            <!-- Add more movie cards here -->
        </div>

        <!-- Movie Details Page -->
        <div class="movie-details">
            <video controls width="600" src="https://via.placeholder.com/600x400?text=Movie+Video" id="moviePlayer">
                Your browser does not support the video tag.
            </video>
            <div class="details">
                <h1>Movie Title</h1>
                <p><strong>Genre:</strong> Action, Adventure</p>
                <p><strong>Rating:</strong> 8.5/10</p>
                <p><strong>Synopsis:</strong> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin suscipit, nunc at cursus.</p>
            </div>
        </div>

        <!-- Admin Dashboard -->
        <div class="admin-dashboard">
            <h2>Admin Dashboard</h2>
            <table>
                <thead>
                    <tr>
                        <th>Title</th>
                        <th>Release Date</th>
                        <th>Status</th>
                        <th>Actions</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Movie Title</td>
                        <td>2024-01-01</td>
                        <td>Published</td>
                        <td>
                            <button onclick="showEditForm()">Edit</button>
                            <button>Delete</button>
                        </td>
                    </tr>
                    <!-- Add more rows here -->
                </tbody>
            </table>
        </div>

        <!-- Edit Form -->
        <div class="edit-form" id="editForm" style="display:none;">
            <h2>Edit Movie</h2>
            <label for="movieTitle">Movie Title</label>
            <input type="text" id="movieTitle" placeholder="Enter movie title">

            <label for="releaseDate">Release Date</label>
            <input type="date" id="releaseDate">

            <label for="profileImage">Profile Image</label>
            <input type="file" id="profileImage">

            <label for="movieVideo">Movie Video</label>
            <input type="file" id="movieVideo" accept=".mp4, .mkv, .avi, .mov, .flv">

            <label for="synopsis">Synopsis</label>
            <textarea id="synopsis" placeholder="Enter synopsis"></textarea>

            <button>Save Changes</button>
        </div>

        <!-- Upload Form -->
        <div class="upload-form">
            <h2>Upload New Movie</h2>
            <label for="newMovieTitle">Movie Title</label>
            <input type="text" id="newMovieTitle" placeholder="Enter movie title">

            <label for="newReleaseDate">Release Date</label>
            <input type="date" id="newReleaseDate">

            <label for="newProfileImage">Profile Image</label>
            <input type="file" id="newProfileImage">

            <label for="newMovieFile">Movie Video</label>
            <input type="file" id="newMovieFile" accept=".mp4, .mkv, .avi, .mov, .flv">

            <label for="newSynopsis">Synopsis</label>
            <textarea id="newSynopsis" placeholder="Enter synopsis"></textarea>

            <button>Add Movie</button>
        </div>
    </div>

    <script>
        function showEditForm() {
            document.getElementById('editForm').style.display = 'block';
        }
    </script>
</body>
</html>
