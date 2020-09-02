---
title: 'DA0004: duże użycie procesora | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a0e14a7400b937c56c2aac49a43d1d59cf96eba0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158694"
---
# <a name="da0004-high-processor-usage"></a>DA0004: Znaczące użycie procesora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikator reguły | DA0004 |  
| Kategoria | Użycie narzędzia profilowania |  
| Metody profilowania | Próbkowanie Instrumentacji |  
| Komunikat | Użycie procesora jest spójne powyżej 75%. Rozważ użycie trybu próbkowania dla aplikacji powiązanych z PROCESORem. |  
| Typ reguły | Informacje |  
  
 Podczas profilowania przy użyciu metod pobierania próbek, pamięci .NET lub rywalizacji o zasoby należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.  
  
## <a name="cause"></a>Przyczyna  
 Wykorzystanie procesora (CPU) było znacznie wysokie w danych profilowania zebranych za pomocą metody instrumentacji. Rozważ użycie metody profilowania próbkowania podczas profilowania aplikacji powiązanej z PROCESORem.  
  
## <a name="rule-description"></a>Opis reguły  
 Podczas tego przebiegu profilowania procesor (lub procesory) był stale bardzo zajęty. Wysokie wykorzystanie procesora CPU może wskazywać na aplikację powiązaną z PROCESORem. Profile Instrumentacji zwykle nie są najbardziej efektywne, aby zbadać scenariusze użycia procesora CPU. Próbkowanie jest zwykle wydajniejsze w przypadku profilowania aplikacji, które poświęcają wiele czasu na wykonywanie instrukcji dotyczących procesora.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Rozważ ponowne profilowanie aplikacji przy użyciu metody próbkowania zamiast metody instrumentacji, chyba że wymagane są chronometraże funkcji lub jesteś bardziej interesujący w zrozumieniu danych wejściowych/wyjściowych niż wąskie gardła procesora.
