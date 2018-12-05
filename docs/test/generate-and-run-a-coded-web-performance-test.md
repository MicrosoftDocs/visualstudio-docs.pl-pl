---
title: Kodowanego testu wydajności WWW w programie Visual Studio
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 76b2e7eebf66bb4a9c2564ca30a72a7b17dbdcfc
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895512"
---
# <a name="generate-and-run-a-coded-web-performance-test"></a>Generowanie i uruchamianie kodowanego testu wydajności sieci Web

Testy wydajności sieci Web są rejestrowane przez przeglądanie aplikacji sieci web. Testy są zawarte w testach obciążenia do pomiaru wydajności aplikacji sieci web pod wpływem wielu użytkowników. Test wydajności sieci web mogą być konwertowane do skryptu oparte na kodzie, który można edytować i dostosowywać jak inny kod źródłowy. Na przykład można dodać konstrukcje pętli i rozgałęzień.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="generate-a-coded-web-performance-test"></a>Generuj zakodowany internetowy test wydajnościowy

1.  Jeśli nie utworzono testu wydajności sieci web, zobacz [rejestrowanie testu wydajności sieci web](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-web-performance-and-load-test-project?view=vsts).

2.  Generowanie kodowanego testu.

     ![Generuj zakodowany internetowy test wydajnościowy](../test/media/web_test_coded_generate.png)

3.  Nazwij przypadek testowy.

     ![Wprowadź nazwę dla kodowany internetowy test wydajnościowy](../test/media/web_test_coded_generate_nametest.png)

     Nowy test zakodowany otwiera się w edytorze kodu.

     Zależności od tego, które wydajności sieci web i szablon projektu testu obciążenia został dodany do rozwiązania zostanie wygenerowany kod w języku Visual Basic lub Visual C#.

     ![Nowy test zakodowany otwiera się w edytorze kodu](../test/media/web_test_coded_generate_opencodeeditor.png)

     W kodzie widać, że metoda GetRequestEnumerator() w języku C# lub metoda Run() w języku Visual Basic zawiera każdy sprawdzania poprawności reguły i żądanie sieci web w teście zapisane.

4.  Aby wykazać, dodając kilka prostych kodów, przewiń w dół do końca metody i po kodzie dla ostatniego żądania sieci web i Dodaj następujący kod:

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

5.  Kompiluj rozwiązanie, aby sprawdzić, czy skompilowanie niestandardowego kodu.

6.  Uruchom test.

     ![Uruchom kodowany internetowy test wydajnościowy](../test/media/web_test_coded_generate_run.png)

     A ponieważ dzień uruchomienie miało miejsce w środę...

     ![Wyników testu wydajności sieci web kodowanego](../test/media/web_test_coded_generate_results.png)

## <a name="qa"></a>PYTANIA I ODPOWIEDZI

### <a name="q-can-i-run-more-than-one-test-at-a-time"></a>P: czy można uruchomić więcej niż jeden test naraz?
 **Odp.:** tak, użyj menu kontekstowego w **Eksploratora rozwiązań**.

### <a name="q-should-i-add-a-data-source-before-or-after-i-generate-a-coded-test"></a>P: czy należy dodać źródła danych przed czy po wygenerowaniu kodowanego testu?
 **Odp.:** ułatwia dodawanie [źródła danych](../test/add-a-data-source-to-a-web-performance-test.md) przed wygenerowaniem kodowanego testu, ponieważ kod zostanie automatycznie wygenerowany dla Ciebie.

 Po uruchomieniu testu kodowanego ze źródłem danych, można napotkać następujący komunikat o błędzie:

 **Nie można uruchomić testu \<testu nazwy > na agencie \<nazwa komputera >: odwołanie nie ustawione na wystąpienie obiektu do obiektu.**

 Taka sytuacja może wystąpić, ponieważ masz zdefiniowane dla klasy testowej, bez odpowiedniego DataBindingAttribute DataSourceAttribute. Aby rozwiązać ten problem, Dodaj odpowiedni DataBindingAttribute, usuń go lub Wypowiedz go z kodu.

### <a name="q-should-i-add-validation-and-extraction-rules-before-or-after-i-generate-a-coded-test"></a>P: czy należy dodać reguły walidacji i wyodrębniania przed czy po wygenerowaniu kodowanego testu?
 **Odp.:** ułatwia dodawanie reguł sprawdzania poprawności i reguł wyodrębniania przed wygenerowaniem zakodowanego testu; jednak zalecamy użycie [kodowane testy interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md) do celów sprawdzania poprawności.