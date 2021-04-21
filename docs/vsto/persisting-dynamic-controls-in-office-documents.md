---
title: Utrwalanie kontrolek dynamicznych w dokumentach pakietu Office
description: Dowiedz się, jak dodać kod do rozwiązania w celu ponownego utworzenia trwałych kontrolek dynamicznych, gdy użytkownik otworzy ponownie zamknięty dokument.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9d42aa2d8594ed44e4fd4edbac8a0d64c4dc16da
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826151"
---
# <a name="persist-dynamic-controls-in-office-documents"></a>Utrwalanie kontrolek dynamicznych w dokumentach pakietu Office

Kontrolki dodawane w czasie uruchamiania nie są utrwalane, gdy dokument lub skoroszyt jest zapisywany i zamykany. Dokładne zachowanie jest inne w przypadku kontrolek hosta i Windows Forms kontroli. W obu przypadkach możesz dodać kod do rozwiązania, aby ponownie utworzyć kontrolki, gdy użytkownik otworzy ponownie dokument.

Kontrolki, które dodajesz do dokumentów w czasie uruchamiania, są nazywane *kontrolkami dynamicznymi*. Aby uzyskać więcej informacji na temat kontrolek dynamicznych, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie uruchamiania.](../vsto/adding-controls-to-office-documents-at-run-time.md)

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="persist-host-controls-in-the-document"></a>Utrwalanie kontrolek hosta w dokumencie

Po zapisaniu i zamknięciu dokumentu wszystkie dynamiczne kontrolki hosta są usuwane z dokumentu. Tylko podstawowe natywne obiekty pakietu Office pozostają w tyle. Na przykład <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> kontrolka hosta staje się kontrolką <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName> . Natywne obiekty pakietu Office nie są połączone ze zdarzeniami sterowania hosta i nie mają funkcji powiązania danych kontrolki hosta.

W poniższej tabeli wymieniono natywny obiekt pakietu Office, który pozostaje w dokumencie dla każdego typu kontrolki hosta.

|Typ kontrolki hosta|Natywny typ obiektu pakietu Office|
|-----------------------|-------------------------------|
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|

### <a name="re-create-dynamic-host-controls-when-documents-are-opened"></a>Ponowne tworzenie dynamicznych kontrolek hosta po otwarciu dokumentów

Możesz ponownie tworzyć dynamiczne kontrolki hosta w miejsce istniejących kontrolek natywnych za każdym razem, gdy użytkownik otworzy dokument. Tworzenie kontrolek hosta w ten sposób po otwarciu dokumentu symuluje środowisko, które użytkownicy mogą oczekiwać.

Aby ponownie utworzyć kontrolkę hosta dla programu Word lub kontrolkę hosta lub dla programu <xref:Microsoft.Office.Tools.Excel.NamedRange> <xref:Microsoft.Office.Tools.Excel.ListObject> Excel, `Add` \<*control class*> użyj metody obiektu <xref:Microsoft.Office.Tools.Excel.ControlCollection?displayProperty=fullName> lub <xref:Microsoft.Office.Tools.Word.ControlCollection?displayProperty=fullName> . Użyj metody, która ma parametr dla natywnego obiektu pakietu Office.

Jeśli na przykład chcesz utworzyć kontrolkę hosta z istniejącej natywnej kontrolki po otwarciu dokumentu, użyj metody i przekaż <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName> istniejący element <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> <xref:Microsoft.Office.Interop.Excel.ListObject> . Poniższy przykład kodu demonstruje to w projekcie na poziomie dokumentu dla programu Excel. Kod ponownie tworzy dynamiczną, <xref:Microsoft.Office.Tools.Excel.ListObject> która jest oparta na istniejącej nazwie w klasie <xref:Microsoft.Office.Interop.Excel.ListObject> `MyListObject` `Sheet1` .

:::code language="csharp" source="../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/Sheet1.cs" id="Snippet6":::
:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/Sheet1.vb" id="Snippet6":::

### <a name="re-create-chart"></a>Ponowne tworzenie wykresu

Aby ponownie utworzyć kontrolkę hosta, należy najpierw usunąć natywną kontrolkę , a następnie utworzyć ją ponownie <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName> przy użyciu metody <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> . Nie istnieje `Add` \<*control class*> metoda, która umożliwia utworzenie nowego na <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> podstawie istniejącego . <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName>

Jeśli nie usuniesz najpierw natywnego wykresu , podczas ponownego tworzenia utworzysz <xref:Microsoft.Office.Interop.Excel.Chart> drugi, zduplikowany <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> wykres.

## <a name="persist-windows-forms-controls-in-documents"></a>Utrwalanie Windows Forms danych w dokumentach

Gdy dokument jest zapisywany, a następnie zamykany, automatycznie usuwa z dokumentu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Windows Forms utworzone kontrolki. Jednak zachowanie jest inne w przypadku projektów na poziomie dokumentu i dodatków VSTO.

W dostosowaniach na poziomie dokumentu kontrolki i ich podstawowe otoki ActiveX (które są używane do hostować kontrolki w dokumencie) są usuwane przy następnym otwarciu dokumentu. Nie ma żadnego wskazania, że kontrolki były kiedykolwiek dostępne.

