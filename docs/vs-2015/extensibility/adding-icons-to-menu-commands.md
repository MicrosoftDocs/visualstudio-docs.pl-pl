---
title: Dodawanie ikon do poleceń Menu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d10659487d9a747e2359f8fa2e68122b0938a77d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768126"
---
# <a name="adding-icons-to-menu-commands"></a>Dodawanie ikon do poleceń menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Polecenia może znajdować się w menu i na paskach narzędzi. Na paskach narzędzi jest typowe dla polecenia będą wyświetlane tylko ikony (tak, aby zaoszczędzić miejsce na) podczas w menu, że polecenia pojawi się zazwyczaj z zarówno ikonę i tekst.  
  
 Ikony są 16 pikseli szerokości i wysokości 16 pikseli i może być 8-bitowej głębi kolorów (256 kolorów) lub 32-bitowej głębi kolorów (kolor true). ikon koloru 32-bitowe są preferowane. Ikony zwykle są rozmieszczone w jednym wierszu poziomy w postaci bitmapy, chociaż wiele mapy bitowe są dozwolone. Ta mapa bitowa jest zadeklarowana w pliku vsct wraz z poszczególnych ikon dostępnych w mapie bitowej. Zobacz odwołanie do [Bitmaps, Element](../extensibility/bitmaps-element.md) Aby uzyskać więcej informacji.  
  
## <a name="adding-an-icon-to-a-command"></a>Dodawanie ikony do polecenia  
 W poniższej procedurze przyjęto, że masz istniejący projekt pakietu VSPackage przy użyciu polecenia menu. Aby dowiedzieć się, jak to zrobić, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
1.  Tworzenie mapy bitowej o głębi kolorów 32 bity. Ikona jest zawsze 16 x 16, więc tej mapy bitowej muszą być 16 pikseli i wielokrotnością liczby 16 pikseli szerokości.  
  
     Każda ikona jest umieszczany na mapę bitową obok siebie w jednym wierszu. Kanał alfa umożliwia wskazanie miejsc przejrzystości każda ikona.  
  
     Jeśli korzystasz z 8-bitowej głębi kolorów, użyj amarantowy, `RGB(255,0,255)`, jako przejrzystości. Jednak ikon koloru 32-bitowe są preferowane.  
  
2.  Skopiuj plik ikony do katalogu zasobów projektu pakietu VSPackage. W Eksploratorze rozwiązań należy dodać ikonę do projektu. (Wybierz zasoby, w menu kontekstowym kliknij przycisk Dodaj, a następnie istniejący element i wybierz swój plik ikony.)  
  
3.  Otwórz plik vsct w edytorze.  
  
4.  Dodaj `GuidSymbol` elementu o nazwie **testIcon**. Utwórz identyfikator GUID (**narzędzia / Tworzenie identyfikatora GUID**, a następnie wybierz **Format rejestru** i kliknięcie przycisku Kopiuj) i wklej go w `value` atrybutu. Wynik powinien wyglądać następująco:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  Dodaj `<IDSymbol>` ikony. `name` Atrybut jest identyfikator ikony i `value` wskazuje swoją pozycję na taśmy, jeśli istnieje. Jeśli istnieje tylko jedna ikona, należy dodać 1. Wynik powinien wyglądać następująco:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  Tworzenie `<Bitmap>` w `<Bitmaps>` części pliku vsct do reprezentowania mapy bitowej zawierający ikony.  
  
    -   Ustaw `guid` wartość odpowiadającą nazwie `<GuidSymbol>` elementu utworzonego w poprzednim kroku.  
  
    -   Ustaw `href` wartość względną ścieżką pliku mapy bitowej (w tym przypadku **zasobów\\< nazwa pliku ikony\>**.  
  
    -   Ustaw `usedList` wartość IDSymbol, została utworzona wcześniej. Ten atrybut określa rozdzielana przecinkami lista ikon, które zostaną użyte w pakietu VSPackage. Ikony nie ma na liście są wykluczone formularza kompilacji.  
  
         Blok mapy bitowej powinien wyglądać następująco:  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  W istniejącym `<Button>` elementu, ustaw `Icon` elementu GUIDSymbol i IDSymbol utworzonych wcześniej wartości. Poniżej przedstawiono przykład elementu przycisk z tych wartości:  
  
    ```xml  
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">  
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />  
        <Icon guid="testIcon" id="testIcon1" />  
        <Strings>  
            <ButtonText>My Command name</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
8.  Przetestuj ikona. Skompiluj projekt, a następnie rozpocząć debugowanie. W doświadczalnym wystąpieniu znaleźć polecenia. Należy widoczna ikona została dodana.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)   
 [Odwołanie do schematu XML VSCT](../extensibility/vsct-xml-schema-reference.md)

