---
title: Microsoft Office Excel klawiatura, ustawienia klawiatury Microsoft Office — okno dialogowe
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ExcelOptions.KeyboardMappingScheme
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Excel_Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Excel.Keyboard
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 63f3bfc9295501d5f9b8f0267037302cdbb04a76
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970220"
---
# <a name="microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Microsoft Office Excel klawiatura, ustawienia klawiatury Microsoft Office — okno dialogowe
  Program Microsoft Office Excel i programu Visual Studio jednocześnie obsługiwać klawiszy skrótów. Uruchomić ten sam klawisz skrótu dla różnych poleceń w programie Excel, jak i w programie Visual Studio. Gdy program Excel jest otwarty w projekcie na poziomie dokumentu, w programie Visual Studio, tylko jedną aplikację naraz otrzymuje polecenia klawiszy skrótów. Domyślnie program Visual Studio odbiera wszystkie polecenia klawiszy skrótów, ale możesz wprowadzać ich otrzymywania, gdy dokument ma fokus, wybierając w programie Excel **dynamiczny schemat klawiatury**.

 Jeśli używasz klawisza skrótu, który nie jest przypisany do polecenia w aplikacji, która obecnie obsługuje klawiszy skrótów, klawisz skrótu jest przekazywane do innych aplikacji.

 Możesz wybrać opcję będzie obowiązywać dla projektów programu Excel do czasu, możesz go zmienić. Zaznaczenie nie ma wpływu na projekty programu Microsoft Office Word; użytkownik musi zapewnić wszelkie zmiany dla programu Word za pomocą opcji klawiatura programu Microsoft Office Word.

## <a name="uielement-list"></a>Lista elementów interfejsu użytkownika
 **Schemat klawiatury w usłudze Visual Studio** programu Visual Studio odbiera wszystkie polecenia klawiszy skrótów, nawet wtedy, gdy program Excel jest ustawiony fokus. Na przykład, jeśli naciśniesz klawisz funkcji **F5** podczas, gdy program Excel ma fokus, Visual Studio uruchomiony zostanie program debugowania rozwiązania.

 **Dynamiczny schemat klawiatury** programu Visual Studio otrzymuje polecenia klawiszy skrótów, tylko wtedy, gdy ma ona fokus. Gdy program Excel ma fokus, program Excel odbiera wszystkie polecenia klawiszy skrótów. Na przykład, jeśli naciśniesz klawisz funkcji **F5** podczas, gdy program Excel ma fokus, zostanie otwarty **przejdź do** okno dialogowe. Jeśli użytkownik naciśnie klawisz **F5** Chociaż program Visual Studio ma fokus, Visual Studio uruchomiony zostanie program debugowania rozwiązania.

## <a name="see-also"></a>Zobacz także
- [Microsoft Office Word klawiatura, ustawienia klawiatury Microsoft Office — okno dialogowe](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
