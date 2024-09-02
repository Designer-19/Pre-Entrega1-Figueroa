# Pre-Entrega1// 
//Simulador Boliche
const precioEntrada = 9000;

// Precios Bebidas
const cerveza = 7000;
const agua = 3500;
const caipifrutosRojos = 8500; 
const fernetCoca = 8500;       
const vodkaConSpeed = 6790;     
const botellaFernet = 90000;   

// Función para calcular el total de las entradas
function totalEntrada(cantidad) {
    return cantidad * precioEntrada;
}

// Función para calcular el total de una bebida
function calcularTotalBebida(precio, cantidad) {
    return precio * cantidad;
}

// Función para seleccionar una bebida y calcular el total
function seleccionarBebida() {
    const mensajeEligeBebida = `
Elige una bebida:
1. Cerveza
2. Agua
3. Caipi Frutos Rojos
4. Fernet con Coca
5. Vodka con Speed
6. Botella de Fernet
`;
    const opcionBebida = parseInt(prompt(mensajeEligeBebida));

    let precioSeleccionado;
    let nombreBebida;

    switch(opcionBebida) {
        case 1:
            precioSeleccionado = cerveza;
            nombreBebida = "Cerveza";
            break;
        case 2:
            precioSeleccionado = agua;
            nombreBebida = "Agua";
            break;
        case 3:
            precioSeleccionado = caipifrutosRojos;
            nombreBebida = "Caipi Frutos Rojos";
            break;
        case 4:
            precioSeleccionado = fernetCoca;
            nombreBebida = "Fernet con Coca";
            break;
        case 5:
            precioSeleccionado = vodkaConSpeed;
            nombreBebida = "Vodka con Speed";
            break;
        case 6:
            precioSeleccionado = botellaFernet;
            nombreBebida = "Botella de Fernet";
            break;
        default:
            console.log("Opción no válida.");
            return 0;  // Devolver 0 si la opción no es válida
    }

    let cantidadBebidas;
    do {
        cantidadBebidas = parseInt(prompt(`¿Cuántas unidades de ${nombreBebida} quieres? (debe ser un número positivo)`));
    } while (isNaN(cantidadBebidas) || cantidadBebidas <= 0);

    const totalBebidas = calcularTotalBebida(precioSeleccionado, cantidadBebidas);
    console.log(`Precio por unidad de ${nombreBebida}: $${precioSeleccionado}`);
    console.log(`Total a pagar por ${cantidadBebidas} ${nombreBebida}: $${totalBebidas}`);
    
    return totalBebidas;  // Devolver el total de las bebidas seleccionadas
}

// Solicitar la cantidad de entradas con validación
let cantidadEntradas;
do {
    cantidadEntradas = parseInt(prompt("Ingrese la cantidad de entradas (debe ser un número positivo):"));
} while (isNaN(cantidadEntradas) || cantidadEntradas <= 0);

const totalEntradas = totalEntrada(cantidadEntradas);
console.log(`Total a pagar por las entradas: $${totalEntradas}`);

// Inicializar el total de bebidas
let totalBebidasFinal = 0;

// Permitir la selección de bebidas en un ciclo
let continuar;
do {
    totalBebidasFinal += seleccionarBebida();  // Sumar el total de la bebida seleccionada
    continuar = prompt("¿Quieres seleccionar otra bebida? (sí/no)").toLowerCase();
} while (continuar === "sí" || continuar === "si");

console.log("Gracias por tu compra!");

if (totalEntradas + totalBebidasFinal > 100000) {
    console.log("Por gastar más de 100,000, te ofrecemos un descuento del 10%.");
    const descuento = (totalEntradas + totalBebidasFinal) * 0.10;
    console.log(`Descuento aplicado: $${descuento}`);
    totalFinal -= descuento;  // Aplicar el descuento al total final
}

// Función para calcular el total final
function calcularTotalFinal(totalEntradas, totalBebidas) {
    return totalEntradas + totalBebidas;
}

// Calcular y mostrar el total final
const totalFinal = calcularTotalFinal(totalEntradas, totalBebidasFinal);
console.log(`El total a pagar por entradas y bebidas es: $${totalFinal}`);
