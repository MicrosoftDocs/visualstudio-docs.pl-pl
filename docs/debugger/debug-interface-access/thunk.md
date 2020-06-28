---
title: Thunk | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 90eeaefd8784be3e381c72dd452a23c56e0df47d
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461036"
---
# <a name="thunk"></a>Thunk
Każdy `thunk` jest identyfikowany przez `SymTagThunk` tag.

## <a name="properties"></a>Właściwości
 W poniższej tabeli przedstawiono właściwości, które są prawidłowe dla tego typu symbolu.

|Właściwość|Typ danych|Opis|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Atrybut modyfikatora dostępu, jedna z wartości [CV_access_e Wyliczenie](../../debugger/debug-interface-access/cv-access-e.md) (tylko w DIA SDK v 8.0 lub nowszym).|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Przesunięta część lokalizacji; Aby uzyskać szczegółowe informacje, zobacz [Wyliczenie LocationType](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSegment::get_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|`DWORD`|Część lokalizacji; Aby uzyskać szczegółowe informacje, zobacz [Wyliczenie LocationType](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Załączanie klasy nadrzędnej (jeśli istnieje) (tylko w DIA SDK V 8.0 lub nowszej).|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Identyfikator otaczającego symbolu nadrzędnego klasy (tylko w DIA SDK V 8.0 lub nowszym).|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|Ma wartość TRUE, jeśli thunk jest oznaczony jako stała (tylko w DIA SDK V 8.0 lub nowszym).|
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|Wartość TRUE, jeśli thunk jest wprowadzeniem do funkcji wirtualnej (tylko w DIA SDK V 8.0 lub nowszym)|
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|Wartość TRUE, jeśli thunk jest uznawana za statyczną (tylko w DIA SDK V 8.0 lub nowszym).|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Liczba bajtów kodu w thunk.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol dla otaczającego elementu jednostka kompilacji, Block lub Function.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Identyfikator leksykalnego symbolicznego symbolu.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Punkty końcowe mają lokalizację statyczną; Aby uzyskać szczegółowe informacje, zobacz Wyliczenie [lokalizacji symboli](../../debugger/debug-interface-access/symbol-locations.md) .|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nazwa thunk.|
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|Ma wartość TRUE, jeśli thunk jest czysto wirtualny (tylko w DIA SDK V 8.0 lub nowszym).|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Względne położenie tego thunk w swoim module.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Identyfikator indeksu symbolu.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Zwraca `SymTagThunk` (jedną z wartości [wyliczenia SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md) ).|
|[IDiaSymbol::get_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|`DWORD`|Przesunięta część lokalizacji elementu docelowego thunk.|
|[IDiaSymbol::get_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|`DWORD`|Względny adres wirtualny elementu docelowego thunk w jego otaczającym bloku.|
|[IDiaSymbol::get_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|`DWORD`|Część elementu docelowego thunk.|
|[IDiaSymbol::get_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|`ULONGLONG`|Pozycja elementu docelowego thunk w obrazie wykonywalnym.|
|[IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|`DWORD`|Typ thunk, zdefiniowany przez [wyliczenie THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md).|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Typ tego thunk (tylko w DIA SDK V 8.0 lub nowszym).|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Identyfikator symbolu typu (tylko w DIA SDK V 8.0 lub nowszym).|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE`Jeśli thunk nie jest wyrównany (tylko w DIA SDK V 8.0 lub nowszym),|
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE`Jeśli thunk jest wirtualny (tylko w DIA SDK V 8.0 lub nowszym).|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Pozycja tego thunk w obrazie wykonywalnym.|
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|Przesunięcie w tabeli wirtualnej do tego thunk (tylko w DIA SDK V 8.0 lub nowszym).|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE`Jeśli thunk jest oznaczony jako volatile (tylko w DIA SDK V 8.0 lub nowszym).|

## <a name="see-also"></a>Zobacz też
- [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType, wyliczenie](../../debugger/debug-interface-access/locationtype.md)
- [THUNK_ORDINAL, wyliczenie](../../debugger/debug-interface-access/thunk-ordinal.md)