---
title: 'Instrukcje: korzystanie z natywnych testów w czasie wykonywania | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: b50dda3e31e27fa5d177c3b0ba2790babd2a660f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685858"
---
# <a name="how-to-use-native-run-time-checks"></a>Porady: Korzystanie z macierzystego sprawdzania w trakcie wykonywania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W Visual C++ można używać natywnego [runtime_checks](https://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b) do przechwytywania typowych błędów czasu wykonywania, takich jak:  
  
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
 [Debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [runtime_checks](https://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b)   
 [Sprawdzanie błędów czasu wykonywania](https://msdn.microsoft.com/library/c965dd01-57ad-4a3c-b1d6-5aa04f920501)
