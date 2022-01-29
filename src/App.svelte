<script>

	// Size //
	let width = 0;
	let height = 0;

	// Border-radius //
	let borderRadius = 0;
	let borderRadiusPer = 0;
	let toggleLabel = "Toggle / %";

	// Border-radius sides //
	let bdSideRadiusTopLeft = 0;
	let bdSideRadiusTopRight = 0;
	let bdSideRadiusBottomLeft = 0;
	let bdSideRadiusBottomRight = 0;

	let bdSideRadiusPerTopLeft = 0;
	let bdSideRadiusPerTopRight = 0;
	let bdSideRadiusPerBottomLeft = 0;
	let bdSideRadiusPerBottomRight = 0;

	// Border //
	let border = 0;

	// Color //
	let color = '#000000';
	let colorBorder = '#ff73b9';

	// Box-shadow //
	let hShadow = 0;
	let vShadow = 0;
	let blurShadow = 0;
	let spreadShadow = 0;
	let colorShadow = '#000000';

	let hShadowIn = 0;
	let vShadowIn = 0;
	let blurShadowIn = 0;
	let spreadShadowIn = 0;
	let colorShadowIn = '#000000';

	let active = false;
	let activeNav = false;
	let disabled = true;

	let openSize= true;
	let openBorder = false;
	let openBorderRadius = false;
	let openBorderRadiusPart = false;
	let openColor = true;
	let openShadow = false;
	let openShadowInset = false;

	// Border-radius Function //
	function borderLogic(value){
		if(borderRadius > 0 || borderRadiusPer > 0){
			bdSideRadiusTopLeft = 0;
			bdSideRadiusTopRight = 0;
			bdSideRadiusBottomLeft = 0;
			bdSideRadiusBottomRight = 0;

			bdSideRadiusPerTopLeft = 0;
			bdSideRadiusPerTopRight = 0;
			bdSideRadiusPerBottomLeft = 0;
			bdSideRadiusPerBottomRight = 0;
		}
	}

	// Toggle //
	function toggleRadius(){
		if(active === false){
			active = true;

			borderRadius = 0;
			bdSideRadiusTopLeft = 0;
			bdSideRadiusTopRight = 0;
			bdSideRadiusBottomLeft = 0;
			bdSideRadiusBottomRight = 0;

			toggleLabel = "Toggle / px"
		}
		else{
			active = false;

			borderRadiusPer = 0;
			bdSideRadiusPerTopLeft = 0;
			bdSideRadiusPerTopRight = 0;
			bdSideRadiusPerBottomLeft = 0;
			bdSideRadiusPerBottomRight = 0;

			toggleLabel = "Toggle / %"
		}
	}

	// Reset //
	function reset(){
		width = 0;
		height = 0;
		borderRadius = 0;
		borderRadiusPer = 0;
		bdSideRadiusTopLeft = 0;
		bdSideRadiusTopRight = 0;
		bdSideRadiusBottomLeft = 0;
		bdSideRadiusBottomRight = 0;
		bdSideRadiusPerTopLeft = 0;
		bdSideRadiusPerTopRight = 0;
		bdSideRadiusPerBottomLeft = 0;
		bdSideRadiusPerBottomRight = 0;
		border = 0;
		color = '#000000';
		colorBorder = '#ff73b9';
		hShadow = 0;
		vShadow = 0;
		blurShadow = 0;
		spreadShadow = 0;
		colorShadow = '#000000';
		hShadowIn = 0;
		vShadowIn = 0;
		blurShadowIn = 0;
		spreadShadowIn = 0;
		colorShadowIn = '#000000';
	}

	// Nav //
	function navToggle(){
		if(activeNav === false){
			activeNav = true;
		}
		else{
			activeNav = false
		}
	}

	const nav = document.getElementById("nav");
	const toggleNav = document.getElementById("toggleNav");

	const sizeMenu = document.getElementById("sizeMenu");
	const borderMenu = document.getElementById("borderMenu");
	const radiusMenu = document.getElementById("radiusMenu");
	const radiusPartMenu = document.getElementById("radiusPartMenu");
	const colorMenu = document.getElementById("colorMenu");
	const boxShadowMenu = document.getElementById("boxShadowMenu");
	const boxShadowInsetMenu = document.getElementById("boxShadowInsetMenu");

	document.onclick = (e) => {
		if(e.target.id !== 'nav' && e.target.id !== 'toggleNav'
			&& e.target.id !== 'sizeMenu' && e.target.id !== 'borderMenu'
			&& e.target.id !== 'radiusMenu' && e.target.id !== 'radiusPartMenu'
			&& e.target.id !== 'colorMenu' && e.target.id !== 'boxShadowMenu'
			&& e.target.id !== 'boxShadowInsetMenu' && e.target.id !== 'itemsNav'){
			activeNav = false;
		}
	}

