---
title: 'DA0029: Nieobsługiwana wersja środowiska CLR | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 16782fcf3c8f859edd8363c43741f598d5929188
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55007022"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: Nieobsługiwana wersja środowiska CLR

|||  
|-|-|  
|Identyfikator reguły|DA0029|  
|Kategoria|Użycie narzędzia profilowania|  
|Metoda profilowania|Profilowanie z wiersza polecenia|  
|Komunikat|Podczas zbierania Wykryto nieobsługiwaną wersję środowiska CLR. Symbole zarządzane mogą nie być rozpoznawane poprawnie.|  
|Typ reguły|Informacje.|  

## <a name="cause"></a>Przyczyna  
 Chcesz profilować aplikację, która używa [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] nie jest obsługiwana przez narzędzia profilowania.  

## <a name="rule-description"></a>Opis reguły  
 To ostrzeżenie występuje, ponieważ narzędzia profilowania nie będzie można rozwiązać symbole dla kodu zarządzanego w aplikacji. Narzędzia profilowania nie można rozpoznać symbole kodu zarządzanego dla aplikacji, które są uruchomione [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)].  

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Brak.