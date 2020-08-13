title=Example of MySQL stored procedure to INSERT from a SELECT cursor values
date=2016-06-26
type=post
tags=mysql
status=published
~~~~~~
DELIMITER //
DROP PROCEDURE IF EXISTS proc_hotfix1 //
CREATE PROCEDURE proc_hotfix1()
BEGIN
  DECLARE flag INT DEFAULT 0;
  DECLARE CID VARCHAR(64);
  DECLARE LOGIN VARCHAR(1000);
  DECLARE cur1 CURSOR FOR 
    SELECT CID, LOGIN FROM MYUSER WHERE LOGIN LIKE 'bad.guy%';

  OPEN cur1;
  REPEAT
    FETCH cur1 INTO CID, LOGIN;
    INSERT INTO hotfix1(id,f1) VALUES (CID, LOGIN);
  UNTIL flag
  END REPEAT;
  CLOSE cur1;
END //

DELIMITER ;
DROP TABLE IF EXISTS hotfix1;
CREATE TABLE hotfix1(
  id VARCHAR(64) KEY
  ,f1 VARCHAR(1000)
  ,f2 VARCHAR(1000)
  ,f3 VARCHAR(1000)
);
CALL proc_hotfix1();
SELECT COUNT(*) FROM hotfix1;
SELECT * FROM hotfix1;