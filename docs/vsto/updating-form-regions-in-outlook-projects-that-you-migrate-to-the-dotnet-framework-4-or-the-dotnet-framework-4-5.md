---
title: Aktualizowanie regionów formularzy programu Outlook podczas migracji do .NET Framework 4,5
titleSuffix: ''
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
ms.openlocfilehash: 9d8978703630e99ecb930e18e7d128eddff8792f
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584402"
---
# <a name="update-outlook-form-regions-when-migrated-to-net-framework-45"></a>Aktualizowanie regionów formularzy programu Outlook podczas migracji do .NET Framework 4,5

  Jeśli platforma docelowa projektu dodatku VSTO programu Outlook z regionem formularza zostanie zmieniona na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, należy wprowadzić pewne zmiany w kodzie regionu formularza i w dowolnym kodzie, który tworzy wystąpienia niektórych klas regionów formularzy w czasie wykonywania.

## <a name="update-the-generated-form-region-code"></a>Zaktualizuj wygenerowany kod regionu formularza
 Jeśli docelowa platforma projektu została zmieniona na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, należy zmienić wygenerowany kod regionu formularza. Wprowadzane zmiany są różne dla regionów formularzy zaprojektowanych w programie Visual Studio i regionach formularzy zaimportowanych z programu Outlook. Aby uzyskać więcej informacji na temat różnic między tymi typami regionów formularzy, zobacz [Tworzenie regionów formularzy w programie Outlook](../vsto/creating-outlook-form-regions.md).

### <a name="to-update-the-generated-code-for-a-form-region-that-you-designed-in-visual-studio"></a>Aby zaktualizować wygenerowany kod dla regionu formularza zaprojektowanego w programie Visual Studio

1. Otwórz plik z kodem regionu formularza w edytorze kodu. Ten plik ma nazwę *YourFormRegion*. Designer.cs lub *YourFormRegion*. Designer. vb. Aby wyświetlić ten plik w projektach Visual Basic, kliknij przycisk **Pokaż wszystkie pliki** w **Eksplorator rozwiązań**.

2. Zmodyfikuj deklarację klasy region formularza, aby dziedziczyć ją od <xref:Microsoft.Office.Tools.Outlook.FormRegionBase> zamiast `Microsoft.Office.Tools.Outlook.FormRegionControl` .

3. Zmodyfikuj konstruktora klasy region formularza, jak pokazano w poniższym przykładzie kodu.

     Poniższy przykład kodu pokazuje konstruktora klasy regionu formularza w projekcie, który jest przeznaczony dla .NET Framework 3,5.

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

     Poniższy przykład kodu pokazuje konstruktora klasy regionu formularza w projekcie, który jest przeznaczony dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

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

4. Zmodyfikuj podpis `InitializeManifest` metody, jak pokazano poniżej. Upewnij się, że nie modyfikujesz kodu w metodzie; Ten kod reprezentuje ustawienia regionu formularza, które zostały zastosowane do projektanta. W projektach Visual C#, należy rozwinąć region o nazwie, `Form Region Designer generated code` Aby zobaczyć tę metodę.

     Poniższy przykład kodu przedstawia sygnaturę `InitializeManifest` metody w projekcie, która jest przeznaczona dla .NET Framework 3,5.

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

     Poniższy przykład kodu przedstawia `InitializeManifest` metodę podpisu w projekcie, który jest przeznaczony dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

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

5. Dodaj nowy element regionu formularza programu Outlook do projektu. Otwórz plik związany z kodem dla nowego regionu formularza, zlokalizuj *YourNewFormRegion* `Factory` i `WindowFormRegionCollection` klasy w pliku i skopiuj te klasy do Schowka.

6. Usuń nowy region formularza, który został dodany do projektu.

7. W pliku związanym z kodem w regionie formularza, który aktualizujesz, aby działał w projekcie przekierowaniu, Znajdź *YourOriginalFormRegion* `Factory` i `WindowFormRegionCollection` klasy i zastąp je kodem skopiowanym z nowego regionu formularza.

8. W *YourNewFormRegion* `Factory` i `WindowFormRegionCollection` Klasa Wyszukaj wszystkie odwołania do klasy *YourNewFormRegion* i Zmień każde odwołanie do klasy *YourOriginalFormRegion* . Na przykład jeśli aktualizowany region formularza ma nazwę, `SalesDataFormRegion` a nowy region formularza utworzony w kroku 5 ma nazwę `FormRegion1` , Zmień wszystkie odwołania `FormRegion1` do `SalesDataFormRegion` .

#### <a name="to-update-the-generated-code-for-a-form-region-that-you-imported-from-outlook"></a>Aby zaktualizować wygenerowany kod dla regionu formularza zaimportowanego z programu Outlook

