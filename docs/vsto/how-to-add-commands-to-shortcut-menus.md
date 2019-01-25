---
title: 'Instrukcje: Dodawanie poleceń do menu skrótów'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office menus, creating
- Office development in Visual Studio, context menus
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8bcbcce4ad5d1301cc8c9ba0f76b932e5e2390e3
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872810"
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>Instrukcje: Dodawanie poleceń do menu skrótów
  W tym temacie pokazano, jak dodać polecenia do menu skrótów w aplikacji pakietu Office przy użyciu dodatku narzędzi VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
### <a name="to-add-commands-to-shortcut-menus-in-office"></a>Aby dodać polecenia do menu skrótów w pakiecie Office  
  
1.  Dodaj **kodu XML wstążki** elementu na poziomie dokumentu lub projekt dodatku narzędzi VSTO dla programów. Aby uzyskać więcej informacji, zobacz [jak: Wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md). W  
  
2.  **Eksplorator rozwiązań**, wybierz opcję **ThisAddin.cs** lub **ThisAddin.vb**.  
  
3.  Na pasku menu wybierz **widoku** > **kodu**.  
  
     **ThisAddin** plik klas zostanie otwarty w edytorze kodu.  
  
4.  Dodaj następujący kod do **ThisAddin** klasy. Ten kod zastępuje `CreateRibbonExtensibilityObject` metodę i zwraca XML wstążki klasy do aplikacji pakietu Office.  
  
     [!code-csharp[Trin_WordAddIn_Menus#1](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#1)]
     [!code-vb[Trin_WordAddIn_Menus#1](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#1)]  
  
5.  W **Eksploratora rozwiązań**, wybierz plik XML wstążki. Domyślnie, nosi nazwę pliku XML wstążki *Ribbon1.xml*.  
  
6.  Na pasku menu wybierz **widoku** > **kodu**.  
  
     Plik xml wstążki, zostanie otwarty w edytorze kodu.  
  
7.  W edytorze kodu Dodaj kod XML, który opisuje, w menu skrótów i formant, który chcesz dodać do menu skrótów.  
  
     Poniższy przykład dodaje przycisk, menu i kontrolkę galerii do menu skrótów dla dokumentu programu word. Identyfikator formantu tego menu skrótów jest ContextMenuText. Aby uzyskać pełną listę kontroli skrótów pakietu Office 2010 identyfikatory, zobacz [pliki Pomocy pakietu Office 2010: Identyfikatory kontrolki interfejsu użytkownika fluent Office](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>  
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui">  
      <contextMenus>  
        <contextMenu idMso="ContextMenuText">  
          <button id="MyButton" label="My Button" insertBeforeMso="HyperlinkInsert" onAction="GetButtonID" />  
          <menu id="MySubMenu" label="My Submenu" >  
            <button id="MyButton2" label="Button on submenu" />  
          </menu>  
          <gallery id="galleryOne" label="My Gallery">  
            <item id="item1" imageMso="HappyFace" />  
            <item id="item2" imageMso="HappyFace" />  
            <item id="item3" imageMso="HappyFace" />  
            <item id="item4" imageMso="HappyFace" />  
          </gallery>  
        </contextMenu>  
      </contextMenus>  
    </customUI>  
    ```  
  
8.  W **Eksploratora rozwiązań**, wybierz **MyRibbon.cs** lub **MyRibbon.vb**.  
  
9. Dodaj metodę wywołania zwrotnego, która `Ribbon1` klasy dla każdego formantu, który chcesz obsługiwać.  
  
     Następujące obsługuje metody wywołania zwrotnego **przycisk Moje** przycisku. Ten kod dodaje ciąg do aktywnego dokumentu w bieżącej lokalizacji kursor.  
  
     [!code-vb[Trin_WordAddIn_Menus#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb#2)]
     [!code-csharp[Trin_WordAddIn_Menus#2](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs#2)]  
  
## <a name="see-also"></a>Zobacz także  
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [Przewodnik: Tworzenie menu skrótów dla zakładek](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Dostosowywanie menu kontekstowe w pakiecie Office 2010](http://go.microsoft.com/fwlink/?LinkId=182186)  
