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
    
    \\profe aca empieza la clase \\
    
    
    
    <?php
    class calificacion
    {
        public function redondearNota($array){
            foreach ($array as $item => $value){
                $nota = $value[1];
                if ($nota < 38){
                    $array[$item] = [1 => $nota, 2 => $nota];
                    continue;
                }else if (($nota + 1) % 5 == 0){
                    $array[$item] = [1 => $nota, 2 => $nota + 1];
                }else if (($nota + 2) % 5 == 0){
                    $array[$item] = [1 => $nota, 2 => $nota + 2];
                }else{
                    $array[$item] = [1 => $nota, 2 => $nota];
                }
            }
            /*for($i = 1; $i <= 10; $i++){
                $nota = $array['Estudiante ' . $i][1];
                if ($nota < 38){
                    $array['Estudiante ' . $i] = [1 => $nota, 2 => $nota];
                    continue;
                }else if (($nota + 1) % 5 == 0){
                    $array['Estudiante ' . $i] = [1 => $nota, 2 => $nota + 1];
                }else if (($nota + 2) % 5 == 0){
                    $array['Estudiante ' . $i] = [1 => $nota, 2 => $nota + 2];
                }else{
                    $array['Estudiante ' . $i] = [1 => $nota, 2 => $nota];
                }
            }*/
            return $array;
        }
    }
    ?>
    
