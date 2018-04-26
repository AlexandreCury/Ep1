# Ep1#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
Created on Thu Apr 26 18:40:17 2018

@author: AlexandreCury
"""

# DEFININDO CLASSES METODOS E VARIAVEIS GLOBAIS
import json
rodando = True;
estoque ={};

with open('data.json') as json_file:
    estoque = json.load(json_file)


#INICIO DO CODIGO

while(rodando):
    print ("1-Para adcionar produto \n2-Para deletar um produto \n3-Alterar dados de um produto\n4-Imprimir estoque\n5-Add Preco\n6-Imprimir valor total\n7-Imprimir valores negativos\n0-Sair\n");
    a = input("escolha : ");
    if int(a) == 1:
        n = input("Digite o nome do produto : ");
        q = input("Digite a quantidade desse produto: ");
        prod = {n:[q]}
        estoque.update(prod);
    elif int(a) == 2:
            nome = input("Digite o nome do produto : ");
            del estoque[nome];

    elif int(a) == 3:
        nome = input("Digite o nome do produto que deseja alterar : ");
        nova_quantidade = input("Digite a nova quantidade : ");
        estoque[nome] = nova_quantidade;

    elif int(a) == 4:
        for i in estoque.keys():
            if len(estoque[i]) > 1:
                print ('Nome do produto :%s \nQuantidade :%s\nPreco:%s' % (i, estoque[i][0],estoque[i][1]) );
            else:
                print ('Nome do produto :%s \nQuantidade :%s' % (i, estoque[i][0]) );

    elif int(a) == 5:
        n = input("Digite o nome do produto : ");
        q = input("Digite o preco desse produto: ");
        quantidade = estoque[n][0];
        prod = {n:[quantidade, q]};
        estoque.update(prod);
    elif int(a) == 6:
        a = 0;
        for i in estoque.keys():
            if len(estoque[i]) > 1:
                a+= int(estoque[i][1]);
            print("Valor Total:%s" % a);
    elif int(a) == 7:
        for i in estoque.keys():
            if int(estoque[i][0]) < 0:
                print("Produto: %s, Quantidade:%s\n" % (i, estoque[i][0]));
    else:
        print("See You Later Aligator");
        rodando = False;

with open('data.json', 'w') as outfile:
    json.dump(estoque, outfile);
