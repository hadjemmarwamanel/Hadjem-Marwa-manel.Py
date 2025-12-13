import pandas as pd 

# Données : Séquences ADN, Longeur, Pourcentage de GC
data = {
    "Séquences": ["ATGCGTACGTA" , "GCTAGCTAGGCC" , "ATGCGCGTAAGT" , "TACGATCGTA" ,"ATGAAAGGCTT" , "CGTACGTAGC" , "TTAACCGGAT"],
    "Longeur": [12, 12, 12, 10, 11, 10, 10],
    "Pourcentage GC": [50, 66.67, 58.33, 40, 45.45, 60, 50]
}

# Création d'un Dataframe (tableau pandas)
df = pd.DataFrame(data)
print("**************** Création et affichage ****************")

# Affichage du tableau
print("tableau des Longeur :", "\n")
print(df, "\n" "\n")

# Opérations sur les tableau
print("**************** Opérations ****************")
#1) Sélectionner la colonne "Longeur"
Longeur = df ["Longeur"]
print(Longeur, "\n")

#2) Filtrer les Séquences dont la Longeur est superieur à 10
print("************* Filtrage avec la Longeur ****************", "\n")

filtred_df = df[df["Longeur"] > 10]
print(filtred_df, "\n")
 
#3) Calculer le Pourcentage moyenne de GC
print("************** Calcul de la moyenne ****************", "\n")

average_gc = df["Pourcentage GC"].mean()
print(f"Pourcentage moyenne de GC : {average_gc:.3f}%", "\n" "\n")

#4) Ajouter une nouvelle colonne Catégorie GC 
print("*********** Ajout d'une nouvelle colonne ************", "\n")

# Ajouter une nouvelle colonne "Catégorie GC"
df[ "  Catégorie GC "] = df["Pourcentage GC"].apply(lambda x: "Riche" if x > 55  else ("Moyenne" if 45 <= x <= 55 else "Faible"))
print(df, "\n" "\n")

#5) Ajouter une colonne comptant les 'G' de chaque séquence
df["Nombre de G"] = df["Séquences"].str.count("G")
print("******Nombre de G*******", "\n")
print(df,"\n" "\n")

#6) Calculer l'écart-type du % GC et de la longeur des Séquences
std_length = df["Longeur"].std()
print("******l'écart-type de la longeur des Séquences*******")
print("Écart-type de la longueur :", std_length,"\n")

std_gc = df["Pourcentage GC"].std()
print("******l'écart-type du % GC******")
print("Écart-type du % GC :", std_gc, "\n")

#7) Sauvegarde le tableau final dans un fichier CSV
df.to_csv("tableau_final.csv", index = False)
