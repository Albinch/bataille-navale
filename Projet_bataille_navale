import numpy as np
import random
from tkinter import *
TAILLEX=1360
TAILLEY=660

nbClic=0

nombre_touche_joueur=0
nombre_touche_IA=0



def creation(nbCases): #Cette fonction premet de créer le tableau de base rempli de zéros

    tabl=np.full((nbCases,nbCases), 0)

    return tabl


def tab_touche_joueur(nbCases2): #Cette fonction permet de créer le tableau où l'utilisateur va poser les bombes

    tabl2=np.full((nbCases2,nbCases2),0)

    return tabl2


def position_aleatoire(tab): #Cette fonction sert à placer les bateaux aléatoirement sur le terrain

    definir_taille_bateau=1 #Variable qui sert à "choisir" quel bateau on va placer aléatoirement, on l'incrémente à la fin de la fonction
    numBateau=1
    tailleBateau=0

    for i in range(0,5):

        if definir_taille_bateau==1:

            tailleBateau=2

        elif definir_taille_bateau==2:

            tailleBateau=3

        elif definir_taille_bateau==3:

            tailleBateau=3

        elif definir_taille_bateau==4:

            tailleBateau=4

        elif definir_taille_bateau==5:

            tailleBateau=5

        else:

            print("Erreur, votre bateau est coulé d'office")
            tailleBateau=0

        x=random.randint(0,10-tailleBateau) #10-tailleBateau: pour empêcher les bateaux de sortir du terrain
        y=random.randint(0,10-tailleBateau)
        orientation=random.randint(1,2)


        superpose_alea=superposition(tab,x,y,orientation,tailleBateau) #superpose2 est la variable retournée par la fonction superposition

        while superpose_alea==True: #Tant que la position n'est pas libre, on ne place pas le bateau

            x=random.randint(0,10-tailleBateau) #10-tailleBateau: pour empêcher les bateaux de sortir du terrain
            y=random.randint(0,10-tailleBateau)
            superpose_alea=superposition(tab,x,y,orientation,tailleBateau) #on ré-appelle la fonction pour revérifier si la case est libre


        for j in range(0,tailleBateau): #Boucle qui permet de placer les chiffres à la suite pour ne pas que le bateau soit éparpillé sur tout le terrain

            tab[x][y]=numBateau

            if orientation==1 and x!=9: #Si x=9, on ne fait pas "x+1" pour ne pas déborder du terrain

                x=x+1  #Si orientation=1, le bateau sera vertical

            elif orientation==2 and y!=9: #Si y=9, on ne fait pas "y+1" pour ne pas déborder du terrain

                y=y+1  #Si orientation=2, le bateau sera horizontal

        numBateau=numBateau+1
        definir_taille_bateau=definir_taille_bateau+1

    print("Voici votre tableau de jeu")
    print(tab)
    print("")
    print(tab_bombe_joueur)
    return orientation


