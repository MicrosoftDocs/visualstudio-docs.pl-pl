---
title: Debugowanie kodu natywnego | Dokumentacja firmy Microsoft
ms.date: 04/11/2017
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging native code
- debugging [C++], native code
- debugging [Visual Studio], native code
- native code, debugging
ms.assetid: d94eee90-7e0d-4cac-88c1-9831030daa5e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 59811e522268b7a9cb3993add76d2ace8dc3aada
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685498"
---
# <a name="debugging-native-code"></a>Debugowanie kodu natywnego
Sekcji omówiono niektóre typowe problemy z debugowania i technik dla natywnych aplikacji. Technik opisanych w tej sekcji są techniki wysokiego poziomu. Mechanika przy użyciu debugera programu Visual Studio, można zobaczyć [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)).

## <a name="in-this-section"></a>W tej sekcji
 [Instrukcje: Debugowanie zoptymalizowanego kodu](../debugger/how-to-debug-optimized-code.md) zapewnia wskazówki dotyczące debugowania zoptymalizowanego kodu, w szczególności, dlaczego należy debugować niezoptymalizowanym wersję programu domyślne ustawienia pozycji Optymalizacja konfiguracji Debug i Release i porady dla wyszukiwania, tylko błędy pojawiają się w zoptymalizowanym kodzie (włączenie funkcji optymalizacji w konfiguracji kompilacji debugowania).

 [DebugBreak i __debugbreak](../debugger/debugbreak-and-debugbreak.md) opisuje Win32 `DebugBreak` funkcji i Link do jego temat referencyjny w zestawie SDK platformy. Opisano również `__debugbreak` wewnętrzne.

 [Potwierdzenia C/C++](../debugger/c-cpp-assertions.md) w tym artykule omówiono instrukcji potwierdzania, jak to działa, zalety korzystania z nich (połowowe błędy logiczne, sprawdzanie wyników operacji i testowanie warunki błędu), ich interakcji z `_DEBUG`oraz typy potwierdzenia w obsługiwane [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

 [Instrukcje: Debugowanie kodu zestawu wbudowanego](../debugger/how-to-debug-inline-assembly-code.md) zawiera krótkie instrukcje na temat korzystania z okna dezasemblacji Aby wyświetlić instrukcje zestawu i z okna rejestrów, aby wyświetlić zawartość rejestru i zawiera łącza do tematów dotyczących tych oknach.

 [Techniki testowania MFC](../debugger/mfc-debugging-techniques.md) podano łącza do debugowania programów MFC, łącznie z: afxdebugbreak —, TRACE — makro, wykrywanie pamięci przecieki w MFC, MFC, asercje i zmniejszenie rozmiaru debugowania MFC kompilacji.

 [Techniki testowania CRT](../debugger/crt-debugging-techniques.md) podano łącza do debugowania dla biblioteki wykonawczej C, w tym o korzystaniu z biblioteki debugowania CRT, makra raportowania, różnice między funkcji malloc i _malloc_dbg, pisanie debugowanie funkcji punktów zaczepienia i sterty debugowania CRT.

 [Debugowanie natywne kodu — często zadawane pytania](../debugger/debugging-native-code-faqs.md) zawiera odpowiedzi na często zadawane pytania dotyczące debugowania programów Visual C++

 [COM i debugowanie ActiveX](../debugger/com-and-activex-debugging.md) zawiera informacje na temat debugowania aplikacji modelu COM i ActiveX, w tym narzędzi można użyć dla modelu COM i debugowanie ActiveX.

 [Instrukcje: Możliwe jest debugowanie kodu wprowadzony](../debugger/how-to-debug-injected-code.md) znajdują się wskazówki dotyczące debugowania kodu, który używa atrybutów. Instrukcje zawierają włączanie adnotacji źródła, jak wyświetlić wprowadzonego kodu i sposób wyświetlić kod dezasemblacji w bieżącym punkcie Wykonywanie.

 [Przewodnik: Debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md) w tym artykule opisano sposób używania **zadań równoległych** i **stosów równoległych** narzędzia systemu windows do debugowania aplikacji równoległej.

## <a name="related-sections"></a>Sekcje pokrewne
 [Typy projektów w usłudze Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md) zawiera łącza do tematów opisujących sposób debugowania natywnego projektu typów, utworzone przez Szablony projektów Visual C++.

 [Debugowanie projektów DLL](../debugger/debugging-dll-projects.md) zawiera informacje na temat debugowania bibliotek DLL macierzystych i zarządzanych.

 [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md) zawiera łącza do większych sekcji dokumentacji debugowania. Informacje dotyczące nowości w debugerze, ustawienia i przygotowania, punkty przerwania, obsługa wyjątków, Edytuj i Kontynuuj, debugowanie kodu zarządzanego, debugowanie kodu natywnego, debugowanie SQL i odwołania interfejsu użytkownika.

## <a name="see-also"></a>Zobacz też
 [Zabezpieczenia debugera](../debugger/debugger-security.md) [debugowania w programie Visual Studio](../debugger/index.md)