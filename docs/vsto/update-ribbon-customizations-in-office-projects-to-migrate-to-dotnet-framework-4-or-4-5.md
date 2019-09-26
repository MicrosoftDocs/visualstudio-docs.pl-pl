---
title: Aktualizowanie dostosowań wstążki w projektach pakietu Office migrowanych do .NET Framework 4, 4,5
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
ms.openlocfilehash: c7d7ab5755f592e57e76dcd68f3dcb9dc2a7eab9
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254348"
---
# <a name="update-ribbon-customizations-in-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Aktualizowanie dostosowań wstążki w projektach pakietu Office migrowanych do .NET Framework 4 lub .NET Framework 4,5
  Jeśli projekt zawiera dostosowaną Wstążkę, która została utworzona przy użyciu elementu projektu **wstążka (projektant graficzny)** , należy wprowadzić następujące zmiany w kodzie projektu, jeśli struktura docelowa zostanie zmieniona na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później.

- Zmodyfikuj wygenerowany kod wstążki.

- Modyfikuj każdy kod, który tworzy wystąpienie formantów wstążki w czasie wykonywania, obsługuje zdarzenia wstążki lub ustawia pozycję składnika wstążki programowo.

## <a name="update-the-generated-ribbon-code"></a>Aktualizowanie wygenerowanego kodu wstążki
 Jeśli docelowa platforma projektu została zmieniona na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, należy zmienić wygenerowany kod dla elementu wstążki, wykonując poniższe kroki. Pliki kodu, które należy zaktualizować, zależą od języka programowania i sposobu tworzenia projektu:

- W projektach Visual Basic lub C# w projektach wizualnych utworzonych w [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] ramach lub [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] wykonaj wszystkie kroki w pliku związanym z kodem wstążki (*YourRibbonItem*. Designer.cs lub *YourRibbonItem*. Designer. vb). Aby wyświetlić plik związany z kodem w projektach Visual Basic, kliknij przycisk **Pokaż wszystkie pliki** w **Eksplorator rozwiązań**.

- W projektach C# wizualnych utworzonych w programie Visual Studio 2008, a następnie uaktualnioniu do [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], wykonaj pierwsze dwa kroki w pliku kodu wstążki (*YourRibbonItem*. cs lub *YourRibbonItem*. vb) i wykonaj pozostałe kroki z Plik związany z kodem wstążki.

### <a name="to-change-the-generated-ribbon-code"></a>Aby zmienić wygenerowany kod wstążki

1. Zmodyfikuj deklarację klasy wstążki, aby dziedziczyć ją od <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> `Microsoft.Office.Tools.Ribbon.OfficeRibbon`zamiast.

2. Zmodyfikuj konstruktora klasy wstążki, jak pokazano poniżej. Jeśli dodaliśmy dowolny z własnych kodów do konstruktora, nie należy zmieniać kodu. W projektach Visual Basic należy zmodyfikować tylko konstruktora bez parametrów. Zignoruj inny Konstruktor.

     Poniższy przykład kodu pokazuje domyślny Konstruktor klasy wstążki w projekcie, który jest przeznaczony dla .NET Framework 3,5.

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

     Poniższy przykład kodu pokazuje domyślny Konstruktor klasy wstążki w projekcie, który jest przeznaczony dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później.

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

