---
title: Idiasession::findlinesbylinenum — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByLinenum method
ms.assetid: 76d5622d-9a91-4c2a-a98f-263af5d1daef
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5e3210dc974914779a8bff032ead3159c72535b0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787578"
---
# <a name="idiasessionfindlinesbylinenum"></a>IDiaSession::findLinesByLinenum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Określa numerów wierszy compiland —, że podany numer wiersza w pliku źródłowym znajduje się w obrębie lub w pobliżu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 [in] [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiekt, który reprezentuje compiland —, w których należy szukać numerów wierszy. Ten parametr nie może być `NULL`.  
  
 `file`  
 [in] [Idiasourcefile —](../../debugger/debug-interface-access/idiasourcefile.md) obiekt, który reprezentuje plik źródłowy do przeszukania. Ten parametr nie może być `NULL`.  
  
 `linenum`  
 [in] Określa numer liczonego od jednego wiersza.  
  
> [!NOTE]
>  Nie można użyć zero, aby określić wszystkie wiersze (Użyj [idiasession::findlines —](../../debugger/debug-interface-access/idiasession-findlines.md) metody do znalezienia wszystkich wierszy).  
  
 `column`  
 [in] Określa liczbę kolumn. Użyj wartości zero, aby określić wszystkie kolumny. Kolumna jest bajt przesunięcie wiersza.  
  
 `ppResult`  
 [out] Zwraca [idiaenumlinenumbers —](../../debugger/debug-interface-access/idiaenumlinenumbers.md) pobrać objta zawierający listę numerów wierszy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób otwierania pliku źródłowego, wyliczanie compilands pochodzącego z tego pliku i Znajdź numery wierszy w pliku źródłowym, gdzie rozpoczyna się każdego compiland —.  
  
```cpp#  
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
 [Idiaenumlinenumbers —](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [Idiasession::findlinesbyaddr —](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)   
 [Idiasourcefile —](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



