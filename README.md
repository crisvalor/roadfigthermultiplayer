# roadfigthermultiplayer
import tkinter as t
import random as r
ventana = t.Tk()
ventana.geometry("600x400+500+200")
ventana.title("menu")
#Imagen del juego
imagenP = t.PhotoImage(file = "portada.png")
Imagen = t.Label(ventana, image = imagenP).place(x = 0, y = 0)
#Carros del juego
carrop = t.PhotoImage(file="carro.png")
carros = t.PhotoImage(file="carros.png")
choque = t.PhotoImage(file="explosion.png")
icarro1 = t.PhotoImage(file="carro2.png")
icarro2 = t.PhotoImage(file="carro3.png")
icarro3 = t.PhotoImage(file="carro4.png")
perder1 = t.PhotoImage(file="perder1.png")
perder2 = t.PhotoImage(file="perder2.png")
p1 = t.PhotoImage(file = "pista.png")
p2 = t.PhotoImage(file = "pista2.png")
p3 = t.PhotoImage(file = "pista3.png")
p4 = t.PhotoImage(file = "pista4.png")
p5 = t.PhotoImage(file = "pista5.png")
pun = t.PhotoImage(file= "negro.png")
p = None
U1 = t.Label(text = "Player1:",font = ("Arial",10),background = "red").place(x = 190, y = 110)
eU1 = t.StringVar()
tU1 = t.Entry(ventana,textvariable = eU1).place(x = 260,y = 110)
U2 = t.Label(text = "Player2:",font = ("Arial",10),background = "blue").place(x = 190, y = 150)
eU2 = t.StringVar()
tU2 = t.Entry(ventana,textvariable = eU2).place(x = 260,y = 150)
i = 0
n = 0
j = 0
o = 0
k = 0
b = 0
u = 0
m = 0
g = 0
s = False
e = False
q = False
j2 = 0
o2 = 0
k2 = 0
b2 = 0
u2 = 0
m2 = 0
s2 = False
e2 = False
q2 = False
v1 = 3
v2 = 3
x1 = 250+i
y1 = 500
x2 = 950+n
y2 = 500
x3 = r.randint(170,330)
y3 = -40
x4 = r.randint(170,330)
y4 = -40
x5 = r.randint(170,330)
y5 = -40
x32 = r.randint(870,1030)
y32 = -40
x42 = r.randint(870,1030)
y42 = -40
x52 = r.randint(870,1030)
y52 = -40
def key(event):
    """
    """
    global x,i,x1,y1,n,l,v1,v2
    tecla = repr(event.char)
    if(tecla == "'d'"):
        if(i < 80):
            d.delete(x)
            i = i + 10
            x = d.create_image(x1+i,y1,image=carrop)
        else:
            d.delete(x)
            x = d.create_image(x1+i,y1,image=choque)
            v1 = v1 - 1
    if(tecla == "'a'"):
        if(i > -80 ):
            d.delete(x)
            i = i - 10
            x = d.create_image(x1+i,y1,image=carrop)
        else:
            d.delete(x)
            x = d.create_image(x1+i,y1,image=choque)
            v1 = v1 - 1
    if(tecla == "'l'"):
        if(n < 80):
            d.delete(l)
            n = n + 10
            l = d.create_image(x2+n,y2,image=carros)
        else:
            d.delete(l)
            l = d.create_image(x2+n,y2,image=choque)
            v2 = v2 - 1
    if(tecla == "'j'"):
        if(n > -80):
            d.delete(l)
            n = n - 10
            l = d.create_image(x2+n,y2,image=carros)
        else:
            d.delete(l)
            l = d.create_image(x2+n,y2,image=choque)
            v2 = v2 - 1
        
def mcarro1():
    global v,d,y,j,x1,y1,x3,y3,i,x,s,g,v1
    s = True
    if(j<700):
        d.delete(y)
        y = d.create_image(x3,y3,image=icarro1)
        d.move(y,0,1)
        j = j + 1
        y3 = y3 + 1
        dx = abs(x1+i - x3)
        dy = abs(y1 - y3)
        dcx = 29
        dcy = 49
        if(dx <= dcx and dy <= dcy):
            d.delete(x)
            d.delete(y)
            x = d.create_image(x1+i,y1,image=choque)
            print("choqe")
            y3 = y3 + 1000
            d.delete(y)
            v1 = v1 - 1
        else:
            v.after(g,mcarro1)
    if(j == 700):
        j = 0
        x3 = r.randint(170,330)
        y3 = -40
        s = False
        ecarro()
