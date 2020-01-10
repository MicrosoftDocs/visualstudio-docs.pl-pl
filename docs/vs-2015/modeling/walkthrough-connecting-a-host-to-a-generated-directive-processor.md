---
title: 'Przewodnik: łączenie hosta z wygenerowanym procesorem dyrektywy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
ms.assetid: 254540d9-90d6-42de-8c1c-068affd56e83
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 47e1b1f11fd885afbb5e84e1530a171442938af0
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851294"
---
# <a name="walkthrough-connecting-a-host-to-a-generated-directive-processor"></a>Wskazówki: łączenie hosta z generowanym procesorem dyrektywy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można napisać własnego hosta, który przetwarza szablony tekstowe. Podstawowy Host niestandardowy jest prezentowany w [przewodniku: Tworzenie niestandardowego hosta szablonu tekstu](../modeling/walkthrough-creating-a-custom-text-template-host.md). Ten host można rozłożyć, aby dodać funkcje, takie jak generowanie wielu plików wyjściowych.

 W tym instruktażu rozwiniesz niestandardowego hosta, aby obsługiwał szablony tekstowe, które wywołują procesory dyrektywy. Podczas definiowania języka specyficznego dla domeny generuje on *procesor dyrektywy* dla modelu domeny. Procesor dyrektywy ułatwia użytkownikom pisanie szablonów, które uzyskują dostęp do modelu, co zmniejsza konieczność pisania dyrektyw zestawu i importowania w szablonach.

> [!WARNING]
> Ten przewodnik kompiluje [Przewodnik: Tworzenie niestandardowego hosta szablonu tekstu](../modeling/walkthrough-creating-a-custom-text-template-host.md). Najpierw wykonaj ten przewodnik.

 Ten instruktaż zawiera następujące zagadnienia:

- Użycie [!INCLUDE[dsl](../includes/dsl-md.md)] do wygenerowania procesora dyrektywy, który jest oparty na modelu domeny.

- Łączenie hosta niestandardowego szablonu tekstu z wygenerowanym procesorem dyrektywy.

