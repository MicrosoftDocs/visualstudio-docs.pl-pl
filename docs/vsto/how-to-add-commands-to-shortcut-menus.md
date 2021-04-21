---
title: 'How to: Add Commands to shortcut menus (Jak dodać polecenia do menu skrótów)'
description: Dowiedz się, jak dodawać polecenia do menu skrótów w aplikacji pakietu Office przy użyciu dodatku narzędzi VSTO.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office menus, creating
- Office development in Visual Studio, context menus
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 276dc7b8094c495a1b3896a4a93a068b1005c8d5
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828452"
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>Jak dodać polecenia do menu skrótów
  W tym temacie pokazano, jak dodać polecenia do menu skrótów w aplikacji pakietu Office przy użyciu dodatku narzędzi VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

### <a name="to-add-commands-to-shortcut-menus-in-office"></a>Aby dodać polecenia do menu skrótów w psłudze Office

1. Dodaj element **XML wstążki** do projektu dodatku na poziomie dokumentu lub VSTO. Aby uzyskać więcej informacji, [zobacz How to: Get started customizing the Ribbon](../vsto/how-to-get-started-customizing-the-ribbon.md)(Jak rozpocząć dostosowywanie wstążki). W

2. **Eksplorator rozwiązań** wybierz pozycję **ThisAddin.cs** lub **ThisAddin.vb.**

3. Na pasku menu wybierz pozycję **Wyświetl**  >  **kod.**

     Plik **klasy ThisAddin** zostanie otwarty w edytorze kodu.

4. Dodaj następujący kod do **klasy ThisAddin.** Ten kod zastępuje metodę i zwraca klasę XML wstążki `CreateRibbonExtensibilityObject` do aplikacji pakietu Office.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb" id="Snippet1":::

5. W **Eksplorator rozwiązań** wybierz plik XML wstążki. Domyślnie plik XML wstążki ma nazwę *Ribbon1.xml*.

6. Na pasku menu wybierz pozycję **Wyświetl**  >  **kod.**

     Plik XML wstążki zostanie otwarty w Edytorze kodu.

7. W Edytorze kodu dodaj kod XML opisujący menu skrótów i kontrolkę, którą chcesz dodać do menu skrótów.

     Poniższy przykład dodaje przycisk, menu i kontrolkę galerii do menu skrótów dla dokumentu programu Word. Identyfikator kontrolki tego menu skrótów to ContextMenuText. Aby uzyskać pełną listę identyfikatorów kontrolek skrótów pakietu Office 2010, zobacz Pliki pomocy pakietu [Office 2010: Identyfikatory](https://www.microsoft.com/download/details.aspx?id=6627)kontrolek interfejsu użytkownika fluent pakietu Office.

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

8. W **Eksplorator rozwiązań** wybierz **pozycję MyRibbon.cs** lub **MyRibbon.vb.**

9. Dodaj metodę wywołania zwrotnego do `Ribbon1` klasy dla każdej kontrolki, którą chcesz obsługiwać.

     Następująca metoda wywołania zwrotnego obsługuje **przycisk Mój** przycisk. Ten kod dodaje ciąg do aktywnego dokumentu w bieżącej lokalizacji przekleństwa.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs" id="Snippet2":::

## <a name="see-also"></a>Zobacz też
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Przewodnik: tworzenie menu skrótów dla zakładek](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
- [Dostosowywanie menu kontekstowych w psłudze Office 2010](/previous-versions/office/developer/office-2010/ee691832(v=office.14))