def mcarro2():
    global v,d,z,o,x1,y1,x4,y4,i,x,e,g,v1
    e = True
    if(o<700):
        d.delete(z)
        z = d.create_image(x4,y4,image=icarro2)
        d.move(z,0,1)
        o = o + 1
        y4 = y4 + 1
        if(o == 400):
            if(x4+45 > 330):
                d.delete(z)
                z = d.create_image(x4-30,y4,image=icarro2)
                x4 = x4 - 30
                v.after(0,mcarro2)
                return x4
            if(x4-45 < 170):
                d.delete(z)
                z = d.create_image(x4+30,y4,image=icarro2)
                x4 = x4 + 30
                v.after(0,mcarro2)
                return x4
            else:
                s = r.randint(0,1)
                if(s == 0):
                    d.delete(z)
                    z = d.create_image(x4+30,y4,image=icarro2)
                    x4 = x4 + 30
                    v.after(0,mcarro2)
                    return x4
                if(s == 1):
                    d.delete(z)
                    z = d.create_image(x4-30,y4,image=icarro2)
                    x4 = x4 - 30
                    v.after(0,mcarro2)
                    return x4
        dx  = abs(x1+i - x4)
        dy  = abs(y1 - y4)
        dcx = 29
        dcy = 49
        if(dx <= dcx and dy <= dcy):
            d.delete(x)
            d.delete(z)
            x = d.create_image(x1+i,y1,image=choque)
            print("choqe")
            y4 = y4 + 1000
            d.delete(z)
            v1 = v1 - 1
        else:
            v.after(g,mcarro2)
    if(o == 700):
        o = 0
        x4 = r.randint(170,330)
        y4 = -40
        e = False
        ecarro()
def mcarro3():
    global v,d,a,k,x1,y1,x5,y5,i,x,q,g,v1
    q = True
    if(k<700):
        d.delete(a)
        a = d.create_image(x5,y5,image=icarro3)
        d.move(a,0,1)
        k = k + 1
        y5 = y5 + 1
        if(k == 400):
            if(x5 > x1+i and x5-45 > 170):
                d.delete(a)
                a = d.create_image(x5-30,y5,image=icarro3)
                x5 = x5 - 30
                v.after(0,mcarro3)
                return x5
            if(x5 < x1+i and x5+45 < 330):
                d.delete(a)
                a = d.create_image(x5+30,y5,image=icarro3)
                x5 = x5 + 30
                v.after(0,mcarro3)
                return x5
        dx = abs(x1+i - x5)
        dy = abs(y1 - y5)
        dcx = 29
        dcy = 49
        if(dx <= dcx and dy <= dcy):
            d.delete(x)
            d.delete(a)
            x = d.create_image(x1+i,y1,image=choque)
            print("choqe")
            y5 = y5 + 1000
            d.delete(a)
            v1 = v1 - 1
        else:
            v.after(g,mcarro3)
    if(k == 700):
        k = 0
        x5 = r.randint(170,330)
        y5 = -40
        q = False 
        ecarro()
def carro1():
    global d,y,t,v,x,b
    y = d.create_image(x3,y3,image=icarro1)
    b = 1
    mcarro1()
    
def carro2():
    global d,z,t,v,x,u
    z = d.create_image(x4,y4,image=icarro2)
    u = 1
    mcarro2()
def carro3():
    global d,a,t,v,x,m
    a = d.create_image(x5,y5,image=icarro3)
    m = 1
    mcarro3()
    
def mcarro12():
    global v,d,y9,j2,x2,y2,x32,y32,n,l,s2,g,v2
    s2 = True
    if(j2<700):
        d.delete(y9)
        y9 = d.create_image(x32,y32,image=icarro1)
        d.move(y9,0,1)
        j2 = j2 + 1
        y32 = y32 + 1
        dx2 = abs(x2+n - x32)
        dy2 = abs(y2 - y32)
        dcx2 = 29
        dcy2 = 49
        if(dx2 <= dcx2 and dy2 <= dcy2):
            d.delete(l)
            d.delete(y9)
            l = d.create_image(x2+n,y2,image=choque)
            print("choqe")
            y32 = y32 + 1000
            d.delete(y9)
            v2 = v2 - 1
        else:
            v.after(g,mcarro12)
    if(j2 == 700):
        j2 = 0
        x32 = r.randint(870,1030)
        y32 = -40
        s2 = False
        ecarro2()
