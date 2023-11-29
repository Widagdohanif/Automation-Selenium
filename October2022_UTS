import time
import tkinter as tiki
from tkinter import StringVar, ttk
from tkinter.messagebox import showinfo

from selenium import webdriver


def gui_main():
    #Window konfigurasi
    layar = tiki.Tk()
    layar.configure(bg="brown", border=20)
    layar.geometry("400x335")
    layar.title("Rate_5_Mach")

    #Frame konfigurasi
    frame_awal = ttk.Frame(layar)
    frame_awal.pack(padx=5, pady=1, fill='x')
    frame_isi = ttk.Frame(layar)
    frame_isi.pack(padx=5, pady=1, fill='x')
    frame_akhir = ttk.Frame(layar)
    frame_akhir.pack(padx=5, pady=1, fill='x')

    #variable
    result_nama = tiki.StringVar()
    result_nim = tiki.StringVar()
    _kelas_= tiki.IntVar()
    looping = tiki.IntVar()

    #Konfigurasi frame lanjutan
    label_welcome = ttk.Label(frame_awal ,text="Welcome to AutoRateMachine").pack(padx=10, pady=10)


    label_nama = ttk.Label(frame_isi, text="Nama")
    label_nama.pack()
    entry_nama = ttk.Entry(frame_isi, textvariable= result_nama, justify="center").pack(padx=50,pady=3,fill='x',expand=True)


    label_nim = ttk.Label(frame_isi, text="NIM")
    label_nim.pack()
    entry_nim = ttk.Entry(frame_isi, textvariable= result_nim, justify="center").pack(padx=50,pady=3,fill='x',expand=True)

    #kelas button
    frame_kelas_utama = ttk.Frame(frame_isi)
    frame_kelas_utama.pack(padx=5, pady=1)
    label_kelas_utama = ttk.Label(frame_kelas_utama, text="Kelas").pack()

    frame_kelas = ttk.Frame(frame_isi)
    frame_kelas.pack(padx=5, pady=1,side="left")

    frame_kelas1 = ttk.Frame(frame_isi)
    frame_kelas1.pack(padx=5, pady=1,side="right")


    tiki.Radiobutton(frame_kelas, text="RKS Reguler A", variable= _kelas_, value=1, padx=20).pack()
    tiki.Radiobutton(frame_kelas1, text="RKS Reguler B", variable= _kelas_, value=2, padx=20).pack()
    tiki.Radiobutton(frame_kelas, text="RKS Malam A", variable= _kelas_, value=3, padx=20).pack()
    tiki.Radiobutton(frame_kelas1, text="RKS Malam B", variable= _kelas_, value=4, padx=20).pack()

    #submit and function
    frame_tombol_utama = ttk.Frame(frame_akhir)
    frame_tombol_utama.pack(padx=5, pady=1)

    label_loop_utama = ttk.Label(frame_tombol_utama, text="How many Looping",).pack()
    entry_looping = ttk.Entry(frame_tombol_utama, textvariable=looping, justify="center").pack(padx=50,pady=3,fill='x',expand=True)

    tombol_run = ttk.Button(frame_tombol_utama, text="Execute!", command=lambda: main_utama(result_nim.get(), result_nama.get(), _kelas_.get(), looping.get()))
    tombol_run.pack(fill="x", padx=5, pady=5)
    

    layar.mainloop()
 
def main_utama(nim, nama, kelas_, loop):
    #pengecekan isi loop
    if loop == 0:
        tiki.messagebox.WARNING(title="Warning!!", text="Please fill The Loop!")


        #driver dan link tujuan
    deriver = webdriver.Chrome(executable_path='home/dao/chromedriver') 
    url = 'https://docs.google.com/forms/d/e/1FAIpQLSf102NzJH39BFwSdOt6aJ-MhwqkF5r1l82v4ILijgqcWnfeDw/viewform'

        #Menuju link website
    deriver.get(url)
    time.sleep(1) #cooldown for load
        
    def main_looping():
            #nim
        insert_nim = deriver.find_element('xpath', '//*[@id="mG61Hd"]/div[2]/div/div[2]/div[2]/div/div/div[2]/div/div[1]/div/div[1]/input')
        nim_insert = insert_nim.send_keys(nim)

            #nama
        insert_nama = deriver.find_element('xpath', '//*[@id="mG61Hd"]/div[2]/div/div[2]/div[3]/div/div/div[2]/div/div[1]/div/div[1]/input')
        nama_insert = insert_nama.send_keys(nama)
            
            #pilih kelas       
        kelas = deriver.find_element('xpath','//*[@id="mG61Hd"]/div[2]/div/div[2]/div[1]/div/div/div[2]/div/div[1]/div[1]/div[1]')
        kelas.click()
        time.sleep(1)
            #Kelas Link
        if kelas_ == 1:
            kelas_a = deriver.find_element('xpath','//*[@id="mG61Hd"]/div[2]/div/div[2]/div[1]/div/div/div[2]/div/div[2]/div[3]')
            kelas_a.click()

        elif kelas_ == 2:
            kelas_b = deriver.find_element('xpath','//*[@id="mG61Hd"]/div[2]/div/div[2]/div[1]/div/div/div[2]/div/div[2]/div[4]')
            kelas_b.click()

        elif kelas_ == 3:
            kelas_am = deriver.find_element('xpath','//*[@id="mG61Hd"]/div[2]/div/div[2]/div[1]/div/div/div[2]/div/div[2]/div[5]')
            kelas_am.click()

        elif kelas_ == 4:
            kelas_bm = deriver.find_element('xpath','//*[@id="mG61Hd"]/div[2]/div/div[2]/div[1]/div/div/div[2]/div/div[2]/div[6]')
            kelas_bm.click()
                                
            #rating
        rating_lima = deriver.find_element('xpath','//*[@id="mG61Hd"]/div[2]/div/div[2]/div[4]/div/div/div[2]/div/div[1]/div/div[10]/span/div[2]/div').click()
        tombol_kirim = deriver.find_element('xpath','//*[@id="mG61Hd"]/div[2]/div/div[3]/div[1]/div[1]/div').click()
        
        #kirim jawaban lain
        reloads = deriver.find_element('xpath','/html/body/div[1]/div[2]/div[1]/div/div[4]/a').click()
        
        time.sleep(1) 
    # Define a loop function 
    loop_ = int(loop)
    i=0
    while i != loop_ :
        main_looping()
        i += 1

    #pesan muncul juka sudah selesai
    tiki.messagebox.showinfo(title="Information", message="Successfull!")
    
gui_main()
