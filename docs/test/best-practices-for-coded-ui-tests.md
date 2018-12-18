---
title: Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, best practices
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed2ab3ff15e94bf0e014b99b6451840e6f26a04e
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896027"
---
# <a name="best-practices-for-coded-ui-tests"></a>Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika

W tym temacie opisano niektóre zalecenia dotyczące tworzenia kodowanych testów interfejsu użytkownika.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="best-practices"></a>Najlepsze rozwiązania

Skorzystaj z poniższych wskazówek do tworzenia elastycznych kodowanego testu interfejsu użytkownika.

-   Użyj **kodowanego testu interfejsu użytkownika** zawsze, gdy jest to możliwe.

-   Nie należy modyfikować *UIMap.designer.cs* pliku bezpośrednio. Jeśli zmodyfikujesz plik, zmiany w pliku zostaną zastąpione.

-   Utwórz test jako sekwencja zarejestrowane metody. Aby uzyskać więcej informacji o sposobie rejestrowania metody, zobacz [tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md).

-   Każda metoda zarejestrowane powinna działać na jednej stronie, formularza lub okno dialogowe. Utworzenie nowej metody testów dla każdej nowej strony, formularza lub okno dialogowe.

-   Podczas tworzenia metody należy użyć nazwy metody istotnych zamiast domyślnej nazwy. Znaczącą nazwę pomaga w identyfikacji przeznaczenia metody.

-   Jeśli to możliwe, należy ograniczyć każdego nagraną metodę do mniej niż 10 akcji. To podejście modułowej ułatwia zastąpić metodę, jeśli zmieni się interfejs użytkownika.

-   Tworzenie przy użyciu każdego potwierdzenia **kodowanego testu interfejsu użytkownika**, która automatycznie dodaje metodę potwierdzenie *UIMap.Designer.cs* pliku.

-   Jeśli zmieni się interfejs użytkownika (UI), ponownie zarejestrować metod testowych lub metody asercji, lub ponownie zarejestrować poszczególnych sekcjach istniejącej metody testowej.

-   Utwórz osobne <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> pliku dla każdego modułu w testowanej aplikacji. Aby uzyskać więcej informacji, zobacz [testowanie dużej aplikacji przy użyciu wielu map UI](../test/testing-a-large-application-with-multiple-ui-maps.md).

-   W testowanej aplikacji, użyj nazw opisowych, podczas tworzenia kontrolek interfejsu użytkownika. Za pomocą zrozumiałej nazwy zapewnia większą przejrzystość i użyteczność nazw automatycznie wygenerowanego formantu.

-   Jeśli tworzysz potwierdzenia od kodowania za pomocą interfejsu API, należy utworzyć metodę dla każdego potwierdzenia w części <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> klasę, która znajduje się w *UIMap.cs* pliku. Aby wykonać potwierdzenie, należy wywołać tę metodę ze swojej metody testowej.

-   Jeśli bezpośrednio kodują przy użyciu interfejsu API, użyj właściwości i metod w klasach wygenerowane w *UIMap.Designer.cs* pliku w kodzie, jak możesz. W ramach tych zajęć ułatwi pracę, łatwiejsze i bardziej niezawodne i pomoże Ci osiągnąć bardziej produktywne.

Kodowane testy interfejsu użytkownika automatycznie dostosowywać się do wielu zmian w interfejsie użytkownika. Jeśli na przykład element interfejsu użytkownika został zmieniony, położenie i kolor, w większości przypadków kodowanego testu interfejsu użytkownika będą nadal znaleźć poprawny element.

Podczas przebiegu testu kontrolek interfejsu użytkownika znajduje się w ramach testowania przy użyciu zestawu właściwości wyszukiwania. Właściwości wyszukiwania są stosowane do każdej klasy formantu w definicjach utworzone przez **kodowanego testu interfejsu użytkownika** w *UIMap.Designer.cs* pliku. Właściwości wyszukiwania zawierają pary nazwa / wartość nazw właściwości i wartości właściwości, które mogą służyć do identyfikowania kontrolki, takie jak <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A>, i <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A> właściwości formantu. Jeśli właściwości wyszukiwania nie ulegną zmianie, kodowany test interfejsu użytkownika pomyślnie odnaleźć formantu w interfejsie użytkownika. Zmiana właściwości wyszukiwania kodowane testy interfejsu użytkownika mają algorytmu inteligentnego dopasowania, który stosuje Algorytm heurystyczny w celu znalezienia kontrolek i systemu windows w interfejsie użytkownika. Gdy interfejs użytkownika został zmieniony, może być zmodyfikowanie właściwości wyszukiwania wcześniej zdefiniowane elementy, aby upewnić się, że zostaną znalezione.

## <a name="if-your-user-interface-changes"></a>Jeśli zmieni się interfejs użytkownika

Interfejsy użytkownika, która jest często zmieniać podczas programowania. Oto kilka sposobów, aby zmniejszyć wpływ tych zmian:

-   Znajdowanie nagraną metodę, która odwołuje się do tego formantu oraz używanie **kodowanego testu interfejsu użytkownika** do ponownego rejestrowania akcji dla tej metody. Taką samą nazwę dla metody umożliwia zastąpienie istniejących działań.

-   Jeśli w kontrolce wystąpi potwierdzenie, że nie jest już prawidłowy:

    -   Usuń metodę, która zawiera potwierdzenie.

    -   Usuń wywołanie tej metody z metody testowej.

    -   Dodawanie nowej asercji przeciągając przycisk krzyżyka do kontrolki interfejsu użytkownika, otwórz mapę interfejsu użytkownika i Dodaj nowe potwierdzenie.

Aby uzyskać więcej informacji na temat sposobu rejestrowania kodowane testy interfejsu użytkownika, zobacz [automatyzacji w użyciu interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md).

## <a name="if-a-background-process-needs-to-complete-before-the-test-can-continue"></a>Jeśli proces w tle potrzebuje do wykonania przed rozpoczęciem badania można kontynuować

Trzeba będzie poczekać, aż do zakończenia procesu, przed kontynuowaniem do następnej akcji interfejsu użytkownika. Można użyć w tym celu <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A> oczekiwania na zakończenie testu będzie się powtarzał, jak w poniższym przykładzie:

```csharp
// Set the playback to wait for all threads to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.AllThreads;

// Press the submit button
this.UIMap.ClickSubmit();

// Reset the playback to wait only for the UI thread to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.UIThreadOnly;
```

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>
- <xref:Microsoft.VisualStudio.TestTools.UITesting>
- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md)
- [Testowanie dużej aplikacji przy użyciu wielu map UI](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)