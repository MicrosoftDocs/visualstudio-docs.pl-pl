---
title: Kodowane testy wydajności sieci Web
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, creating
- code, Web performance tests
- Web performance tests, coded
ms.assetid: 169e48f9-52fd-4d0b-83d9-54913bde506b
dev_langs:
- CSharp
- VB
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4297f60c74e32b904d7c36912a8377d33f23ebdf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75589581"
---
# <a name="generate-and-run-a-coded-web-performance-test"></a>Generowanie i uruchamianie kodowanego testu wydajności sieci Web

Testy wydajności sieci Web są rejestrowane przez przeglądanie aplikacji sieci Web. Testy są zawarte w testach obciążeniowych, aby mierzyć wydajność aplikacji sieci Web pod obciążeniem wielu użytkowników. Test wydajności sieci Web można przekonwertować na skrypt oparty na kodzie, który można edytować i dostosowywać jak każdy inny kod źródłowy. Na przykład można dodać konstrukcje pętli i rozgałęziania.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="generate-a-coded-web-performance-test"></a>Generowanie kodowanego testu wydajności sieci Web

1. Jeśli nie utworzono testu wydajności sieci Web, zobacz artykuł [Rejestrowanie testów wydajności sieci Web](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-web-performance-and-load-test-project).

2. Generowanie kodowanego testu.

     ![Generowanie kodowanego testu wydajności sieci Web](../test/media/web_test_coded_generate.png)

3. Nazwij test.

     ![Wprowadź nazwę kodowanego testu wydajności sieci Web](../test/media/web_test_coded_generate_nametest.png)

     Nowy kodowany test zostanie otwarty w edytorze kodu.

     W zależności od tego, który szablon projektu testu wydajności i obciążenia sieci Web został dodany do rozwiązania, kod zostanie wygenerowany w Visual Basic lub Visual C#.

     ![Nowy kodowany test otwiera się w edytorze kodu](../test/media/web_test_coded_generate_opencodeeditor.png)

     Można zobaczyć w kodzie, który Metoda GetRequestEnumerator () w języku C# lub metoda Run () w Visual Basic, zawiera wszystkie reguły walidacji i żądania sieci Web, które były w testowanym teście.

4. Aby zademonstrować Dodawanie kodu prostego, przewiń w dół do końca metody i po kodzie dla ostatniego żądania sieci Web i Dodaj następujący kod:

    ```c#
    if (DateTime.Today.DayOfWeek == DayOfWeek.Wednesday)
    {
        WebTestRequest customRequest = new WebTestRequest("http://weather.msn.com/");
        yield return customRequest;
    }
    else
    {
        WebTestRequest customRequest = new WebTestRequest("https://msdn.microsoft.com/");
        yield return customRequest;
    }
    ```

    ```vb
    If DateTime.Today.DayOfWeek = DayOfWeek.Wednesday Then
        Dim customRequest As WebTestRequest = New WebTestRequest("http://weather.msn.com/")
        MyBase.Send(customRequest)
    Else
        Dim customRequest As WebTestRequest = New WebTestRequest("https://msdn.microsoft.com/")
        MyBase.Send(customRequest)
    End If
    ```

5. Skompiluj rozwiązanie, aby sprawdzić, czy kod niestandardowy został skompilowany.

6. Uruchom test.

     ![Uruchamianie kodowanego testu wydajności sieci Web](../test/media/web_test_coded_generate_run.png)

     I ponieważ dzień tego uruchomienia miał miejsce w środę...

     ![Kodowane wyniki testów wydajności sieci Web](../test/media/web_test_coded_generate_results.png)

## <a name="qa"></a>Pytania i odpowiedzi

### <a name="q-can-i-run-more-than-one-test-at-a-time"></a>P: Czy można uruchomić więcej niż jeden test jednocześnie?
Odp **.:** Tak, użyj menu kontekstowego kliknij prawym przyciskiem myszy w **Eksplorator rozwiązań**.

### <a name="q-should-i-add-a-data-source-before-or-after-i-generate-a-coded-test"></a>P: czy należy dodać źródło danych przed czy po wygenerowaniu kodowanego testu?
Odp **.:** Łatwiej jest dodać [Źródło danych](../test/add-a-data-source-to-a-web-performance-test.md) przed wygenerowaniem kodowanego testu, ponieważ kod zostanie wygenerowany automatycznie.

Po uruchomieniu kodowanego testu ze źródłem danych może zostać wyświetlony następujący komunikat o błędzie:

**Nie można uruchomić testu \<Test Name> na agencie \<Computer Name> : odwołanie do obiektu nie jest ustawione na wystąpienie obiektu.**

Taka sytuacja może wystąpić, ponieważ istnieje element DataSourceAttribute zdefiniowany dla klasy testowej bez odpowiadającego mu elementu DataBindingAttribute. Aby rozwiązać ten problem, Dodaj odpowiedni element DataBindingAttribute, usuń go lub Dodaj komentarz do tego kodu.

### <a name="q-should-i-add-validation-and-extraction-rules-before-or-after-i-generate-a-coded-test"></a>P: czy należy dodać reguły walidacji i wyodrębniania przed czy po wygenerowaniu kodowanego testu?
Odp **.:** Łatwiej jest dodać reguły sprawdzania poprawności i reguły wyodrębniania przed wygenerowaniem kodowanego testu; zaleca się jednak używanie [kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md) do celów weryfikacji.
