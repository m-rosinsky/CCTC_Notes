# Reverse Engineering Writeup

Box:
```
192.168.28.111
Port: 2222

Creds:
comrade:StudentWebExploitPassword
```

File Dir:
```
/var/www/html/consulting/public_html/longTermStorage
```

## Basic Algorithm

Exec:
```
basic1.exe
```

Code:
Trying to return 0x34cf
```
undefined4 __cdecl FUN_004010a0(byte *param_1)

{
  int iVar1;
  int local_8;

  iVar1 = FUN_00404a5c(param_1);
  local_8 = 2;
  while( true ) {
    if (0xb < local_8) {
      return 0xc;
    }
    if (local_8 * 0x2e == iVar1) break;
    local_8 = local_8 + 1;
  }
  return 0x34cf;
```

Success Keys:
```
2 * 46 = 92
3 * 46 = 138
4 * 46 = 184
5 * 46 = 230
6 * 46 = 276
7 * 46 = 322
8 * 46 = 368
9 * 46 = 414
10 * 46 = 460
11 * 46 = 506
Sum: 2990 ->
79bc18f6cbd3b2290cbd69c190d62bc6
```

## SDST 1

Exec:
```
sdst.exe
```

Main:
```
undefined4 FUN_00401100(void)

{
  FILE *pFVar1;
  int iVar2;
  char local_8 [4];

  FUN_00401000();
  FUN_00401280((wchar_t *)s_Press_enter_key:_004220c0);
  pFVar1 = (FILE *)FUN_004047cc(0);
  FUN_00404a84(local_8,2,pFVar1);
  iVar2 = FUN_00401060();
  if (iVar2 == 0x2a2) {
    FUN_00401280((wchar_t *)s_Success!_004220d4);
    Sleep(5000);
  }
  else {
    FUN_00401280((wchar_t *)s_Invalid_key._004220e0);
    Sleep(5000);
  }
  return 0;
}
```

```
undefined4 FUN_00401060(void)

{
  undefined4 uVar1;
  int local_10;
  int local_c;
  FILE *local_8;

  local_8 = _fopen(s_C:\Users\Public\Documents\secret_00422064,&DAT_00422060);
  FID_conflict:_fwprintf(local_8,(wchar_t *)&DAT_0042208c,&local_c);
  _fclose(local_8);
  local_8 = _fopen(s_C:\Users\Public\Documents\secret_00422094,&DAT_00422090);
  FID_conflict:_fwprintf(local_8,(wchar_t *)&DAT_004220bc,&local_10);
  _fclose(local_8);
  if (local_c + local_10 == 0x447f) {
    uVar1 = 0x2a2;
  }
  else {
    uVar1 = 0x44f6;
  }
  return uVar1;
}
```

Secret files at the locations, added together needs
to equal 17535

```
secret2.txt -> 8011
17535 - 8011 = 9524 ->
4c8b12c6485fc0b4ebae47a30f49ca0c
```

## SDST 2

Exec:
```
sdst2.exe
```

Main:
```
undefined4 FUN_00401170(void)

{
  BOOL BVar1;
  FILE *pFVar2;
  int iVar3;
  int local_10;
  HANDLE local_c;
  char local_8 [4];

  BVar1 = IsDebuggerPresent();
  if (BVar1 == 0) {
    local_c = (HANDLE)0xffffffff;
    local_10 = 0;
    local_c = GetCurrentProcess();
    CheckRemoteDebuggerPresent(local_c,&local_10);
    if (local_10 == 0) {
      FUN_00401000();
      printf((wchar_t *)s_Press_enter_key:_004200a4);
      pFVar2 = (FILE *)___acrt_iob_func(0);
      FUN_0040325f(local_8,2,pFVar2);
      iVar3 = user_func1();
      if (iVar3 == 0x92) {
        printf((wchar_t *)s_Success!_004200b8);
        Sleep(5000);
      }
      else {
        printf((wchar_t *)s_Invalid_key._004200c4);
        Sleep(5000);
      }
    }
    else {
      printf((wchar_t *)s_Stop_Cheating._00420094);
      Sleep(5000);
    }
  }
  else {
    printf((wchar_t *)s_Stop_cheating._004200d4);
    Sleep(5000);
  }
  return 0;
```

`user_func1` must return 0x92 (146)

