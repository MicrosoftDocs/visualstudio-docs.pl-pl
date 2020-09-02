---
title: Modyfikowanie stylu obiektów w programie Blend | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 31192d2c-5b84-41bc-94c0-898638c170bd
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0335efcb0c42c6fce06df448a0503457e79ec345
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664239"
---
# <a name="modify-the-style-of-objects-in-blend"></a>Modyfikowanie stylu obiektów w programie Blend
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najprostszym sposobem dostosowania obiektu jest ustawienie właściwości w okienku **Właściwości** .

 Jeśli chcesz ponownie użyć ustawień lub grup ustawień, utwórz zasób do ponownego użycia. Może to być *styl*, *szablon*lub coś prostego, takiego jak kolor niestandardowy. Formant może być również wyświetlany inaczej w zależności od jego stanu. Na przykład przycisk włącza kolor zielony, gdy użytkownik go klika.

 **W tym temacie**:

- [Pędzle: modyfikowanie wyglądu obiektu](#Brushes)

- [Style i szablony: tworzenie spójnego wyglądu i działania między kontrolkami](#Styles)

- [Stany wizualne: Zmienianie wyglądu kontrolki na podstawie jej stanu](#Visual)

- [Zasoby: Tworzenie kolorów, stylów i szablonów oraz ponowne używanie ich w przyszłości](#Resources)

## <a name="brushes-modify-the-appearance-of-an-object"></a><a name="Brushes"></a> Pędzle: modyfikowanie wyglądu obiektu
 Zastosuj pędzel do obiektu, jeśli chcesz zmienić jego wygląd.

 **Obejrzyj krótkie wideo:** ![Konfigurowanie zainstalowanych funkcji](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Edytor pędzli](http://www.popscreen.com/v/6A4mO/Microsoft-Expression-Blend-The-Brushes-Editor).

### <a name="paint-a-repeating-image-or-pattern-on-an-object"></a>Malowanie powtarzanego obrazu lub wzorca na obiekcie
 Malowanie powtarzanego obrazu lub wzorca w obiekcie przy użyciu *pędzla kafelków*.

 Aby utworzyć pędzel kafelków, Zacznij od utworzenia *pędzla obrazu*, *pędzla rysowania*lub zasobu *pędzla wizualnego* .

 Utwórz pędzel obrazu przy użyciu obrazu. Na poniższych ilustracjach przedstawiono pędzle obrazu, fragment pędzla obrazu oraz odwrócony pędzel obrazu.

 ![](../designers/media/81f84f56-906d-456b-8288-d77da1e01e31.png "81f84f56-906d-456b-8288-d77da1e01e31") ![](../designers/media/d3782ca8-64da-47a4-a095-c6cdd0fa47a2.png "d3782ca8-64da-47a4-a095-c6cdd0fa47a2") ![](../designers/media/38ae3691-f3f1-4a1e-82ca-c7fa164bf56e.png "38ae3691-f3f1-4a1e-82ca-c7fa164bf56e")

 Utwórz pędzel rysowania przy użyciu rysunku wektora, takiego jak ścieżka lub kształt. Na poniższych ilustracjach przedstawiono pędzel rysowania, malowanie pędzla i przerzucanie pędzla rysowania.

 ![](../designers/media/197666ac-ef57-4c5c-9779-669e991a00a5.png "197666ac-ef57-4c5c-9779-669e991a00a5") ![](../designers/media/ba09cda3-4cee-40ba-b3d4-edc032158bdc.png "ba09cda3-4cee-40ba-b3d4-edc032158bdc") ![](../designers/media/15bf6021-620c-4490-9eae-086153d3f14f.png "15bf6021-620c-4490-9eae-086153d3f14f")

 Utwórz pędzel wizualny na podstawie kontrolki, takiej jak Button. Na poniższych ilustracjach przedstawiono wizualizację wizualną, a pędzle wizualizacji są rozmieszczane.

 ![](../designers/media/fb6c90e0-153c-48fe-b563-e601beac6227.png "fb6c90e0-153c-48fe-b563-e601beac6227") ![](../designers/media/e261b99f-7d8f-4d91-bc84-19c7beccc255.png "e261b99f-7d8f-4d91-bc84-19c7beccc255")

 **Obejrzyj krótkie wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [pędzle kafelków](http://www.popscreen.com/v/6A4iM/Microsoft-Expression-Blend-Tile-Brushes).

## <a name="styles-and-templates-create-a-consistent-look-and-feel-across-controls"></a><a name="Styles"></a> Style i szablony: tworzenie spójnego wyglądu i działania między kontrolkami
 Możesz zaprojektować wygląd i zachowanie kontrolki jeden raz i zastosować ten projekt do innych kontrolek, aby nie trzeba było ich obsługiwać osobno.

 Czy używasz **stylu?**: Jeśli chcesz po prostu ustawić właściwości domyślne (takie jak kolor przycisku), użyj *stylu*. Formant można modyfikować nawet po zastosowaniu stylu do niego.

 Czy używasz **szablonu?**: Jeśli chcesz zmienić strukturę kontrolki, użyj *szablonu*. Załóżmy, że Konwertowanie grafiki lub logo na przycisk. Nie można modyfikować kontrolki po zastosowaniu szablonu do niego.

### <a name="create-a-template-or-style"></a>Tworzenie szablonu lub stylu
 Istnieją dwa sposoby tworzenia szablonu. Możesz przekonwertować dowolny obiekt w obszarze kompozycji na kontrolkę lub oprzeć szablon na istniejącym formancie.

 Aby przekonwertować dowolny obiekt na szablon kontrolki, zaznacz obiekt, a następnie w menu **Narzędzia** wybierz polecenie **Przekształć w kontrolkę**.

 Jeśli chcesz oprzeć szablon w istniejącym formancie, zaznacz obiekt w obszarze kompozycji. Następnie w górnej części obszaru kompozycji wybierz przycisk nawigacyjny, wybierz pozycję **Edytuj szablon**, a następnie wybierz opcję **Edytuj kopię** lub **Utwórz pustą**.

 ![](../designers/media/5ebdb33f-aad2-4c10-a328-5e8b04c56a36.png "5ebdb33f-aad2-4c10-a328-5e8b04c56a36")

 Aby utworzyć styl, wybierz obiekt, a następnie w menu **obiekt** wybierz polecenie **Edytuj styl**, a następnie wybierz **Edytuj kopię** lub **Utwórz pustą**.

- Wybierz opcję **Edytuj kopię** , aby rozpocząć od domyślnego stylu lub szablonu kontrolki.

- Wybierz pozycję **Utwórz pusty** , aby zacząć od początku.

  Opcja **Edytuj bieżące** jest wyświetlana tylko w przypadku edytowania stylu lub szablonu, który został już utworzony. Nie będzie ona wyświetlana dla formantu, który nadal używa domyślnego szablonu systemowego.

  W oknie dialogowym **Tworzenie zasobu stylu** można nazwać styl lub szablon, aby można było go użyć później, lub można zastosować styl lub szablon do wszystkich kontrolek tego typu.

  ![](../designers/media/4818ee6a-ce60-4b79-91c8-3b1871829eea.png "4818ee6a-ce60-4b79-91c8-3b1871829eea")

> [!NOTE]
> Nie można tworzyć stylów ani szablonów dla każdego typu kontrolki. Jeśli kontrolka nie obsługuje tych funkcji, nie pojawi się nad obszarem kompozycji.
>
> Aby powrócić do zakresu edycji dokumentu głównego, kliknij przycisk **Zwróć zakres do** ![](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png "55844eb3-ed98-4f20-aa66-a6f5b23eeb2b") .
>
> ![](../designers/media/4a5612e1-7a28-4587-b870-0fe7112ec2ad.png "4a5612e1-7a28-4587-b870-0fe7112ec2ad")

 **Obejrzyj krótkie wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Utwórz styl](https://www.youtube.com/watch?v=W8YdXDPeKdc).

### <a name="apply-a-style-or-template-to-a-control"></a>Stosowanie stylu lub szablonu do kontrolki
 Kliknij prawym przyciskiem myszy obiekt w panelu [obiekty i oś czasu](https://msdn.microsoft.com/135a5a5e-ec6d-4f38-8827-60e284cd5f57) , wybierz polecenie **Edytuj szablon**, a następnie wybierz polecenie **Zastosuj zasób**.

 ![](../designers/media/dc12debc-7711-47d9-84ce-10322a384397.png "dc12debc-7711-47d9-84ce-10322a384397")

### <a name="restore-the-default-style-or-template-of-a-control"></a>Przywracanie domyślnego stylu lub szablonu kontrolki
 Zaznacz kontrolkę, a następnie w panelu [Właściwości](https://msdn.microsoft.com/135a5a5e-ec6d-4f38-8827-60e284cd5f57) Znajdź właściwość **styl** lub **szablon** . Następnie kliknij pozycję **Opcje zaawansowane** ![](../designers/media/12e06962-5d8a-480d-a837-e06b84c545bb.png "12e06962-5d8a-480d-a837-e06b84c545bb") , a następnie w menu skrótów kliknij polecenie **Zresetuj** .

## <a name="visual-states-change-the-appearance-of-a-control-based-on-its-state"></a><a name="Visual"></a> Stany wizualne: Zmienianie wyglądu kontrolki na podstawie jej stanu
 Kontrolki mogą mieć różne wyglądy wizualizacji w oparciu o Interakcje użytkownika. Na przykład można sprawić, aby przycisk był zielony, gdy użytkownik kliknie go lub uruchomi animację. Skracanie lub wydłużenie czasu między Stanami wizualnymi przy użyciu przejść.

 ![](../designers/media/a95c671a-5639-40b9-83db-1e6b214330d5.png "a95c671a-5639-40b9-83db-1e6b214330d5")

 **Obejrzyj krótkie wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Zarządzaj stanem formantów WPF](https://www.youtube.com/watch?v=m0PlkF5i6uw).

## <a name="resources-create-colors-styles-and-templates-and-reuse-them-later"></a><a name="Resources"></a> Zasoby: Tworzenie kolorów, stylów i szablonów oraz ponowne używanie ich w przyszłości
 Możesz skonwertować wszystko w projekcie do zasobu. Zasób jest tylko obiektem, którego można użyć w różnych miejscach w aplikacji. Na przykład można utworzyć kolor jeden raz, uczynić go zasobem, a następnie używać tego koloru na kilku obiektach. Aby zmienić kolor wszystkich tych obiektów, wystarczy zmienić zasób koloru.

 ![](../designers/media/89203705-cf66-46e0-b153-52a23cd744f7.png "89203705-cf66-46e0-B153-52a23cd744f7") ![](../designers/media/6bff8b19-3cd5-41a0-bbf9-ff65532d5aae.png "6bff8b19-3cd5-41a0-bbf9-ff65532d5aae")

 **Obejrzyj krótkie wideo:** ![Skonfiguruj zainstalowane funkcje](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [krótko mówiąc z zasobami](http://www.popscreen.com/v/6A4k7/Microsoft-Expression-Blend-Brief-Touch-on-Resources).

## <a name="see-also"></a>Zobacz też
 [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
