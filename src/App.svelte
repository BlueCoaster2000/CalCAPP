<script>
	let peso;
	let sexoSelect = ''
	let caloriasMantener='';
	let caloriasSubir='';
	let caloriasBajar='';
	let actividad;
	let mostrarResultado = false; //Para mostrar el div del resultado
	function handleChange(event) { //Funcion para registrar cada que cambia el sexooo
    sexoSelect = event.target.value;
  }
  function calcular(){
	
	if(parseInt(peso)<=0 || peso == undefined){
		alert('Introduce todos los datos');
	}else{

		if(sexoSelect == 'Hombre'){
			caloriasMantener = peso*25;
			caloriasBajar = caloriasMantener-300;
			caloriasSubir = caloriasMantener+300;
		}else{
			caloriasMantener = peso*23
			caloriasBajar = caloriasMantener-300;
			caloriasSubir = caloriasMantener+300;
		}
		mostrarResultado = true;
		
	}
}
</script>

<main>
	<h1 style="color:#0E6EFD;font-weight:bolder;" class="text-center">CalCAPP</h1>
	<p class="h2">Introduce tu peso (KG)</p><input type="number" bind:value={peso}>
	<p class="h2">Introduce tu edad</p><input type="number" name="" id="">
	<p class="h2">Introduce tu sexo</p>
	<select bind:value={sexoSelect} on:change={handleChange}>
		<option value="">Seleccione...</option>
		<option value="Hombre">Hombre</option>
		<option value="Mujer">Mujer</option>
	</select>
	<p><b>{sexoSelect}</b></p>
	<p class="h2">Nivel de Actividad:</p>
	<div class="container">
		<p>Sedentario</p><input type="radio" bind:group={actividad} value="mateo" name="nivelAct" id="">
		<p>Moderado</p><input type="radio" bind:group={actividad} name="nivelAct" id="">
		<p>Normal(3-4/Semana)</p><input bind:group={actividad} type="radio" name="nivelAct" id="">
		<p>Alto(5/Semana)</p><input type="radio" bind:group={actividad}  name="nivelAct" id="">
		<p>Profesional(2/Día)</p><input type="radio" bind:group={actividad} name="nivelAct" id="">
	</div>
	<button on:click={calcular} class="btn btn-secondary">Terminar</button>


	{#if mostrarResultado}
		<div class="bg-primary">
			<h3>Calorías Diarias para mantenerte en tu peso</h3>
			<h4>{caloriasMantener}</h4>
			
		</div>
		<div class="bg-danger">
			<h3>Calorías Necesarias Para Bajar de peso</h3>
			<h3>{caloriasBajar}</h3>
		</div>
		<div class="bg-success">
			<h3>Calorías Necesarias Para Subir de peso</h3>
			<h3>{caloriasSubir}</h3>
		</div>
		{:else}
		<h3 class="bg-warning mt-4 p-3">Tu resultado se mostrará aquí</h3>
		{/if}

	</main>
	
	<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>