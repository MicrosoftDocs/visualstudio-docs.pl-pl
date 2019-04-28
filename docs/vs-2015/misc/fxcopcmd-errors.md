---
title: Błędy FxCopCmd | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: 12
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3e0770654f564c57cf576666dcd9575f47d9ce1c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432291"
---
# <a name="fxcopcmd-errors"></a>FxCopCmd — Błędy
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
  
 Błąd analizy jest zwracane błędy krytyczne. Wskazuje, że nie można wykonać analizy. Jeśli ma to zastosowanie, kod błędu zawiera także podstawową przyczyną błędu krytycznego. Następujące warunki generować błędy krytyczne:  
  
- Analiza nie można wykonać spowodowane przez niewystarczające dane wejściowe.  
  
- Analiza zgłosiła wyjątek, który nie jest obsługiwany przez FxCopCmd.  
  
- Plik projektu nie można odnaleźć lub jest uszkodzony.  
  
- Nie określono opcji output lub nie można zapisać pliku.  
  
    > [!NOTE]
    > Fxcopcmd — kod powrotny "Odwołuje się zestaw błąd" 0x200 przez siebie to ostrzeżenie, a nie błąd. Ten kod powrotny wskazuje, znaleziono brakujące odwołania pośredniego, ale że FxCopCmd mógł je obsłużyć. Jest to ostrzeżenie, że istnieje możliwość, że niektóre wyniki analizy mogą zabezpieczenia mogły zostać naruszone. Należy wziąć pod uwagę kod powrotny "Odwołuje się zestaw błąd" jako błąd połączeniu z innymi kod powrotny.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy zgłaszane przez aplikację do analizy kodu](../code-quality/code-analysis-application-errors.md)