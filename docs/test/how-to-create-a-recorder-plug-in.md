---
title: Tworzenie wtyczki dla testów wydajności sieci web rejestratora
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, recorder plug-in
ms.assetid: 6fe13be1-aeb5-4927-9bff-35950e194da9
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.openlocfilehash: d047298a263e707c2f4e09475d2f6510a586a4f2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945824"
---
# <a name="how-to-create-a-recorder-plug-in"></a>Instrukcje: Tworzenie wtyczki rejestratora

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> Umożliwia modyfikowanie nagranych internetowego testu wydajnościowego. Modyfikacja występuje po wybraniu **zatrzymać** w **rejestratora testów wydajności sieci Web** narzędzi, ale przed testu zapisaniem i przedstawieniem w edytorze testu wydajności sieci Web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Wtyczka rejestratora umożliwia wykonywanie własnej niestandardowej korelacji na parametrach dynamicznych. Dzięki wbudowanym funkcjom korelacji testy wydajności sieci web wykrywają parametry dynamiczne w sieci web rejestracji po zakończeniu lub po użyciu **Przekształć dynamiczne parametry na parametry testu sieci Web** na **sieci Web Edytor testów wydajności** paska narzędzi. Jednak wbudowanych w wykrywaniu funkcji nie zawsze znajdzie wszystkie parametry dynamiczne. Na przykład nie odnajdzie Identyfikatora sesji, który zwykle zmienia swoją wartość od 5 do 30 minut. W związku z tym należy ręcznie przeprowadzić proces korelacji.

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> Umożliwia pisanie kodu dla własnego niestandardowego dodatku typu plug-in. Ta wtyczka może wykonywać korelację lub modyfikować test wydajności sieci web na wiele sposobów przed jego zapisaniem i przedstawieniem w edytorze testu wydajności sieci Web. W związku z tym jeśli okaże się, że określona zmienna dynamiczna musi zostać skorelowana dla wielu nagrań, możesz zautomatyzować ten proces.

Inny sposób, że dodatek typu plug-in rejestratora mogą być używane dotyczy dodawania ekstrakcji i reguł sprawdzania poprawności, dodawania parametrów kontekstu lub konwertowania komentarzy do transakcji w wydajności sieci web test.

W poniższych procedurach opisano sposób tworzenia kodu szczątkowego dla rejestratora wtyczki, wdrażania dodatek typu plug-in i wykonać dodatku typu plug-in. Przykładowy kod, zgodnie z procedurami pokazuje, jak używać języka Visual C# do tworzenia dodatku typu plug-in rejestratora korelacji parametrów dynamicznych niestandardowych.

## <a name="create-a-recorder-plug-in"></a>Tworzenie wtyczki rejestratora

### <a name="to-create-a-recorder-plug-in"></a>Aby utworzyć wtyczkę rejestratora

1.  Otwórz rozwiązanie, które zawiera projekt testu obciążenia i wydajności sieci web za pomocą testu wydajności sieci web, dla której chcesz utworzyć wtyczkę rejestratora.

2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie, wybierz **Dodaj**, a następnie wybierz **nowy projekt**.

     **Dodaj nowy projekt** zostanie wyświetlone okno dialogowe.

3.  W obszarze **zainstalowane szablony**, wybierz opcję **Visual C#**.

4.  Na liście szablonów wybierz **biblioteki klas**.

5.  W **nazwa** polu tekstowym wpisz nazwę dla dodatku plug-in.

     Biblioteka klas jest dodawana do **Eksploratora rozwiązań** i Nowa klasa jest otwierana w **Edytor kodu**.

6.  W **Eksploratora rozwiązań**, w nowym folderze projektu biblioteki klas, kliknij prawym przyciskiem myszy **odwołania** i wybierz polecenie **Dodaj odwołanie**.

    > [!TIP]
    > Na przykład nowy folder projektu biblioteki klas **RecorderPlugins**.

     **Dodaj odwołanie** zostanie wyświetlone okno dialogowe.

7.  Wybierz **.NET** kartę.

8.  Przewiń w dół i wybierz **Microsoft.VisualStudio.QualityTools.WebTestFramework** , a następnie wybierz **OK**.

     **Microsoft.VisualStudio.QualityTools.WebTestFramework** zostanie dodany do **odwołania** folderu w **Eksploratora rozwiązań**.

9. Pisz kod dla dodatku rejestratora. Najpierw utwórz nową klasę publiczną, która pochodzi od klasy <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>.

10. Zastąp <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*> metody.

    ```csharp
    public class Class1 : WebTestRecorderPlugin
        {
            public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
            {
                base.PostWebTestRecording(sender, e);
            }
        }
    ```

     Argumenty zdarzenia zostaną wyświetlone dwa obiekty przeznaczone do pracy z: wynik nagrany i nagrany internetowego testu wydajnościowego. Pozwoli to do iteracji wyników dla niektórych wartości i następnie przeskakiwanie do tego samego żądania w teście wydajności sieci web, można wprowadzić modyfikacje. Możesz też po prostu zmodyfikować testu wydajności sieci web, jeśli chcesz dodać parametr kontekstu lub zdefiniować parametry części adresu URL.

    > [!NOTE]
    > Jeśli modyfikujesz test wydajności sieci web, należy również ustawić <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs.RecordedWebTestModified*> właściwości na wartość true: `e.RecordedWebTestModified = true;`

