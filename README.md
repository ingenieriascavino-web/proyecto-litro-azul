const duchasInput = document.getElementById('duchas');
const minutosInput = document.getElementById('minutos');
const lavadoInput = document.getElementById('lavado');
const personasInput = document.getElementById('personas');
const resultado = document.getElementById('resultado');
const mensaje = document.getElementById('mensaje');
const calcularBtn = document.getElementById('calcular');

function calcularConsumo() {
  const duchas = Number(duchasInput.value) || 0;
  const minutos = Number(minutosInput.value) || 0;
  const lavado = Number(lavadoInput.value) || 0;
  const personas = Number(personasInput.value) || 1;

  const consumoDucha = duchas * minutos * 9;
  const consumoLavado = lavado * 45;
  const consumoTotal = (consumoDucha + consumoLavado) * personas;

  resultado.textContent = `${Math.round(consumoTotal).toLocaleString()} L`;

  if (consumoTotal < 150) {
    mensaje.textContent = '¡Excelente! Estás consumiendo muy poco agua para tu hogar.';
  } else if (consumoTotal < 300) {
    mensaje.textContent = 'Tu consumo está dentro del rango promedio. Puedes mejorar con pequeños ajustes.';
  } else {
    mensaje.textContent = 'Tu consumo es alto. Considera reducir tiempos y repetir menos ciclos de lavado.';
  }
}

calcularBtn.addEventListener('click', calcularConsumo);

document.addEventListener('DOMContentLoaded', calcularConsumo);
