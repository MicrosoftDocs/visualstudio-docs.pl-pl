---
title: Podgląd zmian kodu
ms.date: 12/16/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.codefix.previewchanges
ms.workload:
- multiple
ms.openlocfilehash: f45b186153b4cc046d35fd941f6a80e108476fc0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585772"
---
# <a name="preview-changes-window"></a>Okno Zmiany podglądu

Podczas korzystania z różnych *szybkich akcji* lub *refaktoryzacji* narzędzi w programie Visual Studio, często jest możliwe do podglądu zmian, które mają być wprowadzone do projektu przed ich zaakceptowaniem. Okno **Zmiany podglądu** jest w miejscu, w którym jest to zrobione.  Na przykład w tym miejscu znajduje się okno **Zmiany podglądu** pokazujące, co zostanie zmienione podczas refaktoryzatora zmień nazwę w projekcie języka C#:

![Podgląd zmian](media/previewchanges.png)

W górnej połowie okna są wyświetlane określone wiersze, które zostaną zmienione, z których każda ma pole wyboru. Można zaznaczyć lub odznaczyć każde pole wyboru, jeśli chcesz selektywnie zastosować refaktoryzowanie tylko do określonych wierszy.

W dolnej połowie okna jest wyświetlany sformatowany kod z projektu, który zostanie zmieniony, z wyróżnionymi obszarami, których dotyczy problem. Wybranie konkretnej linii w górnej połowie okna spowoduje podświetlenie odpowiedniej linii w dolnej połowie. Dzięki temu można szybko przejść do odpowiedniego wiersza i zobaczyć otaczający kod.

Po zapoznaniu się ze zmianami kliknij przycisk **Zastosuj,** aby zatwierdzić te zmiany, lub kliknij przycisk **Anuluj,** aby pozostawić rzeczy takie, które były.

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja w programie Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Szybkie akcje](../ide/quick-actions.md)
