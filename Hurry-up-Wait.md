# Hurry-up!-Wait!
## Category
Reverse Engineering
## Problem Description
[svchost.exe](https://mercury.picoctf.net/static/df4efca50acbb7c5e829f8fd472fb796/svchost.exe)
## Approach
Opening the file in Ghidra the following function stands out.
```
void FUN_0010298a(void)

{
  ada__calendar__delays__delay_for(1000000000000000);
  FUN_00102616();
  FUN_001024aa();
  FUN_00102372();
  FUN_001025e2();
  FUN_00102852();
  FUN_00102886();
  FUN_001028ba();
  FUN_00102922();
  FUN_001023a6();
  FUN_00102136();
  FUN_00102206();
  FUN_0010230a();
  FUN_00102206();
  FUN_0010257a();
  FUN_001028ee();
  FUN_0010240e();
  FUN_001026e6();
  FUN_00102782();
  FUN_001028ee();
  FUN_001022a2();
  FUN_0010226e();
  FUN_001023da();
  FUN_00102206();
  FUN_0010230a();
  FUN_0010233e();
  FUN_00102136();
  FUN_00102956();
  return;
}

```
```
void FUN_00102616(void)

{
  ada__text_io__put__4(&DAT_00102cd8,&DAT_00102cb8);
  return;
}
```
Visiting DAT_00102cd8 in the function FUN_00102616(void) revealed the letter p and consequently all the functions together produced the flag.
## Flag
picoCTF{d15a5m_ftw_87e5ab1}
