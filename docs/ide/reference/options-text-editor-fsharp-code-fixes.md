---
title: 'Opcje, Edytor tekstu, F #, poprawki kodu'
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c20646c8da4101ac674a64c5ca1ed23a3b1fd7b5
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770932"
---
# <a name="options-text-editor--f--code-fixes"></a>Opcje: Edytor tekstu > F # > poprawek kodu

Strona Opcje poprawek kodu służy do określania ustawień, które mogą ułatwić identyfikację błędów kodu i oferowanie rozwiązań. Aby uzyskać dostęp do tej strony opcji **Tools**, wybierz  >  **Opcje**narzędzia, a następnie wybierz pozycję **Edytor tekstu**  >  poprawki kodu w**języku F #**  >  **Code Fixes**.

## <a name="code-fixes"></a>Poprawki kodu

- **Uproszczenie nazw (usuwanie niepotrzebnych kwalifikatorów)**

  Jeśli to pole wyboru jest zaznaczone, w pełni kwalifikowane nazwy są uproszczone, gdy kwalifikacje nie są konieczne, na przykład dla elementu członkowskiego często używanej przestrzeni nazw.

- **Zawsze umieszczaj otwarte instrukcje na najwyższym poziomie**

  Jeśli to pole wyboru jest zaznaczone i wpiszesz `open` instrukcję w kodzie, zostanie ona umieszczona na najwyższego poziomu.

- **Usuń nieużywane otwarte instrukcje**

  Jeśli to pole wyboru jest zaznaczone, dokumenty są analizowane pod kątem nieużywanych `open` instrukcji, a do usuwania wszystkich nieużywanych instrukcji zostanie wyświetlona żarówka z [szybką akcją](../quick-actions.md) `open` .

- **Analizowanie i sugerowanie poprawek dla nieużywanych wartości**

  Jeśli to pole wyboru jest zaznaczone, narzędzie rozpoznaje wartość, która nie jest używana w kodzie. Po umieszczeniu wskaźnika myszy na nieużywanej wartości zalecane jest, aby użyć wartości.

## <a name="see-also"></a>Zobacz także

- [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
- [Znajdowanie zmian w kodzie i innych elementów historii kodu za pomocą funkcji CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)
