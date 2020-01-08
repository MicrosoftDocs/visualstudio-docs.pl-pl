---
title: Edycja przy użyciu wielokaretki
description: Wstaw tekst w wielu lokalizacjach podczas edytowania kodu w Visual Studio dla komputerów Mac.
author: cobey
ms.author: cobey
ms.date: 08/19/2019
ms.openlocfilehash: a21bebda057a772017fa1481e18f9801d1fbcbdf
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75451448"
---
# <a name="multi-caret-editing"></a>Edycja przy użyciu wielokaretki

Edycja z obsługą wielu karetki pozwala na jednorazowe dodanie _n_ numerów punktów wstawiania. W trybie wielodostępnym można dodawać kolejne karetke do dokumentu za pośrednictwem kliknięć myszą lub za pomocą poleceń klawiatury. Pierwszy karetka jest wskazywany przez czerwony kursor, podczas gdy pomocnicze karetke obecne w kolorze jasnoniebieskim. Tryb edycji z wielokaretką można wyłączyć za pomocą klucza `ESC`.

## <a name="enabling-multi-caret-editing"></a>Włączanie edycji z zastosowaniem wielokaretki

### <a name="keyboard"></a>Klawiatura

Możesz włączyć tryb wielu karetki za pośrednictwem klawiatury na kilka sposobów. Poniższa tabela zawiera skróty klawiaturowe dostępne do wprowadzania określonych trybów edycji wielokaretki:

| Klawisz skrótu  | Akcja                        | 
|---------| ------------------------------|
|  ⌥⇧.   | Wstaw następny pasujący karetkę    | 
|  ⌥⇧;   | Wstaw karetkę we wszystkich dopasowaniach | 
|  ⌥⇧,   | Usuń ostatni karetkę             | 
|  ⌥⇧/   | Przesuń ostatni karetkę w dół          | 

Każdy z tych zachowań jest zakotwiczony do bieżącej pozycji karetki, gdy wywołasz polecenie. Na przykład, jeśli karetka znajduje się na początku słowa "name" i wywołujesz polecenie "Wstaw karetke we wszystkich dopasowaniach" (⌥ ⇧;) Każde wystąpienie słowa "name" w bieżącym dokumencie będzie miało karetkę wstawioną na początku wyrazu. Podobnie, jeśli wywołasz polecenie "Wstaw następny pasujący karetkę" (⌥ ⇧), karetka zostanie umieszczona w następnym wystąpieniu słowa "name" (nazwa). To polecenie można wywołać wiele razy.

![Klawiatura z wielokaretką](media/multi-caret-keyboard.gif)

## <a name="mousetouchpad"></a>Mysz/płytka dotykowa

Za pomocą kursora można bezpłatnie wybierać punkty wstawiania dla wielu karetki. Chociaż skróty klawiaturowe są powiązane z pasującymi ciągami, można ręcznie wstawić karetkę w dowolnym miejscu w dokumencie za pomocą kursora. Po ustawieniu karetki, każda z nich będzie echo wpisów kluczy wpisywanych na klawiaturze.

Aby użyć myszy do wstawienia wielu karetki, musisz nacisnąć i trzymać ⌘ ⌥ i kliknąć miejsce, w którym chcesz wprowadzić karetkę. Będziesz w trybie wstawiania, dopóki klucze ⌥ ⌘ są przechowywane. Jeśli wstawisz karetkę do nieprawidłowej lokalizacji, możesz usunąć karetkę, kontynuując ⌘ ⌥ i klikając w tym samym obszarze ponownie. Gdy wszystkie karetke znajdują się w tym miejscu, Zatrzymaj naciskanie klawiszy ⌘ ⌥ i zacznij pisać. Poniższy GIF ilustruje zarówno wybranie zestawu punktów wstawiania, jak i usunięcie błędnie ustawionych punktów.

![mysz wielokaretka](media/multi-caret-mouse.gif)

## <a name="see-also"></a>Zobacz także

- [Szybkie akcje (Visual Studio w systemie Windows)](/visualstudio/ide/quick-actions)
- [Kod refaktoryzacji (Visual Studio w systemie Windows)](/visualstudio/ide/refactoring-in-visual-studio)
