---
title: błędy FxCopCmd
ms.date: 10/19/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- FxCopCmd errors
ms.author: gewarren
author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d723065e224058b7e269299aad2900f97a1425d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62936650"
---
# <a name="fxcopcmd-tool-errors"></a>Fxcopcmd — błędy narzędzi

Fxcopcmd — nie należy wziąć pod uwagę wszystkie błędy jako krytyczny. Jeśli FxCopCmd ma wystarczające informacje, aby przeprowadzić analizę częściowe, wykonuje błędów analizy i raporty, które wystąpiły. Kod błędu, który jest 32-bitową liczbę całkowitą, zawiera bitowa kombinacja wartości liczbowe, które odnoszą się do błędów.

W poniższej tabeli opisano kody błędów zwracane przez polecenia FxCopCmd:

|Błąd|Wartość liczbowa|
|-----------|-------------------|
|Brak błędów|0x0|
|Błąd analizy|0x1|
|Wyjątki od reguły|0x2|
|Błąd ładowania projektu|0x4|
|Błąd ładowania zestawu|0x8|
|Błąd ładowania biblioteki reguły|0x10|
|Błąd ładowania raportu importu|0x20|
|Błąd danych wyjściowych|0x40|
|Błąd przełącznik wiersza polecenia|0x80|
|Błąd podczas inicjowania|0x100|
|Błąd odwołania do zestawu|0x200|
|BuildBreakingMessage|0x400|
|Nieznany błąd|0x1000000|

**Błąd analizy** jest zwracany w przypadku błędów krytycznych. Wskazuje, że nie można wykonać analizy. Jeśli ma to zastosowanie, kod błędu zawiera także podstawową przyczyną błędu krytycznego. Następujące warunki generować błędy krytyczne:

- Nie można wykonać analizy ze względu na niewystarczające dane wejściowe.

- Analiza zgłosiła wyjątek, który nie jest obsługiwany przez FxCopCmd.

- Plik projektu nie można odnaleźć lub jest uszkodzony.

- Nie określono opcji output lub nie można zapisać pliku.

> [!NOTE]
> Kod powrotny polecenia FxCopCmd **błąd odwołuje się zestaw** 0x200 przez siebie to ostrzeżenie, a nie błąd. Ten kod powrotny wskazuje, że zawierają odwołania pośrednie niejedna FxCopCmd mógł je obsłużyć. Ostrzeżenie oznacza, że istnieje możliwość, że niektóre wyniki analizy mogą zabezpieczenia mogły zostać naruszone. Traktuj **błąd odwołuje się zestaw** jako błąd, w połączeniu z innymi kod powrotny.

## <a name="see-also"></a>Zobacz także

- [Błędy zgłaszane przez aplikację do analizy kodu](../code-quality/code-analysis-application-errors.md)