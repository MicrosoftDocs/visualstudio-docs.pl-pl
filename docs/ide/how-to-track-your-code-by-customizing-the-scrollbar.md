---
title: Tryb mapy paska przewijania i tryb paska
ms.date: 09/25/2018
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 997f44fede7b31fe44b1e2ea28186ad52d39f443
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656581"
---
# <a name="how-to-customize-the-scroll-bar"></a>Instrukcje: Dostosowywanie paska przewijania

Podczas pracy z długimi plikami kodu może być trudno śledzić, gdzie wszystko znajduje się w pliku. Możesz dostosować pasek przewijania edytora kodu, aby uzyskać ogólny obraz tego, co dzieje się w kodzie.

## <a name="annotations"></a>Adnotacje

Możesz wybrać, czy pasek przewijania ma wyświetlać adnotacje, takie jak zmiany kodu, punkty przerwania, zakładki, błędy i położenie karetki.

   1. Otwórz stronę opcji **paski przewijania** , wybierając pozycję **narzędzia**  > **Opcje**  > **Edytor tekstu**  > **wszystkie języki**  > **paski przewijania**.

   2. Wybierz pozycję **Pokaż adnotacje na pionowym pasku przewijania**, a następnie wybierz Adnotacje, które chcesz zobaczyć. Dostępne adnotacje to:

      - zmiany
      - znaki
      - błędy
      - położenie karetki

      > [!TIP]
      > Opcja **Pokaż znaczniki** zawiera punkty przerwania i zakładki.

Wypróbuj ją, otwierając plik dużego kodu i zastępując jakiś tekst występujący w kilku miejscach w pliku. Pasek przewijania pokazuje efekt zamian, dzięki czemu można cofnąć zmiany, jeśli zamienisz coś, czego nie trzeba.

Oto jak wygląda pasek przewijania po wyszukiwaniu ciągu. Zauważ, że wszystkie wystąpienia ciągu pojawiają się na pasku przewijania.

![Pasek przewijania programu Visual Studio po wyszukiwaniu ciągu](../ide/media/enhancedscrollbarsearch.png)

Poniżej znajduje się pasek przewijania po zastąpieniu wszystkich wystąpień ciągu. Czerwone znaczniki na pasku przewijania pokazują, gdzie zastępowanie tekstu zostało wprowadzone błędy.

![Pasek przewijania programu Visual Studio po zamianie ciągu z błędami](../ide/media/enhancedscrollbarreplace.png)

## <a name="display-modes"></a>Tryby wyświetlania

Pasek przewijania ma dwa tryby: tryb paskowy i tryb mapowania.

### <a name="bar-mode"></a>Tryb paska

W *trybie paska* są wyświetlane wskaźniki adnotacji na pasku przewijania. Kliknięcie paska przewijania Przewija stronę w górę lub w dół, ale nie przechodzi do tej lokalizacji w pliku.

### <a name="map-mode"></a>Tryb mapy

W *trybie mapy*, gdy klikniesz lokalizację na pasku przewijania, kursor przejdzie do tej lokalizacji w pliku, a nie tylko przewijanie w górę lub w dół strony. Wiersze kodu są wyświetlane na pasku przewijania w miniaturach. Możesz wybrać szerokość kolumny mapy, wybierając wartość w **przeglądzie źródła**. Aby włączyć większą wersję zapoznawczą kodu po umieszczeniu wskaźnika na mapie, wybierz opcję **Pokaż podgląd etykietki narzędzia** . Zwinięte regiony są zacienione inaczej i rozszerzane po dwukrotnym kliknięciu.

> [!TIP]
> Miniaturowy widok kodu można wyłączyć w trybie mapy, ustawiając opcję **Źródło przegląd** na **off**. Jeśli zaznaczona jest **etykietka narzędzia Pokaż podgląd** , nadal zobaczysz Podgląd kodu w tej lokalizacji po umieszczeniu wskaźnika na pasku przewijania, a kursor nadal przeskakuje do tej lokalizacji w pliku po kliknięciu.

Na poniższej ilustracji przedstawiono przykład wyszukiwania, gdy tryb mapy jest włączony, a szerokość jest ustawiona na **Średni**:

![Pasek przewijania programu Visual Studio w trybie mapy](../ide/media/enhancedscrollbar.png)

Na poniższej ilustracji przedstawiono opcję **Pokaż podgląd etykietki narzędzia** :

![Pasek przewijania programu Visual Studio z etykietką](../ide/media/enhancedscrollbarsearchtooltip.png)

## <a name="see-also"></a>Zobacz także

- [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)