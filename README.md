import tkinter as tk

val = " "
def dis(key):
    global val
    val += key
    label_1.config(text = val)

def res():
    global val
    res = ""
    if val != "":
        try:
            res = str(eval(val))
        except:
            res = "Error"
            val = ""
        label_1.config(text = res)

def clr():
    global val
    val = ""
    label_1.config(text = val,)    
    

window = tk.Tk()
window.title("CALCULATOR")
window.configure(bg='green')

label_1 = tk.Label(window,width = 30,height=4,font = ("Dosis",20,"bold"),bg='grey',fg='black')

label_1.grid(row=0,column=0,columnspan=5)



button = ['C', ' (', ' )', ' /',
           '7', '8', '9',' *',
           '4', '5', '6', '+',
           '1', '2', '3', ' -',
           ' .', '0','%', '=']

row_val = 1
col_val = 0

for b in button:
    a = lambda x=b: dis(x) if x not in ['=', 'C'] else res() if x == '=' else clr()
    if b=='C':
        tk.Button(window,text=b,bg='red',padx=25, pady=15,bd=10, font=('Oswald',25), command=a).grid(row=row_val, column=col_val)
        col_val += 1
    elif b=='=':
        tk.Button(window,text=b,bg='yellow',padx=25, pady=15,bd=10, font=('Oswald',25), command=a).grid(row=row_val, column=col_val)
        col_val += 1
    else:
        tk.Button(window,text=b,padx=25,bg='ivory',fg='black',pady=15,bd=10,font=('Oswald', 22), command=a).grid(row=row_val, column=col_val)
        col_val += 1
        if col_val > 3:
            col_val = 0
            row_val += 1

window.mainloop()
