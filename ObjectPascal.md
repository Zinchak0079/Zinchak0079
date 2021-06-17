procedure TForm1.Timer1Timer(Sender: TObject);
begin
today := Now;
Form1.Caption:='Комуналка ' + ('| '+DateToStr(today)+' | '+TimeToStr(today));

end;

procedure TForm1.Button1Click(Sender: TObject);
var
  sv1,vod1,gs1,smit1,kanal1:Integer;
  sv2,vod2,gs2,smit2,kanal2:Extended;
  y: integer;
  t, c: real;
begin

if (Edit1.Text<>'') and (Edit2.Text<>'') and(Edit3.Text<>'')and(Edit4.Text<>'')
and(Edit5.Text<>'')then begin
DBGrid1.DataSource.DataSet.First;
mis := DBGrid1.DataSource.DataSet.Fields[1].AsString;
svit := DBGrid1.DataSource.DataSet.Fields[2].AsInteger;
kvt := DBGrid1.DataSource.DataSet.Fields[3].AsInteger ;
voda := DBGrid1.DataSource.DataSet.Fields[4].AsInteger ;
m3voda := DBGrid1.DataSource.DataSet.Fields[5].AsInteger ;
gas := DBGrid1.DataSource.DataSet.Fields[6].AsInteger ;
m3gas := DBGrid1.DataSource.DataSet.Fields[7].AsInteger;
smittya := DBGrid1.DataSource.DataSet.Fields[8].AsInteger ;
kanal := DBGrid1.DataSource.DataSet.Fields[9].AsInteger;
m3kanal := DBGrid1.DataSource.DataSet.Fields[10].AsInteger;
DBGrid1.DataSource.DataSet.First;

ed1:=(Edit1.Text);
ed2:= StrToInt(Edit2.Text);
ed3:= StrToInt(Edit3.Text) ;
ed4:= StrToInt(Edit4.Text) ;
ed5:= StrToInt(Edit5.Text);

Label1.Caption:=(ed1) ;
Label2.Caption:=IntToStr(ed2-svit) ;
Label3.Caption:=IntToStr(ed3-voda);
Label4.Caption:=IntToStr(ed4-gas) ;
Label6.Caption:=IntToStr(ed5);
Label7.Caption:=IntToStr(ed3-voda);

{j:=I+StrToInt(Edit2.Text);
Label3.Caption:=IntToStr(j);}

DBGrid1.DataSource.DataSet.Append;
DBGrid1.DataSource.DataSet.FieldByName('Місяць').AsString:=edit1.text;
DBGrid1.DataSource.DataSet.FieldByName('Світло').AsString:=edit2.text;
DBGrid1.DataSource.DataSet.FieldByName('КВт').AsString:=Label2.Caption;
DBGrid1.DataSource.DataSet.FieldByName('Вода').AsString:=edit3.text ;
DBGrid1.DataSource.DataSet.FieldByName('м3(вода)').AsString:=Label3.Caption ;
DBGrid1.DataSource.DataSet.FieldByName('Газ').AsString:=edit4.text ;
DBGrid1.DataSource.DataSet.FieldByName('м3(газ)').AsString:=Label4.Caption;
DBGrid1.DataSource.DataSet.FieldByName('Вивіз сміття').AsString:=edit5.text;
DBGrid1.DataSource.DataSet.FieldByName('Каналізація').AsString:=edit3.text;
DBGrid1.DataSource.DataSet.FieldByName('м3(канал)').AsString:=Label7.Caption;
DBGrid1.DataSource.DataSet.First;

