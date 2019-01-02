---
title: Microsoft Office Word klawiatura, ustawienia klawiatury Microsoft Office — okno dialogowe
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard
- VST.WordOptions.KeyboardMappingScheme
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fd493a1448276dcf151a862771546a31f201c761
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53909284"
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Microsoft Office Word klawiatura, ustawienia klawiatury Microsoft Office — okno dialogowe
  Microsoft Word pakietu Office i programu Visual Studio jednocześnie obsługiwać klawiszy skrótów. Uruchomić ten sam klawisz skrótu dla różnych poleceń w programie Word i w programie Visual Studio. Gdy program Word jest otwarty w projekcie na poziomie dokumentu, w programie Visual Studio, tylko jedną aplikację naraz otrzymuje polecenia klawiszy skrótów. Domyślnie program Visual Studio odbiera wszystkie polecenia klawiszy skrótów, ale możesz wprowadzać Word ich otrzymywania, gdy dokument ma fokus, wybierając **dynamiczny schemat klawiatury**.  
  
 Jeśli używasz klawisza skrótu, który nie jest przypisany do polecenia w aplikacji, która obecnie obsługuje klawiszy skrótów, klawisz skrótu jest przekazywane do innych aplikacji.  
  
 Możesz wybrać opcję będzie obowiązywać dla projektów programu Word do momentu zmiany. Zaznaczenie nie ma wpływu na projekty programu Microsoft Office Excel; należy wszelkie zmiany dla programu Excel, korzystając z opcji klawiatura programu Microsoft Office Excel.  
  
## <a name="uielement-list"></a>Lista elementów interfejsu użytkownika  
 **Schemat klawiatury w usłudze Visual Studio**  
 Program Visual Studio odbiera wszystkie polecenia klawiszy skrótów, nawet wtedy, gdy dokument programu Word jest ustawiony fokus. Na przykład, jeśli naciśniesz klawisz funkcji **F5** podczas dokument ma fokus, Visual Studio uruchomiony zostanie program debugowania rozwiązania.  
  
 **Dynamiczny schemat klawiatury**  
 Program Visual Studio otrzymuje polecenia klawiszy skrótów, tylko wtedy, gdy ma ona fokus. Po aktywowaniu w dokumencie programu Word, wyraz odbiera wszystkie polecenia klawiszy skrótów. Na przykład, jeśli naciśniesz klawisz funkcji **F5** podczas dokument programu Word jest ustawiony fokus, wyświetlane jest okno **Znajdź i Zamień** okno dialogowe z **przejdź do** wybraną kartą. Jeśli użytkownik naciśnie klawisz **F5** Chociaż program Visual Studio ma fokus, Visual Studio uruchomiony zostanie program debugowania rozwiązania.  
  
## <a name="see-also"></a>Zobacz także  
 [Microsoft Office Excel klawiatura, ustawienia klawiatury Microsoft Office — okno dialogowe](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
