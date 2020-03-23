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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589581"
---
# <a name="generate-and-run-a-coded-web-performance-test"></a>Generowanie i uruchamianie kodowanego testu wydajności sieci Web

Testy wydajności sieci Web są rejestrowane przez przeglądanie aplikacji sieci web. Testy są uwzględniane w testach obciążenia, aby zmierzyć wydajność aplikacji sieci web w warunkach naprężeń wielu użytkowników. Test wydajności sieci Web można przekonwertować na skrypt oparty na kodzie, który można edytować i dostosowywać jak każdy inny kod źródłowy. Na przykład można dodać konstrukcje pętli i rozgałęzienia.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="generate-a-coded-web-performance-test"></a>Generowanie zakodowany test wydajności sieci Web

1. Jeśli nie utworzono testu wydajności sieci Web, zobacz [Rejestrowanie testu wydajności sieci Web](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-web-performance-and-load-test-project).

2. Wygeneruj zakodowany test.

     ![Generowanie zakodowany test wydajności sieci Web](../test/media/web_test_coded_generate.png)

3. Nazwij test.

     ![Wprowadź nazwę zakodowany test wydajności sieci Web](../test/media/web_test_coded_generate_nametest.png)

     Nowy kodowany test zostanie otwarty w edytorze kodu.

     W zależności od tego, który szablon projektu testu wydajności sieci web i testu obciążenia został dodany do rozwiązania, kod zostanie wygenerowany w języku Visual Basic lub Visual C#.

     ![Nowy kodowany test otwiera się w edytorze kodu](../test/media/web_test_coded_generate_opencodeeditor.png)

     W kodzie widać, że metoda GetRequestEnumerator() w języku C#lub Metoda Run() w języku Visual Basic zawiera każdą regułę sprawdzania poprawności i żądanie sieci web, które znajdowało się w przekodowanym teście.

4. Aby zademonstrować dodanie prostego kodu, przewiń w dół do końca metody i po kodzie dla ostatniego żądania sieci web i dodaj następujący kod:

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

5. Skompiluj rozwiązanie, aby sprawdzić, czy kod niestandardowy jest kompilowany.

6. Uruchom test.

     ![Uruchamianie zakodowany test wydajności sieci Web](../test/media/web_test_coded_generate_run.png)

     A ponieważ dzień, w którym to było prowadzone stało się środa ...

     ![Kodowane wyniki testów wydajności sieci web](../test/media/web_test_coded_generate_results.png)

## <a name="qa"></a>Pytania i odpowiedzi

### <a name="q-can-i-run-more-than-one-test-at-a-time"></a>Pyt.: Czy mogę uruchomić więcej niż jeden test naraz?
**Odp.:** Tak, użyj menu (kontekstu) w **Eksploratorze rozwiązań**.

### <a name="q-should-i-add-a-data-source-before-or-after-i-generate-a-coded-test"></a>Pyt.: Czy należy dodać źródło danych przed lub po wygenerowaniu zakodowany test?
**Odp.:** Jest łatwiejsze do dodania [źródła danych](../test/add-a-data-source-to-a-web-performance-test.md) przed wygenerowaniem zakodowany test, ponieważ kod zostanie wygenerowany automatycznie dla Ciebie.

Po uruchomieniu zakodowany test ze źródłem danych może zostać wyświetlony następujący komunikat o błędzie:

**Nie można \<uruchomić testu Nazwa testu \<> w> nazwa komputera agenta: Odwołanie do obiektu nie jest ustawione na wystąpienie obiektu.**

Może to nastąpić, ponieważ masz DataSourceAttribute zdefiniowane dla klasy testowej, bez odpowiedniego DataBindingAttribute. Aby rozwiązać ten błąd, dodaj odpowiedni atrybut DataBindingAttribute, usuń go lub skomentuj go poza kodem.

### <a name="q-should-i-add-validation-and-extraction-rules-before-or-after-i-generate-a-coded-test"></a>Pyt.: Należy dodać reguły sprawdzania poprawności i wyodrębniania przed lub po wygenerowaniu zakodowany test?
**Odp.:** Jest łatwiejsze do dodania reguł sprawdzania poprawności i reguł wyodrębniania przed wygenerowaniem zakodowany test; Jednak zaleca się użycie [kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md) do celów sprawdzania poprawności.
