---
title: Wstawianie kontrolek i modyfikowanie ich zachowania w projektant XAML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 015d929331294baf1fea14c66956674548c29845
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664358"
---
# <a name="insert-controls-and-modify-their-behavior-in-xaml-designer"></a>Wstawianie kontrolek i modyfikowanie ich zachowania w programie Projektant XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kontrolki umożliwiają użytkownikom współpracują z aplikacją. Można ich używać do zbierania informacji i wykonywania akcji, takich jak animowanie obiektu lub zapytanie względem źródła danych.

 **W tym temacie:**

- [Dodawanie kontrolek do obszaru kompozycji](#Insert)

- [Tworzenie elementów sterujących](#Modify)

## <a name="Insert"></a>Dodawanie kontrolek do obszaru kompozycji
 Możesz przeciągnąć kontrolki z panelu **składniki** do **obszaru kompozycji**, a następnie zmodyfikować je w oknie **Właściwości** .

 ![FlipView &#45; zasobów &#45; Blend](../designers/media/blend-assetsflipview-xaml.png "blend_AssetsFlipView_XAML")

 Te wideo pokazują, jak używać niektórych bardziej typowych kontrolek.

|formant|Obejrzyj krótkie wideo|
|-------------|-------------------------|
|`Menu` ![](../designers/media/015a263c-0b2b-4253-ac57-b86fcb8c9591.png "015a263c-0b2b-4253-ac57-b86fcb8c9591")|![Konfigurowanie zainstalowanych funkcji](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Dodawanie kontrolek](https://www.youtube.com/watch?v=ra4AHfgD4Ys&list=PLBDF977B2F1DAB358&index=45)|
|`Button` ![](../designers/media/05df1779-a68f-436b-b834-a91b7995a3ec.png "05df1779-a68f-436b-b834-a91b7995a3ec")|![Konfigurowanie zainstalowanych funkcji](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [projektowanie przycisku](http://www.popscreen.com/v/6A4gb/Microsoft-Expression-Blend-Designing-a-Button)|
|`Textblock` ![](../designers/media/42165963-00f7-4a33-abcd-b0849edebada.png "42165963-00f7-4a33-abcd-b0849edebada")|![Konfigurowanie zainstalowanych funkcji](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Dodawanie obrazów do bloku TextBlock](http://www.popscreen.com/v/6A4du/Microsoft-Expression-Blend-Adding-Images-to-a-TextBlock)|
|`Slider` ![](../designers/media/bf689d92-3c74-4218-815c-e98c930ac189.png "bf689d92-3c74-4218-815c-e98c930ac189")|![Konfigurowanie zainstalowanych funkcji](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Tworzenie suwaka przy użyciu etykietki narzędzia](http://www.bing.com/videos/search?q=slider%20expression%20blend&qs=n&form=QBVR&pq=slider%20expression%20blend&sc=1-23&sp=-1&sk=#view=detail&mid=F1BB7DB91B2772A8CA2AF1BB7DB91B2772A8CA2A)|
|`GridSplitter` ![](../designers/media/d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be.png "d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be")|![Konfigurowanie zainstalowanych funkcji](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracy z użyciu GridSplitter](https://www.youtube.com/watch?v=bf4t6c8ms2w)|

### <a name="make-a-control-out-of-an-image-shape-or-path"></a>Określanie kontrolki obrazu, kształtu lub ścieżki
 Można utworzyć dowolny obiekt w kontrolce.

 ![Okno dialogowe Przekształć w kontrolkę](../designers/media/blend-makeintocontrol-xaml.png "blend_MakeIntoControl_XAML")

 Załóżmy na przykład, że obraz telewizora znajduje się na środku strony. Można sprawić, aby kontrolki z małych obrazów wyglądały jak przyciski TV. Następnie użytkownicy mogą kliknąć te przyciski, aby zmienić kanał.

 Jest to możliwe, ponieważ przyciski są teraz kontrolkami. Za pomocą kontrolek można reagować na interakcje użytkowników; w tym przypadku, gdy użytkownik kliknie przycisk.

 Aby utworzyć kontrolkę, wybierz obiekt. Następnie w menu **Narzędzia** kliknij pozycję **uczyń kontrolę**.

## <a name="Modify"></a>Tworzenie elementów sterujących
 Kontrolki mogą wykonywać akcje, gdy użytkownicy współpracują z nimi. Na przykład mogą rozpocząć animację, zaktualizować źródło danych lub odtworzyć wideo.

 Użyj *wyzwalaczy*, *zachowań*i *zdarzeń* , aby wykonywać formanty.

### <a name="triggers"></a>Wyzwalacze
 *Wyzwalacz* zmienia właściwość lub wykonuje zadanie w odpowiedzi na zdarzenie lub zmianę innej właściwości. Można na przykład zmienić kolor przycisku, gdy użytkownicy umieściją nad nim wskaźnikiem myszy.

 ![Panel wyzwalacze](../designers/media/custom-button-blend-propertytriggerinfo.png "custom_button_blend_PropertyTriggerInfo")

 **Obejrzyj krótkie wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Dodaj wyzwalacz właściwości](http://www.popscreen.com/v/6A4gO/Microsoft-Expression-Blend-Adding-a-Property-Trigger).

### <a name="behaviors"></a>Zachowania
 *Zachowanie* to pakiet kodu wielokrotnego użytku. Może to być nieco więcej niż właściwości zmiany. Może wykonywać takie działania, jak wysyłanie zapytań do usługi danych. Program Blend zawiera niewielką kolekcję, ale możesz dodać więcej. Przeciągnij zachowanie na dowolny obiekt w obszarze kompozycji, a następnie dostosuj zachowanie, ustawiając właściwości.

 ![Zachowanie fluidmovebehavior w panelu Właściwości](../designers/media/b4-fluidmovebehaviorproperties-sample.png "b4_FluidMoveBehaviorProperties_Sample")

 **Obejrzyj krótkie wideo:** ![Konfigurowanie zainstalowanych funkcji](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [— wskazówki dotyczące mieszania: wprowadzenie do korzystania z zachowań części 1](http://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).

### <a name="events"></a>Zdarzenia
 Aby zapewnić całkowitą elastyczność, należy obsłużyć *zdarzenie*. Musisz napisać kod.

 **Obejrzyj krótkie wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Dodaj zdarzenie myszy](https://www.youtube.com/watch?v=2PMxAlb-x_E).
