---
title: Informacje o alokacji pamięci i wartościach danych o okresie istnienia obiektu | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145443"
---
# <a name="understanding-memory-allocation-and-object-lifetime-data-values"></a>Zapoznanie z alokacją pamięci i wartościami danych o okresie istnienia obiektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metoda profilowania *alokacji pamięci .net* [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzia profilowania zbiera informacje o rozmiarze i liczbie obiektów, które zostały utworzone w alokacji lub zniszczone w wyrzucaniu elementów bezużytecznych, oraz dodatkowe informacje o *stosie wywołań* funkcji po wystąpieniu zdarzenia. *Stos wywołań* jest strukturą dynamiczną, która przechowuje informacje o funkcjach wykonywanych na procesorze.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Profiler pamięci przerywa procesor komputera przy każdej alokacji obiektu .NET Framework w profilowanej aplikacji. Jeśli są zbierane również informacje o okresie istnienia obiektu, profiler przerywa działanie procesora po każdym zdarzeniu wyrzucania elementów bezużytecznych w środowisku .NET Framework. Dane są agregowane dla każdej profilowanej funkcji i dla każdego typu obiektu.  
  
## <a name="allocation-data"></a>Dane alokacji  
 Gdy wystąpi zdarzenie. Memory, Łączna liczba i rozmiary przydzieloną lub zniszczonych obiektów pamięci są zwiększane.  
  
 Gdy wystąpi zdarzenie alokacji pamięci, profiler zwiększa liczbę próbek dla każdej funkcji na stosie wywołań. Gdy dane są zbierane, tylko jedna funkcja na stosie wywołań wykonuje obecnie kod w jego treści funkcji. Inne funkcje na stosie są elementami nadrzędnymi w hierarchii wywołań funkcji, które oczekują na zwrócenie przez te funkcje.  
  
- W przypadku zdarzenia alokacji Profiler zwiększa liczbę *wyłącznych* próbek funkcji, która wykonuje obecnie instrukcje. Ze względu na to, że próbka wyłączna jest również częścią łącznej (*włącznie*) próbek funkcji, jest również zwiększana liczba włączonych próbek dla obecnie aktywnej funkcji.  
  
- Profiler zwiększa liczbę włączonych próbek wszystkich innych funkcji na stosie wywołań.  
  
## <a name="lifetime-data"></a>Dane okresu istnienia  
 Moduł wyrzucania elementów bezużytecznych .NET Framework zarządza alokacją i ilością pamięci dla aplikacji. Aby zoptymalizować wydajność modułu wyrzucania elementów bezużytecznych, sterta zarządzana jest dzielona na trzy generacje: 0, 1 i 2. Moduł zbierający elementy bezużyteczne w czasie wykonywania przechowuje nowe obiekty w generacji 0. Obiekty, które przeżyły kolekcje, są promowane i przechowywane w generacjach 1 i 2.  
  
 Moduł zbierający elementy bezużyteczne odzyskuje pamięć przez cofnięcie przydziału całej generacji obiektów. W przypadku obiektów tworzonych przez profilowaną aplikację widok okres istnienia obiektu wyświetla liczbę i rozmiar obiektów oraz generację, gdy są odzyskiwane.
