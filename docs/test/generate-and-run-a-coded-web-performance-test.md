---
title: Kodowanego testu wydajności www
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
manager: jillfra
ms.openlocfilehash: 49691b2031d1d935871a73833924e9dc4aa46dcd
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68918410"
---
# <a name="generate-and-run-a-coded-web-performance-test"></a>Generowanie i uruchamianie kodowanego testu wydajności sieci Web

Testy wydajności sieci Web są rejestrowane przez przeglądanie aplikacji sieci web. Testy są zawarte w testach obciążenia do pomiaru wydajności aplikacji sieci web pod wpływem wielu użytkowników. Test wydajności sieci web mogą być konwertowane do skryptu oparte na kodzie, który można edytować i dostosowywać jak inny kod źródłowy. Na przykład można dodać konstrukcje pętli i rozgałęzień.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="generate-a-coded-web-performance-test"></a>Generuj zakodowany internetowy test wydajnościowy

1. Jeśli nie utworzono testu wydajności sieci web, zobacz [rejestrowanie testu wydajności sieci web](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-web-performance-and-load-test-project).

2. Generowanie kodowanego testu.

     ![Generuj zakodowany internetowy test wydajnościowy](../test/media/web_test_coded_generate.png)

3. Nazwij przypadek testowy.

     ![Wprowadź nazwę dla kodowany internetowy test wydajnościowy](../test/media/web_test_coded_generate_nametest.png)

     Nowy test zakodowany otwiera się w edytorze kodu.

     Zależności od tego, które wydajności sieci web i szablon projektu testu obciążenia został dodany do rozwiązania zostanie wygenerowany kod w języku Visual Basic lub Visual C#.

     ![Nowy test zakodowany otwiera się w edytorze kodu](../test/media/web_test_coded_generate_opencodeeditor.png)

     W kodzie widać, że metoda GetRequestEnumerator() w języku C# lub metoda Run() w języku Visual Basic zawiera każdy sprawdzania poprawności reguły i żądanie sieci web w teście zapisane.

4. Aby wykazać, dodając kilka prostych kodów, przewiń w dół do końca metody i po kodzie dla ostatniego żądania sieci web i Dodaj następujący kod:

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

5. Kompiluj rozwiązanie, aby sprawdzić, czy skompilowanie niestandardowego kodu.

6. Uruchom test.

     ![Uruchom kodowany internetowy test wydajnościowy](../test/media/web_test_coded_generate_run.png)

     A ponieważ dzień uruchomienie miało miejsce w środę...

     ![Wyników testu wydajności sieci web kodowanego](../test/media/web_test_coded_generate_results.png)

## <a name="qa"></a>PYTANIA I ODPOWIEDZI

### <a name="q-can-i-run-more-than-one-test-at-a-time"></a>PYTANIA Czy można uruchomić więcej niż jeden test jednocześnie?
**Z** Tak, użyj menu kontekstowego kliknij prawym przyciskiem myszy w **Eksplorator rozwiązań**.

### <a name="q-should-i-add-a-data-source-before-or-after-i-generate-a-coded-test"></a>PYTANIA Czy należy dodać źródło danych przed czy po wygenerowaniu kodowanego testu?
**Z** Łatwiej jest dodać [Źródło danych](../test/add-a-data-source-to-a-web-performance-test.md) przed wygenerowaniem kodowanego testu, ponieważ kod zostanie wygenerowany automatycznie.

Po uruchomieniu testu kodowanego ze źródłem danych, można napotkać następujący komunikat o błędzie:

**Nie można uruchomić \<testowej nazwy > na nazwie \<komputera agenta >: Odwołanie do obiektu nie jest ustawione na wystąpienie obiektu.**

Taka sytuacja może wystąpić, ponieważ masz zdefiniowane dla klasy testowej, bez odpowiedniego DataBindingAttribute DataSourceAttribute. Aby rozwiązać ten problem, Dodaj odpowiedni DataBindingAttribute, usuń go lub Wypowiedz go z kodu.

### <a name="q-should-i-add-validation-and-extraction-rules-before-or-after-i-generate-a-coded-test"></a>PYTANIA Czy należy dodać reguły weryfikacji i wyodrębniania przed czy po wygenerowaniu kodowanego testu?
**Z** Łatwiej jest dodać reguły sprawdzania poprawności i reguły wyodrębniania przed wygenerowaniem kodowanego testu; zaleca się jednak używanie [kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md) do celów weryfikacji.