# codigoprofe

<?php
    require "Calificacion.php";
    $califica = new Calificacion();
    $arreglo = [];
    $totalAlumnos = 20;
    $notas = [];
    for ($i = 1; $i <= $totalAlumnos; $i++){
        $nota = mt_rand(1,100);
        $arreglo [$i] = [1 => $nota];
    }
    $notas = $califica->redondearNota($arreglo);
    $CantidadFila = $totalAlumnos;
    $CantidadColumna = 3;
    echo "<table border=5>";
    for ($fila = 1; $fila <= $CantidadFila; $fila++){
        echo "<tr>";
        for ($columna = 0; $columna < $CantidadColumna; $columna++){
            if ($columna == 0){
                echo "<td> Estudiante $fila </td>";
            }else if ($columna == 1){
                $numero = $notas[$fila][$columna];
                print_r("<td> $numero </td>");
            }else{
                $numero = $notas[$fila][$columna];
                echo "<td> $numero</td>";
            }
        }
        echo "</tr>";
    }
    echo "</table>";
    ?>
