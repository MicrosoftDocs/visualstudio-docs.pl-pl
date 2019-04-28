---
title: Dodawanie poleceń programu Visual Studio do strony początkowej | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 638c9c0f0d024830124445485dcf9991678bd4d7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63429012"
---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Dodawanie poleceń programu Visual Studio do strony początkowej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tworząc niestandardową stronę początkową, możesz dodać do niego poleceń programu Visual Studio. W tym dokumencie omówiono różne sposoby, aby powiązać obiekty XAML na stronie początkowej poleceń programu Visual Studio.  
  
 Aby uzyskać więcej informacji na temat poleceń w XAML, zobacz [polecenia — omówienie](http://msdn.microsoft.com/library/bc208dfe-367d-426a-99de-52b7e7511e81)  
  
## <a name="adding-commands-from-the-command-well"></a>Dodawanie poleceń polecenia dobrze  
 Strony początkowej tworzone w [tworzenie niestandardowe strony początkowej](../extensibility/creating-a-custom-start-page.md) dodano <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> i <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> przestrzeni nazw, w następujący sposób.  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Dodaj inny obszar nazw dla Microsoft.VisualStudio.Shell z zestawu Microsoft.VisualStudio.Shell.Immutable.11.0.dll. (Może być konieczne dodanie odwołania do tego zestawu w projekcie).  
  
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
> `x:` Alias, który odwołuje się do schematu XAML, jest wymagany na początku wszystkich poleceń.  
  
 Można ustawić wartość `Command` właściwości do dowolnego polecenia, które są dostępne z **polecenia** okna. Aby uzyskać listę dostępnych poleceń, zobacz [Visual Studio — aliasy poleceń](../ide/reference/visual-studio-command-aliases.md).  
  
 Jeśli polecenie, aby dodać wymagane dodatkowy parametr, można dodać ją do wartości `CommandParameter` właściwości. Oddzielne parametry za pomocą poleceń za pomocą spacji, jak pokazano w poniższym przykładzie.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>Podczas wywoływania rozszerzenia polecenia dobrze  
 Polecenia można wywołać z zarejestrowanych pakietów VSPackage przy użyciu tej samej składni, która służy do wywoływania innych poleceń programu Visual Studio. Na przykład, jeśli dodaje zainstalowanego pakietu VSPackage **strony głównej** polecenie **widoku** menu, można wywołać tego polecenia, ustawiając `CommandParameter` do `View.HomePage`.  
  
> [!NOTE]
> Wywołanie polecenia, który jest skojarzony z pakietu VSPackage można załadować pakietu, gdy polecenie jest wywoływany.  
  
## <a name="adding-commands-from-assemblies"></a>Dodawanie poleceń z zestawów  
 Aby wywołać polecenie z zestawu lub kod dostępu w pakietu VSPackage, który nie jest skojarzony z polecenia menu, możesz utworzyć alias dla zestawu, a następnie wywołać aliasu.  
  
#### <a name="to-call-a-command-from-an-assembly"></a>Aby wywołać polecenie z zestawu  
  
1. W rozwiązaniu Dodaj odwołanie do zestawu.  
  
2. W górnej części pliku StartPage.xaml dodać dyrektywę przestrzeni nazw dla zestawu, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3. Wywołaj polecenie ustawiając `Command` właściwość obiektu XAML, jak pokazano w poniższym przykładzie.  
  
     Xaml  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
> Należy skopiować zestaw, a następnie wklej go w... \\ *Folder instalacji programu visual Studio*\Common7\IDE\PrivateAssemblies\ się upewnić, że jest załadowany, przed jego wywołaniem.  
  
## <a name="adding-commands-with-the-dte-object"></a>Dodawanie poleceń za pomocą obiektu DTE  
 Ze strony Start, zarówno w znaczników i kodu, możesz uzyskać dostęp obiekt DTE.  
  
 W znaczniku, możesz do niego dostęp za pomocą [— rozszerzenie znaczników powiązania](http://msdn.microsoft.com/library/83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63) składnia do wywoływania <xref:EnvDTE.DTE> obiektu. Takie podejście umożliwia powiązania proste właściwości, takie jak te, które zwracają kolekcje, ale nie można powiązać z metody lub usługi. W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.TextBlock> kontrolki, która jest powiązywana z <xref:EnvDTE._DTE.Name%2A> właściwości i <xref:System.Windows.Controls.ListBox> formant, który wylicza <xref:EnvDTE.Window.Caption%2A> właściwości kolekcji, który jest zwracany przez <xref:EnvDTE._DTE.Windows%2A> właściwości.  
  
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
  
 Aby uzyskać przykład, zobacz [instruktażu: Zapisywanie ustawień użytkownika na stronie początkowej](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie kontrolki użytkownika do strony początkowej](../extensibility/adding-user-control-to-the-start-page.md)
