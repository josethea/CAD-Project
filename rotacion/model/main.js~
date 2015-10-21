$(function(){

	var points=[];
	var polygons = [];

	var c = $("#canvas").get(0);
	var ctx = c.getContext('2d');
	var flag = false;
	var cleaned = true;
	var drawed = false;
	var pivot = [];

	$("#canvas").click(function(e){

		event = e;
		event = event || window.event;
		x = event.pageX - c.offsetLeft,
		y = event.pageY - c.offsetTop;
		y = convert(y);

		if(!drawed){
			Dot.draw(x,y,ctx);
			points.push({
				x:x,
				y:y
			});
		}
		else{
			pivot=[];
			clearScreen(c,ctx);
			polygons[0].draw();

			Dot.draw(x,y,ctx);

			pivot.push({
				x:x,
				y:y
			})
		}
		console.log("X = "+x);
		console.log("Y = "+y);



	});


	$("#draw").click(function(){

		if(!drawed){
			if(!flag||cleaned){
				//Crear un nuevo poligono

				if(points.length>1){
					var polygon =  new Polygon(points,ctx);
					// Dibujar el poligono
					polygon.draw();

					polygons.push(polygon);
					points = [];

					drawed = true;
					flag = true;
					cleaned = false;
				}
				else {
					alert('Por favor seleccione los puntos antes de dibujar')
				}
			}
			else {
				alert('Por favor realize una accion, rotar o mover, antes de volver a dibujar');
			}
		}
		else {
			alert('Por favor limpie la pantalla antes de continuar');
		}

	});

	$("#rotate").click(function(){
		if(drawed){

			var angle = $("#angle").val();
			if(angle.length!=0){
				if(pivot.length!=0){
					clearScreen(c,ctx);
					console.log("Poligono sin rotar " + polygons[0]);
					polygons[0].rotate(pivot[0],angle);
					console.log("Poligono rotado " + polygons[0]);
					pivot=[];
					flag = false;
				}
				else {
					alert('Por favor ingrese un punto de referencia para girar');
				}
			}
			else {
				alert('Por favor ingrese el angulo con el que se quiere rotar');
			}
		}
		else {
			alert('Por favor dibuje alguna figura antes de continuar');
		}
	});

	// $("#move").click(function(){
	// 	var point = points[points.length-1];
	// 	polygons[0].move(point.x,point.y);
	//
	// 	flag = false;
	// });

	$("#clear").click(function(){
		cleaned = true;
		drawed = false;
		polygons=[];
		clearScreen(c,ctx);
		var angle = $("#angle").val("");
	});

});

function clearScreen(c,ctx){
	ctx.clearRect(0,0,c.width,c.height);
}

function convert(y)
{
    y = Number(y);
    var yprima = 500 - y;
    return yprima;
}
