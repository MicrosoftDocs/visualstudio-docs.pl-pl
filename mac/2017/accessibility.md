---
title: Ułatwienia dostępu
description: W tym artykule przedstawiono funkcje ułatwień dostępu w programie Visual Studio dla komputerów Mac i jak można je włączyć.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 08/15/2017
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.openlocfilehash: c0f056643a8cea0c9a5eca9801d2bd008e0793a8
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "79301686"
---
# <a name="accessibility"></a>Ułatwienia dostępu

Oprócz funkcji i narzędzi w systemie macOS program Visual Studio dla komputerów Mac ma następujące funkcje, dzięki czemu jest bardziej dostępny dla osób niepełnosprawnych:

- Rozszerzenie tekstu w rozwiązaniu i podkładkach edytora
- Opcje rozmiaru tekstu w edytorach
- Dostosowywanie kolorów w edytorach
- Dostosowywanie skrótów klawiaturowych
- Uzupełnianie kodu dla metod i parametrów

Aby uzyskać więcej informacji na temat funkcji ułatwień dostępu w systemie macOS, zobacz [witrynę firmy Apple](https://www.apple.com/accessibility/mac/)w sieci Web .

## <a name="using-accessibility-features-in-visual-studio-for-mac"></a>Korzystanie z funkcji ułatwień dostępu w programie Visual Studio dla komputerów Mac

Funkcje ułatwień dostępu w programie Visual Studio dla komputerów Mac są domyślnie wyłączone. Aby je włączyć, wykonaj następujące czynności:

1. Przejdź do **programu Visual Studio > preferencje > inne > ułatwień dostępu**.

2. Zaznacz pole wyboru **Włącz ułatwienia dostępu,** jak pokazano na poniższym diagramie:

    ![Pole wyboru Włącz ułatwienia dostępu](media/accessibility-image1.png)

3. Naciśnij przycisk **Uruchom ponownie program Visual Studio,** aby umożliwić korzystanie z funkcji ułatwień dostępu.

Alternatywnie można użyć wiersza polecenia, aby włączyć funkcje ułatwień dostępu. Aby to zrobić, wprowadź następujące polecenie w terminalu:

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

Po włączeniu ułatwień dostępu należy ponownie uruchomić program Visual Studio.

## <a name="how-to-use-keyboard-navigation"></a>Jak: Korzystanie z nawigacji za pomocą klawiatury

Nawigację za pomocą klawiatury można włączyć, ustawiając opcję Pełny dostęp do klawiatury w **preferencjach systemowych > klawiatury > skróty** do **wszystkich kontrolek:**

![Panel preferencji systemowych w macos](media/accessibility-image2.png)

Ustawienie pełnego dostępu do klawiatury włącza prostokąt fokusu. Następnie można wybrać kontrolki za pomocą:

- Tabulator, aby przejść do przodu za pomocą kontrolek
- Shift-Tab, aby przejść do tyłu za pomocą kontrolek
- Klawisze strzałek, aby przejść między formantami w kierunku strzałek.

Naciśnięcie paska spacji aktywuje formant.

## <a name="how-to-enable-and-use-voice-over"></a>Jak: Włączanie i używanie funkcji Voice Over

Włączanie lub wyłączanie **Cmd + F5** funkcji VoiceOver

Aby poruszać się po poleceniach UI VoiceOver, należy użyć następujących poleceń:

- Przesuń kursor VoiceOver między kontrolkami: **Ctrl + Alt + klawisz strzałki w lewo / klawisz strzałki w prawo**

   VoiceOver odczytuje nazwę elementów sterujących, niektóre szczegóły na ten temat i co można z nim zrobić.

- Wprowadzanie grup i kontrolek (takich jak skrzynka rozrachowa, przybornik i inne klocki): **Ctrl + Alt + Shift + Strzałka w dół**

   Po wejściu do formantu można użyć **klawiszy Ctrl + Alt + Arrows,** aby poruszać się wewnątrz niego.

Aby uzyskać ogólne informacje na temat korzystania z funkcji VoiceOver w systemie macOS, zapoznaj się z następującymi przewodnikami:

- [Wprowadzenie do voiceover](https://help.apple.com/voiceover/info/guide/10.12/)
- [Polecenia VoiceOver w systemie macOS](https://lab.dotjay.com/notes/voiceover-commands/)

## <a name="see-also"></a>Zobacz też

- [Funkcje ułatwień dostępu programu Visual Studio (w systemie Windows)](/visualstudio/ide/reference/accessibility-features-of-visual-studio)