---
title: 'CA1900: Pola typu wartości powinny być przenośne | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 35bdef10d63f79c3d1ff649a486a708c34b28078
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2019
ms.locfileid: "58355051"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: Pola typu wartości powinny być przenośne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [CA1900: Pola typu wartości powinny być przenośne](https://docs.microsoft.com/visualstudio/code-quality/ca1900-value-type-fields-should-be-portable) w witrynie docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|ValueTypeFieldsShouldBePortable|  
|CheckId|CA1900|  
|Kategoria|Microsoft.Portability|  
|Zmiana kluczowa|Przerywanie — Jeśli pola są widoczne poza zestawem.<br /><br /> Bez podziału — Jeśli pole nie jest widoczna spoza zestawu.|  
  
## <a name="cause"></a>Przyczyna  
 Ta reguła sprawdza, czy struktury, które są zadeklarowane za pomocą jawnego układu, zostaną prawidłowo wyrównane podczas przekazywania do kodu niezarządzanego w 64-bitowych systemach operacyjnych. IA-64 nie zezwala na dostępów do niewyrównanych pamięci i proces ulegnie awarii, jeśli to naruszenie nie został rozwiązany.  
  
## <a name="rule-description"></a>Opis reguły  
 Struktury, które mają jawne układ, który zawiera niewyrównane pola powodują awarię na 64-bitowych systemach operacyjnych.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Wszystkie pola, które są mniejsze niż 8 bajtów musi mieć wartość przesunięcia, które są wielokrotnością ich rozmiar i pola, które są 8 bajtów lub więcej musi mieć przesunięcia, których to wielokrotność liczby 8. Innym rozwiązaniem jest użycie `LayoutKind.Sequential` zamiast `LayoutKind.Explicit`, jeśli jest to uzasadnione.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 To ostrzeżenie powinno być pomijane, tylko wtedy, gdy wystąpi błąd.
