---
title: Edycja przy użyciu wielokaretki
description: Wstaw tekst w wielu lokalizacjach podczas edytowania kodu w programie Visual Studio dla komputerów Mac.
author: cobey
ms.author: cobey
ms.date: 08/19/2019
ms.openlocfilehash: a21bebda057a772017fa1481e18f9801d1fbcbdf
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451448"
---
# <a name="multi-caret-editing"></a>Edycja przy użyciu wielokaretki

Edycja wielodyszowa umożliwia dodawanie _n_ liczby punktów wstawiania w jednym czasie. W trybie wielodyszowym można dodać dodatkowe daszki do dokumentu za pomocą kliknięć myszą lub za pomocą poleceń klawiaturowych. Główną opiekę nadają czerwony kursor, podczas gdy pomocnicze opiekunki są obecne w kolorze jasnoniebieskim. Tryb edycji wielu dań można `ESC` wyłączyć za pomocą klawisza.

## <a name="enabling-multi-caret-editing"></a>Włączanie edycji wielodyskowej

### <a name="keyboard"></a>Klawiatura

Możesz włączyć tryb wielodyszowy za pomocą klawiatury na kilka sposobów. Poniższa tabela zawiera skróty klawiaturowe dostępne do wprowadzania określonych trybów edycji wielodyscypowy:

| Hotkey  | Akcja                        | 
|---------| ------------------------------|
|  ⌥⇧.   | Wstawianie następnej pasującej cieczy    | 
|  ⌥⇧;   | Wstaw cieszczki w każdym pasującym | 
|  ⌥⇧,   | Usuń ostatnią ciecz             | 
|  ⌥⇧/   | Przenieś ostatnią szedę w dół          | 

Każde z tych zachowań są zakotwiczone w bieżącej pozycji daszka podczas wywoływania polecenia. Na przykład, jeśli daszek znajduje się na początku słowa "name" i wywołasz "Wstaw cieptki przy wszystkich pasujących" (;) każde wystąpienie słowa "nazwa" w bieżącym dokumencie będzie miało cieszkę wstawioną na początku wyrazu. Podobnie, jeśli wywołasz polecenie "Wstaw następny pasująca dacie" (♡♡) wówczas w następnym wystąpieniu wyrazu "name". To polecenie można wywołać wiele razy.

![klawiatura wielodrogowa](media/multi-caret-keyboard.gif)

## <a name="mousetouchpad"></a>Mysz/płytka dotykowa

Za pomocą kursora możesz uwolnić wybrane określone punkty wstawiania dla wielu pielęjców. Gdy skróty klawiaturowe są powiązane z pasującymi ciągami, można ręcznie wstawić daszkownika w dowolnym miejscu dokumentu za pomocą kursora. Po ustawieniu daszków każdy będzie powtarzał wpisy klawiszy wpisy na klawiaturze.

Aby użyć myszy do wstawienia wielu daszków, należy nacisnąć i przytrzymać i kliknąć miejsce, w którym chcesz wprowadzić daszki. Będziesz w trybie wstawiania tak długo, jak długo przechowywane są klawisze. Jeśli wstawisz karetkę w niewłaściwym miejscu, możesz usunąć karetkę, kontynuując przytrzymanie i ponowne kliknięcie w tym samym obszarze. Po tym, jak wszystkie daszki znajdują się tam, gdzie chcesz, przestań naciskać klawisze i zacznij pisać. Poniższy GIF pokazuje zarówno wybór zestawu punktów wstawiania, jak i usunięcie błędnie nastaw.

![mysz wielodyszowa](media/multi-caret-mouse.gif)

## <a name="see-also"></a>Zobacz też

- [Szybkie akcje (Visual Studio w systemie Windows)](/visualstudio/ide/quick-actions)
- [Kod refaktoryzatora (Visual Studio w systemie Windows)](/visualstudio/ide/refactoring-in-visual-studio)
