---
title: Hierarchia leksykalna typów symboli | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: a92f3f8f5174717b3fe3e992706a0f16478f99df
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56612806"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Hierarchia leksykalna typów symboli
W poniższej tabeli przedstawiono typy symbol w hierarchia leksykalna.

## <a name="symbol-types"></a>Typów symboli

|Typ symbolu|Opis|
|-----------------|-----------------|
|[Adnotacja](../../debugger/debug-interface-access/annotation.md)|Określa lokalizację adnotacjami w kodzie programu.|
|[Blok](../../debugger/debug-interface-access/block.md)|Określa zagnieżdżonych zakresów w funkcjach.|
|`Compiland`|Określa `compiland` połączone z pliku .exe.|
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Określa compiland — danych, może wymagają, trwa ładowanie szczegółów dodatkowe compiland — dlatego naliczane środowiska wykonawczego obciążenie do pobrania.|
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Określa wszelkie dodatkowe zmienne środowiskowe istotny dla kompilacji compiland —.|
|[Niestandardowe (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Określa symbol zdefiniowany przez użytkownika.|
|[Dane (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Określa takich zmiennych jako parametry, zmiennych lokalnych, zmiennych globalnych i składowych klasy.|
|[Exe](../../debugger/debug-interface-access/exe.md)|Określa globalny zakres danych. odnosi się do całego pliku .exe lub .dll.|
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Określa funkcję, która ma zdefiniowany punkt, w których debugowanie jest aby zakończyć.|
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Określa funkcję, która ma zdefiniowany punkt, w których debugowanie jest rozpoczęcie.|
|[Funkcja (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Określa funkcję.|
|[Etykieta (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Określa lokalizację, w kodzie programu.|
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Określa symbol zewnętrzny, który pojawia się podczas tworzenia pliku wykonywalnego programu.|
|[Thunk](../../debugger/debug-interface-access/thunk.md)|Określa `thunk`.|
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Określa `namespace`identyfikatora.|

> [!NOTE]
>  Właściwości dodatkowe symboli może znajdować się w zależności od typu symbolu. Te właściwości są podane w tematach pojedynczy symbol.

## <a name="see-also"></a>Zobacz też
- [Hierarchia klas typów symboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
- [Symbole i tagi symboli](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
- [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)