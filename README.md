php-ile-myphp-yedek-alma
============

PHP kullanarak basit ve hızlı MySQL yedekleme / geri yükleme sistemi. Full veritabanı veya bazı tabloların yedeğini alabilirsiniz.

PHP 5.0.5 veya sonraki bir sürümü gerektirir.

Kullanımı
-----

**Yedekleme:**

Herhangi bir FTP programı ile siteniniz ana dizinine *myphp-backup.php* dosyasını yükleyin daha sonra http://www.example.com/myphp-backup.php şeklinde sitenize bağlanarak dosyayı çalıştırabilirsiniz.

*myphp-backup.php* Dosyasını hostunuza atmadan önce ayarlarınızı yapmayı unutmayın.

	define("DB_USER", 'your_username');
	define("DB_PASSWORD", 'your_password');
	define("DB_NAME", 'your_db_name');
	define("DB_HOST", 'localhost');

	define("BACKUP_DIR", 'myphp-backup-files'); // Comment this line to use same script's directory ('.')
	define("TABLES", '*'); // Full backup
	//define("TABLES", 'table1, table2, table3'); // Partial backup
	define("CHARSET", 'utf8');
	define("GZIP_BACKUP_FILE", true); // Set to false if you want plain SQL backup files (not gzipped)

Yedek alınırken yedekleri *myphp-backup-files* klasöründe *myphp-backup-{DB_NAME}-YYYYmmdd-HHMMSS.sql.gz* varsayılan ismi ile yedeklemektedir. Örnek yedeklenmiş dosya adı:

	myphp-backup-files/myphp-backup-daniloaz-20170828-131745.sql.gz

**Onarıma:**

*myphp-restore.php* dosyasını ana dizin ve yedekleme dosyanızı *myphp-backup-files* klasörüne yükleyin. daha sonra http://www.example.com/myphp-restore.php şeklinde sitenize bağlanarak dosyayı çalıştırabilirsiniz.

*myphp-restore.php* Dosyasını hostunuza atmadan önce ayarlarınızı yapmayı unutmayın.

	/**
	 * Define database parameters here
	 */
	define("DB_USER", 'your_username');
	define("DB_PASSWORD", 'your_password');
	define("DB_NAME", 'your_db_name');
	define("DB_HOST", 'localhost');
	define("BACKUP_DIR", 'myphp-backup-files'); // Comment this line to use same script's directory ('.')
	define("BACKUP_FILE", 'your-backup-file.sql.gz'); // Script will autodetect if backup file is gzipped or not based on .gz extension
	define("CHARSET", 'utf8');

-----
Project at GitHub: https://github.com/savasdersimcelik/php-myphp-backup

(c) Savaş Dersim Çelik, 2014-2018 (http://webinyo.com)
