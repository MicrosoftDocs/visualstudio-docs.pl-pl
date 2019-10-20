---
title: Opcje, Edytor tekstu, F#, poprawki kodu
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a5c736be59c257d98085831971d6b7b9dc2a0ef3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666273"
---
# <a name="options-text-editor--f--code-fixes"></a>Opcje: Edytor tekstu > F# > poprawek kodu

Strona Opcje poprawek kodu służy do określania ustawień, które mogą ułatwić identyfikację błędów kodu i oferowanie rozwiązań. Aby uzyskać dostęp do tej strony opcji, wybierz pozycję **narzędzia**  > **Opcje**, a następnie wybierz**F#** pozycję **Edytor tekstu**  >   > **poprawki kodu**.

## <a name="code-fixes"></a>Poprawki kodu

- **Uproszczenie nazw (usuwanie niepotrzebnych kwalifikatorów)**

  Jeśli to pole wyboru jest zaznaczone, w pełni kwalifikowane nazwy są uproszczone, gdy kwalifikacje nie są konieczne, na przykład dla elementu członkowskiego często używanej przestrzeni nazw.

- **Zawsze umieszczaj otwarte instrukcje na najwyższym poziomie**

  Jeśli to pole wyboru jest zaznaczone i wpiszesz instrukcję `open` w kodzie, zostanie ona umieszczona na najwyższego poziomu.

- **Usuń nieużywane otwarte instrukcje**

  Jeśli to pole wyboru jest zaznaczone, dokumenty są analizowane pod kątem nieużywanych instrukcji `open` i zostanie wyświetlona żarówka [z akcją](../quick-actions.md) usuwania wszystkich nieużywanych instrukcji `open`.

- **Analizowanie i sugerowanie poprawek dla nieużywanych wartości**

  Jeśli to pole wyboru jest zaznaczone, narzędzie rozpoznaje wartość, która nie jest używana w kodzie. Po umieszczeniu wskaźnika myszy na nieużywanej wartości zalecane jest, aby użyć wartości.

## <a name="see-also"></a>Zobacz także

- [Ogólne, Środowisko, Opcje — okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
- [Znajdowanie zmian w kodzie i innych elementów historii za pomocą wskaźników CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)
