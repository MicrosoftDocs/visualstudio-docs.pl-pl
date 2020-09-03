---
title: Dodawanie poleceń programu Visual Studio do strony startowej | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80740111"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Dodawanie poleceń programu Visual Studio do strony początkowej

Podczas tworzenia niestandardowej strony początkowej można dodać do niej polecenia programu Visual Studio. W tym dokumencie omówiono różne sposoby powiązania poleceń programu Visual Studio z obiektami XAML na stronie startowej.

Aby uzyskać więcej informacji na temat poleceń w języku XAML, zobacz [Omówienie poleceń](/dotnet/framework/wpf/advanced/commanding-overview)

## <a name="add-commands-from-the-command-well"></a>Dodawanie poleceń z poziomu polecenia

Strona startowa utworzona w obszarze [Utwórz niestandardową stronę początkową](../extensibility/creating-a-custom-start-page.md) dodała <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> przestrzenie nazw i w następujący sposób.

```xml
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

Dodaj kolejną przestrzeń nazw dla elementu Microsoft. VisualStudio. Shell z zestawu *Microsoft.VisualStudio.Shell.Immutable.11.0.dll*. (Może być konieczne dodanie odwołania do tego zestawu w projekcie).

```xml
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
```

Możesz użyć `vscom:` aliasu, aby powiązać polecenia programu Visual Studio z kontrolkami XAML na stronie przez ustawienie <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> właściwości kontrolki na `vscom:VSCommands.ExecuteCommand` . Następnie można ustawić <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> Właściwość na nazwę polecenia, które ma zostać wykonane, jak pokazano w poniższym przykładzie.

```xml
<Button Name="btnNewProj" Content="New Project"
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
    CommandParameter="File.NewProject" >
</Button>
```

> [!NOTE]
> `x:`Alias, który odwołuje się do schematu XAML, jest wymagany na początku wszystkich poleceń.

 Można ustawić wartość `Command` właściwości na dowolne polecenie, do którego można uzyskać dostęp z okna **poleceń** . Listę dostępnych poleceń można znaleźć w temacie [Aliasy poleceń programu Visual Studio](../ide/reference/visual-studio-command-aliases.md).

 Jeśli polecenie do dodania wymaga dodatkowego parametru, można dodać go do wartości `CommandParameter` właściwości. Oddziel parametry od poleceń przy użyciu spacji, jak pokazano w poniższym przykładzie.

```xml
<Button Content="Web Search"
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"
        CommandParameter="View.WebBrowser www.bing.com" />
```

### <a name="call-extensions-from-the-command-well"></a>Wywoływanie rozszerzeń z poziomu polecenia
 Polecenia z zarejestrowanych pakietów VSPackage można wywołać za pomocą tej samej składni, która jest używana do wywoływania innych poleceń programu Visual Studio. Na przykład jeśli zainstalowana pakietu VSPackage dodaje polecenie **strony głównej** do menu **Widok** , można wywołać to polecenie, ustawiając wartość `CommandParameter` `View.HomePage` .

> [!NOTE]
> Jeśli wywołasz polecenie, które jest skojarzone z pakietu VSPackage, pakiet musi zostać załadowany, gdy polecenie jest wywoływane.

## <a name="add-commands-from-assemblies"></a>Dodawanie poleceń z zestawów
 Aby wywołać polecenie z zestawu lub uzyskać dostęp do kodu w pakietu VSPackage, który nie jest skojarzony z poleceniem menu, należy utworzyć alias dla zestawu, a następnie wywołać alias.

### <a name="to-call-a-command-from-an-assembly"></a>Aby wywołać polecenie z zestawu

1. W rozwiązaniu Dodaj odwołanie do zestawu.

2. W górnej części pliku *Startpage. XAML* Dodaj dyrektywę Namespace dla zestawu, jak pokazano w poniższym przykładzie.

    ```xml
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
    ```

3. Wywołaj polecenie, ustawiając `Command` właściwość obiektu XAML, jak pokazano w poniższym przykładzie.

     Formatu

    ```
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>
    ```

> [!NOTE]
> Musisz skopiować zestaw, a następnie wkleić go w *.. \\ {Folder instalacyjny programu Visual Studio} \Common7\IDE\PrivateAssemblies, \* Aby upewnić się, że jest załadowany przed wywołaniem.

## <a name="add-commands-with-the-dte-object"></a>Dodawanie poleceń z obiektem DTE
 Dostęp do obiektu DTE można uzyskać ze strony początkowej, zarówno w znacznikach, jak i w kodzie.

 W znaczniku można uzyskać do niego dostęp przy użyciu składni [rozszerzenia znaczników powiązań](/dotnet/framework/wpf/advanced/binding-markup-extension) do wywołania <xref:EnvDTE.DTE> obiektu. Tego podejścia można użyć do powiązania z prostymi właściwościami, takimi jak te, które zwracają kolekcje, ale nie można powiązać z metodami lub usługami. Poniższy przykład pokazuje <xref:System.Windows.Controls.TextBlock> kontrolkę, która jest powiązana z <xref:EnvDTE._DTE.Name%2A> właściwością, oraz <xref:System.Windows.Controls.ListBox> formant, który wylicza <xref:EnvDTE.Window.Caption%2A> właściwości kolekcji zwracanej przez <xref:EnvDTE._DTE.Windows%2A> Właściwość.

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

 Aby zapoznać się z przykładem, zobacz [Przewodnik: zapisywanie ustawień użytkownika na stronie startowej](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).

## <a name="see-also"></a>Zobacz też

- [Dodawanie kontrolki użytkownika do strony początkowej](../extensibility/adding-user-control-to-the-start-page.md)