11. Dodaj więcej kodu według tego, co rejestratora wtyczki ma wykonać po rejestrowaniu w sieci web. Na przykład można dodać kod do obsługi niestandardowej korelacji, jak pokazano w poniższym przykładzie. Można również utworzyć wtyczki dla takich rejestratora, jak przetestować konwertowania komentarzy do transakcji lub dodawania reguł sprawdzania poprawności do wydajności sieci web.

12. Na **kompilacji** menu, wybierz **kompilacji \<Nazwa projektu biblioteki klas >**.

13. Następnie należy wdrożyć zarejestrowany dodatek w celu użycia go zarejestrować za pomocą programu Visual Studio.

### <a name="deploy-the-recorder-plug-in"></a>Wdróż wtyczkę Rejestrator

Po skompilowaniu dodatku plug-in rejestratora umieścić wynikowy DLL w jednej z dwóch lokalizacji:

- *% ProgramFiles (x86) %\Microsoft Visual Studio\\[wersja]\\\Common7\IDE\PrivateAssemblies\WebTestPlugins [wersja]*

- *%USERPROFILE%\Documents\Visual studio [wersja] \WebTestPlugins*

> [!WARNING]
> Po skopiowaniu dodatku plug-in rejestratora do jednej z dwóch lokalizacji, należy ponownie uruchomić program Visual Studio dla dodatku plug-in do zarejestrowania.

### <a name="to-execute-the-recorder-plug-in"></a>Aby wykonać wtyczkę rejestratora

1.  Utwórz nowy test wydajności sieci web.

     **Włącz WebTestRecordPlugins** Wyświetla okno dialogowe.

2.  Zaznacz pole wyboru dla dodatku plug-in rejestratora i wybierz polecenie **OK**.

     Po zakończeniu testu wydajności sieci web zostanie wykonany nowy dodatek plug-in rejestratora.

    > [!WARNING]
    > Możesz otrzymać błąd podobny do następującego po uruchomieniu testu wydajności sieci web lub testu obciążenia, który korzysta z Twojej wtyczki:
    >
    > **Żądanie nie powiodło się: Wyjątek w \<wtyczki > zdarzenia: Nie można załadować pliku lub zestawu "\<pliku dll"Nazwa wtyczki">, wersja =\<n.n.n.n >, Culture = neutral, PublicKeyToken = null" lub jednej z jego zależności. System nie może odnaleźć określonego pliku.**
    >
    > Dzieje się tak Jeśli wprowadzasz zmiany kodu do dowolnego typu plug-ins i utworzyć nową wersję biblioteki DLL **(wersja = 0.0.0.0)**, ale wtyczka nadal odwołuje się do oryginalnej wersji wtyczki. Aby rozwiązać ten problem, wykonaj następujące kroki:
    >
    > 1. W wydajności sieci web i obciążenia projektu testowego zostanie wyświetlone ostrzeżenie w odwołaniach. Usuń i ponownie Dodaj odwołanie do biblioteki DLL dodatku plug-in.
    > 2. Usuń dodatek plug-in z testu lub odpowiedniej lokalizacji, a następnie dodaj go ponownie.

## <a name="example"></a>Przykład

Ten przykład przedstawia sposób tworzenia dodatku typu plug-in do wykonywania niestandardowych korelacji parametrów dynamicznych rejestratora testów wydajności sieci web dostosowane.

> [!NOTE]
> Pełną listę przykładowy kod znajduje się w dolnej części tego tematu.

**Recenzowanie przykładowego kodu**

## <a name="iterate-through-the-result-to-find-first-page-with-reportsession"></a>Wykonuj iteracje przez wyniki w celu znalezienia pierwszej strony z obiektem ReportSession

Ta część próbki kodu iteruje przez każdy nagrany obiekt i wyszukuje treść odpowiedzi dla ReportSession.

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

## <a name="add-an-extraction-rule"></a>Dodawanie reguły wyodrębniania

Teraz, gdy odpowiedź została znaleziona, należy dodać regułę ekstrakcji. Ta część przykładowy kod tworzy regułę ekstrakcji przy użyciu <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference> klasy, a następnie znajduje poprawne żądanie w teście wydajności sieci web, aby dodać do niego regułę ekstrakcji. Każdy obiekt wynikowy ma nową właściwość o nazwie DeclarativeWebTestItemId, która jest on używany w kodzie w celu uzyskania poprawnego żądania z testu wydajności sieci web.

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

## <a name="replace-query-string-parameters"></a>Zamień parametry ciągu zapytania

Teraz kod znajduje wszystkie zapytania parametry ciągu, które mają wartość ReportSession jako nazwę, a następnie zmień wartość na {{IdentyfikatorSesji}}, jak pokazano w tej części przykładowego kodu:

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

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążenia](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Generowanie i uruchom kodowany internetowy test wydajnościowy](../test/generate-and-run-a-coded-web-performance-test.md)