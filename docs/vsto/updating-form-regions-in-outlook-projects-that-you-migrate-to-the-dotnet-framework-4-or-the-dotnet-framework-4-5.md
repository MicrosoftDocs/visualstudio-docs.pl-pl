---
title: Aktualizowanie regionów formularzy w projektach programu Outlook, są migrowane do programu .NET Framework 4 lub .NET Framework 4.5
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
ms.openlocfilehash: e27850b7531af4d0883f2cbf250987562a56b8f5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56597650"
---
# <a name="update-form-regions-in-outlook-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Aktualizowanie regionów formularzy w projektach programu Outlook, są migrowane do programu .NET Framework 4 lub .NET Framework 4.5
  Zmiana platformy docelowej projektu dodatku narzędzi VSTO dla programu Outlook z regionu formularza na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, należy wprowadzić pewne zmiany do kodu regionu generowanym formularzu i wszelki kod, który tworzy wystąpienie niektórych klas regionu formularza w czasie wykonywania.

## <a name="update-the-generated-form-region-code"></a>Zaktualizuj kod regionu generowanym formularzu
 Jeśli platforma docelowa projektu zostanie zmieniony na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej, musisz zmienić kod regionu generowanym formularzu. Wprowadzone zmiany są różne dla regionów formularza, które skonstruowane w programie Visual Studio i formularz regionach, zaimportowane z programu Outlook. Aby uzyskać więcej informacji na temat różnic między tymi typami regionów formularzy zobacz [regionach formularzy programu Outlook z tworzenia](../vsto/creating-outlook-form-regions.md).

### <a name="to-update-the-generated-code-for-a-form-region-that-you-designed-in-visual-studio"></a>Aby zaktualizować kod generowany dla regionu formularza zaprojektowanego w programie Visual Studio

1.  Otwórz plik CodeBehind regionu formularza w edytorze kodu. Ten plik ma nazwę *YourFormRegion*. Designer.cs narzędzie lub *YourFormRegion*. Designer.VB. Aby wyświetlić ten plik w projektach języka Visual Basic, kliknij **Pokaż wszystkie pliki** znajdujący się w **Eksploratora rozwiązań**.

2.  Zmodyfikuj deklarację klasy regionu formularza, tak, aby pochodzi od klasy <xref:Microsoft.Office.Tools.Outlook.FormRegionBase> zamiast `Microsoft.Office.Tools.Outlook.FormRegionControl`.

3.  Zmodyfikuj konstruktora klasy regionu formularza, jak pokazano w poniższych przykładach kodu.

     Poniższy przykład kodu pokazuje konstruktora klasy regionu formularza w projekcie, przeznaczonego programu .NET Framework 3.5.

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(formRegion)
        Me.InitializeComponent()
    End Sub
    ```

    ```csharp
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(formRegion)
    {
        this.InitializeComponent();
    }
    ```

     Poniższy przykład kodu pokazuje konstruktora klasy regionu formularza w projekcie przeznaczonego [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(Globals.Factory, formRegion)
        Me.InitializeComponent()
    End Sub
    ```

    ```csharp
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(Globals.Factory, formRegion)
    {
        this.InitializeComponent();
    }
    ```

4.  Zmodyfikuj podpis metody `InitializeManifest` metody, jak pokazano poniżej. Upewnij się, że nie należy modyfikować kod w metodzie; Ten kod reprezentuje ustawienia regionu formularza, które zostały zastosowane w projektancie. W elemencie wizualnym C# projektów, należy rozwinąć region, który nosi nazwę `Form Region Designer generated code` Aby wyświetlić tę metodę.

     Poniższy przykład kodu pokazuje podpis `InitializeManifest` metody w projekcie, który jest przeznaczony dla .NET Framework 3.5.

    ```vb
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest)

        ' Do not change code in this method.
    End Sub
    ```

    ```csharp
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest)
    {
        // Do not change code in this method.
    }
    ```

     Poniższy przykład kodu pokazuje podpis `InitializeManifest` metody w projekcie, który jest przeznaczony dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].

    ```vb
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest,
        ByVal factory As Microsoft.Office.Tools.Outlook.Factory)

        ' Do not change code in this method.
    End Sub
    ```

    ```csharp
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest,
        Microsoft.Office.Tools.Outlook.Factory factory)
    {
        // Do not change code in this method.
    }
    ```

5.  Dodaj nowy element Region formularza programu Outlook do projektu. Otwórz plik związany z kodem, aby uzyskać nowy region formularza, odszukaj *YourNewFormRegion* `Factory` i `WindowFormRegionCollection` klasy w pliku, a następnie skopiuj te klasy do Schowka.

6.  Usuń nowy region formularza, który został dodany do projektu.

7.  W pliku związanym z kodem regionu formularza, która jest aktualizowana do pracy w projekcie zmienianą zlokalizuj *YourOriginalFormRegion* `Factory` i `WindowFormRegionCollection` klasy i zastąpić je z kodem, który został skopiowany z Nowy region formularza.

8.  W *YourNewFormRegion* `Factory` i `WindowFormRegionCollection` wyszukiwanie wszystkich odwołań do klas, *YourNewFormRegion* klasy i zmienić każde odwołanie do  *YourOriginalFormRegion* klasy zamiast tego. Na przykład, jeśli aktualizujesz region formularza jest o nazwie `SalesDataFormRegion` i nosi nazwę nowy region formularza zostanie utworzony w kroku 5 `FormRegion1`, zmienić wszystkie odwołania z `FormRegion1` do `SalesDataFormRegion`.

