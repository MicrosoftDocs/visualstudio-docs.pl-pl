---
title: 'DA0004: Wykorzystanie procesora | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54762527"
---
# <a name="da0004-high-processor-usage"></a>DA0004: Wykorzystanie procesora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rule Id|DA0004|  
| Kategoria | Profilowanie użycia narzędzia |  
| Profilowanie metody | Próbkowanie Instrumentacji |  
| Komunikat | Użycie procesora jest stale powyżej 75%. Należy rozważyć użycie trybu próbkowania dla aplikacji zależne od Procesora CPU. |  
| Typ reguły | Informacji |  
  
 Podczas profilowania za pomocą próbkowania pamięci platformy .NET i metod rywalizacji zasobów musi zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  
  
## <a name="cause"></a>Przyczyna  
 Użycie procesora (CPU) został znacznie wysoko w danych, które zostały zebrane przy użyciu metody Instrumentacji profilowania. Należy wziąć pod uwagę przy użyciu metody próbkowania, metoda profilowania, gdy profilowanie Procesora powiązana aplikacja.  
  
## <a name="rule-description"></a>Opis reguły  
 Podczas tego uruchomienia profilowania procesora (czy procesory) były spójne bardzo zajęty. Wysokie wykorzystanie procesora CPU można wskazać aplikacji zależne od Procesora CPU. Instrumentowane profile nie są zwykle najbardziej efektywny sposób Badaj scenariusze użycia procesora CPU. Próbkowanie jest zazwyczaj bardziej efektywne w przypadku profilowania aplikacji, które spędzają większość czasu wykonywania instrukcji na procesorze.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Należy wziąć pod uwagę profilowania aplikację ponownie przy użyciu metody próbkowania zamiast metody instrumentacji, o ile nie wymagają funkcji chronometrażu lub interesuje Cię bardziej opis wejścia/wyjścia niż wąskich gardeł.
