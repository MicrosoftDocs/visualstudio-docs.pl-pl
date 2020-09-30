---
title: Office Word — klawiatura, ustawienia, Opcje — okno dialogowe
titleSuffix: ''
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 83cfe2e6061f82d48a00354b610955c698a9a11f
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584506"
---
# <a name="microsoft-office-word-keyboard-settings-options-dialog-box"></a>Microsoft Office klawiatura, ustawienia, Opcje — okno dialogowe
  Microsoft Office programy Word i Visual Studio obsługują klawisze skrótów. Ta sama kombinacja klawiszy skrótu może być podstawą dla różnych poleceń w programie Word i w programie Visual Studio. Gdy program Word jest otwarty w projekcie na poziomie dokumentu w programie Visual Studio, tylko jedna aplikacja jednocześnie otrzymuje polecenia klawiszy skrótu. Domyślnie program Visual Studio otrzymuje wszystkie polecenia klawisza skrótu, ale można wyrazić je od momentu, gdy dokument ma fokus, wybierając **dynamiczny schemat klawiatury**.

 Jeśli używasz klawisza skrótu, który nie jest przypisany do polecenia w aplikacji, która aktualnie obsługuje klawisze skrótów, klawisz skrótu jest przenoszona do innej aplikacji.

 Wybrana opcja będzie obowiązywać dla projektów programu Word, dopóki nie zostanie zmieniona. Zaznaczenie nie ma wpływu na Microsoft Office projekty programu Excel; musisz wprowadzić dowolną zmianę dla programu Excel, korzystając z opcji klawiatury Microsoft Office Excel.

## <a name="uielement-list"></a>Lista elementów UIElement
 **Schemat klawiatury programu Visual Studio** Program Visual Studio odbiera wszystkie polecenia klawiszy skrótów, nawet jeśli dokument programu Word ma fokus. Na przykład po naciśnięciu klawisza **F5** , gdy dokument ma fokus, program Visual Studio rozpocznie debugowanie Twojego rozwiązania.

 **Dynamiczny schemat klawiatury** Program Visual Studio otrzymuje polecenia skrótu klawiaturowego tylko wtedy, gdy ma fokus. Gdy dokument programu Word ma fokus, program Word otrzymuje wszystkie polecenia klawiszy skrótów. Na przykład po naciśnięciu klawisza **F5** , gdy dokument programu Word ma fokus, program Word otwiera okno dialogowe **Znajdowanie i zamienianie** z wybraną kartą **Przejdź do** . Jeśli naciśniesz klawisz **F5** , a program Visual Studio ma fokus, program Visual Studio rozpocznie debugowanie Twojego rozwiązania.

## <a name="see-also"></a>Zobacz też
- [Microsoft Office klawiatura programu Excel, ustawienia klawiatury Microsoft Office, okno dialogowe Opcje](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
