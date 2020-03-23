---
title: 'Porady: tworzenie tekstury podstawowej'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0222e8bf-d29f-421b-9b1f-123d500fa179
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 916be87824a86e96d6fcb791cf8181d70e1e8104
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589461"
---
# <a name="how-to-create-a-basic-texture"></a>Instrukcje: tworzenie tekstury podstawowej

W tym artykule pokazano, jak za pomocą Edytora obrazów utworzyć podstawową teksturę, w tym następujące działania:

- Ustawianie rozmiaru tekstury

- Ustawianie kolorów pierwszego planu i tła

- Korzystanie z kanału alfa (przezroczystość)

- Korzystanie z narzędzi **Wypełnienie** i **Elipsa**

- Ustawianie właściwości narzędzia

## <a name="create-a-basic-texture"></a>Tworzenie tekstury podstawowej

Za pomocą Edytora obrazów można tworzyć i modyfikować obrazy i tekstury dla gry lub aplikacji.

Poniższe kroki pokazują, jak utworzyć teksturę, która reprezentuje "strzał w dziesiątkę" cel. Po zakończeniu tekstura powinna wyglądać jak na poniższym obrazie. Aby lepiej zademonstrować przezroczystość tekstury, Edytor obrazów został skonfigurowany do używania zielonego wzoru w kratkę do jego wyświetlania.

![Cel "Bullseye" z przezroczystością pokazaną na zielono](../designers/media/digit-bullseye-texture-in-editor.png)

Przed rozpoczęciem upewnij się, że jest wyświetlane okno **Właściwości.** Okno **Właściwości** służy do ustawiania rozmiaru obrazu, zmieniania właściwości narzędzia i określania kolorów podczas pracy.

### <a name="create-a-bullseye-target-texture"></a>Tworzenie tekstury celu "strzał w dziesiątkę"

1. Utwórz teksturę, z którą ma pracować. Aby uzyskać informacje dotyczące dodawania tekstury do projektu, zobacz [Edytor obrazów](../designers/image-editor.md#get-started).

2. Ustaw rozmiar obrazu na 512x512 pikseli. W oknie **Właściwości** ustaw wartości właściwości **Szerokość** i **Wysokość** na `512`.

3. Na pasku narzędzi Edytor obrazów wybierz narzędzie **Wypełnienie.** Okno **Właściwości** wyświetla teraz właściwości narzędzia **Wypełnienie** wraz z właściwościami obrazu.

4. Ustaw kolor pierwszego planu na w pełni przezroczystą czerń. W oknie **Właściwości** w grupie **Właściwości Kolory** wybierz pozycję **Pierwszy plan**. Ustaw wartości właściwości **R,** **G,** **B**i **A** obok selektora `0`kolorów na .

5. Na pasku narzędzi Edytor obrazów wybierz narzędzie **Wypełnienie,** a następnie naciśnij i przytrzymaj klawisz **Shift** i wybierz dowolny punkt obrazu. Użycie klawisza **Shift** powoduje, że wartość alfa koloru wypełnienia zastępuje kolor obrazu; w przeciwnym razie wartość alfa jest używana do mieszania koloru wypełnienia z kolorem obrazu.

    > [!IMPORTANT]
    > Ten krok, wraz z zaznaczeniem kolorów w poprzednim kroku, zapewnia, że obraz bazowy jest przygotowany do tekstury docelowej "dziesiątki", którą będziesz rysować. Gdy obraz jest wypełniony przezroczystą czernią i ponieważ obramowanie obiektu docelowego jest czarne, wokół obiektu docelowego nie będzie żadnych artefaktów aliasingu.

6. Na pasku narzędzi Edytor obrazów wybierz narzędzie **Elipsa.**

7. Ustaw kolor pierwszego planu na całkowicie nieprzezroczysty czarny. Ustaw wartości właściwości **R,** **G**i **B** `0` oraz wartość właściwości **A** `255`na .

8. Ustaw kolor tła na całkowicie nieprzezroczysty biały. W oknie **Właściwości** w grupie **Właściwości Kolory** wybierz pozycję **Tło**. Ustaw wartości właściwości **R,** **G,** **B**i `255` **A** na .

9. Ustaw szerokość konturu elipsy. W oknie **Właściwości** w grupie właściwości **Wygląd** ustaw wartość właściwości `8` **Width** na .

10. Upewnij się, że wygładzenie jest włączone. W oknie **Właściwości** w grupie właściwości **Wygląd** upewnij się, że ustawiona jest właściwość **wygładowy.**

11. Za pomocą narzędzia **Elipsa** narysuj okrąg ze współrzędnej `(3, 3)` piksela do współrzędnej `(508, 508)`piksela . Aby łatwiej narysować okrąg, możesz nacisnąć i przytrzymać klawisz **Shift** podczas rysowania.

    > [!NOTE]
    > Współrzędne pikseli bieżącej lokalizacji wskaźnika są wyświetlane na pasku stanu programu Visual Studio.

12. Zmień kolor tła. Ustaw **R** R `44`na `165`, **G** do , `255` **B** do `211`, i **A** do .

13. Narysuj `(64, 64)` kolejny okrąg ze współrzędnej piksela do współrzędnej `(448, 448)`piksela .

14. Zmień kolor tła z powrotem na całkowicie nieprzezroczysty biały. Ustaw **R,** **G,** **B** `255`i **A** na .

15. Narysuj `(128, 128)` kolejny okrąg ze współrzędnej piksela do współrzędnej `(384, 384)`piksela .

16. Zmień kolor tła. Ustaw **R** R `255`na , `64` **G** i **B** do , i **A** do `255`.

17. Narysuj `(192, 192)` kolejny okrąg ze współrzędnej piksela do współrzędnej `(320, 320)`piksela .

Tekstura celu "dziesiątki" jest kompletna. Oto ostateczny obraz, pokazany z przezroczystością.

![Kompletna tekstura celu "dziesiątki"](../designers/media/gfx_image_demo_bullseye.png)

Następnym krokiem można wygenerować poziomy MIP dla tej tekstury. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie i modyfikowanie poziomów PROCEDURY MIP](../designers/how-to-create-and-modify-mip-levels.md).

## <a name="see-also"></a>Zobacz też

- [Edytor obrazów](../designers/image-editor.md)
