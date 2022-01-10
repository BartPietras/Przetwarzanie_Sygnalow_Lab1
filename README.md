# Kod (Mathematica)

## wyznaczanie alfy:
c = 0.001<br>
R = 1969<br>
\[Alpha] = 1/(c R)

## obliczenie t:
Solve[0.05 == Exp[-\[Alpha]*t], t]

## badanie zależności i stworzenie wykresów:
\[Omega] = 1;<br>
s = {}; sd = {};<br>
Do[<br>
  \[Omega] = 0.1  i;<br>
  T = 2 \[Pi] / \[Omega] ;<br>
  tmax = 10 T;<br>
  eq = q'[t] + \[Alpha] q[t] == Sin[\[Omega] t];<br>
  wp = q[0] = 0;<br>
  sol = NDSolve[{eq, wp}, q, {t, 0, Tmax}];<br>
  f[t_] := (-\[Omega] Cos[\[Omega]t] + \[Alpha] Sin[\[Omega]t])/(\
\[Alpha] ^2 +  \[Omega]^2);<br>
  f'[t];<br>
  tt1 = FindMaxValue[f[t], t];<br>
  tt2 = FindMaxValue[f'[t], t];<br>
  AppendTo[s, tt1];<br>
  AppendTo[sd, tt2];<br>
  , {i, 1, 100}];<br>

ListPlot[{s, sd}]<br>

LogPlot[q[\[Omega]], {\[Omega], 0, 10}]