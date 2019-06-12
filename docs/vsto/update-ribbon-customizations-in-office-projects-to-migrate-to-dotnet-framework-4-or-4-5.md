---
title: Aktualizacja dostosowań Wstążki w projektach pakietu Office migracji do platformy .NET Framework 4, 4.5
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
ms.openlocfilehash: 03424ecb477a32ecff31a83d341a6eef178a31e0
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66836077"
---
# <a name="update-ribbon-customizations-in-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Aktualizowanie dostosowań Wstążki w projektach pakietu Office, które przenoszonych do oprogramowania .NET Framework 4 lub .NET Framework 4.5
  Jeśli projekt zawiera dostosowania wstążki, który został utworzony przy użyciu **Wstążka (Projektant graficzny)** elementu projektu, należy wprowadzić następujące zmiany do kodu projektu, zmiana platformy docelowej na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później.

- Zmodyfikuj wygenerowanego kodu wstążki.

- Zmodyfikować każdy kod, który tworzy formantów wstążki w czasie wykonywania, obsługi zdarzeń Wstążki lub programowo Ustawia położenie składnika wstążki.

## <a name="update-the-generated-ribbon-code"></a>Aktualizacja wygenerowanego kodu wstążki
 Jeśli platforma docelowa projektu zostanie zmieniony na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej, należy zmienić wygenerowanego kodu dla elementu wstążki, wykonując następujące kroki. Pliki kodu, który należy zaktualizować zależą od języka programowania i sposobu tworzenia projektu:

- W projektach języka Visual Basic lub w projektach Visual C#, które zostały utworzone w jednej [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] lub [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] wykonaj wszystkie kroki przedstawione w pliku związanym z kodem wstążki (*YourRibbonItem*. Designer.cs narzędzie lub *YourRibbonItem*. Designer.VB). Aby wyświetlić plik związany z kodem w projektach języka Visual Basic, kliknij **Pokaż wszystkie pliki** znajdujący się w **Eksploratora rozwiązań**.

- W projektach Visual C#, utworzone w programie Visual Studio 2008 i następnie przeprowadzono uaktualnienie do [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], wykonaj dwa pierwsze kroki w plik kodu wstążki (*YourRibbonItem*.cs lub *YourRibbonItem*.vb), a Wykonaj pozostałe kroki w pliku związanym z kodem wstążki.

### <a name="to-change-the-generated-ribbon-code"></a>Aby zmienić wygenerowanego kodu wstążki

1. Zmodyfikuj deklarację klasy wstążki, tak, aby pochodzi od klasy <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> zamiast `Microsoft.Office.Tools.Ribbon.OfficeRibbon`.

