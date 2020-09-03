---
title: DA0004 — duże użycie procesora | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e0ac8d8558ee73903898e920ed8174c73ea66c4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548177"
---
# <a name="da0004-high-processor-usage"></a>DA0004: Znaczące użycie procesora

|Element|Wartość|
|-|-|
|Identyfikator reguły|DA0004|
|Kategoria|Użycie narzędzia profilowania|
|Metody profilowania|Oprzyrządowanie<br /><br /> Próbkowanie|
|Komunikat|Użycie procesora jest spójne powyżej 75%. Rozważ użycie trybu próbkowania dla aplikacji powiązanych z PROCESORem.|
|Typ reguły|Informacje|

 Podczas profilowania przy użyciu metod pobierania próbek, pamięci .NET lub rywalizacji o zasoby należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="cause"></a>Przyczyna
 Użycie procesora (CPU) było wysokie w danych profilowania zebranych za pomocą metody instrumentacji. Rozważ użycie metody profilowania próbkowania podczas profilowania aplikacji powiązanej z PROCESORem.

## <a name="rule-description"></a>Opis reguły
 Podczas tego przebiegu profilowania procesor (lub procesory) był stale zajęty. Wysokie wykorzystanie procesora CPU może wskazywać na aplikację powiązaną z PROCESORem. Profile instrumentacji nie są najbardziej efektywne, aby zbadać scenariusze użycia procesora CPU. Próbkowanie jest wydajniejsze w przypadku profilowania aplikacji, które poświęcają wiele czasu na wykonywanie instrukcji dotyczących procesora.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Rozważ ponowne profilowanie aplikacji przy użyciu metody próbkowania zamiast metody instrumentacji, chyba że wymagane są chronometraże funkcji lub jesteś bardziej interesujący w zrozumieniu danych wejściowych/wyjściowych niż wąskie gardła procesora.
