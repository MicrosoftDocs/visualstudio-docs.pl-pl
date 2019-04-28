---
title: Zaktualizuj projekty programu Excel i Word, są migrowane do programu .NET Framework 4 lub .NET Framework 4.5
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fd80f4a72151fdebb3f0445024963a65db981e63
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436477"
---
# <a name="update-excel-and-word-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Zaktualizuj projekty programu Excel i Word, są migrowane do programu .NET Framework 4 lub .NET Framework 4.5
  Jeśli masz projekt programu Excel lub Word, który wykorzystuje dowolne z następujących funkcji, należy zmodyfikować kod zmiana platformy docelowej na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej:

- [GetVstoObject i hasvstoobject — metody](#GetVstoObject)

- [Wygenerowanych klas w projektach na poziomie dokumentu](#generatedclasses)

- [Formanty Windows Forms w dokumentach](#winforms)

- [Zdarzenia kontrolki zawartości programu Word](#ccevents)

- [Klasy OLEObject i OLEControl](#ole)

- [Właściwość Controls.Item(Object)](#itemproperty)

- [Kolekcje, które wynikają z CollectionBase](#collections)

  Musisz również usunąć `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` i odwołuje się do `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` klas w projektach programu Excel, które są ukierunkowany na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej. Program Visual Studio nie powoduje usunięcia tego atrybutu lub odwołania do klasy dla Ciebie.

## <a name="remove-the-excellocale1033-attribute-from-excel-projects"></a>Usuń atrybut ExcelLocale1033 z projektów programu Excel
 `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` Została usunięta z części programu Visual Studio 2010 Tools dla pakietu Office runtime, używany do rozwiązania, których platformą docelową [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej. Środowisko uruchomieniowe języka wspólnego (CLR) w [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] i później zawsze przekazuje ustawienia regionalne 1033 identyfikator modelu obiektów programu Excel, a nie będzie można użyć tego atrybutu Aby wyłączyć to zachowanie. Aby uzyskać więcej informacji, zobacz [globalizacja i lokalizacja rozwiązania programu Excel](../vsto/globalization-and-localization-of-excel-solutions.md).

### <a name="to-remove-the-excellocale1033attribute"></a>Aby usunąć ExcelLocale1033Attribute

1. Otwarty projekt w programie Visual Studio, otwórz **Eksploratora rozwiązań**.

2. W obszarze **właściwości** węzeł (C#) lub **mój projekt** węzeł (Visual Basic), kliknij dwukrotnie plik kodu AssemblyInfo, aby otworzyć go w edytorze kodu.

    > [!NOTE]
    > W projektach języka Visual Basic, należy kliknąć przycisk **Pokaż wszystkie pliki** znajdujący się w **Eksploratora rozwiązań** aby zobaczyć plik kodu AssemblyInfo.

3. Znajdź `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` i usuń go z pliku lub komentarz dotyczący działanie.

    ```vb
    <Assembly: ExcelLocale1033Proxy(True)>
    ```

    ```csharp
    [assembly: ExcelLocale1033Proxy(true)]
    ```

## <a name="remove-a-reference-to-the-excellocal1033proxy-class"></a>Usuń odwołanie do klasy ExcelLocal1033Proxy
 Projekty, które zostały utworzone przy użyciu programu Microsoft Visual Studio 2005 Tools dla pakietu Microsoft Office System wystąpienia programu Excel <xref:Microsoft.Office.Interop.Excel.Application> obiektu za pomocą `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` klasy. Ta klasa została usunięta z części programu Visual Studio 2010 Tools dla pakietu Office runtime, która została użyta w przypadku rozwiązań przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej. W związku z tym należy usunąć lub przekształcić w komentarz wiersz kodu, który odwołuje się do tej klasy.

### <a name="to-remove-the-reference-to-the-excellocal1033proxy-class"></a>Aby usunąć odwołanie do klasy ExcelLocal1033Proxy

1. Otwórz projekt w programie Visual Studio, a następnie otwórz **Eksploratora rozwiązań**.

2. W **Eksploratora rozwiązań**, otwórz menu skrótów dla *ThisAddin.cs* (dla C#) lub *ThisAddin.vb* (w języku Visual Basic), a następnie wybierz **Wyświetl kod** .

3. W edytorze kodu w `VSTO generated code` regionu, usuń lub komentarz następujący wiersz kodu.

    ```vb
    Me.Application = CType(Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(GetType(Excel.Application), Me.Application), Excel.Application)

    ```

    ```csharp
    this.Application = (Excel.Application)Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(typeof(Excel.Application), this.Application);

    ```

## <a name="GetVstoObject"></a> Zaktualizuj kod, który używa metody GetVstoObject i HasVstoObject
 W projektach przeznaczonych dla platformy .NET Framework 3.5 `GetVstoObject` lub `HasVstoObject` metody są dostępne jako metody rozszerzenia dla jednej z następujących obiektów natywnych w projekcie: <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>, lub <xref:Microsoft.Office.Interop.Excel.ListObject>. Kiedy te metody, nie musisz przekazać parametr. Poniższy przykład kodu demonstruje sposób użycia metody GetVstoObject w dodatku narzędzi VSTO programu Word, który jest przeznaczony dla .NET Framework 3.5.

```vb
Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject()
```

```csharp
Microsoft.Office.Tools.Word.Document vstoDocument =
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject();
```

 W przypadku projektów, których platformą docelową [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej, należy zmodyfikować swój kod, aby uzyskać dostęp do tych metod w jedną z następujących sposobów:

- Możesz uzyskiwać dostęp tych metod jako metody rozszerzenia, na <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>, lub <xref:Microsoft.Office.Interop.Excel.ListObject> obiektów. Jednak teraz należy przekazać obiekt zwrócony przez `Globals.Factory` właściwości tych metod.

  ```vb
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory)
  ```

  ```csharp
  Microsoft.Office.Tools.Word.Document vstoDocument =
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory);
  ```

- Alternatywnie dostęp do tych metod w obiekcie, który jest zwracany przez `Globals.Factory` właściwości. Gdy uzyskujesz dostęp do tych metod w ten sposób, należy przekazać natywnego obiektu, który ma zostać rozszerzony do metody.

  ```vb
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument)
  ```

  ```csharp
  Microsoft.Office.Tools.Word.Document vstoDocument =
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument);
  ```

  Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="generatedclasses"></a> Zaktualizuj kod, który używa wystąpienia wygenerowanych klas w projektach na poziomie dokumentu
 W przypadku projektów na poziomie dokumentu przeznaczonych dla programu .NET Framework 3.5, wygenerowanych klas w projektach dziedziczyć następujące klasy w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]:

- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.Document>

- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.Workbook>

- `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.Worksheet>

- `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheet>

  W przypadku projektów, których platformą docelową [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym, typy w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wymienione powyżej są interfejsami zamiast klasami. Wygenerowany klasy w projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później pochodzić od następujących nowych klas w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]:

- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>

- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>

- `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.WorksheetBase>

- `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheetBase>

  Jeśli kod w projekcie odwołuje się do wystąpienia jednego z wygenerowanych klas jako klasę bazową, która pochodzi od klasy, należy zmodyfikować kod.

  Na przykład w projekcie skoroszyt programu Excel, który jest przeznaczony dla .NET Framework 3.5, Niewykluczone, że metody pomocnika, która wykonuje jakąś pracę na wystąpień wygenerowany `Sheet` *n* klasy w projekcie.

```vb
Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.Worksheet)
    ' Do something to the worksheet object.
End Sub
```

```csharp
private void DoSomethingToSheet(Microsoft.Office.Tools.Excel.Worksheet worksheet)
{
    // Do something to the worksheet object.
}
```

 Przekierowanie projektu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej, należy jeden z następujących zmian w kodzie:

- Zmodyfikować każdy kod, który wywołuje `DoSomethingToSheet` metodę, aby przekazać <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Base%2A> właściwość <xref:Microsoft.Office.Tools.Excel.WorksheetBase> obiektu w projekcie. Ta właściwość zwraca <xref:Microsoft.Office.Tools.Excel.Worksheet> obiektu.

    ```vb
    DoSomethingToSheet(Globals.Sheet1.Base)
    ```

    ```csharp
    DoSomethingToSheet(Globals.Sheet1.Base);
    ```

- Modyfikowanie `DoSomethingToSheet` parametru metody, można oczekiwać <xref:Microsoft.Office.Tools.Excel.WorksheetBase> zamiast tego obiektu.

    ```vb
    Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.WorksheetBase)
        ' Do something to the worksheet object.
    End Sub
    ```

    ```csharp
    private void DoSomethingToSheet (Microsoft.Office.Tools.Excel.WorksheetBase worksheet)
    {
        // Do something to the worksheet object.
    }
    ```

## <a name="winforms"></a> Aktualizowanie kodu, która używa formantów Windows Forms w dokumentach
 Należy dodać **przy użyciu** (C#) lub **Importy** — instrukcja (Visual Basic), dla <xref:Microsoft.Office.Tools.Excel> lub <xref:Microsoft.Office.Tools.Word> przestrzeni nazw na początku każdego pliku kodu, który używa właściwości formantów, aby dodawać Windows Tworzy kontrolki do dokumentu lub arkuszu programowo.

 W projektach przeznaczonych dla platformy .NET Framework 3.5, metody, które dodać kontrolek formularzy Windows Forms (takie jak `AddButton` metoda) są definiowane w <xref:Microsoft.Office.Tools.Excel.ControlCollection> i <xref:Microsoft.Office.Tools.Word.ControlCollection> klasy.

 W przypadku projektów, których platformą docelową [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, te metody są metody rozszerzenia, które są dostępne dla właściwości kontrolek. Aby korzystać z tych metod rozszerzenia, musi mieć plik kodu, w którym możesz użyć metody **przy użyciu** lub **Importy** poufności informacji dotyczące <xref:Microsoft.Office.Tools.Excel> lub <xref:Microsoft.Office.Tools.Word> przestrzeni nazw. Ta instrukcja jest generowana automatycznie w nowych projektach, których platformą docelową [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej. Jednak ta instrukcja nie został dodany automatycznie w projektach programu .NET Framework 3.5, których platformą docelową, więc należy ją dodać, jeśli przekierowanie projektu.

 Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w środowisku uruchomieniowym](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="ccevents"></a> Zaktualizuj kod, który obsługuje zdarzenia formantu zawartości programu Word
 W projektach przeznaczonych dla programu .NET Framework 3.5, zdarzenia formanty zawartości programu Word są obsługiwane przez ogólnego <xref:System.EventHandler%601> delegować. W przypadku projektów, których platformą docelową [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym, te zdarzenia są obsługiwane przez inne delegatów.

 W poniższej tabeli wymieniono zdarzenia formantu zawartości programu Word i delegatów, które są skojarzone z nimi w projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej.

|Zdarzenie|Delegat do użycia w [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] i nowszych projektów|
|-----------| - |
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>|<xref:Microsoft.Office.Tools.Word.ContentControlAddedEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlContentUpdatingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>|<xref:Microsoft.Office.Tools.Word.ContentControlDeletingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>|<xref:Microsoft.Office.Tools.Word.ContentControlEnteringEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>|<xref:Microsoft.Office.Tools.Word.ContentControlExitingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlStoreUpdatingEventHandler>|

## <a name="ole"></a> Zaktualizuj kod, który korzysta z klas OLEObject i OLEControl
 W projektach przeznaczonych dla programu .NET Framework 3.5, można dodać niestandardowe formanty (na przykład kontrolek użytkownika Windows Forms) w dokumencie lub arkuszu za pomocą `Microsoft.Office.Tools.Excel.OLEObject` i `Microsoft.Office.Tools.Word.OLEControl` klasy.

 W przypadku projektów, których platformą docelową [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, w ramach tych zajęć zostały zastąpione przez <xref:Microsoft.Office.Tools.Excel.ControlSite> i <xref:Microsoft.Office.Tools.Word.ControlSite> interfejsów. Należy zmodyfikować kod, który odwołuje się do `Microsoft.Office.Tools.Excel.OLEObject` i `Microsoft.Office.Tools.Word.OLEControl` się natomiast do <xref:Microsoft.Office.Tools.Excel.ControlSite> i <xref:Microsoft.Office.Tools.Word.ControlSite>. Innego niż nowe nazwy tych kontrolek zachowują się tak samo jak w projektach przeznaczonych dla programu .NET Framework 3.5.

 Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w środowisku uruchomieniowym](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="itemproperty"></a> Zaktualizuj kod, który używa właściwości Controls.Item(Object)
 W projektach przeznaczonych dla programu .NET Framework 3.5, można użyć właściwości Item(Object) Microsoft.Office.Tools.Word.Document.Controls lub `Microsoft.Office.Tools.Excel.Worksheet.Controls` kolekcji, aby ustalić, czy dokument lub skoroszyt ma określoną kontrolkę.

 W przypadku projektów, których platformą docelową [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej, właściwość Item(Object) została usunięta w tych kolekcjach. Aby ustalić, czy dokument lub skoroszyt zawiera określoną kontrolkę, należy użyć metody Contains(System.Object) <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> lub <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> kolekcji zamiast tego.

 Aby uzyskać więcej informacji o zbieraniu formantów dokumentów i arkuszy, zobacz [dodawanie formantów do dokumentów pakietu Office w środowisku uruchomieniowym](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="collections"></a> Zaktualizuj kod, który używa kolekcje, które wynikają z CollectionBase
 W projektach przeznaczonych dla programu .NET Framework 3.5 kolekcji kilka typów w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] dziedziczyć <xref:System.Collections.CollectionBase> klasy, takie jak `Microsoft.Office.Tools.SmartTagCollection`, `Microsoft.Office.Tools.Excel.ControlCollection`, i `Microsoft.Office.Tools.Word.ControlCollection`.

 W przypadku projektów, których platformą docelową [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym, te typy kolekcji są teraz interfejsy, które nie pochodzą z <xref:System.Collections.CollectionBase>. Niektóre elementy członkowskie nie są już dostępne w tych typów kolekcji, takich jak <xref:System.Collections.CollectionBase.Capacity%2A>, <xref:System.Collections.CollectionBase.List%2A>, i <xref:System.Collections.CollectionBase.InnerList%2A>.

## <a name="see-also"></a>Zobacz także
- [Migrowanie rozwiązań pakietu Office do wersji programu .NET Framework 4 lub nowszej](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Formanty zawartości](../vsto/content-controls.md)
- [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
