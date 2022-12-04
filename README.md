# pension-holders-details-updation
project
Create table pension1 (
          name varchar2(20), 
          pensionid number (20),
          address varchar2(25),
          mobileno number(15));


insert into pension1 values('sai ram',552,'maharashtra',9347279638);

insert into pension1 values('ramesh',553,'agiripalli',95590339639);

insert into pension1 values('raji',564,'vizag',9985023589);





SQL> create or replace procedure pension
  2  (P_name varchar2,
            P_pensionid number,
            p_address varchar2,
            P_mobileno number,
            P_status  out varchar2)
  3  as
  4  begin
  5  update pension1 SET name = P_name,
  6        pensionid          =P_pensionid,
  7        address            =p_address
  8  where mobileno           =P_mobileno;
  9  if sql%found then
 10  commit;
 11  P_status:= 'pension details are updated successfully.';
 12  else
 13  rollback;
 14  P_status:='error in serer,please try again later.';
 15  end if;
 16  end pension;
 17  /
 

SQL> declare
  2  result varchar2(100);
  3  begin
  4  pension(P_name      =>'sai',
  5  P_pensionid         =>553,
  6  P_address           =>'maharashtra',
  7  P_mobileno          =>9347279638,
  8  P_status            =>result);
  9  dbms_output.put_line(result);
 10  end;
 11  /
