---
title: 'Instrukcje: Ochrona części dokumentów za pomocą formantów zawartości'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 25b30db78706dce95188289187ce55011ce1362d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441739"
---
# <a name="how-to-protect-parts-of-documents-by-using-content-controls"></a>Instrukcje: Ochrona części dokumentów za pomocą formantów zawartości
  W przypadku ochrony części dokumentu, można uniemożliwić użytkownikom zmienianie lub usuwanie zawartości w tej części dokumentu. Istnieje kilka sposobów, w części dokumentu Microsoft Word pakietu Office można chronić za pomocą formantów zawartości:

- Można chronić zawartość formantu.

- Możesz chronić część dokumentu, który nie znajduje się w zawartości formantu.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="EditDeleteControl"></a> Ochrona zawartości kontrolki
 Można uniemożliwić użytkownikom edytowanie lub usuwanie zawartości formantu przez ustawienie właściwości formantu w projekcie na poziomie dokumentu, w czasie projektowania lub w czasie wykonywania.

 Umożliwia również ochronę formanty zawartości, które dodajesz do dokumentu w czasie wykonywania za pomocą projektu dodatku narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md).

### <a name="to-protect-a-content-control-at-design-time"></a>Aby chronić zawartość formantu w czasie projektowania

1. W dokumencie, który znajduje się w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektancie zaznacz formant zawartości, który chcesz chronić.

2. W **właściwości** okna, ustawić jedną lub obie następujące właściwości:

    - Aby uniemożliwić użytkownikom edytowanie kontrolki, należy ustawić **LockContents** do **True**.

    - Aby zapobiec usunięciu formantu użytkowników, należy ustawić **LockContentControl** do **True**.

3. Kliknij przycisk **OK**.

### <a name="to-protect-a-content-control-at-runtime"></a>Aby chronić zawartość formantu w czasie wykonywania

1. Ustaw `LockContents` właściwości formantu zawartości do **true** aby uniemożliwić użytkownikom edytowanie kontrolkę i ustawić `LockContentControl` właściwości **true** aby uniemożliwić użytkownikom usunięcie formantu.

     Poniższy przykład kodu demonstruje sposób użycia <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> i <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> dwa różne właściwości <xref:Microsoft.Office.Tools.Word.RichTextContentControl> obiektów w projekcie na poziomie dokumentu. Aby uruchomić ten kod, Dodaj kod, aby `ThisDocument` klasy w projekcie i Wywołaj `AddProtectedContentControls` metody z `ThisDocument_Startup` programu obsługi zdarzeń.

     [!code-csharp[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#2)]

     Poniższy przykład kodu demonstruje sposób użycia <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> i <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> dwa różne właściwości <xref:Microsoft.Office.Tools.Word.RichTextContentControl> obiektów w projekcie dodatku narzędzi VSTO. Aby uruchomić ten kod, Dodaj kod, aby `ThisAddIn` klasy w projekcie i Wywołaj `AddProtectedContentControls` metody z `ThisAddIn_Startup` programu obsługi zdarzeń.

     [!code-vb[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#14)]
     [!code-csharp[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#14)]

## <a name="protect-a-part-of-a-document-that-is-not-in-a-content-control"></a>Ochrona części dokumentu, który nie znajduje się w kontrolkę zawartości
 Można uniemożliwić użytkownikom możliwość zmieniania obszar dokumentu przez umieszczenie obszaru w <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Jest to przydatne w następujących scenariuszach:

- Chcesz chronić obszar, który nie zawiera formanty zawartości.

- Chcesz chronić obszar, który zawiera już formanty zawartości, ale tekst lub inne elementy, które mają być chronione nie znajdują się w zawartości kontrolki.

> [!NOTE]
> Jeśli tworzysz <xref:Microsoft.Office.Tools.Word.GroupContentControl> zawierającą osadzone formanty zawartości, embedded formanty zawartości nie są automatycznie chronione. Aby uniemożliwić użytkownikom edytowanie osadzonego formantu zawartości, należy użyć **LockContents** właściwości formantu.

### <a name="to-protect-an-area-of-a-document-at-design-time"></a>Aby chronić obszar dokumentu w czasie projektowania

1. W dokumencie, który znajduje się w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektanta, wybierz obszar, który chcesz chronić.

2. Na wstążce kliknij **Developer** kartę.

    > [!NOTE]
    > Jeśli **Developer** karta nie jest widoczna, najpierw musisz wyświetlić. Aby uzyskać więcej informacji, zobacz [jak: Pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

3. W **kontrolki** grupy, kliknij przycisk **grupy** przycisk listy rozwijanej, a następnie kliknij **grupy**.

     A <xref:Microsoft.Office.Tools.Word.GroupContentControl> zawierający chronione regionów jest automatycznie generowany w `ThisDocument` klasy w projekcie. Obramowanie reprezentujący kontrolkę grupa jest widoczna w czasie projektowania, ale nie będzie widoczne obramowania w czasie wykonywania.

### <a name="to-protect-an-area-of-a-document-at-runtime"></a>Aby chronić obszar dokumentu w czasie wykonywania

1. Programowe Zaznaczanie obszaru, który chcesz chronić, a następnie wywołaj <xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A> metodę w celu utworzenia <xref:Microsoft.Office.Tools.Word.GroupContentControl>.

     Poniższy przykład kodu dla projektów dokumentów dodaje tekstu do pierwszego akapitu w dokumencie, wybierze opcję pierwszego akapitu, a następnie tworzy wystąpienie <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Aby uruchomić ten kod, Dodaj kod, aby `ThisDocument` klasy w projekcie i Wywołaj `ProtectFirstParagraph` metody z `ThisDocument_Startup` programu obsługi zdarzeń.

     [!code-csharp[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#1)]

     Poniższy przykład kodu w projekcie dodatku narzędzi VSTO dodaje tekst do pierwszego akapitu w aktywnym dokumencie wybierze opcję pierwszego akapitu, a następnie tworzy wystąpienie <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Aby uruchomić ten kod, Dodaj kod, aby `ThisAddIn` klasy w projekcie i Wywołaj `ProtectFirstParagraph` metody z `ThisAddIn_Startup` programu obsługi zdarzeń.

     [!code-vb[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#15)]
     [!code-csharp[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#15)]

## <a name="see-also"></a>Zobacz także
- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Formanty zawartości](../vsto/content-controls.md)
- [Instrukcje: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
