# Man_Db
@(一个基于pymysql模块的mysql操作类)
**DEMO**
```SELECT ONE
sql = 'SELECT * FROM '+db.table('articles')+' WHERE id=%s LIMIT 0,1'
    if db.query(sql ,(1,)):
        row = db.fetch_one()
        print row

# SELECT many
    sql = 'SELECT * FROM '+db.table('articles')+' WHERE id>%s LIMIT 0,10'
    if db.query(sql,(1,)):
        rows = db.fetch_all()
        for r in rows:
            print r
    # INSERT
    datas = {
        'content':'This is content',
        'status':0,
        'created':int(time.time()),
        'title':'This is title'
    }
    id = db.insert('articles' ,datas)
    if id > 0 :
        db.commit()
    # UPDATE
    updates = {
        'title':'This is a test for update'
    }
    res = db.update('articles' ,updates ,'id=10')
    if res is not False:
        db.commit()
    # DELETE
    res = db.delete('articles' ,'id=%s',(2,))
    if res is not False:
        db.commit()
```