---
title: Modyfikowanie stylu obiektów
titleSuffix: Blend for Visual Studio
description: Dowiedz się, jak modyfikować styl obiektów w Blend for Visual Studio przez stosowanie pędzli, Ustawianie Stanów wizualnych i stosowanie stylów i szablonów wielokrotnego użytku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cfe54db27a16d95904412b5e1181d589ed2fcde8
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046791"
---
# <a name="modify-the-style-of-objects-in-blend-for-visual-studio"></a>Modyfikowanie stylu obiektów w Blend for Visual Studio

Najprostszym sposobem dostosowania obiektu jest ustawienie właściwości w okienku **Właściwości** .

Jeśli chcesz ponownie użyć ustawień lub grup ustawień, utwórz zasób wielokrotnego użytku. Może to być *styl* , *szablon* lub coś prostego, takiego jak kolor niestandardowy. Formant może być również wyświetlany inaczej w zależności od jego stanu. Na przykład przycisk włącza kolor zielony, gdy użytkownik go klika.

## <a name="brushes-modify-the-appearance-of-an-object"></a>Pędzle: modyfikowanie wyglądu obiektu

Zastosuj pędzel do obiektu, jeśli chcesz zmienić jego wygląd.

### <a name="paint-a-repeating-image-or-pattern-on-an-object"></a>Malowanie powtarzanego obrazu lub wzorca na obiekcie

Malowanie powtarzanego obrazu lub wzorca w obiekcie przy użyciu *pędzla kafelków* .

Aby utworzyć pędzel kafelków, Zacznij od utworzenia *pędzla obrazu* , *pędzla rysowania* lub zasobu *pędzla wizualnego* .

Utwórz pędzel obrazu przy użyciu obrazu. Na poniższych ilustracjach przedstawiono pędzle obrazu, fragment pędzla obrazu oraz odwrócony pędzel obrazu.

![Pędzel obrazu](../designers/media/81f84f56-906d-456b-8288-d77da1e01e31.png) ![Pędzel w programie Mage](../designers/media/d3782ca8-64da-47a4-a095-c6cdd0fa47a2.png) ![Odwrócony pędzel obrazu](../designers/media/38ae3691-f3f1-4a1e-82ca-c7fa164bf56e.png)

Utwórz pędzel rysowania przy użyciu rysunku wektora, takiego jak ścieżka lub kształt. Na poniższych ilustracjach przedstawiono pędzel rysowania, malowanie pędzla i przerzucanie pędzla rysowania.

![Pędzel rysowania](../designers/media/197666ac-ef57-4c5c-9779-669e991a00a5.png) ![Rysowanie pędzla sąsiadująco](../designers/media/ba09cda3-4cee-40ba-b3d4-edc032158bdc.png) ![Przerzucanie pędzla rysowania](../designers/media/15bf6021-620c-4490-9eae-086153d3f14f.png)

Utwórz pędzel wizualny na podstawie kontrolki, takiej jak Button. Na poniższych ilustracjach przedstawiono wizualizację wizualną, a pędzle wizualizacji są rozmieszczane.

![Pędzel wizualny](../designers/media/fb6c90e0-153c-48fe-b563-e601beac6227.png) ![Pędzel wizualny sąsiadujący](../designers/media/e261b99f-7d8f-4d91-bc84-19c7beccc255.png)

## <a name="styles-and-templates-create-a-consistent-look-and-feel-across-controls"></a>Style i szablony: tworzenie spójnego wyglądu i działania między kontrolkami

Możesz zaprojektować wygląd i zachowanie kontrolki jeden raz i zastosować ten projekt do innych kontrolek, aby nie trzeba było ich obsługiwać osobno.

Czy używasz **stylu?** : Jeśli chcesz po prostu ustawić właściwości domyślne (takie jak kolor przycisku), użyj *stylu* . Formant można modyfikować nawet po zastosowaniu stylu do niego.

Czy używasz **szablonu?** : Jeśli chcesz zmienić strukturę kontrolki, użyj *szablonu* . Załóżmy, że Konwertowanie grafiki lub logo na przycisk. Nie można modyfikować kontrolki po zastosowaniu szablonu do niego.

### <a name="create-a-template-or-style"></a>Tworzenie szablonu lub stylu

Istnieją dwa sposoby tworzenia szablonu. Możesz przekonwertować dowolny obiekt w obszarze kompozycji na kontrolkę lub oprzeć szablon na istniejącym formancie.

