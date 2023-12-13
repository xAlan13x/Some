PHP
display_errors
Default Value: On
Default Value: On

extension_dir = "C:/php/ext" line 770
extension=mysqli	line 940

Apache

187 en load module:
LoadModule php_module "c:\php\php8apache2_4.dll"
AddHandler application/x-httpd-php .php
PHPIniDir "C:\Windows"

-----------------------
<?php

$cnn=new mysqli("localhost","root", "1301","web1");

if(mysqli_connect_errno()){
    echo "Error".$cnn->connect_errno;
    exit();
}else{
    //echo "Conexion OK";
    //echo var_dump($cnn);
    $consul=$cnn->query("select * from cliente");
    //echo var_dump($consul);
    //consulta
    /*
    while($ren=$consul->fetch_array(MYSQLI_ASSOC)){
        echo $ren["nombre"]."<br/>";
    }*/
    //insert, Update, delete
    /*$ejec=$cnn->query("insert into cliente values(null, 'Juan', 'San felipe')");

    echo $ejec;*/
}

?>

function crear_usuario(){
    var sol=new XMLHttpRequest();
    var datos=new FormData();
    var contenedor=document.getElementById("contenedor");
    var f=document.querySelector("#form-crear-usuario");
    datos.append("opc", "usuario");
    datos.append("acc", "crear");
    datos.append("nombre", f.nombre.value);
    datos.append("paterno", f.paterno.value);
    datos.append("materno", f.materno.value);
    datos.append("correo", f.correo.value);
    datos.append("contrasena", f.contrasena.value);
    datos.append("estado", "activo");
    //alert("alet");
    sol.addEventListener("load", function(e){
        e.target.responseText;
    });

    sol.open("POST", "php/procesos.php");
    sol.send(datos);
    alert("Usuario Creado con exito");
    view_login("login");
}

case 'agregar':
                    $url = "productos.txt";
                    $arch = fopen($url,'a+');
                    fwrite($arch, "\n". $_POST['codigo']."-@-". $_POST['nombre']."-@-". $_POST['medida']."-@-".$_POST['cantidad']."-@-".$_POST['stockMax']."-@-".$_POST['stockMin']."-@-".$_POST['pu']."-@-".$_POST['provedor']."@@");
                    fclose($arch);
                    //echo var_dump($_POST);

                    break;

case 'modificar':
                    //echo var_dump($_POST);
                    $ar="";
                    $cadena="";
                    $url = "productos.txt";
                    $arch=fopen($url,"r");

                    while(!feof($arch)){
                        $ar=explode("-@-",fgets($arch));
                        //echo var_dump($ar);
                        //echo $_POST['codigo'];
                        if($ar[0]==$_POST['codigo']){
                            $last_data=str_replace("@@", "", $_POST['pu']);
                            //echo $last_data;
                            $cadena.=$_POST['codigo']."-@-". $_POST['nombre']."-@-". $_POST['medida']."-@-".$_POST['cantidad']."-@-".$_POST['stockMax']."-@-".$_POST['stockMin']."-@-".$last_data."@@"."\n";
                        }else{
                            if($ar[0]!=""){
                                $cadena.=$ar[0]."-@-". $ar[1]."-@-". $ar[2]."-@-". $ar[3]."-@-". $ar[4]."-@-". $ar[5]."-@-". $last_data."@@"."\n";
                            }
                            #echo $cadena;
                        }
                    }
                    //echo $cadena;
                    
                    fclose($arch);
                    $arch=fopen($url,"w");
                    fwrite($arch,$cadena);
                    fclose();

                    break;


case 'listado':
                    $ruta = "productos.txt";
                    $archivo = fopen($ruta,"r");
                    $codigo="";
                    $ban=TRUE;
                    while (!feof($archivo)) {
                        $linea = fgets($archivo);
                        if (!empty($linea)) {
                            $renglon = explode("-@-", $linea); 
                            $codigo.= "<tr>
                                    <td class='small'>{$renglon[0]}</td> 
                                    <td class='small'>{$renglon[1]}</td> 
                                    <td class='small'>{$renglon[2]}</td> 
                                    <td class='small'>{$renglon[3]}</td>
                                    <td class='small'>{$renglon[4]}</td> 
                                    <td class='small'>
                                        <button onclick='javasript:view_productos(\"detalles\",\"$renglon[0]\")' class='btn btn-info'>Detalles</button>
                                        <button onclick='javasript:view_productos(\"modificar\",\"$renglon[0]\")' class='btn btn-warning'>Modificar</button>
                                        <button onclick='javasript:view_productos(\"eliminar\")' class='btn btn-danger'>Eliminar</button>
                                    </td>
                                </tr>";
                        }
                    }
                    fclose($archivo);

'agregar':
                    $ruta = "provedor.txt";
                    $archivo = fopen($ruta,"r");
                    $codigo.="<option value=''>Por Asignar</option>";
                    while (!feof($archivo)) {
                        $linea = fgets($archivo);
                        if (!empty($linea)) {
                            $renglon = explode("-@-", $linea); 
                            $codigo.="<option value='".$renglon[0]."'>".$renglon[1]."</option>";
                        }
                    }  
                    fclose($archivo);
