---
title: Użyj Edytuj i Kontynuuj (C#) | Microsoft Docs
ms.date: 10/04/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 18d11f552d486fd9ebd7a95323e327324de14108
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851856"
---
# <a name="how-to-use-edit-and-continue-c"></a>Porady: korzystanie z opcji edytuj i kontynuuj (C#)
Za pomocą Edytuj i Kontynuuj można wprowadzać i stosować zmiany w kodzie w trybie przerwania podczas debugowania, bez konieczności zatrzymywania i ponownego uruchamiania sesji debugowania.

Edytuj i Kontynuuj dla języka C# odbywa się automatycznie po wprowadzeniu zmian w kodzie w trybie przerwania, a następnie kontynuuj debugowanie przy użyciu opcji **Kontynuuj**, **Wkrocz**lub **Ustaw następną instrukcję**lub Oceń funkcję w oknie debugera.

Aby uzyskać więcej informacji, zobacz [Edytuj i Kontynuuj (Visual C#)](../debugger/edit-and-continue-visual-csharp.md).

>[!NOTE]
>Polecenie Edytuj i Kontynuuj nie jest obsługiwane w przypadku optymalizacji, mieszanego ani SQL Server kodu integracji środowiska uruchomieniowego języka wspólnego (CLR). Aby uzyskać informacje na temat innych nieobsługiwanych scenariuszy, zobacz [obsługiwane zmiany kodu (C# i Visual Basic)](../debugger/supported-code-changes-csharp.md). Jeśli spróbujesz edytować i kontynuować w jednym z tych scenariuszy, pojawi się okno komunikatu z informacją, że opcja Edytuj i Kontynuuj nie jest obsługiwana.

**Aby włączyć lub wyłączyć funkcję Edytuj i Kontynuuj:**

1. Jeśli jesteś w sesji debugowania, Zatrzymaj debugowanie (**Debuguj**  >  **Zatrzymaj debugowanie** lub **SHIFT** + **F5**).

1. W **Tools**oknie  >  **Opcje** narzędzia (lub **Debug**  >  **Opcje**debugowania) > **debugowanie**  >  **Ogólne**, zaznacz lub wyczyść pole wyboru **Włącz edytowanie i kontynuowanie** .

Ustawienie zacznie obowiązywać po rozpoczęciu lub ponownym uruchomieniu sesji debugowania.

**Aby użyć Edytuj i Kontynuuj:**

1. Podczas debugowania w trybie przerwania wprowadź zmiany w kodzie źródłowym.

1. Z menu **Debuguj** kliknij polecenie **Kontynuuj**, **krok**lub **Ustaw następną instrukcję**lub Oceń funkcję w oknie debugera.

   Debugowanie jest kontynuowane z nowym, skompilowanym kodem.

Niektóre typy zmian w kodzie nie są obsługiwane przez program Edytuj i Kontynuuj. Aby uzyskać więcej informacji, zobacz [obsługiwane zmiany kodu (C# i Visual Basic)](../debugger/supported-code-changes-csharp.md).