</script>

<head>
	<link href="https://fonts.googleapis.com/icon?family=Material+Icons+Outlined" rel="stylesheet">
</head>

<!-- TODO 3
	Add box-shadow: {h}px {v}px {blur}px {spread}px {color};
		and 	 	inset {h}px {v}px {blur}px {spread}px {color};

	 TODO 4
	 Fix bug box-shadow

2/12/21 - 14:22
-->

<nav class="nav">
	<div class="toggle" id="toggleNav" class:active={activeNav} on:click="{navToggle}"></div>
	<div class="options" id="nav" class:active={activeNav}>
		<div class="navItems">
			<div class="navMenu menu-1">
				<label for="sizeMenu">Size</label>
				<input type="checkbox" id="sizeMenu" class="checkBox" bind:checked={openSize}>
			</div>
			<div class="navMenu menu-2">
				<label for="borderMenu">Border</label>
				<input type="checkbox" id="borderMenu" class="checkBox" bind:checked={openBorder}>
			</div>
			<div class="navMenu menu-3">
				<label for="radiusMenu">Border-raidus</label>
				<input type="checkbox" id="radiusMenu" class="checkBox" bind:checked={openBorderRadius}>
			</div>
			<div class="navMenu menu-4">
				<label for="radiusPartMenu">Border-raidus (part)</label>
				<input type="checkbox" id="radiusPartMenu" class="checkBox" bind:checked={openBorderRadiusPart}>
			</div>
			<div class="navMenu menu-5">
				<label for="colorMenu">Color</label>
				<input type="checkbox" id="colorMenu" class="checkBox" bind:checked={openColor}>
			</div>
			<div class="navMenu menu-6">
				<label for="boxShadowMenu">Box-shadow</label>
				<input type="checkbox" id="boxShadowMenu" class="checkBox" bind:checked={openShadow}>
			</div>
			<div class="navMenu menu-7">
				<label for="boxShadowInsetMenu">Box-shadow (inset)</label>
				<input type="checkbox" id="boxShadowInsetMenu" class="checkBox" bind:checked={openShadowInset}>
			</div>
		</div>
	</div>
</nav>

