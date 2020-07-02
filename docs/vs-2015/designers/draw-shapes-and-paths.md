---
title: Rysowanie kształtów i ścieżek | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9eba4e5bfef052f7a82c3148f5628eff9413180
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542210"
---
# <a name="draw-shapes-and-paths"></a>Rysowanie kształtów i ścieżek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W projektant XAML *kształt* jest dokładnie to, czego oczekujesz. Na przykład: prostokąt, okrąg lub Elipsa. *Ścieżka* jest bardziej elastyczną wersją kształtu. Można wykonywać inne czynności, takie jak zmiana kształtu lub łączenie ich ze sobą w celu utworzenia nowych kształtów.

 Kształty i ścieżki używają grafiki wektorowej, dzięki czemu są skalowane do wyświetlania o wysokiej rozdzielczości. Jeśli chcesz dowiedzieć się więcej na temat grafiki wektorowej, zobacz [co to jest grafika wektorowa](https://www.youtube.com/watch?v=MoCSwF0n-io) lub [grafika wektorowa](https://www.webopedia.com/TERM/V/vector_graphics.html).

 **W tym temacie:**

- [Rysowanie kształtu](#Shape)

- [Rysowanie ścieżki](#Path)

- [Konwertowanie kształtu do ścieżki](#Convert)

- [Połącz ścieżki](#Combine)

- [Utwórz ścieżkę złożoną](#Compound)

- [Utwórz ścieżkę przycinającą](#Clipping)

## <a name="draw-a-shape"></a><a name="Shape"></a>Rysowanie kształtu
 Kształty można znaleźć w panelu **składniki** .

 ![Kategoria kształtów w panelu Składniki](../designers/media/b4-shapes-assetspanel.png "b4_Shapes_AssetsPanel")

 Przeciągnij dowolny kształt, który chcesz umieścić w obszarze kompozycji. Następnie można użyć uchwytów na kształcie do skalowania, obracania, przenoszenia lub pochylania kształtu.

 ![](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png "84261e83-3091-4490-ab58-4218b188439e")

## <a name="draw-a-path"></a><a name="Path"></a>Rysowanie ścieżki
 Ścieżka to Seria połączonych linii i krzywych. Użyj ścieżki, aby utworzyć interesujące kształty, które nie są dostępne w panelu **składniki** .

 Ścieżkę można narysować przy użyciu linii, pióra lub ołówka. Te narzędzia można znaleźć w panelu **Narzędzia** .

 ![](../designers/media/717956a8-b6a5-4e37-8af3-70bcfc78c82a.png "717956a8-b6a5-4e37-8af3-70bcfc78c82a") ![](../designers/media/8fbbbb21-be83-4cf6-903b-3a49f00c9860.png "8fbbbb21-be83-4cf6-903b-3a49f00c9860")

### <a name="draw-a-straight-line"></a>Rysowanie prostej
 Użyj narzędzia **pióro** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") lub narzędzia **wiersza** ![](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "eb618397-5283-48be-8396-3449be7b6fbf") .

 **Korzystanie z narzędzia Pióro**![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54")

 W obszarze kompozycji kliknij raz, aby zdefiniować punkt początkowy, a następnie kliknij przycisk ponownie, aby zdefiniować koniec wiersza.

 **Korzystanie z narzędzia wiersza**![](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "eb618397-5283-48be-8396-3449be7b6fbf")

 W obszarze kompozycji przeciągnij kursor od miejsca, w którym chcesz uruchomić linię, a następnie zwolnij w punkcie, w którym ma się zakończyć linia.

### <a name="draw-a-curve"></a>Rysowanie krzywych
 Użyj narzędzia **pióro** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") .

 W obszarze kompozycji kliknij raz, aby zdefiniować punkt początkowy wiersza, a następnie kliknij i przeciągnij wskaźnik, aby utworzyć odpowiednią krzywą.

 Jeśli chcesz zamknąć ścieżkę, kliknij pierwszy punkt w wierszu.

### <a name="change-the-shape-of-a-curve"></a>Zmiana kształtu krzywej
 Użyj narzędzia **Zaznaczanie bezpośrednie** ![](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f-c116-451d-8dd2-1f88b8406362") .

 Kliknij kształt, a następnie przeciągnij dowolny punkt na kształcie, aby zmienić kształt krzywej.

### <a name="draw-a-free-form-path"></a>Rysowanie ścieżki dowolnej
 Użyj narzędzia **ołówek** ![](../designers/media/509dc167-734f-46c9-b012-987ee63450cd.png "509dc167-734f-46c9-b012-987ee63450cd") .

 W obszarze kompozycji narysuj bezpłatną ścieżkę, tak jak w przypadku użycia rzeczywistego ołówka.

### <a name="remove-part-of-a-path"></a>Usuń część ścieżki
 Użyj narzędzia **Zaznaczanie bezpośrednie** ![](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f-c116-451d-8dd2-1f88b8406362") .

 Wybierz ścieżkę zawierającą segment, który chcesz usunąć, a następnie kliknij przycisk **Usuń** .

### <a name="remove-a-point-in-a-path"></a>Usuwanie punktu w ścieżce
 Użyj narzędzia **Zaznaczanie** ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa") i narzędzia **pióro** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") .

 Użyj narzędzia **Zaznaczanie** , ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa") Aby wybrać ścieżkę. Następnie za pomocą narzędzia **pióro** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") kliknij punkt, który chcesz usunąć.

### <a name="add-a-point-to-a-path"></a>Dodawanie punktu do ścieżki
 Użyj narzędzia **Zaznaczanie** ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa") i narzędzia **pióro** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") .

 Użyj narzędzia **Zaznaczanie** , ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa") Aby wybrać ścieżkę. Za pomocą narzędzia **pióro** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") kliknij w dowolnym miejscu ścieżki, w której chcesz dodać punkt.

## <a name="convert-a-shape-to-a-path"></a><a name="Convert"></a>Konwertowanie kształtu na ścieżkę
 Aby zmodyfikować kształt w taki sam sposób, jak w przypadku modyfikacji ścieżki, Przekształć kształt na ścieżkę.

 **Obejrzyj krótkie wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracujące z ścieżkami: Przekształć kształt na ścieżkę](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147).

## <a name="combine-paths"></a><a name="Combine"></a>Połącz ścieżki
 Ścieżki i kształty można łączyć w jedną ścieżkę.

 ![](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png "2df17a5d-a338-4ef4-96c5-dae51cc1ca8a")

|Image (Obraz)|Opis|Image (Obraz)|Opis|
|-|-|-|-|
|![](../designers/media/b1-1.png "B1_1")|Dwa kształty przed połączeniem|![](../designers/media/b1-4.png "B1_4")|Wspólnej|
|![](../designers/media/b1-2.png "B1_2")|Jednostka|![](../designers/media/b1-5.png "B1_5")|Wyklucz nakładanie|
|![](../designers/media/b1-3.png "B1_3")|Dzielenie|![](../designers/media/b1-6.png "B1_6")|Odejmowanie|

 **Obejrzyj krótkie wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracujące z ścieżkami: Połącz ścieżki](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195).

## <a name="create-a-compound-path"></a><a name="Compound"></a>Utwórz ścieżkę złożoną
 Po utworzeniu ścieżki złożonej wszystkie przecinające się części ścieżek są odejmowane od wyniku, a wynikowa ścieżka przyjmuje właściwości wizualizacji z najniższej ścieżki.

 Ścieżkę złożoną można rozdzielić w dowolnym momencie po jej utworzeniu.

 ![](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png "2157a8aa-d9a7-4de4-8de5-b10d28f08a84")

 **Obejrzyj krótkie wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracujące z ścieżkami: Utwórz ścieżkę złożoną](https://www.youtube.com/watch?v=Io5bC0-nH6Q).

## <a name="create-a-clipping-path"></a><a name="Clipping"></a>Utwórz ścieżkę przycinającą
 Ścieżka przycinająca jest ścieżką lub kształtem, który jest stosowany do innego obiektu, ukrywając części maskowanego obiektu, który znajduje się poza ścieżką przycinającą.

 ![](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png "22471e98-a841-4f39-a3ef-36090cf5a625")

 **Obejrzyj krótkie wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracujące z ścieżkami: Utwórz ścieżkę przycinającą](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232).

## <a name="see-also"></a>Zobacz też
 [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
