---
title: Organizowanie obiektów w kontenery układów w projektant XAML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 90c30f27ada6673608a1c5cf9500207f9aeb2d72
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664199"
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>Organizowanie obiektów w kontenery układów w projektancie XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wyobraź sobie, gdzie chcesz, aby obiekty były wyświetlane na stronie; obiekty, takie jak obrazy, przyciski i wideo. Być może chcesz, aby były wyświetlane w wierszach i kolumnach, w jednym wierszu w pionie lub w poziomie lub w stałej pozycji.

 Po dodaniu szansy myślisz, jak może wyglądać Strona, wybierz Panel układu. Wszystkie strony zaczynają się od siebie, ponieważ potrzebne jest dodanie obiektów do programu. Domyślnie jest to **Siatka** , ale można ją zmienić.

 Panele układów ułatwiają rozmieszczanie obiektów na stronie, ale nie wykonują tych czynności. Ułatwiają one projektowanie dla różnych rozmiarów i rozdzielczości ekranu. Gdy użytkownicy uruchamiają aplikację, wszystko w panelu układu zmienia rozmiar tak, aby pasował do zawartości ekranu na urządzeniu. Oczywiście, jeśli nie chcesz, aby układ został przesłonięty, możesz przesłonić to zachowanie dla części układu lub całego układu. Możesz użyć właściwości Height i Width, aby to sterować.

 Ta strona zawiera opis paneli i kontrolek układu, a następnie kieruje Cię do krótkich filmów wideo, które ułatwiają rozpoczęcie pracy z nimi.

> [!NOTE]
> Niektóre wideo mogą odwoływać się do programu Blend lub Expression Blend, który używa tego samego projektanta XAML, co program Visual Studio i Blend for Visual Studio.

## <a name="layout-panels"></a>Panele układów
 Rozpocznij swoją stronę, wybierając jeden z tych paneli układu. Strona może mieć więcej niż jeden. Na przykład możesz zacząć od panelu układu **siatki** , a następnie dodać **StackPanel** do obszaru w **siatce** , aby można było rozmieścić kontrolki w pionie w tym elemencie.

 Następujące panele układu są najczęściej używane, ale istnieją inne. Wszystkie te informacje można znaleźć w panelu **składniki** .

