---
title: Zapoznanie z alokacją pamięci i danych o okresie istnienia obiektu wartościami | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools, .NET memory method
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 463bb6510e304de8d9068e1c8d133c4ab331ea4f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54978675"
---
# <a name="understand-memory-allocation-and-object-lifetime-data-values"></a>Omówienie pamięci alokacji i obiekt okresu istnienia wartości danych

*Alokacji pamięci .NET* profilowanie metody [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profiling Tools umożliwia zbieranie informacji dotyczących rozmiaru i liczby obiektów, które zostały utworzone w alokacji lub zniszczyć wyrzucania elementów bezużytecznych i dodatkowe informacje na temat funkcji *stos wywołań* wystąpienia zdarzenia. A *stos wywołań* jest dynamiczne struktury, która przechowuje informacje dotyczące funkcji, które są wykonywane na procesorze.

Profiler pamięci przerywa działanie procesora komputera na każdej alokacji obiekt .NET Framework w profilowanej aplikacji. Jeśli są zbierane również informacje o okresie istnienia obiektu, profiler przerywa działanie procesora po każdym zdarzeniu wyrzucania elementów bezużytecznych w środowisku .NET Framework. Dane są agregowane dla każdej funkcji profilowanych i dla poszczególnych typów obiektu.

## <a name="allocation-data"></a>Dane alokacji

Gdy wystąpi zdarzenie .memory, całkowitej liczby i rozmiarów obiekty przydzielone lub zniszczone pamięci są zwiększane.

Gdy wystąpi zdarzenie alokacji .memory, program profilujący zwiększa liczby próbek dla każdej funkcji na stosie wywołań. Podczas zbierania danych tylko jednej funkcji — na stosie wywołań jest aktualnie wykonuje kod w jego treści funkcji. Innych funkcji na stosie są elementów nadrzędnych w hierarchii wywołań funkcji, które oczekują na funkcje, które jest wywoływana w celu zwrócenia.

- Dla zdarzenia alokacji, zwiększa profiler *wyłączne* liczba funkcji, która jest w trakcie wykonywania instrukcji próbek. Ponieważ próbek wyłącznych wchodzi w skład całości (*włącznie*) przykłady funkcji liczność próbki włączne aktualnie aktywnych funkcji również jest zwiększany.

- Program profilujący zwiększa liczność próbki włączne wszystkich funkcji w stosie wywołań.

## <a name="lifetime-data"></a>Danych o okresie istnienia

Moduł odśmiecania pamięci środowiska .NET Framework zarządza alokacją i zwolnieniem pamięci dla aplikacji. W celu zoptymalizowania wydajności moduł zbierający elementy bezużyteczne, zarządzanego stosu jest podzielony na trzy generacje: 0, 1 i 2. Moduł odśmiecania pamięci w czasie wykonywania zapisuje nowe obiekty w generacji 0. Obiekty, które przeżyły kolekcje są promowane i przechowywane w generacji 1 i 2.

Moduł odśmiecania pamięci odzyskuje pamięć, cofnięcie przydziału całego generacji obiektów. Dla obiektów utworzonych w profilowanej aplikacji widok okresu istnienia obiektu przedstawia liczbę i rozmiar obiektów oraz jego generacji, kiedy są odzyskiwane.