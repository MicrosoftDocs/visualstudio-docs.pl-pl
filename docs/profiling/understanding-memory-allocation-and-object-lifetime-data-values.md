---
title: Alokacja pamięci & wartości danych okresu istnienia obiektu
description: Dowiedz się, jak Metoda profilowania alokacji pamięci .NET zbiera informacje o rozmiarze i liczbie obiektów, które zostały utworzone w alokacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools, .NET memory method
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2faabb8d37cdebf1bdd6c83d10356edc1ce78690
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921936"
---
# <a name="understand-memory-allocation-and-object-lifetime-data-values"></a>Opis alokacji pamięci i wartości danych okresu istnienia obiektu

Metoda profilowania *alokacji pamięci .net* [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania zbiera informacje o rozmiarze i liczbie obiektów, które zostały utworzone w alokacji lub zniszczone w wyrzucaniu elementów bezużytecznych, oraz dodatkowe informacje o *stosie wywołań* funkcji po wystąpieniu zdarzenia. *Stos wywołań* jest strukturą dynamiczną, która przechowuje informacje o funkcjach wykonywanych na procesorze.

Profiler pamięci przerywa procesor komputera przy każdej alokacji obiektu .NET Framework w profilowanej aplikacji. Jeśli są zbierane również informacje o okresie istnienia obiektu, profiler przerywa działanie procesora po każdym zdarzeniu wyrzucania elementów bezużytecznych w środowisku .NET Framework. Dane są agregowane dla każdej profilowanej funkcji i dla każdego typu obiektu.

## <a name="allocation-data"></a>Dane alokacji

Gdy wystąpi zdarzenie. Memory, Łączna liczba i rozmiary przydzieloną lub zniszczonych obiektów pamięci są zwiększane.

Gdy wystąpi zdarzenie alokacji pamięci, profiler zwiększa liczbę próbek dla każdej funkcji na stosie wywołań. Gdy dane są zbierane, tylko jedna funkcja na stosie wywołań wykonuje obecnie kod w jego treści funkcji. Inne funkcje na stosie są elementami nadrzędnymi w hierarchii wywołań funkcji, które oczekują na zwrócenie przez te funkcje.

- W przypadku zdarzenia alokacji Profiler zwiększa liczbę *wyłącznych* próbek funkcji, która wykonuje obecnie instrukcje. Ze względu na to, że próbka wyłączna jest również częścią łącznej (*włącznie*) próbek funkcji, jest również zwiększana liczba włączonych próbek dla obecnie aktywnej funkcji.

- Profiler zwiększa liczbę włączonych próbek wszystkich innych funkcji na stosie wywołań.

## <a name="lifetime-data"></a>Dane okresu istnienia

Moduł wyrzucania elementów bezużytecznych .NET Framework zarządza alokacją i ilością pamięci dla aplikacji. Aby zoptymalizować wydajność modułu wyrzucania elementów bezużytecznych, sterta zarządzana jest dzielona na trzy generacje: 0, 1 i 2. Moduł zbierający elementy bezużyteczne w czasie wykonywania przechowuje nowe obiekty w generacji 0. Obiekty, które przeżyły kolekcje, są promowane i przechowywane w generacjach 1 i 2.

Moduł zbierający elementy bezużyteczne odzyskuje pamięć przez cofnięcie przydziału całej generacji obiektów. W przypadku obiektów tworzonych przez profilowaną aplikację widok okres istnienia obiektu wyświetla liczbę i rozmiar obiektów oraz generację, gdy są odzyskiwane.