3. W metodzie zmodyfikuj każdy kod, który konstruuje kontrolkę wstążki, tak aby kod używał jednej z metod <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> pomocnika obiektu. `InitializeComponent`

    > [!NOTE]
    > W projektach C# wizualnych należy rozwinąć region o nazwie `Component Designer generated code` , aby zobaczyć `InitializeComponent` metodę.

     Załóżmy na przykład, że plik zawiera następujący wiersz kodu, który tworzy wystąpienie <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> nazwy `button1` w projekcie, który jest przeznaczony dla .NET Framework 3,5.

    ```vb
    Me.button1 = New Microsoft.Office.Tools.Ribbon.RibbonButton()
    ```

    ```csharp
    this.button1 = new Microsoft.Office.Tools.Ribbon.RibbonButton();
    ```

     W projekcie, który jest przeznaczony [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] dla lub później, należy zamiast tego użyć poniższego kodu.

    ```vb
    Me.button1 = Me.Factory.CreateRibbonButton()
    ```

    ```csharp
    this.button1 = this.Factory.CreateRibbonButton();
    ```

     Aby uzyskać pełną listę metod pomocnika dla kontrolek wstążki, zobacz Tworzenie [instancji kontrolek wstążki](#ribboncontrols).

4. W projektach C# wizualnych zmodyfikuj dowolny wiersz kodu w `InitializeComponent` <xref:System.EventHandler%601> metodzie, która używa delegata, aby zamiast tego użyć określonego delegata wstążki.

     Załóżmy na przykład, że plik zawiera następujący wiersz kodu, który obsługuje <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> zdarzenie w projekcie, który jest przeznaczony dla .NET Framework 3,5.

    \<CodeContentPlaceHolder > 8</CodeContentPlaceHolder> w projekcie, który jest przeznaczony [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] dla lub w późniejszym czasie, należy zamiast tego użyć poniższego kodu.

    \<CodeContentPlaceHolder > 9</CodeContentPlaceHolder> pełna lista delegatów wstążki znajduje się w temacie [Obsługa zdarzeń wstążki](#ribbonevents).

5. W Visual Basic projekty Znajdź `ThisRibbonCollection` klasę na końcu pliku. Zmodyfikuj deklarację tej klasy, aby nie dziedziczyć od `Microsoft.Office.Tools.Ribbon.RibbonReadOnlyCollection`.

## <a name="ribboncontrols"></a>Tworzenie wystąpień kontrolek wstążki
 Należy zmodyfikować każdy kod, który dynamicznie tworzy wystąpienia kontrolek wstążki. W projektach, które są przeznaczone dla .NET Framework 3,5, formanty wstążki są klasy, które można utworzyć bezpośrednio w niektórych scenariuszach. W projektach, które są [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] przeznaczone dla lub później, te kontrolki są interfejsami, których nie można utworzyć bezpośrednio. Należy utworzyć kontrolki przy użyciu metod dostarczonych przez <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> obiekt.

 Istnieją dwa sposoby uzyskania dostępu <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> do obiektu:

- Przy użyciu właściwości Factory klasy wstążki. Użyj podejścia z kodu w klasie wstążki.

- Za pomocą `Globals.Factory.GetRibbonFactory` metody. Użyj podejścia do kodu spoza klasy wstążki. Aby uzyskać więcej informacji na temat klasy Globals, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).

  Poniższy przykład kodu ilustruje sposób tworzenia <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> w klasie wstążki w projekcie, który jest przeznaczony dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później.

\<CodeContentPlaceHolder > 10</CodeContentPlaceHolder> \<CodeContentPlaceHolder > 11</CodeContentPlaceHolder> w poniższej tabeli wymieniono kontrolki, które można programistycznie utworzyć, i metodę, która ma być używana do tworzenia kontrolek w projektach przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później.

|formant|Metoda RibbonFactory do użycia w [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] projektach i nowszych|
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

## <a name="ribbonevents"></a>Obsłuż zdarzenia wstążki
 Należy zmodyfikować dowolny kod, który obsługuje zdarzenia formantów wstążki. W projektach przeznaczonych dla .NET Framework 3,5 te zdarzenia są obsługiwane przez delegata ogólnego <xref:System.EventHandler%601> . W projektach przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszych zdarzeń te zdarzenia są teraz obsługiwane przez innych delegatów.

 Poniższa tabela zawiera listę zdarzeń wstążki i delegatów skojarzonych z nimi w projektach przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszych.

|Zdarzenie|Delegat do użycia w [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] projektach i nowszych|
|-----------| - |
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>zdarzenie w wygenerowanej klasie wstążki|<xref:Microsoft.Office.Tools.Ribbon.RibbonLoadImageEventHandler>|
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>|<xref:Microsoft.Office.Tools.Ribbon.RibbonUIEventHandler>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.SelectionChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventHandler>|

## <a name="set-the-position-of-a-ribbon-component-programmatically"></a>Ustaw położenie składnika wstążki programowo
 Należy zmodyfikować każdy kod, który ustawia położenie grup wstążki, kart lub kontrolek. `AfterOfficeId` W projektach przeznaczonych dla .NET Framework 3,5 można użyć metod i `BeforeOfficeId` klasy `Position` statycznej `Microsoft.Office.Tools.Ribbon.RibbonPosition` , aby przypisać właściwość grupy, karty lub kontrolki. W projektach przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszych należy uzyskać dostęp do tych metod przy <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.RibbonPosition%2A> użyciu właściwości dostarczonej przez <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> obiekt.

 Istnieją dwa sposoby uzyskania dostępu <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> do obiektu:

- Przy użyciu `Factory` właściwości klasy wstążki. Użyj podejścia z kodu w klasie wstążki.

- Za pomocą `Globals.Factory.GetRibbonFactory` metody. Użyj podejścia do kodu spoza klasy wstążki. Aby uzyskać więcej informacji na temat klasy Globals, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).

  Poniższy przykład kodu demonstruje, jak ustawić `Position` Właściwość karty w klasie wstążki w projekcie, który jest przeznaczony dla .NET Framework 3,5.

```vb
Me.tab1.Position = RibbonPosition.AfterOfficeId("TabHome")
```

```csharp
this.tab1.Position = RibbonPosition.AfterOfficeId("TabHome");
```

 Poniższy przykład kodu demonstruje to samo zadanie w projekcie, który odwołuje się [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]do.

```vb
Me.tab1.Position = Me.Factory.RibbonPosition.AfterOfficeId("TabHome")
```

```csharp
this.tab1.Position = this.Factory.RibbonPosition.AfterOfficeId("TabHome");
```

## <a name="see-also"></a>Zobacz także
- [Migrowanie rozwiązań pakietu Office do .NET Framework 4 lub nowszego](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
