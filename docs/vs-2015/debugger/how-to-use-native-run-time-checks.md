---
title: 'Porady: Korzystanie z macierzystego sprawdzania w czasie wykonywania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- c.runtime.errorchecks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
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
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4efbb4e151ea47f655f0b28e19d2811d5541e944
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798758"
---
# <a name="how-to-use-native-run-time-checks"></a>Porady: Korzystanie z macierzystego sprawdzania w trakcie wykonywania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual C++ można użyć natywny [runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b) do przechwytywania typowych błędów czasu wykonywania, takich jak:  
  
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
  
-   Użyj **usunęliśmy** opcji i łącze z wersji debugowania biblioteki wykonawczej języka C (/ MDd, na przykład).  
  
### <a name="to-modify-native-run-time-check-behavior"></a>Aby zmodyfikować zachowanie natywnych sprawdzenie czasu wykonywania  
  
-   Użyj `runtime_checks` pragmy.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b)   
 [Sprawdzanie błędów czasu wykonywania](http://msdn.microsoft.com/library/c965dd01-57ad-4a3c-b1d6-5aa04f920501)





