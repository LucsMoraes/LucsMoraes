<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Correndo sobre o tempo</title>

    <style>

        .container{
            background-image: url(Imagem\ do\ tigrão.png);
            background-position:100px 10px;
            background-attachment: fixed;
            background-size: cover;
        }
         button{
            background-color: rgb(165, 42, 42);
            color: rgb(255, 255, 0);
            font-size: 32px;
            padding: 20px 30px;
            cursor: pointer;
            border: 0px;
            font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
            background-position: center;
        }

        select{
            border-bottom: 0px; 
            background-color: rgb(240, 232, 165);
        }
        body{
            background: url(Imagem\ de\ fundo.png);
            background-size:cover;
            background-position:center;
            background-attachment: fixed;
        }
        h2{
            font-family: Arial, Helvetica, sans-serif;
            color: aliceblue;
            font-size: 30px;
        }
        h3{
            font-size: 30px;
            text-align: center;
            font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
        

        }
        select{
            padding:20px 70px;
            color: rgb(255, 255, 0);
            background-color: rgb(165, 42, 42);
            font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
            font-size: 30px;
        }
        
    </style>  
</head>
<body>
    <audio 

    id="sound"   
    src="./Som de Relógio Tic Tac.mp3"
    style="display: none;">
    </audio>


    <div class="container">

    <!--Criando select Segundos-->
    <h2>Segundos</h2>
    <select id="Segundos" name="Segundos"></select>

    <!--Criando o select Minutos-->   
    <h2>Minutos</h2>
    <select id="Minutos" name="Minutos"></select>

    
    <!--Criando select Horas-->
    <h2>Horas</h2>
    <select id="Horas" name="Horas" ></select>

    <!--Coloquei um espaço entre os butões de selecionar e começar-->
    <br>
    <br>    

    <!--CRIADO BUTÃO DE COMEÇAR-->
    <button id="Comecar">Começar!</button>
    </div>

   <!--CRIEI UM ID CHAMADO DISPLAY-->
    <div id="display">
        <h3>00:00:00</h3>

    
        <div class="alert"
        style="text-align: center;">
        
        </div>
      </div>

    <!--CRIANDO O SCRIPT-->
    <script>

        //Criando display
    var display = document.getElementById('display');

    //Criando display para Minutos
    var Minutos = document.getElementById('Minutos');

    //Criando display para Segundos
    var Segundos = document.getElementById('Segundos');

    //Criando display para Horas
    var Horas = document.getElementById('Horas');

    //Criando display para Comecar
    var Comecar = document.getElementById('Comecar');

    var cronometroSeg;//Varialvel Cronometro Segundos
    var MinutosAtual;//Varialvel Minuto Atual
    var SegundosAtual;//Varialvel Segundo Atual
    var HorasAtual;//Varialvel Hora Atual
    var interval;//Varialvel Intervalo

    //Preenchendo os minutos (até 60 minutos)
    for (var i = 0; i <=60; i++){
        Minutos.innerHTML+='<option value="'+i+'">'+i+'</option>';
    }

    //Preenchendo os segundos (até 60 segudos)
    for (var i = 0; i<=60; i++){
        Segundos.innerHTML+='<Option value="'+i+'">'+i+'</option>';
    }
       for (var i = 0; i <=60; i++){
        Minutos.innerHTML+='<option value="'+i+'">'+i+'</option>';
    }

    //Preenchendo os horas (até 60 horas)
    for (var i=0; i<=60; i++){
        Horas.innerHTML+='<option value="'+i+'">'+i+'</option>';
    }

    Comecar.addEventListener('click',function(){

        MinutosAtual = Minutos.value;
        SegundosAtual = Segundos.value;
        HorasAtual   = Horas.value;

        //criar tempo inicial
        display.childNodes[1].innerHTML = formatarTempo(HorasAtual) + ":" + formatarTempo(MinutosAtual) + ":" + formatarTempo(SegundosAtual);

        //Começar a contagem do tempo
        interval = setInterval(function(){

            SegundosAtual--;

            if(SegundosAtual <0){
                SegundosAtual = 59;
                MinutosAtual --;

            if(MinutosAtual <0){
                MinutosAtual = 59; 
                HorasAtual --;

            if(HorasAtual <0){
            clearInterval(interval); // Para o interval
            alert("Tempo esgotado!");//alerta do tempo
            document.getElementById("sound").play(); // Toca o som
            
            }
            }
            }

            //Atualizar o tempo de exibição
            display.childNodes[1].innerHTML = formatarTempo(HorasAtual) + ":" + formatarTempo(MinutosAtual) + ":" + formatarTempo(SegundosAtual);
            },1000);//Atualizar a cada segundo
    });
    // Função para formatar o tempo e sempre mostrar 2 dígitos
    function formatarTempo(tempo) {
            return tempo < 10 ? '0' + tempo : tempo;
        }
        

    </script>

</body>
</html>


