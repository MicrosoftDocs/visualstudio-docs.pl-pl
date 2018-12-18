---
title: 'DA0004: Znaczące wykorzystanie czasu procesora | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a942a26bb4cd8ccca94fd442250fe8a239cba4ed
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764027"
---
# <a name="da0004-high-processor-usage"></a>DA0004: Znaczące wykorzystanie czasu procesora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikator reguły | DA0004 |  
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




