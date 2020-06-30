---
title: 'DA0010: drogie GetHashCode | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: af234cd130d06c2a76c5ddbc958a67eb064d9128
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547579"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: Kosztowna funkcja GetHashCode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [DA0010: kosztowne GetHashCode](/visualstudio/profiling/da0010-expensive-gethashcode).  

|Element|Wartość|  
|-|-|  
|Identyfikator reguły|DA0010|  
|Kategoria|Użycie .NET Framework|  
|Metody profilowania|Próbkowanie<br /><br /> Pamięć platformy .NET|  
|Komunikat|Funkcje GetHashCode powinny być tanie i nie mogą przydzielać żadnej pamięci. Zmniejsz złożoność funkcji kodu skrótu, jeśli jest to możliwe.|  
|Typ wiadomości|Ostrzeżenie|  
  
## <a name="cause"></a>Przyczyna  
 Wywołania metody GetHashCode typu są znaczną częścią danych profilowania lub metoda przydziela pamięć.  
  
## <a name="rule-description"></a>Opis reguły  
 Mieszanie jest techniką szybkiego lokalizowania określonego elementu w dużej kolekcji. Ponieważ tabele skrótów mogą być bardzo duże i muszą obsługiwać wysokie stawki dostępu, tabele skrótów powinny być niezwykle wydajne. Implikacje tego wymagania polega na tym, że metody GetHashCode w .NET Framework nie powinny przydzielić pamięci. Alokacja pamięci zwiększa obciążenie w module wyrzucania elementów bezużytecznych i uwidacznia metodę do potencjalnych opóźnień, jeśli konieczne jest uruchomienie wyrzucania elementów bezużytecznych w wyniku żądania alokacji.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Zmniejsz złożoność metody.
