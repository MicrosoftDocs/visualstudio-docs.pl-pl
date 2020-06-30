---
title: 'Instrukcje: ochrona części dokumentów za pomocą kontrolek zawartości'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b03521023ea0b4d92bd3125f256d2230de9bba03
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541352"
---
# <a name="how-to-protect-parts-of-documents-by-using-content-controls"></a>Instrukcje: ochrona części dokumentów za pomocą kontrolek zawartości
  Ochrona części dokumentu uniemożliwia użytkownikom zmianę lub usunięcie zawartości w tej części dokumentu. Istnieje kilka sposobów ochrony części dokumentu programu Microsoft Office Word przy użyciu kontrolek zawartości:

- Można chronić kontrolkę zawartości.

- Możesz chronić część dokumentu, który nie znajduje się w kontrolce zawartości.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="protect-a-content-control"></a><a name="EditDeleteControl"></a>Ochrona kontrolki zawartości
 Można uniemożliwić użytkownikom edytowanie lub usuwanie kontrolki zawartości przez ustawienie właściwości kontrolki w projekcie na poziomie dokumentu w czasie projektowania lub w czasie wykonywania.

 Możesz również chronić kontrolki zawartości dodawane do dokumentu w czasie wykonywania przy użyciu projektu dodatku VSTO. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md).

### <a name="to-protect-a-content-control-at-design-time"></a>Aby chronić kontrolkę zawartości w czasie projektowania

1. W dokumencie, który jest hostowany w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektancie, wybierz kontrolkę zawartość, która ma być chroniona.

2. W oknie **Właściwości** Ustaw jedną lub obie następujące właściwości:

    - Aby uniemożliwić użytkownikom edytowanie kontrolki, ustaw **LockContents** na **true**.

    - Aby uniemożliwić użytkownikom usuwanie kontrolek, ustaw **LockContentControl** na **true**.

3. Kliknij przycisk **OK**.

### <a name="to-protect-a-content-control-at-run-time"></a>Aby chronić kontrolkę zawartości w czasie wykonywania

1. Ustaw `LockContents` Właściwość kontrolki zawartość na **wartość true** , aby uniemożliwić użytkownikom edytowanie kontrolki i ustawić `LockContentControl` Właściwość na **true** , aby uniemożliwić użytkownikom usuwanie kontrolek.

     Poniższy przykład kodu demonstruje użycie <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> właściwości i dwóch różnych <xref:Microsoft.Office.Tools.Word.RichTextContentControl> obiektów w projekcie na poziomie dokumentu. Aby uruchomić ten kod, Dodaj kod do `ThisDocument` klasy w projekcie i Wywołaj `AddProtectedContentControls` metodę z `ThisDocument_Startup` procedury obsługi zdarzeń.

     [!code-csharp[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#2)]

     Poniższy przykład kodu demonstruje użycie <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> właściwości i dwóch różnych <xref:Microsoft.Office.Tools.Word.RichTextContentControl> obiektów w projekcie dodatku VSTO. Aby uruchomić ten kod, Dodaj kod do `ThisAddIn` klasy w projekcie i Wywołaj `AddProtectedContentControls` metodę z `ThisAddIn_Startup` procedury obsługi zdarzeń.

     [!code-vb[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#14)]
     [!code-csharp[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#14)]

## <a name="protect-a-part-of-a-document-that-is-not-in-a-content-control"></a>Ochrona części dokumentu, która nie znajduje się w kontrolce zawartości
 Można uniemożliwić użytkownikom zmianę obszaru dokumentu przez umieszczenie obszaru w <xref:Microsoft.Office.Tools.Word.GroupContentControl> . Jest to przydatne w następujących scenariuszach:

- Chcesz chronić obszar, który nie zawiera formantów zawartości.

- Chcesz chronić obszar, który zawiera już kontrolki zawartości, ale tekst lub inne elementy, które mają być chronione, nie znajdują się w kontrolkach zawartości.

> [!NOTE]
> W przypadku utworzenia, <xref:Microsoft.Office.Tools.Word.GroupContentControl> który zawiera osadzone kontrolki zawartości, osadzone kontrolki zawartości nie są automatycznie chronione. Aby uniemożliwić użytkownikom edytowanie osadzonej kontrolki zawartości, należy użyć właściwości **LockContents** formantu.

### <a name="to-protect-an-area-of-a-document-at-design-time"></a>Aby chronić obszar dokumentu w czasie projektowania

1. W dokumencie, który jest hostowany w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektancie, wybierz obszar, który ma być chroniony.

2. Na wstążce kliknij kartę **deweloper** .

    > [!NOTE]
    > Jeśli karta **deweloper** nie jest widoczna, należy ją najpierw pokazać. Aby uzyskać więcej informacji, zobacz [jak: wyświetlić kartę Deweloper na Wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

3. W grupie **formanty** kliknij przycisk listy rozwijanej **Grupa** , a następnie kliknij pozycję **Grupa**.

     Element zawierający <xref:Microsoft.Office.Tools.Word.GroupContentControl> chroniony region jest generowany automatycznie w `ThisDocument` klasie w projekcie. Obramowanie reprezentujące formant grupy jest widoczne w czasie projektowania, ale nie ma żadnych widocznych obramowania w czasie wykonywania.

### <a name="to-protect-an-area-of-a-document-at-run-time"></a>Aby chronić obszar dokumentu w czasie wykonywania

1. Program programowo zaznacz obszar, który ma być chroniony, a następnie Wywołaj <xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A> metodę, aby utworzyć <xref:Microsoft.Office.Tools.Word.GroupContentControl> .

     Poniższy przykład kodu dla projektu na poziomie dokumentu dodaje tekst do pierwszego akapitu w dokumencie, wybiera pierwszy akapit, a następnie tworzy wystąpienie a <xref:Microsoft.Office.Tools.Word.GroupContentControl> . Aby uruchomić ten kod, Dodaj kod do `ThisDocument` klasy w projekcie i Wywołaj `ProtectFirstParagraph` metodę z `ThisDocument_Startup` procedury obsługi zdarzeń.

     [!code-csharp[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#1)]

     Poniższy przykład kodu dla projektu dodatku VSTO dodaje tekst do pierwszego akapitu w aktywnym dokumencie, wybiera pierwszy akapit, a następnie tworzy wystąpienie a <xref:Microsoft.Office.Tools.Word.GroupContentControl> . Aby uruchomić ten kod, Dodaj kod do `ThisAddIn` klasy w projekcie i Wywołaj `ProtectFirstParagraph` metodę z `ThisAddIn_Startup` procedury obsługi zdarzeń.

     [!code-vb[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#15)]
     [!code-csharp[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#15)]

## <a name="see-also"></a>Zobacz też
- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Kontrolki zawartości](../vsto/content-controls.md)
- [Instrukcje: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
