% Definimos un predicado para calcular el IMC
imc(Peso, Altura, IMC) :-
    Altura > 0, % Aseguramos que la altura no sea cero
    IMC is Peso / (Altura * Altura).

% Definimos un predicado para clasificar el IMC
clasificar_imc(IMC, Categoria) :-
    IMC < 18.5 -> Categoria = 'Bajo peso';
    IMC >= 18.5, IMC < 24.9 -> Categoria = 'Peso normal';
    IMC >= 25, IMC < 29.9 -> Categoria = 'Sobrepeso';
    Categoria = 'Obesidad'.

% Predicado principal que calcula y clasifica el IMC
calcular_imc(Peso, Altura, IMC, Categoria) :-
    imc(Peso, Altura, IMC),
    clasificar_imc(IMC, Categoria).

% Función para determinar el rango de peso ideal según la altura
peso_ideal(Altura, PesoMinimo, PesoMaximo) :-
    IMCObjetivo is 22, % Usamos 22 como el IMC objetivo para peso normal
    PesoMinimo is IMCObjetivo * (Altura * Altura),
    PesoMaximo is (IMCObjetivo + 2) * (Altura * Altura). % Rango más amplio

% Función para recomendaciones de estilo de vida
recomendaciones(Categoria, Recomendacion) :-
    Categoria = 'Bajo peso' -> Recomendacion = 'Aumentar la ingesta calórica y consultar a un médico.';
    Categoria = 'Peso normal' -> Recomendacion = 'Mantener una dieta equilibrada y ejercicio regular.';
    Categoria = 'Sobrepeso' -> Recomendacion = 'Considerar una dieta saludable y aumentar la actividad física.';
    Categoria = 'Obesidad' -> Recomendacion = 'Consultar a un profesional de la salud para un plan de pérdida de peso adecuado.'.

% Función para calcular el peso ideal en base a un IMC objetivo
peso_para_imc_objetivo(Altura, IMCObjetivo, PesoIdeal) :-
    PesoIdeal is IMCObjetivo * (Altura * Altura).
