---
title: Idiaenumsymbolsbyaddr — | Dokumentacja firmy Microsoft
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
- IDiaEnumSymbolsbyAddr interface
ms.assetid: 37d3dcdf-e4fa-4354-b5e1-8843566b52ac
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f394e0fa3f2c6c6697db5b81eca16f4020f314d7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753777"
---
# <a name="idiaenumsymbolsbyaddr"></a>IDiaEnumSymbolsByAddr
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wylicza przy użyciu adresu różnych symboli znajdujących się w źródle danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaEnumSymbolsByAddr : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDiaEnumSymbolsByAddr`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)|Umieszcza modułu wyliczającego, wykonując wyszukiwanie w sekcji i przesunięcie.|  
|[IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)|Umieszcza modułu wyliczającego, wykonując wyszukiwanie przez względnych adresów wirtualnych (RVA).|  
|[IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)|Umieszcza modułu wyliczającego, wykonując wyszukiwanie przy użyciu wirtualnego adresu (oceny luk w zabezpieczeniach).|  
|[IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)|Pobiera następny symbole w kolejności według adresu. Aktualizuje pozycja modułu wyliczającego z kilku elementów pobrana.|  
|[IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)|Pobiera poprzednich symboli w kolejności według adresu. Aktualizuje pozycja modułu wyliczającego z kilku elementów pobrana.|  
|[IDiaEnumSymbolsByAddr::Clone](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-clone.md)|Tworzy kopię obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs zawiera symbole, pogrupowane według adresu. Do pracy z symbolami, pogrupowane według typu, na przykład `SymTagUDT` (typ zdefiniowany przez użytkownika) lub `SymTagBaseClass`, użyj [idiaenumsymbols —](../../debugger/debug-interface-access/idiaenumsymbols.md) interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Uzyskanie tego interfejsu, wywołując [idiasession::getsymbolsbyaddr —](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md) metody.  
  
## <a name="example"></a>Przykład  
 Funkcja ta wyświetla nazwę i adres wszystkie symbole, uporządkowane według względny adres wirtualny.  
  
```cpp#  
void ShowSymbolsByAddress(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSymbolsByAddr> pEnumByAddr;  
    if ( FAILED( psession->getSymbolsByAddr( &pEnumByAddr ) ) )  
    {  
        Fatal( "getSymbolsByAddr" );  
    }  
    CComPtr<IDiaSymbol> pSym;  
    if ( FAILED( pEnumByAddr->symbolByAddr( 1, 0, &pSym ) ) )  
    {  
        Fatal( "symbolByAddr" );  
    }  
    DWORD rvaLast = 0;  
    if ( pSym->get_relativeVirtualAddress( &rvaLast ) == S_OK )  
    {  
        pSym = 0;  
        if ( FAILED( pEnumByAddr->symbolByRVA( rvaLast, &pSym ) ) )  
        {  
            Fatal( "symbolByAddr" );  
        }  
        printf( "Symbols in order\n" );  
        do  
        {   
            CDiaBSTR name;  
            if ( pSym->get_name( &name ) != S_OK )  
            {  
                printf( "\t0x%08X (%ws) <no name>\n", rvaLast );  
            }  
            else  
            {  
               printf( "\t0x%08X %ws\n", rvaLast, name );  
            }  
            pSym = 0;  
            celt = 0;  
            if ( FAILED( hr = pEnumByAddr->Next( 1, &pSym, &celt ) ) )  
            {  
                break;  
            }  
        } while ( celt == 1 );  
    }  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Dia2.h  
  
 Biblioteka: diaguids.lib  
  
 Biblioteki DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (debugowanie zestaw SDK dostępu do interfejsu)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiasession::getsymbolsbyaddr —](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)



