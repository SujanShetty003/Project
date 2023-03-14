from tkinter import *
from tkinter import messagebox

window = Tk()
window.geometry('650x400')
window.minsize(650, 400)
window.maxsize(650, 400)
window.title("Website Blocker")

heading = Label(window, text='Website Blocker', font='arial')
heading.pack()

host_path = 'C:\Windows\System32\drivers\etc\hosts'
ip_address = '127.0.0.1'

label1 = Label(window, text='Enter Website :(with www.)', font='arial 13 bold')
label1.place(x=5, y=60)

enter_Website = Text(window, font='arial', height='2', width=40)
enter_Website.place(x=230, y=60)

blabels = 0
ulabels = 0

message = ""


def Blocker(message):
    website_lists = enter_Website.get(1.0, END)
    Websites = website_lists.split(",")
    with open(host_path, 'r+') as host_file:
        file_content = host_file.read()
        for website in Websites:
            if website in file_content:
                message += website + ': Already Blocked\n'
            else:
                host_file.write('\n' + ip_address + " " + website)
                host_file.write('\n' + ip_address + " " +
                                website.replace('www.', ""))
                message += website + ': Blocked\n'
    messagebox.showinfo("Blocked/Unblocked", message)


def Unblock(message):
    website_lists = enter_Website.get(1.0, END)
    Websites = website_lists.split(",")
    with open(host_path, 'r+') as host_file:
        file_content = host_file.read()
    for website in Websites:
        if website in file_content:
            file_content = file_content.replace(
                '\n' + ip_address + " " + website, "")
            file_content = file_content.replace(
                '\n' + ip_address + " " + website.replace('www.', ""), "")
            message += website + ": Unblocked\n"
        else:
            message += website + ": Already Unblocked\n"
    with open(host_path, 'w') as host_file:
        host_file.write(file_content)
    messagebox.showinfo("Blocked/Unblocked", message)


block_button = Button(window, text='Block', font='arial', pady=5,
                      command=lambda: Blocker(message), width=6, bg='royal blue1', activebackground='grey')
block_button.place(x=230, y=150)

unblock_button = Button(window, text='UnBlock', font='arial', pady=5,
                        command=lambda: Unblock(message), width=6, bg='royal blue1', activebackground='grey')
unblock_button.place(x=350, y=150)

window.mainloop()
