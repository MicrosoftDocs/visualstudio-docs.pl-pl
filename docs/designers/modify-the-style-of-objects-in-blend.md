---
title: Modyfikowanie stylu obiektów w programie Blend
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fcdd5b98ce49dbf437e8071c5e2cd7d734c666c4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55028572"
---
# <a name="modify-the-style-of-objects-in-blend"></a>Modyfikowanie stylu obiektów w programie Blend

Najprostszym sposobem dostosować obiekt jest do ustawiania właściwości **właściwości** okienka.

Jeśli chcesz ponownie użyć ustawień lub grupy ustawień, należy utworzyć zasób do ponownego użycia. Może to być *styl*, *szablonu*, lub coś prostego, takich jak kolor niestandardowy. Można również ustawić kontrolki pojawiają się inaczej w oparciu o jego stan. Na przykład przycisk zmienia kolor na zielony, gdy użytkownik kliknie przycisk.

## <a name="brushes-modify-the-appearance-of-an-object"></a>Pędzle: Modyfikowanie wyglądu obiektu

Stosowanie pędzla do obiektu, jeśli chcesz zmienić jego wygląd.

### <a name="paint-a-repeating-image-or-pattern-on-an-object"></a>Malowanie powtarzające się obraz lub wzorzec do obiektu

Malowanie powtarzające się obraz lub wzorzec do obiektu za pomocą *pędzla kafelków*.

Aby utworzyć pędzla kafelków, Rozpocznij od utworzenia *obrazu pędzla*, *DrawingBrush*, lub *VisualBrush* zasobów.

Tworzenie pędzla obrazu przy użyciu obrazu. Na poniższych ilustracjach przedstawiono pędzla obrazu, ImageBrush sąsiadująco i przerzucać pędzla obrazu.

![Klasa ImageBrush](../designers/media/81f84f56-906d-456b-8288-d77da1e01e31.png) ![Pędzel mage sąsiadująco](../designers/media/d3782ca8-64da-47a4-a095-c6cdd0fa47a2.png) ![Klasa ImageBrush przerzucane](../designers/media/38ae3691-f3f1-4a1e-82ca-c7fa164bf56e.png)

Tworzenie pędzla przy użyciu wektorowej, takich jak ścieżki lub kształtu. Na poniższych ilustracjach przedstawiono pędzla, pędzla sąsiadująco i pędzla odwrócony.

![Klasa DrawingBrush](../designers/media/197666ac-ef57-4c5c-9779-669e991a00a5.png) ![Klasa DrawingBrush sąsiadująco](../designers/media/ba09cda3-4cee-40ba-b3d4-edc032158bdc.png) ![Przerzucać pędzla do rysowania](../designers/media/15bf6021-620c-4490-9eae-086153d3f14f.png)

Tworzenie pędzla visual w kontrolce, takiej jak przycisk. Na poniższych ilustracjach przedstawiono VisualBrush i VisualBrush sąsiadująco.

![Klasa VisualBrush](../designers/media/fb6c90e0-153c-48fe-b563-e601beac6227.png) ![Klasa VisualBrush sąsiadująco](../designers/media/e261b99f-7d8f-4d91-bc84-19c7beccc255.png)

## <a name="styles-and-templates-create-a-consistent-look-and-feel-across-controls"></a>Style i szablony: Tworzenie spójnego wyglądu i zachowania między formantów

Można zaprojektować wygląd i zachowanie kontrolki, jeden raz i zastosowanie tego projektu do innych kontrolek, dzięki czemu nie trzeba zachować je oddzielnie.

**Należy użyć stylu?** : Jeśli chcesz ustawić domyślne właściwości (np. kolor przycisku), użyj *styl*. Kontrolki można modyfikować, nawet w przypadku, po zastosowaniu styl do niego.

**Należy użyć szablonu?** : Jeśli chcesz zmienić strukturę kontrolki, należy użyć *szablonu*. Wyobraź sobie, konwertowania grafika lub logo na przycisku. Nie można zmodyfikować kontrolki, po zastosowaniu szablonu do niego.

### <a name="create-a-template-or-style"></a>Tworzenie stylu lub szablonu

Istnieją dwa sposoby tworzenia szablonu. Dowolny obiekt można przekonwertować na Twojego obszaru roboczego do formantu lub szablonu można oprzeć na istniejącej kontrolki.

Aby przekonwertować dowolny obiekt szablonu kontrolki, zaznacz obiekt, a następnie na **narzędzia** menu, wybierz **przerób na kontrolkę**.

