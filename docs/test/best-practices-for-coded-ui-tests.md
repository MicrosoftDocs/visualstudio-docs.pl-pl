---
title: Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, best practices
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e71029a185d1b3fea1812b2a4b1cf7bf20effff8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565165"
---
# <a name="best-practices-for-coded-ui-tests"></a>Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika

W tym temacie opisano niektóre zalecenia dotyczące tworzenia kodowanych testów interfejsu użytkownika.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="best-practices"></a>Najlepsze rozwiązania

Poniższe wskazówki umożliwiają utworzenie elastycznego kodowanego testu interfejsu użytkownika.

- Używaj **konstruktora kodowanego testu interfejsu użytkownika** wszędzie tam, gdzie to możliwe.

- Nie należy modyfikować pliku *UIMap.Designer.cs* bezpośrednio. W przypadku zmodyfikowania pliku zmiany wprowadzone w pliku zostaną nadpisywane.

- Utwórz swój test jako sekwencję zarejestrowanych metod. Aby uzyskać więcej informacji na temat rejestrowania metody, zobacz [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md).

- Każda zarejestrowana Metoda powinna działać na pojedynczej stronie, formularzu lub oknie dialogowym. Utwórz nową metodę testową dla każdej nowej strony, formularza lub okna dialogowego.

- Podczas tworzenia metody należy użyć zrozumiałej nazwy metody zamiast nazwy domyślnej. Zrozumiała nazwa pomaga identyfikować przeznaczenie metody.

- Jeśli to możliwe, należy ograniczyć każdą zapisaną metodę do mniej niż 10 akcji. Takie podejście modularne ułatwia Zastępowanie metody w przypadku zmiany interfejsu użytkownika.

- Utwórz każde potwierdzenie przy użyciu **konstruktora kodowanego testu interfejsu użytkownika**, który automatycznie dodaje metodę potwierdzenia do pliku *UIMap.Designer.cs* .

- Jeśli interfejs użytkownika zostanie zmieniony, należy ponownie zarejestrować metody testu lub metody potwierdzenia lub ponownie zarejestrować odnośne sekcje istniejącej metody testowej.

- Utwórz oddzielny plik [UIMap](/previous-versions/dd580454(v=vs.140)) dla każdego modułu w testowanej aplikacji. Aby uzyskać więcej informacji, zobacz [Testowanie dużej aplikacji przy użyciu wielu map interfejsu użytkownika](../test/testing-a-large-application-with-multiple-ui-maps.md).

- W testowanej aplikacji należy używać znaczących nazw podczas tworzenia formantów interfejsu użytkownika. Korzystanie z nazw znaczących zapewnia większą przejrzystość i użyteczność dla automatycznie generowanych nazw kontrolek.

- Jeśli tworzysz potwierdzenia przez kodowanie przy użyciu interfejsu API, Utwórz metodę dla każdego potwierdzenia w części klasy [UIMap](/previous-versions/dd580454(v=vs.140)) , która znajduje się w pliku *UIMap.cs* . Aby wykonać potwierdzenie, Wywołaj tę metodę z metody testowej.

- Jeśli bezpośrednio kodujesz przy użyciu interfejsu API, użyj właściwości i metod w klasach, które są generowane w pliku *UIMap.Designer.cs* w kodzie, tak jak to możliwe. Te klasy będą łatwiejsze, bardziej niezawodne i bardziej produktywne.

Kodowane testy interfejsu użytkownika automatycznie dostosowują się do wielu zmian w interfejsie użytkownika. Jeśli na przykład element interfejsu użytkownika zmienił pozycję lub kolor, większość czasu kodowanego testu interfejsu użytkownika nadal znajdzie prawidłowy element.

W trakcie przebiegu testowego formanty interfejsu użytkownika są zlokalizowane przez platformę testową za pomocą zestawu właściwości wyszukiwania. Właściwości wyszukiwania są stosowane do każdej klasy kontrolki w definicjach utworzonych przez **konstruktora kodowanego testu interfejsu użytkownika** w pliku *UIMap.Designer.cs* . Właściwości wyszukiwania zawierają pary nazwa-wartość nazw właściwości i wartości właściwości, które mogą służyć do identyfikowania kontrolki, takie jak <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A>i <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A> właściwości formantu. Jeśli właściwości wyszukiwania nie są zmieniane, kodowany test interfejsu użytkownika będzie pomyślnie znajdował formant w interfejsie użytkownika. Jeśli właściwości wyszukiwania są zmieniane, kodowane testy interfejsu użytkownika mają algorytm inteligentnego dopasowania, który stosuje heurystykę do znajdowania formantów i okien w interfejsie użytkownika. Po zmianie interfejsu użytkownika można modyfikować właściwości wyszukiwania poprzednio zidentyfikowanych elementów, aby upewnić się, że zostały znalezione.

## <a name="if-your-user-interface-changes"></a>Jeśli Twój interfejs użytkownika ulegnie zmianie

Interfejsy użytkownika często zmieniają się podczas opracowywania. Oto kilka sposobów, aby zmniejszyć wpływ tych zmian:

- Znajdź zapisaną metodę odwołującą się do tej kontrolki i Użyj **konstruktora kodowanego testu interfejsu użytkownika** , aby ponownie zarejestrować akcje dla tej metody. Możesz użyć tej samej nazwy dla metody, aby zastąpić istniejące akcje.

- Jeśli kontrolka ma potwierdzenie, które nie jest już prawidłowe:

  - Usuń metodę, która zawiera potwierdzenie.

  - Usuń wywołanie tej metody z metody testowej.

  - Dodaj nowe potwierdzenie, przeciągając przycisk krzyżyka na kontrolkę interfejsu użytkownika, otwierając mapę interfejsu użytkownika i dodając nowe potwierdzenie.

Aby uzyskać więcej informacji na temat rejestrowania kodowanych testów interfejsu użytkownika, zobacz [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md).

## <a name="if-a-background-process-needs-to-complete-before-the-test-can-continue"></a>Jeśli proces w tle musi zakończyć się przed kontynuowaniem testu

Może być konieczne poczekanie, aż proces zakończy się, zanim będzie można kontynuować pracę z następną akcją interfejsu użytkownika. W tym celu można użyć <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A>, aby czekać przed kontynuowaniem testu, jak w poniższym przykładzie:

```csharp
// Set the playback to wait for all threads to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.AllThreads;

// Press the submit button
this.UIMap.ClickSubmit();

// Reset the playback to wait only for the UI thread to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.UIThreadOnly;
```

## <a name="see-also"></a>Zobacz także

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting>
- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md)
- [Testowanie dużej aplikacji przy użyciu wielu map interfejsu użytkownika](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