<main>
	<h1>Make object</h1>
	<div class="make-box">
		<!-- Side Width / Height -->
		<div class:open={!openSize}>
			<div class="value-custom size-grid" id="size-value">
				<lable for="width-value" id="w-label">width - px</lable>
				<div class="value-custom" id="width-value">
					<input class="valueShow" type="number" bind:value={width} min=0 max=500>
					<input class="slider" type="range" bind:value={width} min=0 max=500>
				</div>

				<lable for="height-value" id="h-label">height - px</lable>
				<div class="value-custom" id="height-value">
					<input class="valueShow" type="number" bind:value={height} min=0 max=500>
					<input class="slider" type="range" bind:value={height} min=0 max=500>
				</div>

			</div>
		</div>

		<!-- border -->
		<div class:open={!openBorder}>
			<div class="value-custom border-grid" id="border-value">
				<lable for="border-value" id="border-label">border</lable>
				<div class="value-custom" id="border-custom">
					<input class="valueShow" type="number" bind:value={border} min=0 max={width >= height ? height/2 : width/2}>
					<input class="slider" type="range" bind:value={border} min=0 max={width >= height ? height/2 : width/2}>
				</div>
			</div>
		</div>
		
		<!-- Border radius all side -->
		<div class:open={!openBorderRadius}>
			<div id="border-radius">
				<lable for="toggleBtn" id="border-radius-label">border-radius</lable>
				<button on:click="{toggleRadius}" class="btn" id="toggleBtn">{toggleLabel}</button>
				<div class="value-custom" id="border-radius-value">		
					<div class:active={active} class="border-radius-items" id="br-px">
						<label>
							<input class="valueShow" type="number" 
								bind:value={borderRadius} 
								on:input="{e => borderLogic(e.target.value)}" 
								min=0 max=250>
							<lable for="height-value">px</lable>
							<input class="slider" type="range" 
								bind:value={borderRadius} 
								on:input="{e => borderLogic(e.target.value)}" 
								min=0 max=250>
						</label>
					</div>

					<div class:active={active} class="border-radius-items" id="br-per">
						<label>
							<input class="valueShow" type="number" 
								bind:value={borderRadiusPer} 
								on:input="{e => borderLogic(e.target.value)}" 
								min=0 max=100>
							<lable for="height-value">%</lable>
							<input class="slider" type="range" 
								bind:value={borderRadiusPer} 
								on:input="{e => borderLogic(e.target.value)}" 
								min=0 max=100>
						</label>
					</div>
					
				</div>
			</div>
		</div>

		<!-- Border radius some side -->
		<div class:open={!openBorderRadiusPart}>
			<div class="value-custom" id="border-radius-part">
				<div class:active={active} class="br-sides-toggle" id="br-sides-px">
					<!-- px -->
					<div class="value-custom br-sides-grid" id="border-radius-sides-px">
						<!-- Top-Left -->
						<lable for="br-t-l" id="brTL-label">Top-left</lable>
						<div class:active={active} class="border-radius-sides" id="br-t-l">
							<input class="valueShow" type="number" 
									bind:value={bdSideRadiusTopLeft} 
									disabled={borderRadius > 0 ? disabled : !disabled}
									min=0 max={borderRadius > 0 ? 0 : 255}>
							<lable for="height-value">px</lable>
							<input class="slider" type="range" 
									bind:value={bdSideRadiusTopLeft} 
									disabled={borderRadius > 0 ? disabled : !disabled}
									min=0 max={borderRadius > 0 ? 0 : 255}>
						</div>

						<!-- Top-Right -->
						<lable for="br-t-l" id="brTR-label">Top-right</lable>
						<div class:active={active} class="border-radius-sides" id="br-t-r">
							<input class="valueShow" type="number" 
									bind:value={bdSideRadiusTopRight} 
									disabled={borderRadius > 0 ? disabled : !disabled}
									min=0 max={borderRadius > 0 ? 0 : 255}
							>
							<lable for="height-value">px</lable>
							<input class="slider" type="range" 
									bind:value={bdSideRadiusTopRight} 
									disabled={borderRadius > 0 ? disabled : !disabled}
									min=0 max={borderRadius > 0 ? 0 : 255}
							>
						</div>

						<!-- Bottom-Left -->
						<lable for="br-t-l" id="brBL-label">Bottom-Left</lable>
						<div class:active={active} class="border-radius-sides" id="br-b-l">
							<input class="valueShow" type="number" 
									bind:value={bdSideRadiusBottomLeft} 
									disabled={borderRadius > 0 ? disabled : !disabled}
									min=0 max={borderRadius > 0 ? 0 : 255}
							>
							<lable for="height-value">px</lable>
							<input class="slider" type="range" 
									bind:value={bdSideRadiusBottomLeft} 
									disabled={borderRadius > 0 ? disabled : !disabled}
									min=0 max={borderRadius > 0 ? 0 : 255}
							>
						</div>

						<!-- Bottom-Right -->
						<lable for="br-t-l" id="brBR-label">Bottom-right</lable>
						<div class:active={active} class="border-radius-sides" id="br-b-r">
							<input class="valueShow" type="number" 
									bind:value={bdSideRadiusBottomRight} 
									disabled={borderRadius > 0 ? disabled : !disabled}
									min=0 max={borderRadius > 0 ? 0 : 255}
							>
							<lable for="height-value">px</lable>
							<input class="slider" type="range" 
									bind:value={bdSideRadiusBottomRight} 
									disabled={borderRadius > 0 ? disabled : !disabled}
									min=0 max={borderRadius > 0 ? 0 : 255}
							>
						</div>
					</div>
				</div>

				<!-- percent -->
				<div class:active={active} class="br-sides-toggle" id="br-sides-per">
					<div class="value-custom br-sides-grid" id="border-radius-sides-per">
						<!-- Top-Left -->
						<lable for="br-t-l" id="brTL-label">Top-left</lable>
						<div class:active={active} class="border-radius-sides" id="br-t-l">
							<input class="valueShow" type="number" 
									bind:value={bdSideRadiusPerTopLeft} 
									disabled={borderRadiusPer > 0 ? disabled : !disabled}
									min=0 max={borderRadiusPer > 0 ? 0 : 100}
							>
							<lable for="height-value">%</lable>
							<input class="slider" type="range" 
									bind:value={bdSideRadiusPerTopLeft} 
									disabled={borderRadiusPer > 0 ? disabled : !disabled}
									min=0 max={borderRadiusPer > 0 ? 0 : 100}
							>
						</div>

						<!-- Top-Right -->
						<lable for="br-t-l" id="brTR-label">Top-right</lable>
						<div class:active={active} class="border-radius-sides" id="br-t-r">
							<input class="valueShow" type="number" 
									bind:value={bdSideRadiusPerTopRight} 
									disabled={borderRadiusPer > 0 ? disabled : !disabled}
									min=0 max={borderRadiusPer > 0 ? 0 : 100}
							>
							<lable for="height-value">%</lable>
							<input class="slider" type="range" 
									bind:value={bdSideRadiusPerTopRight} 
									disabled={borderRadiusPer > 0 ? disabled : !disabled}
									min=0 max={borderRadiusPer > 0 ? 0 : 100}
							>
						</div>

						<!-- Bottom-Left -->
						<lable for="br-t-l" id="brBL-label">Bottom-Left</lable>
						<div class:active={active} class="border-radius-sides" id="br-b-l">
							<input class="valueShow" type="number" 
									bind:value={bdSideRadiusPerBottomLeft} 
									disabled={borderRadiusPer > 0 ? disabled : !disabled}
									min=0 max={borderRadiusPer > 0 ? 0 : 100}
							>
							<lable for="height-value">%</lable>
							<input class="slider" type="range" 
									bind:value={bdSideRadiusPerBottomLeft} 
									disabled={borderRadiusPer > 0 ? disabled : !disabled}
									min=0 max={borderRadiusPer > 0 ? 0 : 100}
							>
						</div>

						<!-- Bottom-Right -->
						<lable for="br-t-l" id="brBR-label">Bottom-right</lable>
						<div class:active={active} class="border-radius-sides" id="br-b-r">
							<input class="valueShow" type="number" 
									bind:value={bdSideRadiusPerBottomRight} 
									disabled={borderRadiusPer > 0 ? disabled : !disabled}
									min=0 max={borderRadiusPer > 0 ? 0 : 100}
							>
							<lable for="height-value">%</lable>
							<input class="slider" type="range" 
									bind:value={bdSideRadiusPerBottomRight} 
									disabled={borderRadiusPer > 0 ? disabled : !disabled}
									min=0 max={borderRadiusPer > 0 ? 0 : 100}
							>
						</div>
					</div>
				</div>
			</div>
		</div>

		<!-- Color -->
		<div class:open={!openColor}>
			<div class="value-custom color-grid" id="color-value">

				<div class="openColor">
					<div class="color-items">
						<lable class="colorLabel" for="colorpicker" id="color-label">Color</lable>
						<input class="picker" type="color" id="colorpicker" bind:value={color}>
						<p class="colorCode" id="color-code">Hex : <spac style="font-weight: 700;">{color}</spac></p>
					</div>
				</div>

				<div class="openColor" class:open={!openBorder}>
					<div class="color-items">
						<lable class="colorLabel" for="colorpickerBorder" id="color-border-label">Border color</lable>
						<input class="picker" type="color" id="colorpickerBorder" bind:value={colorBorder}>
						<p class="colorCode" id="color-border-code">Hex : <spac style="font-weight: 700;">{colorBorder}</spac></p>
					</div>
				</div>

				<div class="openColor" class:open={!openShadow}>
					<div class="color-items">
						<lable class="colorLabel" for="colorpickerShadow" id="color-shadow-label">Shadow color</lable>
						<input class="picker" type="color" id="colorpickerShadow" bind:value={colorShadow}>
						<p class="colorCode" id="color-shadow-code">Hex : <spac style="font-weight: 700;">{colorShadow}</spac></p>
					</div>
				</div>

				<div class="openColor" class:open={!openShadowInset}>
					<div class="color-items">
						<lable class="colorLabel" for="colorpickerShadowIn" id="color-shadow-in-label">Shadow color (inset)</lable>
						<input class="picker" type="color" id="colorpickerShadowIn" bind:value={colorShadowIn}>
						<p class="colorCode" id="color-shadow-in-code">Hex : <spac style="font-weight: 700;">{colorShadowIn}</spac></p>
					</div>
				</div>
			</div>
		</div>

		<!-- box-shadow -->
		<div class:open={!openShadow}>
			<div class="value-custom box-shadow" id="box-shadow">
				<lable for="outShadow" id="box-shadow-label">box-shadow</lable>
				<div class="value-custom outShadow">
					<!-- {h}px {v}px {blur}px {spread}px {color} -->
					<div class="value-custom positionShadow">
						<lable for="hShadow" class="hShadow-label">Horizontal</lable>
						<div class="value-custom hShadow" >
							<input class="valueShow" type="number" 
									bind:value={hShadow} 
									min=-100 max=100>
							<lable for="hShadow">px</lable>
							<input class="slider" type="range" 
									bind:value={hShadow} 
									min=-100 max=100>
						</div>

						<lable for="vShadow" class="vShadow-label">Vertical</lable>
						<div class="value-custom vShadow" >
							<input class="valueShow" type="number" 
									bind:value={vShadow} 
									min=-100 max=100>
							<lable for="vShadow">px</lable>
							<input class="slider" type="range" 
									bind:value={vShadow} 
									min=-100 max=100>
						</div>

						<lable for="bShadow" class="bShadow-label">Blur</lable>
						<div class="value-custom bShadow" >
							<input class="valueShow" type="number" 
									bind:value={blurShadow} 
									min=0 max=100>
							<lable for="bShadow">px</lable>
							<input class="slider" type="range" 
									bind:value={blurShadow} 
									min=0 max=100>
						</div>

						<lable for="sShadow" class="sShadow-label">Spread</lable>
						<div class="value-custom sShadow" >
							<input class="valueShow" type="number" 
									bind:value={spreadShadow} 
									min=0 max=100>
							<lable for="sShadow">px</lable>
							<input class="slider" type="range" 
									bind:value={spreadShadow} 
									min=0 max=100>
						</div>
					</div>
				</div>
			</div>
		</div>
		<div class:open={!openShadowInset}>
			<div class="value-custom box-shadow" id="box-shadow-inset">
				<lable for="insetShadow" id="box-shadow-inset-label">box-shadow (inset)</lable>
				<div class="value-custom insetShadow">
					<!-- {h}px {v}px {blur}px {spread}px {color} -->
					<div class="value-custom positionShadow">
						<lable for="hShadow" class="hShadow-label">Horizontal</lable>
						<div class="value-custom hShadow" >
							<input class="valueShow" type="number" 
									bind:value={hShadowIn} 
									min=-100 max=100>
							<lable for="hShadow">px</lable>
							<input class="slider" type="range" 
									bind:value={hShadowIn} 
									min=-100 max=100>
						</div>

						<lable for="vShadow" class="vShadow-label">Vertical</lable>
						<div class="value-custom vShadow" >
							<input class="valueShow" type="number" 
									bind:value={vShadowIn} 
									min=-100 max=100>
							<lable for="vShadow">px</lable>
							<input class="slider" type="range" 
									bind:value={vShadowIn} 
									min=-100 max=100>
						</div>

						<lable for="bShadow" id="bShadow-label">Blur</lable>
						<div class="value-custom bShadow" >
							<input class="valueShow" type="number" 
									bind:value={blurShadowIn} 
									min=0 max=100>
							<lable for="bShadow">px</lable>
							<input class="slider" type="range" 
									bind:value={blurShadowIn} 
									min=0 max=100>
						</div>	

						<lable for="sShadow" class="sShadow-label">Spread</lable>
						<div class="value-custom sShadow" >
							<input class="valueShow" type="number" 
									bind:value={spreadShadowIn} 
									min=0 max=100>
							<lable for="sShadow">px</lable>
							<input class="slider" type="range" 
									bind:value={spreadShadowIn} 
									min=0 max=100>
						</div>
					</div>
				</div>
			</div>
		</div>

		<div class="footer-menu">
			<button on:click="{reset}" class="btn btn-reset">
				<span id="reset-icon" class="material-icons-outlined">delete</span>
				Reset
			</button>
		</div>
	</div>

	<h1>Output</h1>
	<div class="dummy">
		<div class="dummy-items" id="dummy-size" 
			style="	width: {width}px;
					height: {height}px;
					border-radius: {borderRadius}px;
					border-radius: {borderRadiusPer}%;
					background: {color};

					border-top-left-radius: {bdSideRadiusTopLeft}px;
					border-top-right-radius: {bdSideRadiusTopRight}px;
					border-bottom-left-radius: {bdSideRadiusBottomLeft}px;
					border-bottom-right-radius: {bdSideRadiusBottomRight}px;

					border-top-left-radius: {bdSideRadiusPerTopLeft}%;
					border-top-right-radius: {bdSideRadiusPerTopRight}%;
					border-bottom-left-radius: {bdSideRadiusPerBottomLeft}%;
					border-bottom-right-radius: {bdSideRadiusPerBottomRight}%;

					border: {border}px solid {colorBorder};

					box-shadow: {hShadow}px {vShadow}px {blurShadow}px {spreadShadow}px {colorShadow},
								inset {hShadowIn}px {vShadowIn}px {blurShadowIn}px {spreadShadowIn}px {colorShadowIn};
				"
			></div>
	</div>
