---
title: Zapoznanie z alokacją pamięci i danych o okresie istnienia obiektu wartościami | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools, .NET memory method
ms.assetid: a22445b3-39a6-4919-8506-2b5b0ceaf77e
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 816f750148cc30de86fc116f80f64b218b4699d0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60069748"
---
# <a name="understanding-memory-allocation-and-object-lifetime-data-values"></a>Zapoznanie z alokacją pamięci i wartościami danych o okresie istnienia obiektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Alokacji pamięci .NET* profilowanie metody [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profiling Tools umożliwia zbieranie informacji dotyczących rozmiaru i liczby obiektów, które zostały utworzone w alokacji lub zniszczyć wyrzucania elementów bezużytecznych i dodatkowe informacje na temat funkcji *stos wywołań* wystąpienia zdarzenia. A *stos wywołań* jest dynamiczne struktury, która przechowuje informacje dotyczące funkcji, które są wykonywane na procesorze.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Profiler pamięci przerywa działanie procesora komputera na każdej alokacji obiekt .NET Framework w profilowanej aplikacji. Jeśli są zbierane również informacje o okresie istnienia obiektu, profiler przerywa działanie procesora po każdym zdarzeniu wyrzucania elementów bezużytecznych w środowisku .NET Framework. Dane są agregowane dla każdej funkcji profilowanych i dla poszczególnych typów obiektu.  
  
## <a name="allocation-data"></a>Dane alokacji  
 Gdy wystąpi zdarzenie .memory, całkowitej liczby i rozmiarów obiekty przydzielone lub zniszczone pamięci są zwiększane.  
  
 Gdy wystąpi zdarzenie alokacji .memory, program profilujący zwiększa liczby próbek dla każdej funkcji na stosie wywołań. Podczas zbierania danych tylko jednej funkcji — na stosie wywołań jest aktualnie wykonuje kod w jego treści funkcji. Innych funkcji na stosie są elementów nadrzędnych w hierarchii wywołań funkcji, które oczekują na funkcje, które jest wywoływana w celu zwrócenia.  
  
- Dla zdarzenia alokacji, zwiększa profiler *wyłączne* liczba funkcji, która jest w trakcie wykonywania instrukcji próbek. Ponieważ próbek wyłącznych wchodzi w skład całości (*włącznie*) przykłady funkcji liczność próbki włączne aktualnie aktywnych funkcji również jest zwiększany.  
  
- Program profilujący zwiększa liczność próbki włączne wszystkich funkcji w stosie wywołań.  
  
## <a name="lifetime-data"></a>Danych o okresie istnienia  
 Moduł odśmiecania pamięci środowiska .NET Framework zarządza alokacją i zwolnieniem pamięci dla aplikacji. W celu zoptymalizowania wydajności moduł zbierający elementy bezużyteczne, zarządzanego stosu jest podzielony na trzy generacje: 0, 1 i 2. Moduł odśmiecania pamięci w czasie wykonywania zapisuje nowe obiekty w generacji 0. Obiekty, które przeżyły kolekcje są promowane i przechowywane w generacji 1 i 2.  
  
 Moduł odśmiecania pamięci odzyskuje pamięć, cofnięcie przydziału całego generacji obiektów. Dla obiektów utworzonych w profilowanej aplikacji widok okresu istnienia obiektu przedstawia liczbę i rozmiar obiektów oraz jego generacji, kiedy są odzyskiwane.
