---
title: Tryb mapy paska przewijania i tryb paska
ms.date: 03/20/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c66cda1b90d11a44f744faf0012a3e41212d33dd
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "79988561"
---
# <a name="how-to-customize-the-scroll-bar"></a>Jak: Dostosowywanie paska przewijania

Podczas pracy z długimi plikami kodu może być trudno śledzić, gdzie wszystko jest w pliku. Możesz dostosować pasek przewijania edytora kodów, aby dać ogólny obraz tego, co dzieje się w kodzie.

## <a name="annotations"></a>Adnotacje

Można wybrać, czy na pasku przewijania są wyświetlane adnotacje, takie jak zmiany kodu, punkty przerwania, zakładki, błędy i położenie karetki.

   1. Otwórz stronę opcji **Paski przewijania,** wybierając pozycję**Opcje** >  **narzędzi** > **Edytor** > tekstu Wszystkie**paski przewijania****języków** > .

   2. Wybierz **pozycję Pokaż adnotacje na pionowym pasku przewijania**, a następnie wybierz adnotacje, które chcesz wyświetlić. Dostępne adnotacje to:

      - zmiany
      - znaki
      - błędy
      - pozycja cieczy

      > [!TIP]
      > Opcja **Pokaż znaczniki** zawiera punkty przerwania i zakładki.

Wypróbuj, otwierając duży plik kodu i zastępując tekst, który występuje w kilku miejscach w pliku. Pasek przewijania pokazuje efekt zamienników, dzięki czemu możesz wycofać zmiany, jeśli zastąpiono coś, czego nie powinieneś mieć.

Oto jak pasek przewijania wygląda po wyszukanie ciągu. Należy zauważyć, że wszystkie wystąpienia ciągu są wyświetlane na pasku przewijania.

![Pasek przewijania programu Visual Studio po wyszukicie ciągu](../ide/media/enhancedscrollbarsearch.png)

Oto pasek przewijania po wymianie wszystkich wystąpień ciągu. Czerwone znaki na pasku przewijania pokazują, gdzie wprowadzono błędy w wymianie tekstu.

![Pasek przewijania programu Visual Studio po zastąpieniu ciągu błędami](../ide/media/enhancedscrollbarreplace.png)

## <a name="display-modes"></a>Tryby wyświetlania

Pasek przewijania ma dwa tryby: tryb paskowy i tryb mapy.

### <a name="bar-mode"></a>Tryb prętów

*Tryb paska* wyświetla wskaźniki adnotacji na pasku przewijania. Kliknięcie paska przewijania powoduje przewijanie strony w górę lub w dół, ale nie powoduje przeskakiwania do tej lokalizacji w pliku.

### <a name="map-mode"></a>Tryb mapy

*W trybie mapy* na pasku przewijania wyświetlane są linie kodu w miniaturze. Możesz wybrać, jak szeroka jest kolumna mapy, wybierając wartość w **przeglądzie źródła**. Aby włączyć większy podgląd kodu podczas umieszczenia wskaźnika na mapie, wybierz opcję **Pokaż podgląd etykietki narzędzia.** Zwinięte regiony są inaczej zacieniowane i rozszerzane po dwukrotnym kliknięciu.

> [!TIP]
> Miniaturowy widok kodu można wyłączyć w trybie mapy, ustawiając **podgląd źródła** na **Wyłączone**. Jeśli zaznaczona jest **etykietka narzędzia Pokaż podgląd,** po kliknięciu wskaźnika na pasku przewijania nadal jest wyświetlany podgląd kodu w tej lokalizacji, a kursor nadal przechodzi do tej lokalizacji w pliku.

Na poniższej ilustracji przedstawiono przykład wyszukiwania, gdy tryb mapy jest włączony, a szerokość jest ustawiona na **Średni:**

![Pasek przewijania programu Visual Studio w trybie mapy](../ide/media/enhancedscrollbar.png)

Na poniższej ilustracji przedstawiono opcję **Pokaż etykietkę narzędzia Podgląd:**

![Pasek przewijania programu Visual Studio z etykietką narzędzia](../ide/media/enhancedscrollbarsearchtooltip.png)

> [!TIP]
> Aby zmienić kolory widoczne w trybie mapy, wybierz pozycję**Opcje** >  **narzędzi** > **Czcionki** > **i kolory**środowiska . Następnie w **pozycji Wyświetl elementy**wybierz dowolny z elementów poprzedzony "Przegląd", wykonuj żądane zmiany kolorów, a następnie wybierz przycisk **OK**.

## <a name="see-also"></a>Zobacz też

- [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)
