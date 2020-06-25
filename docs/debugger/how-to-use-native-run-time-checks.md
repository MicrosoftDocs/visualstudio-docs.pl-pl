---
title: Jak używać natywnych testów w czasie wykonywania | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- c.runtime.errorchecks
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- /RTC compiler option [C++], /O compiler option
- run-time checks, native
- stack, pointer corruption
- stack pointers, corruption
- /O compiler option, /RTC option
- run-time errors, error checks
- O compiler option, /RTC option
- debugger, runtime errors
- variables [debugger], loss of data
- runtime_checks pragma
- variables [debugger], catching dependencies on uninitialized local variables
- run-time errors, debugging
- debugger, native run-time checks
- optimized build option
- RTC compiler option, /O compiler option
- native run-time checks
- run-time checks
- debugging arrays
- stack pointers
- arrays [Visual Studio], debugging
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 5fccf510719aa5e960c12fdc807d6375ee31d3d0
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348850"
---
# <a name="how-to-use-native-run-time-checks"></a>Porady: Korzystanie z macierzystego sprawdzania w trakcie wykonywania
W projekcie Visual Studio C++ można użyć natywnego [runtime_checks](/cpp/preprocessor/runtime-checks) do przechwytywania typowych błędów czasu wykonywania, takich jak:

- Uszkodzenie wskaźnika stosu.

- Przekroczenia tablic lokalnych.

- Uszkodzenie stosu.

- Zależności od niezainicjowanych zmiennych lokalnych.

- Utrata danych w przypisaniu do krótszej zmiennej.

  Jeśli używasz **/RTC** z zoptymalizowaną (**/o**) kompilacją, wynik błędu kompilatora. Jeśli `runtime_checks` w zoptymalizowanej kompilacji używasz dyrektywy pragma, pragma nie ma żadnego wpływu.

  Podczas debugowania programu, który ma włączone sprawdzanie czasu wykonywania, domyślną akcją jest zatrzymanie i przerwanie działania programu w debugerze w przypadku wystąpienia błędu w czasie wykonywania. Można zmienić to zachowanie domyślne dla dowolnego sprawdzenia w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md).

  W poniższych procedurach opisano, jak włączyć natywne testy w czasie wykonywania w kompilacji debugowania oraz jak zmodyfikować natywne zachowanie w czasie wykonywania.

  W innych tematach w tej sekcji znajdują się informacje o:

- [Dostosowywanie kontroli w czasie wykonywania przy użyciu biblioteki wykonawczej C](../debugger/native-run-time-checks-customization.md)

- [Używanie testów w czasie wykonywania bez biblioteki wykonawczej C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)

### <a name="to-enable-native-run-time-checks-in-a-debug-build"></a>Aby włączyć natywne testy w czasie wykonywania w kompilacji debugowania

- Użyj opcji **/RTC** i Połącz z wersją debugową biblioteki wykonawczej C (na przykład/MDD).

### <a name="to-modify-native-run-time-check-behavior"></a>Aby zmodyfikować natywne zachowanie sprawdzania w czasie wykonywania

- Użyj `runtime_checks` dyrektywy pragma.

## <a name="see-also"></a>Zobacz też
- [Debugowanie w Visual Studio](../debugger/index.yml)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [runtime_checks](/cpp/preprocessor/runtime-checks)
- [Sprawdzanie błędów czasu wykonywania](/cpp/c-runtime-library/run-time-error-checking)