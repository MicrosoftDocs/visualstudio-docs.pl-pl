---
title: Tworzenie wtyczki rejestratora do testów wydajności sieci Web
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, recorder plug-in
ms.assetid: 6fe13be1-aeb5-4927-9bff-35950e194da9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5e32faa4525edc79da3d759d67ad2b5676f38fc2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589163"
---
# <a name="how-to-create-a-recorder-plug-in"></a>Jak: Tworzenie wtyczki rejestratora

Umożliwia <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> modyfikowanie zarejestrowanego testu wydajności sieci Web. Modyfikacja występuje po wybraniu **opcji Zatrzymaj** na pasku narzędzi **rejestratora testów wydajności sieci Web,** ale przed zapisaniem i zaprezentowaniem testu w Edytorze testów wydajności sieci Web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Wtyczka rejestratora umożliwia wykonywanie własnych niestandardowych korelacji parametrów dynamicznych. Dzięki wbudowanej funkcji korelacji testy wydajności sieci Web wykrywają parametry dynamiczne w nagraniu internetowym po zakończeniu lub podczas korzystania z **funkcji Promuj parametry dynamiczne do parametrów testu sieci Web** na pasku narzędzi Edytor wydajności sieci **Web.** Jednak wbudowana funkcja wykrywania nie zawsze znajduje wszystkie parametry dynamiczne. Na przykład nie znajduje identyfikatora sesji, który zwykle pobiera jego wartość zmieniona między 5 do 30 minut. W związku z tym należy ręcznie wykonać proces korelacji.

Umożliwia <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> pisanie kodu dla własnej wtyczki niestandardowej. Ta wtyczka może wykonywać korelację lub modyfikować test wydajności sieci Web na wiele sposobów, zanim zostanie zapisany i przedstawiony w Edytorze testów wydajności sieci Web. W związku z tym jeśli okaże się, że określona zmienna dynamiczna musi być skorelowana dla wielu nagrań, można zautomatyzować proces.

Niektóre inne sposoby, że dodatek rejestratora może służyć do dodawania reguł wyodrębniania i sprawdzania poprawności, dodawanie parametrów kontekstu lub konwertowanie komentarzy do transakcji w teście wydajności sieci web.

W poniższych procedurach opisano sposób tworzenia kodu elementarnego wtyczki nagrywarki, wdrażania wtyczki i wykonywania wtyczki. Przykładowy kod zgodnie z procedurami pokazuje, jak używać visual C# do tworzenia niestandardowego parametru dynamicznego rejestratora korelacji plug-in.

## <a name="create-a-recorder-plug-in"></a>Tworzenie wtyczki rejestratora

### <a name="to-create-a-recorder-plug-in"></a>Aby utworzyć wtyczkę nagrywarki

1. Otwórz rozwiązanie, które zawiera projekt testu wydajności sieci web i obciążenia za pomocą testu wydajności sieci Web, dla którego chcesz utworzyć wtyczkę rejestratora.

2. Dodaj nowy projekt **biblioteki klas** do rozwiązania.

3. W **Eksploratorze rozwiązań**w nowym folderze projektu biblioteki klas kliknij prawym przyciskiem myszy folder **Odwołania** i wybierz polecenie **Dodaj odwołanie**.

    > [!TIP]
    > Przykładem nowego folderu projektu biblioteki klas jest **RecorderPlugins**.

     Zostanie wyświetlone okno dialogowe **Dodawanie odwołania.**

4. Wybierz kartę **.NET.**

5. Przewiń w dół i wybierz pozycję **Microsoft.VisualStudio.QualityTools.WebTestFramework,** a następnie wybierz przycisk **OK**.

     **Program Microsoft.VisualStudio.QualityTools.WebTestFramework** jest dodawany w folderze Odwołania w **Eksploratorze** **rozwiązań** .

6. Wpisz kod wtyczki nagrywarki. Najpierw utwórz nową klasę publiczną, która wywodzi się z <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>.