</main>
<p class="myCopyRight">Made by Thianrawit Phaedsri</p>

<style>
	*{
		box-sizing: border-box;
	}

	.myCopyRight{
		position: sticky;
		display: flex;
		justify-content: flex-end;
		padding: 10px;
		margin: 5px;
		font-size: calc(0.15vw + 0.15vh + 2vmin);
		font-weight: lighter;
		font-family:-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", sans-serif;
	}

	.open{
		display: none;
	}

	main {
		text-align: center;
		padding: 1em;
		margin: 0 auto;

		display: grid;
		justify-content: center;
		align-items: center;
		font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", sans-serif;

	}

	nav{
		margin: 0;
		padding: 0;
		position: relative;
		font-weight: lighter;
		font-family:-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", sans-serif;
	}

	nav .toggle{
		width: calc(2vw + 2vh + 2vmin);
		height: calc(2vw + 2vh + 2vmin);
		background: #353535;

		position: fixed;
		top: 0;
		right: 0;

		display: flex;
		justify-content: center;
		align-items: center;

		cursor: pointer;
		z-index: 999;
	}

	nav .toggle::before{
		content: "";
		position: absolute;
		top: 35%;

		width: calc(1vw + 1vh + 2vmin);
    	height: calc(0.1vw + 0.1vh + 0.25vmin);
		background: #fff;

		transition: 0.25s all ease;
	}

	nav .toggle::after{
		content: "";
		position: absolute;
		bottom: 35%;

		width: calc(1vw + 1vh + 2vmin);
    	height: calc(0.1vw + 0.1vh + 0.25vmin);
		background: #fff;
		transition: 0.25s all ease;
	}

	nav .toggle.active::before{
		transform: rotate(-225deg);
		top: 45%;
		transition: 0.25s all ease;
	}

	nav .toggle.active::after{
		transform: rotate(-135deg);
		top: 45%;
		transition: 0.25s all ease;
	}

	nav .options{
		width: 35%;
		height: 100%;
		background: rgba(0,0,0,0.45);
		backdrop-filter: blur(10px);

		position: fixed;
		top: 0;
		right: -50%;

		z-index: 1;
		transition: 0.25s all ease;

		display: grid;
		align-items: center;
		align-content: center;
		justify-content: center;
		justify-items: center;
	}

	nav .options.active{
		top: 0;
		right: 0;
		transition: 0.25s all ease;
	}

	nav .navItems{
		display: grid;
		align-items: center;
		align-content: center;
		justify-items: center;

		grid-template-columns: auto;
		grid-template-rows: auto;

		min-width: 135%;
	}

	nav .navMenu label{
		grid-area: l;
	}

	nav .navMenu input{
		grid-area: i;
	}

	nav .navMenu input[type=checkbox]{
		width: calc(0.2vw + 0.2vh + 2vmin);
		height: calc(0.2vw + 0.2vh + 2vmin);
		border: none;
		outline: none;
		cursor: pointer;
	}

	nav .navMenu{
		display: grid;
		align-items: center;
		justify-content: space-between;

    	width: 100%;
		margin: 5%;
		padding: 5%;

		font-size: calc(0.1vw + 0.1vh + 2vmin);

		color: #eaeff0;

		grid-template-areas:
		"l i"
		;
	}

	:global(body){
		background: #efeaf0;
	}

	h1 {
		color: #161616;
		text-transform: uppercase;
		font-size: 2em;
		font-weight: 100;
	}

	.btn{
		padding: 10px 25px;
		margin: 10px;

		background: #5a5a5a;
		color: #efeaf0;
		border: none;
		border-radius: 20px;
		opacity: 0.75;
		transition: 0.25s all ease;

		font-weight: 100;
		cursor: pointer;
	}

	.btn:hover{
		opacity: 1;
	}

	.make-box{
		display: flex;
		justify-content: center;
		align-items: center;
		padding: 10px;
		margin: 10px;

		border-radius: 20px;

		box-shadow: 10px 10px 20px rgba(0, 0, 0, 0.15),
					-10px -10px 20px rgba(255, 255, 255, 0.75);
	}

	.make-box{
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
	}

	.value-custom{
		display: flex;
		justify-content: center;
		align-items: center;

		padding: 10px;
	}

	/*Grid size*/
	#w-label{
		grid-area: wl;
	}
	#h-label{
		grid-area: hl;
	}
	#width-value{
		grid-area: w;
	}
	#height-value{
		grid-area: h;
	}

	.size-grid{
		display: grid;
		grid-template-columns: auto;
		grid-template-rows: auto;
		grid-template-areas:
		'wl hl'
		'w h';

		margin: 10px;
		padding: 10px;

		justify-items: center;
    	align-content: center;
	}
	/**************************************/

	/*Grid size*/

	.colorLabel{
		grid-area: cl;
	}
	.picker{
		grid-area: p;
		width: 5em;
		height: 3em;
	}
	.colorCode{
		grid-area: cc;
	}

	.color-items{
		display: grid;
		grid-template-columns: 10em;
		grid-template-rows: 25% 50% 25%;
		grid-template-areas:
		"cl"
		"p"
		"cc";

		padding: 10px;

		justify-items: center;
    	align-content: center;
	}

	.color-grid{
		display: grid;
		grid-template-columns: auto auto;
		grid-template-rows: auto;
		grid-gap: 10%;
		
		margin: 10px 10px 20px;
		padding: 10px;

		justify-items: center;
    	align-content: center;
	}
	/**************************************/

	#size-value{
		flex-direction: row;
	}

	.valueShow{
		height: 35px;
		border-radius: 20px;
		text-align: center;
		outline: none;
		border: none;

		background: #efefef;
		box-shadow: inset 5px 5px 5px rgba(0, 0, 0, 0.1),
					inset -5px -5px 5px rgba(255, 255, 255, 0.95);
	}

	.slider {
		-webkit-appearance: none;
		width: 100%;
		height: 25px;
		border-radius: 20px;

		background: #efefef;
		box-shadow: inset 5px 5px 5px rgba(0, 0, 0, 0.1),
					inset -5px -5px 5px rgba(255, 255, 255, 0.95);
		
		overflow: hidden;
		border: none;
		outline: none;
		opacity: 0.7;
		-webkit-transition: .2s;
		transition: 0.25s all ease;
	}

	.slider:hover {
		opacity: 1;
	}

	.slider::-webkit-slider-thumb {
		-webkit-appearance: none;
		appearance: none;
		width: 25px;
		height: 25px;
		border-radius: 20px;
		background: #5a5a5a;
		box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.3);
		cursor: pointer;
	}

	.picker{
		border: none;
		outline: none;

	}

	input{
		margin: 10px;
	}

	.border-radius-items label{
		display: flex;
		justify-content: center;
		align-items: center;
	}

	/*Toggle Border-radius*/
	.border-radius-items#br-px{
		display: block;
	}

	.border-radius-items#br-per{
		display: none;
	}

	.border-radius-items#br-px.active{
		display: none;
	}

	.border-radius-items#br-per.active{
		display: block;
	}
	/**************************************/

	/* Grid border-radius sides */
	#brTL-label{
		grid-area: tl;
		font-size: 14px;
	}
	#br-t-l{
		grid-area: TL;
	}

	#brTR-label{
		grid-area: tr;
		font-size: 14px;
	}
	#br-t-r{
		grid-area: TR;
	}

	#brBL-label{
		grid-area: bl;
		font-size: 14px;
	}
	#br-b-l{
		grid-area: BL;
	}

	#brBR-label{
		grid-area: br;
		font-size: 14px;
	}
	#br-b-r{
		grid-area: BR;
	}

	.border-radius-sides{
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.br-sides-toggle#br-sides-px{
		display: block;
	}
	.br-sides-toggle#br-sides-per{
		display: none;
	}
	.br-sides-toggle#br-sides-px.active{
		display: none;
	}
	.br-sides-toggle#br-sides-per.active{
		display: block;
	}

	.br-sides-grid{
		display: grid;
		grid-template-columns: auto;
		grid-template-rows: auto;
		grid-row-gap: 10px;

		grid-template-areas:
		'tl tr'
		'TL TR'
		'bl br'
		'BL BR';
		
		margin: 0 0 20px 0;
		padding: 10px;

		justify-items: center;
    	align-content: center;
	}

	/* Border */

	#border-radius{
		display: grid;
		justify-content: center;
		align-items: center;
		justify-items: center;

		grid-template-columns: auto;
		grid-template-rows: auto;
	}

	#border-label{
		grid-area: bl;
	}
	#border-radius-label{
		padding: 10px;
	}
	#border-custom{
		grid-area: bc; 
	}

	.border-grid{
		display: grid;
		grid-template-columns: auto;
		grid-template-rows: auto;
		grid-row-gap: 10px;

		grid-template-areas:
		'bl'
		'bc';
		
		margin: 10px;
		padding: 10px;

		justify-items: center;
    	align-content: center;
	}

	/* Box-shadow */
	#box-shadow-label{
		grid-area: bl;
	}

	.outShadow{
		grid-area: os;

		display: grid;
		justify-items: center;
		justify-content: center;
		align-items: center;
		grid-template-columns: auto;
		grid-template-rows: auto;
	}

	.insetShadow{
		display: grid;
		justify-items: center;
		justify-content: center;
		align-items: center;
		grid-template-columns: auto;
		grid-template-rows: auto;
	}

	.box-shadow{
		display: grid;
		grid-template-columns: auto;
		grid-template-rows: auto;

		grid-template-areas:
		"bl"
		"os";

		margin: 10px;
		padding: 10px;

		justify-items: center;
    	align-content: center;
	}

	.hShadow{
		grid-area: h;
	}
	.hShadow-label{
		grid-area: hl;
	}
	.vShadow{
		grid-area: v;
	}
	.vShadow-label{
		grid-area: vl;
	}

	.bShadow{
		grid-area: b;
	}
	.bShadow-label{
		grid-area: bl;
	}
	.sShadow{
		grid-area: s;
	}
	.sShadow-label{
		grid-area: sl;
	}

	.positionShadow{
		display: grid;
		grid-template-columns: auto;
		grid-template-rows: auto;

		grid-template-areas:
		'hl vl'
		'h v'
		'bl sl'
		'b s';

		margin: 10px;
		padding: 10px;

		justify-content: center;
		align-content: center;
	}

	.footer-menu{
		display: flex;
		width: 100%;
		justify-content: right;
	}

	.btn-reset{
		border: 2px solid #7f7e7f;
		color: #7f7e7f;
		font-weight: 700;
		background: transparent;

		display: inline-flex;
		justify-self: center;
		align-items: center;
	}

	span{
		padding: 0 5px;
	}

	.dummy{
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.dummy-items{
		margin: 10px;
		background: red;
	}

	/*Responsive*/
	@media (max-width: 640px) {
		main {
			max-width: none;
		}

		.size-grid{
			display: grid;
			grid-template-columns: auto;
			grid-template-rows: auto;
			grid-template-areas:
			'wl'
			'w'
			'hl'
			'h';

			margin: 10px;
			padding: 10px;
		}

		.br-sides-grid{
			display: grid;
			grid-template-columns: auto;
			grid-template-rows: auto;
			grid-row-gap: 10px;

			grid-template-areas:
			'tl'
			'TL'
			'tr'
			'TR'
			'bl'
			'BL'
			'br'
			'BR';
			
			margin: 40px 0;
			padding: 10px;

			justify-items: center;
			align-content: center;
		}

		nav .options{
			min-width: 100%;
			min-height: 100%;

			right: -100%;
		}

		nav .navItems{
			min-width: 120%;

			grid-template-columns: auto auto;
			grid-template-rows: auto;
		}

		nav .navMenu input[type=checkbox]{
			width: calc(0.5vw + 0.5vh + 2vmin);
			height: calc(0.5vw + 0.5vh + 2vmin);
		}

		nav .navMenu{
			font-size: calc(0.5vw + 0.5vh + 2vmin);
		}

		.positionShadow{
			grid-template-areas:
			'hl'
			'h'
			'vl'
			'v'
			'bl'
			'b'
			'sl'
			's';
		}
	}

</style>