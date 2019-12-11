---
title: Ułatwienia dostępu
description: W tym artykule wprowadzono funkcje ułatwień dostępu w Visual Studio dla komputerów Mac oraz sposób ich włączania.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 08/15/2017
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.openlocfilehash: c0f056643a8cea0c9a5eca9801d2bd008e0793a8
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74984875"
---
# <a name="accessibility"></a>Ułatwienia dostępu

Oprócz funkcji i narzędzi w programie macOS Visual Studio dla komputerów Mac ma następujące funkcje, co sprawia, że są one bardziej dostępne dla osób niepełnosprawnych:

- Rozszerzenie tekstu w okienkach rozwiązania i edytora
- Opcje rozmiaru tekstu w edytorach
- Dostosowywanie kolorów w edytorach
- Dostosowywanie skrótów klawiatury
- Uzupełnianie kodu dla metod i parametrów

Aby uzyskać więcej informacji na temat funkcji ułatwień dostępu w programie macOS, zobacz [witrynę sieci Web firmy Apple](https://www.apple.com/accessibility/mac/).

## <a name="using-accessibility-features-in-visual-studio-for-mac"></a>Korzystanie z funkcji ułatwień dostępu w programie Visual Studio dla komputerów Mac

Funkcje ułatwień dostępu w Visual Studio dla komputerów Mac są domyślnie wyłączone. Aby je włączyć, wykonaj następujące czynności:

1. Przejdź do **preferencji > programu Visual Studio > innych ułatwień >** .

2. Zaznacz pole wyboru **Włącz dostępność** , jak pokazano na poniższym diagramie:

    ![Pole wyboru Włącz ułatwienia dostępu](media/accessibility-image1.png)

3. Naciśnij przycisk **Uruchom ponownie program Visual Studio** , aby zezwolić na działanie funkcji ułatwień dostępu.

Alternatywnie można użyć wiersza polecenia, aby włączyć funkcje ułatwień dostępu. W tym celu wprowadź następujące polecenie w terminalu:

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

Po włączeniu ułatwień dostępu należy ponownie uruchomić program Visual Studio.

## <a name="how-to-use-keyboard-navigation"></a>Instrukcje: korzystanie z nawigacji z klawiatury

Nawigowanie po klawiaturze można włączyć, ustawiając opcję pełny dostęp z klawiatury w **preferencjach systemowych > skróty klawiaturowe >** do **wszystkich kontrolek**:

![Panel Preferencje systemu w MacOS](media/accessibility-image2.png)

Ustawienie pełny dostęp z klawiatury spowoduje włączenie prostokąta fokusu. Następnie możesz wybrać kontrolki przy użyciu:

- Tab, aby przechodzić do przodu przez kontrolki
- Shift-Tab, aby przechodzić do tyłu przez kontrolki
- Klawisze strzałek do przechodzenia między kontrolkami w kierunku strzałek.

Naciśnięcie paska spacja aktywuje formant fokus.

## <a name="how-to-enable-and-use-voice-over"></a>Instrukcje: Włączanie i Używanie głosu

Włącz lub Wyłącz VoiceOver naciśnij klawisze **cmd + F5**

Aby nawigować przez polecenia interfejsu użytkownika VoiceOver, użyj następujących poleceń:

- Przenieś kursor VoiceOver między kontrolkami: **Ctrl + Alt + Strzałka w lewo/klawisz Strzałka w prawo**

   VoiceOver odczytuje nazwy kontrolek, niektóre szczegółowe informacje o niej i co można z nią zrobić.

- Wprowadź grupy i kontrolki (takie jak okienko rozwiązania, Przybornik i inne konsole): **Ctrl + Alt + Shift + Strzałka w dół**

   Po umieszczeniu wewnątrz kontrolki można poruszać się w pobliżu za pomocą **klawiszy Ctrl + Alt + strzałki** .

Aby uzyskać ogólne informacje na temat używania VoiceOver w programie macOS, zobacz następujące przewodniki:

- [Wprowadzenie z VoiceOver](https://help.apple.com/voiceover/info/guide/10.12/)
- [Polecenia VoiceOver w macOS](https://lab.dotjay.com/notes/voiceover-commands/)

## <a name="see-also"></a>Zobacz także

- [Funkcje ułatwień dostępu programu Visual Studio (w systemie Windows)](/visualstudio/ide/reference/accessibility-features-of-visual-studio)