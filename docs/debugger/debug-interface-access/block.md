---
title: Blokuj | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SymTagBlock symbol
- nested scopes
- Block symbol
ms.assetid: 95b7b0c1-ecc9-405f-8456-5f9cfb866498
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c39c69900859957f0d0746c688334f31c8419d5f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745468"
---
# <a name="block"></a>Blok
Każdy blok kodu jest identyfikowany przez symbol `SymTagBlock`. Symbole blokowe służą do identyfikowania zagnieżdżonych zakresów w funkcjach.

## <a name="properties"></a>Właściwości
 W poniższej tabeli przedstawiono właściwości, które są prawidłowe dla tego typu symbolu.

|Właściwość|Typ danych|Opis|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Przesunięta część lokalizacji; Aby uzyskać szczegółowe informacje, zobacz [Wyliczenie LocationType](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Część lokalizacji; Aby uzyskać szczegółowe informacje, zobacz [Wyliczenie LocationType](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Liczba bajtów kodu w bloku.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol otaczającego bloku lub funkcji.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Zwraca identyfikator leksykalnego symbolicznego symbolu.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Bloki mają lokalizacje statyczne; Aby uzyskać szczegółowe informacje, zobacz [lokalizacji symboli](../../debugger/debug-interface-access/symbol-locations.md).|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Zwraca nazwę bloku (zazwyczaj jest to ciąg pusty).|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Zwraca wirtualny adres tego bloku względem jego leksykalnego elementu nadrzędnego.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Identyfikator indeksu symbolu.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Zwraca `SymTagBlock` (jedną z wartości [wyliczenia SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md) ).|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Zwraca wirtualny adres tego bloku w pliku wykonywalnym.|

## <a name="see-also"></a>Zobacz także
- [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType, wyliczenie](../../debugger/debug-interface-access/locationtype.md)
- [Lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md)