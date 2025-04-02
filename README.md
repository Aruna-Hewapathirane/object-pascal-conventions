# 1. Naming Conventions

## **Variables & Constants**

Use **camel case** for variables:

```pascal 
var  
  userName: string;
  countItems: Integer;
```

Use **all caps** for constants:
```pascal 
const  
  MAX_USERS = 1000;
  DEFAULT_PATH = '/home/user/';
```
## **Types**

Prefix custom types with T:
```pascal 
type  
  TUser = record  
    Name: string;  
    Age: Integer;  
end;
```
## **Classes & Objects**

Class names should start with T:
```pascal 
type  
  TPerson = class  
    private  
      FAge: Integer;  
    public  
      property Age: Integer read FAge write FAge;  
  end;
```
Fields should start with F:
```pascal 
private  
  FName: string;
```
Methods & properties should use **PascalCase:**
```pascal 
function GetName: string;
procedure SetName(const AValue: string);
```
Parameters should start with A:
```pascal 
procedure SetName(const AName: string);
```

## **Global Variables**

Prefix with G to indicate global scope:
```pascal 
var  
  GAppTitle: string;
```

# 2. Formatting & Indentation

Use **2 or 4 spaces** per indentation (avoid tabs).

**Begin-End blocks should be indented:**
```pascal 
if X > 0 then  
begin  
  WriteLn('Positive');
end;
```
**Place begin and end on separate lines:**
```pascal 
procedure DoSomething;  
begin  
  WriteLn('Hello, World!');  
end;
```
**Keep if statements readable:**
```pascal 
if (Value > 10) and (Value < 20) then  
begin  
  WriteLn('Between 10 and 20');  
end;
```
**Single-line if allowed but discouraged:**
```pascal 
    if X = 0 then Exit;
```
# 3. Commenting

**Use** {} **or** (* *) **for block comments:**
```pascal 
{ This is a block comment }  
(* Another block comment *)
```
**Use** // **for single-line comments:**
```pascal 
// This is a single-line comment
```
**Describe complex logic:**
```pascal 
// Check if the file exists before reading
if FileExists(FileName) then  
  begin  
    LoadFile(FileName);  
  end;
```
# 4. Code Structure

**Procedure & function declarations should be at the top of the interface section:**
```pascal 
type  
  TPerson = class  
    private  
      FName: string;  
    public  
      function GetName: string;  
      procedure SetName(const AValue: string);  
  end;
```
**Implementation goes into the implementation section:**
```pascal 
implementation  

function TPerson.GetName: string;  
  begin  
    Result := FName;  
  end;
```
# 5. Error Handling

**Use** try..except **for exceptions:**
```pascal 
try  
  SomeRiskyOperation;  
except  
  on E: Exception do  
    WriteLn('Error: ', E.Message);
end;
```
**Use** try..finally **for cleanup:**
```pascal 
var  
FileHandle: TFileStream;  
begin  
  FileHandle := TFileStream.Create('data.txt', fmOpenRead);  
    try  
      // Process the file  
    finally  
      FileHandle.Free;  
    end;  
end;
```
# 6. Units & Uses Clause

**Group standard and third-party libraries separately:**
```pascal 
uses  
  SysUtils, Classes, StrUtils,  
  MyUnit1, MyUnit2;
```
**Avoid circular dependencies**—use forward declaration if necessary.

# 7. Memory Management

**Always free objects:**
```pascal 
var  
  Obj: TObject;  
begin  
  Obj := TObject.Create;  
    try  
      // Use Obj  
    finally  
      Obj.Free;  
    end;  
end;    
```
# 8. Pascal-Specific Best Practices

**Use** const **for parameters whenever possible** (avoids unnecessary copying):
```pascal 
procedure ShowMessage(const AText: string);
```
**Use** with **sparingly** (can make code harder to read):
```pascal 
with SomeObject do  
begin  
  Name := 'John';  
  Age := 30;  
end;
```
**Use** Enumerated types **instead of magic numbers:**
```pascal 
type  
  TColor = (clRed, clGreen, clBlue);
```
**Conclusion**
These conventions make Object Pascal code cleaner, more readable, and maintainable. 


<a href="https://info.flagcounter.com/qK70"><img src="https://s01.flagcounter.com/count2/qK70/bg_FFFFFF/txt_000000/border_CCCCCC/columns_2/maxflags_10/viewers_0/labels_0/pageviews_0/flags_0/percent_0/" alt="Flag Counter" border="0"></a>

