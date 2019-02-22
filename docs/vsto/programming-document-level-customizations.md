---
title: Program dostosowań na poziomie dokumentu
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- Sheet3
- thisWorkbook
- thisDocument
- Sheet1
- Sheet2
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument class
- Sheet3 class
- ThisWorkbook class
- writing code for Office solutions
- programming [Office development in Visual Studio], document-level customizations
- Sheet1 class
- Office applications [Office development in Visual Studio], document-level customizations
- Sheet2 class
- document-level customizations [Office development in Visual Studio], programming
- application development [Office development in Visual Studio], document-level customizations
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0815ccf781782a0d638fcf941a6e48edcf8ccd1f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56624688"
---
# <a name="program-document-level-customizations"></a>Program dostosowań na poziomie dokumentu
  Rozszerzając program Microsoft Office Word lub Microsoft Office Excel za pomocą dostosowania poziomu dokumentu, należy wykonać następujące zadania:

- Automatyzacja aplikacji za pomocą jego modelu obiektów.

- Dodawanie formantów do powierzchni dokumentu.

- Wywoływanie języka Visual Basic for Applications (VBA) kod w dokumencie z zestaw dostosowania.

- Wywołaj kod w zestawie dostosowywania z języka VBA.

- Zarządzania niektórymi aspektami dokumentu, gdy znajduje się na serwerze, na którym nie ma zainstalowany w Microsoft Office.

- Dostosowywanie interfejsu użytkownika (UI) aplikacji.

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

  Niektóre aspekty pisanie kodu w projektach na poziomie dokumentu różnią się od innych typów projektów w programie Visual Studio. Wiele z tych różnic jest spowodowana przez sposób Office modele obiektów są widoczne dla kodu zarządzanego. Aby uzyskać więcej informacji, zobacz [pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md).

  Aby uzyskać ogólne informacje dotyczące dostosowywania poziomie dokumentu i innych typów rozwiązań, można utworzyć za pomocą narzędzi programistycznych pakietu Office w programie Visual Studio, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="use-the-generated-classes-in-document-level-projects"></a>Użyj wygenerowanych klas w projektach na poziomie dokumentu
 Podczas tworzenia projektów dokumentów programu Visual Studio automatycznie generuje klasę w projekcie, który służy do rozpoczęcia pisania kodu. Program Visual Studio generuje różnych klas dla programów Word i Excel:

- W projektach na poziomie dokumentu dla programu Word, nosi nazwę klasy `ThisDocument` domyślnie.

- Projektów na poziomie dokumentu dla programu Excel ma wiele wygenerowanych klas: jeden dla samego skoroszytu i jeden dla każdego arkusza. Domyślnie tych klas mają następujące nazwy:

  -   `ThisWorkbook`

  -   `Sheet1`

  -   `Sheet2`

  -   `Sheet3`

  Wygenerowana klasa zawiera procedury obsługi zdarzeń, które są wywoływane, gdy otwarcie lub zamknięcie dokumentu. Aby uruchomić kod po otwarciu dokumentu, Dodaj kod, aby `Startup` programu obsługi zdarzeń. Aby uruchomić kod zaraz przed zamknięciem dokumentu, Dodaj kod, aby `Shutdown` programu obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

### <a name="understand-the-design-of-the-generated-classes"></a>Omówienie konstrukcji wygenerowanych klas
 W przypadku projektów, których platformą docelową [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], typów elementów hosta w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] są interfejsy, więc wygenerowanych klas nie może pochodzić z ich implementacji, które z nich. Wygenerowane klasy pochodzi większość swoich członków z następujących klas bazowych:

- `ThisDocument`: pochodzi z <xref:Microsoft.Office.Tools.Word.DocumentBase>.

- `ThisWorkbook`: pochodzi z <xref:Microsoft.Office.Tools.Excel.WorkbookBase>.

- `Sheet` *n*: pochodzi z <xref:Microsoft.Office.Tools.Excel.WorksheetBase>.

  Tych klas bazowych przekierować wszystkie wywołania do ich elementów członkowskich do wewnętrznych implementacji odpowiednich interfejsów elementu hosta w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Na przykład, jeśli wywołasz <xref:Microsoft.Office.Tools.Word.DocumentBase.Protect%2A> metody `ThisDocument` klasy <xref:Microsoft.Office.Tools.Word.DocumentBase> klasy przekierowuje to wywołanie wewnętrzną implementację <xref:Microsoft.Office.Tools.Word.Document> interfejsu w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

