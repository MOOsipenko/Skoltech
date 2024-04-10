import numpy as np
import pandas as pd
from numpy import load
from matplotlib import pyplot as plt

data = load('data_ps1.npz')
lst = data.files
for item in lst:
    pass
    #print(item)
    #print(data[item])

#print(lst)
#print(data["environment"])
#print(data["rod"].shape)
#print(data["rod"])


#plt.imshow(data["environment"])
#plt.show()

'''
fig, axis = plt.figure(6, 6)
for i in range(11):
    axis.imshow(data["rod"][i])
    plt.show()
'''

#print(data["rod"][7])
#plt.imshow(data["rod"][7])
#plt.show()

def plot_enviroment(img: np.ndarray, obj: np.ndarray, state: tuple):
    """
    @param img: original image in 2d
    @param obj: is the 3d array of different configurations
    @param state: is the current pose (x, y, orientation) of the object

    @return: the merged image
    """
    dims = obj.shape
    dim_x = int((dims[0] - 1) / 2)
    dim_y = int((dims[1] - 1) / 2)
    merged_img = np.copy(img)
    merged_img[state[0] - dim_x:state[0] + dim_x + 1, state[1] - dim_y:state[1] + dim_y + 1] += obj[:, :, state[2]] * 0.5
    return merged_img

#print((data["environment"].shape[0] - 1) / 2)
#print(data["rod"][1])
b = plot_enviroment(data["environment"], data["rod"], (11, 11, 2))
plt.imshow(b)
plt.show()