```
import tkinter as tk     #导入图形界面接口库，将代码以小游戏界面显示
import random            #导入产生随机数的库
number = random.randint(0,100)     #随机产生0-1024的一位数字
running = True
num = 0
nmaxn = 100          #nmaxn、nminn用于告知用户输入数字的范围，每输一次更新一次
nminn = 0

def eBtnClose(event):
    root.destroy()

#以下一段代码是实现猜数字的功能

def eBtnGuess(eent):
    global nmaxn
    global nminn
    global num
    global running

    if running:
        var_a = int(entry_a.get())          #获取猜测数字并转换为数字
        if var_a == number:
            labelqval("恭喜你答对了！")
            num += 1
            running = False
            numGuess()
        elif var_a < number:
            if var_a > nminn:
                nminn = var_a                #修改提示范围的最小值
                num += 1
                labelqval("小了哦，请输入"+str(nminn)+"到"+str(nmaxn)+"之间任意整数：")
        else:
            if var_a < nmaxn:
                nmaxn = var_a                #修改提示范围的最大值
                num +=1
                labelqval("大了哦，请输入"+str(nminn)+"到"+str(nmaxn)+"之间任意整数：")
    else:labelqval('你已经答对啦。。。')



#输出猜测的次数

def numGuess():
    if num == 1:
        labelqval('一次答对！')
    elif num<10:
        labelqval('==十次以内就答对了。。。尝试次数:'+str(num))
    else:
        labelqval('好吧，您超过十次了。。。尝试次数:'+str(num))


# 该函数用于修改提示标签文字

def labelqval(vText):
    label_val_q.config(label_val_q,text = vText)

root = tk.Tk(className="猜数字游戏")         #创建主窗口，名字为“猜数字游戏”
root.geometry("400x90+200+200")            #设置主窗口的初始大小
label_val_q = tk.Label(root,width = "80")  #提示标签宽度设置
label_val_q.pack(side = "top")             #把组件放在父组件的上面

entry_a = tk.Entry(root,width = "40")      #设置输入标签的宽度
btnGuess = tk.Button(root,text = "猜")     #插入按钮组件，名字为“猜”
entry_a.pack(side = "left")                #将组件放在父组件的左边
entry_a.bind('<Return>',eBtnGuess)         #绑定事件
btnGuess.bind('<Button-1>',eBtnGuess)
btnGuess.pack(side = "left")
btnClose = tk.Button(root,text = "关闭")    #插入按钮组件，名字为“关闭”
btnClose.bind('<Button-1>',eBtnClose)
btnClose.pack(side = "left")
labelqval("请输入0到100之间任意整数：")
entry_a.focus_get()
print(number)
root.mainloop()
```
