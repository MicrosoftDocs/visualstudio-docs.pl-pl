---
title: Okno dialogowe Edytuj i Kontynuuj komunikat o błędzie | Microsoft Docs
ms.date: 10/15/2018
ms.topic: reference
f1_keywords:
- vs.debug.ENC.SupportedButNotAvailable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7df95eae689f7c3abbb0d75a7557ce749bdceee5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "73188233"
---
# <a name="edit-and-continue-error-message"></a>Komunikat o błędzie Edytuj i Kontynuuj

Okno komunikatu o błędzie **Edytuj i Kontynuuj** pojawia się, gdy debugujesz w języku kodu, który obsługuje funkcję Edytuj i Kontynuuj, ale Edytuj i Kontynuuj nie jest dostępny dla wprowadzonych zmian w kodzie. Komunikat o błędzie zawiera bardziej szczegółowe wyjaśnienie. Aby odpowiedzieć na okno dialogowe, wybierz **przycisk OK** , aby zamknąć okno dialogowe i anulować próbę edycji.

Możliwe przyczyny tego komunikatu o błędzie:

- Próba edycji kodu SQL Server.
- Próba edycji zoptymalizowanego kodu. Może być konieczne przełączenie kompilacji wydania na kompilację debugowania.
- Próba edycji kodu w trakcie jego działania, a nie wstrzymana w debugerze. Spróbuj [ustawić punkt przerwania](../debugger/using-breakpoints.md)i edytując kod w trakcie wstrzymania.
- Podjęto próbę edycji kodu zarządzanego, gdy jest włączone tylko debugowanie niezarządzane. Edytuj i Kontynuuj nie działa w przypadku [debugowania w trybie mieszanym](../debugger/how-to-debug-in-mixed-mode.md).
- Wprowadzanie zmian w kodzie, które nie są obsługiwane przez edytowanie i kontynuowanie w języku programowania. Aby uzyskać więcej informacji, zobacz artykuły o [obsługiwanych zmianach kodu w języku C#](supported-code-changes-csharp.md), [Nieobsługiwane edycje w Visual Basic Edytuj i Kontynuuj](supported-code-changes-csharp.md)oraz [obsługiwane zmiany kodu w języku C++](supported-code-changes-cpp.md).
- Próba edycji kodu w aplikacji, do której jest dołączona, zamiast uruchamiania debugowania z menu **debugowanie** .
- Próba edycji kodu podczas debugowania zrzutu programu Dr. Watson.
- Podjęto próbę edycji kodu po wystąpieniu nieobsługiwanego wyjątku, a opcja **odwinięcia stosu wywołań w przypadku nieobsługiwanych wyjątków** nie jest zaznaczona.
- Próba edycji kodu podczas debugowania osadzonej aplikacji środowiska uruchomieniowego.
- Podjęto próbę edycji kodu zarządzanego przy użyciu wersji .NET Framework wcześniejszej niż 4.5.1 z 64-bitową aplikacją docelową. Aby użyć opcji Edytuj i Kontynuuj dla .NET Framework wcześniejszej niż 4.5.1, ustaw wartość docelowy na **x86** na **\<ProjectName>**  >  **Properties**  >  karcie**Kompilowanie** właściwości, **Zaawansowane ustawienia kompilatora** .
- Podjęto próbę edycji kodu w zestawie, który został zmodyfikowany podczas debugowania i został ponownie załadowany.
- Podjęto próbę edycji kodu w zestawie, który nie został załadowany.
- Rozpoczynanie debugowania starej wersji aplikacji, ponieważ Najnowsza wersja zawiera błędy kompilacji.

Aby uzyskać więcej informacji, zobacz:
- [Wpis w blogu Edytuj i Kontynuuj języka C++](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/)
- [Obsługiwane zmiany kodu (C++)](../debugger/supported-code-changes-cpp.md)
- [Edytuj i kontynuuj](../debugger/edit-and-continue.md)