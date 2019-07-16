---
title: Techniki debugowania CRT | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.runtime.debugging
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [CRT]
- CRT, debugging
- debugging [C++], CRT debug support
ms.assetid: 9be561f6-14a8-44ff-925d-d911d5b8e6ff
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a69defe75b80ef1f395931017dfc942398ca2710
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68161484"
---
# <a name="crt-debugging-techniques"></a>Techniki testowania CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