7. Zastąd <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*> w tej metodzie.

    ```csharp
    public class Class1 : WebTestRecorderPlugin
        {
            public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
            {
                base.PostWebTestRecording(sender, e);
            }
        }
    ```

     Argumenty zdarzenia daje dwa obiekty do pracy z: zarejestrowany wynik i test wydajności rejestrowane sieci web. Pozwoli to na iterację przez wynik wyszukując pewne wartości, a następnie przejść do tego samego żądania w teście wydajności sieci web, aby wprowadzić zmiany. Można również po prostu zmodyfikować test wydajności sieci Web, jeśli chcesz dodać parametr kontekstu lub parametryzować części adresu URL.

    > [!NOTE]
    > Jeśli zmodyfikujesz test wydajności sieci Web, <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs.RecordedWebTestModified*> należy również ustawić właściwość na true:`e.RecordedWebTestModified = true;`

8. Dodaj więcej kodu zgodnie z tym, co chcesz, aby wtyczka nagrywarki została wykonana po nagraniu internetowym. Na przykład można dodać kod do obsługi korelacji niestandardowej, jak pokazano w poniższym przykładzie. Można również utworzyć wtyczkę rejestratora dla takich rzeczy, jak konwertowanie komentarzy do transakcji lub dodawanie reguł sprawdzania poprawności do testu wydajności sieci Web.

9. W menu **Kompilacja** wybierz polecenie **>wybierz polecenie Build \<class library project name . **

Następnie wdrożyć wtyczkę rejestratora, aby zarejestrować się w programie Visual Studio.

### <a name="deploy-the-recorder-plug-in"></a>Wdrażanie wtyczki rejestratora

Po skompilowaniu wtyczki rejestratora umieść wynikową bibliotekę DLL w jednej z dwóch lokalizacji:

- *%ProgramFiles(x86)%\Microsoft Visual\\Studio\\[wersja] [edycja]\Common7\IDE\PrivateAssemblies\WebTestPlugins*

- *%USERPROFILE%\Documents\Visual Studio [wersja]\WebTestPlugins*

> [!WARNING]
> Po skopiowaniu wtyczki rejestratora do jednej z dwóch lokalizacji należy ponownie uruchomić program Visual Studio, aby wtyczka nagrywarki została zarejestrowana.

### <a name="execute-the-recorder-plug-in"></a>Wykonaj wtyczkę nagrywarki

1. Utwórz nowy test wydajności sieci Web.

     Zostanie wyświetlone okno dialogowe **Włącz program WebTestRecordPlugins.**

2. Zaznacz pole wyboru wtyczki nagrywarki i wybierz przycisk **OK**.

     Po zakończeniu testu wydajności sieci Web zostanie wykonana nowa wtyczka nagrywarki.

    > [!WARNING]
    > Po uruchomieniu testu wydajności sieci Web lub testu obciążenia, który używa wtyczki, może pojawić się błąd podobny do następującego:
    >
    > **Żądanie nie powiodło \<się: Wyjątek w> zdarzenia dodatku\<plug-in: nie można załadować pliku lub zestawu\<' "Nazwa wtyczki".dll plik>, Version= n.n.n.n>, Culture=neutral, PublicKeyToken=null' lub jedną z jego zależności. System nie może odnaleźć określonego pliku.**
    >
    > Jest to spowodowane wprowadzeniem zmian w kodzie do któregokolwiek z wtyczek i utworzeniem nowej wersji biblioteki DLL **(Version=0.0.0.0),** ale wtyczka nadal odwołuje się do oryginalnej wersji wtyczki. Aby rozwiązać ten problem, wykonaj następujące kroki:
    >
    > 1. W projekcie testu wydajności sieci web i obciążenia zostanie wyświetlone ostrzeżenie w odwołaniach. Usuń i ponownie dodaj odwołanie do biblioteki DLL wtyczek.
    > 2. Wyjmij wtyczkę z testu lub w odpowiedniej lokalizacji, a następnie dodaj ją z powrotem.

## <a name="example"></a>Przykład

W tym przykładzie pokazano, jak utworzyć dostosowaną wtyczkę rejestratora testów wydajności sieci web w celu wykonania niestandardowej korelacji parametrów dynamicznych.

> [!NOTE]
> Pełna lista przykładowego kodu znajduje się na dole tego tematu.

### <a name="iterate-through-the-result-to-find-first-page-with-reportsession"></a>Iteracji przez wynik, aby znaleźć pierwszą stronę z ReportSession

Ta część przykładu kodu iteruje za pośrednictwem każdego zarejestrowanego obiektu i przeszukuje treść odpowiedzi w poszukiwaniu ReportSession.

