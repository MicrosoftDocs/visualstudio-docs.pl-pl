---
title: Rysowanie kształtów i ścieżek
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e0efd4b4f9fb301f5bcba4a12857647a8d911f1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60104580"
---
# <a name="draw-shapes-and-paths"></a>Rysowanie kształtów i ścieżek

W Projektancie XAML *kształt* dokładnie to, czego można oczekiwać. Na przykład: prostokąt, okrąg lub elipsy. A *ścieżki* jest nieco bardziej elastyczne kształtu. Można wykonać czynności, jak zmienić kształt je lub połączyć je ze sobą nowe kształty formularza.

Kształtów i ścieżek należy używać grafiki wektorowej, więc ich przeskalować do ekranów o wysokiej rozdzielczości. Jeśli chcesz dowiedzieć się więcej na temat grafiki wektorowej, zobacz [co to są grafiki wektorowej](https://www.youtube.com/watch?v=MoCSwF0n-io) lub [grafika wektorowa](http://www.webopedia.com/TERM/V/vector_graphics.html).

## <a name="Shape"></a> Rysowanie kształtu
 Możesz znaleźć kształty w **zasoby** panelu.

 ![Kategoria kształtów na panelu Zasoby](../designers/media/b4_shapes_assetspanel.png)

 Przeciągnij dowolny kształt, który ma do obszaru kompozycji. Następnie umożliwia uchwytów na kształcie skalowanie, obracanie, Przenieś lub pochylić kształtu.

 ![Handles](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png)

## <a name="Path"></a> Rysowanie ścieżki
 Ścieżka jest szereg podłączonych linii i krzywych. Użyj ścieżki, aby tworzyć interesujące kształty, które nie są dostępne w **zasoby** panelu.

 Ścieżkę można zdefiniować przy użyciu linii, Pióro lub ołówka. Można znaleźć tych narzędzi w **narzędzia** panelu.

 ![Pióro](../designers/media/717956a8-b6a5-4e37-8af3-70bcfc78c82a.png) ![Opcje narzędzia pióra](../designers/media/8fbbbb21-be83-4cf6-903b-3a49f00c9860.png)

### <a name="draw-a-straight-line"></a>Rysowanie prostej
 Użyj **pióra** narzędzie ![pióro](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png), lub **wiersza** narzędzie ![narzędzie wiersza](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png).

 **Za pomocą pióra** ![pióro](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png)

 W obszarze kompozycji kliknij jeden raz, aby zdefiniować punkt początkowy, a następnie kliknij ponownie, aby zdefiniować końca wiersza.

 **Przy użyciu narzędzia wiersza** ![narzędzie wiersza](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png)

 W obszarze kompozycji przeciągnij z dowolnego miejsca wiersza, aby rozpocząć, a następnie zwolnij się w punkcie, w którym punktu końcowego linii.

### <a name="draw-a-curve"></a>Rysowanie krzywych
 Użyj **pióra** narzędzie ![pióro](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png).

 W obszarze kompozycji kliknij jeden raz aby zdefiniować punkt początkowy dla wiersza, a następnie kliknąć i przeciągnąć wskaźnikiem w taki sposób, aby utworzyć żądany krzywej.

 Jeśli chcesz zamknąć ścieżkę, kliknij pierwszy punkt, w wierszu.

### <a name="change-the-shape-of-a-curve"></a>Zmiana kształtu krzywej
 Użyj **bezpośrednie zaznaczenie** narzędzie ![narzędzia Zaznaczanie bezpośrednie](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png).

 Kliknij kształt, a następnie przeciągnij dowolny punkt, kształtu, aby zmienić krzywej kształtów.

### <a name="draw-a-free-form-path"></a>Rysowanie ścieżki dowolnej
 Użyj **ołówka** narzędzie ![Ołówek-narzędzie](../designers/media/509dc167-734f-46c9-b012-987ee63450cd.png).

 W obszarze kompozycji rysowanie ścieżki dowolnej postaci tak samo jak przy użyciu rzeczywistego ołówka.

### <a name="remove-part-of-a-path"></a>Usuwanie części ścieżki
 Użyj **bezpośrednie zaznaczenie** narzędzie ![narzędzia Zaznaczanie bezpośrednie](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png).

 Wybierz ścieżkę zawierającą segment, aby usunąć, a następnie kliknij przycisk **Usuń** przycisku.

### <a name="remove-a-point-in-a-path"></a>Usuwanie punktu na ścieżce
 Użyj **wybór** narzędzie ![narzędzia zaznaczania](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png)i **pióra** narzędzie ![pióro](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png).

 Użyj **wybór** narzędzie ![narzędzia zaznaczania](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png) aby wybrać ścieżkę. Następnie należy użyć **pióra** narzędzie ![pióro](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png) kliknij punkt, który chcesz usunąć.

### <a name="add-a-point-to-a-path"></a>Dodaj punkt do ścieżki
 Użyj **wybór** narzędzie ![narzędzia zaznaczania](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png)i **pióra** narzędzie ![pióro](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png).

 Użyj **wybór** narzędzie ![narzędzia zaznaczania](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png) aby wybrać ścieżkę. Użyj **pióra** narzędzie ![pióro](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png) kliknąć ścieżkę, w której chcesz dodać punkt w dowolnym miejscu.

## <a name="Convert"></a> Konwertowanie kształtu do ścieżki
 Aby zmodyfikować kształtu w taki sam sposób, aby zmodyfikować ścieżkę, konwertowanie kształtu do ścieżki.

 **Obejrzyj krótki film wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.png) [pracy dzięki określeniu ścieżki: Konwertowanie kształtu na ścieżkę](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147).

## <a name="Combine"></a> Połącz ścieżki
 Można połączyć kształtów i ścieżek w pojedynczą ścieżkę.

 ![Połącz ścieżki](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png)

|||||
|-|-|-|-|
|![Dwa kształty przed łączenie](../designers/media/b1_1.png)|Dwa kształty przed łączenie|![INTERSECT](../designers/media/b1_4.png)|INTERSECT|
|![Wyklucz nakładanie](../designers/media/b1_2.png)|Różne|![](../designers/media/b1_5.png)|Wyklucz nakładanie|
|![Odejmowanie](../designers/media/b1_3.png)|Dzielenie|![](../designers/media/b1_6.png)|Odejmowanie|

 **Obejrzyj krótki film wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.png) [pracy dzięki określeniu ścieżki: Połącz ścieżki](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195).

## <a name="Compound"></a> Utwórz ścieżkę złożoną
 Podczas tworzenia ścieżki złożonej żadnych przecinających się części ścieżki są odejmowane od wyniku, a wynikowe ścieżki zajmuje się we właściwościach visual znajdujących się najniżej ścieżki.

 Możesz przerwać od siebie ścieżkę złożoną dowolnej chwili po jego utworzeniu.

 ![Przerwij ścieżkę złożoną](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png)

 **Obejrzyj krótki film wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.png) [pracy dzięki określeniu ścieżki: Utwórz ścieżkę złożoną](https://www.youtube.com/watch?v=Io5bC0-nH6Q).

## <a name="Clipping"></a> Tworzenie ścieżki przycinania
 Ścieżki przycięcia jest ścieżka lub kształtu, który jest stosowany do innego obiektu, ukrywanie części maskowanego obiektu, które wykraczają poza przycinania.

 ![Ścieżki przycięcia](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png)

 **Obejrzyj krótki film wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.png) [pracy dzięki określeniu ścieżki: Tworzenie ścieżki przycinania](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232).

## <a name="see-also"></a>Zobacz także

- [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)