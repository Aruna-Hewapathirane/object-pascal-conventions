# Object Pascal Conventions

# 1. Naming Conventions
**Variables & Constants**

Use **camel case** for variables:

```pascal 
var  
  userName: string;
  countItems: Integer;```

Use **all caps** for constants:

    const  
      MAX_USERS = 1000;
      DEFAULT_PATH = '/home/user/';

**Types**

    Prefix custom types with T:

    type  
      TUser = record  
        Name: string;  
        Age: Integer;  
      end;

**Classes & Objects**

    Class names should start with T:

type  
  TPerson = class  
    private  
      FAge: Integer;  
    public  
      property Age: Integer read FAge write FAge;  
  end;

Fields should start with F:

private  
  FName: string;

Methods & properties should use **PascalCase:**

function GetName: string;
procedure SetName(const AValue: string);

Parameters should start with A:

    procedure SetName(const AName: string);

**Global Variables**

    Prefix with G to indicate global scope:

    var  
      GAppTitle: string;

# 2. Formatting & Indentation

Use **2 or 4 spaces** per indentation (avoid tabs).

**Begin-End blocks should be indented:**

if X > 0 then  
begin  
  WriteLn('Positive');
end;

**Place begin and end on separate lines:**

procedure DoSomething;  
begin  
  WriteLn('Hello, World!');  
end;

**Keep if statements readable:**

if (Value > 10) and (Value < 20) then  
begin  
  WriteLn('Between 10 and 20');  
end;

**Single-line if allowed but discouraged:**

    if X = 0 then Exit;

# 3. Commenting

**Use** {} **or** (* *) **for block comments:**

{ This is a block comment }  
(* Another block comment *)

**Use** // **for single-line comments:**

// This is a single-line comment

**Describe complex logic:**

    // Check if the file exists before reading
    if FileExists(FileName) then  
    begin  
      LoadFile(FileName);  
    end;

# 4. Code Structure

**Procedure & function declarations should be at the top of the interface section:**

type  
  TPerson = class  
    private  
      FName: string;  
    public  
      function GetName: string;  
      procedure SetName(const AValue: string);  
  end;

**Implementation goes into the implementation section:**

implementation  

function TPerson.GetName: string;  
  begin  
    Result := FName;  
  end;

# 5. Error Handling

**Use** try..except **for exceptions:**

try  
  SomeRiskyOperation;  
except  
  on E: Exception do  
    WriteLn('Error: ', E.Message);
end;

**Use** try..finally **for cleanup:**

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

# 6. Units & Uses Clause

**Group standard and third-party libraries separately:**

uses  
  SysUtils, Classes, StrUtils,  
  MyUnit1, MyUnit2;

**Avoid circular dependencies**—use forward declaration if necessary.

# 7. Memory Management

**Always free objects:**

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

# 8. Pascal-Specific Best Practices

**Use** const **for parameters whenever possible** (avoids unnecessary copying):

procedure ShowMessage(const AText: string);

**Use** with **sparingly** (can make code harder to read):

with SomeObject do  
begin  
  Name := 'John';  
  Age := 30;  
end;

**Use** Enumerated types **instead of magic numbers:**

type  
  TColor = (clRed, clGreen, clBlue);

**Conclusion**
These conventions make Object Pascal code cleaner, more readable, and maintainable. Do you follow any specific conventions in your Lazarus projects, or do you want me to suggest something tailored to your style?




