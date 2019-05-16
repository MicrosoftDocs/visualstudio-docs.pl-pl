---
title: Modyfikowanie stylu obiektów w programie Blend | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 31192d2c-5b84-41bc-94c0-898638c170bd
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a5ca94c88a1f131065b7d5de57e9cdc200696d58
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65681429"
---
# <a name="modify-the-style-of-objects-in-blend"></a>Modyfikowanie stylu obiektów w programie Blend
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najprostszym sposobem dostosować obiekt jest do ustawiania właściwości **właściwości** okienka.  
  
 Jeśli chcesz ponownie użyć ustawień lub grupy ustawień, należy utworzyć zasób do ponownego użycia. Może to być *styl*, *szablonu*, lub coś prostego, takich jak kolor niestandardowy. Można również ustawić kontrolki pojawiają się inaczej w oparciu o jego stan. Na przykład przycisk zmienia kolor na zielony, gdy użytkownik kliknie przycisk.  
  
 **W tym temacie**:  
  
- [Pędzle: Modyfikowanie wyglądu obiektu](#Brushes)  
  
- [Style i szablony: Tworzenie spójnego wyglądu i zachowania między formantów](#Styles)  
  
- [Stany wizualne: Zmienianie wyglądu kontrolki oparte na stanie](#Visual)  
  
- [Zasoby dotyczące oprogramowania: Tworzenie, kolory, style i szablony i używać ich ponownie później](#Resources)  
  
## <a name="Brushes"></a> Pędzle: Modyfikowanie wyglądu obiektu  
 Stosowanie pędzla do obiektu, jeśli chcesz zmienić jego wygląd.  
  
 **Obejrzyj krótki film wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pędzle edytora](http://www.popscreen.com/v/6A4mO/Microsoft-Expression-Blend-The-Brushes-Editor).  
  
### <a name="paint-a-repeating-image-or-pattern-on-an-object"></a>Malowanie powtarzające się obraz lub wzorzec do obiektu  
 Malowanie powtarzające się obraz lub wzorzec do obiektu za pomocą *pędzla kafelków*.  
  
 Aby utworzyć pędzla kafelków, Rozpocznij od utworzenia *obrazu pędzla*, *DrawingBrush*, lub *VisualBrush* zasobów.  
  
 Tworzenie pędzla obrazu przy użyciu obrazu. Na poniższych ilustracjach przedstawiono pędzla obrazu, ImageBrush sąsiadująco i przerzucać pędzla obrazu.  
  
 ![](../designers/media/81f84f56-906d-456b-8288-d77da1e01e31.png "81f84f56-906d-456b-8288-d77da1e01e31") ![](../designers/media/d3782ca8-64da-47a4-a095-c6cdd0fa47a2.png "d3782ca8-64da-47a4-a095-c6cdd0fa47a2") ![](../designers/media/38ae3691-f3f1-4a1e-82ca-c7fa164bf56e.png "38ae3691-f3f1-4a1e-82ca-c7fa164bf56e")  
  
 Tworzenie pędzla przy użyciu wektorowej, takich jak ścieżki lub kształtu. Na poniższych ilustracjach przedstawiono pędzla, pędzla sąsiadująco i pędzla odwrócony.  
  
 ![](../designers/media/197666ac-ef57-4c5c-9779-669e991a00a5.png "197666ac-ef57-4c5c-9779-669e991a00a5") ![](../designers/media/ba09cda3-4cee-40ba-b3d4-edc032158bdc.png "ba09cda3-4cee-40ba-b3d4-edc032158bdc") ![](../designers/media/15bf6021-620c-4490-9eae-086153d3f14f.png "15bf6021-620c-4490-9eae-086153d3f14f")  
  
 Tworzenie pędzla visual w kontrolce, takiej jak przycisk. Na poniższych ilustracjach przedstawiono VisualBrush i VisualBrush sąsiadująco.  
  
 ![](../designers/media/fb6c90e0-153c-48fe-b563-e601beac6227.png "fb6c90e0-153c-48fe-b563-e601beac6227") ![](../designers/media/e261b99f-7d8f-4d91-bc84-19c7beccc255.png "e261b99f-7d8f-4d91-bc84-19c7beccc255")  
  
 **Obejrzyj krótki film wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Kafelek pędzle](http://www.popscreen.com/v/6A4iM/Microsoft-Expression-Blend-Tile-Brushes).  
  
## <a name="Styles"></a> Style i szablony: Tworzenie spójnego wyglądu i zachowania między formantów  
 Można zaprojektować wygląd i zachowanie kontrolki, jeden raz i zastosowanie tego projektu do innych kontrolek, dzięki czemu nie trzeba zachować je oddzielnie.  
  
 **Należy użyć stylu?** : Jeśli chcesz ustawić domyślne właściwości (np. kolor przycisku), użyj *styl*. Kontrolki można modyfikować, nawet w przypadku, po zastosowaniu styl do niego.  
  
 **Należy użyć szablonu?** : Jeśli chcesz zmienić strukturę kontrolki, należy użyć *szablonu*. Wyobraź sobie, konwertowania grafika lub logo na przycisku. Nie można zmodyfikować kontrolki, po zastosowaniu szablonu do niego.  
  
### <a name="create-a-template-or-style"></a>Tworzenie stylu lub szablonu  
 Ma dwa sposoby tworzenia szablonu. Dowolny obiekt można przekonwertować na Twojego obszaru roboczego do formantu lub szablonu można oprzeć na istniejącej kontrolki.  
  
 Aby przekonwertować dowolny obiekt szablonu kontrolki, zaznacz obiekt, a następnie na **narzędzia** menu, wybierz **przerób na kontrolkę**.  
  
 Jeśli chcesz utworzyć nowy szablon istniejącej kontrolki, zaznacz obiekt w obszarze kompozycji. Następnie w górnej części obszaru kompozycji wybierz przycisk nawigacji, wybierz polecenie **Edytuj szablon**, a następnie wybierz **Edytuj kopię** lub **Utwórz pusty**.  
  
 ![](../designers/media/5ebdb33f-aad2-4c10-a328-5e8b04c56a36.png "5ebdb33f-aad2-4c10-a328-5e8b04c56a36")  
  
 Tworzenie stylu, wybierz obiekt, a następnie w polu **obiektu** menu, wybierz **Edytuj styl**, a następnie wybierz **Edytuj kopię** lub **Utwórz pusty**.  
  
- Wybierz **Edytuj kopię** chcesz rozpocząć od domyślnego stylu lub szablonu kontrolki.  
  
- Wybierz **Utwórz pusty** od samego początku.  
  
  **Edytuj bieżący** opcja jest wyświetlana tylko wtedy, gdy edytujesz stylu lub szablonu, który został już utworzony. Nie będzie on widoczny dla formantu, który nadal jest używany domyślny szablon systemu.  
  
  W **tworzenie zasobu stylu** okno dialogowe można albo nazwę stylu lub szablonu, aby można jej użyć później, lub stylu lub szablonu można zastosować do wszystkich formantów tego typu.  
  
  ![](../designers/media/4818ee6a-ce60-4b79-91c8-3b1871829eea.png "4818ee6a-ce60-4b79-91c8-3b1871829eea")  
  
> [!NOTE]
> Nie można utworzyć style lub szablony dla każdego typu formantu. Jeśli ich nie obsługuje formant, przycisk nawigacji nie pojawi się powyżej obszaru kompozycji.  
>   
> Aby powrócić do zakresu edycji dokumentu głównego, kliknij przycisk **Zwróć zakres do** ![](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png "55844eb3-ed98-4f20-aa66-a6f5b23eeb2b").  
>   
> ![](../designers/media/4a5612e1-7a28-4587-b870-0fe7112ec2ad.png "4a5612e1-7a28-4587-b870-0fe7112ec2ad")  
  
 **Obejrzyj krótki film wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Tworzenie stylu](https://www.youtube.com/watch?v=W8YdXDPeKdc).  
  
### <a name="apply-a-style-or-template-to-a-control"></a>Stosowanie stylu lub szablonu do formantu  
 Kliknij prawym przyciskiem myszy obiekt w [obiekty i oś czasu](https://msdn.microsoft.com/135a5a5e-ec6d-4f38-8827-60e284cd5f57) panelu, wybierz polecenie **Edytuj szablon**, a następnie wybierz **Zastosuj zasób**.  
  
 ![](../designers/media/dc12debc-7711-47d9-84ce-10322a384397.png "dc12debc-7711-47d9-84ce-10322a384397")  
  
### <a name="restore-the-default-style-or-template-of-a-control"></a>Przywracanie domyślnego stylu lub szablonu kontrolki  
 Wybierz kontrolkę a następnie w [właściwości](https://msdn.microsoft.com/135a5a5e-ec6d-4f38-8827-60e284cd5f57) panelu, odszukaj **styl** lub **szablonu** właściwości. Następnie kliknij przycisk **zaawansowane opcje** ![](../designers/media/12e06962-5d8a-480d-a837-e06b84c545bb.png "12e06962-5d8a-480d-a837-e06b84c545bb"), a następnie kliknij przycisk **resetowania** w menu skrótów.  
  
## <a name="Visual"></a> Stany wizualne: Zmienianie wyglądu kontrolki oparte na stanie  
 Formanty mogą mieć inny wygląd visual na podstawie interakcji użytkownika. Można na przykład należy przycisk, zielony, po kliknięciu przez użytkownika lub uruchomieniu animacji. Skróć lub wydłużyć czas między stany wizualne za pomocą przejścia.  
  
 ![](../designers/media/a95c671a-5639-40b9-83db-1e6b214330d5.png "a95c671a-5639-40b9-83db-1e6b214330d5")  
  
 **Obejrzyj krótki film wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [zarządzać stanem formantów WPF](https://www.youtube.com/watch?v=m0PlkF5i6uw).  
  
## <a name="Resources"></a> Zasoby dotyczące oprogramowania: Tworzenie, kolory, style i szablony i używać ich ponownie później  
 Możesz również przekonwertować wszystko, co w projekcie do zasobu. Zasób jest tylko obiekt, który można ponownie użyć w różnych miejscach w aplikacji. Na przykład można utworzyć jeden raz kolor, ułatwiają zasobu i następnie użyć tego koloru na kilka obiektów. Aby zmienić kolor wszystkich tych obiektów, można zmienić kolor zasobu.  
  
 ![](../designers/media/89203705-cf66-46e0-b153-52a23cd744f7.png "89203705-cf66-46e0-b153-52a23cd744f7") ![](../designers/media/6bff8b19-3cd5-41a0-bbf9-ff65532d5aae.png "6bff8b19-3cd5-41a0-bbf9-ff65532d5aae")  
  
 **Obejrzyj krótki film wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [krótki touch na zasobach](http://www.popscreen.com/v/6A4k7/Microsoft-Expression-Blend-Brief-Touch-on-Resources).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
