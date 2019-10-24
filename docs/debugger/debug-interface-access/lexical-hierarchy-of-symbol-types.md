---
title: Hierarchia leksykalna typów symboli | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ad782ddb9a88b492d03e2338f17d95fb7bfa4f79
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738672"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Hierarchia leksykalna typów symboli
W poniższej tabeli przedstawiono typy symboli w hierarchii leksykalnej.

## <a name="symbol-types"></a>Typy symboli

|Typ symbolu|Opis|
|-----------------|-----------------|
|[Adnotacja](../../debugger/debug-interface-access/annotation.md)|Określa lokalizację do adnotacji w kodzie programu.|
|[Blok](../../debugger/debug-interface-access/block.md)|Określa zagnieżdżone zakresy w funkcjach.|
|`Compiland`|Określa `compiland` połączony z plikiem exe.|
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Określa jednostka kompilacji dane, które mogą wymagać ładowania dodatkowych jednostka kompilacji szczegóły, a tym samym naliczanie obciążenia w czasie wykonywania.|
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Określa wszelkie dodatkowe zmienne środowiskowe istotne dla kompilacji jednostka kompilacji.|
|[Niestandardowe (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Określa symbol zdefiniowany przez użytkownika.|
|[Dane (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Określa zmienne jako parametry, zmienne lokalne, zmienne globalne i składowe klas.|
|[Exe](../../debugger/debug-interface-access/exe.md)|Określa globalny zakres danych; odnosi się do całego pliku exe lub. dll.|
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Określa funkcję, która ma zdefiniowany punkt, w którym debugowanie ma zostać zakończone.|
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Określa funkcję, która ma zdefiniowany punkt, w którym rozpocznie się debugowanie.|
|[Funkcja (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Określa funkcję.|
|[Etykieta (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Określa lokalizację w kodzie programu.|
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Określa zewnętrzny symbol, który pojawia się podczas kompilowania programu wykonywalnego.|
|[Thunk](../../debugger/debug-interface-access/thunk.md)|Określa `thunk`.|
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Określa `namespace`identifier.|

> [!NOTE]
> Dodatkowe właściwości symboli mogą być dostępne w zależności od typu symbolu. Te właściwości są wymienione w tematach poszczególnych symboli.

## <a name="see-also"></a>Zobacz także
- [Hierarchia klas typów symboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
- [Symbole i tagi symboli](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
- [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)