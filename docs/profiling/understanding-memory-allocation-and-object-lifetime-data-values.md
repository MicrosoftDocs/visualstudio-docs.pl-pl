---
title: Opis alokacji pamięci & wartości danych okresu istnienia obiektu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools, .NET memory method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6eec0c4bc5fc27e07bc04a8445ca14ce538ac376
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74780003"
---
# <a name="understand-memory-allocation-and-object-lifetime-data-values"></a>Opis alokacji pamięci i wartości danych okresu istnienia obiektów

Metoda *profilowania alokacji pamięci .NET* [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi profilowania zbiera informacje o rozmiarze i liczbie obiektów, które zostały utworzone w alokacji lub zniszczone w wyrzucaniu elementów bezużytecznych i dodatkowe informacje o *stosie wywołań* funkcji, gdy wystąpiło zdarzenie. *Stos wywołań* to struktura dynamiczna, która przechowuje informacje o funkcjach wykonywanych na procesorze.

Profiler pamięci przerywa procesor komputera przy każdej alokacji obiektu .NET Framework w profilowanej aplikacji. Jeśli są zbierane również informacje o okresie istnienia obiektu, profiler przerywa działanie procesora po każdym zdarzeniu wyrzucania elementów bezużytecznych w środowisku .NET Framework. Dane są agregowane dla każdej funkcji profilowane i dla każdego typu obiektu.

## <a name="allocation-data"></a>Dane alokacji

Po wystąpieniu zdarzenia .memory całkowita liczba i rozmiary obiektów przydzielonej lub zniszczonej pamięci są zwiększane.

Gdy wystąpi zdarzenie alokacji .memory, profiler zwiększa liczbę próbek dla każdej funkcji na stosie wywołań. Gdy dane są zbierane, tylko jedna funkcja na stosie wywołań jest obecnie wykonywanie kodu w treści funkcji. Inne funkcje na stosie są elementów ami w hierarchii wywołań funkcji, które oczekują na funkcje, które powołano do zwrócenia.

- W przypadku zdarzenia alokacji profiler zwiększa *liczbę próbek wyłącznych* funkcji, która jest obecnie wykonywania jego instrukcji. Ponieważ próbka wyłączna jest również częścią całkowitych *(włącznie)* próbek funkcji, zwiększa się również liczba próbek włącznie aktualnie aktywnej funkcji.

- Profiler zwiększa włącznie liczba próbek wszystkich innych funkcji na stosie wywołań.

## <a name="lifetime-data"></a>Dane dotyczące okresu istnienia

Moduł zbierający elementy bezużyteczne programu .NET Framework zarządza alokacją i wydaniem pamięci dla aplikacji. Aby zoptymalizować wydajność modułu zbierającego elementy bezużyteczne, zarządzany stos jest podzielony na trzy generacje: 0, 1 i 2. Moduł zbierający elementy bezużyteczne w czasie wykonywania przechowuje nowe obiekty w generacji 0. Obiekty, które przetrwają kolekcje są promowane i przechowywane w pokoleniach 1 i 2.

Moduł zbierający elementy bezużyteczne odzyskuje pamięć przez rozdzielenie alokacji całej generacji obiektów. W przypadku obiektów utworzonych przez profilowane aplikacje w widoku Okres istnienia obiektu wyświetlana jest liczba i rozmiar obiektów oraz generowanie, gdy są one odzyskiwana.
