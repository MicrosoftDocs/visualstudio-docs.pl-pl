---
title: 'Wskazówki: debugowanie szablonu tekstowego uzyskującego dostęp do modelu'
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e33297bba899c1843b8601c031d7669531a1bd3f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546903"
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Wskazówki: debugowanie szablonu tekstowego uzyskującego dostęp do modelu
W przypadku modyfikowania lub dodawania szablonów tekstowych w rozwiązaniu języka specyficznego dla domeny mogą wystąpić błędy, gdy aparat przekształca szablon w kod źródłowy lub kompiluje wygenerowany kod. W poniższym przewodniku przedstawiono niektóre czynności, które można wykonać w celu debugowania szablonu tekstu.

> [!NOTE]
> Aby uzyskać więcej informacji na temat ogólnych szablonów tekstowych, zobacz sekcję [generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md). Aby uzyskać więcej informacji na temat debugowania szablonów tekstowych, zobacz [Przewodnik: Debugowanie szablonu tekstowego](debugging-a-t4-text-template.md).

## <a name="creating-a-domain-specific-language-solution"></a>Tworzenie rozwiązania dotyczącego języka specyficznego dla domeny
 W tej procedurze utworzysz rozwiązanie językowe właściwe dla domeny o następujących cechach:

- Nazwa: DebuggingTestLanguage

- Szablon rozwiązania: minimalny język

- Rozszerzenie pliku: DDD

- Nazwa firmy: fabrikam

  Aby uzyskać więcej informacji na temat tworzenia rozwiązania dotyczącego języka specyficznego dla domeny, zobacz [How to: Create a specyficzne dla domeny rozwiązanie językowe](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="creating-a-text-template"></a>Tworzenie szablonu tekstu
 Dodaj szablon tekstowy do rozwiązania.

#### <a name="to-create-a-text-template"></a>Aby utworzyć szablon tekstowy

1. Skompiluj rozwiązanie i uruchom je w debugerze. (W menu **kompilacja** kliknij pozycję **Kompiluj rozwiązanie**, a następnie w menu **debugowanie** kliknij polecenie **Rozpocznij debugowanie**). Nowe wystąpienie programu Visual Studio otwiera projekt debugowania.

2. Dodaj plik tekstowy o nazwie `DebugTest.tt` do projektu debugowania.

3. Upewnij się, że właściwość **narzędzia niestandardowe** DebugTest.tt jest ustawiona na wartość `TextTemplatingFileGenerator` .

## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Dyrektywy debugowania, które uzyskują dostęp do modelu z szablonu tekstu
 Aby można było uzyskać dostęp do modelu z instrukcji i wyrażeń w szablonie tekstowym, należy najpierw wywołać wygenerowany procesor dyrektywy. Wywołanie wygenerowanego procesora dyrektywy sprawia, że klasy w modelu są dostępne dla kodu szablonu tekstu jako właściwości. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do modeli z szablonów tekstowych](../modeling/accessing-models-from-text-templates.md).

 Poniższe procedury służą do debugowania niepoprawnej nazwy dyrektywy i niepoprawnej nazwy właściwości.

#### <a name="to-debug-an-incorrect-directive-name"></a>Aby debugować niepoprawną nazwę dyrektywy

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

2. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję DebugTest.TT, a następnie kliknij polecenie **Uruchom narzędzie niestandardowe**.

     W oknie **Lista błędów** zostanie wyświetlony następujący błąd:

     **Procesor o nazwie "DebuggingTestLanguageDirectiveProcessor" nie obsługuje dyrektywy o nazwie "modelRoot". Transformacja nie zostanie uruchomiona.**

     W takim przypadku wywołanie dyrektywy zawiera niepoprawną nazwę dyrektywy. Określono `modelRoot` jako nazwę dyrektywy, ale poprawna nazwa dyrektywy to `DebuggingTestLanguage` .

3. Kliknij dwukrotnie błąd w oknie **Lista błędów** , aby przejść do kodu.

4. Aby poprawić kod, Zmień nazwę dyrektywy na `DebuggingTestLanguage` .

     Zmiana zostanie wyróżniona.

    ```csharp
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

    ```vb
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

5. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję DebugTest.TT, a następnie kliknij polecenie **Uruchom narzędzie niestandardowe**.

     Teraz system przekształca szablon tekstowy i generuje odpowiadający mu plik wyjściowy. W oknie **Lista błędów** nie będą widoczne żadne błędy.

#### <a name="to-debug-an-incorrect-property-name"></a>Aby debugować niepoprawną nazwę właściwości

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

2. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję DebugTest.TT, a następnie kliknij polecenie **Uruchom narzędzie niestandardowe**.

     Zostanie wyświetlone okno **Lista błędów** i zostanie wyświetlony jeden z następujących błędów:

     (C#)

     **Kompilowanie transformacji: Microsoft. VisualStudio. TextTemplating \<GUID> . GeneratedTextTransformation "nie zawiera definicji dla elementu" ExampleModel "**

     (Visual Basic)

     **Kompilowanie transformacji: element "ExampleModel" nie jest członkiem elementu "Microsoft. VisualStudio. TextTemplating \<GUID> . GeneratedTextTransformation'.**

     W takim przypadku kod szablonu tekstu zawiera niepoprawną nazwę właściwości. Określono `ExampleModel` jako nazwę właściwości, ale poprawna nazwa właściwości to `LibraryModel` . Poprawna nazwa właściwości znajduje się w parametrze dostarcza, jak pokazano w poniższym kodzie:

    ```
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>
    ```

3. Kliknij dwukrotnie błąd w oknie Lista błędów, aby przejść do kodu.

4. Aby poprawić kod, Zmień nazwę właściwości na `LibraryModel` wartość w kodzie szablonu tekstu.

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

5. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję DebugTest.TT, a następnie kliknij polecenie **Uruchom narzędzie niestandardowe**.

     Teraz system przekształca szablon tekstowy i generuje odpowiadający mu plik wyjściowy. W oknie **Lista błędów** nie będą widoczne żadne błędy.
