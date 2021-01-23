---
title: Widok wierszy | Microsoft Docs
description: Dowiedz się, jak widok linie jest dostępny tylko dla danych profilera zebranych za pomocą metody próbkowania.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.lines
helpviewer_keywords:
- profiling tools reports, Line view
- profiling tools, Line view
- Lines view
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ac0d7785071e5f2928e7eabb4a29b1655b42c5ad
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721297"
---
# <a name="lines-view"></a>Widok linii
Widok linie jest dostępny tylko dla danych profilera, które zostały zebrane przy użyciu metody próbkowania. Widok nie jest dostępny dla danych, które zostały zebrane przy użyciu instrumentacji.

 W przypadku danych profilu próbkowania widok wierszy identyfikuje instrukcję w funkcji, która była wykonywana bezpośrednio podczas zbierania próbki. W przypadku danych pamięci .NET Widok wiersze identyfikuje instrukcje, które przydzielą pamięć.

 W pliku źródłowym instrukcja może obejmować więcej niż jeden wiersz w pliku źródłowym, a pojedynczy wiersz może zawierać więcej niż jedną instrukcję.

 Instrukcja jest identyfikowana przez następujące elementy:

- Plik źródłowy, który zawiera instrukcję Function.

- Funkcja, która zawiera instrukcję.

- Wiersz źródłowy, w którym rozpocznie się wykonywanie instrukcji.

- Znak w wierszu źródłowym, w którym rozpocznie się wykonywanie instrukcji.

- Wiersz źródłowy, w którym zostanie zakończona instrukcja.

- Znak w wierszu źródłowym, w którym następuje zakończenie instrukcji.

## <a name="see-also"></a>Zobacz także
- [Widok linii](../profiling/lines-view-sampling-data.md)
- [Widok linii — próbkowanie](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [Widok linii](../profiling/lines-view-contention-data.md)
