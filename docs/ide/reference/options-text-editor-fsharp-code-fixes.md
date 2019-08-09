---
title: Opcje, Edytor tekstu, F#, poprawki kodu
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a73991702455fab54baf868499634e1a4f5bbf48
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68870745"
---
# <a name="options-text-editor--f--code-fixes"></a>Opcje: > F# Edytora tekstu > poprawek kodu

Strona Opcje poprawek kodu służy do określania ustawień, które mogą ułatwić identyfikację błędów kodu i oferowanie rozwiązań. Aby uzyskać dostęp do tej strony opcji, wybierz**Opcje** **Narzędzia** > , a następnie wybierz**poprawki kodu** **edytora** > **F#**  > tekstu.

## <a name="code-fixes"></a>Poprawki kodu

- **Uproszczenie nazw (usuwanie niepotrzebnych kwalifikatorów)**

  Jeśli to pole wyboru jest zaznaczone, w pełni kwalifikowane nazwy są uproszczone, gdy kwalifikacje nie są konieczne, na przykład dla elementu członkowskiego często używanej przestrzeni nazw.

- **Zawsze umieszczaj otwarte instrukcje na najwyższym poziomie**

  Jeśli to pole wyboru jest zaznaczone i wpiszesz `open` instrukcję w kodzie, zostanie ona umieszczona na najwyższego poziomu.

- **Usuń nieużywane otwarte instrukcje**

  Jeśli to pole wyboru jest zaznaczone, dokumenty są analizowane pod kątem nieużywanych `open` instrukcji, a do usuwania wszystkich nieużywanych `open` instrukcji zostanie wyświetlona żarówka z szybką [akcją](../quick-actions.md) .

- **Analizowanie i sugerowanie poprawek dla nieużywanych wartości**

  Jeśli to pole wyboru jest zaznaczone, narzędzie rozpoznaje wartość, która nie jest używana w kodzie. Po umieszczeniu wskaźnika myszy na nieużywanej wartości zalecane jest, aby użyć wartości.

## <a name="see-also"></a>Zobacz także

- [Ogólne, Środowisko, Opcje — okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
- [Znajdowanie zmian w kodzie i innych elementów historii za pomocą wskaźników CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)