- [Siatka](#Grid)

- [UniformGrid](#Uniform)

- [Kanwa](#Canvas)

- [StackPanel](#Stack)

- [WrapPanel](#Wrap)

- [DockPanel](#Dock)

### <a name="Grid"></a>Siatki
 Uporządkuj obiekty w wiersze i kolumny.

 ![](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png "98b234b2-ac3b-441f-9136-98375fee87b7")

 **Obejrzyj krótkie wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [przy użyciu siatek](http://www.popscreen.com/v/6A4hj/Microsoft-Expression-Blend-Using-Grids)

### <a name="Uniform"></a>UniformGrid
 Rozmieść obiekty w równych lub jednorodnych regionach siatki. Ten panel doskonale nadaje się do porządkowania list obrazów.

 ![](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png "928b9284-a7e8-4678-875a-656b80b78076")

 (Dostępne tylko dla projektów WPF)

 **Obejrzyj krótkie wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracujące z UniformGrid](http://www.popscreen.com/v/6A4iq/Microsoft-Expression-Blend-Working-with-a-UniformGrid)

### <a name="Canvas"></a>Przestrzeń
 Rozmieść obiekty w dowolny sposób. Gdy użytkownicy uruchamiają aplikację, te elementy będą miały stałe pozycje na ekranie.

 ![](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png "e1ae27f0-3a57-454e-b580-877dcea8836d")

 **Obejrzyj krótkie wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracujące z kanwą](http://www.popscreen.com/v/6A4hT/Microsoft-Expression-Blend-Working-with-the-Canvas)

### <a name="Stack"></a>StackPanel
 Rozmieść obiekty w jednym wierszu w poziomie lub w pionie.

 ![](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png "a85a7b57-b0a8-495e-b985-f0291e41d093")

 **Obejrzyj krótkie wideo:** ![Konfigurowanie zainstalowanych funkcji](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracujących z StackPanel i kontrolce WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)

### <a name="Wrap"></a>Kontrolce WrapPanel
 Rozmieść obiekty sekwencyjnie od lewej do prawej. Gdy panel nie jest widoczny w skrajnie prawej krawędzi, *zawija* zawartość do następnego wiersza i tak dalej, od lewej do prawej, od góry do dołu. Możesz również zmienić orientację panelu zawijania w pionie, aby obiekty były przesyłane z góry do dołu, od lewej do prawej.

 (Dostępne tylko dla projektów WPF)

 ![](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png "b1c415fb-9a32-4a18-aa0b-308fca994ac9")

 **Obejrzyj krótkie wideo:** ![Konfigurowanie zainstalowanych funkcji](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracujących z StackPanel i kontrolce WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)

### <a name="Dock"></a>DockPanel
 Rozmieść obiekty w taki sposób, aby stały się one lub *zadokowane*, do jednej krawędzi panelu.

 (Dostępne tylko dla projektów WPF)

 ![](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png "72d46b58-9a49-4dd5-8af7-6843c0440226")

 **Obejrzyj krótkie wideo:** ![Konfigurowanie zainstalowanych funkcji](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [WPF-DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)

## <a name="layout-controls"></a>Kontrolki układu
 Możesz również dodać obiekty do kontrolek układu. Nie są one jako panel układu, ale mogą być przydatne w niektórych scenariuszach.

 Poniższe kontrolki układu są najczęściej używane, ale istnieją inne. Wszystkie te informacje można znaleźć w panelu **składniki** .

- [Obramowanie](#Border)

- [Okno podręczne](#Popup)

- [ScrollViewer](#Scroll)

- [UniformGrid](#Uniform)

- [Okno widoku](#View)

### <a name="Border"></a>Granicznym
 Utwórz obramowanie, tło lub oba elementy wokół obiektu. Do **obramowania**można dodać tylko jeden obiekt. Jeśli chcesz zastosować obramowanie lub tło dla więcej niż jednego obiektu, Dodaj panel układu do **obramowania**. Następnie Dodaj obiekty do tego panelu lub kontrolki.

 ![](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png "e761238b-99fd-43c5-bbc4-57538b8289ff")

 **Obejrzyj krótkie wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracujące z obramowaniami](http://www.popscreen.com/v/6A4hB/Microsoft-Expression-Blend-Working-with-Borders)

### <a name="Popup"></a>Elementy
 Pokaż informacje lub opcje dla użytkowników w oknie. Do **okna podręcznego**można dodać tylko jeden obiekt. Domyślnie **okno podręczne** zawiera **siatkę** , ale można to zmienić.

### <a name="Scroll"></a>ScrollViewer
 Włącz użycie, aby przewinąć w dół stronę lub obszar strony. Można dodać tylko jeden obiekt do **ScrollViewer** , tak aby miał wiele sens, aby dodać Panel układu, taki jak **Siatka** lub **StackPanel**.

 ![](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png "06b326d4-f23d-41a6-b26b-e1aff37572a7")

### <a name="View"></a>Viewbox
 Skaluj obiekty w taki sam sposób, jak w przypadku kontrolki powiększenia. Do **Viewbox**można dodać tylko jeden obiekt. Jeśli chcesz zastosować ten efekt do więcej niż jednego obiektu, Dodaj panel układu do **Viewbox**, a następnie Dodaj kontrolki do tego panelu układu.

 (Dostępne tylko dla projektów WPF)

 ![](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png "f5b13c66-d918-4141-8a16-bd8f8628687a")

## <a name="see-also"></a>Zobacz też
 [Praca z elementami w Projektant XAML](../designers/working-with-elements-in-xaml-designer.md) [Tworzenie interfejsu użytkownika przy użyciu Projektant XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
