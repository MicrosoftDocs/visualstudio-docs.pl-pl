---
title: 'Instrukcje: Dodawanie poleceń do menu skrótów'
description: Dowiedz się, jak dodawać polecenia do menu skrótów w aplikacji pakietu Office przy użyciu dodatku VSTO.
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
ms.openlocfilehash: 2f5c244d78ab5a6b5d98550b11c280159f285db7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913455"
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>Instrukcje: Dodawanie poleceń do menu skrótów
  W tym temacie pokazano, jak dodać polecenia do menu skrótów w aplikacji pakietu Office przy użyciu dodatku VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

### <a name="to-add-commands-to-shortcut-menus-in-office"></a>Aby dodać polecenia do menu skrótów w pakiecie Office

1. Dodaj element **XML wstążki** do projektu dodatku VSTO lub poziomu dokumentu. Aby uzyskać więcej informacji, zobacz [How to: wprowadzenie dostosowywanie wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md). W

2. **Eksplorator rozwiązań**, wybierz pozycję **ThisAddIn.cs** lub **ThisAddIn. vb**.

3. Na pasku menu wybierz polecenie **Wyświetl**  >  **kod**.

     Plik klasy **ThisAddIn** zostanie otwarty w edytorze kodu.

4. Dodaj następujący kod do klasy **ThisAddIn** . Ten kod przesłania `CreateRibbonExtensibilityObject` metodę i zwraca klasę XML wstążki do aplikacji pakietu Office.

     [!code-csharp[Trin_WordAddIn_Menus#1](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#1)]
     [!code-vb[Trin_WordAddIn_Menus#1](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#1)]

5. W **Eksplorator rozwiązań** wybierz plik XML wstążki. Domyślnie plik XML wstążki ma nazwę *Ribbon1.xml*.

6. Na pasku menu wybierz polecenie **Wyświetl**  >  **kod**.

     Plik XML wstążki zostanie otwarty w edytorze kodu.

7. W edytorze kodu, Dodaj kod XML, który opisuje menu skrótów i kontrolkę, którą chcesz dodać do menu skrótów.

     Poniższy przykład dodaje przycisk, menu i kontrolkę Galeria do menu skrótów dla dokumentu programu Word. Identyfikator kontrolki tego menu skrótów to ContextMenuText. Aby uzyskać pełną listę identyfikatorów kontrolek skrótu pakietu Office 2010, zobacz [pliki pomocy pakietu office 2010: identyfikatory formantów interfejsu użytkownika pakietu Office Fluent](https://www.microsoft.com/download/details.aspx?id=6627).

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

8. W **Eksplorator rozwiązań** wybierz pozycję **MyRibbon.cs** lub **wstążka. vb**.

9. Dodaj metodę wywołania zwrotnego do `Ribbon1` klasy dla każdej kontrolki, która ma być obsługiwana.

     Następująca metoda wywołania zwrotnego obsługuje przycisk **My** . Ten kod dodaje ciąg do aktywnego dokumentu w bieżącej lokalizacji programu.

     [!code-vb[Trin_WordAddIn_Menus#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb#2)]
     [!code-csharp[Trin_WordAddIn_Menus#2](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs#2)]

## <a name="see-also"></a>Zobacz też
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Przewodnik: Tworzenie menu skrótów dla zakładek](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
- [Dostosowywanie menu kontekstowego w pakiecie Office 2010](/previous-versions/office/developer/office-2010/ee691832(v=office.14))
