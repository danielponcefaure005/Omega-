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