// рахує загальну кількість грошей
sv1:=DBGrid1.DataSource.DataSet.Fields[3].AsInteger;
sv2:=DBGrid2.DataSource.DataSet.Fields[2].AsFloat;
vod1:=DBGrid1.DataSource.DataSet.Fields[5].AsInteger;
vod2:=DBGrid2.DataSource.DataSet.Fields[3].AsFloat;
gs1:=DBGrid1.DataSource.DataSet.Fields[7].AsInteger;
gs2:=DBGrid2.DataSource.DataSet.Fields[4].AsFloat;
smit1:=DBGrid1.DataSource.DataSet.Fields[10].AsInteger;
smit2:=DBGrid2.DataSource.DataSet.Fields[6].AsFloat;
// нижче стоїть [fields [8]] бо в delphi таблиці поміняв місцями поля, але не в базі
kanal1:=DBGrid1.DataSource.DataSet.Fields[9].AsInteger;
kanal2:=DBGrid2.DataSource.DataSet.Fields[5].AsFloat;
Label10.Caption:=FloatToStr(sv1*sv2)+' | '+FloatToStr(vod1*vod2)+' | '+FloatToStr(gs1*gs2)+' | '+
FloatToStr(smit1*smit2)+' | '+FloatToStr(kanal1*kanal2)+'  |  '
+ FloatToStr(sv1*sv2+vod1*vod2+gs1*gs2+smit1*smit2+kanal1*kanal2)+' грн ';

Edit1.Text:='';
Edit2.Text:='';
Edit3.Text:='';
Edit4.Text:='';
Edit5.Text:='';
end
else
Dialogs.ShowMessage('Введіть дані в поля вводу');

{begin
y:=StrToInt(Label2.Caption);
c:=0;
if (y<0) then
c:=(y*(-1));
end }
end;




procedure TForm1.DBGrid1DrawColumnCell(Sender: TObject; const Rect: TRect;
  DataCol: Integer; Column: TColumn; State: TGridDrawState);
begin
// дозволяє базам бути змінена
DBGrid1.DataSource.DataSet.Edit;
DBGrid2.DataSource.DataSet.Edit;
end;



procedure TForm1.DBGrid1CellClick(Column: TColumn);
var
i,b:integer;
begin
{b:= StrToInt(Edit2.Text);
i:=DBGrid1.SelectedIndex; //определяем номер выделенной колонки
 Label1.Caption:=DBGrid1.DataSource.DataSet.Fields.Fields[i].Value; //выводим, например, на метку значение ячейки
 Label2.Caption:=DBGrid1.Columns.Items[0].Field.asstring;
 Label3.Caption:=IntToStr((b)-DBGrid1.DataSource.DataSet.Fields.Fields[i].Value); }
  end;
procedure TForm1.FormCreate(Sender: TObject);
begin
       // так відбувається сортування таблиці
   ADOTable1.Sort:='Код DESC';
   ADOTable2.Sort:='Код DESC';
    // ADOTable1.Sort:=f + ' ASC'; (или DESC)
    DBGrid1.DataSource.DataSet.First;
    DBGrid2.DataSource.DataSet.First;
end;



procedure TForm1.Button2Click(Sender: TObject);
var
sv1,vod1,gs1,smit1,kanal1:Integer;
sv2,vod2,gs2,smit2,kanal2:Extended;
begin
if (Edit6.Text<>'') and (Edit7.Text<>'') and(Edit8.Text<>'')and(Edit9.Text<>'')
and(Edit10.Text<>'')then begin




{ed12:=(Edit6.Text);
ed6:= StrToInt(Edit7.Text);
ed7:= StrToInt(Edit8.Text) ;
ed8:= StrToInt(Edit9.Text) ;
ed9:= StrToInt(Edit10.Text);}

{j:=I+StrToInt(Edit2.Text);
Label3.Caption:=IntToStr(j);}

// записує дані в 2таблицю з Едіта під таблицею
DBGrid2.DataSource.DataSet.Append;
DBGrid2.DataSource.DataSet.FieldByName('Дата').AsString:=edit6.text;
DBGrid2.DataSource.DataSet.FieldByName('Світло').AsString:=Edit7.Text;
DBGrid2.DataSource.DataSet.FieldByName('Вода').AsString:=edit8.text ;
DBGrid2.DataSource.DataSet.FieldByName('Газ').AsString:=edit9.text ;
DBGrid2.DataSource.DataSet.FieldByName('Каналізація').AsString:=edit10.text;
DBGrid2.DataSource.DataSet.FieldByName('Вивіз Сміття').AsString:=edit11.text;
DBGrid2.DataSource.DataSet.First;



end
else
Dialogs.ShowMessage('Введіть дані в поля вводу');

end;


end.
