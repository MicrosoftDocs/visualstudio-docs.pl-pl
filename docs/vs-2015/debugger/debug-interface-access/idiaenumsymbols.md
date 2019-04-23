---
title: Idiaenumsymbols — | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols interface
ms.assetid: 649f7bfd-86ac-49a5-8533-aff77e1bc62e
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2f0aa09fe72030289f33ccf32f9777870a151ce1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60063195"
---
# <a name="idiaenumsymbols"></a>IDiaEnumSymbols
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wylicza różnych symboli znajdujących się w źródle danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaEnumSymbols : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDiaEnumSymbols`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaEnumSymbols::get__NewEnum](../../debugger/debug-interface-access/idiaenumsymbols-get-newenum.md)|Pobiera `IEnumVARIANT Interface` wersję tego modułu wyliczającego.|  
|[IDiaEnumSymbols::get_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md)|Pobiera liczbę symboli.|  
|[IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)|Pobiera symbol za pomocą indeksu.|  
|[IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)|Pobiera określoną liczbę symboli w kolejności wyliczenia.|  
|[IDiaEnumSymbols::Skip](../../debugger/debug-interface-access/idiaenumsymbols-skip.md)|Pomija określoną liczbę symboli w kolejności wyliczenia.|  
|[IDiaEnumSymbols::Reset](../../debugger/debug-interface-access/idiaenumsymbols-reset.md)|Resetuje sekwencji wyliczenia na początku.|  
|[IDiaEnumSymbols::Clone](../../debugger/debug-interface-access/idiaenumsymbols-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs zapewnia symbole, pogrupowane według określonego typu symbolu, na przykład `SymTagUDT` (typy zdefiniowane przez użytkownika) lub `SymTagBaseClass`. Aby pracować z symbolami, pogrupowane według adresów, należy użyć [idiaenumsymbolsbyaddr —](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md) interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Uzyskaj tego interfejsu, wywołując następujących metod:  
  
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
- [IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak uzyskać `IDiaEnumSymbols` interfejsu, a następnie użyj tego wyliczenia do listy typów zdefiniowanych przez użytkownika (UDTs).  
  
> [!NOTE]
>  `CDiaBSTR` jest klasą, która otacza `BSTR` i automatycznie obsługuje zwalnianie ciągu, gdy podczas tworzenia wystąpienia wykracza poza zakres.  
  
```cpp#  
void ShowUDTs(IDiaSymbol *pGlobals)  
{  
    CComPtr<IDiaEnumSymbols> pEnum;  
    CComPtr<IDiaSymbol> pSymbol;  
    HRESULT hr;  
  
    hr = pGlobals->findChildren(SymTagUDT,  
                                NULL,  
                                nsfCaseInsensitive | nsfUndecoratedName,  
                                &pEnum);  
    if (hr == S_OK)  
    {  
        while ( SUCCEEDED( hr = pEnum->Next( 1, &pSymbol, &celt ) ) &&  
                celt == 1 )  
        {  
            CDiaBSTR name;  
            if ( pSymbol->get_name( &name ) != S_OK )  
                Fatal( "get_name" );  
            printf( "Found UDT: %ws\n", name );  
            pSymbol = 0;  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Dia2.h  
  
 Biblioteka: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (debugowanie zestaw SDK dostępu do interfejsu)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiasession::findchildren —](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