#### <a name="to-update-the-generated-code-for-a-form-region-that-you-imported-from-outlook"></a>Aby zaktualizować kod generowany dla regionu formularza, który został zaimportowany z programu Outlook

1.  Otwórz plik CodeBehind regionu formularza w edytorze kodu. Ten plik ma nazwę *YourFormRegion*. Designer.cs narzędzie lub *YourFormRegion*. Designer.VB. Aby wyświetlić ten plik w projektach języka Visual Basic, kliknij **Pokaż wszystkie pliki** znajdujący się w **Eksploratora rozwiązań**.

2.  Zmodyfikuj deklarację klasy regionu formularza, tak, aby pochodzi od klasy <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase> zamiast `Microsoft.Office.Tools.Outlook.ImportedFormRegion`.

3.  Zmodyfikuj konstruktora klasy regionu formularza, jak pokazano w poniższych przykładach kodu.

     Poniższy przykład kodu pokazuje konstruktora klasy regionu formularza w projekcie, przeznaczonego programu .NET Framework 3.5.

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(formRegion)
    End Sub
    ```

    ```csharp
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(formRegion)
    {
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);
    }
    ```

     Poniższy przykład kodu pokazuje podpis konstruktora klasy regionu formularza w projekcie przeznaczonego [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(Globals.Factory, formRegion)
    End Sub
    ```

    ```csharp
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(Globals.Factory, formRegion)
    {
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);
    }
    ```

4.  Dla każdego wiersza kodu w `InitializeControls` metodę, która inicjuje kontrolkę w klasie regionu formularza, należy zmodyfikować kod, jak pokazano poniżej.

     W poniższym przykładzie kodu pokazano, jak zainicjować formantu w projekcie przeznaczonego programu .NET Framework 3.5. W tym kodzie `GetFormRegionControl` metoda ma parametr typu, który określa typ kontrolki, która jest zwracana.

    ```vb
    Me.olkTextBox1 = Me.GetFormRegionControl(Of Microsoft.Office.Interop.Outlook.OlkTextBox)("OlkTextBox1")
    ```

    ```csharp
    this.olkTextBox1 = this.GetFormRegionControl<Microsoft.Office.Interop.Outlook.OlkTextBox>("OlkTextBox1");
    ```

     Poniższy przykład kodu pokazuje, jak zainicjować kontrolkę, która w projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. W tym kodzie <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase.GetFormRegionControl%2A> metoda nie ma parametru typu. Należy rzutować wartości zwróconej na typ kontrolki, które są inicjowanie.

    ```vb
    Me.olkTextBox1 = CType(GetFormRegionControl("OlkTextBox1"), Microsoft.Office.Interop.Outlook.OlkTextBox)
    ```

    ```csharp
    this.olkTextBox1 = (Microsoft.Office.Interop.Outlook.OlkTextBox)GetFormRegionControl("OlkTextBox1");
    ```

5.  Dodaj nowy element Region formularza programu Outlook do projektu. Otwórz plik związany z kodem, aby uzyskać nowy region formularza, odszukaj *YourNewFormRegion* `Factory` i `WindowFormRegionCollection` klasy w pliku, a następnie skopiuj te klasy do Schowka.

6.  Usuń nowy region formularza, który został dodany do projektu.

7.  W pliku związanym z kodem regionu formularza, która jest aktualizowana do pracy w projekcie zmienianą zlokalizuj *YourOriginalFormRegion* `Factory` i `WindowFormRegionCollection` klasy i zastąpić je z kodem, który został skopiowany z Nowy region formularza.

8.  W *YourNewFormRegion* `Factory` i `WindowFormRegionCollection` wyszukiwanie wszystkich odwołań do klas, *YourNewFormRegion* klasy i zmienić każde odwołanie do  *YourOriginalFormRegion* klasy zamiast tego. Na przykład, jeśli aktualizujesz region formularza jest o nazwie `SalesDataFormRegion` i nosi nazwę nowy region formularza zostanie utworzony w kroku 5 `FormRegion1`, zmienić wszystkie odwołania z `FormRegion1` do `SalesDataFormRegion`.

## <a name="instantiate-form-region-classes"></a>Utwórz wystąpienie klasy regionu formularza
 Należy zmodyfikować każdy kod, który dynamicznie tworzy niektórych klas regionu formularza. W projektach przeznaczonych dla programu .NET Framework 3.5, można utworzyć wystąpienie klasy regionu formularza takich jak `Microsoft.Office.Tools.Outlook.FormRegionManifest` bezpośrednio. W przypadku projektów, których platformą docelową [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym, te klasy są interfejsy, które nie są bezpośrednio wystąpienia.

 Jeśli platforma docelowa projektu zostanie zmieniony na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej, trzeba utworzyć przy użyciu metod, które są dostarczane przez interfejsy `Globals.Factory` właściwości. Aby uzyskać więcej informacji na temat `Globals.Factory` właściwości, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).

 Poniższa tabela zawiera listę typów regionu formularza i metody służące do utworzenia wystąpienia typów projektów, których celem [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej.

|Typ|Metoda fabryki do użycia|
|----------|---------------------------|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionCustomAction>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionCustomAction%2A>|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionInitializingEventArgs%2A>|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionManifest%2A>|

## <a name="see-also"></a>Zobacz także
- [Migrowanie rozwiązań pakietu Office do wersji programu .NET Framework 4 lub nowszej](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
