---
title: Thunk | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- thunk properties [DIA SDK]
- thunk symbol
ms.assetid: 01abb95f-d89a-465c-a4eb-8e8509598c95
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1012053d3c63f9da18120dd3ccaa652ffc2301a8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070373"
---
# <a name="thunk"></a>Thunk
Każdy `thunk` jest identyfikowane za pomocą `SymTagThunk` tagu.  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli przedstawiono właściwości, które są prawidłowe dla tego typu symbolu.  
  
|Właściwość|Typ danych|Opis|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Atrybut modyfikator dostępu do jednego z [cv_access_e — wyliczenie](../../debugger/debug-interface-access/cv-access-e.md) wartości (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Przesunięcie część lokalizacji. Aby uzyskać więcej informacji, zobacz [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSegment::get_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|`DWORD`|Sekcja część lokalizacji. Aby uzyskać więcej informacji, zobacz [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Otaczającej klasy nadrzędnej, ewentualnej (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Identyfikator symbolu otaczającej klasy nadrzędnej (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|Wartość TRUE, jeśli osadzenia jest oznaczona jako stała (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|Wartość TRUE, jeśli thunk stanowi wprowadzenie do funkcji wirtualnych (tylko w DIA SDK w wersji 8.0 lub nowszy)|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|Wartość TRUE, jeśli osadzenia jest uznawany za statyczne (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Liczba bajtów kodu w osadzenia.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol compiland —, bloku lub funkcji otaczającej.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Identyfikator symbol leksykalne nadrzędnej.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Punkty końcowe mają statyczny lokalizacji. Aby uzyskać więcej informacji, zobacz [lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md) wyliczenia.|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nazwa osadzenia.|  
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|Wartość TRUE, jeśli thunk czysto wirtualny (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Względne położenie tego thunk w ramach jego moduł.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Identyfikator indeksu: symbolu.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Zwraca `SymTagThunk` (jeden z [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md) wartości).|  
|[IDiaSymbol::get_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|`DWORD`|Część lokalizacji docelowej thunk przesunięcia.|  
|[IDiaSymbol::get_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|`DWORD`|Względny adres wirtualny docelowej thunk w jego otaczającym bloku.|  
|[IDiaSymbol::get_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|`DWORD`|Część sekcji thunk obiektu docelowego.|  
|[IDiaSymbol::get_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|`ULONGLONG`|Pozycja elementu docelowego thunk w obrazu pliku wykonywalnego.|  
|[IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|`DWORD`|Dokonać konwersji bitowej adresów typu, zgodnie z definicją [thunk_ordinal — wyliczenie](../../debugger/debug-interface-access/thunk-ordinal.md).|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Typ tego thunk (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Identyfikator typu symbolu (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` w przypadku osadzenia nie jest wyrównany (tylko w DIA SDK w wersji 8.0 lub nowszy)|  
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE` w przypadku osadzenia wirtualnego (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Położenie tego thunk w obrębie obrazu pliku wykonywalnego.|  
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|Przesunięcie w wirtualnej tabeli, aby ta thunk (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` w przypadku osadzenia jest oznaczona jako volatile (tylko w DIA SDK w wersji 8.0 lub nowszym).|  
  
## <a name="see-also"></a>Zobacz też  
 [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md)   
 [THUNK_ORDINAL, wyliczenie](../../debugger/debug-interface-access/thunk-ordinal.md)