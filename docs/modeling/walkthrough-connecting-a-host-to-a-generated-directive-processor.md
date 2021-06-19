---
title: Łączenie hosta z wygenerowanym procesorem dyrektywy
description: Dowiedz się, jak rozszerzyć niestandardowego hosta tak, aby obsługujeł szablony tekstowe, które wywołują procesory dyrektyw.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
dev_langs:
- CSharp
- VB
ms.openlocfilehash: ed51688e5b65e34d7067963dbf7b839b1f022768
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388324"
---
# <a name="walkthrough-connect-a-host-to-a-generated-directive-processor"></a>Przewodnik: łączenie hosta z wygenerowanym procesorem dyrektywy

Możesz napisać własnego hosta, który przetwarza szablony tekstowe. Podstawowy host niestandardowy został zademonstrowany w [przewodniku: Tworzenie niestandardowego hosta szablonu tekstowego.](../modeling/walkthrough-creating-a-custom-text-template-host.md) Możesz rozszerzyć tego hosta, aby dodać funkcje, takie jak generowanie wielu plików wyjściowych.

W tym przewodniku rozszerzysz niestandardowy host tak, aby obsługujeł szablony tekstowe, które wywołują procesory dyrektyw. Podczas definiowania języka specyficznego dla domeny generuje procesor *dyrektywy* dla modelu domeny. Procesor dyrektywy ułatwia użytkownikom pisanie szablonów, które mają dostęp do modelu, co zmniejsza potrzebę pisania dyrektyw zestawu i importu w szablonach.

> [!NOTE]
> Ten przewodnik jest kompilowany w oparciu [o przewodnik: tworzenie niestandardowego hosta szablonu tekstu.](../modeling/walkthrough-creating-a-custom-text-template-host.md) Najpierw wykonaj ten przewodnik.

Ten instruktaż zawiera następujące zagadnienia:

- Przy [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] użyciu do generowania procesora dyrektywy, który jest oparty na modelu domeny.

- Łączenie niestandardowego hosta szablonu tekstu z wygenerowanym procesorem dyrektywy.

- Testowanie niestandardowego hosta za pomocą wygenerowanego procesora dyrektywy.

## <a name="prerequisites"></a>Wymagania wstępne

Aby zdefiniować DSL, musisz mieć zainstalowane następujące składniki:

| Składnik | Link |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index) |
| Visual Studio SDK wizualizacji i modelowania | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Ponadto musisz mieć utworzone przekształcenie niestandardowego szablonu tekstu w [przewodniku: tworzenie niestandardowego hosta szablonu tekstu.](../modeling/walkthrough-creating-a-custom-text-template-host.md)

## <a name="use-domain-specific-language-tools-to-generate-a-directive-processor"></a>Używanie Domain-Specific języka do generowania procesora dyrektywy

W tym przewodniku użyjemy kreatora projektanta języka Domain-Specific, aby utworzyć język specyficzny dla domeny dla rozwiązania DSLMinimalTest.

1. Utwórz rozwiązanie języka specyficzne dla domeny, które ma następujące cechy:

   - Nazwa: DSLMinimalTest

   - Szablon rozwiązania: Minimalny język

   - Rozszerzenie pliku: min

   - Nazwa firmy: Fabrikam

   Aby uzyskać więcej informacji na temat tworzenia rozwiązania językowego specyficznego dla domeny, zobacz How to: Create a Domain-Specific Language Solution (Jak utworzyć rozwiązanie Domain-Specific [językowego).](../modeling/how-to-create-a-domain-specific-language-solution.md)

2. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

   > [!IMPORTANT]
   > Ten krok generuje procesor dyrektywy i dodaje klucz dla niego w rejestrze.

3. W menu **Debugowanie** kliknij polecenie **Rozpocznij debugowanie**.

    Zostanie otwarte drugie Visual Studio aplikacji.

4. W kompilacji eksperymentalnej w **Eksplorator rozwiązań** kliknij dwukrotnie plik **sample.min.**

    Plik zostanie otwarty w projektancie. Zwróć uwagę, że model ma dwa elementy: ExampleElement1 i ExampleElement2 oraz połączenie między nimi.

5. Zamknij drugie wystąpienie Visual Studio.

6. Zapisz rozwiązanie, a następnie zamknij Domain-Specific Language Designer.

## <a name="connect-a-custom-text-template-host-to-a-directive-processor"></a>Łączenie niestandardowego hosta szablonu tekstu z procesorem dyrektywy

Po wygenerowaniu procesora dyrektywy połącz procesor dyrektywy i niestandardowego hosta szablonu tekstu utworzonego w [przewodniku: Tworzenie](../modeling/walkthrough-creating-a-custom-text-template-host.md)niestandardowego hosta szablonu tekstu.

1. Otwórz rozwiązanie CustomHost.

