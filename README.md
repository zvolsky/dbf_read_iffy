# dbf_read_iffy
Make possible to read from dbf's*) with codepage unsupported by modules dbf and codecs (895 cz Kamenicky, ..)

	import dbf
	from dbf_read_iffy import fix_init, fix_895
	
	fix_init(dbf)
	t = dbf.Table('autori.dbf')
	t.open('read-only')
	for record in t:
	    print fix_895(record.autor)
	t.close()

*) Tip: In fact fix_895() converts the cp895 if you have read it as cp437. So you could use this function (without fix_init) to import any cp895 text into python, not only the dbf content.

You can ignore Python 2.7 installation error in test_v3.py (from aenum which is requirement of dbf).

For 620 pl Mazovia: You can define conversion map in fix_620(). If possible please: Fork me, clone your fork, commit/push, generate Pull request from your fork. Thx.
