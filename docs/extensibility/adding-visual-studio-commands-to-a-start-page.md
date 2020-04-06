---
title: Dodawanie poleceń programu Visual Studio do strony początkowej | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 13dd40006039209b06cc6a71760fdbaa240db4fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740111"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Dodawanie poleceń programu Visual Studio do strony początkowej

Podczas tworzenia niestandardowej strony początkowej można dodawać do niej polecenia programu Visual Studio. W tym dokumencie omówiono różne sposoby powiązania poleceń programu Visual Studio z obiektami XAML na stronie początkowej.

Aby uzyskać więcej informacji o poleceniach w języku XAML, zobacz [Omówienie poleceń](/dotnet/framework/wpf/advanced/commanding-overview)

## <a name="add-commands-from-the-command-well"></a>Dobrze dodawać polecenia z polecenia

Strona początkowa utworzona w obszarze Tworzenie <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> [niestandardowej strony początkowej](../extensibility/creating-a-custom-start-page.md) dodała obszary nazw i obszary nazw w następujący sposób.

```xml
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

Dodaj inną przestrzeń nazw dla pliku Microsoft.VisualStudio.Shell z zestawu *Microsoft.VisualStudio.Shell.Immutable.11.0.dll*. (Może być konieczne dodanie odwołania do tego zestawu w projekcie).

```xml
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
```

`vscom:` Aliasu można użyć do powiązania poleceń programu Visual Studio z <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> formantami XAML na stronie, ustawiając właściwość formantu na `vscom:VSCommands.ExecuteCommand`. Następnie można ustawić <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> właściwość na nazwę polecenia do wykonania, jak pokazano w poniższym przykładzie.

```xml
<Button Name="btnNewProj" Content="New Project"
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
    CommandParameter="File.NewProject" >
</Button>
```

> [!NOTE]
> Alias, `x:` który odwołuje się do schematu XAML, jest wymagany na początku wszystkich poleceń.

 Można ustawić wartość właściwości `Command` na dowolne polecenie, do którego można uzyskać dostęp z okna **Polecenia.** Aby uzyskać listę dostępnych poleceń, zobacz [Aliasy poleceń programu Visual Studio](../ide/reference/visual-studio-command-aliases.md).

 Jeśli polecenie dodawania wymaga dodatkowego parametru, można dodać `CommandParameter` go do wartości właściwości. Oddziel parametry od poleceń za pomocą spacji, jak pokazano w poniższym przykładzie.

```xml
<Button Content="Web Search"
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"
        CommandParameter="View.WebBrowser www.bing.com" />
```

### <a name="call-extensions-from-the-command-well"></a>Dobrze wywołać rozszerzenia z polecenia
 Polecenia z zarejestrowanych pakietów VSPackages można wywołać przy użyciu tej samej składni, która jest używana do wywoływania innych poleceń programu Visual Studio. Jeśli na przykład zainstalowany program VSPackage doda polecenie **Strona główna** do menu `CommandParameter` **Widok,** można wywołać to polecenie, ustawiając na `View.HomePage`.

> [!NOTE]
> Jeśli wywołasz polecenie, które jest skojarzone z VSPackage, pakiet musi zostać załadowany, gdy polecenie jest wywoływane.

## <a name="add-commands-from-assemblies"></a>Dodawanie poleceń z zestawów
 Aby wywołać polecenie z zestawu lub uzyskać dostęp do kodu w programie VSPackage, który nie jest skojarzony z poleceniem menu, należy utworzyć alias dla zestawu, a następnie wywołać alias.

### <a name="to-call-a-command-from-an-assembly"></a>Aby wywołać polecenie z zestawu

1. W rozwiązaniu dodaj odwołanie do zestawu.

2. U góry pliku *StartPage.xaml* dodaj dyrektywę obszaru nazw dla zestawu, jak pokazano w poniższym przykładzie.

    ```xml
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
    ```

3. Wywołaj polecenie, ustawiając `Command` właściwość obiektu XAML, jak pokazano w poniższym przykładzie.

     Xaml

    ```
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>
    ```

> [!NOTE]
> Należy skopiować zespół, a następnie wkleić go w *.. \\{Folder instalacyjny programu Visual Studio}\Common7\IDE\PrivateAssemblies,\* aby upewnić się, że jest ładowany przed jego wywołaniem.

## <a name="add-commands-with-the-dte-object"></a>Dodawanie poleceń za pomocą obiektu DTE
 Dostęp do obiektu DTE można uzyskać ze strony początkowej, zarówno w znacznikach, jak i w kodzie.

 W znacznikach można uzyskać do niego dostęp za pomocą składni <xref:EnvDTE.DTE> [rozszerzenia znaczników powiązania,](/dotnet/framework/wpf/advanced/binding-markup-extension) aby wywołać obiekt. Za pomocą tej metody można powiązać z simple właściwości, takie jak te, które zwracają kolekcje, ale nie można powiązać z metod lub usług. Poniższy przykład <xref:System.Windows.Controls.TextBlock> przedstawia formant, <xref:EnvDTE._DTE.Name%2A> który wiąże <xref:System.Windows.Controls.ListBox> się z właściwością <xref:EnvDTE.Window.Caption%2A> i formant, który wylicza właściwości kolekcji, która jest zwracana przez <xref:EnvDTE._DTE.Windows%2A> właściwość.

```xml
<TextBlock Text="{Binding Path=DTE.Name}" FontSize="12" HorizontalAlignment="Center"/>
<ListBox ItemsSource="{Binding Path=DTE.Windows}">
    <ListBox.ItemTemplate>
        <DataTemplate>
            <TextBlock Text="{Binding Path=Caption}"/>
        </DataTemplate>
    </ListBox.ItemTemplate>
</ListBox
```

 Na przykład zobacz [Przewodnik: Zapisywanie ustawień użytkownika na stronie początkowej](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).

## <a name="see-also"></a>Zobacz też

- [Dodawanie formantu użytkownika do strony początkowej](../extensibility/adding-user-control-to-the-start-page.md)
