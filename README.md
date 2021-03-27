from sympy import*
from sympy.plotting import*
#Funções
x = Function(input('Variável: '))
f = Function('f')
#Simbolos genéricos
P, Q, W, M = symbols('P Q W M')
#Simbolos de entes fisicos
t, g, m, a = symbols('t g m a',real=True, positive=True)
#Simbolos de entes fisicos para osciladores mecânicos
omega, omega1, beta, gamma, Fo, k = symbols('omega omega1 beta gamma Fo k', real = True, positive=True)
#Simbolos de entes fisicos para osciladores elétricos
R, L, C, epsilon = symbols('R L C epsilon')
print(t,omega, beta, m, omega1, Fo)
#Derivadas
def x1(t):
    return x(t).diff(t)
def x2(t):
    return x1(t).diff(t)
#Diferential Equation
#P*x2(t)+Q*x1(t)+R*x(t)=M
print('Equação Geral de Movimento com Coeficientes Constantes')
pprint(Eq(P*x2(t)+Q*x1(t)+W*x(t),M))
print('Defina os parâmetros P, Q, W e M')
P = eval(input('P= '))
Q = eval(input('Q= '))
W = eval(input('W= '))
M = eval(input('M= '))
#Solução Geral
pprint(Eq(P*x2(t)+Q*x1(t)+W*x(t),M))
solve = dsolve(Eq(P*x2(t)+Q*x1(t)+W*x(t),M))
pprint(solve)
#Condições iniciais
if P==0:
    ics={x(0):eval(input('x(0)= '))}
else:
    ics={x(0):eval(input('x(0)= ')),x1(t).subs(t,0):eval(input('x1(0)= '))}
#Solução particular
solvepart = dsolve(Eq(P*x2(t)+Q*x1(t)+W*x(t),M),ics=ics)
pprint(solvepart)
#Graficos
#Definição de valores numéricos para os parâmetros gerais
print('Defina valores numéricos para os parâmetros')
Q = eval(input('Q= '))
W = eval(input('W= '))
M = eval(input('M= '))
solvepart2 = dsolve(Eq(P*x2(t)+Q*x1(t)+W*x(t),M),ics=ics)
print(solvepart2.args[1])
plot(solvepart2.args[1], legend=True, autoescale=True)