def position_choix(tab): #Cette fonction permet à l'utilisateur de choisir l'emplacement de ses bateaux sur le terrain

    numBateau=1
    tailleBateau2=0

    for i in range(0,5):

        nomBateau=str(input("Entrez le nom de votre bateau. Frégate (2c) ou Croiseur (3c) ou Sous-marin (3c) ou Cuirassé (4c)                 ou Porte-avions (5c): "))

        if nomBateau=="Frégate":

            tailleBateau2=2

        elif nomBateau=="Croiseur":

            tailleBateau2=3

        elif nomBateau=="Sous-marin":

            tailleBateau2=3

        elif nomBateau=="Cuirassé":

            tailleBateau2=4

        elif nomBateau=="Porte-avions":

            tailleBateau2=5

        else:

            print("Erreur, votre bateau est coulé d'office")
            tailleBateau2=0

    #On choisit ici où placer le bateau

        x2=int(input("Entrez la ligne de votre bateau: "))
        y2=int(input("Entrez la colone de votre bateau: "))
        orientation=int(input("Entrez l'orientation de votre bateau (1 pour vertical et 2 pour horizontal): "))

                #La boucle qui suit est là pour empêcher les bateaux de sortir du terrain
                #Si le bateau est vertical et que sa coordonnée en x est supérieur aux cases restantes pour placer le bateau, on demande à l'utilisateur de réentrer des coordonnnés

        while orientation==1 and x2>10-tailleBateau2 or orientation==2 and y2>10-tailleBateau2:

                x2=int(input("Votre bateau sort du terrain, entrez une nouvelle valeur de ligne svp: "))
                y2=int(input("Votre bateau sort du terrain, entrez une nouvelle valeur de colonne svp: "))
                orientation=int(input("Entrez l'orientation de votre bateau (1 pour vertical et 2 pour horizontal): "))


        #Appel de la fonction superpose pour voir si le bateau peut-être placé

        superpose_choix=superposition(tab,x2,y2,orientation,tailleBateau2)

        #tant que les bateaux se superposent on demande à l'utilisateur de réentrer les coordonnées

        while superpose_choix==True:

            print("Vos bateaux se superposent, veuillez recommencer.")
            x2=int(input("Entrez la ligne de votre bateau: "))
            y2=int(input("Entrez la colone de votre bateau: "))
            orientation=int(input("Entrez l'orientation de votre bateau (1 pour vertical et 2 pour horizontal): "))
            superpose_choix=superposition(tab,x2,y2,orientation,tailleBateau2)

            #On remet la condition pour vérifier que les bateaux ne sortent pas après la nouvelle saisie
            while orientation==1 and x2>10-tailleBateau2 or orientation==2 and y2>10-tailleBateau2:

                x2=int(input("Votre bateau sort du terrain, entrez une nouvelle valeur de ligne svp: "))
                y2=int(input("Votre bateau sort du terrain, entrez une nouvelle valeur de colonne svp: "))
                orientation=int(input("Entrez l'orientation de votre bateau (1 pour vertical et 2 pour horizontal): "))



        for j in range(0,tailleBateau2): #Même mécanisme que la fonction précedente

            tab[x2][y2]=numBateau

            if orientation==1 and x2!=9: #Si x=9, on ne fait pas "x+1" pour ne pas déborder du terrain

                x2=x2+1  #Si orientation=1, le bateau sera vertical

            elif orientation==2 and y2!=9: #Si y=9, on ne fait pas "y+1" pour ne pas déborder du terrain

                y2=y2+1  #Si orientation=2, le bateau sera horizontal

        numBateau=numBateau+1
        print(tab)


def superposition(tab,x,y,orientation,tailleBateau): #Cette fonction permet de déterminer si la place est libre pour pouvoir placer un bateau

    superpose=False

    #On part du point d'"origine" du bateau (le premier chiffre qui est placé) et on regarde si il n'y a aucun bateau qui gêne sur la ligne

    for i in range(0,tailleBateau):

        if orientation==2:

            if tab[x][i+y]>0:

                superpose=True

        elif orientation==1:

            if tab[i+x][y]>0:

                superpose=True

    return superpose


def place_bombe_joueur(tab_bombe_joueur,tableau_IA,x,y): #Fonction qui permet à l'utilisateur de "tirer" les bombes

        if tableau_IA[x][y]>0: #Si sur le tableau de l'IA, on tombe sur une valeur > 0, on affiche un 9 sur le tableau des bombes du joueur (on vient de toucher un bateau)

            tab_bombe_joueur[ligne_bombe][colonne_bombe]=9

        elif tableau_IA[x][y]==0: #Si sur le tableau de l'IA, on tombe sur une valeur = 0, on affiche un 8 sur le tableau des bombes du joueur (notre bombe est tombée à l'eau)

            tab_bombe_joueur[ligne_bombe][colonne_bombe]=8


        print(tab_bombe_joueur)


def tab_IA(nbCases_IA): #Création du tableau vide de l'IA

    tableau=np.full((nbCases_IA,nbCases_IA),0)

    return tableau


def placement_bateaux_IA(tableau_IA): #Remplissage du tableau de l'IA

#Toujours le même mécanisme que pour pooistion_aleatoire donc ce n'est pas nécessaire de re commenter cette fonction

    definir_taille_bateau=1
    taille_bateau_IA=0
    numBateau_IA=1

    for i in range(0,5):

        if definir_taille_bateau==1:

            taille_bateau_IA=2

        elif definir_taille_bateau==2:

            taille_bateau_IA=3

        elif definir_taille_bateau==3:

            taille_bateau_IA=3

        elif definir_taille_bateau==4:

            taille_bateau_IA=4

        else:

            taille_bateau_IA=5

        x=random.randint(0,10-taille_bateau_IA)
        y=random.randint(0,10-taille_bateau_IA)
        orientation=random.randint(1,2)

        #On utilise la même fonction superpose que précédemment

        superpose_IA=superposition(tableau_IA,x,y,orientation,taille_bateau_IA)

        while superpose_IA==True:

            x=random.randint(0,10-taille_bateau_IA)
            y=random.randint(0,10-taille_bateau_IA)
            superpose_IA=superposition(tableau_IA,x,y,orientation,taille_bateau_IA)

        for j in range(0,taille_bateau_IA):

            tableau_IA[x][y]=numBateau_IA

            if orientation==1 and x!=9:

                x=x+1

            elif orientation==2 and y!=9:

                y=y+1

        definir_taille_bateau=definir_taille_bateau+1
        numBateau_IA=numBateau_IA+1

    return(tableau_IA)


