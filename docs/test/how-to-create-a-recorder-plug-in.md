---
title: Tworzenie wtyczki rejestratora dla testów wydajności sieci Web
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, recorder plug-in
ms.assetid: 6fe13be1-aeb5-4927-9bff-35950e194da9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f75114683a4f456d0514af20c1c201c373bd4b0
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288013"
---
# <a name="how-to-create-a-recorder-plug-in"></a>Instrukcje: tworzenie wtyczki rejestratora

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>Pozwala modyfikować zarejestrowany test wydajności sieci Web. Modyfikacja odbywa się po wybraniu opcji **Zatrzymaj** na pasku narzędzi **rejestratora testu wydajności sieci Web** , ale przed zapisaniem testu i wyświetleniem go w Edytor internetowego testu wydajnościowego.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Wtyczka rejestratora umożliwia wykonywanie własnej niestandardowej korelacji w parametrach dynamicznych. Dzięki wbudowanym funkcjom korelacji testy wydajności sieci Web wykrywają dynamiczne parametry w rejestrowaniu w sieci Web po zakończeniu lub w przypadku korzystania z **Przekształć dynamiczne parametry na parametry testu sieci Web** na pasku narzędzi **Edytor internetowego testu wydajnościowego** . Jednak Wbudowana funkcja wykrywania nie zawsze znajduje wszystkie parametry dynamiczne. Na przykład nie znajduje identyfikatora sesji, który zwykle otrzymuje wartość z przedziału od 5 do 30 minut. W związku z tym należy ręcznie przeprowadzić proces korelacji.

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>Pozwala napisać kod dla własnej wtyczki niestandardowej. Ta wtyczka może wykonać korelację lub zmodyfikować test wydajności sieci Web na wiele sposobów przed jego zapisaniem i przedłożeniem w Edytor internetowego testu wydajnościowego. W związku z tym, jeśli określisz, że określona zmienna dynamiczna musi być skorelowane dla dużej liczby nagrań, Możesz zautomatyzować ten proces.

Innymi sposobami korzystania z wtyczki rejestratora jest możliwość dodawania reguł wyodrębniania i walidacji, dodawania parametrów kontekstu lub konwertowania komentarzy do transakcji w teście wydajności sieci Web.

W poniższych procedurach opisano, jak utworzyć kod podstawowe dla wtyczki rejestratora, wdrożyć wtyczkę i wykonać wtyczkę. Przykładowy kod po procedurach pokazuje, jak używać języka Visual C# do tworzenia niestandardowej wtyczki rejestratora korelacji parametrów dynamicznych.

## <a name="create-a-recorder-plug-in"></a>Tworzenie wtyczki rejestratora

### <a name="to-create-a-recorder-plug-in"></a>Aby utworzyć wtyczkę rejestratora

1. Otwórz rozwiązanie, które zawiera projekt testu wydajności sieci Web i obciążenia z testem wydajności sieci Web, dla którego chcesz utworzyć wtyczkę rejestratora.

2. Dodaj nowy projekt **biblioteki klas** do rozwiązania.

3. W **Eksplorator rozwiązań**w folderze nowy projekt biblioteki klas kliknij prawym przyciskiem myszy folder **odwołania** i wybierz polecenie **Dodaj odwołanie**.

    > [!TIP]
    > Przykładem nowego folderu projektu biblioteki klas jest **RecorderPlugins**.

     Zostanie wyświetlone okno dialogowe **Dodawanie odwołania** .

4. Wybierz kartę **.NET** .

5. Przewiń w dół i wybierz pozycję **Microsoft. VisualStudio. QualityTools. WebTestFramework** , a następnie wybierz **przycisk OK**.

     **Microsoft. VisualStudio. QualityTools. WebTestFramework** zostanie dodana do folderu **references** w **Eksplorator rozwiązań**.

6. Napisz kod dla wtyczki rejestratora. Najpierw utwórz nową klasę publiczną, która pochodzi od <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> .

7. Zastąp <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*> metodę.

    ```csharp
    public class Class1 : WebTestRecorderPlugin
        {
            public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
            {
                base.PostWebTestRecording(sender, e);
            }
        }
    ```

     Argumenty zdarzeń będą zawierać dwa obiekty do współpracy: zarejestrowany wynik i zarejestrowany test wydajności sieci Web. Pozwoli to na iterację wyników szukających określonych wartości, a następnie przechodzenie do tego samego żądania w teście wydajności sieci Web, aby wprowadzić modyfikacje. Możesz również zmodyfikować test wydajności sieci Web, jeśli chcesz dodać parametr kontekstowy lub Sparametryzuj części adresu URL.

    > [!NOTE]
    > Jeśli modyfikujesz test wydajności sieci Web, należy również ustawić <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs.RecordedWebTestModified*> Właściwość na true:`e.RecordedWebTestModified = true;`

