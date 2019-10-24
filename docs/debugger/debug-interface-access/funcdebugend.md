---
title: FuncDebugEnd | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- FuncDebugEnd symbol
- debugging [DIA SDK], end point
ms.assetid: 68f84fff-7cd3-4636-b929-7063a45009f8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b16e258e16fc49d220c4a7e31f5863e534c5a152
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745166"
---
# <a name="funcdebugend"></a>FuncDebugEnd
Jeśli funkcja ma zdefiniowany punkt, w którym debugowanie ma zostać zakończone, punkt początkowy debugowania jest identyfikowany przez symbol z tagiem `SymTagFuncDebugEnd`.

## <a name="properties"></a>Właściwości
 W poniższej tabeli przedstawiono właściwości, które są prawidłowe dla tego typu symbolu.

|Właściwość|Typ danych|Opis|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Przesunięta część lokalizacji; Aby uzyskać szczegółowe informacje, zobacz [Wyliczenie LocationType](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Część lokalizacji; Aby uzyskać szczegółowe informacje, zobacz [Wyliczenie LocationType](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE`, jeśli funkcja używa niestandardowej konwencji wywoływania (tylko w DIA SDK V 8.0 lub nowszym).|
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE`, jeśli funkcja wykonuje operację odwracania (tylko w DIA SDK V 8.0 lub nowszym).|
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` funkcja IF zawiera zwrot z przerwania (tylko w DIA SDK V 8.0 lub nowszym).|
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE`, jeśli funkcja jest statyczna (tylko w DIA SDK V 8.0 lub nowszym).|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol dla otaczającej funkcji.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Identyfikator leksykalnego symbolicznego symbolu.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Punkty końcowe mają lokalizację statyczną; Aby uzyskać szczegółowe informacje, zobacz [lokalizacji symboli](../../debugger/debug-interface-access/symbol-locations.md).|
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE`, jeśli funkcja została określona przy użyciu atrybutu [NoLine](/cpp/cpp/noinline) (tylko w DIA SDK v 8.0 lub nowszym).|
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE`, jeśli funkcja została określona za pomocą atrybutu [noreturn](/cpp/cpp/noreturn) (tylko w DIA SDK v 8.0 lub nowszym).|
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE`, jeśli funkcja nie jest nigdy wywoływana (tylko w DIA SDK V 8.0 lub nowszym).|
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Przesunięcie symbolu w pamięci; Aby uzyskać szczegółowe informacje, zobacz [Wyliczenie LocationType](../../debugger/debug-interface-access/locationtype.md), `LocIsRegRel`.|
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE`, jeśli funkcja ma informacje debugowania dla zoptymalizowanego kodu (tylko w DIA SDK V 8.0 lub nowszym).|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Identyfikator indeksu symbolu.|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Względne położenie końca tej funkcji w ramach modułu.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Zwraca `SymTagFuncDebugEnd` (jedną z wartości [wyliczenia SymTagEnum —](../../debugger/debug-interface-access/symtagenum.md) ).|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Pozycja tej funkcji w obrazie wykonywalnym.|

## <a name="see-also"></a>Zobacz także
- [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType, wyliczenie](../../debugger/debug-interface-access/locationtype.md)
- [Lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md)