def maj_tableau_IA(tableau_IA,tab_bombe_joueur,ligne_bombe,colonne_bombe): #Cette fonction mets à jour les tirs de l'utilisateur sur le tableau de l'IA

#On retranscrit simplement les valeurs du tableau des bombes du joueur sur le tableau de l'IA

    if tab_bombe_joueur[ligne_bombe][colonne_bombe]==8:

        tableau_IA[ligne_bombe][colonne_bombe]=8

    elif tab_bombe_joueur[ligne_bombe][colonne_bombe]==9:

        tableau_IA[ligne_bombe][colonne_bombe]=9


def tir_IA(tab,x_bombe_IA,y_bombe_IA): #Cette fonction mets à jour les tirs de l'IA sur le tableau de l'utilisateur

#Même mécanisme que pour place_bombe_joueur

    if tab[x_bombe_IA][y_bombe_IA]==0:

        tab[x_bombe_IA][y_bombe_IA]=8

    elif tab[x_bombe_IA][y_bombe_IA]>0:

        tab[x_bombe_IA][y_bombe_IA]=9

    return(tab)


def superposition_bombe_IA(tab,x_bombe_IA,y_bombe_IA): #Cette fonction permet à l'IA de ne pas tirer deux fois au même endroit

    superpose_bombe=False

    if tab[x_bombe_IA][y_bombe_IA]==8 or tab[x_bombe_IA][y_bombe_IA]==9: #Les valeurs 8 et 9 sont les valeurs que l'ont doit afficher en tirant les bombes (9 si touché et 8 si à l'eau). On regarde donc simplement si il y a un 8 ou un 9 dans la case où on souhaite tirer

        superpose_bombe=True #Si superpose_bombe est à vrai, alors il y a déja une bombe à l'endroit où on veut tirer

    return(superpose_bombe)


def superpostion_bombe_utilisateur(tab_bombe_joueur,ligne_bombe,colonne_bombe): #Cette fonction permet de déterminer si l'utilisateur essaye de tirer à un endroit où il y a déjà une bombe

#Même mécanisme que pour superposition_bombe_IA

    superpose_bombe_2=False

    if tab_bombe_joueur[ligne_bombe][colonne_bombe]==8 or tab_bombe_joueur[ligne_bombe][colonne_bombe]==9:

        superpose_bombe_2=True

    return(superpose_bombe_2)

#Les deux fonctions suivantes servent à créer le damier du terrain avec des traits tracés à intervalles réguliers

def trace_trait_vertical():

    for i in range(0,11):
        cadre.create_line(i*60,0,i*60,TAILLEX)

def trace_trait_horizontal():

    for i in range(0,11):
        cadre.create_line(0,i*60,TAILLEY,i*60)


#Les deux fontions suivantes servent à placer les coordonnées sur le damier

def place_coord_vertical():

    txt_0=cadre.create_text(33,99,text="0")
    txt_1=cadre.create_text(33,156,text="1")
    txt_2=cadre.create_text(33,215,text="2")
    txt_3=cadre.create_text(33,270,text="3")
    txt_4=cadre.create_text(33,335,text="4")
    txt_5=cadre.create_text(33,395,text="5")
    txt_6=cadre.create_text(33,450,text="6")
    txt_7=cadre.create_text(33,510,text="7")
    txt_8=cadre.create_text(33,570,text="8")
    txt_9=cadre.create_text(33,627,text="9")

