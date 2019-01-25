---
title: Rysowanie kształtów i ścieżek | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: eae8f49efbff2fd2219d0180db3a542f553a8027
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54775356"
---
# <a name="draw-shapes-and-paths"></a>Rysowanie kształtów i ścieżek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W Projektancie XAML *kształt* dokładnie to, czego można oczekiwać. Na przykład: prostokąt, okrąg lub elipsy. A *ścieżki* jest nieco bardziej elastyczne kształtu. Można wykonać czynności, jak zmienić kształt je lub połączyć je ze sobą nowe kształty formularza.  
  
 Kształtów i ścieżek należy używać grafiki wektorowej, więc ich przeskalować do ekranów o wysokiej rozdzielczości. Jeśli chcesz dowiedzieć się więcej na temat grafiki wektorowej, zobacz [co to są grafiki wektorowej](https://www.youtube.com/watch?v=MoCSwF0n-io) lub [grafika wektorowa](http://www.webopedia.com/TERM/V/vector_graphics.html).  
  
 **W tym temacie:**  
  
-   [Rysowanie kształtu](#Shape)  
  
-   [Rysowanie ścieżki](#Path)  
  
-   [Konwertowanie kształtu do ścieżki](#Convert)  
  
-   [Połącz ścieżki](#Combine)  
  
-   [Utwórz ścieżkę złożoną](#Compound)  
  
-   [Tworzenie ścieżki przycinania](#Clipping)  
  
##  <a name="Shape"></a> Rysowanie kształtu  
 Możesz znaleźć kształty w **zasoby** panelu.  
  
 ![Kategoria kształtów w panelu Składniki](../designers/media/b4-shapes-assetspanel.png "b4_Shapes_AssetsPanel")  
  
 Przeciągnij dowolny kształt, który ma do obszaru kompozycji. Następnie umożliwia uchwytów na kształcie skalowanie, obracanie, Przenieś lub pochylić kształtu.  
  
 ![](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png "84261e83-3091-4490-ab58-4218b188439e")  
  
##  <a name="Path"></a> Rysowanie ścieżki  
 Ścieżka jest szereg podłączonych linii i krzywych. Użyj ścieżki, aby tworzyć interesujące kształty, które nie są dostępne w **zasoby** panelu.  
  
 Ścieżkę można zdefiniować przy użyciu linii, Pióro lub ołówka. Można znaleźć tych narzędzi w **narzędzia** panelu.  
  
 ![](../designers/media/717956a8-b6a5-4e37-8af3-70bcfc78c82a.png "717956a8-b6a5-4e37-8af3-70bcfc78c82a") ![](../designers/media/8fbbbb21-be83-4cf6-903b-3a49f00c9860.png "8fbbbb21-be83-4cf6-903b-3a49f00c9860")  
  
### <a name="draw-a-straight-line"></a>Rysowanie prostej  
 Użyj **pióra** narzędzie ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54"), lub **wiersza** narzędzie ![](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "eb618397-5283-48be-8396-3449be7b6fbf").  
  
 **Za pomocą pióra** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54")  
  
 W obszarze kompozycji kliknij jeden raz, aby zdefiniować punkt początkowy, a następnie kliknij ponownie, aby zdefiniować końca wiersza.  
  
 **Przy użyciu narzędzia wiersza** ![](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "eb618397-5283-48be-8396-3449be7b6fbf")  
  
 W obszarze kompozycji przeciągnij z dowolnego miejsca wiersza, aby rozpocząć, a następnie zwolnij się w punkcie, w którym punktu końcowego linii.  
  
### <a name="draw-a-curve"></a>Rysowanie krzywych  
 Użyj **pióra** narzędzie ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54").  
  
 W obszarze kompozycji kliknij jeden raz aby zdefiniować punkt początkowy dla wiersza, a następnie kliknąć i przeciągnąć wskaźnikiem w taki sposób, aby utworzyć żądany krzywej.  
  
 Jeśli chcesz zamknąć ścieżkę, kliknij pierwszy punkt, w wierszu.  
  
### <a name="change-the-shape-of-a-curve"></a>Zmiana kształtu krzywej  
 Użyj **bezpośrednie zaznaczenie** narzędzie ![](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f-c116-451d-8dd2-1f88b8406362").  
  
 Kliknij kształt, a następnie przeciągnij dowolny punkt, kształtu, aby zmienić krzywej kształtów.  
  
### <a name="draw-a-free-form-path"></a>Rysowanie ścieżki dowolnej  
 Użyj **ołówka** narzędzie ![](../designers/media/509dc167-734f-46c9-b012-987ee63450cd.png "509dc167-734f-46c9-b012-987ee63450cd").  
  
 W obszarze kompozycji rysowanie ścieżki dowolnej postaci tak samo jak przy użyciu rzeczywistego ołówka.  
  
### <a name="remove-part-of-a-path"></a>Usuwanie części ścieżki  
 Użyj **bezpośrednie zaznaczenie** narzędzie ![](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f-c116-451d-8dd2-1f88b8406362").  
  
 Wybierz ścieżkę zawierającą segment, aby usunąć, a następnie kliknij przycisk **Usuń** przycisku.  
  
### <a name="remove-a-point-in-a-path"></a>Usuwanie punktu na ścieżce  
 Użyj **wybór** narzędzie ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa")i **pióra** narzędzie ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54").  
  
 Użyj **wybór** narzędzie ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa") aby wybrać ścieżkę. Następnie należy użyć **pióra** narzędzie ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") kliknij punkt, który chcesz usunąć.  
  
### <a name="add-a-point-to-a-path"></a>Dodaj punkt do ścieżki  
 Użyj **wybór** narzędzie ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa")i **pióra** narzędzie ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54").  
  
 Użyj **wybór** narzędzie ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa") aby wybrać ścieżkę. Użyj **pióra** narzędzie ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4e00-84cf-a9bc8f38fc54") kliknąć ścieżkę, w której chcesz dodać punkt w dowolnym miejscu.  
  
##  <a name="Convert"></a> Konwertowanie kształtu do ścieżki  
 Aby zmodyfikować kształtu w taki sam sposób, aby zmodyfikować ścieżkę, konwertowanie kształtu do ścieżki.  
  
 **Obejrzyj krótki film wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracy dzięki określeniu ścieżki: Konwertowanie kształtu na ścieżkę](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147).  
  
##  <a name="Combine"></a> Połącz ścieżki  
 Można połączyć kształtów i ścieżek w pojedynczą ścieżkę.  
  
 ![](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png "2df17a5d-a338-4ef4-96c5-dae51cc1ca8a")  
  
|||||  
|-|-|-|-|  
|![](../designers/media/b1-1.png "B1_1")|Dwa kształty przed łączenie|![](../designers/media/b1-4.png "B1_4")|INTERSECT|  
|![](../designers/media/b1-2.png "B1_2")|Różne|![](../designers/media/b1-5.png "B1_5")|Wyklucz nakładanie|  
|![](../designers/media/b1-3.png "B1_3")|Dzielenie|![](../designers/media/b1-6.png "B1_6")|Odejmowanie|  
  
 **Obejrzyj krótki film wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracy dzięki określeniu ścieżki: Połącz ścieżki](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195).  
  
##  <a name="Compound"></a> Utwórz ścieżkę złożoną  
 Podczas tworzenia ścieżki złożonej żadnych przecinających się części ścieżki są odejmowane od wyniku, a wynikowe ścieżki zajmuje się we właściwościach visual znajdujących się najniżej ścieżki.  
  
 Możesz przerwać od siebie ścieżkę złożoną dowolnej chwili po jego utworzeniu.  
  
 ![](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png "2157a8aa-d9a7-4de4-8de5-b10d28f08a84")  
  
 **Obejrzyj krótki film wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracy dzięki określeniu ścieżki: Utwórz ścieżkę złożoną](https://www.youtube.com/watch?v=Io5bC0-nH6Q).  
  
##  <a name="Clipping"></a> Tworzenie ścieżki przycinania  
 Ścieżki przycięcia jest ścieżka lub kształtu, który jest stosowany do innego obiektu, ukrywanie części maskowanego obiektu, które wykraczają poza przycinania.  
  
 ![](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png "22471e98-a841-4f39-a3ef-36090cf5a625")  
  
 **Obejrzyj krótki film wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracy dzięki określeniu ścieżki: Tworzenie ścieżki przycinania](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
