---
title: Utrwalanie kontrolek dynamicznych w dokumentach pakietu Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Office documents [Office development in Visual Studio, host controls
- controls [Office development in Visual Studio], persisting in the document
- Windows Forms controls [Office development in Visual Studio], persisting in the document
- documents [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], persisting in the document
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8fd44d535cd8a9920ebc3de37d0c483a19dac8f8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117983"
---
# <a name="persist-dynamic-controls-in-office-documents"></a>Utrwalanie kontrolek dynamicznych w dokumentach pakietu Office

Formanty, które są dodawane w czasie wykonywania nie są zachowywane, gdy dokument lub skoroszyt zostanie zapisany i zamknięte. Dokładne zachowanie różni się dla formantów hosta i kontrolek formularzy Windows Forms. W obu przypadkach można dodać kod do rozwiązania, aby ponownie utworzyć kontrolki, gdy użytkownik ponownie otwiera dokument.

Formanty, które dodają do dokumentów w czasie wykonywania są nazywane *kontrolek dynamicznych*. Aby uzyskać więcej informacji na temat kontrolek dynamicznych, zobacz [dodawanie formantów do dokumentów pakietu Office w środowisku uruchomieniowym](../vsto/adding-controls-to-office-documents-at-run-time.md).

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="persist-host-controls-in-the-document"></a>Utrwalanie kontrolki hosta w dokumencie

Po zapisaniu dokumentu i następnie zamknięte, wszystkie formanty hosta dynamicznego zostaną usunięte z dokumentu. Tylko podstawowy natywnych obiektów pakietu Office pozostają za zaporą. Na przykład <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> staje się kontrolki hosta <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName>. Natywnych obiektów pakietu Office nie są podłączone do zdarzenia kontrolki hosta, a nie mają funkcji powiązanie danych kontrolki hosta.

W poniższej tabeli wymieniono natywnego obiektu pakietu Office, który jest pozostawione w dokumencie dla każdego typu kontrolki hosta.

|Typ kontrolki hosta|Natywne typ obiektów pakietu Office|
|-----------------------|-------------------------------|
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|

### <a name="re-create-dynamic-host-controls-when-documents-are-opened"></a>Ponownie utworzyć formanty hosta dynamicznego, gdy są otwarte dokumenty

Za każdym razem, gdy użytkownik otwiera dokument, można ponownie utworzyć formanty hosta dynamicznego zamiast istniejącej kontrolki natywne. Tworzenie kontrolki hosta w ten sposób, po otwarciu dokumentu symuluje środowisko, które użytkownicy mogą oczekiwać.

Aby ponownie utworzyć kontrolki hosta programu Word, lub <xref:Microsoft.Office.Tools.Excel.NamedRange> lub <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki hosta dla programu Excel, użyj `Add` \< *kontrolować klasy*> metody <xref:Microsoft.Office.Tools.Excel.ControlCollection?displayProperty=fullName> lub <xref:Microsoft.Office.Tools.Word.ControlCollection?displayProperty=fullName> obiektu. Metoda, która ma parametr dla natywnych obiektów pakietu Office.

Na przykład, jeśli chcesz utworzyć <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> kontrolki z istniejących natywnych hosta <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName> po otwarciu dokumentu, użyj <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> metody i przekazać w istniejącym <xref:Microsoft.Office.Interop.Excel.ListObject>. W poniższym przykładzie kodu pokazano to w projekcie na poziomie dokumentu dla programu Excel. Ponownie tworzy dynamiczny kod <xref:Microsoft.Office.Tools.Excel.ListObject> opartego na istniejącej <xref:Microsoft.Office.Interop.Excel.ListObject> o nazwie `MyListObject` w `Sheet1` klasy.

[!code-csharp[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/Sheet1.cs#6)]
[!code-vb[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/Sheet1.vb#6)]

### <a name="re-create-chart"></a>Ponowne tworzenie wykresu

Ponownie utworzyć <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> kontrolki, hosta należy najpierw usunąć natywnych <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName>i ponownie utwórz <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> przy użyciu <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> metody. Istnieje nie `Add` \< *kontrolować klasy*> metodę, która umożliwia utworzenie nowego <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> oparty na istniejącym <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName>.

Jeśli nie usuwaj najpierw natywnych <xref:Microsoft.Office.Interop.Excel.Chart>, a następnie utworzysz wykres drugi, zduplikowany, po ponownym utworzeniu <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName>.

## <a name="persist-windows-forms-controls-in-documents"></a>Utrwalanie formantów Windows Forms w dokumentach

Po zapisaniu dokumentu i następnie zamknięty [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] automatycznie usuwa wszystkie kontrolki Windows Forms utworzony dynamicznie z dokumentu. Jednak to zachowanie różni się na poziomie dokumentu i projektów dodatku VSTO.

W dostosowaniach na poziomie dokumentu kontrolki i ich podstawowej otoki ActiveX, (które są używane do hostowania kontrolki do dokumentu) są usuwane przy następnym otwarciu dokumentu. Nie ma żadnego wskazania, że formanty były nigdy nie istnieje.

W dodatków narzędzi VSTO dla programów formanty są usuwane, ale otoki ActiveX pozostają w dokumencie. Przy następnym otwarciu dokumentu, otoki ActiveX są widoczne. W programie Excel otoki ActiveX wyświetlanie obrazów formantów, postaci aktualnej podczas ostatniego dokument został zapisany. W programie Word otoki ActiveX są niewidoczne, chyba że użytkownik kliknie na nich, w tym przypadku są wyświetlane linia kropkowana, który reprezentuje obramowania kontrolki. Istnieje kilka sposobów, możesz usunąć otoki ActiveX. Aby uzyskać więcej informacji, zobacz [Usuń otoki ActiveX w dodatku](#removingActiveX).

### <a name="re-create-windows-forms-controls-when-documents-are-opened"></a>Utwórz ponownie kontrolek formularzy Windows Forms, gdy są otwarte dokumenty

Możesz je ponownie utworzyć usuniętego kontrolek Windows Forms po użytkownik ponownie otwiera dokument. Aby to zrobić, rozwiązanie musi wykonać następujące zadania:

1. Store informacji na temat rozmiaru, lokalizacja i stan kontrolki, gdy dokument zostanie zapisany lub zamknięte. W dostosowaniu na poziomie dokumentu można zapisać danych do pamięci podręcznej danych w dokumencie. W dodatku narzędzi VSTO dla programów można zapisać danych z niestandardowym elementem XML w dokumencie.

2. Utwórz ponownie kontrolek w zdarzenie, które jest wywoływane, gdy dokument jest otwarty. W projektach na poziomie dokumentu, można to zrobić `Sheet` *n* `_Startup` lub `ThisDocument_Startup` procedury obsługi zdarzeń. W projektach dodatku narzędzi VSTO można zrobić w przypadku tym programy obsługi dla <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> lub <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> zdarzenia.

### <a name="removingActiveX"></a> Usuń otoki ActiveX w dodatku

Po dodaniu dynamiczne kontrolek Windows Forms do dokumentów za pomocą dodatku narzędzi VSTO uniemożliwia otoki ActiveX dla formantów znajdujących się w dokumencie następnym razem, gdy zostanie otwarta w następujący sposób.

#### <a name="remove-activex-wrappers-when-the-document-is-opened"></a>Po otwarciu dokumentu, Usuń otoki ActiveX

Aby usunąć wszystkie otoki ActiveX, należy wywołać `GetVstoObject` metodę w celu wygenerowania element hosta dla elementu <xref:Microsoft.Office.Interop.Word.Document> lub <xref:Microsoft.Office.Interop.Excel.Workbook> reprezentujący nowo otwartego dokumentu. Na przykład, aby usunąć wszystkie otoki ActiveX z dokumentu programu Word, należy wywołać `GetVstoObject` metodę w celu wygenerowania element hosta dla elementu <xref:Microsoft.Office.Interop.Word.Document> obiektu, który jest przekazywany do narzędzia obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> zdarzeń.

Ta procedura jest przydatna, gdy wiadomo, że dokument zostanie otwarty tylko na komputerach, które mają dodatku narzędzi VSTO zainstalowane. Jeśli dokument mogą być przekazywane do innych użytkowników, którzy nie mają dodatku narzędzi VSTO zainstalowane, rozważ usunięcie kontrolki przed zamknięciem zamiast tego dokumentu.

Poniższy przykład kodu pokazuje sposób wywołania `GetVstoObject` metody, gdy dokument jest otwarty.

[!code-vb[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#11)]
[!code-csharp[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#11)]

Mimo że `GetVstoObject` metoda jest używana głównie w celu wygenerowania nowego elementu hosta w czasie wykonywania, ta metoda także czyści wszystkie otoki ActiveX z dokumentu jest wywoływana dla określonego dokumentu po raz pierwszy. Aby uzyskać więcej informacji o sposobie używania `GetVstoObject` metody, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

Jeśli dodatku narzędzi VSTO dla programów tworzy kontrolek dynamicznych, po otwarciu dokumentu, dodatku narzędzi VSTO dla programów już wywoła `GetVstoObject` metodę jako część procesu tworzenia kontrolki. Nie musisz dodać wywołanie oddzielnych `GetVstoObject` metodę, aby usunąć otoki ActiveX w tym scenariuszu.

#### <a name="remove-the-dynamic-controls-before-the-document-is-closed"></a>Usuwanie kontrolek dynamicznych, przed zamknięciem dokumentu

Dodatek narzędzi VSTO dla programu jawnie usunąć każdy dynamicznej kontroli z dokumentu przed zamknięciem dokumentu. Ta procedura jest przydatne w przypadku dokumentów, które mogą być przekazywane do innych użytkowników, którzy nie mają dodatku narzędzi VSTO zainstalowane.

Poniższy przykład kodu demonstruje sposób usunięcia wszystkich kontrolek Windows Forms z dokumentu programu Word, gdy dokument zostanie zamknięty.

[!code-vb[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#10)]
[!code-csharp[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#10)]

## <a name="see-also"></a>Zobacz także

- [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
