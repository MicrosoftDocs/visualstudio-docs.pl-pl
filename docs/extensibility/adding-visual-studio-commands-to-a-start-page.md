---
title: Dodawanie poleceń programu Visual Studio do strony początkowej | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 499b6cb593dd29d9bd881203daab19fc319ff1a7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53902457"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Dodawanie poleceń programu Visual Studio do strony początkowej
Podczas tworzenia niestandardowej strony początkowej poleceń programu Visual Studio można dodać do niego. W tym dokumencie omówiono różne sposoby, aby powiązać obiekty XAML na stronie sieci uruchomić poleceń programu Visual Studio.  
  
 Aby uzyskać więcej informacji na temat poleceń w XAML, zobacz [Commanding — omówienie](/dotnet/framework/wpf/advanced/commanding-overview)  
  
## <a name="add-commands-from-the-command-well"></a>Dodawanie poleceń polecenia dobrze  
 Strona startowa utworzone w [Tworzenie niestandardowej strony początkowej](../extensibility/creating-a-custom-start-page.md) dodano <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> i <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> przestrzeni nazw, w następujący sposób.  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Dodawanie innej przestrzeni nazw dla Microsoft.VisualStudio.Shell z zestawu *Microsoft.VisualStudio.Shell.Immutable.11.0.dll*. (Może być konieczne dodanie odwołania do tego zestawu w projekcie).  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 Możesz użyć `vscom:` alias, aby powiązać polecenia programu Visual Studio XAML kontrolki na stronie przez ustawienie <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> właściwości formantu, aby `vscom:VSCommands.ExecuteCommand`. Następnie można ustawić <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> właściwość na nazwę polecenia do wykonania, jak pokazano w poniższym przykładzie.  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  `x:` Alias, który odwołuje się do schematu XAML, jest wymagany na początku wszystkich poleceń.  
  
 Można ustawić wartość `Command` właściwości do dowolnego polecenia, które są dostępne z **polecenia** okna. Aby uzyskać listę dostępnych poleceń, zobacz [Visual Studio — aliasy poleceń](../ide/reference/visual-studio-command-aliases.md).  
  
 Jeśli polecenie, aby dodać wymagane dodatkowy parametr, można dodać ją do wartości `CommandParameter` właściwości. Oddzielne parametry za pomocą poleceń za pomocą spacji, jak pokazano w poniższym przykładzie.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="call-extensions-from-the-command-well"></a>Również wywołać rozszerzenia polecenia  
 Polecenia można wywołać z zarejestrowanych pakietów VSPackage przy użyciu tej samej składni, która służy do wywoływania innych poleceń programu Visual Studio. Na przykład, jeśli dodaje zainstalowanego pakietu VSPackage **strony głównej** polecenie **widoku** menu, można wywołać tego polecenia, ustawiając `CommandParameter` do `View.HomePage`.  
  
> [!NOTE]
>  Wywołanie polecenia, który jest skojarzony z pakietu VSPackage można załadować pakietu, gdy polecenie jest wywoływany.  
  
## <a name="add-commands-from-assemblies"></a>Dodawanie poleceń z zestawów  
 Aby wywołać polecenie z zestawu lub kod dostępu w pakietu VSPackage, który nie jest skojarzony z polecenia menu, możesz utworzyć alias dla zestawu, a następnie wywołać aliasu.  
  
### <a name="to-call-a-command-from-an-assembly"></a>Aby wywołać polecenie z zestawu  
  
1.  W rozwiązaniu Dodaj odwołanie do zestawu.  
  
2.  W górnej części *StartPage.xaml* pliku, dodać dyrektywę przestrzeni nazw dla zestawu, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  Wywołaj polecenie ustawiając `Command` właściwość obiektu XAML, jak pokazano w poniższym przykładzie.  
  
     XAML  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  Należy skopiować zestaw, a następnie wklej go w *... \\\Common7\IDE\PrivateAssemblies {folder instalacji programu visual Studio}\* się upewnić, że jest załadowany, przed jego wywołaniem.  
  
## <a name="add-commands-with-the-dte-object"></a>Dodawanie poleceń za pomocą obiektu DTE  
 Ze strony Start, zarówno w znaczników i kodu, możesz uzyskać dostęp obiekt DTE.  
  
 W znaczniku, możesz do niego dostęp za pomocą [— rozszerzenie znaczników powiązania](/dotnet/framework/wpf/advanced/binding-markup-extension) składnia do wywoływania <xref:EnvDTE.DTE> obiektu. Takie podejście umożliwia powiązania proste właściwości, takie jak te, które zwracają kolekcje, ale nie można powiązać z metody lub usługi. W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.TextBlock> kontrolki, która jest powiązywana z <xref:EnvDTE._DTE.Name%2A> właściwości i <xref:System.Windows.Controls.ListBox> formant, który wylicza <xref:EnvDTE.Window.Caption%2A> właściwości kolekcji, który jest zwracany przez <xref:EnvDTE._DTE.Windows%2A> właściwości.  
  
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
  
 Aby uzyskać przykład, zobacz [instruktażu: Zapisywanie ustawień użytkownika na stronie sieci uruchomić](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Dodawanie kontrolki użytkownika do strony początkowej](../extensibility/adding-user-control-to-the-start-page.md)