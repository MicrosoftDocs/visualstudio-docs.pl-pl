---
title: Debugowanie kodu natywnego | Microsoft Docs
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
ms.openlocfilehash: f98b99a31d9215d661879aa7fa52d4b671024496
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738165"
---
# <a name="debugging-native-code"></a>Debugowanie kodu natywnego
Sekcja dotyczy niektórych typowych problemów z debugowaniem i technik dla aplikacji natywnych. Techniki omówione w tej sekcji są technikami wysokiego poziomu. Aby Mechanics za pomocą debugera programu Visual Studio, zobacz [pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md)).

## <a name="in-this-section"></a>W tej sekcji
 [Instrukcje: debugowanie zoptymalizowanego kodu](../debugger/how-to-debug-optimized-code.md) Podaje porady dotyczące debugowania zoptymalizowanego kodu, w tym, dlaczego należy debugować niezoptymalizowaną wersję programu, domyślne ustawienia optymalizacji konfiguracji debugowania i wydania oraz porady dotyczące znajdowania błędów, które pojawiają się tylko w zoptymalizowanym kodzie (Włączanie Optymalizacja w konfiguracji kompilacji debugowania).

 [DebugBreak i __debugbreak](../debugger/debugbreak-and-debugbreak.md) Opisuje funkcję Win32 `DebugBreak` i zawiera łącze do jej tematu referencyjnego w zestawie SDK platformy. Opisuje również `__debugbreak` wewnętrznie.

 [C/C++ potwierdzenia](../debugger/c-cpp-assertions.md) W tym artykule omówiono instrukcje potwierdzania, sposób ich działania, korzyści wynikające z ich używania (przechwytywanie błędów logiki, sprawdzanie wyników operacji i testowanie warunków błędów), interakcje z `_DEBUG`ami i typy potwierdzeń, które są obsługiwane w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

 [Instrukcje: Debugowanie kodu zestawu wbudowanego](../debugger/how-to-debug-inline-assembly-code.md) Zawiera krótkie instrukcje dotyczące korzystania z okna demontażu w celu wyświetlenia instrukcji zestawu i okna rejestrów, aby wyświetlić zawartość rejestru i zawiera łącza do tematów dotyczących tych okien.

 [Techniki debugowania MFC](../debugger/mfc-debugging-techniques.md) Łącza do technik debugowania dla programów MFC, w tym: afxDebugBreak, makro śledzenia, Wykrywanie przecieków pamięci w MFC, potwierdzenia MFC i zmniejszanie rozmiaru kompilacji debugowania MFC.

 [Techniki debugowania CRT](../debugger/crt-debugging-techniques.md) Łączy się z technikami debugowania dla biblioteki wykonawczej C, w tym z użyciem biblioteki debugowania CRT, makr dla raportowania, różnic między funkcjami malloc i _malloc_dbg, pisania funkcji punktu zaczepienia debugowania i sterty debugowania CRT.

 [Debugowanie często zadawanych pytań dotyczących kodu natywnego](../debugger/debugging-native-code-faqs.md) Zawiera odpowiedzi na często zadawane pytania dotyczące debugowania C++ programów

 [Debugowanie modelu COM i ActiveX](../debugger/com-and-activex-debugging.md) Zawiera informacje dotyczące debugowania aplikacji COM i ActiveX, w tym narzędzi, których można użyć do debugowania obiektów COM i ActiveX.

 [Instrukcje: debugowanie](../debugger/how-to-debug-injected-code.md) wprowadzonego kodu Zawiera wskazówki dotyczące debugowania kodu, który używa atrybutów. Instrukcje obejmują Włączanie adnotacji źródłowej, sposób wyświetlania wstrzykniętego kodu i sposób wyświetlania kodu demontażu w bieżącym punkcie wykonywania.

 [Przewodnik: debugowanie aplikacji równoległej](../debugger/walkthrough-debugging-a-parallel-application.md) Opisuje sposób używania okienek **zadań równoległych** i **stosów równoległych** do debugowania aplikacji równoległej.

## <a name="related-sections"></a>Sekcje pokrewne
 [Przygotowanie do debugowania C++ projektów](../debugger/debugging-preparation-visual-cpp-project-types.md) zawiera linki do tematów opisujących sposób debugowania natywnych typów projektów utworzonych przez szablony C++ projektu.

 [Debugowanie projektów DLL](../debugger/debugging-dll-projects.md) Zawiera informacje na temat debugowania natywnych i zarządzanych bibliotek DLL.

 [Pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md) Zawiera łącza do większych sekcji dokumentacji debugowania. Informacje obejmują nowości w debugerze, ustawienia i przygotowania, punkty przerwania, obsługa wyjątków, edytowanie i kontynuowanie, debugowanie kodu zarządzanego, debugowanie kodu natywnego, debugowanie SQL i odwołania do interfejsu użytkownika.

## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Debugowanie w programie Visual Studio](../debugger/index.yml)