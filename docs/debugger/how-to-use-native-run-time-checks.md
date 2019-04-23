---
title: 'Instrukcje: Korzystanie z macierzystego sprawdzania w czasie wykonywania | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 4ccf0fea80ddfcc7db0921512391f5063a8f2dad
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60100212"
---
# <a name="how-to-use-native-run-time-checks"></a>Instrukcje: Korzystanie z macierzystego sprawdzania w czasie wykonywania
W elemencie wizualnym C++, możesz użyć natywnych [runtime_checks](/cpp/preprocessor/runtime-checks) do przechwytywania typowych błędów czasu wykonywania, takich jak:

- Uszkodzenie wskaźnika stosu.

- Przepełnienia lokalne tablice.

- Uszkodzenie stosu.

- Zależności w niezainicjowanych zmiennych lokalnych.

- Utrata danych na przypisanie do zmiennej krótszy.

  Jeśli używasz **usunęliśmy** przy użyciu zoptymalizowanego (**/O**) kompilacji powoduje błąd kompilatora. Jeśli używasz `runtime_checks` pragmy w optymalizowania kompilacji pragmy nie ma wpływu.

  Podczas debugowania programu, który ma włączone kontrole czasu wykonywania, domyślna akcja dotyczy programu zatrzymać, a następnie Przerwij do debugera, gdy wystąpi błąd czasu wykonywania. Można zmienić to domyślne zachowanie dla sprawdzanie w czasie wykonania. Aby uzyskać więcej informacji, zobacz [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md).

  W poniższych procedurach opisano sposób włączania macierzyste sprawdzanie w czasie wykonywania w kompilacji debugowania oraz jak zmodyfikować zachowanie natywnych sprawdzanie w czasie wykonania.

  Inne tematy w tej sekcji zawierają informacje dotyczące:

- [Dostosowywanie środowiska wykonawczego sprawdza, czy za pomocą biblioteki wykonawczej języka C](../debugger/native-run-time-checks-customization.md)

- [Za pomocą środowiska wykonawczego sprawdza, czy bez biblioteki wykonawczej języka C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)

### <a name="to-enable-native-run-time-checks-in-a-debug-build"></a>Aby włączyć macierzyste sprawdzanie w czasie wykonywania w kompilacji debugowania

- Użyj **usunęliśmy** opcji i łącze z wersji debugowania biblioteki wykonawczej języka C (/ MDd, na przykład).

### <a name="to-modify-native-run-time-check-behavior"></a>Aby zmodyfikować zachowanie natywnych sprawdzenie czasu wykonywania

- Użyj `runtime_checks` pragmy.

## <a name="see-also"></a>Zobacz też
- [Debugowanie w programie Visual Studio](../debugger/index.md)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [runtime_checks](/cpp/preprocessor/runtime-checks)
- [Sprawdzanie błędów czasu wykonywania](/cpp/c-runtime-library/run-time-error-checking)