def mcarro22():
    global v,d,z2,o2,x2,y2,x42,y42,n,l,e2,g,v2
    e2 = True
    if(o2<700):
        d.delete(z2)
        z2 = d.create_image(x42,y42,image=icarro2)
        d.move(z2,0,1)
        o2 = o2 + 1
        y42 = y42 + 1
        if(o2 == 400):
            if(x42+45 > 1030):
                d.delete(z2)
                z2 = d.create_image(x42-30,y42,image=icarro2)
                x42 = x42 - 30
                v.after(0,mcarro22)
                return x42
            if(x42-45 < 870):
                d.delete(z2)
                z2 = d.create_image(x42+30,y42,image=icarro2)
                x42 = x42 + 30
                v.after(0,mcarro22)
                return x42
            else:
                f = r.randint(0,1)
                if(f == 0):
                    d.delete(z2)
                    z2 = d.create_image(x42+30,y42,image=icarro2)
                    x42 = x42 + 30
                    v.after(0,mcarro22)
                    return x42
                if(f == 1):
                    d.delete(z2)
                    z2 = d.create_image(x42-30,y42,image=icarro2)
                    x42 = x42 - 30
                    v.after(0,mcarro22)
                    return x42
        dx2  = abs(x2+n - x42)
        dy2  = abs(y2 - y42)
        dcx2 = 29
        dcy2 = 49
        if(dx2 <= dcx2 and dy2 <= dcy2):
            d.delete(l)
            d.delete(z2)
            l = d.create_image(x2+n,y2,image=choque)
            print("choqe")
            y42 = y42 + 1000
            d.delete(z2)
            v2 = v2 - 1
        else:
            v.after(g,mcarro22)
    if(o2 == 700):
        o2 = 0
        x42 = r.randint(870,1030)
        y42 = -40
        e2 = False
        ecarro2()
def mcarro32():
    global v,d,a2,k2,x2,y2,x52,y52,n,l,q2,g,v2
    q2 = True
    if(k2<700):
        d.delete(a2)
        a2 = d.create_image(x52,y52,image=icarro3)
        d.move(a2,0,1)
        k2 = k2 + 1
        y52 = y52 + 1
        if(k2 == 400):
            if(x52 > x2+n and x52-45 > 870):
                d.delete(a2)
                a2 = d.create_image(x52-30,y52,image=icarro3)
                x52 = x52 - 30
                v.after(0,mcarro32)
                return x52
            if(x52 < x2+n and x52+45 < 1030):
                d.delete(a2)
                a2 = d.create_image(x52+30,y52,image=icarro3)
                x52 = x52 + 30
                v.after(0,mcarro32)
                return x52
        dx2 = abs(x2+n - x52)
        dy2 = abs(y2 - y52)
        dcx2 = 29
        dcy2 = 49
        if(dx2 <= dcx2 and dy2 <= dcy2):
            d.delete(l)
            d.delete(a2)
            l = d.create_image(x2+n,y2,image=choque)
            print("choqe")
            y52 = y52 + 1000
            d.delete(a2)
            v2 = v2 - 1
        else:
            v.after(g,mcarro32)
    if(k2 == 700):
        k2 = 0
        x52 = r.randint(870,1030)
        y52 = -40
        q2 = False 
        ecarro2()
def carro12():
    global d,y9,t,v,l,b2
    y9 = d.create_image(x32,y32,image=icarro1)
    b2 = 1
    mcarro12()
    
def carro22():
    global d,z2,t,v,l,u2
    z2 = d.create_image(x42,y42,image=icarro2)
    u2 = 1
    mcarro22()
def carro32():
    global d,a2,t,v,l,m2
    a2 = d.create_image(x52,y52,image=icarro3)
    m2 = 1
    mcarro32()


