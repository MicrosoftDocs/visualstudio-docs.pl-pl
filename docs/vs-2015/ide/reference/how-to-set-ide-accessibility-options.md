---
title: 'Instrukcje: Ustawianie opcji ułatwień dostępu IDE | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 18f03e2bd37d8275685f34a65c9ab96740ed80a3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60051625"
---
# <a name="how-to-set-ide-accessibility-options"></a>Instrukcje: Ustawianie opcji ułatwień dostępu IDE
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zawiera funkcje, które ułatwiają dla osób niedowidzących do odczytu, a także dla osób o ograniczonej sprawności ruchowej, aby zapisać. Funkcje te obejmują, zmienianie rozmiaru i koloru tekstu w edytorach, zmieniając rozmiar tekstu i przycisków na paskach narzędzi i automatycznego uzupełniania dla metod i parametrów, kilka.  
  
 Ponadto [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] obsługuje układy klawiatury Dvoraka, które powodują, że najczęściej wpisane znaki łatwiej dostępne. Można również dostosować domyślne klawiszy skrótu dostępnych z [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Aby uzyskać więcej informacji, zobacz [określenie i dostosowywanie skrótów klawiaturowych](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="editors-dialogs-and-tool-windows"></a>Edytory, okna dialogowe i narzędzie Windows  
 Domyślnie, okna dialogowe i okna narzędzi w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] używać tego samego rozmiaru czcionki i kolory jako systemu operacyjnego. Ustawienia kolorów dla ramki w IDE, okna dialogowe, paski narzędzi i okien narzędzi opierają się schemat kolorów: jasny i ciemny. Możesz zmienić bieżący motyw kolorów w [ogólne, środowisko, opcje, okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md).  
  
 Można także wyświetlić wyskakującego okienka, w widoku kodu w edytorze. Te okna można monitują dostępni członkowie na bieżący obiekt i parametry do wykonania funkcji lub instrukcji. Okna te mogą być przydatne, jeśli masz problemy z pisaniem. Jednak przeszkadzają fokus w edytorze kodu, który może być problematyczne dla niektórych użytkowników. Można wyłączyć te okna, otwierając okno dialogowe Opcje i wyczyszczenie **automatyczna lista członków** i **informacje o parametrach** w **edytora tekstów**, **wszystkie Języki**, **ogólne** strony w **opcje** okno dialogowe. Aby uzyskać więcej informacji, zobacz [jak: Ustawianie opcji ogólnych edytora](http://msdn.microsoft.com/704e4a7b-2162-4bed-8a47-f4f6ffec98c2).  
  
 Możesz zmienić kolejność systemu windows w zintegrowanym środowisku programistycznym (IDE) stosownie do potrzeb sposobu pracy. Można zadokować, float, ukryć lub automatycznie ukrywaj każdego okna narzędzi.  
  
 Aby uzyskać więcej informacji dotyczących sposobu zmieniania układy okna, zobacz [dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
### <a name="changing-the-size-of-text"></a>Zmiana rozmiaru tekstu  
 Można zmienić ustawienia dla okien narzędzi oparte na tekście, takie jak **polecenia** oknie **bezpośrednie** oknie i **dane wyjściowe** okna w **czcionek i Kolory** okienku **środowiska** opcji na liście **narzędzia** okno dialogowe. Gdy **[wszystkie tekstowe narzędzie Windows]** wybrano w **Pokaż ustawienia dla** listy rozwijanej ustawieniem domyślnym jest wymieniony jako **domyślne** w **pierwszy plan elementu**  i **tła elementu** list rozwijanych. Ustawienia można również zmienić sposób wyświetlania tekstu w edytorze.  
  
##### <a name="to-change-the-size-of-text-in-text-based-tool-windows-and-editors"></a>Aby zmienić rozmiar tekstu w oknach narzędzi tekstowych i edytory  
  
1. Z **narzędzia** menu, wybierz **opcje**.  
  
2. Wybierz **czcionki i kolory** na **środowiska** folderu.  
  
3. Wybierz jedną z opcji na **Pokaż ustawienia dla** menu rozwijanego.  
  
     Aby zmienić rozmiar czcionki dla tekstu w edytorze, wybierz **edytora tekstów**.  
  
     Aby zmienić rozmiar czcionki dla tekstu w oknach narzędzi tekstowych, wybierz **[Windows wszystkie narzędzia Tekst]**.  
  
     Aby zmienić rozmiar czcionki dla tekstu etykietki narzędzia w edytorze, wybierz **etykietki narzędzi edytora**.  
  
     Aby zmienić rozmiar czcionki dla tekstu w wyskakujące okienka uzupełniania instrukcji, wybierz **uzupełniania instrukcji**.  
  
4. Z **wyświetlania elementów**, wybierz opcję **zwykły tekst**.  
  
5. W **czcionki**, wybierz nowy typ czcionki.  
  
6. W **rozmiar**, wybierz nowy rozmiar czcionki.  
  
    > [!NOTE]
    >  Aby zresetować rozmiar okna narzędzi tekstowych i edytorów, wybierz **Użyj ustawień domyślnych**.  
  
7. Wybierz **OK**.  
  
### <a name="changing-the-colors-used-in-the-ide"></a>Zmienianie kolorów używanych w środowisku IDE  
 Możesz również zmienić kolory domyślne tekstu, wskaźniki margines, biały i elementy kodu w edytorze.  
  
> [!NOTE]
>  Aby użyć dużego kontrastu kolorów dla wszystkich aplikacji systemu windows w systemie operacyjnym, naciśnij klawisz po lewej stronie <strong>ALT +</strong>po lewej stronie **SHIFT + PRINT SCREEN**. Jeśli [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] jest otworzyć, zamknij i otwórz ponownie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] do pełnego wdrożenia dużego kontrastu kolorów.  
  
##### <a name="to-change-the-color-of-items-in-the-editor"></a>Aby zmienić kolor elementów w edytorze  
  
1. Z **narzędzia** menu, wybierz **opcje**.  
  
2. Wybierz **czcionki i kolory** z **środowiska** folderu.  
  
3. W **Pokaż ustawienia dla**, wybierz **edytora tekstów**.  
  
4. Z **wyświetlania elementów**, wybierz element, którego ekran zachodzi potrzeba zmiany, takie jak **zwykły tekst**, **margines wskaźnika**, **pokazuj biały znak**, **Nazwa atrybutu HTML**, lub **atrybutu XML**.  
  
5. Wybierz ustawienia wyświetlania spośród następujących opcji: **Pierwszy plan elementu**, **tła elementu**, i **Bold**.  
  
6. Wybierz **OK**.  
  
## <a name="toolbars"></a>Paski narzędzi  
 Aby zwiększyć użyteczność paska narzędzi i dostępność, można dodać tekstu do przycisków paska narzędzi.  
  
#### <a name="to-assign-text-to-toolbar-buttons"></a>Aby przypisać tekstu do przycisków paska narzędzi  
  
1. Z **narzędzia** menu, wybierz **Dostosuj**.  
  
2. W **Dostosuj** okno dialogowe, wybierz opcję **polecenia** kartę.  
  
3. Wybierz **narzędzi** , a następnie wybierz nazwę paska narzędzi, zawierający przycisk, mają do wyświetlania tekstu.  
  
4. Na liście wybierz polecenie, które chcesz zmienić.  
  
5. Wybierz **Modyfikuj zaznaczenie**.  
  
6. Wybierz **tekstowych i obrazów**.  
  
#### <a name="to-modify-the-buttons-displayed-text"></a>Aby zmodyfikować go w wyświetlanym tekstem  
  
1. Wybierz ponownie **Modyfikuj zaznaczenie**.  
  
2. Sąsiadujące w **nazwa**, Wstaw Podaj nowy podpis dla przycisku.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje ułatwień dostępu programu Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)   
 [Zasoby do projektowania dostępnych aplikacji](../../ide/reference/resources-for-designing-accessible-applications.md)
