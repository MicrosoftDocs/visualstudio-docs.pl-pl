---
title: 'IDiaSession:: findLinesByLinenum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByLinenum method
ms.assetid: 76d5622d-9a91-4c2a-a98f-263af5d1daef
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e2486d3cbbecad1dee6b171f105d155d95a4e231
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855131"
---
# <a name="idiasessionfindlinesbylinenum"></a>IDiaSession::findLinesByLinenum
Określa numery wierszy jednostka kompilacji, w których znajduje się określony numer wiersza w pliku źródłowym.

## <a name="syntax"></a>Składnia

```C++
HRESULT findLinesByLinenum ( 
    IDiaSymbol*           compiland,
    IDiaSourceFile*       file,
    DWORD                 linenum,
    DWORD                 column,
    IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametry
`compiland`

podczas Obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , który reprezentuje jednostka kompilacji do wyszukiwania numerów wierszy. Ten parametr nie może być `NULL` .

`file`

podczas Obiekt [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) , który reprezentuje plik źródłowy do przeszukania. Ten parametr nie może być `NULL` .

`linenum`

podczas Określa pojedynczy numer wiersza.

> [!NOTE]
> Nie można użyć zera do określenia wszystkich wierszy (Użyj metody [IDiaSession:: findLines](../../debugger/debug-interface-access/idiasession-findlines.md) , aby znaleźć wszystkie wiersze).

`column`

podczas Określa numer kolumny. Użyj wartości zero, aby określić wszystkie kolumny. Kolumna jest przesunięciem bajtów do wiersza.

`ppResult`

określoną Zwraca [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) objta, który zawiera listę pobranych wierszy.

## <a name="return-value"></a>Wartość zwracana
Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak otworzyć plik źródłowy, wyliczyć compilands, który został wniesiony przez ten plik, i zlokalizować numery wierszy w pliku źródłowym, w którym uruchamiane są poszczególne jednostka kompilacji.

```C++
void ShowLinesInCompilands(IDiaSession *pSession, LPCOLESTR filename)
{
    IDiaEnumSourceFiles* pEnum;
    IDiaSourceFile*      pFile;
    DWORD                celt;

    pSession->findFile ( NULL, filename, nsFNameExt, &pEnum );
    while ( pEnum->Next ( 1, &pFile, &celt ) == S_OK ) // for each file
    {
        IDiaEnumSymbols* pEnumCompilands;
        IDiaSymbol* pCompiland;

        pFile->get_compilands ( &pEnumCompilands );
        // for each compiland
        while ( pEnumCompilands->Next ( 1, &pCompiland, &celt ) == S_OK )
        {
            IDiaEnumLineNumbers* pEnum;
            // Find first compiland closest to line 1 of the file.
            if (pSession->findLinesByLinenum( pCompiland, pFile, 1, 0, &pEnum ) == S_OK)
            {
                IDiaLineNumber *pLineNumber;
                DWORD lineCount;
                while ( pEnum->Next(1,&pLineNumber,&lineCount) == S_OK)
                {
                    DWORD lineNum;
                    if (pLineNumber->get_line(&lineNum) == S_OK)
                    {
                        printf("compiland starts in source at line number = %lu\n",lineNum);
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Zobacz też
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
