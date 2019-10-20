---
title: 'Instrukcje: Tworzenie tekstury podstawowej | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0222e8bf-d29f-421b-9b1f-123d500fa179
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a19cd0b68927effc32b0480fdeb7286be8ad8dd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664573"
---
# <a name="how-to-create-a-basic-texture"></a>Porady: tworzenie tekstury podstawowej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym dokumencie przedstawiono sposób tworzenia tekstury podstawowej przy użyciu edytora obrazów.

 W tym dokumencie przedstawiono następujące działania:

- Ustawianie rozmiaru tekstury

- Ustawianie koloru pierwszego planu i tła

- Korzystanie z kanału alfa (przezroczystość)

- Korzystanie z narzędzi do **wypełniania** i **elipsy**

- Ustawianie właściwości narzędzia

## <a name="creating-a-basic-texture"></a>Tworzenie tekstury podstawowej
 Możesz użyć edytora obrazów do tworzenia i modyfikowania obrazów i tekstur dla swojej gry lub aplikacji.

 Poniższe kroki pokazują, jak utworzyć teksturę, która reprezentuje obiekt docelowy "Bullseye". Po zakończeniu tekstura powinna wyglądać jak na poniższej ilustracji. Aby lepiej zademonstrować przezroczystość tekstury, Edytor obrazów został skonfigurowany tak, aby wyświetlał go przy użyciu zielonego, wydanego wzorca.

 ![Element docelowy "Bullseye" z przezroczystością pokazywaną w kolorze zielonym](../designers/media/digit-bullseye-texture-in-editor.png "Cyfra — Bullseye — tekstura w edytorze")

 Przed rozpoczęciem upewnij się, że wyświetlane jest okno **Właściwości** . Za pomocą okna **Właściwości** można ustawić rozmiar obrazu, zmienić właściwości narzędzia i określić kolory podczas pracy.

#### <a name="to-create-a-bullseye-target-texture"></a>Aby utworzyć teksturę docelową "Bullseye"

1. Utwórz teksturę, z którą chcesz współpracować. Aby uzyskać informacje na temat sposobu dodawania tekstury do projektu, zobacz sekcję Wprowadzenie w [Edytorze obrazu](../designers/image-editor.md).

2. Ustaw rozmiar obrazu na 512 x 512 pikseli. W oknie **Właściwości** Ustaw wartości właściwości **Width** i **Height** na `512`.

3. Na pasku narzędzi edytora obrazu wybierz narzędzie **wypełnienie** . W oknie **Właściwości** są teraz wyświetlane właściwości narzędzia **wypełnienie** wraz z właściwościami obrazu.

4. Ustaw kolor pierwszego planu na całkowicie przezroczysty czarny. W oknie **Właściwości** w grupie właściwości **kolory** wybierz pozycję **pierwszy plan**. Ustaw wartości **R**, **G**, **B**i właściwości obok selektora **kolorów, aby** `0`.

5. Na pasku narzędzi edytora obrazu wybierz narzędzie **wypełnienie** , a następnie naciśnij i przytrzymaj klawisz Shift i wybierz dowolny punkt na obrazie. Użycie klawisza Shift powoduje, że wartość alfa koloru wypełnienia zastąpi kolor obrazu. w przeciwnym razie wartość alfa służy do mieszania koloru wypełnienia ze kolorem obrazu.

   > [!IMPORTANT]
   > Ten krok wraz z wyborem koloru w poprzednim kroku gwarantuje, że obraz podstawowy jest przygotowany do rysowania tekstury docelowej "Bullseye". Gdy obraz jest wypełniony przezroczystą czernią i ponieważ obramowanie elementu docelowego jest czarne — nie będzie żadnych artefaktów aliasów wokół obiektu docelowego.

6. Na pasku narzędzi edytora obrazu wybierz narzędzie **wielokropek** .

7. Ustaw kolor pierwszego planu na całkowicie nieprzezroczysty czarny. Ustaw wartości właściwości **R**, **G**i **B** na `0` i **wartość właściwości `255`** .

8. Ustaw kolor tła na całkowicie nieprzezroczysty biały. W oknie **Właściwości** w grupie właściwości **kolory** wybierz pozycję **tło**. Ustaw wartości właściwości **R**, **G**, **B**i na `255`.

9. Ustaw szerokość konturu elipsy. W oknie **Właściwości** , w grupie właściwości **wygląd** , ustaw wartość właściwości **Width** na `8`.

10. Upewnij się, że wygładzanie jest włączone. Upewnij się, że właściwość **Anti-alias** jest ustawiona w oknie **Właściwości** w grupie właściwości **wygląd** .

11. Używając narzędzia **Elipsa** , narysuj okrąg od współrzędnych pikseli `(3, 3)` do `(508, 508)` współrzędnej piksela. Aby łatwiej rysować okrąg, możesz nacisnąć i przytrzymać klawisz Shift podczas rysowania.

    > [!NOTE]
    > Współrzędne pikseli bieżącej lokalizacji wskaźnika są wyświetlane na pasku stanu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

12. Zmień kolor tła. Ustaw wartość **R** na `44`, **G** do `165`, **B** `211` i **a** do `255`.

13. Narysuj inny okrąg od współrzędnych pikseli `(64, 64)` do `(448, 448)` współrzędnych pikseli.

14. Zmień kolor tła z powrotem na całkowicie nieprzezroczysty biały. Ustaw wartości **R**, **G**, **B**i **a na `255`** .

15. Narysuj inny okrąg od współrzędnych pikseli `(128, 128)` do `(384, 384)` współrzędnych pikseli.

16. Zmień kolor tła. Ustaw wartość **R** na `255`, **G** i **B** na **`64` i `255`** .

17. Narysuj inny okrąg od współrzędnych pikseli `(192, 192)` do `(320, 320)` współrzędnych pikseli.

    Tekstura docelowa "Bullseye" została zakończona. Poniżej znajduje się obraz przedstawiający przezroczystość.

    ![Kompletna tekstura docelowa "Bullseye"](../designers/media/gfx-image-demo-bullseye.png "gfx_image_demo_bullseye")

    Następnym krokiem jest wygenerowanie poziomów MIP dla tej tekstury. Aby uzyskać więcej informacji, zobacz [How to: Create and Modify Levels MIP](../designers/how-to-create-and-modify-mip-levels.md).

## <a name="see-also"></a>Zobacz też
 [Edytor obrazów](../designers/image-editor.md)
