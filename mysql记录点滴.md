mysql if elseif语句的使用:
  SET GLOBAL log_bin_trust_function_creators = 1;

  DELIMITER $$
  CREATE FUNCTION pro_salary_grade8( wxapp_support TINYINT, app_support TINYINT) RETURNS CHAR
  BEGIN
       DECLARE support TINYINT  DEFAULT "0";

      IF wxapp_support=1 and app_support=1  THEN SET support ="0";
      ELSEIF wxapp_support=2 and app_support=1 THEN SET support ="1";
      ELSEIF wxapp_support=1 and app_support=2 THEN SET support ="2";
      ELSEIF wxapp_support=2 and app_support=2 THEN SET support ="3";
      ELSE SET support="0";
      END IF;

      RETURN support;

  END $$
  DELIMITER ;
  INSERT INTO wc_trade (id,mid,`name`,title,img_url,`desc`,support,issystem) 
  SELECT mid as id,mid,`name`,title,logo as img_url,ability as `desc`,pro_salary_grade8(wxapp_support,app_support) as support,issystem FROM `hd_modules`;

多级分类列表：select `id`,`path`,`p_id`,`name`,`level`,`description`,`is_recommend`,`status`,`sort`,`is_deleted`,`create_time`,`update_time` from dx_category where is_deleted="0" and status="1" order by CONCAT(path,id,",") asc;(path:0,14,17,)

一个字段中存在都好分割的多个id，查询某一个id是否在里面，并返回这条数据：SELECT * FROM `plus_store` where FIND_IN_SET(1059,uniacid);
