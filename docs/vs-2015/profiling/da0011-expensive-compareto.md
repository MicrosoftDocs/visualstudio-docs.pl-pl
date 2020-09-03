---
title: 'DA0011: drogie CompareTo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a66242554de28ab45cc797d523ea7b5a967e9e5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542977"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Kosztowna funkcja CompareTo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [DA0011: kosztowne CompareTo](/visualstudio/profiling/da0011-expensive-compareto).  
  
|Element|Wartość|  
|-|-|  
|Identyfikator reguły|DA0011|  
|Kategoria|Użycie .NET Framework|  
|Metody profilowania|Próbkowanie<br /><br /> Pamięć platformy .NET|  
|Komunikat|Funkcje CompareTo powinny być tanie i nie mogą przydzielać żadnej pamięci. Zmniejsz złożoność funkcji CompareTo, jeśli jest to możliwe.|  
|Typ reguły|Ostrzeżenie|  
  
## <a name="cause"></a>Przyczyna  
 Metoda CompareTo typu jest kosztowna lub przydziela pamięć.  
  
## <a name="rule-description"></a>Opis reguły  
 Metody CompareTo powinny być wydajne i nie powinny przydzielić pamięci.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Zmniejsz złożoność metody CompareTo.
