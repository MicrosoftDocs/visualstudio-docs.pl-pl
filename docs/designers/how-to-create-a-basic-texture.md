---
title: 'Instrukcje: Tworzenie tekstury podstawowej'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 0222e8bf-d29f-421b-9b1f-123d500fa179
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 132fd7c9af4bbee7ae6984ccd58ae5c403121627
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953201"
---
# <a name="how-to-create-a-basic-texture"></a>Instrukcje: Tworzenie tekstury podstawowej

W tym artykule przedstawiono sposób używania edytora obrazu, aby utworzyć teksturę podstawową, wykonując następujące czynności:

- Ustawianie rozmiaru tekstury

- Ustawianie pierwszego planu i tła kolorów

- Za pomocą kanału alfa (przezroczystości)

- Za pomocą **wypełnienia** i **elipsy** narzędzia

- Ustawianie właściwości narzędzia

## <a name="create-a-basic-texture"></a>Tworzenie tekstury podstawowej

Edytor obrazu do tworzenia i modyfikowania obrazów i tekstur dla Twojej gry lub aplikacji.

Poniższe kroki pokazują jak utworzyć teksturę, która reprezentuje element docelowy "bullseye". Gdy skończysz, Tekstura powinno wyglądać jak na poniższym obrazie. Aby zademonstrować lepiej przezroczystości tekstury, edytora obrazów skonfigurowano do korzystania z wzorca zielony, szachownicą, aby go wyświetlić.

![Docelowy "Bullseye" z przezroczystością na zielono](../designers/media/digit-bullseye-texture-in-editor.png)

Przed rozpoczęciem upewnij się, że **właściwości** zostanie wyświetlone okno. Możesz użyć **właściwości** okna, aby ustawić rozmiar obrazu, zmień właściwości narzędzia i określić kolory, podczas pracy.

### <a name="create-a-bullseye-target-texture"></a>Utwórz teksturę target "bullseye"

1. Utwórz teksturę, z którą chcesz pracować. Aby uzyskać informacje dotyczące sposobu dodawania tekstury do projektu, zobacz [edytora obrazów](../designers/image-editor.md#get-started).

2. Ustaw wielkość obrazu do 512 x 512 pikseli. W **właściwości** okna, ustaw wartości **szerokość** i **wysokość** właściwości `512`.

3. Na pasku narzędzi edytora obrazów, wybierz **wypełnienia** narzędzia. **Właściwości** oknie zostaną wyświetlone właściwości **wypełnienia** narzędzie wraz z właściwości obrazu.

4. Aby całkowicie przezroczysty czarny, należy ustawić kolor pierwszego planu. W **właściwości** okna w **kolory** grupie właściwości, wybierz opcję **pierwszego planu**. Ustaw wartości **R**, **G**, **B**, i **A** właściwości obok selektor kolorów do `0`.

5. Na pasku narzędzi edytora obrazów, wybierz **wypełnienia** narzędzia, a następnie naciśnij i przytrzymaj **Shift** klucza i wybrać dowolny punkt na obrazie. Za pomocą **Shift** klucza powoduje, że wartość alfa odpowiadającą koloru wypełnienia, aby zastąpić kolor w obrazie; w przeciwnym razie wartość alfa odpowiadającą służy do programu blend kolor wypełnienia wraz z kolorów na obrazie.

    > [!IMPORTANT]
    > Ten krok, wraz z wybór koloru w poprzednim kroku gwarantuje, że podstawowy obraz jest gotowy do "bullseye" docelową teksturę będzie rysowania. Gdy obraz jest wypełniany przezroczysty czarny — i dlatego jest czarny, obramowania docelowy — nie będzie żadnych artefaktów wygładzania wokół obiektu docelowego.

6. Na pasku narzędzi edytora obrazów, wybierz **elipsy** narzędzia.

7. Ustaw kolor pierwszego planu, aby całkowicie nieprzezroczysty czarny. Ustaw wartości **R**, **G**, i **B** właściwości `0` i wartość **A** właściwość `255`.

8. Ustaw kolor tła na całkowicie nieprzezroczyste biały. W **właściwości** okna w **kolory** grupie właściwości, wybierz opcję **tła**. Ustaw wartości **R**, **G**, **B**, i **A** właściwości `255`.

9. Ustaw szerokość konturu elipsy. W **właściwości** okna w **wygląd** grupy właściwość, ustaw wartość **szerokość** właściwość `8`.

10. Upewnij się, że wygładzanie jest włączony. W **właściwości** okna w **wygląd** właściwości grupy, upewnij się, że **wygładzanie** właściwość jest ustawiona.

11. Za pomocą **elipsy** narzędzie, narysuj okręg z współrzędnych pikseli `(3, 3)` do współrzędnej pikseli `(508, 508)`. Aby narysować łatwiej koła, naciśnij i przytrzymaj **Shift** klucza podczas rysowania.

    > [!NOTE]
    > Współrzędne bieżącej lokalizacji wskaźnika w pikselach, są wyświetlane na pasku stanu programu Visual Studio.

12. Umożliwia zmianę koloru tła. Ustaw **R** do `44`, **G** do `165`, **B** do `211`, i **A** do `255`.

13. Rysowanie okrąg inny od współrzędnych pikseli `(64, 64)` do współrzędnej pikseli `(448, 448)`.

14. Zmienić kolor tła na całkowicie nieprzezroczyste biały. Ustaw **R**, **G**, **B**, i **A** do `255`.

15. Rysowanie okrąg inny od współrzędnych pikseli `(128, 128)` do współrzędnej pikseli `(384, 384)`.

16. Umożliwia zmianę koloru tła. Ustaw **R** do `255`, **G** i **B** do `64`, i **A** do `255`.

17. Rysowanie okrąg inny od współrzędnych pikseli `(192, 192)` do współrzędnej pikseli `(320, 320)`.

Docelową teksturę "bullseye" zostało zakończone. Oto finalnego obrazu, przedstawiono przezroczystości.

![Ukończone "bullseye" docelowej tekstury](../designers/media/gfx_image_demo_bullseye.png)

Kolejnym krokiem może wygenerować poziomy MIP dla tej tekstury. Aby uzyskać informacje, zobacz [jak: Tworzenie i modyfikacja poziomów MIP](../designers/how-to-create-and-modify-mip-levels.md).

## <a name="see-also"></a>Zobacz także

- [Edytor obrazów](../designers/image-editor.md)