Aby przekonwertować dowolny obiekt na szablon kontrolki, zaznacz obiekt, a następnie w menu **Narzędzia** wybierz polecenie **Przekształć w kontrolkę** .

Jeśli chcesz oprzeć szablon w istniejącym formancie, zaznacz obiekt w obszarze kompozycji. Następnie w górnej części obszaru kompozycji wybierz przycisk nawigacyjny, wybierz pozycję **Edytuj szablon** , a następnie wybierz opcję **Edytuj kopię** lub **Utwórz pustą** .

![Menu Edytuj szablon](../designers/media/5ebdb33f-aad2-4c10-a328-5e8b04c56a36.png)

Aby utworzyć styl, wybierz obiekt, a następnie w menu **obiekt** wybierz polecenie **Edytuj styl** , a następnie wybierz **Edytuj kopię** lub **Utwórz pustą** .

- Wybierz opcję **Edytuj kopię** , aby rozpocząć od domyślnego stylu lub szablonu kontrolki.

- Wybierz pozycję **Utwórz pusty** , aby zacząć od początku.

Opcja **Edytuj bieżące** jest wyświetlana tylko w przypadku edytowania stylu lub szablonu, który został już utworzony. Nie będzie ona wyświetlana dla formantu, który nadal używa domyślnego szablonu systemowego.

W oknie dialogowym **Tworzenie zasobu stylu** można nazwać styl lub szablon, aby można było go użyć później, lub można zastosować styl lub szablon do wszystkich kontrolek tego typu.

![Okno dialogowe Tworzenie zasobu stylu](../designers/media/4818ee6a-ce60-4b79-91c8-3b1871829eea.png)

> [!NOTE]
> Nie można tworzyć stylów ani szablonów dla każdego typu kontrolki. Jeśli kontrolka nie obsługuje tych funkcji, nie pojawi się nad obszarem kompozycji.
> Aby powrócić do zakresu edycji dokumentu głównego, kliknij przycisk **Zwróć zakres, aby** ![ zwrócić zakres do ikony ](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png) .

### <a name="apply-a-style-or-template-to-a-control"></a>Stosowanie stylu lub szablonu do kontrolki

W oknie [obiekty i oś czasu](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window) kliknij prawym przyciskiem myszy obiekt, wybierz polecenie **Edytuj szablon** , a następnie wybierz pozycję **Zastosuj zasób** .

![Menu Zastosuj zasób](../designers/media/dc12debc-7711-47d9-84ce-10322a384397.png)

### <a name="restore-the-default-style-or-template-of-a-control"></a>Przywracanie domyślnego stylu lub szablonu kontrolki

Zaznacz kontrolkę, a następnie w oknie * * właściwości * * * * Znajdź właściwość **styl** lub **szablon** . Wybierz **Opcje zaawansowane** , a następnie w menu skrótów kliknij polecenie **Zresetuj** .

## <a name="visual-states"></a>Stany wizualne

Stany wizualne umożliwiają zmianę wyglądu kontrolki na podstawie jej stanu. Kontrolki mogą mieć różne wyglądy wizualizacji w oparciu o Interakcje użytkownika. Na przykład można sprawić, aby przycisk był zielony po kliknięciu go przez użytkownika, lub można uruchomić animację. Skracanie lub wydłużenie czasu między Stanami wizualnymi przy użyciu przejść.

![Wskaźnik myszy nad stanem](../designers/media/a95c671a-5639-40b9-83db-1e6b214330d5.png)

**Obejrzyj krótkie wideo:** ![ Przycisk odtwarzania ](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Zarządzaj stanem formantów WPF](https://www.youtube.com/watch?v=m0PlkF5i6uw).

## <a name="resources-create-colors-styles-and-templates-and-reuse-them-later"></a>Zasoby: Tworzenie kolorów, stylów i szablonów oraz ponowne używanie ich w przyszłości

Możesz skonwertować wszystko w projekcie do zasobu. Zasób jest tylko obiektem, którego można użyć w różnych miejscach w aplikacji. Na przykład można utworzyć kolor jeden raz, uczynić go zasobem, a następnie używać tego koloru na kilku obiektach. Aby zmienić kolor wszystkich tych obiektów, wystarczy zmienić zasób koloru.

![Przycisk konwersji koloru na zasób](../designers/media/89203705-cf66-46e0-b153-52a23cd744f7.png) ![Okno dialogowe Tworzenie zasobu koloru](../designers/media/6bff8b19-3cd5-41a0-bbf9-ff65532d5aae.png)

## <a name="see-also"></a>Zobacz też

- [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)