2. Zmodyfikuj konstruktora klasy wstążki, jak pokazano poniżej. Jeśli dodano własne kodu do konstruktora, nie należy zmieniać swój kod. W projektach języka Visual Basic zmodyfikuj konstruktora bez parametrów. Ignoruj innego konstruktora.

     Poniższy przykład kodu pokazuje konstruktora domyślnego w klasie wstążki w projekcie, przeznaczonego programu .NET Framework 3.5.

    ```vb
    Public Sub New()
        MyBase.New()
        InitializeComponent()
    End Sub
    ```

    ```csharp
    public Ribbon1()
    {
        InitializeComponent();
    }
    ```

     Poniższy przykładowy kod przedstawia domyślny konstruktor obiektu klasy wstążki w projekcie przeznaczonego [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej.

    ```vb
    Public Sub New()
        MyBase.New(Globals.Factory.GetRibbonFactory())
        InitializeComponent()
    End Sub
    ```

    ```csharp
    public Ribbon1()
        : base(Globals.Factory.GetRibbonFactory())
    {
        InitializeComponent();
    }
    ```

3. W `InitializeComponent` metody, zmodyfikować każdy kod, który konstruuje formantu wstążki, aby kod zamiast tego używa jednej z metod Pomocnika <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> obiektu.

    > [!NOTE]
    > W projektach Visual C#, należy rozwinąć region, który nosi nazwę `Component Designer generated code` się `InitializeComponent` metody.

     Na przykład załóżmy, że plik zawiera następujący wiersz kodu, która tworzy wystąpienie <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> o nazwie `button1` w projekcie, który jest przeznaczony dla .NET Framework 3.5.

    ```vb
    Me.button1 = New Microsoft.Office.Tools.Ribbon.RibbonButton()
    ```

    ```csharp
    this.button1 = new Microsoft.Office.Tools.Ribbon.RibbonButton();
    ```

     W projekcie, który jest przeznaczony dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej, należy użyć następującego kodu.

    ```vb
    Me.button1 = Me.Factory.CreateRibbonButton()
    ```

    ```csharp
    this.button1 = this.Factory.CreateRibbonButton();
    ```

     Aby uzyskać pełną listę metody pomocnicze dla formantów wstążki, zobacz [formantów wstążki wystąpienia](#ribboncontrols).

4. W projektach Visual C#, modyfikowanie dowolnej linii kodu w `InitializeComponent` metody, która używa <xref:System.EventHandler%601> delegata, aby użyć określonego delegata wstążki.

     Na przykład załóżmy, że plik zawiera następujący wiersz kodu, który obsługuje <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> zdarzenia w projekcie, który jest przeznaczony dla .NET Framework 3.5.

    \<CodeContentPlaceHolder > 8</CodeContentPlaceHolder> w projekcie, który jest przeznaczony dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej, należy użyć następującego kodu.

    \<CodeContentPlaceHolder > 9</CodeContentPlaceHolder> uzyskać pełną listę obiektów delegowanych wstążki, zobacz [zdarzeń obsługi wstążki](#ribbonevents).

5. W projektach języka Visual Basic, zlokalizuj `ThisRibbonCollection` klasy na końcu pliku. Zmodyfikuj deklarację zmiennej tej klasy, dzięki czemu nie będzie już dziedziczył z `Microsoft.Office.Tools.Ribbon.RibbonReadOnlyCollection`.

## <a name="ribboncontrols"></a> Utwórz wystąpienie formanty wstążki
 Należy zmodyfikować każdy kod, który dynamicznie tworzy formanty wstążki. W projektach programu .NET Framework 3.5, których platformą docelową formanty wstążki są klas, które można utworzyć wystąpienie bezpośrednio w niektórych scenariuszach. W przypadku projektów, których platformą docelową [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej, te kontrolki są interfejsy, które nie są bezpośrednio wystąpienia. Formanty należy utworzyć przy użyciu metod, które są dostarczane przez <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> obiektu.

 Istnieją dwa sposoby dostępu do <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> obiektu:

- Za pomocą właściwości fabryki klasy wstążki. Użyj podejścia z kodu w klasie wstążki.

- Za pomocą `Globals.Factory.GetRibbonFactory` metody. Użyj podejścia do kodu spoza klasy wstążki. Aby uzyskać więcej informacji na temat klasy globalne Zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).

  Poniższy przykład kodu demonstruje sposób tworzenia <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> w klasie wstążki w projekcie, który jest przeznaczony dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej.

\<CodeContentPlaceHolder > 10</CodeContentPlaceHolder> \<CodeContentPlaceHolder > 11</CodeContentPlaceHolder> w poniższej tabeli wymieniono kontrolki, można programowo tworzyć i metody służące do tworzenia kontrolek w projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej.

|formant|Metoda RibbonFactory do użycia w [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] i nowszych projektów|
|-------------| - |
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButton%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButtonGroup%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonCheckBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonComboBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDialogLauncher%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>:|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDown%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDownItem>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDownItem%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonEditBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGallery%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGroup%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonLabel%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonManager>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonManager%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonMenu%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSeparator%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSplitButton%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonTab%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonToggleButton%2A>|

## <a name="ribbonevents"></a> Obsługi zdarzeń wstążki
 Należy zmodyfikować każdy kod, który obsługuje zdarzenia formantów wstążki. W projektach przeznaczonych dla programu .NET Framework 3.5, te zdarzenia są obsługiwane przez ogólnego <xref:System.EventHandler%601> delegować. W przypadku projektów, których platformą docelową [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym, te zdarzenia są teraz obsługiwane przez inne delegatów.

 W poniższej tabeli wymieniono zdarzenia Wstążki i delegatów, które są skojarzone z nimi w projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej.

|Zdarzenie|Delegat do użycia w [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] i nowszych projektów|
|-----------| - |
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage> zdarzenia w generowanej klasie wstążki|<xref:Microsoft.Office.Tools.Ribbon.RibbonLoadImageEventHandler>|
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>|<xref:Microsoft.Office.Tools.Ribbon.RibbonUIEventHandler>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.SelectionChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventHandler>|

## <a name="set-the-position-of-a-ribbon-component-programmatically"></a>Programowe Ustawianie położenia komponentu wstążki
 Należy zmodyfikować każdy kod, który Ustawia położenie grup, karty lub kontrolek wstążki. W projektach przeznaczonych dla programu .NET Framework 3.5, można użyć `AfterOfficeId` i `BeforeOfficeId` metod statycznych `Microsoft.Office.Tools.Ribbon.RibbonPosition` klasy, aby przypisać `Position` właściwości grupy, karty lub kontrolki. W przypadku projektów, których platformą docelową [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, należy dostęp tych metod przy użyciu <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.RibbonPosition%2A> podana przez właściwość <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> obiektu.

 Istnieją dwa sposoby dostępu do <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> obiektu:

- Za pomocą `Factory` właściwość klasy wstążki. Użyj podejścia z kodu w klasie wstążki.

- Za pomocą `Globals.Factory.GetRibbonFactory` metody. Użyj podejścia do kodu spoza klasy wstążki. Aby uzyskać więcej informacji na temat klasy globalne Zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).

  Poniższy przykład kodu demonstruje sposób ustawiania `Position` właściwości karty w klasie wstążki w projekcie, który jest przeznaczony dla .NET Framework 3.5.

```vb
Me.tab1.Position = RibbonPosition.AfterOfficeId("TabHome")
```

```csharp
this.tab1.Position = RibbonPosition.AfterOfficeId("TabHome");
```

 Poniższy przykład kodu demonstruje tego samego zadania w projekcie, który jest przeznaczony dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].

```vb
Me.tab1.Position = Me.Factory.RibbonPosition.AfterOfficeId("TabHome")
```

```csharp
this.tab1.Position = this.Factory.RibbonPosition.AfterOfficeId("TabHome");
```

## <a name="see-also"></a>Zobacz także
- [Migrowanie rozwiązań pakietu Office do wersji programu .NET Framework 4 lub nowszej](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
