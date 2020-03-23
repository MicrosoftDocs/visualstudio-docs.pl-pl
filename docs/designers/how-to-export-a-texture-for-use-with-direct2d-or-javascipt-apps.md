---
title: Eksportowanie tekstury dla aplikacji Direct2D i JavaScript
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 241c25fe-764e-4e1b-ad32-b1377dcbb605
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d163aafa8b00ce1d59b1fc7b597ab5ca535a1ee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "72635510"
---
# <a name="how-to-export-a-texture-for-use-with-direct2d-or-javascript-apps"></a>Jak: Eksportowanie tekstury do użytku z aplikacjami Direct2D lub JavaScript

Potok zawartości obrazu może generować tekstury, które są zgodne z wewnętrznymi konwencjami renderowania Direct2D. Tekstury tego rodzaju nadają się do użytku w aplikacjach korzystających z funkcji Direct2D oraz w aplikacjach platformy uniwersalnej systemu Windows utworzonych za pomocą języka JavaScript.

W tym dokumencie przedstawiono następujące działania:

- Konfigurowanie obrazu źródłowego do przetworzenia przez potok zawartości obrazu.

- Konfigurowanie potoku zawartości obrazu w celu wygenerowania tekstury, której można używać w aplikacji Direct2D lub JavaScript.

  - Generowanie pliku *dds* skompresowanego przez blok.

  - Generowanie wstępniemultiplied alfa.

  - Wyłącz generowanie mipmap.

## <a name="rendering-conventions-in-direct2d"></a>Konwencje renderowania w direct2d

Tekstury używane w kontekście Direct2D muszą być zgodne z tymi wewnętrznymi konwencjami renderowania Direct2D:

- Direct2D implementuje przezroczystość i przezroczystość przy użyciu wstępniemultiplied alfa. Tekstury używane z Direct2D muszą zawierać wstępnie nagraną alfa, nawet jeśli tekstura nie używa przezroczystości ani przezroczystości. Aby uzyskać więcej informacji na temat wstępniemultiplied alfa, zobacz [Jak: Eksportowanie tekstury, która ma wstępniemultiplied Alpha](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md).

- Tekstura musi być dostarczana w formacie *.dds* przy użyciu jednego z następujących formatów kompresji blokowej:

  - kompresja BC1_UNORM

  - kompresja BC2_UNORM

  - kompresja BC3_UNORM

- Mipmaps nie są obsługiwane.

### <a name="to-create-a-texture-thats-compatible-with-direct2d-rendering-conventions"></a>Aby utworzyć teksturę zgodną z konwencjami renderowania Direct2D

1. Zacznij od podstawowej tekstury. Załaduj istniejący obraz lub utwórz nowy obraz, zgodnie z opisem w [: Jak: Utwórz teksturę podstawową](../designers/how-to-create-a-basic-texture.md). Aby obsługiwać kompresję blokową w formacie *.dds,* należy określić teksturę o szerokości i wysokości, która ma wielokrotność czterech rozmiarów, na przykład 100x100, 128x128 lub 256x192. Ponieważ mipmapping nie jest obsługiwany, tekstura nie musi być kwadratowa i nie musi być potęgą dwóch rozmiarów.

2. Skonfiguruj plik tekstury tak, aby był przetwarzany przez potok zawartości obrazu. W **Eksploratorze rozwiązań**otwórz menu skrótów dla właśnie utworzonego pliku tekstury, a następnie wybierz polecenie **Właściwości**. Na stronie **Właściwości konfiguracji** > **ogólne** ustaw właściwość Typ **elementu** na Potok **zawartości obrazu**. Upewnij się, że właściwość **Content** jest ustawiona na **Tak,** a **opcja Wyklucz z kompilacji** jest ustawiona na **Nie**, a następnie wybierz przycisk **Zastosuj.** Zostanie wyświetlona strona właściwości właściwości konfiguracji **potoku zawartości** obrazu.

3. Ustaw format wyjściowy na jeden z formatów skompresowanych blokami. Na stronie**Ogólne** **potoku zawartości** > obrazu **właściwości konfiguracji** > ustaw właściwość **Kompresuj** na **kompresję BC3_UNORM (/kompresuj:BC3_UNORM)**. W zależności od wymagań można wybrać dowolny z pozostałych formatów BC1, BC2 lub BC3. Direct2D obecnie nie obsługuje tekstur BC4, BC5, BC6 ani BC7. Aby uzyskać więcej informacji na temat różnych formatów BC, zobacz [Blokowanie kompresji (Direct3D 10)](/windows/desktop/direct3d10/d3d10-graphics-programming-guide-resources-block-compression).

   > [!NOTE]
   > Określony format kompresji określa format pliku, który jest produkowany przez potok zawartości obrazu. Jest to inna niż właściwość **Format** obrazu źródłowego w Edytorze obrazów, która określa format pliku obrazu źródłowego przechowywanego na dysku — czyli *format roboczy*. Zazwyczaj nie chcesz formatu roboczego, który jest skompresowany.

4. Skonfiguruj potok zawartości obrazu do produkcji danych wyjściowych, które używają wstępniemultiplied alfa. Na stronie**Ogólne**  > **potoku** > zawartości obrazu właściwości **Właściwości Konwertuj**na **wstępnie pomnożone w formacie alfa** na **Tak (/generatepremultipliedalpha)**.

5. Skonfiguruj potok zawartości obrazu, aby nie generował mipmaps. Na stronie**Ogólne** **potoku zawartości** > obrazu **właściwości konfiguracji** > ustaw właściwość **Generowanie mips** na **Nie**.

6. Wybierz przycisk **OK.**

   Podczas tworzenia projektu potok zawartości obrazu konwertuje obraz źródłowy z formatu roboczego na określony format wyjściowy — konwersja obejmuje generowanie wstępniemulatowanych alfa — a wynik jest kopiowany do katalogu wyjściowego projektu.
