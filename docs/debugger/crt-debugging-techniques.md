---
title: Techniki debugowania CRT | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- c.runtime.debugging
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [CRT]
- CRT, debugging
- debugging [C++], CRT debug support
ms.assetid: 9be561f6-14a8-44ff-925d-d911d5b8e6ff
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8dedb7a35e95cc9efc68cbd947b415b4499a8fa9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54943919"
---
# <a name="crt-debugging-techniques"></a>Techniki testowania CRT
Jeśli debugujesz program, który używa biblioteki wykonawczej języka C, te techniki debugowania mogą być przydatne.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Korzystanie z biblioteki debugowania CRT](../debugger/crt-debug-library-use.md)  
 W tym artykule opisano obsługę debugowania, dostarczone przez biblioteki wykonawczej C i zawiera instrukcje dotyczące uzyskiwania dostępu do narzędzi.  
  
 [Makra raportowania](../debugger/macros-for-reporting.md)  
 Zawiera informacje na temat **_RPTn** i **_RPTFn** makra (zdefiniowane w CRTDBG. Godz.), która zastępuje użycia `printf` instrukcje do debugowania.  
  
 [Wersje debugowania funkcji alokacji sterty](../debugger/debug-versions-of-heap-allocation-functions.md)  
 W tym artykule omówiono specjalne wersje do debugowania funkcji alokacji sterty, w tym: sposób CRT mapowania wywołań, korzyści wynikające z wywołania ich jawnie, jak uniknąć konwersji, śledzenia oddzielne typy alokacji w blokach klienta i nie Definiowanie _ wyniki DEBUGOWANIE.  
  
 [Szczegóły dotyczące sterty debugowania CRT](../debugger/crt-debug-heap-details.md)  
 Zawiera łącza do zarządzania pamięcią i stosu debugowania, typy bloków na stercie debugowania przy użyciu sterty debugowania, stanu sterty funkcje raportowania i śledzenie żądań alokacji sterty.  
  
 [Pisanie funkcji debugowania punktów zaczepienia](../debugger/debug-hook-function-writing.md)  
 Utworzenie punktu zaczepienia Wyświetla łącza do bloku klienta, functions, funkcje punktu zaczepienia alokacji, punkty zaczepienia alokacji i alokacji pamięci CRT i raportowanie funkcji punktów zaczepienia.  
  
 [Wyszukiwanie przecieków pamięci za pomocą biblioteki CRT](../debugger/finding-memory-leaks-using-the-crt-library.md)  
 Opisano techniki wykrywanie i izolowanie przecieków pamięci za pomocą debugera i biblioteki wykonawczej C.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)  
 W tym artykule omówiono niektóre typowe problemy z debugowania i technik dla aplikacji C i C++.  
  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)  
 Zawiera zalecenia dotyczące debugowania bardziej bezpieczne.