1. Otwórz plik z kodem regionu formularza w edytorze kodu. Ten plik ma nazwę *YourFormRegion*. Designer.cs lub *YourFormRegion*. Designer. vb. Aby wyświetlić ten plik w projektach Visual Basic, kliknij przycisk **Pokaż wszystkie pliki** w **Eksplorator rozwiązań**.

2. Zmodyfikuj deklarację klasy region formularza, aby dziedziczyć ją od <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase> zamiast `Microsoft.Office.Tools.Outlook.ImportedFormRegion` .

3. Zmodyfikuj konstruktora klasy region formularza, jak pokazano w poniższym przykładzie kodu.

     Poniższy przykład kodu pokazuje konstruktora klasy regionu formularza w projekcie, który jest przeznaczony dla .NET Framework 3,5.

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

     Poniższy przykład kodu przedstawia sygnaturę konstruktora klasy regionu formularza w projekcie, który odwołuje się do [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

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

4. Dla każdego wiersza kodu w `InitializeControls` metodzie, która inicjuje formant w klasie region formularza, zmodyfikuj kod, jak pokazano poniżej.

     Poniższy przykład kodu pokazuje, jak zainicjować kontrolkę w projekcie, który jest przeznaczony dla .NET Framework 3,5. W tym kodzie `GetFormRegionControl` Metoda ma parametr typu, który określa typ zwracanej kontrolki.

    ```vb
    Me.olkTextBox1 = Me.GetFormRegionControl(Of Microsoft.Office.Interop.Outlook.OlkTextBox)("OlkTextBox1")
    ```

    ```csharp
    this.olkTextBox1 = this.GetFormRegionControl<Microsoft.Office.Interop.Outlook.OlkTextBox>("OlkTextBox1");
    ```

     Poniższy przykład kodu pokazuje, jak zainicjować kontrolkę w projekcie, który jest przeznaczony dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . W tym kodzie Metoda nie <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase.GetFormRegionControl%2A> ma parametru typu. Wartość zwracana należy rzutować na typ inicjowanej kontrolki.

    ```vb
    Me.olkTextBox1 = CType(GetFormRegionControl("OlkTextBox1"), Microsoft.Office.Interop.Outlook.OlkTextBox)
    ```

    ```csharp
    this.olkTextBox1 = (Microsoft.Office.Interop.Outlook.OlkTextBox)GetFormRegionControl("OlkTextBox1");
    ```

5. Dodaj nowy element regionu formularza programu Outlook do projektu. Otwórz plik związany z kodem dla nowego regionu formularza, zlokalizuj *YourNewFormRegion* `Factory` i `WindowFormRegionCollection` klasy w pliku i skopiuj te klasy do Schowka.

6. Usuń nowy region formularza, który został dodany do projektu.

7. W pliku związanym z kodem w regionie formularza, który aktualizujesz, aby działał w projekcie przekierowaniu, Znajdź *YourOriginalFormRegion* `Factory` i `WindowFormRegionCollection` klasy i zastąp je kodem skopiowanym z nowego regionu formularza.

8. W *YourNewFormRegion* `Factory` i `WindowFormRegionCollection` Klasa Wyszukaj wszystkie odwołania do klasy *YourNewFormRegion* i Zmień każde odwołanie do klasy *YourOriginalFormRegion* . Na przykład jeśli aktualizowany region formularza ma nazwę, `SalesDataFormRegion` a nowy region formularza utworzony w kroku 5 ma nazwę `FormRegion1` , Zmień wszystkie odwołania `FormRegion1` do `SalesDataFormRegion` .

## <a name="instantiate-form-region-classes"></a>Tworzenie wystąpienia klas regionów formularza
 Należy zmodyfikować każdy kod, który dynamicznie tworzy wystąpienia niektórych klas regionów formularza. W projektach przeznaczonych dla .NET Framework 3,5 można utworzyć wystąpienia klas regionów formularza, takich jak `Microsoft.Office.Tools.Outlook.FormRegionManifest` bezpośrednio. W projektach przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszych, te klasy są interfejsami, których nie można utworzyć bezpośrednio.

 Jeśli docelowa platforma projektu została zmieniona na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, należy utworzyć wystąpienie interfejsów przy użyciu metod dostarczonych przez `Globals.Factory` Właściwość. Aby uzyskać więcej informacji na temat `Globals.Factory` właściwości, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).

 W poniższej tabeli przedstawiono typy regionów formularzy i metodę, która ma zostać użyta do utworzenia wystąpienia typów w projektach przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub w późniejszym czasie.

|Typ|Metoda fabryki do użycia|
|----------|---------------------------|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionCustomAction>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionCustomAction%2A>|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionInitializingEventArgs%2A>|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionManifest%2A>|

## <a name="see-also"></a>Zobacz też
- [Migrowanie rozwiązań pakietu Office do .NET Framework 4 lub nowszego](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
