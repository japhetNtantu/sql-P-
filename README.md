import sqlite3

dbase = sqlite3.connect('CDB.db')
print('Database ouverte')

dbase.execute(''' CREATE TABLE IF NOT EXISTS chevaliers_table_ronde(
    ID INT PRIMARY KEY NOT NULL,
    CHEVALIERS NOT NULL,
    TITRE TEXT NOT NULL,
    COULEURS TEXT NOT NULL,
    REPUTATION TEXT NOT NULL,
    QUETES TEXT NOT NULL,
    EXPLOITS TEXT NOT NULL,
    ETAT INT NOT NULL) ''')

print('Table crée')
    
def insert_record(ID,CHEVALIERS,TITRE,COULEURS,REPUTATION,QUETES,EXPLOITS,ETAT):
    dbase.execute(''' INSERT INTO chevaliers_table_ronde(ID,CHEVALIERS,TITRE,COULEURS,REPUTATION,QUETES,EXPLOITS,ETAT)
            VALUES(?,?,?,?,?,?,?,?)''',(ID,CHEVALIERS,TITRE,COULEURS,REPUTATION,QUETES,EXPLOITS,ETAT))

    dbase.commit()
    print ('REcord inserted')
    
#insert_record(17,'5','5','5','5','5','5',5)

def read_Data():
    data = dbase.execute(''' SELECT * FROM chevaliers_table_ronde ORDER BY TITRE''')
    for record in data:
        print ('ID : ')+str(record[0])
        print ('CHEVALIERS : ')+str(record[1])
        print ('TITRE : '+)str(record[2])
        print ('COULEURS : ')+str(record[3])
        print ('REPUTATION : ')+str(record[2])
        print ('QUETES : ')+str(record[2])
        print ('EXPLOITS : ')+str(record[2])
        print ('ETAT : ')+str(record[2])+'\n'


def update_record():
    dbase.execute(''' UPDATE chevaliers_table_ronde SET REPUTATION='3' WHERE ID='2' ''')
    dbase.commit()
    print ('Updated')

def delete_record():
    #dbase.execute(''' DELETE from chevaliers_table_ronde WHERE ID='16' ''')
    dbase.commit()
    prit ('deleted')
delete_record
    
dbase.close()
print (' Database Closed')
