---
title: Wstawianie kontrolek i modyfikowanie ich zachowania w Projektancie XAML | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1c3f00c8cd0c9289c9b9c8d948502f9d614934ae
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57867342"
---
# <a name="insert-controls-and-modify-their-behavior-in-xaml-designer"></a>Wstawianie kontrolek i modyfikowanie ich zachowania w programie Projektant XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kontrolki umożliwiają użytkownikom na interakcję z aplikacją. Można użyć ich do zbierania informacji i wykonywanie działań takich jak animować obiekt lub zbadać źródło danych.  
  
 **W tym temacie:**  
  
-   [Dodawanie formantów do obszaru kompozycji](#Insert)  
  
-   [Umożliwianie wykonywały formantów](#Modify)  
  
##  <a name="Insert"></a> Dodawanie formantów do obszaru kompozycji  
 Można przeciągać formantów z **zasoby** panelu na **obszaru kompozycji**, a następnie zmodyfikuj je w **właściwości** okna.  
  
 ![Blend &#45; Assets &#45; FlipView](../designers/media/blend-assetsflipview-xaml.png "blend_AssetsFlipView_XAML")  
  
 W tych filmach wideo pokazano, jak korzystać z niektórych bardziej powszechne kontrolek.  
  
|formant|Obejrzyj krótki film wideo|  
|-------------|-------------------------|  
|`Menu` ![](../designers/media/015a263c-0b2b-4253-ac57-b86fcb8c9591.png "015a263c-0b2b-4253-ac57-b86fcb8c9591")|![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [dodać formanty](https://www.youtube.com/watch?v=ra4AHfgD4Ys&list=PLBDF977B2F1DAB358&index=45)|  
|`Button` ![](../designers/media/05df1779-a68f-436b-b834-a91b7995a3ec.png "05df1779-a68f-436b-b834-a91b7995a3ec")|![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [zaprojektować przycisk](http://www.popscreen.com/v/6A4gb/Microsoft-Expression-Blend-Designing-a-Button)|  
|`Textblock` ![](../designers/media/42165963-00f7-4a33-abcd-b0849edebada.png "42165963-00f7-4a33-abcd-b0849edebada")|![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Dodawanie obrazów do textblock](http://www.popscreen.com/v/6A4du/Microsoft-Expression-Blend-Adding-Images-to-a-TextBlock)|  
|`Slider` ![](../designers/media/bf689d92-3c74-4218-815c-e98c930ac189.png "bf689d92-3c74-4218-815c-e98c930ac189")|![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [kompilacji obiekt Slider z etykietki narzędzia](http://www.bing.com/videos/search?q=slider%20expression%20blend&qs=n&form=QBVR&pq=slider%20expression%20blend&sc=1-23&sp=-1&sk=#view=detail&mid=F1BB7DB91B2772A8CA2AF1BB7DB91B2772A8CA2A)|  
|`GridSplitter` ![](../designers/media/d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be.png "d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be")|![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pracy przy użyciu GridSplitter](https://www.youtube.com/watch?v=bf4t6c8ms2w)|          

 
  
### <a name="make-a-control-out-of-an-image-shape-or-path"></a>Kontrolka poza obrazu, kształtu lub ścieżki  
 Można wprowadzić dowolny obiekt w kontrolce.  
  
 ![Okno dialogowe przerób na kontrolkę w programie Blend](../designers/media/blend-makeintocontrol-xaml.png "blend_MakeIntoControl_XAML")  
  
 Na przykład Wyobraź sobie obraz telewizyjnych w środkowej części strony. Można utworzyć kontrolki poza małe obrazy, które wyglądają jak przyciski telewizyjnych w Twoim regionie. Następnie można kliknięciu tych przycisków, aby zmienić kanału.  
  
 Jest to możliwe, ponieważ przyciski są teraz kontrolki. Za pomocą kontrolek możesz odpowiedzieć na interakcję użytkownika; w tym przypadku, gdy użytkownik kliknie przycisk.  
  
 Aby utworzyć formant, zaznacz obiekt. Następnie na **narzędzia** menu, kliknij przycisk **wprowadzić formant**.  
  
##  <a name="Modify"></a> Umożliwianie wykonywały formantów  
 Formanty może wykonywać akcje podczas interakcji z użytkownikiem. Na przykład mogą rozpocząć animacji, zaktualizować źródło danych lub odtwarzanie wideo.  
  
 Użyj *wyzwalaczy*, *zachowania*, i *zdarzenia* aby wykonywały kontrolki.  
  
### <a name="triggers"></a>Wyzwalacze  
 A *wyzwalacza* zmiany właściwości lub wykonuje zadanie w odpowiedzi na zdarzenie lub zmianę w innej właściwości. Na przykład możesz zmienić kolor przycisku po umieszczeniu nad nim.  
  
 ![Panel "Triggers"](../designers/media/custom-button-blend-propertytriggerinfo.png "custom_button_blend_PropertyTriggerInfo")  
  
 **Obejrzyj krótki film wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Dodaj wyzwalacz właściwości](http://www.popscreen.com/v/6A4gO/Microsoft-Expression-Blend-Adding-a-Property-Trigger).  
  
### <a name="behaviors"></a>Zachowania  
 A *zachowanie* pakiet do ponownego wykorzystania kodu. Go może zrobić coś więcej niż zmiany właściwości. Może wykonywać akcje, takie jak zapytania usługi danych. Blend jest dostarczany z małych kolekcji z nich, ale można dodać więcej. Przeciągnij zachowanie na dowolnego obiektu w Twojego obszaru roboczego, a następnie dostosować zachowanie przez ustawienie właściwości.  
  
 ![FluidMoveBehavior, w panelu właściwości](../designers/media/b4-fluidmovebehaviorproperties-sample.png "b4_FluidMoveBehaviorProperties_Sample")  
  
 **Obejrzyj krótki film wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Blend porad: Wprowadzenie do usługi za pomocą zachowań część 1](http://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).  
  
### <a name="events"></a>Zdarzenia  
 Ultimate elastyczność obsługi *zdarzeń*. Będziesz mieć do napisania kodu.  
  
 **Obejrzyj krótki film wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Dodaj zdarzenie myszy](https://www.youtube.com/watch?v=2PMxAlb-x_E).