def pistaP():
    global v,d,pista,p1,x,y,z,a,b,m,u,v1,c1,c2,c3,s,e,q,g,p
    if (d.coords(pista)[1] <= 600):
        d.move(pista,0,1) 
        v.after(g,pistaP)
        if(v1 == 2):
            d.delete(c1)
        if(v1 == 1):
            d.delete(c2)
        if(v1 == 0):
            d.delete(c3)
            d.delete(x)
            d.delete(pista)
            s == True
            e = True
            q = True
            h = d.create_image(250,300,image=perder1)
            
    if (d.coords(pista)[1] > 600):
        d.delete(x)
        d.delete(pista)
        pista = d.create_image(250,0,image=p)
        x = d.create_image(x1+i,y1,image=carrop)
def pistaS():
    global v,d,pista2,p1,l,y,v2,c12,c22,c32,s2,e2,q2,g,p  
    if (d.coords(pista2)[1] <= 600):
        d.move(pista2,0,1) 
        v.after(g,pistaS)
        if(v2 == 2):
            d.delete(c12)
        if(v2 == 1):
            d.delete(c22)
        if(v2 == 0):
            d.delete(c32)
            d.delete(l)
            d.delete(pista2)
            s2 == True
            e2 = True
            q2 = True
            h2 = d.create_image(950,300,image=perder2)
    if (d.coords(pista2)[1] > 600):
        d.delete(l)
        d.delete(pista2)
        pista2 = d.create_image(950,0,image=p)
        l = d.create_image(x2+n,y2,image=carros)

def vidas():
    global d,v,t,c1,c2,c3,c12,c22,c32
    vidas1 = t.Label(v,text = "Vidas= ",fg= "white",background = "black").place(x = 530, y = 200)
    vidas2 = t.Label(v,text = "Vidas= ",fg = "white",background = "black").place(x = 530, y = 400)
    c1 = d.create_image(560,260,image=carrop)
    c2 = d.create_image(600,260,image=carrop)
    c3 = d.create_image(640,260,image=carrop)
    c12 = d.create_image(560,460,image=carros)
    c22 = d.create_image(600,460,image=carros)
    c32 = d.create_image(640,460,image=carros)

        
def ecarro():
    global d,v,t,s,e,q,v1,c1,c2,c3
    w = r.choice([1,2,3])
    if(w == 1):
        if(s == False): 
            carro1()
    if(w == 2):
        if(e == False):
            carro2()
    if(w == 3):
        if(q == False):
            carro3()
 
def ecarro2():
    global d,v,t,s2,e2,q2,v2,c12,c22,c32
    w = r.choice([1,2,3])
    if(w == 1):
        if(s2 == False): 
            carro12()
    if(w == 2):
        if(e2 == False):
            carro22()
    if(w == 3):
        if(q2 == False):
            carro32()

    
def nivel1():
    global d,x,v,pista,p1,pista2,y,z,a,l,g,p
    v = t.Toplevel()
    v.geometry("1200x600")
    ventana.iconify()
    d = t.Canvas(v, width=1200, height=600)
    pista = d.create_image(250,0,image=p1)
    pista2 = d.create_image(950,0,image=p1)
    p = p1
    info = d.create_image(600,300,image=pun)
    nombre1 = t.Label(v,text = "Player1= " + eU1.get(),fg = "white",background = "black").place(x = 530, y = 150)
    nombre2 = t.Label(v,text = "Player2= " + eU2.get(),fg = "white",background = "black").place(x = 530, y = 350)
    vidas()
    d.bind("<Key>", key)
    d.focus_set()
    d.pack()
    g = 10
    ecarro()
    ecarro2()
    x = d.create_image(x1+i,y1,image=carrop)
    l = d.create_image(x2+n,y2,image=carros)
    pistaP()
    pistaS()
    v.mainloop()

def nivel2():
    global d,x,v,pista,p1,pista2,y,z,a,l,g,p
    v = t.Toplevel()
    v.geometry("1200x600")
    ventana.iconify()
    d = t.Canvas(v, width=1200, height=600)
    pista = d.create_image(250,0,image=p2)
    pista2 = d.create_image(950,0,image=p2)
    p = p2
    info = d.create_image(600,300,image=pun)
    nombre1 = t.Label(v,text = "Usuario1= " + eU1.get(),fg = "white",background = "black").place(x = 530, y = 150)
    nombre2 = t.Label(v,text = "Usuario2= " + eU2.get(),fg = "white",background = "black").place(x = 530, y = 350)
    vidas()
    d.bind("<Key>", key)
    d.focus_set()
    d.pack()
    g = 8
    ecarro()
    ecarro2()
    x = d.create_image(x1+i,y1,image=carrop)
    l = d.create_image(x2+n,y2,image=carros)
    pistaP()
    pistaS()
    v.mainloop()

