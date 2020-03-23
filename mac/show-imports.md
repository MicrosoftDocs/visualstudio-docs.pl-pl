---
title: Pokaż elementy importu
description: Użyj pokaż elementów importu, aby rozwinąć intellisense w programie Visual Studio dla komputerów Mac.
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 964fbbf2f46e2495184b01c47cba888a93f24ea8
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451511"
---
# <a name="show-import-items"></a>Pokaż elementy importu

Program Visual Studio dla komputerów Mac może wyświetlać wszystkie dostępne typy, nawet jeśli nie są importowane do projektu, na liście uzupełniania IntelliSense. Wybierając element, który nie jest importowany, `using` do pliku źródłowego zostanie dodana poprawna instrukcja.

![pokaż omówienie importu elementów](media/importitems-overview.gif)

## <a name="how-to-enable"></a>Jak włączyć

Aby włączyć tę funkcję, otwórz **preferencje** za pośrednictwem **programu Visual Studio** > **Preferences** i przejdź do **edytora** > tekstu**IntelliSense**. Zaznacz pole **Pokaż elementy importu,** aby włączyć dodatkowe elementy w programie IntelliSense.

![pokaż opcję importuj towary](media/show-import-items.png)

## <a name="usage"></a>Sposób użycia

Po włączeniu **opcji Pokaż importowanie towarów**proces importowania elementu za pomocą funkcji jest podobny do normalnych akcji w programie IntelliSense. Podczas wpisywania kodu elementy, które są prawidłowe, wypełnią listę uzupełnień. Obejmuje to elementy, które nie zostały jeszcze zaimportowane. Elementy, które nie są importowane będą wyświetlane ich pełny obszar nazw po prawej stronie elementu, dzięki czemu można zobaczyć, które importuje się do projektu.

![pokaż listę elementów importu](media/show-import-items-list.png)

Na liście IntelliSense obszary nazw są wyświetlane obok elementów członkowskich, `using` do których nie odwołuje się obecnie instrukcja. Jeśli wybierzesz jeden z tych elementów z listy, element `using` członkowski zostanie dodany do _kodu, a_ instrukcja zostanie dodana do górnej części pliku. Członkowie z typów już odwołuje się w kodowane nie będą wyświetlane ich obszaru nazw w IntelliSense.

## <a name="see-also"></a>Zobacz też

- [Szybkie akcje (Visual Studio w systemie Windows)](/visualstudio/ide/quick-actions)
- [Kod refaktoryzatora (Visual Studio w systemie Windows)](/visualstudio/ide/refactoring-in-visual-studio)
