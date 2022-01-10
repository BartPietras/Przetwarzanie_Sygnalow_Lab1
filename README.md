# Kod (Mathematica)

wyznaczanie alfy:
c = 0.001
R = 1969
\[Alpha] = 1/(c R)

obliczenie t:
Solve[0.05 == Exp[-\[Alpha]*t], t]

badanie zależności i stworzenie wykresów:
\[Omega] = 1;
s = {}; sd = {};
Do[
  \[Omega] = 0.1  i;
  T = 2 \[Pi] / \[Omega] ;
  tmax = 10 T;
  eq = q'[t] + \[Alpha] q[t] == Sin[\[Omega] t];
  wp = q[0] = 0;
  sol = NDSolve[{eq, wp}, q, {t, 0, Tmax}];
  f[t_] := (-\[Omega] Cos[\[Omega]t] + \[Alpha] Sin[\[Omega]t])/(\
\[Alpha] ^2 +  \[Omega]^2);
  f'[t];
  tt1 = FindMaxValue[f[t], t];
  tt2 = FindMaxValue[f'[t], t];
  AppendTo[s, tt1];
  AppendTo[sd, tt2];
  , {i, 1, 100}];

ListPlot[{s, sd}]

LogPlot[q[\[Omega]], {\[Omega], 0, 10}]