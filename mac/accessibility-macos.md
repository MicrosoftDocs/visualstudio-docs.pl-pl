---
title: Korzystanie z opcji ułatwień dostępu macOS
description: Korzystanie z opcji i funkcji ułatwień dostępu macOS, takich jak wysoki kontrast, Nawigacja po klawiaturze i VoiceOver
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/23/2019
ms.assetid: 598FC25A-6DA3-44BB-B128-AD979E9F86EA
ms.topic: how-to
ms.openlocfilehash: 6796ab12716d1d2f3ec2570c32b410c8360b8a81
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998389"
---
# <a name="accessibility-features-of-macos"></a>Funkcje ułatwień dostępu w programie macOS

macOS to dostępny system operacyjny z szeregiem funkcji, które ułatwiają użytkownikom różne możliwości. Te funkcje obejmują tryb dużego kontrastu, nawigację klawiatury i VoiceOver (czytnik ekranu macOS).

## <a name="enable-accessibility-features"></a>Włącz funkcje ułatwień dostępu

W Visual Studio dla komputerów Mac obsługa technologii pomocniczych jest domyślnie wyłączona. Aby włączyć obsługę ułatwień dostępu:

1. Przejdź do pozycji Preferencje **programu Visual Studio (menu)**  >  **Preferences**  >  **inne** i wybierz pozycję **ułatwienia dostępu**.

1. Zaznacz pole wyboru **Włącz ułatwienia dostępu** .

   ![Zrzut ekranu z preferencjami dostępności z wybraną opcją Włącz ułatwienia dostępu](media/accessibility-preferences.png)

1. Wybierz pozycję **Uruchom ponownie program Visual Studio** , aby włączyć obsługę technologii pomocniczych firmy Apple.

Alternatywnie można użyć wiersza polecenia, aby włączyć funkcje ułatwień dostępu. W tym celu wprowadź następujące polecenie w terminalu:

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

Po zmianie tego ustawienia za pomocą wiersza polecenia konieczne będzie ponowne uruchomienie programu Visual Studio.

## <a name="increase-the-contrast-in-macos"></a>Zwiększ kontrast w macOS

Visual Studio dla komputerów Mac obsługuje zwiększony kontrast w macOS, zwiększając kontrast elementów interfejsu użytkownika i wprowadzając konspekty bardziej zdefiniowane. Aby włączyć to:

1. Otwórz okno **preferencji systemu**.

1. Przejdź do pozycji **ułatwienia dostępu**, a następnie wybierz pozycję **Wyświetl**.

1. Zaznacz pole wyboru **Zwiększ kontrast** .