8. Dodaj więcej kodu według tego, co wtyczka Rejestrator ma wykonać po nagraniu w sieci Web. Na przykład można dodać kod do obsługi korelacji niestandardowej, jak pokazano w poniższym przykładzie. Możesz również utworzyć wtyczkę rejestratora dla takich elementów jak konwertowanie komentarzy do transakcji lub dodawanie reguł sprawdzania poprawności do testu wydajności sieci Web.

9. W menu **kompilacja** wybierz polecenie **Kompiluj \<class library project name> **.

Następnie wdróż wtyczkę rejestratora, aby mogła ona zostać zarejestrowana w programie Visual Studio.

### <a name="deploy-the-recorder-plug-in"></a>Wdróż wtyczkę rejestratora

Po skompilowaniu wtyczki rejestratora Umieść w jednej z dwóch lokalizacji uzyskaną bibliotekę DLL:

- *% ProgramFiles (x86)% \ Microsoft Visual Studio \\ [wersja] \\ [Edition] \Common7\IDE\PrivateAssemblies\WebTestPlugins*

- *%USERPROFILE%\Documents\Visual Studio [wersja] \WebTestPlugins*

> [!WARNING]
> Po skopiowaniu wtyczki rejestratora do jednej z dwóch lokalizacji, należy ponownie uruchomić program Visual Studio, aby zarejestrowano wtyczkę rejestratora.

### <a name="execute-the-recorder-plug-in"></a>Wykonaj wtyczkę rejestratora

1. Utwórz nowy test wydajności sieci Web.

     Zostanie wyświetlone okno dialogowe **Włącz WebTestRecordPlugins** .

2. Zaznacz pole wyboru dla wtyczki rejestratora i wybierz **przycisk OK**.

     Po zakończeniu nagrywania testu wydajności sieci Web zostanie wykonany nowy dodatek plug-in rejestratora.

    > [!WARNING]
    > Po uruchomieniu testu wydajności sieci Web lub testu obciążenia, który korzysta z wtyczki, może zostać wyświetlony błąd podobny do poniższego:
    >
    > **Żądanie nie powiodło się: wyjątek w \<plug-in> zdarzeniu: nie można załadować pliku lub zestawu " \<"Plug-in name".dll file> , Version = \<n.n.n.n> , Culture = neutral, PublicKeyToken = null" lub jednej z jego zależności. System nie może znaleźć określonego pliku.**
    >
    > Jest to spowodowane wprowadzeniem zmian w kodzie w dowolnych wtyczkach i utworzenie nowej wersji biblioteki DLL **(Version = 0.0.0.0)**, ale wtyczka nadal odwołuje się do oryginalnej wersji wtyczki. Aby rozwiązać ten problem, wykonaj następujące kroki:
    >
    > 1. W projekcie testu wydajności i obciążenia sieci Web zobaczysz ostrzeżenie w odwołaniach. Usuń i Dodaj odwołanie do biblioteki DLL wtyczki.
    > 2. Usuń wtyczkę z testu lub odpowiedniej lokalizacji, a następnie dodaj ją ponownie.

## <a name="example"></a>Przykład

Ten przykład pokazuje, jak utworzyć dostosowaną wtyczkę rejestratora testów wydajności sieci Web w celu wykonania niestandardowej korelacji parametrów dynamicznych.

> [!NOTE]
> Pełna lista przykładowego kodu znajduje się w dolnej części tego tematu.

### <a name="iterate-through-the-result-to-find-first-page-with-reportsession"></a>Wykonaj iterację w wyniku, aby znaleźć pierwszą stronę z ReportSession

Ta część przykładu kodu iteruje przez każdy zarejestrowany obiekt i przeszukuje treść odpowiedzi dla ReportSession.

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

### <a name="add-an-extraction-rule"></a>Dodaj regułę wyodrębniania

Teraz, gdy zostanie znaleziona odpowiedź, należy dodać regułę wyodrębniania. Ta część przykładu kodu tworzy regułę wyodrębniania za pomocą <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference> klasy, a następnie odnajduje odpowiednie żądanie w teście wydajności sieci Web, aby dodać regułę wyodrębniania do programu. Każdy obiekt wynikowy ma nową właściwość o nazwie DeclarativeWebTestItemId, która jest używana w kodzie, aby uzyskać prawidłowe żądanie od testu wydajności sieci Web.

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

### <a name="replace-query-string-parameters"></a>Zastąp parametry ciągu zapytania

Teraz kod znajduje wszystkie parametry ciągu zapytania, które mają ReportSession jako nazwę, i zmień wartość na {{SessionId}}, jak pokazano w tej części przykładu kodu:

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
