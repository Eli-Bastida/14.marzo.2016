ELISA BASTIDA
PAZ ALEXIA DIAZ
MARIA FERNANDA FLORES
MARIA FERNANDA GONZALEZ

# 14.marzo.2016
series de tiempo múltiple (trabajo en clase y ejercicio)

### series de tiempo multiple ###

indi3 <- ts(read.csv(("C:\\Users\\SALA-C9\\Desktop\\IndicadoresENOE_2016-03-14 (1).csv"), header = TRUE), frequency = 4, start = 2015)
## headre true porque la tabla de excel si tiene encabezados
class(indi3)
## para separar la tabal en comumnas, los corchetes indican que parte de la matriz, [fila, columna]
desoparcial<- ts(indi3[,1], start = 2005, frequency = 4)
asala<- ts(indi3[,2], start = 2005, frequency = 4)
til1<- ts(indi3[,3], start = 2005, frequency = 4)

## serie de tiempo multiple, ya que declare las variable como series de tiempo ya puedo
## ocupar la funcuion ts.intersect y llamar las 3 series
seriemultiple <- ts.intersect(desoparcial, asala, til1)
## grafica
plot(seriemultiple, main= "Series de Tiempo Múltiple", xlab= "Años", ylab = "Número de personas", col = "blue")
seriemultiple
## si una de las series de tiempo empieza en otro año toda la amtriz se corta al año mas reciente

#### separar la serie de tiempo dependiendo del analisis
seriemultiple05.09 <- window(seriemultiple, start= c(2005,1), end = c(2009,4)) ## star=c(año, trimestre) e lo mismo para end
seriemultiple10.15 <- window(seriemultiple, start = c(2010, 1), end= c(2015,4))

plot(seriemultiple05.09, main ="Series de Tiempo Multiple", xlab = "Años", ylab = "No. de personas", col = "red")
plot(seriemultiple10.15, main ="Series de Tiempo Multiple", xlab = "Años", ylab = "No. de personas", col = "gray")
start(seriemultiple); end(seriemultiple) ## para conocer donde inicia y donde termina la serie de tiempo mltiple

### ejercicio
##a) importar la base
## b) declararla serie de tiempo
## graficar las variables por separado
## c) graficar juntas como serie de tiempo
## d) crear serie de tiempo muultiple

## a)
ocuem <- ts(read.csv(("C:\\Users\\SALA-C9\\Desktop\\ocupacion y empleo, ejercicio.csv"), header = TRUE), frequency = 4, start = 2005)
View (ocuem)
spfc<- ts(ocuem[,1], start = 2005, frequency = 4)
masde5<- ts(ocuem[,2], start = 2005, frequency = 4)
menosde15<- ts(ocuem[,3], start = 2005, frequency = 4)
conpres<- ts(ocuem[,4], start = 2005, frequency = 4)

plot(spfc, main = "Servicios profesionales, financieros y corporativos", xlab= "años", ylab = "#personas")
plot(masde5, main = "Más de 5 salarios mínimos", xlab= "años", ylab = "#personas")
plot (menosde15, main = "Menos de 15 horas", xlab= "años", ylab = "#personas")
plot(conpres, main = "Con prestaciones", xlab= "años", ylab = "#personas")

seriemultiple <- ts.intersect(spfc, masde5, menosde15, conpres)
plot(seriemultiple, main = "Ocupación y Empleo", xlab= "años", ylab = "#personas")

seriemultiple2005.2009 <- window(seriemultiple, start = c(2005), end= c(2009))
plot(seriemultiple2005.2009, main = "Ocupación y Empleo", xlab= "años", ylab = "#personas")
