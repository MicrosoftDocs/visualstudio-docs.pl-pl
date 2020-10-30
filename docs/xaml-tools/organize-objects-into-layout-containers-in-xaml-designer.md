---
title: Organizowanie obiektów w kontenery układów w projektancie XAML
description: Poznaj panele i kontrolki układu w projektant XAML, które są używane do porządkowania obiektów na stronie, takich jak siatka, Kanwa, obramowanie i Viewbox.
ms.custom: SEO-VS-2020
ms.date: 07/17/2020
ms.topic: conceptual
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 6df200c5adb4993d13e896eaa6d2041e0e9db044
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047349"
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>Organizowanie obiektów w kontenery układów w projektancie XAML

W tym artykule opisano panele i kontrolki układu dla projektant XAML.

Załóżmy, gdzie obiekty mają być wyświetlane na &mdash; obiektach stron, takich jak obrazy, przyciski i wideo. Być może chcesz, aby były wyświetlane w wierszach i kolumnach, w jednym wierszu w pionie lub w poziomie lub w stałej pozycji.

Po dodaniu szansy myślisz, jak może wyglądać Strona, wybierz Panel układu. Wszystkie strony zaczynają się od siebie, ponieważ potrzebujesz czegoś, do którego chcesz dodać obiekty. Domyślnie jest to **Siatka** , ale można ją zmienić.

Panele układów ułatwiają rozmieszczanie obiektów na stronie, ale nie wykonują tych czynności. Ułatwiają one projektowanie dla różnych rozmiarów i rozdzielczości ekranu. Gdy użytkownicy uruchamiają aplikację, wszystko w panelu układu zmienia rozmiar tak, aby pasował do zawartości ekranu na urządzeniu. Oczywiście, jeśli nie chcesz, aby układ został przesłonięty, możesz przesłonić to zachowanie dla części układu lub całego układu. Możesz użyć właściwości Height i Width, aby to sterować.

## <a name="layout-panels"></a>Panele układów

Rozpocznij swoją stronę, wybierając jeden z tych paneli układu. Strona może mieć więcej niż jeden. Na przykład możesz zacząć od panelu układu **siatki** , a następnie dodać **StackPanel** do obszaru w **siatce** , aby można było rozmieścić kontrolki w pionie w tym elemencie.

Następujące panele układu są najczęściej używane, ale istnieją inne. Wszystkie te elementy można znaleźć w **przyborniku** w programie Visual Studio lub panelu **składniki** w Blend for Visual Studio.

### <a name="grid"></a>Siatka

Uporządkuj obiekty w wiersze i kolumny.

![Panel układu siatki](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png)

### <a name="uniformgrid"></a>UniformGrid

Rozmieść obiekty w równych lub jednorodnych regionach siatki. Ten panel doskonale nadaje się do porządkowania list obrazów.

(Dostępne tylko dla projektów WPF).

![Panel układu UniformGrid](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png)

### <a name="canvas"></a>Kanwa

Rozmieść obiekty w dowolny sposób. Gdy użytkownicy uruchamiają aplikację, te elementy będą miały stałe pozycje na ekranie.

![Panel układu kanwy](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png)

### <a name="stackpanel"></a>StackPanel

Rozmieść obiekty w jednym wierszu w poziomie lub w pionie.

![Panel układu StackPanel](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png)

### <a name="wrappanel"></a>WrapPanel

Rozmieść obiekty sekwencyjnie od lewej do prawej. Gdy panel nie jest widoczny w skrajnie prawej krawędzi, *zawija* zawartość do następnego wiersza i tak dalej, od lewej do prawej, od góry do dołu. Możesz również zmienić orientację panelu zawijania w pionie, aby obiekty były przesyłane z góry do dołu, od lewej do prawej.

(Dostępne tylko dla projektów WPF).

![Panel układu kontrolce WrapPanel](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png)

### <a name="dockpanel"></a>DockPanel

Rozmieść obiekty w taki sposób, aby stały się one lub *zadokowane* , do jednej krawędzi panelu.

(Dostępne tylko dla projektów WPF).

![Panel układu DockPanel](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png)

**Obejrzyj krótkie wideo:** ![ Przycisk odtwarzania ](../designers/media/bldadminconsoleinitialconfigicon.PNG) [— WPF — DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)

## <a name="layout-controls"></a>Kontrolki układu

Możesz również dodać obiekty do kontrolek układu. Nie są one jako panel układu, ale mogą być przydatne w niektórych scenariuszach.

Następujące kontrolki układu są najbardziej popularne, ale istnieją inne. Wszystkie te elementy można znaleźć w **przyborniku** w programie Visual Studio lub panelu **składniki** w Blend for Visual Studio.

### <a name="border"></a>Obramowanie

Utwórz obramowanie, tło lub oba elementy wokół obiektu. Do **obramowania** można dodać tylko jeden obiekt. Jeśli chcesz zastosować obramowanie lub tło dla więcej niż jednego obiektu, Dodaj panel układu do **obramowania** . Następnie Dodaj obiekty do tego panelu lub kontrolki.

![Kontrolka układu obramowania](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png)

### <a name="popup"></a>Okno podręczne

Pokaż informacje lub opcje dla użytkowników w oknie. Do **okna podręcznego** można dodać tylko jeden obiekt. Domyślnie **okno podręczne** zawiera **siatkę** , ale można to zmienić.

### <a name="scrollviewer"></a>ScrollViewer

Zezwól użytkownikom na przewijanie w dół strony lub obszaru strony. Można dodać tylko jeden obiekt do **ScrollViewer** , więc warto dodać Panel układu, taki jak **Siatka** lub **StackPanel** .

![Kontrolka układu ScrollViewer](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png)

### <a name="viewbox"></a>Okno widoku

Skaluj obiekty w taki sam sposób, jak w przypadku kontrolki powiększenia. Do **Viewbox** można dodać tylko jeden obiekt. Jeśli chcesz zastosować ten efekt do więcej niż jednego obiektu, Dodaj panel układu do **Viewbox** , a następnie Dodaj kontrolki do tego panelu układu.

![Kontrolka układu ViewBox](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png)

## <a name="see-also"></a>Zobacz też

- [Praca z elementami w projektancie XAML](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