## <a name="access-the-object-model-of-the-host-application"></a>Dostęp do modelu obiektów w aplikacji hosta
 Aby uzyskać dostęp do modelu obiektów w aplikacji hosta, należy używać elementów członkowskich wygenerowanej klasy w projekcie. Każda z tych klas odnosi się do obiektu w modelu obiektów programu Excel lub Word i zawierają większość tych samych właściwości, metod i zdarzeń. Na przykład `ThisDocument` klasy w projekcie na poziomie dokumentu dla programu Word zawiera większość tych samych elementów członkowskich jako <xref:Microsoft.Office.Interop.Word.Document> obiektu w modelu obiektów programu Word.

 Poniższy przykład kodu pokazuje, jak zapisać dokument, który jest częścią dostosowywania poziomie dokumentu dla programu Word za pomocą modelu obiektów programu Word. W tym przykładzie jest przeznaczona do uruchamiania z `ThisDocument` klasy.

```vb
Me.Save()
```

```csharp
this.Save();
```

 Aby zrobić to samo z poza `ThisDocument` klasy, należy użyć `Globals` do dostępu do obiektu `ThisDocument` klasy. Na przykład możesz można dodać ten kod do pliku kodu w okienku Akcje, jeśli chcesz dołączyć **Zapisz** przycisku w okienku Akcje interfejsu użytkownika.

```vb
Globals.ThisDocument.Save()
```

```csharp
Globals.ThisDocument.Save();
```

 Ponieważ `ThisDocument` klasy uzyskuje większość składowe <xref:Microsoft.Office.Tools.Word.Document> element hosta `Save` to metoda, która jest wywoływana w tym kodzie, naprawdę <xref:Microsoft.Office.Tools.Word.Document.Save%2A> metody <xref:Microsoft.Office.Tools.Word.Document> element hosta. Ta metoda odnosi się do <xref:Microsoft.Office.Interop.Word._Document.Save%2A> metody <xref:Microsoft.Office.Interop.Word.Document> obiektu w modelu obiektów programu Word.

 Aby uzyskać więcej informacji o korzystaniu z modeli obiektów programu Word i Excel, zobacz [model obiektu Word — omówienie](../vsto/word-object-model-overview.md) i [model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md).

 Aby uzyskać więcej informacji na temat `Globals` obiektu, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).

## <a name="add-controls-to-documents"></a>Dodawanie formantów do dokumentów
 Aby dostosować interfejs użytkownika dokumentu, można dodać kontrolek formularzy Windows Forms lub *hostowania kontrolek* do powierzchni dokumentu. Łączenie różnych zestawów kontrolek i napisanie kodu, można powiązać formanty z danymi, zbiera informacje o użytkowniku i reagować na działania użytkownika.

 Formanty hosta to klasy, które rozszerzają niektóre obiekty w modelu obiektów programu Word i Excel. Na przykład <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki hosta zawiera wszystkie funkcje <xref:Microsoft.Office.Interop.Excel.ListObject> w programie Excel. Jednak <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki hosta ma również dodatkowe zdarzenia i możliwości wiązania danych.

 Aby uzyskać więcej informacji, zobacz [elementów, a omówienie kontrolek](../vsto/host-items-and-host-controls-overview.md) i [Windows forms, formanty na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

## <a name="combine-vba-and-document-level-customizations"></a>Łączenie VBA i dostosowywanie na poziomie dokumentu
 Za pomocą kodu z VBA w dokumencie, który jest częścią dostosowywania poziomie dokumentu. Możesz wywołać kod VBA w dokumencie z zestaw dostosowania, a można również skonfigurować projektu w celu włączenia kodu z VBA w dokumencie w celu wywołania kodu w zestaw dostosowania.

 Aby uzyskać więcej informacji, zobacz [łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md).

## <a name="manage-documents-on-a-server"></a>Zarządzanie dokumentami na serwerze
 Możesz zarządzać kilka różnych aspektów dostosowywania poziomie dokumentu na serwerze, który nie ma programu Microsoft Office Word lub zainstalowany program Microsoft Office Excel. Na przykład możesz uzyskać dostęp i modyfikować dane w pamięci podręcznej danych dokumentu. Można również zarządzać zestaw dostosowania, który jest skojarzony z dokumentem. Na przykład można programowo usunąć zestaw z dokumentu, aby dokument nie jest już uruchamia kod lub zestawu programowo można dołączyć do dokumentu.

 Aby uzyskać więcej informacji, zobacz [Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Dostosowywanie interfejsu użytkownika aplikacji pakietu Microsoft Office
 Za pomocą dostosowania poziomu dokumentu, można dostosować interfejsu użytkownika programu Word i Excel w następujący sposób:

- Dodaj formanty hosta i kontrolek formularzy Windows Forms do powierzchni dokumentu.

   Aby uzyskać więcej informacji, zobacz [automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md), [automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md), i [kontrolek formularzy Windows w dokumentach pakietu Office ― omówienie](../vsto/windows-forms-controls-on-office-documents-overview.md).

- Dodawanie okienek akcji do dokumentu.

   Aby uzyskać więcej informacji, zobacz [okienko akcji ― omówienie](../vsto/actions-pane-overview.md).

- Dodaj niestandardowe karty do wstążki.

   Aby uzyskać więcej informacji, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md).

- Dodaj niestandardowe grupy do wbudowanej karty na Wstążce.

   Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md).

  Aby uzyskać więcej informacji na temat dostosowywania aplikacji interfejsu użytkownika pakietu Microsoft Office, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

