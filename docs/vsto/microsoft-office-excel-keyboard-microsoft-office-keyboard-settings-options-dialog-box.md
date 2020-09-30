---
title: Office Excel — klawiatura, ustawienia, Opcje — okno dialogowe
titleSuffix: ''
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
ms.openlocfilehash: 8b590f82d5f28c3a71e86e18dfe16b1c3e6c4c5a
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584519"
---
# <a name="microsoft-office-excel-keyboard-settings-options-dialog-box"></a>Microsoft Office klawiatura, ustawienia, Opcje — okno dialogowe
  Microsoft Office program Excel i program Visual Studio obsługują klawisze skrótów. Ta sama kombinacja klawiszy skrótu może być podstawą dla różnych poleceń w programie Excel i w programie Visual Studio. Gdy program Excel jest otwarty w projekcie na poziomie dokumentu w programie Visual Studio, tylko jedna aplikacja jednocześnie otrzymuje polecenia klawiszy skrótu. Domyślnie program Visual Studio otrzymuje wszystkie polecenia klawiszy skrótów, ale można sprawić, aby program Excel otrzymywał je, gdy dokument ma fokus, wybierając **dynamiczny schemat klawiatury**.

 Jeśli używasz klawisza skrótu, który nie jest przypisany do polecenia w aplikacji, która aktualnie obsługuje klawisze skrótów, klawisz skrótu jest przenoszona do innej aplikacji.

 Wybrana opcja będzie obowiązywać dla projektów programu Excel, dopóki nie zostanie zmieniona. Zaznaczenie nie ma wpływu na projekty Microsoft Office Word; należy wprowadzić dowolną zmianę dla programu Word przy użyciu opcji klawiatury Microsoft Office Word.

## <a name="uielement-list"></a>Lista elementów UIElement
 **Schemat klawiatury programu Visual Studio** Program Visual Studio odbiera wszystkie polecenia klawiszy skrótów, nawet jeśli program Excel ma fokus. Na przykład po naciśnięciu klawisza **F5** , gdy program Excel ma fokus, program Visual Studio rozpocznie debugowanie Twojego rozwiązania.

 **Dynamiczny schemat klawiatury** Program Visual Studio otrzymuje polecenia skrótu klawiaturowego tylko wtedy, gdy ma fokus. Gdy program Excel ma fokus, program Excel odbiera wszystkie polecenia klawiszy skrótów. Na przykład po naciśnięciu klawisza **F5** , gdy program Excel ma fokus, program Excel otwiera okno dialogowe **Przejdź do** . Jeśli naciśniesz klawisz **F5** , a program Visual Studio ma fokus, program Visual Studio rozpocznie debugowanie Twojego rozwiązania.

## <a name="see-also"></a>Zobacz też
- [Klawiatura Microsoft Office Word, ustawienia klawiatury Microsoft Office, okno dialogowe Opcje](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
