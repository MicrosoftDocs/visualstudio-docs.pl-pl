---
title: Debugowanie kodu natywnego | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging native code
- debugging [C++], native code
- debugging [Visual Studio], native code
- native code, debugging
ms.assetid: d94eee90-7e0d-4cac-88c1-9831030daa5e
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 61ee852f75737d85604fda106b15e61dc3634899
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196423"
---
# <a name="debugging-native-code"></a>Debugowanie kodu natywnego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sekcja dotyczy niektórych typowych problemów z debugowaniem i technik dla aplikacji natywnych. Techniki omówione w tej sekcji są technikami wysokiego poziomu. Aby Mechanics za pomocą debugera programu Visual Studio, zobacz [Plan debugera](../debugger/debugger-basics.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: debugowanie zoptymalizowanego kodu](../debugger/how-to-debug-optimized-code.md)  
 Podaje porady dotyczące debugowania zoptymalizowanego kodu, w tym, dlaczego należy debugować niezoptymalizowaną wersję programu, domyślne ustawienia optymalizacji konfiguracji debugowania i wydania oraz porady dotyczące znajdowania błędów, które pojawiają się tylko w zoptymalizowanym kodzie (włączenie optymalizacji w konfiguracji kompilacji debugowania).  
  
 [DebugBreak i __debugbreak](../debugger/debugbreak-and-debugbreak.md)  
 Opisuje funkcję Win32 `DebugBreak` i zawiera łącze do jej tematu referencyjnego w zestawie SDK platformy. Zawiera również informacje o programie `__debugbreak` wewnętrznym.  
  
 [Potwierdzenia C/C++](../debugger/c-cpp-assertions.md)  
 W tym artykule omówiono instrukcje potwierdzania, sposób ich działania, korzyści z używania ich (przechwytywanie błędów logiki, sprawdzanie wyników operacji i testowanie warunków błędów), interakcje z programem `_DEBUG` oraz typy potwierdzeń, które są obsługiwane w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 [Instrukcje: Debugowanie kodu zestawu wbudowanego](../debugger/how-to-debug-inline-assembly-code.md)  
 Zawiera krótkie instrukcje dotyczące korzystania z okna demontażu w celu wyświetlenia instrukcji zestawu i okna rejestrów, aby wyświetlić zawartość rejestru i zawiera łącza do tematów dotyczących tych okien.  
  
 [Techniki testowania MFC](../debugger/mfc-debugging-techniques.md)  
 Łącza do technik debugowania dla programów MFC, w tym: afxDebugBreak, makro śledzenia, Wykrywanie przecieków pamięci w MFC, potwierdzenia MFC i zmniejszanie rozmiaru kompilacji debugowania MFC.  
  
 [Techniki testowania CRT](../debugger/crt-debugging-techniques.md)  
 Łącza do technik debugowania dla biblioteki wykonawczej C, w tym przy użyciu biblioteki debugowania CRT, makr dla raportowania, różnic między funkcjami malloc i _malloc_dbg, pisania funkcji punktu zaczepienia debugowania i sterty debugowania CRT.  
  
 [Debugowanie kodu natywnego — Często zadawane pytania](../debugger/debugging-native-code-faqs.md)  
 Zawiera odpowiedzi na często zadawane pytania dotyczące debugowania programów Visual C++  
  
 [COM i debugowanie ActiveX](../debugger/com-and-activex-debugging.md)  
 Zawiera informacje dotyczące debugowania aplikacji COM i ActiveX, w tym narzędzi, których można użyć do debugowania obiektów COM i ActiveX.  
  
 [Instrukcje: debugowanie natywnych bibliotek DLL](../debugger/how-to-debug-native-dlls.md)  
 Wyjaśnia, jak skonfigurować debugowanie dla bibliotek DLL z kodu natywnego.  
  
 [Instrukcje: debugowanie wprowadzonego kodu](../debugger/how-to-debug-injected-code.md)  
 Zawiera wskazówki dotyczące debugowania kodu, który używa atrybutów. Instrukcje obejmują Włączanie adnotacji źródłowej, sposób wyświetlania wstrzykniętego kodu i sposób wyświetlania kodu demontażu w bieżącym punkcie wykonywania.  
  
 [Przewodnik: debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Opisuje sposób używania okienek **zadań równoległych** i **stosów równoległych** do debugowania aplikacji równoległej.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Typy projektów Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)  
 Zawiera łącza do tematów opisujących sposób debugowania natywnych typów projektów utworzonych przez Visual C++ szablonów projektu.  
  
 [Debugowanie w Visual Studio](../debugger/debugging-in-visual-studio.md)  
 Zawiera łącza do większych sekcji dokumentacji debugowania. Informacje obejmują nowości w debugerze, ustawienia i przygotowania, punkty przerwania, obsługa wyjątków, edytowanie i kontynuowanie, debugowanie kodu zarządzanego, debugowanie kodu natywnego, debugowanie SQL i odwołania do interfejsu użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie w Visual Studio](../debugger/debugging-in-visual-studio.md)
