---
title: Ułatwienia dostępu
description: W tym artykule przedstawiono funkcje ułatwień dostępu w programie Visual Studio dla komputerów Mac i jak można ją włączyć.
author: conceptdev
ms.author: crdun
ms.date: 04/17/2019
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.openlocfilehash: 0ee6ffc7bd1567a86bc361f55e00c52ccecddd61
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824447"
---
# <a name="accessibility"></a>Ułatwienia dostępu

Programu Visual Studio dla komputerów Mac ma następujące funkcje ułatwień dostępu, dzięki czemu łatwiej dostępne dla osób z różnymi możliwościami:

- Rozszerzenia tekstu w okienka rozwiązanie i edytora
- Opcje rozmiaru tekstu w edytorach
- Dostosowywanie kolorów w edytorach
- Nawigowanie przy użyciu klawiatury
- Dostosowanie skrótów
- Uzupełnianie kodu dla metody i parametrów

Poza tymi funkcjami Apple udostępnia wiele narzędzi, aby ułatwić użytkownikom ze specjalnymi potrzebami, takie jak VoiceOver i dyktowanie.

Aby uzyskać więcej informacji dotyczących funkcji ułatwień dostępu w systemie macOS, zobacz [witryny sieci Web firmy Apple](https://www.apple.com/accessibility/mac/).

## <a name="enabling-macos-assistive-technologies-in-visual-studio-for-mac"></a>Włączanie systemu macOS technologiami pomocniczymi w programie Visual Studio dla komputerów Mac

Program Visual Studio dla komputerów Mac obsługę technologii ułatwień dostępu systemu macOS jest domyślnie wyłączona. Aby włączyć ją wykonaj następujące kroki:

1. Przejdź do **programu Visual Studio (menu) > Preferencje > Inne > ułatwień dostępu**

2. Sprawdź **dostępności Włącz** pola wyboru:

   ![Zaznacz pole wyboru preferencje ułatwień dostępu](media/accessibility-preferences.png)

3. Wybierz **Uruchom ponownie program Visual Studio** przycisk, aby ponownie uruchomić program Visual Studio i włączyć obsługę technologii ułatwień dostępu firmy Apple.

## <a name="how-to-use-keyboard-navigation"></a>Instrukcje: Korzystanie z nawigacji klawiatury

Obsługa nawigacji klawiatury jest wbudowana bezpośrednio w systemie macOS, ale aby uzyskać najbardziej kompleksowe środowisko, możesz powinni macOS Przejdź **wszystkich kontrolek**:

![Preferencje systemowe klawiatury wszystkie kontrolki](media/accessibility-preferences-keyboard.png)

Ustawienie **pełny dostęp za pomocą klawiatury** do **wszystkich kontrolek** pozwala na przechodzenie przez wszystkie formanty w oknie lub w oknie dialogowym. Następnie możesz wybrać kontrolek przy użyciu:

- TAB, aby przejść do przodu, za pomocą formantów
- Shift + Tab, aby przejść wstecz przez kontrolę nad
- Klawisze strzałek, aby przenieść między kontrolkami w kierunku strzałki
- Karty Kontrola poza obszar tekstu pola
- Naciskając klawisz spacji aktywuje kontrolkę obecnie w trybie koncentracji uwagi.

## <a name="how-to-enable-and-use-voiceover"></a>Instrukcje: Włączanie i używanie VoiceOver

Aby włączyć lub wyłączyć naciśnij VoiceOver  **&#8984; + F5**

Polecenia voiceOver pojawiają się w tym przewodniku jako **VO + *klucz*** zgodnie z którą **VO** odwołuje się do modyfikator w **VoiceOver narzędzie** aplikacji. Modyfikator domyślny jest **Ctrl + Alt**. Na przykład, w zależności od Twojego modyfikator VoiceOver **VO + M** oznacza **Ctrl + Alt + M**. Celu skrócenia programu, klawisze kursora będzie nazywany **po lewej stronie** i **po prawej stronie**itp.

Aby przejść z programu Visual Studio dla komputerów Mac interfejsu użytkownika, należy użyć następujących kombinacji klawiszy:

- **VO + prawo / lewo**: Przechodzenie między elementy interfejsu użytkownika
  - VoiceOver ogłaszamy etykiety i typ kontrolki, a wyjaśniają, jak korzystać z niego.
- **VO + Shift + dół / się**: Krok do / z elementu
  - Po wewnątrz elementu można użyć **VO + lewym / prawym** do poruszania się jego elementy.
- **VO + spacja**: Wybierz opcję / wchodzić w interakcje z kontrolką
- **VO + M**: Korzystać z programu Visual Studio dla komputerów Mac, pasek Menu

Aby uzyskać więcej informacji na temat korzystania z VoiceOver i pełną listę poleceń można znaleźć w następujących przewodnikach:

- [Apple VoiceOver Wprowadzenie — przewodnik](https://support.apple.com/en-us/guide/voiceover-guide/welcome/web)
- [VoiceOver poleceń w systemie macOS](http://lab.dotjay.com/notes/voiceover-commands/)

## <a name="see-also"></a>Zobacz także

- [Funkcje ułatwień dostępu w programie Visual Studio (w Windows)](/visualstudio/ide/reference/accessibility-features-of-visual-studio)
