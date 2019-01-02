---
title: Opcje, Edytor tekstu wszystkie języki paski przewijania
ms.date: 10/25/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Scroll_Bars
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 881f995dc8f4c675691f7eaa63d26acefd4b3d01
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53876789"
---
# <a name="options-text-editor-all-languages-scroll-bars"></a>Opcje, Edytor tekstu wszystkie języki paski przewijania
To okno dialogowe pozwala zmienić domyślne zachowanie paska przewijania w edytorze kodu. Aby wyświetlić te opcje, wybierz **opcje** z **narzędzia** menu. W ramach **edytora tekstów** folder, rozwiń węzeł **wszystkie języki** podfolder, a następnie wybierz **pasków przewijania**.

> [!CAUTION]
> Ta strona ustawia domyślne opcje dla wszystkich języków programowania. Resetowanie opcji, w tym oknie dialogowym przywróci Opcje pasków przewijania we wszystkich językach niezależnie od opcji wybranych są w tym miejscu. Aby zmienić opcje edytora tekstowego dla tylko jednego języka, rozwiń podfolder dla danego języka, a następnie wybierz jego stron opcji.

## <a name="show-horizontal-scroll-bar"></a>Pokaż pasek przewijania w poziomie

Po wybraniu Wyświetla poziomy pasek przewijania, dzięki czemu można przewijać z na boki do elementów widoku, które wykraczają poza obszar wyświetlania edytora. Jeśli poziome paski przewijania są niedostępne, można użyć klawiszy strzałek do przewijania.

## <a name="show-vertical-scroll-bar"></a>Pokaż pionowy pasek przewijania

Po wybraniu Wyświetla pionowy pasek przewijania, dzięki czemu można przewijać w górę i w dół do elementów widoku, które wykraczają poza obszar wyświetlania edytora. Jeśli pionowe paski przewijania są niedostępne, można użyć Page Up, Page Down i klawisze kursora do przewijania.

## <a name="display"></a>Monitor

### <a name="show-annotations-over-vertical-scroll-bar"></a>Pokaż adnotacje na pionowym pasku przewijania

Wybierz, czy pasek przewijania pionowego pokazuje następujących adnotacji:

- zmiany
- znaki
- błędy
- położenia karetki

> [!TIP]
> **Pokaż znaczniki** opcja powoduje dołączenie punkty przerwania i zakładki.

Wypróbuj działanie rozwiązania przez otwarcie pliku z kodem duże i zastępując tekst, który występuje w kilku miejscach w pliku. Pasek przewijania pokazuje wpływ zamiany, dzięki czemu można wycofywanie zmian użytkownika, jeśli coś, czego nie powinny mieć zastąpiony.

## <a name="behavior"></a>Zachowanie

Pasek przewijania w dwóch trybach: pasek trybu ani mapy.

### <a name="use-bar-mode-for-vertical-scroll-bar"></a>Użyj trybu paska dla pionowego paska przewijania

*Pasek tryb* Wyświetla wskaźniki adnotacji na pasku przewijania. Kliknięcie przycisku na pasku przewijania Przewija stronę w górę lub w dół, ale nie jest przenoszony do tej lokalizacji w pliku.

### <a name="use-map-mode-for-vertical-scroll-bar"></a>Użyj trybu mapy dla pionowego paska przewijania

W *tryb mapy*po kliknięciu lokalizacji na przewijania paska przechodzi kursor do tej lokalizacji w pliku, a nie po prostu przewijanie w górę lub w dół strony. Wiersze kodu są wyświetlane w postaci miniatury na pasku przewijania. Można wybrać, jaką szerokość kolumny mapy polega na wybraniu wartości w **Przegląd źródła**. Aby włączyć większy podgląd kodu, gdy wskaźnik myszy znajduje się na mapie, zaznacz **Pokaż etykietki narzędzia w wersji zapoznawczej** opcji. Zwinięte regiony są zacieniowane inaczej i rozwiń, klikając je dwukrotnie.

> [!TIP]
> Można wyłączyć widok kodu miniaturowych w trybie mapy, ustawiając **Przegląd źródła** do **poza**. Jeśli **Pokaż etykietki narzędzia w wersji zapoznawczej** jest zaznaczone, nadal widoczny jest Podgląd kodu w tym miejscu umieść wskaźnik myszy na pasku przewijania, gdy kursor nadal przechodzi do tej lokalizacji w pliku po kliknięciu.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Dostosowywanie paska przewijania](../how-to-track-your-code-by-customizing-the-scrollbar.md)