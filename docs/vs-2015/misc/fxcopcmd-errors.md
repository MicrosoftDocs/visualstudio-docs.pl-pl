---
title: Błędy plik FxCopCmd | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64787276"
---
# <a name="fxcopcmd-errors"></a>FxCopCmd — Błędy
Plik FxCopCmd nie uwzględnia wszystkich błędów jako krytycznych. Jeśli plik FxCopCmd ma wystarczające informacje do przeprowadzenia analizy częściowej, wykonuje analizę i zgłasza błędy, które wystąpiły. Kod błędu, który jest 32-bitową liczbą całkowitą, zawiera bitową kombinację wartości liczbowych, które odnoszą się do błędów.  
  
 W poniższej tabeli opisano kody błędów zwracane przez plik FxCopCmd:  
  
|Błąd|Wartość liczbowa|  
|-----------|-------------------|  
|Brak błędów|0x0|  
|Błąd analizy|0x1|  
|Wyjątki reguł|0x2|  
|Błąd ładowania projektu|0x4|  
|Błąd ładowania zestawu|0x8|  
|Błąd ładowania biblioteki reguł|0x10|  
|Zaimportuj błąd ładowania raportu|0x20|  
|Błąd danych wyjściowych|0x40|  
|Błąd przełączania wiersza polecenia|0x80|  
|Błąd inicjowania|0x100|  
|Błąd odwołań do zestawu|0x200|  
|BuildBreakingMessage|0x400|  
|Nieznany błąd|0x1000000|  
  
 Błąd analizy jest zwracany w przypadku błędów krytycznych. Oznacza to, że analiza nie mogła zostać ukończona. Jeśli ma to zastosowanie, kod błędu zawiera również podstawową przyczynę błędu krytycznego. Poniższe warunki generują błędy krytyczne:  
  
- Nie można wykonać analizy z powodu niewystarczających danych wejściowych.  
  
- Analiza zgłosiła wyjątek, który nie jest obsługiwany przez plik FxCopCmd.  
  
- Nie można znaleźć określonego pliku projektu lub jest on uszkodzony.  
  
- Nie określono opcji Output lub nie można zapisać pliku.  
  
    > [!NOTE]
    > Kod powrotu plik FxCopCmd "błąd odwołania do zestawu" 0x200 przez samego siebie jest ostrzeżeniem, a nie błędem. Ten kod powrotny wskazuje, że nie znaleziono brakujących odwołań pośrednich, ale plik FxCopCmd je obsłużyć. Jest to ostrzeżenie, że istnieje możliwość, że niektóre wyniki analizy mogły zostać naruszone. Rozważmy "błąd odwołania do zestawu" jako błąd, gdy jest on połączony z innym kodem zwrotnym.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy aplikacji analizy kodu](../code-quality/code-analysis-application-errors.md)