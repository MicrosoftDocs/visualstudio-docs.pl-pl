---
title: 'Opcje, Edytor tekstu, F #, poprawki kodu'
description: 'Dowiedz się, jak za pomocą strony poprawki kodu w sekcji F # określić ustawienia, które mogą pomóc identyfikować błędy kodu i oferować rozwiązania.'
ms.custom: SEO-VS-2020
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 73d66e4f8611a08d6dee3733c30b075d71f6712c
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039604"
---
# <a name="options-text-editor--f--code-fixes"></a>Opcje: Edytor tekstu > F # > poprawek kodu

Strona Opcje poprawek kodu służy do określania ustawień, które mogą ułatwić identyfikację błędów kodu i oferowanie rozwiązań. Aby uzyskać dostęp do tej strony opcji **Tools**, wybierz  >  **Opcje** narzędzia, a następnie wybierz pozycję **Edytor tekstu**  >  poprawki kodu w **języku F #**  >  **Code Fixes**.

## <a name="code-fixes"></a>Poprawki kodu

- **Uproszczenie nazw (usuwanie niepotrzebnych kwalifikatorów)**

  Jeśli to pole wyboru jest zaznaczone, w pełni kwalifikowane nazwy są uproszczone, gdy kwalifikacje nie są konieczne, na przykład dla elementu członkowskiego często używanej przestrzeni nazw.

- **Zawsze umieszczaj otwarte instrukcje na najwyższym poziomie**

  Jeśli to pole wyboru jest zaznaczone i wpiszesz `open` instrukcję w kodzie, zostanie ona umieszczona na najwyższego poziomu.

- **Usuń nieużywane otwarte instrukcje**

  Jeśli to pole wyboru jest zaznaczone, dokumenty są analizowane pod kątem nieużywanych `open` instrukcji, a do usuwania wszystkich nieużywanych instrukcji zostanie wyświetlona żarówka z [szybką akcją](../quick-actions.md) `open` .

- **Analizowanie i sugerowanie poprawek dla nieużywanych wartości**

  Jeśli to pole wyboru jest zaznaczone, narzędzie rozpoznaje wartość, która nie jest używana w kodzie. Po umieszczeniu wskaźnika myszy na nieużywanej wartości zalecane jest, aby użyć wartości.

## <a name="see-also"></a>Zobacz też

- [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
- [Znajdowanie zmian w kodzie i innych elementów historii kodu za pomocą funkcji CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)