def place_coord_horizontal():

    txt_0=cadre.create_text(99,33,text="A")
    txt_1=cadre.create_text(156,33,text="B")
    txt_2=cadre.create_text(215,33,text="C")
    txt_3=cadre.create_text(270,33,text="D")
    txt_4=cadre.create_text(335,33,text="E")
    txt_5=cadre.create_text(395,33,text="F")
    txt_6=cadre.create_text(450,33,text="G")
    txt_7=cadre.create_text(510,33,text="H")
    txt_8=cadre.create_text(570,33,text="I")
    txt_9=cadre.create_text(627,33,text="J")

def recupere_coord_bombe(event): #Grâce à cette fonction, on récupère les coordonnés du clic de la souris que l'on transforme en coordonnés entre 0 et 9. De plus, on gère la fin de partie et le tour par tour dans cette fonction

    x_clic=event.x
    y_clic=event.y

    x_coord=int((x_clic-700)/60)-1 #-700 car il y a un décalage de 700 entre le premier et le second damier. -1 car on ne compte pas la case qui comporte les coordonnés

    y_coord=int(y_clic/60)-1

    global nbClic
    nbClic=nbClic+1

    if x_coord<0 or y_coord<0:
        print("Cliquez dans le tableau de droite svp")

    if nbClic<=3: #Tant qu'on a pas cliqué trois fois, on place les bombes sur le damier de droite et on incrémente la variable nombre_touche_joueur si on a touché un bateau

        place_bombe_tk(cadre,tableau_IA,x_coord,y_coord,x_clic,y_clic)
        global nombre_touche_joueur
        nombre_touche_joueur=nombre_touche_joueur+place_bombe_tk(cadre,tableau_IA,x_coord,y_coord,x_clic,y_clic)
        print("Vous avez touché",nombre_touche_joueur,"fois")

    else:

        for j in range(0,3): #Cette boucle permet à l'IA de placer des bombes sur le tableau de l'utilisateur

            x_bombe_IA=random.randint(0,9) #L'IA tire deux chiffres au hasard entre 0 et 9 qui seront les coordonnés de sa bombe
            y_bombe_IA=random.randint(0,9)
            position_libre=superposition_bombe_IA(tab,x_bombe_IA,y_bombe_IA) #booléen

            while position_libre==True: #On vérifie si l'IA n'a pas encore tiré à cet endroit

                x_bombe_IA=random.randint(0,9)
                y_bombe_IA=random.randint(0,9)
                position_libre=superposition_bombe_IA(tab,x_bombe_IA,y_bombe_IA)

            tir_IA(tab,x_bombe_IA,y_bombe_IA) #On tire dans un premier temps dans le shell
            global nombre_touche_IA
            nombre_touche_IA=tir_IA_tk(cadre,tab) #Puis on affiche les valeurs des tirs sur le tk

        print("l'IA a touché ",nombre_touche_IA," fois")

        nbClic=0 #On repasse nbClic à 0
        print(tab)
        print("")
        #print(tableau_IA)


    if nombre_touche_joueur==17: #Pour gagner, on doit toucher 17 fois. Donc dès que la variable nombre_touche_joueur est à 17, on ferme la fenêtre de jeu et on affiche une fenêtre avec écrit "Vous avez gagné!!"
        fenetre.destroy()
        fenetre3.destroy() #Au lancement on a trois fenêtre (1 pour le jeu et les 2 autres pour le message de fin de partie (gagné ou perdu). Si on gagne on ferme la fenêtre qui allait afficher "Vous avez perdu..."
        label=Label(fenetre2, text="Vous avez gagné!!")
        label.pack()
        fenetre2.mainloop()


    elif nombre_touche_IA==17: #Même chose sauf qu'ici c'est l'IA qui gagne (donc le joueur qui perd)
        fenetre.destroy()
        label2=Label(fenetre3, text="Vous avez perdu...")
        label2.pack()
        fenetre3.mainloop()
        fenetre2.destroy()








def affichage_bateaux(cadre,tab): #Cette fonction permet d'afficher les bateaux sur le damier de gauche sur le tk

#On parcourt tout le tableau et dès qu'on a une valeur > 0, on l'affiche sur le damier de gauche

    for i in range(0,10):
        for j in range(0,10):
            if tab[i][j]>0:
                bateau=cadre.create_text((j*60)+60+30,(i*60)+60+30,text=tab[i][j]) #+60+30 pour que les bateaux soient bien centrés et au bon endroit


#Les deux fonctions suivantes servent à tracer les traits pour le damier de droite sur le tk

def trace_trait_vertical_bombe():

    for i in range(0,11):
        cadre.create_line(i*60+700,0,i*60+700,TAILLEX)

