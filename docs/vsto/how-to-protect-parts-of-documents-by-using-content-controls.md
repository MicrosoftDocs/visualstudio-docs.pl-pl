---
title: Jak chronić części dokumentów za pomocą kontrolek zawartości
description: Dowiedz się, jak używać Visual Studio do ochrony części dokumentu programu Microsoft Word przy użyciu kontrolek zawartości.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- partial document protection [Office development in Visual Studio]
- content controls [Office development in Visual Studio], protecting documents
- Word [Office development in Visual Studio], partial document protection
- document protection [Office development in Visual Studio]
- Word [Office development in Visual Studio], restricted permissions
- GroupContentControl
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cc333871d4f371530db84a0c4f07ab891db2a937
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825475"
---
# <a name="how-to-protect-parts-of-documents-by-using-content-controls"></a>Jak chronić części dokumentów za pomocą kontrolek zawartości
  Ochrona części dokumentu uniemożliwia użytkownikom zmienianie lub usuwanie zawartości w tej części dokumentu. Istnieje kilka sposobów ochrony części dokumentu programu Microsoft Office Word za pomocą kontrolek zawartości:

- Możesz chronić kontrolkę zawartości.

- Możesz chronić część dokumentu, która nie znajduje się w kontrolce zawartości.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="protect-a-content-control"></a><a name="EditDeleteControl"></a> Ochrona kontrolki zawartości
 Możesz uniemożliwić użytkownikom edytowanie lub usuwanie kontrolki zawartości, ustawiając właściwości kontrolki w projekcie na poziomie dokumentu w czasie projektowania lub w czasie uruchamiania.

 Kontrolki zawartości, które można dodać do dokumentu w czasie uruchamiania, można również chronić za pomocą projektu dodatku VSTO. Aby uzyskać więcej informacji, zobacz How to: Add content controls to Word documents (Jak [dodawać kontrolki zawartości do dokumentów programu Word).](../vsto/how-to-add-content-controls-to-word-documents.md)

### <a name="to-protect-a-content-control-at-design-time"></a>Aby chronić kontrolkę zawartości w czasie projektowania

1. W dokumencie hostowany w projektancie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wybierz kontrolkę zawartości, którą chcesz chronić.

2. W **oknie** Właściwości ustaw jedną lub obie następujące właściwości:

    - Aby uniemożliwić użytkownikom edytowanie kontrolki, ustaw wartość True dla **ustawienia LockContents.**

    - Aby uniemożliwić użytkownikom usuwanie kontrolki, ustaw wartość **True** **dla ustawienia LockContentControl.**

3. Kliknij przycisk **OK**.

### <a name="to-protect-a-content-control-at-run-time"></a>Aby chronić kontrolkę zawartości w czasie uruchamiania

1. Ustaw właściwość kontrolki zawartości na wartość true, aby uniemożliwić użytkownikom edytowanie kontrolki, a właściwość na wartość true, aby uniemożliwić użytkownikom `LockContents` usunięcie  `LockContentControl` kontrolki. 

     Poniższy przykład kodu demonstruje użycie właściwości <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> i dwóch różnych obiektów w <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> <xref:Microsoft.Office.Tools.Word.RichTextContentControl> projekcie na poziomie dokumentu. Aby uruchomić ten kod, dodaj kod do klasy w projekcie i wywołaj `ThisDocument` metodę z procedury obsługi `AddProtectedContentControls` `ThisDocument_Startup` zdarzeń.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb" id="Snippet2":::

     Poniższy przykład kodu demonstruje użycie właściwości i dwóch różnych <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> obiektów w <xref:Microsoft.Office.Tools.Word.RichTextContentControl> projekcie dodatku VSTO. Aby uruchomić ten kod, dodaj kod do klasy w projekcie `ThisAddIn` i wywołaj `AddProtectedContentControls` metodę z procedury `ThisAddIn_Startup` obsługi zdarzeń.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet14":::

## <a name="protect-a-part-of-a-document-that-is-not-in-a-content-control"></a>Ochrona części dokumentu, która nie znajduje się w kontrolce zawartości
 Możesz uniemożliwić użytkownikom zmianę obszaru dokumentu, umieszczając go w obszarze <xref:Microsoft.Office.Tools.Word.GroupContentControl> . Jest to przydatne w następujących scenariuszach:

- Chcesz chronić obszar, który nie zawiera kontrolek zawartości.

- Chcesz chronić obszar, który zawiera już kontrolki zawartości, ale tekst lub inne elementy, które chcesz chronić, nie znajdują się w kontrolkach zawartości.

> [!NOTE]
> W przypadku utworzenia <xref:Microsoft.Office.Tools.Word.GroupContentControl> kontrolki zawierającej osadzone kontrolki zawartości osadzone kontrolki zawartości nie są automatycznie chronione. Aby uniemożliwić użytkownikom edytowanie osadzonej kontrolki zawartości, użyj właściwości **LockContents** kontrolki.

### <a name="to-protect-an-area-of-a-document-at-design-time"></a>Aby chronić obszar dokumentu w czasie projektowania

1. W dokumencie hostowany w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektancie wybierz obszar, który chcesz chronić.

2. Na wstążce kliknij **kartę Deweloper.**

    > [!NOTE]
    > Jeśli karta **Deweloper** nie jest widoczna, musisz ją najpierw wyświetlić. Aby uzyskać więcej informacji, zobacz How to: Show the developer tab on the ribbon (Jak [wyświetlić kartę dewelopera na wstążce).](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)

3. W grupie **Kontrolki** kliknij przycisk **listy** rozwijanej Grupa, a następnie kliknij pozycję **Grupuj.**

     Klasa <xref:Microsoft.Office.Tools.Word.GroupContentControl> zawierająca chroniony region jest generowana automatycznie w `ThisDocument` klasie w projekcie. Obramowanie reprezentujące kontrolkę grupy jest widoczne w czasie projektowania, ale nie ma widocznego obramowania w czasie uruchamiania.

### <a name="to-protect-an-area-of-a-document-at-run-time"></a>Aby chronić obszar dokumentu w czasie uruchamiania

1. Programowo wybierz obszar, który chcesz chronić, a następnie <xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A> wywołaj metodę , aby utworzyć <xref:Microsoft.Office.Tools.Word.GroupContentControl> .

     Poniższy przykład kodu dla projektu na poziomie dokumentu dodaje tekst do pierwszego akapitu w dokumencie, wybiera pierwszy akapit, a następnie iniekuje . <xref:Microsoft.Office.Tools.Word.GroupContentControl> Aby uruchomić ten kod, dodaj kod do klasy w projekcie i wywołaj `ThisDocument` metodę z procedury obsługi `ProtectFirstParagraph` `ThisDocument_Startup` zdarzeń.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb" id="Snippet1":::

     Poniższy przykład kodu dla projektu dodatku VSTO dodaje tekst do pierwszego akapitu w aktywnym dokumencie, wybiera pierwszy akapit, a następnie iniektuje . <xref:Microsoft.Office.Tools.Word.GroupContentControl> Aby uruchomić ten kod, dodaj kod do klasy w projekcie i wywołaj `ThisAddIn` metodę z procedury obsługi `ProtectFirstParagraph` `ThisAddIn_Startup` zdarzeń.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet15":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet15":::

## <a name="see-also"></a>Zobacz też
- [Automatyzowanie programu Word przy użyciu obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Kontrolki zawartości](../vsto/content-controls.md)
- [2017: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [Programowe ograniczenia elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie rzeczywistym](../vsto/adding-controls-to-office-documents-at-run-time.md)
