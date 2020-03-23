---
title: Widok linii | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 25dbb0beb600f7f043ae006e09ac48b9b64d613b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773984"
---
# <a name="lines-view"></a>Widok linii
Widok Linie jest dostępny tylko dla danych profilera, które zostały zebrane przy użyciu metody próbkowania. Widok nie jest dostępny dla danych, które zostały zebrane przy użyciu instrumentacji.

 W przypadku danych profilu próbkowania widok Linie identyfikuje instrukcję w funkcji, która była wykonywana bezpośrednio podczas pobierania próbki. W przypadku danych pamięci .NET widok Linie identyfikuje instrukcje, które przydzielają pamięć.

 W pliku źródłowym instrukcja może obejmować więcej niż jeden wiersz w pliku źródłowym, a pojedynczy wiersz może zawierać więcej niż jedną instrukcję.

 Oświadczenie jest identyfikowane przez następujące:

- Plik źródłowy zawierający instrukcję funkcji.

- Funkcja, która zawiera instrukcję.

- Wiersz źródłowy, od którego rozpoczyna się instrukcja.

- Znak w wierszu źródłowym, od którego rozpoczyna się instrukcja.

- Wiersz źródłowy, w którym kończy się instrukcja.

- Znak w wierszu źródłowym, w którym kończy się instrukcja.

## <a name="see-also"></a>Zobacz też
- [Widok linii](../profiling/lines-view-sampling-data.md)
- [Widok linii — próbkowanie](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [Widok linii](../profiling/lines-view-contention-data.md)