## <a name="get-extended-objects-from-native-office-objects-in-document-level-customizations"></a>Uzyskiwanie rozszerzonych obiektów natywnych obiektów pakietu Office w dostosowaniach na poziomie dokumentu
 Wiele programów obsługi zdarzeń dla zdarzeń Office otrzymują natywnych obiekt pakietu Office, która reprezentuje skoroszyt, arkusza lub dokument, który spowodował zdarzenie. W niektórych przypadkach warto uruchomienie kodu, tylko wtedy, gdy skoroszyt lub dokumentu w dostosowaniu na poziomie dokumentu spowodował zdarzenie. Na przykład w dostosowaniu na poziomie dokumentu dla programu Excel, możesz chcieć uruchomienie kodu, gdy użytkownik aktywuje jednego z arkuszy w skoroszycie dostosowany, ale nie w przypadku, gdy użytkownik aktywuje arkusza w inny skoroszyt, który ma miejsce otwarte w tym samym czasie.

 W przypadku natywnych obiektów pakietu Office, możesz sprawdzić, czy ten obiekt został rozszerzony do *element hosta* lub *kontrolki hosta* w dostosowaniu na poziomie dokumentu. Obiekty hosta i kontrolek hosta są typów dostarczonych przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] dodaje funkcjonalność do obiektów, które istnieją w sposób natywny w modele obiektów programu Word lub Excel (o nazwie *natywnych obiektów pakietu Office*). Zbiorczo elementów hosta i kontrolek hosta są również nazywane *obiektów rozszerzonych*. Aby uzyskać więcej informacji na temat elementów hosta i kontrolek hosta, zobacz [elementów, a omówienie kontrolek](../vsto/host-items-and-host-controls-overview.md).

## <a name="understand-the-getvstoobject-and-hasvstoobject-methods"></a>Poznasz GetVstoObject i hasvstoobject — metody
 Aby przetestować natywnych obiektów pakietu Office, należy użyć `HasVstoObject` i `GetVstoObject` metody w projekcie:

- Użyj `HasVstoObject` metody, aby określić, czy natywnych obiektów pakietu Office ma rozszerzone obiektu w dostosowaniu. Ta metoda zwraca wartość **true** Jeśli obiekt rozszerzonej natywnych obiektów pakietu Office i **false** inaczej.

- Użyj `GetVstoObject` metody, aby uzyskać obiekt rozszerzone dla natywnych obiektów pakietu Office. Ta metoda zwraca <xref:Microsoft.Office.Tools.Excel.ListObject>, <xref:Microsoft.Office.Tools.Excel.Workbook>, <xref:Microsoft.Office.Tools.Excel.Worksheet>, lub <xref:Microsoft.Office.Tools.Word.Document> obiektu, jeśli określony obiekt natywny Office ma jeden. W przeciwnym razie `GetVstoObject` zwraca **null**. Na przykład `GetVstoObject` metoda zwraca <xref:Microsoft.Office.Tools.Word.Document> Jeśli określony <xref:Microsoft.Office.Interop.Word.Document> jest obiekt źródłowy dla dokumentu w projekcie dokumentu programu Word.

  W projektach na poziomie dokumentu, nie można użyć `GetVstoObject` metodę, aby utworzyć nową <xref:Microsoft.Office.Tools.Excel.Workbook>, <xref:Microsoft.Office.Tools.Excel.Worksheet>, lub <xref:Microsoft.Office.Tools.Word.Document> element hosta w czasie wykonywania. Ta metoda służy tylko do dostępu do istniejących elementów hosta, które są generowane w projekcie w czasie projektowania. Jeśli chcesz utworzyć nowych elementów hosta w czasie wykonywania, należy opracować projekt dodatku narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md) i [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="use-the-getvstoobject-and-hasvstoobject-methods"></a>Użyj metody GetVstoObject i HasVstoObject
 Aby wywołać `HasVstoObject` i `GetVstoObject` metody, użyj `Globals.Factory.GetVstoObject` lub `Globals.Factory.HasVstoObject` metody i przekaż natywnych obiektów programu Word lub Excel (takich jak <xref:Microsoft.Office.Interop.Word.Document> lub <xref:Microsoft.Office.Interop.Excel.Worksheet>), którą chcesz przetestować.

## <a name="see-also"></a>Zobacz także
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md)
- [Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