Jeśli chcesz utworzyć nowy szablon istniejącej kontrolki, zaznacz obiekt w obszarze kompozycji. Następnie w górnej części obszaru kompozycji wybierz przycisk nawigacji, wybierz polecenie **Edytuj szablon**, a następnie wybierz **Edytuj kopię** lub **Utwórz pusty**.

![Szablon menu Edycja](../designers/media/5ebdb33f-aad2-4c10-a328-5e8b04c56a36.png)

Tworzenie stylu, wybierz obiekt, a następnie w polu **obiektu** menu, wybierz **Edytuj styl**, a następnie wybierz **Edytuj kopię** lub **Utwórz pusty**.

- Wybierz **Edytuj kopię** chcesz rozpocząć od domyślnego stylu lub szablonu kontrolki.

- Wybierz **Utwórz pusty** od samego początku.

**Edytuj bieżący** opcja jest wyświetlana tylko wtedy, gdy edytujesz stylu lub szablonu, który został już utworzony. Nie będzie on widoczny dla formantu, który nadal jest używany domyślny szablon systemu.

W **tworzenie zasobu stylu** okno dialogowe można albo nazwę stylu lub szablonu, aby można jej użyć później, lub stylu lub szablonu można zastosować do wszystkich formantów tego typu.

![Tworzenie zasobu stylu, okno dialogowe](../designers/media/4818ee6a-ce60-4b79-91c8-3b1871829eea.png)

> [!NOTE]
> Nie można utworzyć style lub szablony dla każdego typu formantu. Jeśli ich nie obsługuje formant, przycisk nawigacji nie pojawi się powyżej obszaru kompozycji.
> Aby powrócić do zakresu edycji dokumentu głównego, kliknij przycisk **Zwróć zakres do** ![Zwróć zakres do ikony](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png).

### <a name="apply-a-style-or-template-to-a-control"></a>Stosowanie stylu lub szablonu do formantu

Kliknij prawym przyciskiem myszy obiekt w [obiekty i oś czasu](../designers/creating-a-ui-by-using-blend-for-visual-studio.md#tour-of-the-objects-and-timeline-panel) panelu, wybierz polecenie **Edytuj szablon**, a następnie wybierz **Zastosuj zasób**.

![Stosowanie zasobu menu](../designers/media/dc12debc-7711-47d9-84ce-10322a384397.png)

### <a name="restore-the-default-style-or-template-of-a-control"></a>Przywracanie domyślnego stylu lub szablonu kontrolki

Wybierz kontrolkę a następnie w [właściwości](../designers/creating-a-ui-by-using-blend-for-visual-studio.md#tour-of-the-properties-panel) panelu, odszukaj **styl** lub **szablonu** właściwości. Wybierz **zaawansowane opcje**, a następnie kliknij przycisk **resetowania** w menu skrótów.

## <a name="visual-states-change-the-appearance-of-a-control-based-on-its-state"></a>Stany wizualne: Zmienianie wyglądu kontrolki oparte na stanie

Formanty mogą mieć inny wygląd visual na podstawie interakcji użytkownika. Na przykład aby włączyć przycisk, zielony, gdy użytkownik go kliknie, ale można też uruchamiać animacji. Skróć lub wydłużyć czas między stany wizualne za pomocą przejścia.

![Wskaźnik myszy nad stanu](../designers/media/a95c671a-5639-40b9-83db-1e6b214330d5.png)

**Obejrzyj krótki film wideo:** ![Przycisk odtwarzania](../designers/media/bldadminconsoleinitialconfigicon.PNG) [zarządzać stanem formantów WPF](https://www.youtube.com/watch?v=m0PlkF5i6uw).

## <a name="resources-create-colors-styles-and-templates-and-reuse-them-later"></a>Zasoby dotyczące oprogramowania: Tworzenie, kolory, style i szablony i używać ich ponownie później

Możesz również przekonwertować wszystko, co w projekcie do zasobu. Zasób jest tylko obiekt, który można ponownie użyć w różnych miejscach w aplikacji. Na przykład można utworzyć jeden raz kolor, ułatwiają zasobu i następnie użyć tego koloru na kilka obiektów. Aby zmienić kolor wszystkich tych obiektów, można zmienić kolor zasobu.

![Konwertuj kolor na zasób przycisku](../designers/media/89203705-cf66-46e0-b153-52a23cd744f7.png) ![Utwórz zasób koloru — okno dialogowe](../designers/media/6bff8b19-3cd5-41a0-bbf9-ff65532d5aae.png)

## <a name="see-also"></a>Zobacz także

- [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)