W dodatki VSTO formanty są usuwane, ale otoki ActiveX pozostają w dokumencie. Następnym razem, gdy użytkownik otworzy dokument, będą widoczne otoki ActiveX. W programie Excel otoki ActiveX wyświetlają obrazy kontrolek w momencie ich ostatniego zapisania. W programie Word otoki ActiveX są niewidoczne, chyba że użytkownik je kliknie. W takim przypadku jest wyświetlana linia kropkowana reprezentująca obramowanie kontrolek. Otoki ActiveX można usunąć na kilka sposobów. Aby uzyskać więcej informacji, zobacz [Usuwanie otok ActiveX w dodatku](#removingActiveX).

### <a name="re-create-windows-forms-controls-when-documents-are-opened"></a>Ponowne tworzenie kontrolek Windows Forms podczas otwarcia dokumentów

Możesz ponownie utworzyć usunięte kontrolki Windows Forms, gdy użytkownik otworzy ponownie dokument. W tym celu rozwiązanie musi wykonać następujące zadania:

1. Przechowuj informacje o rozmiarze, lokalizacji i stanie kontrolek w momencie zapisania lub zamknięcia dokumentu. W przypadku dostosowywania na poziomie dokumentu można zapisać dane w pamięci podręcznej danych w dokumencie. W dodatku VSTO można zapisać dane w niestandardowej części XML w dokumencie.

2. Utwórz ponownie kontrolki w zdarzeniu, które jest wywoływane po otwarciu dokumentu. W projektach na poziomie dokumentu można to zrobić w `Sheet` *n* `_Startup` lub `ThisDocument_Startup` procedurach obsługi zdarzeń. W projektach dodatków VSTO można to zrobić w procedurach obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> zdarzeń <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> lub .

### <a name="remove-activex-wrappers-in-an-add-in"></a><a name="removingActiveX"></a> Usuwanie otoek ActiveX w dodatku

Podczas dodawania dynamicznych kontrolek Windows Forms do dokumentów przy użyciu dodatku VSTO można zapobiec pojawianiu się otoek ActiveX dla kontrolek przy następnym otwarciu dokumentu w następujący sposób.

#### <a name="remove-activex-wrappers-when-the-document-is-opened"></a>Usuwanie otok ActiveX po otwarciu dokumentu

Aby usunąć wszystkie otoki ActiveX, wywołaj metodę , aby wygenerować element hosta dla elementu `GetVstoObject` <xref:Microsoft.Office.Interop.Word.Document> lub <xref:Microsoft.Office.Interop.Excel.Workbook> reprezentujący nowo otwarty dokument. Aby na przykład usunąć wszystkie otoki ActiveX z dokumentu programu Word, można wywołać metodę w celu wygenerowania elementu hosta dla obiektu przekazywanego do procedury obsługi `GetVstoObject` <xref:Microsoft.Office.Interop.Word.Document> zdarzeń dla <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> zdarzenia.

Ta procedura jest przydatna, gdy wiesz, że dokument zostanie otwarty tylko na komputerach z zainstalowanym dodatku VSTO. Jeśli dokument może zostać przekazany do innych użytkowników, którzy nie mają zainstalowanego dodatku VSTO, rozważ usunięcie kontrolek przed zamknięciem dokumentu.

Poniższy przykład kodu pokazuje, jak wywołać metodę `GetVstoObject` po otwarciu dokumentu.

:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet11":::
:::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet11":::

Mimo że metoda jest używana głównie do generowania nowego elementu hosta w czasie działania, ta metoda umożliwia również wyczyszczenie wszystkich otoek ActiveX z dokumentu przy pierwszym wywołaniu dla `GetVstoObject` określonego dokumentu. Aby uzyskać więcej informacji na temat używania metody , zobacz Extend `GetVstoObject` Word documents and Excel [workbooks in VSTO Add-ins at run time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)(Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie działania).

Jeśli dodatek VSTO tworzy dynamiczne kontrolki po otwarciu dokumentu, dodatek VSTO już wywoła metodę w ramach procesu tworzenia `GetVstoObject` kontrolek. Nie trzeba dodawać oddzielnego wywołania metody , aby usunąć otoki `GetVstoObject` ActiveX w tym scenariuszu.

#### <a name="remove-the-dynamic-controls-before-the-document-is-closed"></a>Usuwanie kontrolek dynamicznych przed zamknięciem dokumentu

Dodatek VSTO może jawnie usunąć każdą kontrolkę dynamiczną z dokumentu przed jego zamknięciem. Ta procedura jest przydatna w przypadku dokumentów, które mogą być przekazywane do innych użytkowników, którzy nie mają zainstalowanego dodatku VSTO.

Poniższy przykład kodu pokazuje, jak usunąć wszystkie kontrolki Windows Forms z dokumentu programu Word po zamknięciu dokumentu.

:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet10":::
:::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet10":::

## <a name="see-also"></a>Zobacz też

- [Dodawanie kontrolek do dokumentów pakietu Office w czasie rzeczywistym](../vsto/adding-controls-to-office-documents-at-run-time.md)
