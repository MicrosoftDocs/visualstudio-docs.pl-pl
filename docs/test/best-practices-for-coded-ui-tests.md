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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565165"
---
# <a name="best-practices-for-coded-ui-tests"></a>Najważniejsze wskazówki dotyczące kodowanych testów interfejsu użytkownika

W tym temacie opisano niektóre zalecenia dotyczące tworzenia kodowanych testów interfejsu użytkownika.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="best-practices"></a>Najlepsze rozwiązania

Skorzystaj z poniższych wskazówek, aby utworzyć elastyczny kodowany test interfejsu użytkownika.

- Użyj **konstruktora testów kodowanych interfejsu użytkownika,** gdy tylko jest to możliwe.

- Nie należy modyfikować pliku *UIMap.designer.cs* bezpośrednio. Jeśli zmodyfikujesz plik, zmiany w pliku zostaną zastąpione.

- Utwórz test jako sekwencję zarejestrowanych metod. Aby uzyskać więcej informacji na temat rejestrowania metody, zobacz [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md).

- Każda zarejestrowana metoda powinna działać na jednej stronie, formularzu lub oknie dialogowym. Utwórz nową metodę testu dla każdej nowej strony, formularza lub okna dialogowego.

- Podczas tworzenia metody należy użyć nazwy metody znaczące zamiast nazwy domyślnej. Miarowa znacząca nazwa pomaga zidentyfikować cel metody.

- Jeśli to możliwe, należy ograniczyć każdą zarejestrowaną metodę do mniej niż 10 akcji. To podejście modułowe ułatwia zastąpienie metody, jeśli ui zmiany.

- Utwórz każde twierdzenie przy użyciu **konstruktora testów interfejsu użytkownika kodowane**, który automatycznie dodaje metodę potwierdzenia do pliku *UIMap.Designer.cs.*

- Jeśli interfejs użytkownika (UI) ulegśnie, ponownie zarejestrować metody testowe lub metody potwierdzenia lub ponownie zarejestrować sekcje, których dotyczy problem istniejącej metody testowej.

- Utwórz oddzielny plik [UIMap](/previous-versions/dd580454(v=vs.140)) dla każdego modułu w testowej aplikacji. Aby uzyskać więcej informacji, zobacz [Testowanie dużej aplikacji z wieloma mapami interfejsu użytkownika.](../test/testing-a-large-application-with-multiple-ui-maps.md)

- W badanej aplikacji należy używać znaczących nazw podczas tworzenia formantów interfejsu użytkownika. Użycie znaczących nazw zapewnia większą przejrzystość i użyteczność automatycznie generowanych nazw formantów.

- Jeśli tworzysz potwierdzenia przez kodowanie za pomocą interfejsu API, utwórz metodę dla każdego potwierdzenia w części klasy [UIMap,](/previous-versions/dd580454(v=vs.140)) która znajduje się w pliku *UIMap.cs.* Aby wykonać asercja, wywołać tę metodę z metody testowej.

- Jeśli bezpośrednio kodowania z interfejsu API, należy użyć właściwości i metody w klasach generowanych w pliku *UIMap.Designer.cs* w kodzie, jak to możliwe. Te klasy sprawią, że twoja praca będzie łatwiejsza, bardziej niezawodna i pomoże Ci być bardziej produktywnym.

Kodowane testy interfejsu użytkownika automatycznie dostosowują się do wielu zmian w interfejsie użytkownika. Jeśli na przykład element interfejsu użytkownika zmienił położenie lub kolor, przez większość czasu kodowany test interfejsu użytkownika nadal znajdzie poprawny element.

Podczas uruchamiania testu formanty interfejsu użytkownika znajdują się przez platformę testowania przy użyciu zestawu właściwości wyszukiwania. Właściwości wyszukiwania są stosowane do każdej klasy formantu w definicjach utworzonych przez **konstruktora testów interfejsu użytkownika kodowanych** w pliku *UIMap.Designer.cs.* Właściwości wyszukiwania zawierają pary nazwa-wartość nazw właściwości i wartości właściwości, które mogą służyć <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A> <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A>do <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A> identyfikowania formantu, takiego jak , i właściwości formantu. Jeśli właściwości wyszukiwania pozostają niezmienione, kodowany test interfejsu użytkownika pomyślnie znajdzie formant w interfejsie użytkownika. Jeśli właściwości wyszukiwania zostaną zmienione, kodowane testy interfejsu użytkownika mają algorytm dopasowania inteligentnego, który stosuje heurystykę, aby znaleźć formanty i okna w interfejsie użytkownika. Po zmianie interfejsu użytkownika można zmodyfikować właściwości wyszukiwania wcześniej zidentyfikowanych elementów, aby upewnić się, że zostały znalezione.

## <a name="if-your-user-interface-changes"></a>Jeśli interfejs użytkownika ulegnie zmianie

Interfejsy użytkownika często zmieniają się podczas tworzenia. Oto kilka sposobów na zmniejszenie efektu tych zmian:

- Znajdź zarejestrowaną metodę, która odwołuje się do tego formantu i użyj **Konstruktora testów kodowanych interfejsu użytkownika,** aby ponownie zarejestrować akcje dla tej metody. Można użyć tej samej nazwy dla metody, aby zastąpić istniejące akcje.

- Jeśli formant ma twierdzenie, które nie jest już prawidłowe:

  - Usuń metodę, która zawiera asercja.

  - Usuń wywołanie tej metody z metody testowej.

  - Dodaj nowe twierdzenie, przeciągając przycisk krzyżyka na kontrolkę interfejsu użytkownika, otwórz mapę interfejsu użytkownika i dodaj nowe twierdzenie.

Aby uzyskać więcej informacji na temat rejestrowania kodowanych testów interfejsu użytkownika, zobacz [Używanie automatyzacji interfejsu użytkownika do testowania kodu.](../test/use-ui-automation-to-test-your-code.md)

## <a name="if-a-background-process-needs-to-complete-before-the-test-can-continue"></a>Jeśli proces w tle musi się zakończyć, zanim test będzie mógł kontynuować

Może być konieczne zaczekanie, aż proces zakończy się, zanim będzie można kontynuować następną akcję interfejsu użytkownika. Aby to zrobić, <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A> można użyć, aby poczekać, zanim test będzie kontynuowany, jak w poniższym przykładzie:

```csharp
// Set the playback to wait for all threads to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.AllThreads;

// Press the submit button
this.UIMap.ClickSubmit();

// Reset the playback to wait only for the UI thread to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.UIThreadOnly;
```

## <a name="see-also"></a>Zobacz też

- [Uimap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting>
- [Użyj automatyzacji interfejsu użytkownika, aby przetestować kod](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md)
- [Testowanie dużej aplikacji z wieloma mapami interfejsu użytkownika](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Obsługiwane konfiguracje i platformy dla zakodowanych testów interfejsu użytkownika i nagrań akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