def nivel3():
    global d,x,v,pista,p1,pista2,y,z,a,l,g,p
    v = t.Toplevel()
    v.geometry("1200x600")
    ventana.iconify()
    d = t.Canvas(v, width=1200, height=600)
    pista = d.create_image(250,0,image=p3)
    pista2 = d.create_image(950,0,image=p3)
    p = p3
    info = d.create_image(600,300,image=pun)
    nombre1 = t.Label(v,text = "Usuario1= " + eU1.get(),fg = "white",background = "black").place(x = 530, y = 150)
    nombre2 = t.Label(v,text = "Usuario2= " + eU2.get(),fg = "white",background = "black").place(x = 530, y = 350)
    vidas()
    d.bind("<Key>", key)
    d.focus_set()
    d.pack()
    g = 6
    ecarro()
    ecarro2()
    x = d.create_image(x1+i,y1,image=carrop)
    l = d.create_image(x2+n,y2,image=carros)
    pistaP()
    pistaS()
    v.mainloop()
    
def nivel4():
    global d,x,v,pista,p1,pista2,y,z,a,l,g,p
    v = t.Toplevel()
    v.geometry("1200x600")
    ventana.iconify()
    d = t.Canvas(v, width=1200, height=600)
    pista = d.create_image(250,0,image=p4)
    pista2 = d.create_image(950,0,image=p4)
    p = p4
    info = d.create_image(600,300,image=pun)
    nombre1 = t.Label(v,text = "Usuario1= " + eU1.get(),fg = "white",background = "black").place(x = 530, y = 150)
    nombre2 = t.Label(v,text = "Usuario2= " + eU2.get(),fg = "white",background = "black").place(x = 530, y = 350)
    vidas()
    d.bind("<Key>", key)
    d.focus_set()
    d.pack()
    g = 4
    ecarro()
    ecarro2()
    x = d.create_image(x1+i,y1,image=carrop)
    l = d.create_image(x2+n,y2,image=carros)
    pistaP()
    pistaS()
    v.mainloop()

def nivel5():
    global d,x,v,pista,p1,pista2,y,z,a,l,g,p
    v = t.Toplevel()
    v.geometry("1200x600")
    ventana.iconify()
    d = t.Canvas(v, width=1200, height=600)
    pista = d.create_image(250,0,image=p5)
    pista2 = d.create_image(950,0,image=p5)
    p = p5
    info = d.create_image(600,300,image=pun)
    nombre1 = t.Label(v,text = "Usuario1= " + eU1.get(),fg = "white",background = "black").place(x = 530, y = 150)
    nombre2 = t.Label(v,text = "Usuario2= " + eU2.get(),fg = "white",background = "black").place(x = 530, y = 350)
    vidas()
    d.bind("<Key>", key)
    d.focus_set()
    d.pack()
    g = 2
    ecarro()
    ecarro2()
    x = d.create_image(x1+i,y1,image=carrop)
    l = d.create_image(x2+n,y2,image=carros)
    pistaP()
    pistaS()
    v.mainloop()
#Crear los botones
dbtnStark1 = t.Button(ventana,text = "Lvl 1",command = nivel1,
                    font = ("Arial",10),background = "green").place(x = 70, y = 250)
btnStark2 = t.Button(ventana,text = "Lvl 2",command = nivel2,
                    font = ("Arial",10),background = "green").place(x = 170, y = 250)
btnStark3 = t.Button(ventana,text = "Lvl 3",command = nivel3,
                    font = ("Arial",10),background = "green").place(x = 270, y = 250)
btnStark4 = t.Button(ventana,text = "Lvl 4",command = nivel4,
                    font = ("Arial",10),background = "green").place(x = 370, y = 250)
btnStark5 = t.Button(ventana,text = "Lvl 5",command = nivel5,
                    font = ("Arial",10),background = "green").place(x = 470, y = 250)
ventana.mainloop()
 
