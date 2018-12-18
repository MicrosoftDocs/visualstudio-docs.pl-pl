---
title: Edytuj i Kontynuuj — okno dialogowe komunikat o błędzie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/15/2018
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.ENC.SupportedButNotAvaiable
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba573a6b6bffdfeebf37c5f46f1f774d699a1131
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388715"
---
# <a name="edit-and-continue-error-message"></a>Edytuj i Kontynuuj komunikat o błędzie 

**Edytuj i Kontynuuj** błąd okno komunikatu pojawia się podczas debugowania w języku kod, który obsługuje Edytuj i Kontynuuj, ale Edytuj i Kontynuuj nie jest dostępna dla zmiany kodu wprowadzone. Komunikat o błędzie zawiera bardziej szczegółowy opis. Aby reagować na okno dialogowe, wybierz pozycję **OK** aby zamknąć okno dialogowe, a następnie anulować próba edycji.  

Możliwe przyczyny tego komunikatu o błędzie:  

-   Podczas próby edytowania kodu programu SQL Server.
-   Podczas próby edytowania zoptymalizowanego kodu. Konieczne może przełączyć się z kompilację wydania do kompilacji debugowania.
-   Próby edytowania kodu, gdy jest uruchomiona, a nie gdy wstrzymaniu w debugerze. Spróbuj [ustawienie punktu przerwania](../debugger/using-breakpoints.md)i Edycja kodu podczas wstrzymania.
-   Podczas próby edytowania kodu zarządzanego, gdy włączone jest tylko debugowanie niezarządzane. Edytuj i Kontynuuj nie działa w przypadku [debugowanie w trybie mieszanym](../debugger/how-to-debug-in-mixed-mode.md).
-   W języku programowania, dzięki czemu kod to zmienić, nie jest obsługiwany przez Edytuj i Kontynuuj. Aby uzyskać więcej informacji, zobacz artykuły [obsługiwane zmiany kodu w języku C#](supported-code-changes-csharp.md), [edycji w języku Visual Basic, Edytuj i Kontynuuj nieobsługiwana](unsupported-edits-in-visual-basic-edit-and-continue.md), i [obsługiwane zmiany kodu C++](supported-code-changes-cpp.md).
-   Próba edycji kodu w aplikacji dołączysz do, zamiast uruchamiania, debugowania z **debugowania** menu.  
-   Podczas próby edytowania kodu podczas debugowania odzyskiwania po awarii. Zrzut programu Watson.  
-   Próby edytowania kodu po wystąpieniu nieobsługiwanego wyjątku, a opcja **Unwind na stosie wywołań dotycząca nieobsłużonych wyjątków** nie jest zaznaczone.  
-   Podczas próby edytowania kodu podczas debugowania aplikacji osadzonego środowiska uruchomieniowego.
-   Podczas próby edytowania kodu zarządzanego za pomocą .NET Framework w wersji wcześniejszej niż 4.5.1 z obiektem docelowym 64-bitowych aplikacji. Aby użyć Edytuj i Kontynuuj dla programu .NET Framework wcześniejszych niż 4.5.1, ustawić element docelowy **x86** w  **\<nazwa_projektu >** > **właściwości**  >  **Skompilować** karcie **zaawansowane kompilatora** ustawienie.  
-   Podczas próby edytowania kodu w zestawie, który został zmodyfikowany podczas debugowania, a został załadowany ponownie.  
-   Podczas próby edytowania kodu w zestawie, który nie został załadowany.  
-   Rozpoczynanie debugowania starą wersję aplikacji, ponieważ najnowsza wersja ma błędy kompilacji.
  
Aby uzyskać więcej informacji, zobacz:
- [C++, Edytuj i Kontynuuj blog post](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/)  
- [Obsługiwane zmiany kodu (C++)](../debugger/supported-code-changes-cpp.md)
- [Edytuj i kontynuuj](../debugger/edit-and-continue.md)