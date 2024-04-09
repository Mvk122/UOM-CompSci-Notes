The pre-calculated weights from the clauradiance team are stored in python's pickle format, however extracting the information from them is extremely difficult as it requires knowledge of:
* The classes that were loaded at the time of pickling.
* It pickles many attributes that we do not require for our purposes.

Hence to get the weights of the GSUCells, we can just save the values at the end of its __init