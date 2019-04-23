---
title: 'Przewodnik: Debugowanie szablonu tekstowego uzyskującego dostęp do modelu | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: af46a7fe-6b98-4d3d-b816-0bbf8e81e220
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: eb5a9e6806c76cbb072090c35444d936ce50bb79
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60087121"
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Przewodnik: Debugowanie szablonu tekstowego uzyskującego dostęp do modelu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W przypadku modyfikowania lub dodać szablonów tekstowych w rozwiązaniu języka dotyczącego określonej domeny mogą wystąpić błędy, gdy aparat przekształcenia szablonu do kodu źródłowego lub kompiluje wygenerowanego kodu. Następujące Instruktaż pokazuje niektóre rzeczy, które można zrobić, aby debugowanie szablonu tekstowego.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat tekstu, szablony ogólnie rzecz biorąc, zobacz [generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md). Aby uzyskać więcej informacji na temat debugowania szablonów tekstowych, patrz [instruktażu: Debugowanie szablonu tekstowego](http://msdn.microsoft.com/library/5c3fd3b7-c110-4e86-a22f-d5756be6b94f).  
  
## <a name="creating-a-domain-specific-language-solution"></a>Tworzenie rozwiązania języka dotyczącego określonej domeny  
 Ta procedura służy do tworzenia rozwiązania języka dotyczącego określonej domeny, które ma następujące cechy:  
  
- Nazwa: DebuggingTestLanguage  
  
- Szablon rozwiązania: Minimalny języka  
  
- Rozszerzenie pliku: .ddd  
  
- Nazwa firmy: Fabrikam  
  
  Aby uzyskać więcej informacji na temat tworzenia rozwiązania języka dotyczącego określonej domeny, zobacz [jak: Tworzenie rozwiązania języka dotyczącego określonej domeny](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## <a name="creating-a-text-template"></a>Tworzenie szablonów tekstowych  
 Dodaj szablon tekstowy do rozwiązania.  
  
#### <a name="to-create-a-text-template"></a>Aby utworzyć szablon tekstowy  
  
1. Skompiluj rozwiązanie, a następnie uruchom go w debugerze. (Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**, a następnie na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.) Nowe wystąpienie programu Visual Studio otwiera projekt debugowania.  
  
2. Dodaj plik tekstowy o nazwie `DebugTest.tt` do debugowania projektu.  
  
3. Upewnij się, że **narzędzie niestandardowe** właściwości DebugTest.tt ustawiono `TextTemplatingFileGenerator`.  
  
## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Debugowanie dyrektywy uzyskujących dostęp do modelu z szablonu tekstowego  
 Aby korzystać z modelu, z instrukcji i wyrażeń w szablonie tekstu, najpierw musisz wywołać generowanym procesorem dyrektywy. Wywoływanie generowanym procesorem dyrektywy udostępnia klasy modelu kodu szablonu tekstu jako właściwości. Aby uzyskać więcej informacji, zobacz [uzyskiwania dostępu do modeli z poziomu szablonów tekstu](../modeling/accessing-models-from-text-templates.md).  
  
 W poniższych procedurach będziesz debugował nieprawidłową nazwą dyrektywy i nazwy nieprawidłowe właściwości.  
  
#### <a name="to-debug-an-incorrect-directive-name"></a>Aby debugować z nieprawidłową nazwą dyrektywy  
  
1. Zastąp kod w DebugTest.tt następującym kodem:  
  
    > [!NOTE]
    >  Ten kod zawiera błąd. Błąd są wprowadza w celu jej debugowania.  
  
    ```csharp  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
  
    Model: <#= this.ExampleModel #>  
    <#  
    foreach (ExampleElement element in this.ExampleModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
  
    Model: <#= Me.ExampleModel #>  
    <#  
    For Each element as ExampleElement in Me.ExampleModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy DebugTest.tt, a następnie kliknij przycisk **Uruchom narzędzie niestandardowe**.  
  
     **Lista błędów** okno wyświetla ten błąd:  
  
     **Procesor o nazwie "DebuggingTestLanguageDirectiveProcessor" nie obsługuje dyrektywy o nazwie "modelRoot". Transformacja nie zostanie uruchomiona.**  
  
     W takim przypadku wywołania dyrektywy zawiera nieprawidłową nazwę dyrektywy. Określono `modelRoot` jako nazwa dyrektywy, ale poprawna nazwa dyrektywy `DebuggingTestLanguage`.  
  
3. Kliknij dwukrotnie błąd w **lista błędów** okna, aby przejść do kodu.  
  
4. Aby poprawić ten kod, Zmień nazwę dyrektywy do `DebuggingTestLanguage`.  
  
     Zmiana zostanie wyróżniona.  
  
    ```csharp  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
    ```vb  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
5. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy DebugTest.tt, a następnie kliknij przycisk **Uruchom narzędzie niestandardowe**.  
  
     Teraz system przekształcenia szablonu tekstu i generuje odpowiadający plik danych wyjściowych. Nie zobaczysz żadnych błędów w **lista błędów** okna.  
  
#### <a name="to-debug-an-incorrect-property-name"></a>Aby debugować niepoprawna właściwość nazwy  
  
1. Zastąp kod w DebugTest.tt następującym kodem:  
  
    > [!NOTE]
    >  Ten kod zawiera błąd. Błąd są wprowadza w celu jej debugowania.  
  
    ```csharp  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= this.ExampleModel #>  
    <#  
    foreach (ExampleElement element in this.ExampleModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= Me.ExampleModel #>  
    <#  
    For Each element as ExampleElement in Me.ExampleModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy DebugTest.tt, a następnie kliknij przycisk **Uruchom narzędzie niestandardowe**.  
  
     **Lista błędów** oknie zostanie wyświetlony i jeden z następujących błędów:  
  
     (C#)  
  
     **Kompilowanie transformacji: Microsoft.VisualStudio.TextTemplating\<GUID>. GeneratedTextTransformation "nie zawiera definicji"ExampleModel"**  
  
     (Visual Basic)  
  
     **Kompilowanie transformacji: "ExampleModel" nie jest członkiem "Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation ".**  
  
     W takim wypadku kod szablonu tekstu zawiera nazwę nieprawidłowe właściwości. Określono `ExampleModel` jako nazwa właściwości, ale odpowiedniej właściwości name jest `LibraryModel`. Możesz znaleźć nazwę odpowiedniej właściwości w zawiera parametr, jak pokazano w poniższym kodzie:  
  
    ```  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
    ```  
  
3. Klikaj dwukrotnie poszczególne błędy w oknie Lista błędów, aby przejść do kodu.  
  
4. Aby poprawić ten kod, Zmień nazwę właściwości, aby `LibraryModel` kodu szablonu tekstu.  
  
     Zmiany są wyróżnione.  
  
    ```csharp  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= this.LibraryModel #>  
    <#  
    foreach (ExampleElement element in this.LibraryModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= Me.LibraryModel #>  
    <#  
    For Each element as ExampleElement in Me.LibraryModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
5. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy DebugTest.tt, a następnie kliknij przycisk **Uruchom narzędzie niestandardowe**.  
  
     Teraz system przekształcenia szablonu tekstu i generuje odpowiadający plik danych wyjściowych. Nie zobaczysz żadnych błędów w **lista błędów** okna.
