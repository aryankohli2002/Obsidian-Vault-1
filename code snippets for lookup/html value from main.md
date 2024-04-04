The following code is saved as **hello.html** in the templates folder.

<!doctype html>
<!---<html>
   <body>
   
      <h1>Hello {{ name }}!</h1>
      
   </body>
</html>
--->
Next, run the following script from Python shell.

from flask import Flask, render_template
app = Flask(__name__)

@app.route('/hello/<user>')
def hello_name(user):
   return render_template('hello.html', name = user)

if __name__ == '__main__':
   app.run(debug = True)