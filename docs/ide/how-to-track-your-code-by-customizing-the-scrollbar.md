---
title: Tryb mapy paska przewijania i tryb paska
ms.date: 09/25/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77f7db396b814eb9163c055b8fadb8793432acee
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55948359"
---
# <a name="how-to-customize-the-scroll-bar"></a>Instrukcje: Dostosowywanie paska przewijania

Podczas pracy z plikami kodu długo może być trudno jest śledzić, gdzie wszystko, co znajduje się w pliku. Można dostosować pasek przewijania w edytorze kodu, aby zapewnić ogólny obraz, co się dzieje w kodzie.

## <a name="annotations"></a>Adnotacje

Możesz wybrać, czy pasek przewijania pokazuje adnotacji, takie jak zmiany kodu, punkty przerwania, zakładek, błędy i położeniu karetki.

   1. Otwórz **pasków przewijania** Strona opcji, wybierając **narzędzia** > **opcje** > **edytora tekstów**  >  **Wszystkie języki** > **pasków przewijania**.

   2. Wybierz **Pokaż adnotacje na pionowym pasku przewijania**, a następnie wybierz pozycję adnotacji mają być wyświetlane. Adnotacje dostępne są następujące:

      - zmiany
      - znaki
      - błędy
      - położenia karetki

      > [!TIP]
      > **Pokaż znaczniki** opcja powoduje dołączenie punkty przerwania i zakładki.

Wypróbuj działanie rozwiązania przez otwarcie pliku z kodem duże i zastępując tekst, który występuje w kilku miejscach w pliku. Pasek przewijania pokazuje wpływ zamiany, dzięki czemu można wycofywanie zmian użytkownika, jeśli coś, czego nie powinny mieć zastąpiony.

Poniżej przedstawiono wygląd paska przewijania po wyszukiwanie ciągu. Należy zauważyć, że wszystkie wystąpienia ciągu są wyświetlane na pasku przewijania.

![Visual Studio pasek przewijania po zakończeniu wyszukiwania dla ciągu](../ide/media/enhancedscrollbarsearch.png)

Oto pasek przewijania po zastąpieniu wszystkie wystąpienia ciągu. Czerwony znaczniki w Pokaż pasek przewijania, gdzie zastępowanie tekstu wprowadzone błędy.

![Visual Studio pasek przewijania po zastąpieniu ciągu z błędami](../ide/media/enhancedscrollbarreplace.png)

## <a name="display-modes"></a>Tryby wyświetlania

Pasek przewijania w dwóch trybach: pasek trybu ani mapy.

### <a name="bar-mode"></a>Pasek tryb

*Pasek tryb* Wyświetla wskaźniki adnotacji na pasku przewijania. Kliknięcie przycisku na pasku przewijania Przewija stronę w górę lub w dół, ale nie jest przenoszony do tej lokalizacji w pliku.

### <a name="map-mode"></a>Tryb mapy

W *tryb mapy*po kliknięciu lokalizacji na przewijania paska przechodzi kursor do tej lokalizacji w pliku, a nie po prostu przewijanie w górę lub w dół strony. Wiersze kodu są wyświetlane w postaci miniatury na pasku przewijania. Można wybrać, jaką szerokość kolumny mapy polega na wybraniu wartości w **Przegląd źródła**. Aby włączyć większy podgląd kodu, gdy wskaźnik myszy znajduje się na mapie, zaznacz **Pokaż etykietki narzędzia w wersji zapoznawczej** opcji. Zwinięte regiony są zacieniowane inaczej i rozwiń, klikając je dwukrotnie.

> [!TIP]
> Można wyłączyć widok kodu miniaturowych w trybie mapy, ustawiając **Przegląd źródła** do **poza**. Jeśli **Pokaż etykietki narzędzia w wersji zapoznawczej** jest zaznaczone, nadal widoczny jest Podgląd kodu w tym miejscu umieść wskaźnik myszy na pasku przewijania, gdy kursor nadal przechodzi do tej lokalizacji w pliku po kliknięciu.

Na poniższej ilustracji przedstawiono przykład wyszukiwania, gdy tryb mapy jest włączony i jest równa szerokości **średni**:

![Visual Studio pasek przewijania w trybie mapy](../ide/media/enhancedscrollbar.png)

Na poniższej ilustracji przedstawiono **Pokaż etykietki narzędzia w wersji zapoznawczej** opcji:

![Visual Studio pasek przewijania z etykietki narzędzia](../ide/media/enhancedscrollbarsearchtooltip.png)

## <a name="see-also"></a>Zobacz także

- [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)