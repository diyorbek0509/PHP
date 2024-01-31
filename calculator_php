<?php 
	if ($_SERVER['REQUEST_METHOD']=="POST") {
		$button = $_POST["button"];
		$skrean = $_POST['skrean'];
		$amal = $_POST['amal'];
		$a = $_POST['a'];
		if($button=="C"){
			$skrean = "";
			$a=null;
			$amal = null;
		}
		elseif ($button=="del" and strlen($skrean)>0) {
			$split = str_split($skrean);
			unset($split[count($split)-1]);
			$skrean = implode("", $split);
		}
		elseif(is_numeric($button)){
			if($skrean=="" or $skrean==0){
				$skrean = $button;
			}else{
				$skrean.=$button;
			}
		}
		elseif($button!="=" and $amal==null and $skrean!=null){
			$amal = $button;
			$a = $skrean;
			$skrean = "";
		}
		elseif($button=='='){
			$b = $skrean;
			switch ($amal) {
				case '+':
					$skrean=$a+$b;
					break;
				case '-':
					$skrean=$a-$b;
					break;
				case '*':
					$skrean=$a*$b;
					break;
				case '/':
					if($b!=0){
						$skrean=$a/$b;
					}
					break;
			}
			if($b!=0){
			$a = null;
			$amal = null;			
			}
		}
	}
?>


<!DOCTYPE html>
<html lang="en" >
<head>
  <meta charset="UTF-8">
  <title>Calculator powered by diyorbek_05_09</title>
  <link rel="stylesheet" href="./style.css">
  <style>
  	* {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
		font-family: "Courier New", Courier, monospace;
	}
	body {
		display: flex;
		height: 100vh;
		align-items: center;
		justify-content: center;
		background-color: #202020;
	}
	.container {
		position: relative;
		min-width: 300px;
		min-height: 400px;
		padding: 40px 30px 30px;
		border-radius: 20px;
		box-shadow: 25px 25px 75px rgba(0, 0, 0, 0.25),
		10px 10px 70px rgba(0, 0, 0, 0.25), inset -5px -5px 15px rgba(0, 0, 0, 0.25),
			inset 5px 5px 15px rgba(0, 0, 0, 0.25);
	}
	.container .num {
		position: relative;
		display: grid;
		width: 80px;
		place-items: center;
		margin: 8px;
		height: 80px;
		background: linear-gradient(180deg, #2f2f2f, #3f3f3f);
		box-shadow: inset -8px 0 8px rgba(0, 0, 0, 0.15),
			inset 0 -8px 8px rgba(0, 0, 0, 0.25), 0 0 0 2px rgba(0, 0, 0, 0.75),
		10px 20px 25px rgba(0, 0, 0, 0.4);
		user-select: none;
		cursor: pointer;
		font-weight: 400;
		border-radius: 10px;
		color: white;
		font-size: 25px;
	}
	.calculator .num:active {
		filter: brightness(1.5);
	}
	.calculator {
		position: relative;
		display: grid;
	}
	.calculator .value {
		position: relative;
		grid-column: span 4;
		height: 100px;
		width: calc(100% - 20px);
		left: 10px;
		border: none;
		outline: none;
		background-color: #a7af7c;
		margin-bottom: 10px;
		border-radius: 10px;
		box-shadow: 0 0 0 2px rgba(0, 0, 0, 0.75);
		text-align: right;
		padding: 10px;
		font-size: 2em;
	}
	.calculator .clear {
		grid-column: span 2;
		width: 180px;
		background: #f00;
	}
	.calculator .del{
		grid-column: span 2;
		width: 180px;
		opacity: <?= ($skrean!=null) ? 1 : 0.4 ; ?>;
	}
	.calculator .clear::before {
		background: linear-gradient(90deg, #d20000, #ffffff5c);
		border-left: 1px solid #fff4;
		border-bottom: 1px solid #fff4;
		border-top: 1px solid #fff4;
	}
	.calculator .equal {
		background: #2196f3;
		opacity: <?= ($amal!=null and $skrean!=null) ? 1 : 0.4 ; ?>;
	}
	.calculator .equal::before{
		background: linear-gradient(90deg, #1479c9, #ffffff5c);
		border-left: 1px solid #fff4;
		border-bottom: 1px solid #fff4;
		border-top: 1px solid #fff4;
	}
	.number{
		border: 1px solid red;
		width: 100px;
		height: 20px;
		background-color: white;
		color: black;
	}
	.none{
		display: none;
	}
	.amal{
		opacity: <?= ($amal==null and $skrean!=null) ? 1 : 0.4 ; ?>;
	}
  </style>
</head>
<body>
	<div class="container">
	      <form action="" name="calc" class="calculator" method="post">
	      	<input type="text" class="value none" value="<?= $a ?>" name="a" readonly>
	      	<input type="text" class="value none" value="<?= $amal ?>" name="amal" readonly>
	        <input type="text" class="value" value="<?= $skrean ?>" name="skrean" readonly>
	        <button  type="submit" value="C" name="button" class="num clear">C</button>
	        <button type="<?= ($skrean!=null) ? "submit" : "button"; ?>" type="submit" value="del" name="button" class="num del"><-</button>
	        <button type="submit" value="7" name="button" class="num">7</button>
	        <button type="submit" value="8" name="button" class="num">8</button>
	        <button type="submit" value="9" name="button" class="num">9</button>
	        <button type="<?= ($amal==null and $skrean!=null) ? "submit" : "button"; ?>" type="submit" value="/" name="button" class="num amal">/</button>
	        <button type="submit" value="4" name="button" class="num">4</button>
	        <button type="submit" value="5" name="button" class="num">5</button>
	        <button type="submit" value="6" name="button" class="num">6</button>
	        <button type="<?= ($amal==null and $skrean!=null) ? "submit" : "button"; ?>" type="submit" value="*" name="button" class="num amal">*</button>
	        <button type="submit" value="1" name="button" class="num">1</button>
	        <button type="submit" value="2" name="button" class="num">2</button>
	        <button type="submit" value="3" name="button" class="num">3</button>
	        <button type="<?= ($amal==null and $skrean!=null) ? "submit" : "button"; ?>" type="submit" value="-" name="button" class="num amal">-</button>
	        <button type="submit" value="0" name="button" class="num">0</button>
	        <button type="submit" value="00" name="button" class="num">00</button>
	        <button type="<?= ($amal!=null and $skrean!=null) ? "submit" : "button"; ?>" type="submit" value="=" name="button" class="num equal">=</button>
	        <button type="<?= ($amal==null and $skrean!=null) ? "submit" : "button"; ?>" type="submit" value="+" name="button" class="num amal">+</button>
	      </form>
	    </div>
	</body>
</html>