def trace_trait_horizontal_bombe():

    for i in range(0,11):
        cadre.create_line(700,i*60,TAILLEX,i*60)

#Les deux fonctions suivantes servent à placer les coordonnés sur le damier de droite

def place_coord_vertical_bombe():

    txt_0=cadre.create_text(730,99,text="0")
    txt_1=cadre.create_text(730,156,text="1")
    txt_2=cadre.create_text(730,215,text="2")
    txt_3=cadre.create_text(730,270,text="3")
    txt_4=cadre.create_text(730,335,text="4")
    txt_5=cadre.create_text(730,395,text="5")
    txt_6=cadre.create_text(730,450,text="6")
    txt_7=cadre.create_text(730,510,text="7")
    txt_8=cadre.create_text(730,570,text="8")
    txt_9=cadre.create_text(730,627,text="9")

def place_coord_horizontal_bombe():

    txt_0=cadre.create_text(790,33,text="A")
    txt_1=cadre.create_text(850,33,text="B")
    txt_2=cadre.create_text(910,33,text="C")
    txt_3=cadre.create_text(970,33,text="D")
    txt_4=cadre.create_text(1030,33,text="E")
    txt_5=cadre.create_text(1090,33,text="F")
    txt_6=cadre.create_text(1150,33,text="G")
    txt_7=cadre.create_text(1210,33,text="H")
    txt_8=cadre.create_text(1270,33,text="I")
    txt_9=cadre.create_text(1330,33,text="J")


#Cette fonction permet de placer des bombes lors du clic de l'utilisateur sur le damier de droite


def place_bombe_tk(cadre,tableau_IA,x_coord,y_coord,x_clic,y_clic):

    cpt=0 #Compteur qui va servir à incrémenter la variable nombre_touche_joueur

    if tableau_IA[x_coord][y_coord]>0: #Si sur le tableau de l'IA en x_coord et y_coord (coordonnées du clic  converties après le calcul vu plus haut) on affiche la valeur contenue dans cet emplacement sur le tk
        cadre.create_text(((((x_clic*60)/x_clic)+730)+x_coord*60),((y_clic*90)/y_clic)+y_coord*60,text=tableau_IA[x_coord][y_coord])
        cpt=cpt+1 #Si on touche un bateau, on incrémente le compteur

#Sinon on affiche un zéro

    else:
        cadre.create_text(((((x_clic*60)/x_clic)+730)+x_coord*60),((y_clic*90)/y_clic)+y_coord*60,text="0")

    return(cpt)

#Cette fonction permet d'afficher, sur le tk, les bombes tirées par l'IA dans le shell

def tir_IA_tk(cadre,tab):

    cpt=0 #Compteur qui sert à incrémenter la variable nombre_touche_IA

    for i in range(0,10):
        for j in range(0,10):
            if tab[i][j]==9: #Si dans le tableau du joueur il y a un 9, cela veut dire que l'IA à touché un bateau et on affiche donc un X rouge sur le damier de gauche
                cadre.create_text((j*60)+60+30,(i*60)+60+30,text="X",fill="red")
                cpt=cpt+1 #Si on a touché, on incrémente le compteur

            elif tab[i][j]==8: #Sinon on affiche un / vert
                cadre.create_text((j*60)+60+30,(i*60)+60+30,text="/",fill="green")

    return(cpt)







#MAIN

fenetre=Tk()
fenetre2=Tk()
fenetre3=Tk()
cadre=Canvas(fenetre,width=TAILLEX,height=TAILLEY,bg="light yellow")
trace_trait_vertical()
trace_trait_horizontal()
place_coord_vertical()
place_coord_horizontal()
trait_separation=cadre.create_line(660,0,660,TAILLEX)
trait_du_bas=cadre.create_line(0,660,TAILLEY,660)
trace_du_bas=cadre.create_line(700,660,TAILLEX,660)
trace_trait_vertical_bombe()
trace_trait_horizontal_bombe()
place_coord_vertical_bombe()
place_coord_horizontal_bombe()

tab=creation(10)
tab_bombe_joueur=tab_touche_joueur(10)

position_aleatoire(tab)

affichage_bateaux(cadre,tab)

tableau_IA=tab_IA(10)
placement_bateaux_IA(tableau_IA)


cadre.bind("<Button-1>",recupere_coord_bombe)



cadre.pack()
fenetre.mainloop()

print(tab)




