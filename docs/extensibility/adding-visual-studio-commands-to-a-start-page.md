---
title: Dodawanie Visual Studio poleceń do strony startowej | Microsoft Docs
description: Poznaj różne sposoby powiązania poleceń Visual Studio obiektami XAML na niestandardowej stronie startowej w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 0bf0f9a3db21dd93b1a497731bca9142a4377acc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901516"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Dodawanie Visual Studio poleceń do strony startowej

Podczas tworzenia niestandardowej strony startowej możesz dodać do Visual Studio polecenia. W tym dokumencie omówiono różne sposoby powiązania poleceń Visual Studio z obiektami XAML na stronie startowej.

Aby uzyskać więcej informacji na temat poleceń w języku XAML, zobacz [Omówienie poleceń](/dotnet/framework/wpf/advanced/commanding-overview)

## <a name="add-commands-from-the-command-well"></a>Dodawanie poleceń z listy poleceń

Na stronie startowej utworzonej w [obszarze Tworzenie niestandardowej strony startowej](../extensibility/creating-a-custom-start-page.md) dodano <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> przestrzenie nazw i w następujący <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> sposób.

```xml
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

Dodaj kolejną przestrzeń nazw Dla Microsoft.VisualStudio.Shell z *zestawuMicrosoft.VisualStudio.Shell.Immutable.11.0.dll*. (Może być konieczne dodanie odwołania do tego zestawu w projekcie).

```xml
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
```

Za pomocą aliasu możesz powiązać polecenia Visual Studio z kontrolkami XAML na stronie, ustawiając właściwość `vscom:` <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> kontrolki na `vscom:VSCommands.ExecuteCommand` . Następnie możesz ustawić właściwość na nazwę polecenia do wykonania, jak <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> pokazano w poniższym przykładzie.

```xml
<Button Name="btnNewProj" Content="New Project"
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
    CommandParameter="File.NewProject" >
</Button>
```

> [!NOTE]
> Alias, `x:` który odwołuje się do schematu XAML, jest wymagany na początku wszystkich poleceń.

 Wartość właściwości można ustawić na dowolne polecenie, do którego można uzyskać dostęp `Command` z okna Polecenia.  Aby uzyskać listę dostępnych poleceń, zobacz [Visual Studio aliasów poleceń](../ide/reference/visual-studio-command-aliases.md).

 Jeśli polecenie do dodania wymaga dodatkowego parametru, możesz dodać go do wartości `CommandParameter` właściwości . Oddziel parametry od poleceń przy użyciu spacji, jak pokazano w poniższym przykładzie.

```xml
<Button Content="Web Search"
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"
        CommandParameter="View.WebBrowser www.bing.com" />
```

### <a name="call-extensions-from-the-command-well"></a>Wywołaj rozszerzenia z listy poleceń
 Polecenia z zarejestrowanych pakietów VSPackage można wywołać przy użyciu tej samej składni, która jest używana do wywołania innych poleceń Visual Studio VSPackage. Jeśli na przykład zainstalowany pakiet VSPackage dodaje polecenie strona główna do menu **Widok,** możesz wywołać to polecenie, ustawiając polecenie na  `CommandParameter` `View.HomePage` .

> [!NOTE]
> Jeśli wywołasz polecenie skojarzone z pakietem VSPackage, pakiet musi zostać załadowany po wywołaniu polecenia.

## <a name="add-commands-from-assemblies"></a>Dodawanie poleceń z zestawów
 Aby wywołać polecenie z zestawu lub uzyskać dostęp do kodu w zestawie VSPackage, który nie jest skojarzony z poleceniem menu, należy utworzyć alias dla zestawu, a następnie wywołać alias.

### <a name="to-call-a-command-from-an-assembly"></a>Aby wywołać polecenie z zestawu

1. W rozwiązaniu dodaj odwołanie do zestawu.

2. W górnej części pliku *StartPage.xaml* dodaj dyrektywę przestrzeni nazw dla zestawu, jak pokazano w poniższym przykładzie.

    ```xml
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
    ```

3. Wywołaj polecenie, `Command` ustawiając właściwość obiektu XAML, jak pokazano w poniższym przykładzie.

     Xaml

    ```
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>
    ```

> [!NOTE]
> Należy skopiować zestaw, a następnie wkleić go w pliku *.. \\ {Visual Studio folder instalacyjny}\Common7\IDE\PrivateAssemblies, aby upewnić się, że został załadowany \* przed jego wywołaniu.

## <a name="add-commands-with-the-dte-object"></a>Dodawanie poleceń za pomocą obiektu DTE
 Dostęp do obiektu DTE można uzyskać ze strony startowej, zarówno w znacznikach, jak i w kodzie.

 W znacznikach można uzyskać do niego dostęp przy użyciu składni rozszerzenia [znaczników powiązania,](/dotnet/framework/wpf/advanced/binding-markup-extension) aby wywołać <xref:EnvDTE.DTE> obiekt . Tego podejścia można użyć do powiązania z prostymi właściwościami, takimi jak te, które zwracają kolekcje, ale nie można powiązać z metodami ani usługami. W poniższym przykładzie przedstawiono kontrolkę, która wiąże się z <xref:System.Windows.Controls.TextBlock> <xref:EnvDTE._DTE.Name%2A> właściwością, oraz kontrolkę, która wylicza właściwości kolekcji zwracane <xref:System.Windows.Controls.ListBox> <xref:EnvDTE.Window.Caption%2A> przez właściwość <xref:EnvDTE._DTE.Windows%2A> .

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

 Aby uzyskać przykład, zobacz [Przewodnik: zapisywanie ustawień użytkownika na stronie startowej.](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)

## <a name="see-also"></a>Zobacz też

- [Dodawanie kontrolki użytkownika do strony startowej](../extensibility/adding-user-control-to-the-start-page.md)
