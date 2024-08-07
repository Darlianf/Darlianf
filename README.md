/auth-app
|-- login.html
|-- register.html
|-- profile.html
|-- styles.css
|-- app.js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="auth-container">
        <div class="auth-card">
            <h2>Login</h2>
            <form id="login-form">
                <label for="login-email">Email:</label>
                <input type="email" id="login-email" name="email" required>
                
                <label for="login-password">Senha:</label>
                <input type="password" id="login-password" name="password" required>
                
                <button type="submit">Login</button>
            </form>
            <p>Não tem uma conta? <a href="register.html">Cadastre-se aqui</a></p>
        </div>
    </div>
    <script src="app.js"></script>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cadastro</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="auth-container">
        <div class="auth-card">
            <h2>Cadastro</h2>
            <form id="register-form">
                <label for="register-name">Nome:</label>
                <input type="text" id="register-name" name="name" required>

                <label for="register-email">Email:</label>
                <input type="email" id="register-email" name="email" required>
                
                <label for="register-password">Senha:</label>
                <input type="password" id="register-password" name="password" required>
                
                <button type="submit">Cadastrar</button>
            </form>
            <p>Já tem uma conta? <a href="login.html">Faça login aqui</a></p>
        </div>
    </div>
    <script src="app.js"></script>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Perfil</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <nav>
            <a href="profile.html" class="logo">App</a>
            <button id="logout-button">Sair</button>
        </nav>
    </header>
    <main>
        <div class="profile-container">
            <div class="profile-card">
                <h2>Seu Perfil</h2>
                <form id="profile-form">
                    <label for="first-name">Nome:</label>
                    <input type="text" id="first-name" name="first-name" required>
                    
                    <label for="last-name">Sobrenome:</label>
                    <input type="text" id="last-name" name="last-name" required>
                    
                    <label for="experience">Experiência:</label>
                    <textarea id="experience" name="experience" required></textarea>
                    
                    <label for="truck-license">Placa da Carreta:</label>
                    <input type="text" id="truck-license" name="truck-license" required>
                    
                    <label for="license">Habilitação:</label>
                    <input type="text" id="license" name="license" required>
                    
                    <button type="submit">Salvar</button>
                </form>
            </div>
        </div>
    </main>
    <script src="app.js"></script>
</body>
</html>
/* General styles */
body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f4f6f9;
}

/* Header styles */
header {
    background-color: #ffffff;
    border-bottom: 1px solid #e0e0e0;
    padding: 10px 20px;
}

nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.logo {
    font-size: 1.5rem;
    font-weight: bold;
    color: #333;
    text-decoration: none;
}

nav button {
    padding: 0.5rem 1rem;
    background-color: #e0245e;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 1rem;
}

nav button:hover {
    background-color: #c8103d;
}

/* Main content styles */
main {
    display: flex;
    justify-content: center;
    align-items: center;
    height: calc(100vh - 60px);
}

.auth-container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
}

.auth-card, .profile-card {
    background-color: white;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    padding: 2rem;
    width: 100%;
    max-width: 400px;
    text-align: center;
}

h2 {
    margin-bottom: 1.5rem;
    font-size: 1.75rem;
    color: #333;
}

form {
    display: flex;
    flex-direction: column;
}

label {
    margin: 0.5rem 0 0.2rem;
    text-align: left;
    font-weight: bold;
    color: #555;
}

input, textarea {
    padding: 0.8rem;
    margin-bottom: 1rem;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-size: 1rem;
}

textarea {
    resize: vertical;
    height: 120px;
}

button {
    padding: 0.8rem;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 1rem;
}

button:hover {
    background-color: #0056b3;
}

p {
    margin-top: 1rem;
}

a {
    color: #007bff;
    text-decoration: none;
}

a:hover {
    text-decoration: underline;
}
document.addEventListener('DOMContentLoaded', () => {
    const loginForm = document.getElementById('login-form');
    const registerForm = document.getElementById('register-form');
    const profileForm = document.getElementById('profile-form');
    const logoutButton = document.getElementById('logout-button');

    // Check if user is logged in
    if (profileForm) {
        if (!localStorage.getItem('loggedIn')) {
            window.location.href = 'login.html'; // Redirect to login if not logged in
        } else {
            // Populate profile form with existing data
            document.getElementById('first-name').value = localStorage.getItem('firstName') || '';
            document.getElementById('last-name').value = localStorage.getItem('lastName') || '';
            document.getElementById('experience').value = localStorage.getItem('experience') || '';
            document.getElementById('truck-license').value = localStorage.getItem('truckLicense') || '';
            document.getElementById('license').value = localStorage.getItem('license') || '';
        }
    }

    if (loginForm) {
        loginForm.addEventListener('submit', (event) => {
            event.preventDefault();
            const email = document.getElementById('login-email').value;
            const password = document.getElementById('login-password').value;

            // Simulate authentication
            const storedEmail = localStorage.getItem('email');
            const storedPassword = localStorage.getItem('password');

            if (email === storedEmail && password === storedPassword) {
                localStorage.setItem('loggedIn', true);
                window.location.href = 'profile.html'; // Redirect to profile page
            } else {
                alert('Email ou senha incorretos');
            }
        });
    }

    if (registerForm) {
        registerForm.addEventListener('submit', (event) => {
            event.preventDefault();
            const name = document.getElementById('register-name').value;
            const email = document.getElementById('register-email').value;
            const password = document.getElementById('register-password').value;

            // Simulate registration
            localStorage.setItem('name', name);
            localStorage.setItem('email', email);
            localStorage.setItem('password', password);

            alert('Cadastro realizado com sucesso!');
            window.location.href = 'login.html'; // Redirect to login page
        });
    }

    if (profileForm) {
        profileForm.addEventListener('submit', (event) => {
            event.preventDefault();
            // Save profile information
            localStorage.setItem('firstName', document.getElementById('first-name').value);
            localStorage.setItem('lastName', document.getElementById('last-name').value);
            localStorage.setItem('experience', document.getElementById('experience').value);
            localStorage.setItem('truckLicense', document.getElementById('truck-license').value);
            localStorage.setItem('license', document.getElementById('license').value);

            alert('Informações salvas com sucesso!');
        });
    }

    if (logoutButton) {
        logoutButton.addEventListener('click', () => {
            localStorage.removeItem('loggedIn');
            window.location.href = 'login.html'; // Redirect to login page
        });
    }
});
