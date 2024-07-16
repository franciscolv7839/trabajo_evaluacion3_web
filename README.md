# trabajo_evaluacion3_web

aca dejo registrado el archivo main.py:

/////main.py////


from flask import Flask, render_template, request

app = Flask(__name__)

@app.route('/')
def inicio():
    return render_template('index.html')


@app.route('/formulario de notas', methods=['GET', 'POST'])
def formulariodenotas():
    if request.method == 'POST':
        Nota1 = float(request.form['Nota 1'])
        Nota2 = float(request.form['Nota 2'])
        Nota3 = float(request.form['Nota 3'])
        resultado1 = Nota1 + Nota2 + Nota3
        resultado2 = Nota1 + Nota2
        resultado3 = Nota1 * Nota2
        resultado4 = round(Nota1 / Nota2, 1)
        return render_template('formulariodenotas.html', Nota1=Nota1,Nota2=Nota2,Nota3=Nota3)

    return render_template('formulariodenotas.html')


@app.route('/formulario de notas2', methods=['GET', 'POST'])
def formulariodenotas2():
    if request.method == 'POST':
        Nombre1=  float(request.form['Nota 1'])
        Nombre2 = float(request.form['Nota 2'])
        Nombre3 = float(request.form['Nota 3'])
        resultado1 = Nombre1 + Nombre1
        resultado2 = Nombre2 + Nombre2
        resultado3 = Nombre3 + Nombre3
        resultado4 = round(Nombre1 / Nombre2,1)
        return render_template('formulariodenotas2.html', Nombre1=Nombre1,Nombre2=Nombre2,Nombre3=Nombre3)

    return render_template('formulariodenotas2.html')


if __name__ == '__main__':
    app.run(debug=True)


    ///DESDE LA CARPETA "TEMPLATES" CREE LOS DOS ARCHIVOS HTML. EL PRIMERO SE LLAMA "FORMULARIODENOTAS"


    <!DOCTYPE html>
<html>
<head>
    <title>Ejercicio 1</title>
    <link rel="stylesheet" type="text/css" href="/static/css/estilosSuma.css">
</head>
<body>
<div class="container">
    <h1>Formulario de Notas</h1>
    <form action="/formulariodenotas" method="POST">
        <label for="Nota1">Nota 1:</label>
        <input type="number" id="Nota1" name="Nota 1" required>
        <br>
        <label for="Nota2">Nota 2:</label>
        <input type="number" id="Nota2" name="Nota 2" required>
        <br>
        <label for="Nota3">Nota 3:</label>
        <input type="number" id="Nota3" name="Nota 3" required>
        <br>
        <label for="Asistencia (%)">Asistencia (%):</label>
        <input type="number" id="Asistencia (%)" name="Asistencia (%)" required>
        <button type="submit">Enviar</button>
    </form>
    {% if Nota1 and Nota2 and Nota3 and Nota4 %}
    <div> class="resultado">
        <p>Resultado: {{ resultado }}</p>
        <h3>El resultado para los numeros {{Nota1}} y {{Nota2}}</h3>
        <p>La suma es: {{ resultado1 }}</p>
        <p>La suma es: {{ resultado2 }}</p>
        <p>La suma es: {{ resultado3 }}</p>
        <p>La suma es: {{ resultado4 }}</p>
    </div>
    {% endif %}
</div>
</body>
</html>

///ACA DEJO EL SEGUNDO ARCHIVO HTML. "FORMULARIODENOTAS2".

<!DOCTYPE html>
<html>
<head>
    <title>Ejercicio 1</title>
    <link rel="stylesheet" type="text/css" href="/static/css/estilosSuma.css">
</head>
<body>
<div class="container">
    <form action="/" method="POST">
        <label for="Nombre1">Nombre 1:</label>
        <input type="text" id="Nombre1" name="Nombre 1" required>
        <br>
        <label for="Nombre2">Nombre 2:</label>
        <input type="text" id="Nombre2" name="Nombre 2" required>
        <br>
        <label for="Nombre3">Nombre 3:</label>
        <input type="text" id="Nombre3" name="Nombre 3" required>
        <button type="submit">Enviar</button>
   </form>
    {% if resultado1 and resultado2 and resultado3 and resultado4 %}
    <div> class="resultado">
        <p>Resultado: {{ resultado }}</p>
        <h3>El resultado para los numeros {{Nota1}} y {{Nota2}}</h3>
        <p>La suma es: {{ resultado1 }}</p>
        <p>La suma es: {{ resultado2 }}</p>
        <p>La suma es: {{ resultado3 }}</p>
        <p>La suma es: {{ resultado4 }}</p>
    </div>
    {% endif %}
</div>
</body>
</html>

////DESDE LA CARPETA "STATIC" CREE LA SUBCARPETA "CSS" DONDE VA EL DISEÑO DE LA PAGINA WEB.
EL PRIMERO LLAMADO "ESTILO SUMA".

body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f4f4f4;
}

.container {
    max-width: 350px;
    margin: left;
    padding: 50px;
    background-color: #fff;
    border-radius: 10px;
    box-shadow: 0px 5px 15px rgba(0, 0, 0, 0.1);
}

h1 {
    text-align: left;
    margin-bottom: 20px;
    color: #333;
}

form {
    text-align: left;
}

label {
    display: block;
    margin-bottom: 20px;
    color: #333;
}

input {
    width: 100%;
    padding: 10px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 1px;
}

////EL ARCHIVO N2 LLAMADO "ESTILO INDEX".DE LA PAGINA PRINCIPAL./////

body {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
    background-color: #f0f0f0;
  }

  .button-container {
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    gap: 10px;
  }


  .button {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 200px;
    height: 100px;
    font-size: 30px;
    background-color: #007BFF;
    color: white;
    border-radius: 10px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  .button:hover {
    background-color: #0056b3;
  }

  ////EL TERCER ARCHIVO CSS LLAMADO "ESTILO NOMBRE Y EDAD"./////

  body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f4f4f4;
}

.container {
    max-width: 300px;
    margin: left;
    padding: 80px;
    background-color: #fff;
    border-radius: 10px;
    box-shadow: 0px 5px 15px rgba(0, 0, 0, 0.1);
}


h1, h2 {
    text-align: center;
    margin-bottom: 20px;
    color: #333;
}

form {
    text-align: center;
}

label {
    display: block;
    margin-bottom: 5px;
    color: #555;
}

input {
    width: 100%;
    padding: 10px;
    margin-bottom: 15px;
    border: 1px solid #ccc;
    border-radius: 3px;
}

button {
    padding: 10px 20px;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 3px;
    cursor: pointer;
    transition: background-color 0.3s;
}

button:hover {
    background-color: #0056b3;
}