user_func1:
```
void user_func1(void)

{
  size_t sVar1;
  DWORD local_218;
  DWORD local_214;
  FILE *local_210;
  HKEY local_20c;
  BYTE local_208 [256];
  char local_108 [256];
  uint local_8;

  local_8 = DAT_004200e8 ^ (uint)&stack0xfffffffc;
  local_214 = 0x100;
  local_218 = 1;
  RegOpenKeyExA((HKEY)0x80000001,s_SOFTWARE\MICROSOFT\KEYED3_00420048,0,0xf003f,&local_20c);
  RegQueryValueExA(local_20c,(LPCSTR)0x0,(LPDWORD)0x0,&local_218,local_208,&local_214);
  RegCloseKey(local_20c);
  local_210 = _fopen(s_C:\Users\Public\Documents\secret_00420068,&DAT_00420064);
  FID_conflict:_fwprintf(local_210,(wchar_t *)&DAT_00420090,local_108);
  _fclose(local_210);
  sVar1 = _strlen(local_108);
  if (sVar1 != 0) {
    _strcmp((char *)local_208,local_108);
  }
  FUN_0040135a(local_8 ^ (uint)&stack0xfffffffc);
  return;
```

The `strcmp` statement must return 0:
```
CALL       _strcmp                                          
ADD        ESP,0x8
TEST       EAX,EAX
JNZ        LAB_00401159
MOV        EAX,0x92
```

Compared to REGKEY:
```
HKCU:\\SOFTWARE\MICROSOFT\KEYED3
```
and
```
C:\Users\Public\Documents\secret3.txt
```

Add string to registry:
```
my_string
```

Run program and wait when prompted.
Add same string to secret3.txt
Press Enter.
Success.

## SDST 3 Part 1

Exec:
```
sdst3.exe
```

Main:
```
{
  undefined8 uVar1;
  long in_FS_OFFSET;
  char local_18 [8];
  long local_10;

  local_10 = *(long *)(in_FS_OFFSET + 0x28);
  createKey();
  printf("Press enter key: ");
  fgets(local_18,2,stdin);
  uVar1 = checkKey();
  if ((int)uVar1 == 0x2701) {
    puts("Success!");
    usleep(5000);
  }
  else {
    puts("Invalid key.");
    usleep(5000);
  }
  if (local_10 != *(long *)(in_FS_OFFSET + 0x28)) {
                    /* WARNING: Subroutine does not return */
    __stack_chk_fail();
  }
  return 0;
}
```

uVar1 must be 0x2701 (9985)
checkKey must return 9985.

createKey:
```
{
  FILE *__s;

  __s = fopen("/tmp/key","w");
  fwrite("UHV0IHRoZSBjb3JyZWN0IGludGVnZXIgb24gdGhpcyBsaW5lIGFmdGVyIHRoaXMgdGV4dCA=",1,0x48,__s);
  fclose(__s);
  return;
}
```

Writes
```
UHV0IHRoZSBjb3JyZWN0IGludGVnZXIgb24gdGhpcyBsaW5lIGFmdGVyIHRoaXMgdGV4dCA=
```
to
```
/tmp/key
```

Decoded:
```
Put the correct integer on this line after this text
```

checkKey:
integer after base64 text in /tmp/key
+
`ENV11` environment variable
=
18765

1. Set ENV11 on linux box as environment variable.
2. Run executable and get prompted.
3. Edit /tmp/key
4. Press Enter

## PE Patching

Exec:
```
patching.exe
```

Main:
```
{
  FILE *pFVar1;
  int iVar2;
  byte local_1c [20];
  uint local_8;

  local_8 = DAT_0041c02c ^ (uint)&stack0xfffffffc;
  printf((wchar_t *)s_Enter_Key:_0041c000);
  pFVar1 = (FILE *)FUN_00404b59(0);
  scanf((char *)local_1c,0x14,pFVar1);
  _strtok((char *)local_1c,&DAT_0041c00c);
  iVar2 = user_func1(local_1c);
  if (iVar2 == 0x34cf) {
    printf((wchar_t *)s_Success!_0041c010);
    Sleep(5000);
  }
  else {
    printf((wchar_t *)s_Invalid_key._0041c01c);
    Sleep(5000);
  }
  @__security_check_cookie@4(local_8 ^ (uint)&stack0xfffffffc);
  return;
}
```

Set `if` statement to always succeed.

## Encrypted Payload 1

main:
```
p_str = [17,66,86,76,64,19,8,25,22,85,71,2]
p_curr =
17 66 86 76 64 19 8 25 22 85 71 22 92 67 90 86 81 30 77 83 80 66 30 119 91 93 65 92 95 116 21 17 92 67 90 86 81 23 69 120 65 17 
```

user_func1
```
Buffer of 500 bytes gets zeroed.

Creates secret.ps1 as a hidden file.
```

secret:
```
PS C:\Users\student\Desktop\RE> cat .\secret3.ps1
$text = 'Ur owned'|Set-Content 'owned.txt'
```