```csharp
foreach (WebTestResultUnit unit in e.RecordedWebTestResult.Children)
 {
     WebTestResultPage page = unit as WebTestResultPage;
     if (page != null)
     {
         if (!foundId)
         {
             int indexOfReportSession = page.RequestResult.Response.BodyString.IndexOf("ReportSession");
             if (indexOfReportSession > -1)
             {
```

### <a name="add-an-extraction-rule"></a>Dodawanie reguły wyodrębniania

Teraz, gdy odpowiedź została znaleziona, należy dodać regułę wyodrębniania. Ta część przykładu kodu tworzy regułę wyodrębniania przy użyciu <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference> klasy, a następnie znajduje poprawne żądanie w teście wydajności sieci web, aby dodać regułę wyodrębniania do. Każdy obiekt wynik ma nową właściwość dodaną o nazwie DeclarativeWebTestItemId, który jest używany w kodzie, aby uzyskać poprawne żądanie z testu wydajności sieci web.

```csharp
ExtractionRuleReference ruleReference = new ExtractionRuleReference();
     ruleReference.Type = typeof(ExtractText);
     ruleReference.ContextParameterName = "SessionId";
     ruleReference.Properties.Add(new PluginOrRuleProperty("EndsWith", "&ControlID="));
     ruleReference.Properties.Add(new PluginOrRuleProperty("HtmlDecode", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("IgnoreCase", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("Index", "0"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("Required", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("StartsWith", "ReportSession="));
     ruleReference.Properties.Add(new PluginOrRuleProperty("UseRegularExpression", "False"));

     WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
     if (requestInWebTest != null)
     {
         requestInWebTest.ExtractionRuleReferences.Add(ruleReference);
         e.RecordedWebTestModified = true;
     }
```

### <a name="replace-query-string-parameters"></a>Zastępowanie parametrów ciągu kwerendy

Teraz kod znajduje wszystkie parametry ciągu kwerendy, które mają ReportSession jako nazwę i zmienić wartość {{SessionId}}, jak pokazano w tej części przykładu kodu:

```csharp
WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
if (requestInWebTest != null)
{
    foreach (QueryStringParameter param in requestInWebTest.QueryStringParameters)
    {
         if (param.Name.Equals("ReportSession"))
         {
             param.Value = "{{SessionId}}";
         }
     }
 }
```

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.TestTools.WebTesting;
using Microsoft.VisualStudio.TestTools.WebTesting.Rules;

namespace RecorderPlugin
{
    [DisplayName("Correlate ReportSession")]
    [Description("Adds extraction rule for Report Session and binds this to querystring parameters that use ReportSession")]
    public class CorrelateSessionId : WebTestRecorderPlugin
    {
        public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
        {
            //first find the session id
            bool foundId = false;
            foreach (WebTestResultUnit unit in e.RecordedWebTestResult.Children)
            {
                WebTestResultPage page = unit as WebTestResultPage;
                if (page != null)
                {
                    if (!foundId)
                    {
                        int indexOfReportSession = page.RequestResult.Response.BodyString.IndexOf("ReportSession");
                        if (indexOfReportSession > -1)
                        {
                            //add an extraction rule to this request
                            // Get the corresponding request in the Declarative Web performance test
                            ExtractionRuleReference ruleReference = new ExtractionRuleReference();

                            ruleReference.Type = typeof(ExtractText);
                            ruleReference.ContextParameterName = "SessionId";
                            ruleReference.Properties.Add(new PluginOrRuleProperty("EndsWith", "&ControlID="));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("HtmlDecode", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("IgnoreCase", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("Index", "0"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("Required", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("StartsWith", "ReportSession="));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("UseRegularExpression", "False"));

                            WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
                            if (requestInWebTest != null)
                            {
                                requestInWebTest.ExtractionRuleReferences.Add(ruleReference);
                                e.RecordedWebTestModified = true;
                            }
                            foundId = true;

                        }
                    }
                    else
                    {
                        //now update query string parameters
                        WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
                        if (requestInWebTest != null)
                        {
                            foreach (QueryStringParameter param in requestInWebTest.QueryStringParameters)
                            {
                                if (param.Name.Equals("ReportSession"))
                                {
                                    param.Value = "{{SessionId}}";
                                }
                            }
                        }
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążeniowych](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Generowanie i uruchamianie kodowanego testu wydajności sieci Web](../test/generate-and-run-a-coded-web-performance-test.md)
