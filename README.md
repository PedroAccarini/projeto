# Automatização_projeto

import glob
import csv

with open("planilha_final.csv", 'w') as final:
    w = csv.writer(final)

    for nf in glob.glob("Fornecedores/*.csv", recursive=True):

        with open(nf) as csv_file:
            temp = csv.reader(csv_file)

            for row in temp:
                w.writerow(row + [';'] + [str(nf).split('\\')[-1].split('.')[-2]])
