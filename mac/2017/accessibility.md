---
title: Ułatwienia dostępu
description: W tym artykule przedstawiono funkcje ułatwień dostępu w programie Visual Studio dla komputerów Mac i jak można ją włączyć.
author: conceptdev
ms.author: crdun
ms.date: 08/15/2017
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.openlocfilehash: f90f5fca9d68ed00162fd746ddf291343c8d51f7
ms.sourcegitcommit: da73f7a0cf1795d5d400c0897ae3326191435dd0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2019
ms.locfileid: "58572986"
---
# <a name="accessibility"></a>Ułatwienia dostępu

Oprócz funkcji i narzędzi w systemie macOS Visual Studio for Mac oferuje następujące funkcje, dzięki czemu łatwiej dostępne dla osób niepełnosprawnych:

- Rozszerzenia tekst w rozwiązaniu i okienka edytora
- Opcje rozmiaru tekstu w edytorach
- Dostosowywanie kolorów w edytorach
- Dostosowywanie skrótów klawiatury
- Uzupełnianie kodu dla metody i parametrów

Aby uzyskać więcej informacji dotyczących funkcji ułatwień dostępu w systemie macOS, zobacz [witryny sieci Web firmy Apple](https://www.apple.com/accessibility/mac/).

## <a name="using-accessibility-features-in-visual-studio-for-mac"></a>Korzystanie z funkcji ułatwień dostępu w programie Visual Studio dla komputerów Mac

Funkcje ułatwień dostępu w programie Visual Studio dla komputerów Mac jest domyślnie wyłączona. Aby je włączyć, wykonaj następujące czynności:

1. Przejdź do **programu Visual Studio > Preferencje > Inne > ułatwień dostępu**.

2. Wybierz **dostępności Włącz** pole wyboru, jak pokazano na poniższym diagramie:

    ![Włącz wyboru ułatwień dostępu](media/accessibility-image1.png)

3. Naciśnij klawisz **Uruchom ponownie program Visual Studio** przycisk, aby zezwolić na te funkcje ułatwień dostępu, aby zaczęły obowiązywać.

Alternatywnie można użyć wiersza polecenia do włączania funkcji ułatwień dostępu. Aby to zrobić, wprowadź następujące polecenie w terminalu:

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

Po włączeniu ułatwień dostępu, musisz ponownie uruchomić program Visual Studio.

## <a name="how-to-use-keyboard-navigation"></a>Instrukcje: Korzystanie z nawigacji klawiatury

Nawigowanie przy użyciu klawiatury, można włączyć przez ustawienie opcji pełny dostęp za pomocą klawiatury **preferencjach systemowych > klawiatury > Skróty** do **wszystkich kontrolek**:

![Panel preferencji systemów w systemie macos](media/accessibility-image2.png)

Ustawienia klawiatury pełnego dostępu do włącza prostokąt fokusu. Następnie możesz wybrać kontrolek przy użyciu:

- TAB, aby przejść do przodu, za pomocą formantów
- Shift + Tab, aby przejść wstecz przez kontrolę nad
- Klawisze strzałek, aby przenieść między kontrolkami w kierunku strzałki.

Naciskając klawisz spacji aktywuje kontrolkę wąsko zdefiniowany.

## <a name="how-to-enable-and-use-voice-over"></a>Instrukcje: Włączanie i używanie Voice Over

Włącz VoiceOver, lub wyłącz naciśnij **Cmd + F5**

Aby przejść za pomocą poleceń VoiceOver interfejsu użytkownika, użyj następujących poleceń:

- Przesunięcie kursora VoiceOver między kontrolkami: **Ctrl + Alt + po lewej stronie Strzałka / Strzałka w prawo**

   VoiceOver odczytuje się nazwę kontrolki, niektóre szczegóły i co można zrobić z nim.

- Wprowadź grupy i formanty (na przykład konsola rozwiązań przybornika i inne konsole): **Ctrl + Alt + Shift + Strzałka w dół**

   Gdy w formancie, można użyć **Ctrl + Alt + strzałki** Aby poruszać się wewnątrz niego.

Ogólne informacje na temat używania VoiceOver w systemie macOS można znaleźć w następujących przewodnikach:

- [Wprowadzenie do VoiceOver](https://help.apple.com/voiceover/info/guide/10.12/)
- [VoiceOver poleceń w systemie macOS](http://lab.dotjay.com/notes/voiceover-commands/)

## <a name="see-also"></a>Zobacz także

- [Funkcje ułatwień dostępu w programie Visual Studio (w Windows)](/visualstudio/ide/reference/accessibility-features-of-visual-studio)