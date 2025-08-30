# BAKERY-MANAGEMENT-SYSTEM
A Bakery Management System built with Python and MySQL to streamline daily operations. Features include inventory tracking, order management, billing, and branch-wise record handling. Designed for efficiency and scalability, making bakery management easier and organized
import mysql.connector

con = mysql.connector.connect(host='localhost', user='root', password='ARYAN99#nigam')
cur = con.cursor()

# Create a new database if it does not exist
cur.execute("CREATE DATABASE IF NOT EXISTS food_service")

# Use the 'food_service' database
cur.execute("USE food_service")

# Create 'branch_shyamnagar' table if not exists
cur.execute("""
    CREATE TABLE IF NOT EXISTS branch_shyamnagar (
        serial_no INT AUTO_INCREMENT PRIMARY KEY,
        products VARCHAR(255) NOT NULL,
        cost INT NOT NULL
    )
""")
# Check if 'branch_shyamnagar' table is empty
cur.execute("SELECT COUNT(*) FROM branch_shyamnagar")
row_count = cur.fetchone()[0]
if row_count == 0:    
    # Insert sample data into 'branch_shyamnagar'
    cur.execute("INSERT INTO branch_shyamnagar (products, cost) VALUES ('cake', 10)")
    cur.execute("INSERT INTO branch_shyamnagar (products, cost) VALUES ('pastry', 12)")
    cur.execute("INSERT INTO branch_shyamnagar (products, cost) VALUES ('juice', 15)")
    cur.execute("INSERT INTO branch_shyamnagar (products, cost) VALUES ('butter', 18)")
    cur.execute("INSERT INTO branch_shyamnagar (products, cost) VALUES ('cheese', 20)")

# Create 'flavours' table if not exists
cur.execute("""
    CREATE TABLE IF NOT EXISTS flavours (
        serial_no INT AUTO_INCREMENT PRIMARY KEY,
        varieties VARCHAR(255) NOT NULL
    )
""")
# Check if 'flavours' table is empty
cur.execute("SELECT COUNT(*) FROM flavours")
row_count = cur.fetchone()[0]
if row_count == 0:    
    # Insert sample data into 'flavours'
    cur.execute("INSERT INTO flavours (varieties) VALUES ('vanilla')")
    cur.execute("INSERT INTO flavours (varieties) VALUES ('chocolate')")
    cur.execute("INSERT INTO flavours (varieties) VALUES ('strawberry')")
    cur.execute("INSERT INTO flavours (varieties) VALUES ('butterscotch')")
    cur.execute("INSERT INTO flavours (varieties) VALUES ('jasmine')")

# Commit changes and close connection
con.commit()
con.close()

con = mysql.connector.connect(host='localhost', user='root', password='ARYAN99#nigam')
cur=con.cursor()
cur.execute("Use food_service")


#ITEMS IN SHOP
def items():
    print("Items in the shop:")
    sql="select*from branch_shyamnagar"
    cur.execute(sql)
    res=cur.fetchall()
    t=(['serial_no','products','cost'])
    for serial_no,products,cost in res:
        print(serial_no,":",products,"\t",'cost',cost)


#VARIETIES OF CAKE
def item():
    print("Varieties available for Cakes:")
    s="select*from flavours"
    cur.execute(s)
    rs=cur.fetchall()
    t=(['serial_no','varieties'])
    for serial_no,varieties in rs:
        print(serial_no,":","\t",varieties)

