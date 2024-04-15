from flask_wtf.csrf import CSRFProtect
app = Flask(__name__)
app.config['SECRET_KEY'] = 'your_secret_key_here'
csrf = CSRFProtect(app)


<h2>Login</h2>

    <form id="loginForm" action="#" method="POST">

      {{ form.hidden_tag() }} {# Include CSRF token #}