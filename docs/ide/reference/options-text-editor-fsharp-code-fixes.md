---
title: Opcje, Edytor tekstu, F#, Poprawki kodu
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "72666273"
---
# <a name="options-text-editor--f--code-fixes"></a>Opcje: > > poprawki kodu > Edytor tekstu F#

Użyj opcji poprawki kodu strony, aby określić ustawienia, które mogą pomóc zidentyfikować błędy kodu i oferować rozwiązania. Aby uzyskać dostęp do tej strony opcji, wybierz pozycję**Opcje** **narzędzi** > , a następnie wybierz pozycję Poprawki**kodu** **Edytora** > tekstu**F#.** > 

## <a name="code-fixes"></a>Poprawki kodu

- **Uprość nazwy (usuń niepotrzebne kwalifikatory)**

  Jeśli to pole wyboru jest zaznaczone, w pełni kwalifikowane nazwy są uproszczone, gdy kwalifikacje nie są konieczne, na przykład dla członka często używanego obszaru nazw.

- **Zawsze umieszczaj otwarte instrukcje na najwyższym poziomie**

  Jeśli to pole wyboru jest `open` zaznaczone i wpisz instrukcję w kodzie, jest umieszczana na najwyższym poziomie.

- **Usuwanie nieużywanych otwartych instrukcji**

  Jeśli to pole wyboru jest zaznaczone, dokumenty `open` są analizowane pod kątem nieużywanych instrukcji, `open` a żarówka Szybka [akcja](../quick-actions.md) jest wyświetlana z akcją usuwania wszystkich nieużywanych instrukcji.

- **Analizowanie i sugerowanie poprawek dla nieużywanych wartości**

  Jeśli to pole wyboru jest zaznaczone, narzędzie rozpoznaje wartość, która nie jest używana w kodzie. Następnie, jeśli najedziesz kursorem myszy na nieużyną wartość, zaleca się sposoby, w których można użyć wartości.

## <a name="see-also"></a>Zobacz też

- [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
- [Znajdowanie zmian w kodzie i innych elementów historii kodu za pomocą funkcji CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)
