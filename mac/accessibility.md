---
title: Ułatwienia dostępu
description: W tym artykule wprowadzono funkcje ułatwień dostępu w Visual Studio dla komputerów Mac oraz sposób ich włączania.
author: conceptdev
ms.author: crdun
ms.date: 04/17/2019
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.openlocfilehash: 13b8d40a6ab31d7178e95a3896afa1c85c804f6c
ms.sourcegitcommit: a124076dfd6b4e5aecda4d01984fee7b0c034745
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/05/2019
ms.locfileid: "68787644"
---
# <a name="accessibility"></a>Ułatwienia dostępu

Visual Studio dla komputerów Mac ma następujące funkcje ułatwień dostępu, dzięki czemu są bardziej dostępne dla osób mających różne możliwości:

- Rozszerzenie tekstu w okienkach rozwiązania i edytora
- Opcje rozmiaru tekstu w edytorach
- Dostosowywanie kolorów w edytorach
- Nawigowanie przy użyciu klawiatury
- Dostosowywanie skrótów
- Uzupełnianie kodu dla metod i parametrów

Oprócz tych funkcji firmy Apple udostępniają wiele narzędzi, które pomagają użytkownikom z specjalnymi potrzebami, takimi jak VoiceOver i dyktowanie.

Aby uzyskać więcej informacji na temat funkcji ułatwień dostępu w programie macOS, zobacz [witrynę sieci Web firmy Apple](https://www.apple.com/accessibility/mac/).

## <a name="enabling-macos-assistive-technologies-in-visual-studio-for-mac"></a>Włączanie technologii macOS z ułatwieniami dostępu w Visual Studio dla komputerów Mac

Obsługa Visual Studio dla komputerów Mac technologii pomocniczych macOS jest domyślnie wyłączona. Aby włączyć tę procedurę, wykonaj następujące czynności:

1. Przejdź do **programu Visual Studio (menu) > preferencji > innych ułatwień dostępu >**

2. Zaznacz pole wyboru **Włącz dostępność** :

   ![Pole wyboru ułatwienia dostępu Preferencje](media/accessibility-preferences.png)

3. Wybierz przycisk **Uruchom ponownie program Visual Studio** , aby ponownie uruchomić program Visual Studio i włączyć obsługę technologii pomocniczych firmy Apple.

## <a name="how-to-use-keyboard-navigation"></a>Instrukcje: Korzystanie z nawigacji klawiaturowej

Obsługa nawigacji przy użyciu klawiatury jest wbudowana bezpośrednio w macOS, ale w celu zapewnienia najbardziej kompleksowego środowiska należy ustawić macOS do nawigowania po **wszystkich kontrolkach**:

![Preferencje systemowe — klawiatura wszystkie kontrolki](media/accessibility-preferences-keyboard.png)

Ustawienie **pełny dostęp z klawiatury** do **wszystkich kontrolek** umożliwia nawigowanie po wszystkich kontrolkach w oknie lub oknie dialogowym. Następnie możesz wybrać kontrolki przy użyciu:

- Tab, aby przechodzić do przodu przez kontrolki
- Shift-Tab, aby przechodzić do tyłu przez kontrolki
- Klawisze strzałek do przechodzenia między kontrolkami w kierunku strzałek
- Kontrolka — Poza polami obszaru tekstowego
- Naciśnięcie paska spacja aktywuje formant, który jest aktualnie fokusem.

## <a name="how-to-enable-and-use-voiceover"></a>Instrukcje: Włączanie i używanie VoiceOver

Aby włączyć lub wyłączyć VoiceOver naciśnięcie klawiszy  **&#8984; + F5**

Polecenia VoiceOver są wyświetlane w tym przewodniku jako **VO +_klucz_**  , w którym **VO** odwołuje się do modyfikatora ustawionego w aplikacji **narzędziowej VoiceOver** . Modyfikatorem domyślnym jest **Ctrl + Alt**. Na przykład w zależności od modyfikatora VoiceOver, **VO + M** oznacza kombinację **klawiszy Ctrl + Alt + M**. W przypadku zwięzłości klucze kursora będą określane jako **lewe** i praweitp.

Aby nawigować do Visual Studio dla komputerów Mac interfejsie użytkownika, należy użyć następujących kombinacji klawiszy:

- **VO + prawy/lewy**: Nawigowanie między elementami interfejsu użytkownika
  - VoiceOver ogłasza etykietę i typ kontrolki i wyjaśni, jak z niej korzystać.
- **VO + Shift + Strzałka w górę/w dół**: Wkrocz do elementu lub z niego
  - Gdy wewnątrz elementu można używać **VO + Left/Right** , aby poruszać się wokół elementów w nim.
- **VO + Spacja**: Wybierz/manipuluj z kontrolką
- **VO + M**: Korzystanie z paska menu Visual Studio dla komputerów Mac

Aby uzyskać więcej informacji na temat korzystania z VoiceOver i kompleksowej listy poleceń, zapoznaj się z następującymi przewodnikami:

- [Przewodnik Wprowadzenie firmy Apple VoiceOver](https://support.apple.com/en-us/guide/voiceover-guide/welcome/web)
- [Polecenia VoiceOver w macOS](http://lab.dotjay.com/notes/voiceover-commands/)

## <a name="see-also"></a>Zobacz także

- [Funkcje ułatwień dostępu programu Visual Studio (w systemie Windows)](/visualstudio/ide/reference/accessibility-features-of-visual-studio)