- Testowanie hosta niestandardowego z wygenerowanym procesorem dyrektywy.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby zdefiniować DSL, musisz mieć zainstalowane następujące składniki:

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](https://docs.microsoft.com/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts)|
|{1&gt;{2&gt;Visual Studio Visualisation i Modeling SDK&lt;2}&lt;1}|[http://go.microsoft.com/fwlink/?LinkID=186128](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples)|

 Ponadto musisz mieć niestandardowe przekształcenia szablonu tekstu utworzonego w [przewodniku: Tworzenie niestandardowego hosta szablonu tekstu](../modeling/walkthrough-creating-a-custom-text-template-host.md).

## <a name="using-domain-specific-language-tools-to-generate-a-directive-processor"></a>Generowanie procesora dyrektywy przy użyciu narzędzia języka specyficznego dla domeny
 W tym instruktażu użyjesz kreatora projektant języka specyficznego dla domeny, aby utworzyć język specyficzny dla domeny dla rozwiązania DSLMinimalTest.

#### <a name="to-use-domain-specific-language-tools-to-generate-a-directive-processor-that-is-based-on-a-domain-model"></a>Aby użyć narzędzia języka specyficznego dla domeny do wygenerowania procesora dyrektywy, który jest oparty na modelu domeny

1. Utwórz rozwiązanie w języku specyficznym dla domeny, które ma następujące cechy:

   - Nazwa: DSLMinimalTest

   - Szablon rozwiązania: minimalny język

   - Rozszerzenie pliku: min

   - Nazwa firmy: fabrikam

     Aby uzyskać więcej informacji na temat tworzenia rozwiązania dotyczącego języka specyficznego dla domeny, zobacz [How to: Create a specyficzne dla domeny rozwiązanie językowe](../modeling/how-to-create-a-domain-specific-language-solution.md).

2. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

   > [!IMPORTANT]
   > Ten krok powoduje wygenerowanie procesora dyrektywy i dodanie klucza do niego w rejestrze.

3. Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.

    Zostanie otwarte drugie wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

4. W przypadku kompilacji eksperymentalnej w **Eksplorator rozwiązań**kliknij dwukrotnie plik **Sample. min**.

    Plik zostanie otwarty w projektancie. Należy zauważyć, że model ma dwa elementy, ExampleElement1 i ExampleElement2, oraz link między nimi.

5. Zamknij drugie wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

6. Zapisz rozwiązanie, a następnie zamknij projektant języka specyficznego dla domeny.

## <a name="connecting-a-custom-text-template-host-to-a-directive-processor"></a>Łączenie hosta niestandardowego szablonu tekstu z procesorem dyrektywy
 Po wygenerowaniu procesora dyrektywy należy podłączyć procesor dyrektywy i hosta niestandardowego szablonu tekstu, który został utworzony w [przewodniku: Tworzenie niestandardowego hosta szablonu tekstu](../modeling/walkthrough-creating-a-custom-text-template-host.md).

#### <a name="to-connect-a-custom-text-template-host-to-the-generated-directive-processor"></a>Aby połączyć hosta niestandardowego szablonu tekstu z wygenerowanym procesorem dyrektywy

1. Otwórz rozwiązanie CustomHost.

2. W menu **projekt** kliknij polecenie **Dodaj odwołanie**.

     Zostanie otwarte okno dialogowe **Dodawanie odwołania** z wyświetlaną kartą **.NET** .

3. Dodaj następujące odwołania:

    - Microsoft.VisualStudio.Modeling.Sdk.11.0

    - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0

    - Microsoft.VisualStudio.TextTemplating.11.0

    - Microsoft.VisualStudio.TextTemplating.Interfaces.11.0

    - Microsoft.VisualStudio.TextTemplating.Modeling.11.0

    - Microsoft.VisualStudio.TextTemplating.VSHost.11.0

4. W górnej części Program.cs lub Module1. vb Dodaj następujący wiersz kodu:

    ```csharp
    using Microsoft.Win32;
    ```

    ```vb
    Imports Microsoft.Win32
    ```

5. Znajdź kod właściwości `StandardAssemblyReferences`i zastąp go następującym kodem:

    > [!NOTE]
    > W tym kroku dodasz odwołania do zestawów, które są wymagane przez wygenerowany procesor dyrektywy, który będzie obsługiwany przez hosta.

    ```csharp
    //the host can provide standard assembly references
    //the engine will use these references when compiling and
    //executing the generated transformation class
    //--------------------------------------------------------------
    public IList<string> StandardAssemblyReferences
    {
        get
        {
            return new string[]
            {
                //if this host searches standard paths and the GAC
                //we can specify the assembly name like this:
                //"System"
                //since this host only resolves assemblies from the
                //fully qualified path and name of the assembly
                //this is a quick way to get the code to give us the
                //fully qualified path and name of the System assembly
                //---------------------------------------------------------
                typeof(System.Uri).Assembly.Location,
                            typeof(System.Uri).Assembly.Location,
                typeof(Microsoft.VisualStudio.Modeling.ModelElement).Assembly.Location,
                typeof(Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape).Assembly.Location,
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating).Assembly.Location,
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation).Assembly.Location

            };
        }
    }
    ```

6. Znajdź kod dla funkcji `ResolveDirectiveProcessor`i zastąp go następującym kodem:

    > [!IMPORTANT]
    > Ten kod zawiera zakodowane odwołania do nazwy wygenerowanego procesora dyrektywy, z którym chcesz się połączyć. Można to łatwo zrobić, a w tym przypadku sprawdza wszystkie procesory dyrektywy wymienione w rejestrze i próbuje znaleźć dopasowanie. W takim przypadku host będzie działał z dowolnym wygenerowanym procesorem dyrektywy.

    ```csharp
    //the engine calls this method based on the directives the user has
            //specified it in the text template
            //this method can be called 0, 1, or more times
            //---------------------------------------------------------------------
            public Type ResolveDirectiveProcessor(string processorName)
            {
                //check the processor name, and if it is the name of the processor the
                //host wants to support, return the type of the processor
                //---------------------------------------------------------------------
                if (string.Compare(processorName, "DSLMinimalTestDirectiveProcessor", StringComparison.InvariantCultureIgnoreCase) == 0)
                {
                    try
                    {
                        string keyName = @"Software\Microsoft\VisualStudio\10.0Exp_Config\TextTemplating\DirectiveProcessors\DSLMinimalTestDirectiveProcessor";
                        using (RegistryKey specificKey = Registry.CurrentUser.OpenSubKey(keyName))
                        {
                            if (specificKey != null)
                            {
                                List<string> names = new List<String>(specificKey.GetValueNames());
                                string classValue = specificKey.GetValue("Class") as string;
                                if (!string.IsNullOrEmpty(classValue))
                                {
                                    string loadValue = string.Empty;
                                    System.Reflection.Assembly processorAssembly = null;
                                    if (names.Contains("Assembly"))
                                    {
                                        loadValue = specificKey.GetValue("Assembly") as string;
                                        if (!string.IsNullOrEmpty(loadValue))
                                        {
                                            //the assembly must be installed in the GAC
                                            processorAssembly = System.Reflection.Assembly.Load(loadValue);
                                        }
                                    }
                                    else if (names.Contains("CodeBase"))
                                    {
                                        loadValue = specificKey.GetValue("CodeBase") as string;
                                        if (!string.IsNullOrEmpty(loadValue))
                                        {
                                            //loading local assembly
                                            processorAssembly = System.Reflection.Assembly.LoadFrom(loadValue);
                                        }
                                    }
                                    if (processorAssembly == null)
                                    {
                                        throw new Exception("Directive Processor not found");
                                    }
                                    Type processorType = processorAssembly.GetType(classValue);
                                    if (processorType == null)
                                    {
                                        throw new Exception("Directive Processor not found");
                                    }
                                    return processorType;
                                }
                            }
                        }
                    }
                    catch (Exception e)
                    {
                        //if the directive processor can not be found, throw an error
                        throw new Exception("Directive Processor not found");
                    }
                }

                //if the directive processor is not one this host wants to support
                throw new Exception("Directive Processor not supported");
            }
    ```

7. Na **pliku** menu, kliknij przycisk **Zapisz wszystko**.

8. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

## <a name="testing-the-custom-host-with-the-directive-processor"></a>Testowanie hosta niestandardowego z procesorem dyrektywy
 Aby przetestować hosta niestandardowego tekstu, najpierw należy napisać szablon tekstu, który wywołuje wygenerowany procesor dyrektywy. Następnie uruchom hosta niestandardowego, przekaż go do nazwy szablonu tekstu i sprawdź, czy dyrektywa została przetworzona prawidłowo.

#### <a name="to-create-a-text-template-to-test-the-custom-host"></a>Aby utworzyć szablon tekstowy w celu przetestowania niestandardowego hosta

1. Utwórz plik tekstowy i nadaj mu nazwę `TestTemplateWithDP.tt`. Do utworzenia pliku można użyć dowolnego edytora tekstu, takiego jak Notatnik.

2. Dodaj następującą zawartość do pliku tekstowego:

    > [!NOTE]
    > Język programowania szablonu tekstu nie musi być zgodny z tym hostem niestandardowym.

    ```csharp
    Text Template Host Test

    <#@ template debug="true" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
    <# //this is the call to the examplemodel directive in the generated directive processor #>
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>
    <# //uncomment this line to test that the host allows the engine to set the extension #>
    <# //@ output extension=".htm" #>

    <# //uncomment this line if you want to see the generated transformation class #>
    <# //System.Diagnostics.Debugger.Break(); #>
    <# //this code uses the results of the examplemodel directive #>
    <#
        foreach ( ExampleElement box in this.ExampleModel.Elements )
        {
            WriteLine("Box: {0}", box.Name);

            foreach (ExampleElement linkedTo in box.Targets)
            {
                WriteLine("Linked to: {0}", linkedTo.Name);
            }

            foreach (ExampleElement linkedFrom in box.Sources)
            {
                WriteLine("Linked from: {0}", linkedFrom.Name);
            }

            WriteLine("");
        }
    #>
    ```

    ```vb
    Text Template Host Test

    <#@ template debug="true" language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>

    <# 'this is the call to the examplemodel directive in the generated directive processor #>
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>

    <# 'Uncomment this line to test that the host allows the engine to set the extension. #>
    <# '@ output extension=".htm" #>

    <# 'Uncomment this line if you want to see the generated transformation class. #>
    <# 'System.Diagnostics.Debugger.Break() #>

    <# 'this code uses the results of the examplemodel directive #>

    <#
       For Each box as ExampleElement In Me.ExampleModel.Elements

           WriteLine("Box: {0}", box.Name)

            For Each LinkedTo as ExampleElement In box.Targets
                WriteLine("Linked to: {0}", LinkedTo.Name)
            Next

            For Each LinkedFrom as ExampleElement In box.Sources
                WriteLine("Linked from: {0}", LinkedFrom.Name)
            Next

            WriteLine("")

       Next
    #>
    ```

3. W kodzie Zastąp \<ścieżkę > ścieżką pliku Sample. min z języka specyficznego dla projektu utworzonego w pierwszej procedurze.

4. Zapisz i zamknij plik.

#### <a name="to-test-the-custom-host"></a>Aby przetestować niestandardowego hosta

1. Otwórz okno wiersza polecenia.

2. Wpisz ścieżkę pliku wykonywalnego dla niestandardowego hosta, ale nie naciskaj jeszcze ENTER.

     Na przykład wpisz:

     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`

    > [!NOTE]
    > Zamiast wpisywać adres, możesz przejść do pliku CustomHost. exe w **Eksploratorze Windows**, a następnie przeciągnąć plik do okna wiersza polecenia.

3. Wpisz spację.

4. Wpisz ścieżkę do pliku szablonu tekstu, a następnie naciśnij ENTER.

     Na przykład wpisz:

     `<YOUR PATH>TestTemplateWithDP.txt`

    > [!NOTE]
    > Zamiast wpisywać adres, możesz przejść do pliku TestTemplateWithDP. txt w **Eksploratorze Windows**, a następnie przeciągnąć plik do okna wiersza polecenia.

     Niestandardowa aplikacja hosta uruchamia proces transformacji szablonu tekstu.

5. W **Eksploratorze Windows**przejdź do folderu, który zawiera plik TestTemplateWithDP. txt.

     Folder zawiera również plik TestTemplateWithDP1. txt.

6. Otwórz ten plik, aby zobaczyć wyniki przekształcenia szablonu tekstu.

     Wyniki wygenerowanego tekstu wyjściowego są wyświetlane i powinny wyglądać następująco:

    ```
    Text Template Host Test

    Box: ExampleElement1
    Linked to: ExampleElement2

    Box: ExampleElement2
    Linked from: ExampleElement1
    ```

## <a name="see-also"></a>Zobacz też
 [Przewodnik: Tworzenie niestandardowego hosta szablonu tekstowego](../modeling/walkthrough-creating-a-custom-text-template-host.md)
