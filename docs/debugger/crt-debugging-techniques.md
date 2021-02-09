---
title: Techniki debugowania CRT | Microsoft Docs
description: Istnieją różne techniki, których można użyć do debugowania programu, który używa biblioteki środowiska uruchomieniowego C (CRT). Skorzystaj z tego artykułu i jego linków, aby dowiedzieć się więcej na temat tych technik.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 84d5f85584403cc18cd00708a8d4698723d614ef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857613"
---
# <a name="crt-debugging-techniques"></a>Techniki testowania CRT
W przypadku debugowania programu korzystającego z biblioteki wykonawczej C te techniki debugowania mogą być przydatne.

## <a name="in-this-section"></a>W tej sekcji
 [Użycie biblioteki debugowania CRT](../debugger/crt-debug-library-use.md)

 Zawiera opis obsługi debugowania dostarczonej przez bibliotekę C Run-Time i zawiera instrukcje dotyczące uzyskiwania dostępu do narzędzi.

 [Makra raportowania](../debugger/macros-for-reporting.md)

 Zawiera informacje dotyczące **_RPTn** i **_RPTFn** makr (zdefiniowane w CRTDBG. H), która zastąpi stosowanie `printf` instrukcji dla debugowania.

 [Wersje debugowania funkcji alokacji sterty](../debugger/debug-versions-of-heap-allocation-functions.md)

 Omawia specjalne wersje debugowania funkcji alokacji sterty, w tym: jak są wywoływane mapowania CRT, zalety wywołania ich jawnie, sposób zapobiegania konwersji, śledzenie oddzielnych typów alokacji w blokach klienta oraz wyniki niedefiniowania _DEBUG.

 [Szczegóły sterty debugowania CRT](../debugger/crt-debug-heap-details.md)

 Oferuje linki do zarządzania pamięcią i sterty debugowania, typy bloków na stercie debugowania, używanie sterty debugowania, funkcji raportowania stanu sterty i śledzenie żądań alokacji sterty.

 [Zapisywanie funkcji punktu zaczepienia debugowania](../debugger/debug-hook-function-writing.md)

 Wyświetla listę linków do funkcji punktu zaczepienia bloku klienta, funkcje punktu zaczepienia alokacji, punkty zaczepienia alokacji i alokacje pamięci CRT oraz raporty funkcji punktu zaczepienia.

 [Wyszukiwanie przecieków pamięci za pomocą biblioteki CRT](../debugger/finding-memory-leaks-using-the-crt-library.md)

 Obejmuje techniki wykrywania i izolowania przecieków pamięci przy użyciu debugera i biblioteki języka C Run-Time.

## <a name="related-sections"></a>Sekcje pokrewne

- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md) — omawia niektóre typowe problemy z debugowaniem i techniki dla aplikacji C i C++.
- [Zabezpieczenia debugera](../debugger/debugger-security.md) — zawiera zalecenia dotyczące bezpieczniejszego debugowania.