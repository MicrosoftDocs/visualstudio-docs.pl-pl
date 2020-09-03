---
title: Techniki debugowania CRT | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161484"
---
# <a name="crt-debugging-techniques"></a>Techniki testowania CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W przypadku debugowania programu korzystającego z biblioteki wykonawczej C te techniki debugowania mogą być przydatne.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Korzystanie z biblioteki debugowania CRT](../debugger/crt-debug-library-use.md)  
 Zawiera opis obsługi debugowania dostarczonej przez bibliotekę wykonawczą C i instrukcje dotyczące uzyskiwania dostępu do narzędzi.  
  
 [Makra raportowania](../debugger/macros-for-reporting.md)  
 Zawiera informacje dotyczące **_RPTn** i **_RPTFn** makr (zdefiniowane w CRTDBG. H), która zastąpi stosowanie `printf` instrukcji dla debugowania.  
  
 [Wersja debugowania funkcji alokacji stosu](../debugger/debug-versions-of-heap-allocation-functions.md)  
 Omawia specjalne wersje debugowania funkcji alokacji sterty, w tym: jak są wywoływane mapowania CRT, zalety wywołania ich jawnie, sposób zapobiegania konwersji, śledzenie oddzielnych typów alokacji w blokach klienta oraz wyniki niedefiniowania _DEBUG.  
  
 [Szczegóły dotyczące sterty debugowania CRT](../debugger/crt-debug-heap-details.md)  
 Oferuje linki do zarządzania pamięcią i sterty debugowania, typy bloków na stercie debugowania, używanie sterty debugowania, funkcji raportowania stanu sterty i śledzenie żądań alokacji sterty.  
  
 [Pisanie debugowanie funkcji punktów zaczepienia](../debugger/debug-hook-function-writing.md)  
 Wyświetla listę linków do funkcji punktu zaczepienia bloku klienta, funkcje punktu zaczepienia alokacji, punkty zaczepienia alokacji i alokacje pamięci CRT oraz raporty funkcji punktu zaczepienia.  
  
 [Wyszukiwanie przecieków pamięci za pomocą biblioteki CRT](../debugger/finding-memory-leaks-using-the-crt-library.md)  
 Obejmuje techniki wykrywania i izolowania przecieków pamięci przy użyciu debugera i biblioteki wykonawczej C.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)  
 W tym artykule omówiono niektóre typowe problemy z debugowaniem i techniki dla aplikacji C i C++.  
  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)  
 Zawiera zalecenia dotyczące bezpieczniejszego debugowania.
