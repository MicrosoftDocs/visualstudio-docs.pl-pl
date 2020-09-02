---
title: 'DA0003: wiele przykładów jądra | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ad9a0671595d4628932ff4f2db41a137e060c4d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158711"
---
# <a name="da0003-many-kernel-samples"></a>DA0003: Wiele przykładów jądra
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikator reguły | DA0003 |  
| Kategoria | Użycie narzędzia profilowania |  
| Metody profilowania | Próbkowanie |  
| Komunikat | Masz dużą część przykładów w trybie jądra. Może to wskazywać na dużą liczbę operacji we/wy lub dużą Częstotliwość przełączania kontekstu. Rozważ ponowne profilowania aplikacji przy użyciu trybu Instrumentacji. |  
| Typ reguły | Informacje |  
  
## <a name="cause"></a>Przyczyna  
 Znaczna część przykładów stosu wywołań, które zostały zebrane dla aplikacji, została uruchomiona w trybie jądra. Rozważ Profilowanie aplikacji przy użyciu innej metody profilowania.  
  
## <a name="rule-description"></a>Opis reguły  
 W systemie Windows kod może być wykonywany w trybie jądra lub w trybie użytkownika. (Tryb jądra jest również nazywany trybem uprzywilejowanym). Tylko kod systemu niskiego poziomu, taki jak sterowniki urządzeń, działa w trybie jądra. Aplikacja w trybie użytkownika może przejść do trybu jądra w celu wykonania operacji we/wy, oczekiwania na elementy pierwotne synchronizacji wątków lub procesów lub wywołania systemowego.  
  
 Próbkowanie jest najbardziej efektywne podczas profilowania aplikacji, które spędzają większość czasu pracy w trybie użytkownika. Liczba próbek zebranych podczas wykonywania aplikacji w trybie jądra może wskazywać częste operacje we/wy lub mogą wskazywać, że występują przełączenia kontekstu. Żadnej z tych operacji nie można zbadać przy użyciu metody próbkowania. Jeśli są pobierane zbyt wiele próbek trybu jądra, dane próbkowania nie mogą zawierać wystarczającej liczby próbek trybu użytkownika do statystycznego znaczenia.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Rozważ ponowne profilowania aplikacji przy użyciu jednej z następujących opcji:  
  
- Profiluj przy użyciu metody instrumentacji.  
  
- Zwiększ częstotliwość próbkowania, aby próbować zebrać więcej próbek w trybie użytkownika.
