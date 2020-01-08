---
title: Pokaż elementy importu
description: Użyj opcji Pokaż elementy importu, aby rozwinąć IntelliSense w Visual Studio dla komputerów Mac.
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 964fbbf2f46e2495184b01c47cba888a93f24ea8
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75451511"
---
# <a name="show-import-items"></a>Pokaż elementy importu

Visual Studio dla komputerów Mac mogą pokazać wszystkie dostępne typy, nawet jeśli nie są one zaimportowane do projektu, na liście uzupełniania IntelliSense. Wybierając element, który nie jest importowany, poprawna `using` instrukcja zostanie dodana do pliku źródłowego.

![Pokaż przegląd elementów importu](media/importitems-overview.gif)

## <a name="how-to-enable"></a>Jak włączyć

Aby włączyć tę funkcję, Otwórz **Preferencje** za pośrednictwem **programu Visual Studio** > **Preferences** i przejdź do **edytora tekstu** > **IntelliSense**. Zaznacz pole wyboru **Pokaż elementy importu** , aby włączyć dodatkowe elementy w IntelliSense.

![Pokaż opcję importowania elementów](media/show-import-items.png)

## <a name="usage"></a>Pomiar

Po włączeniu opcji **Pokaż elementy importu**proces używania funkcji importowania elementu jest podobny do normalnego działania w ramach technologii IntelliSense. Gdy wpiszesz kod, elementy, które są prawidłowe, zostaną wypełnione listą uzupełniania. Obejmuje to elementy, które nie zostały jeszcze zaimportowane. Elementy, które nie zostały zaimportowane, będą zawierać pełną przestrzeń nazw po prawej stronie elementu, co pozwala zobaczyć, które Importy są ściągane do projektu.

![Pokaż listę elementów importu](media/show-import-items-list.png)

Na liście IntelliSense obszary nazw są wyświetlane obok elementów członkowskich, do których obecnie nie odwołują się instrukcje `using`. W przypadku wybrania jednego z tych elementów z listy element członkowski zostanie dodany do kodu, _a_ instrukcja `using` zostanie dodana na początku pliku. Elementy członkowskie z typów, do których już odwołują się odwołania, nie będą pokazywały ich przestrzeni nazw w IntelliSense.

## <a name="see-also"></a>Zobacz także

- [Szybkie akcje (Visual Studio w systemie Windows)](/visualstudio/ide/quick-actions)
- [Kod refaktoryzacji (Visual Studio w systemie Windows)](/visualstudio/ide/refactoring-in-visual-studio)
