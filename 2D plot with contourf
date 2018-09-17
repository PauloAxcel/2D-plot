# -*- coding: utf-8 -*-
"""
Created on Thu Sep 13 00:16:24 2018

@author: user
"""
import matplotlib as mpl
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
from numpy import inf

#Get data into a dataframe

df = pd.read_csv('C:\\Users\\user\\Documents\\birmingham\\Conference\\LAUSANNE_22-24_10\\cad\\09_09_2018\\TOP ELECTROD NOT PATTERNED\\dados2.txt',sep='\t')

#Set the y value as the top columns

y = df.columns.values
y = pd.to_numeric(y, errors='coerce')
y = y[1:]

#Set the x value as the 1st row element for the first column

x = df.iloc[:,0]
x = x.values

#Set the z value as the inside of the table
#   y0  y1  y2  ... yn
#x0 z00 z01 z02 ... z0n 
#x1 z10 z11 z12 ... z1n
#x2 z20 z21 z22 ... z2n
#... ... ... ... ... ...
#xn zn0 zn1 zn2 ... znn
#write z values in log10 to easily analyse the data
#in the case of the enhancement being 0 we need to avoid the infinity

z = df.loc[:, df.columns != 'enhancement']
z = z.values
z = np.log10(z)
z[z == -inf] = 0

#plot the y,x and z in a 2d surface plot

fig, ax2 = plt.subplots()
cnt = ax2.contourf(y,x,z, cmap=mpl.cm.rainbow)
cb2 = fig.colorbar(cnt, ax=ax2 ,  extend='both' , label='log(Enhancement)')