#USER INTERFACE
def for_order():
    print("What do you want to order?")
    items()
    d=int(input("Enter your serial No of the item to buy:"))
    if d==1:
        print("Which cake do you want?")
        item()
        print("### NOTE: All Varieties of Cake Have Same Cost As That Of Cake  ###")
        print("Choose which cake do you want?")
        ck=int(input("Enter your Choice;"))
        if ck==1:
            print("How much quantity of vanilla cake you want?")
            qty=int(input("Enter Qty:"))
            print("You have successfully ordered your item!!!:")
            print("\n")
            Bill()
            da=cur.execute("Select cost from branch_shyamnagar")
            da=cur.fetchall()
            da=da[0][0]
            c=int(da)
            print("Total Quantity of Vanilla Cake:",qty)
            print("Total amount",qty*c)
            print("\n")
            bill()
            print("\n")
        elif ck==2:
            print("How much Quantity of Chocolate cake do you want?")
            qty=int(input("Enter Qty:"))
            print("You have successfully ordered your item!!!:")
            print("\n")
            Bill()
            da=cur.execute("Select cost from branch_shyamnagar")
            da=cur.fetchall()
            da=da[0][0]
            c=int(da)
            print("Total Quantity of Chocolate Cake:",qty)
            print("Total amount",qty*c)
            print("\n")
            bill()
            print("\n")
        elif ck==3:
            print("How much Quantity of Strawberry cake do you want?")
            qty=int(input("Enter Qty:"))
            print("You have successfully ordered your item!!!:")
            print("\n")
            Bill()
            print("\n")
            da=cur.execute("Select cost from branch_shyamnagar")
            da=cur.fetchall()
            da=da[0][0]
            c=int(da)
            print("Total Quantity of Strawberry Cake:",qty)
            print("Total amount",qty*c)
            print("\n")
            bill()
            print("\n")
        elif ck==4:
            print("How much Quantity of Butterscotch cake do you want?")
            qty=int(input("Enter Qty:"))
            print("You have successfully ordered your item!!!:")
            print("\n")
            Bill()
            da=cur.execute("Select cost from branch_shyamnagar")
            da=cur.fetchall()
            da=da[0][0]
            c=int(da)
            print("Total Quantity of Butterscotch Cake:",qty)
            print("Total amount",qty*c)
            print("\n")
            bill()
            print("\n")
        elif ck==5:
            print("How much Quantity of Jasmine cake do you want?")
            qty=int(input("Enter Qty:"))
            print("You have successfully ordered your item!!!:")
            print("\n")
            Bill()
            da=cur.execute("Select cost from branch_shyamnagar")
            da=cur.fetchall()
            da=da[0][0]
            c=int(da)
            print("Total Quantity of Jasmine Cake:",qty)
            print("Total amount",qty*c)
            print("\n")
            bill()
            print("\n")
    elif d==2:
        print("How much pastry do you want?")
        past=int(input("Enter quantity of pastry:"))
        print("You have successfully ordered",past,"pastry")
        d=cur.execute("Select cost from branch_shyamnagar where products='pastry'"';')
        d=cur.fetchall()
        d=d[0][0]
        c=int(d)
        print("\n")
        Bill()
        print("Total quantity of pastry:",past)
        print("Total amount=",past*c)
        print("\n")
        bill()
        print("\n")
    elif d==3:
        print("How much juice do you want?")
        jus=int(input("Enter the quantity of juice you want:"))
        print("You have successfully ordered",jus,"juice")
        d=cur.execute("Select cost from branch_shyamnagar where products='{}'".format('juice'))
        d=cur.fetchall()
        d=d[0][0]
        c=int(d)
        print("\n")
        Bill()
        print("Total quantity of Juice:",jus)
        print("Total amount=",jus*c)
        print("\n")
        bill()
        print("\n")
    elif d==4:
        print("How much butter do you want?")
        but=int(input("Enter the quantity of Butter you want:"))
        print("You have successfully ordered",but,"butter")
        d=cur.execute("Select cost from branch_shyamnagar where products='butter'"';')
        d=cur.fetchall()
        d=d[0][0]
        c=int(d)
        print("\n")
        Bill()
        print("Total quantity of butter:",but)
        print("Total amount=",but*c)
        print("\n")
        bill()
        print("\n")
    elif d==5:
            print("How much cheese do you want?")
            che=int(input("Enter your choice:"))
            print("You have successfully ordered",che,"cheese")
            d=cur.execute("Select cost from branch_shyamnagar where products='cheese'"';')
            d=cur.fetchall()
            d=d[0][0]
            c=int(d)
            print("\n")
            Bill()
            print("Total quantity of cheese:",che)
            print("Total amount=",che*c)
            print("\n")
            bill()
            print("\n")

#BILLING CODE
def Bill():
    print("...........................................................................")
    print("YOUR BILL")
    print("...........................................................................")
    print("Customer's name:",name)
    print("Contact no:",phone)
def bill():
    print("@@@@@@@@@@@@@@@@@@@@@ THANK_YOU FOR ORDERING THESE ITEMS @@@@@@@@@@@@@@@@@@")
    print("@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@ VISIT US AGAIN @@@@@@@@@@@@@@@@@@@@@@@@@@@@")

#ENTRANCE CODE
print("_________________________## CSE PROJECT ##____________________________")
print("___________________________________________________________________________________")
print("|.........................@@@@@@@@@@ WELCOME @@@@@@@@@@@@@........................|")
print("|..........................@@@@@@@@@@@@ TO @@@@@@@@@@@@@@.........................|")
print("|............................BAKERY MANAGEMENT SYSTEM.............................|")
print("|..........................Made by:Aryan Nigam....................................|")
print("|...........................Computer Science Engineering.......................................|")

name=input("Enter your name:")
phone=int(input("Enter your phone number;"))
#MAIN CODE
def Main():
    ch=''
    while ch!='N' or ch!='n':
        print("\n\nPLEASE CHOOSE\n1 FOR CUSTOMER \n2 FOR EXIT:/n/n")
        choice=int(input("Enter your choice"))
        if choice==2:
            break
            return
        elif choice==1:
            print('Press 1 to see the MENU',sep='......')
            print('Press 2 to order any item')
            print('Press 3 to EXIT')
            e=int(input("Enter your choice"))
            if e==3:
                return
            elif e==1:
                print("Items in the shop:")
                items()
            elif e==2:
                for_order()
            else:
                print("Wrong Input")
                ch=input("ARE YOU SURE TO EXIT FROM PROGRAM9Y/N0?")
                if ch=='y' or ch=='include':
                    break
Main()

