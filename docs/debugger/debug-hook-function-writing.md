---
title: Zastępowanie funkcji punktu zaczepienia debugowania | Microsoft Docs
description: Przeczytaj o kilku niestandardowych funkcjach punktu zaczepienia debugowania, które można napisać, aby umożliwić wstawienie kodu do wstępnie zdefiniowanych punktów wewnątrz normalnego przetwarzania debugera.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vc.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], CRT debug support
- debug hook functions
- hooks, debug
- hooks
- debugging [CRT], debug hook functions
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5e2f05005d0b43d526936bfbc8018739cb1ed88
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728940"
---
# <a name="debug-hook-function-writing"></a>Pisanie debugowanie funkcji punktów zaczepienia
W tej sekcji opisano szereg funkcji niestandardowego punktu zaczepienia debugowania, które można napisać, aby umożliwić Wstawianie kodu do niektórych wstępnie zdefiniowanych punktów wewnątrz normalnego przetwarzania debugera.

## <a name="in-this-section"></a>W tej sekcji
 [Funkcje punktu zaczepienia bloku klienta](../debugger/client-block-hook-functions.md) Zawiera wskazówki i prototyp do pisania funkcji, które weryfikują lub raportują zawartość danych przechowywanych w blokach _CLIENT_BLOCK.

 [Funkcje punktu zaczepienia alokacji](../debugger/allocation-hook-functions.md) Definiuje funkcję punktu zaczepienia alokacji, bada jej różne zastosowania, wskazuje ograniczenia i oferuje prototyp.

 [Punkty zaczepienia alokacji i alokacje pamięci CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md) Opisuje ograniczenia dotyczące funkcji punktu zaczepienia alokacji jawnie ignorowanie `_CRT_BLOCK` bloków w przypadku wykonywania przez nich wywołań do funkcji biblioteki wykonawczej języka C, które przydzielą pamięć wewnętrzną. W tym temacie wymieniono również konsekwencje, jeśli punkt zaczepienia alokacji nie ignoruje `_CRT_BLOCK` bloków (z przykładami) i jak zmienić domyślną funkcję punktu zaczepienia alokacji, **CrtDefaultAllocHook**.

 [Raportowanie funkcji punktów zaczepienia](../debugger/report-hook-functions.md) Omówienie `_CrtSetReportHook` , których można użyć do filtrowania raportów, aby skoncentrować się na określonych typach alokacji. Ten temat zawiera również prototyp.

## <a name="related-sections"></a>Sekcje pokrewne

- [Techniki debugowania CRT](../debugger/crt-debugging-techniques.md) — linki do technik debugowania dla biblioteki języka C Run-Time, w tym przy użyciu biblioteki debugowania CRT, makr do raportowania, różnic między `malloc` i `_malloc_dbg` , pisania funkcji punktów zaczepienia debugowania oraz sterty debugowania CRT.