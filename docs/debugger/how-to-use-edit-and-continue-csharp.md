---
title: 'Instrukcje: Użyj funkcji Edytuj i Kontynuuj (C#) | Dokumentacja firmy Microsoft'
ms.date: 10/04/2018
ms.topic: conceptual
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
ms.openlocfilehash: ca4d8efda78974be00973ef3f6c5adcc77c2465d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54965279"
---
# <a name="how-to-use-edit-and-continue-c"></a>Instrukcje: Korzystanie z funkcji Edytuj i kontynuuj [C#]
Z funkcją Edytuj i Kontynuuj możesz wprowadzić i Zastosuj zmiany do kodu w trybie przerwania podczas debugowania, bez konieczności zatrzymywania i uruchamiania sesji debugowania.  

Edytuj i Kontynuuj dla języka C# odbywa się automatycznie po wprowadzeniu zmian w kodzie w trybie przerwania, następnie Kontynuuj debugowanie przy użyciu **Kontynuuj**, **kroku**, lub **Ustaw następną instrukcję**, lub Oceń funkcję w oknie debugera.  

Aby uzyskać więcej informacji, zobacz [Edytuj i Kontynuuj (Visual C#)](../debugger/edit-and-continue-visual-csharp.md).

>[!NOTE]
>Edytuj i Kontynuuj nie jest obsługiwane dla zoptymalizowane pod kątem, mieszany, lub kodu integracji środowiska uruchomieniowego (języka wspólnego CLR) wspólnego języka programu SQL Server. Aby uzyskać informacji na temat innych nieobsługiwanych scenariuszy, zobacz [obsługiwane zmiany kodu (C# i Visual Basic)](../debugger/supported-code-changes-csharp.md). Jeśli zostanie podjęta próba Edytuj i Kontynuuj przy użyciu jednego z tych scenariuszy, pojawi się komunikat informujący, że Edytuj i Kontynuuj nie jest obsługiwany.  
  
**Aby włączyć lub wyłączyć Edytuj i Kontynuuj:**  
   
1. Jeśli pracujesz w sesji debugowania, Zatrzymaj debugowanie (**debugowania** > **Zatrzymaj debugowanie** lub **Shift**+**F5**) .
   
1. W **narzędzia** > **opcje** (lub **debugowania** > **opcje**) > **debugowania**  >  **Ogólne**, zaznacz lub wyczyść **Włącz edytowanie i kontynuowanie** pole wyboru.  
  
Ustawienie zostanie uwzględnione po ponownym uruchomieniu lub uruchom ponownie sesję debugowania.  

**Aby użyć polecenia Edytuj i Kontynuuj:**  
   
1. Podczas debugowania w trybie przerwy wprowadź zmiany do kodu źródłowego.  
   
1. Z **debugowania** menu, kliknij przycisk **Kontynuuj**, **kroku**, lub **Ustaw następną instrukcję**, lub oceń funkcję w oknie debugera.  
   
   Debugowanie nadal stanowi nowy kod skompilowany. 

Niektóre rodzaje zmian w kodzie nie są obsługiwane przez Edytuj i Kontynuuj. Aby uzyskać więcej informacji, zobacz [obsługiwane zmiany kodu (C# i Visual Basic)](../debugger/supported-code-changes-csharp.md).   
