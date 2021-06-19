---
title: 'Przewodnik: debugowanie szablonów tekstowych, które mają dostęp do modelu'
description: Zawiera informacje na temat sposobu debugowania szablonu tekstowego, który uzyskuje dostęp do modelu.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: d39b1ac72210145cc1efa1c513b7f3b76d8c2e36
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388233"
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Wskazówki: debugowanie szablonu tekstowego uzyskującego dostęp do modelu
Podczas modyfikowania lub dodawania szablonów tekstowych w rozwiązaniu językowym specyficznym dla domeny mogą wystąpić błędy podczas przekształcania szablonu w kod źródłowy lub kompilowania wygenerowanego kodu. W poniższym przewodniku przedstawiono niektóre czynności, które można wykonać w celu debugowania szablonu tekstu.

> [!NOTE]
> Aby uzyskać więcej ogólnych informacji na temat szablonów tekstowych, zobacz [Generowanie kodu i Szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md). Aby uzyskać więcej informacji na temat debugowania szablonów tekstowych, [zobacz Przewodnik: debugowanie szablonu tekstowego.](debugging-a-t4-text-template.md)

## <a name="creating-a-domain-specific-language-solution"></a>Tworzenie Domain-Specific językowego
 W tej procedurze utworzysz rozwiązanie języka specyficzne dla domeny, które ma następujące cechy:

- Nazwa: DebuggingTestLanguage

- Szablon rozwiązania: Minimalny język

- Rozszerzenie pliku: ddd

- Nazwa firmy: Fabrikam

  Aby uzyskać więcej informacji na temat tworzenia rozwiązania językowego specyficznego dla domeny, zobacz How to: Create a Domain-Specific Language Solution (Jak utworzyć rozwiązanie Domain-Specific [językowego).](../modeling/how-to-create-a-domain-specific-language-solution.md)

## <a name="creating-a-text-template"></a>Tworzenie szablonu tekstowego
 Dodaj szablon tekstowy do rozwiązania.

#### <a name="to-create-a-text-template"></a>Aby utworzyć szablon tekstowy

1. Skompilowanie rozwiązania i uruchomienie go w debugerze. (W menu **Build (Kompilacja)** kliknij pozycję **Rebuild Solution (Skompilowanie** rozwiązania), a następnie w menu **Debug (Debugowanie)** kliknij pozycję **Start Debugging (Rozpocznij debugowanie).** Nowe wystąpienie klasy Visual Studio projekt Debugowanie.

2. Dodaj plik tekstowy o `DebugTest.tt` nazwie do projektu Debugowanie.

3. Upewnij się, **że właściwość Narzędzia** niestandardowe DebugTest.tt jest ustawiona na wartość `TextTemplatingFileGenerator` .

## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Dyrektywy debugowania, które mają dostęp do modelu z szablonu tekstowego
 Zanim będzie można uzyskać dostęp do modelu z instrukcji i wyrażeń w szablonie tekstowym, należy najpierw wywołać wygenerowany procesor dyrektywy. Wywołanie wygenerowanego procesora dyrektywy sprawia, że klasy w modelu są dostępne dla kodu szablonu tekstu jako właściwości. Aby uzyskać więcej informacji, zobacz [Accessing Models from Text Templates (Uzyskiwanie dostępu do modeli z szablonów tekstowych).](../modeling/accessing-models-from-text-templates.md)

 W poniższych procedurach będziesz debugować nieprawidłową nazwę dyrektywy i nieprawidłową nazwę właściwości.

#### <a name="to-debug-an-incorrect-directive-name"></a>Aby debugować nieprawidłową nazwę dyrektywy

1. Zastąp kod w DebugTest.tt następującym kodem:

    > [!NOTE]
    > Kod zawiera błąd. Wprowadzasz błąd w celu debugowania.

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

2. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję DebugTest.tt, a następnie kliknij polecenie **Uruchom narzędzie niestandardowe.**

     W **oknie Lista błędów** jest wyświetlany ten błąd:

     **Procesor o nazwie "DebuggingTestLanguageDirectiveProcessor" nie obsługuje dyrektywy o nazwie "modelRoot". Przekształcenie nie zostanie uruchomione.**

     W tym przypadku wywołanie dyrektywy zawiera nieprawidłową nazwę dyrektywy. Określono nazwę `modelRoot` dyrektywy, ale poprawną nazwą dyrektywy jest `DebuggingTestLanguage` .

3. Kliknij dwukrotnie błąd w **oknie Lista błędów,** aby przejść do kodu.

4. Aby poprawić kod, zmień nazwę dyrektywy na `DebuggingTestLanguage` .

     Zmiana zostanie wyróżniona.

    ```csharp
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

    ```vb
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

5. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję DebugTest.tt, a następnie kliknij polecenie **Uruchom narzędzie niestandardowe.**

     Teraz system przekształca szablon tekstowy i generuje odpowiedni plik wyjściowy. W oknie Lista błędów nie będą **pojawiać się żadne** błędy.

#### <a name="to-debug-an-incorrect-property-name"></a>Aby debugować nieprawidłową nazwę właściwości

1. Zastąp kod w DebugTest.tt następującym kodem:

    > [!NOTE]
    > Kod zawiera błąd. Wprowadzasz błąd w celu debugowania.

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

2. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję DebugTest.tt, a następnie kliknij polecenie **Uruchom narzędzie niestandardowe.**

     Zostanie **wyświetlone okno Lista** błędów z wyświetlonym jednym z tych błędów:

     (C#)

     **Przekształcanie kompilowania: Microsoft.VisualStudio.TextTemplating \<GUID> . GeneratedTextTransformation" nie zawiera definicji dla "ExampleModel"**

     (Visual Basic)

     **Przekształcanie kompilowania: "ExampleModel" nie jest członkiem "Microsoft.VisualStudio.TextTemplating" \<GUID> . GeneratedTextTransformation".**

     W tym przypadku kod szablonu tekstu zawiera nieprawidłową nazwę właściwości. Określono nazwę `ExampleModel` właściwości, ale poprawną nazwą właściwości jest `LibraryModel` . Poprawną nazwę właściwości można znaleźć w parametrze provides, jak pokazano w poniższym kodzie:

    ```
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>
    ```

3. Kliknij dwukrotnie błąd w oknie Lista błędów, aby przejść do kodu.

4. Aby poprawić kod, zmień nazwę właściwości na `LibraryModel` w kodzie szablonu tekstu.

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

5. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję DebugTest.tt, a następnie kliknij polecenie **Uruchom narzędzie niestandardowe.**

     Teraz system przekształca szablon tekstowy i generuje odpowiedni plik wyjściowy. W oknie Lista błędów nie będą **pojawiać się żadne** błędy.