2. W menu **Project (Projekt)** kliknij pozycję **Add Reference (Dodaj odwołanie).**

     Zostanie **otwarte okno dialogowe** Dodawanie odwołania z wyświetloną **kartą .NET.**

3. Dodaj następujące odwołania:

    - Microsoft.VisualStudio.Modeling.Sdk.11.0

    - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0

    - Microsoft.VisualStudio.TextTemplating.11.0

    - Microsoft.VisualStudio.TextTemplating.Interfaces.11.0

    - Microsoft.VisualStudio.TextTemplating.Modeling.11.0

    - Microsoft.VisualStudio.TextTemplating.VSHost.11.0

4. W górnej części programu Program.cs lub Module1.vb dodaj następujący wiersz kodu:

    ```csharp
    using Microsoft.Win32;
    ```

    ```vb
    Imports Microsoft.Win32
    ```

5. Znajdź kod właściwości `StandardAssemblyReferences` i zastąp go następującym kodem:

    > [!NOTE]
    > W tym kroku dodasz odwołania do zestawów, które są wymagane przez wygenerowany procesor dyrektywy, który host będzie obsługiwać.

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

6. Znajdź kod funkcji `ResolveDirectiveProcessor` i zastąp go następującym kodem:

    > [!IMPORTANT]
    > Ten kod zawiera zakodowane odwołania do nazwy wygenerowanego procesora dyrektywy, z którym chcesz nawiązać połączenie. Można łatwo wprowadzić to bardziej ogólne. W takim przypadku szuka ona wszystkich procesorów dyrektyw wymienionych w rejestrze i próbuje znaleźć dopasowanie. W takim przypadku host będzie działać z dowolnym wygenerowanym procesorem dyrektywy.

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

7. W menu **File** kliknij pozycję **Save All**.

8. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

## <a name="test-the-custom-host-with-the-directive-processor"></a>Testowanie niestandardowego hosta za pomocą procesora dyrektywy

Aby przetestować niestandardowego hosta szablonu tekstu, najpierw musisz napisać szablon tekstowy, który wywołuje wygenerowany procesor dyrektywy. Następnie należy uruchomić niestandardowego hosta, przekazać do niego nazwę szablonu tekstowego i sprawdzić, czy dyrektywa jest prawidłowo przetwarzana.

### <a name="create-a-text-template-to-test-the-custom-host"></a>Tworzenie szablonu tekstowego w celu przetestowania niestandardowego hosta

1. Utwórz plik tekstowy i nadaj temu plikowi nazwę `TestTemplateWithDP.tt` . Do utworzenia pliku możesz użyć dowolnego edytora tekstów, takiego jak Notatnik.

2. Dodaj następującą zawartość do pliku tekstowego:

    > [!NOTE]
    > Język programowania szablonu tekstowego nie musi odpowiadać językowi hosta niestandardowego.

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

3. W kodzie zastąp ścieżką pliku Sample.min z języka specyficznego dla projektu utworzonego \<YOUR PATH> w pierwszej procedurze.

4. Zapisz i zamknij plik.

### <a name="test-the-custom-host"></a>Testowanie niestandardowego hosta

1. Otwórz okno wiersza polecenia.

2. Wpisz ścieżkę pliku wykonywalnego dla niestandardowego hosta, ale nie naciskaj jeszcze ENTER.

     Na przykład wpisz:

     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`

    > [!NOTE]
    > Zamiast wpisywać adres, możesz przejść do pliku CustomHost.exe w Eksplorator Windows , **a** następnie przeciągnąć plik do okna wiersza polecenia.

3. Wpisz spację.

4. Wpisz ścieżkę do pliku szablonu tekstu, a następnie naciśnij ENTER.

     Na przykład wpisz:

     `<YOUR PATH>TestTemplateWithDP.txt`

    > [!NOTE]
    > Zamiast wpisywać adres, możesz przejść do pliku TestTemplateWithDP.txt w Eksplorator Windows , **a** następnie przeciągnąć plik do okna wiersza polecenia.

     Niestandardowa aplikacja hosta uruchamia i uruchamia proces przekształcania szablonu tekstu.

5. W **Eksplorator Windows** przejdź do folderu zawierającego plik TestTemplateWithDP.txt.

     Folder zawiera również plik TestTemplateWithDP1.txt.

6. Otwórz ten plik, aby zobaczyć wyniki przekształcenia szablonu tekstu.

     Zostaną wyświetlone wyniki wygenerowanego tekstu wyjściowego, które powinny wyglądać tak:

    ```
    Text Template Host Test

    Box: ExampleElement1
    Linked to: ExampleElement2

    Box: ExampleElement2
    Linked from: ExampleElement1
    ```

## <a name="see-also"></a>Zobacz też

- [Przewodnik: Tworzenie niestandardowego hosta szablonu tekstowego](../modeling/walkthrough-creating-a-custom-text-template-host.md)
