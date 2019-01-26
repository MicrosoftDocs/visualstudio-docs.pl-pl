---
title: Korzystanie z różnych przeglądarek sieci Web do przeprowadzania kodowanych testów interfejsu użytkownika
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: afbcd419f1890e3414d0076d0a4664df5f941938
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55036241"
---
# <a name="use-different-web-browsers-with-coded-ui-tests"></a>Użyj innej przeglądarki za pomocą kodowanych testów interfejsu użytkownika

Zakodowane testy interfejsu użytkownika mogą zautomatyzować testowanie aplikacji internetowych przez rejestrowanie testów przy użyciu przeglądarki Internet Explorer. Następnie można dostosować swoje badania i odtwarzać je za pomocą Internet Explorer lub innego typu przeglądarki dla tych aplikacji internetowych.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

Najpierw zainstaluj [Selenium components for coded UI cross testowania przeglądarki](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

## <a name="whats-supported-across-all-web-browsers"></a>Co jest obsługiwane we wszystkich przeglądarkach sieci web?

-   [Dodawanie kodu niestandardowego w celu kontrolowania funkcji](https://blogs.msdn.microsoft.com/devops/2012/12/09/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer/) takie jak obiekty właściwości, wyszukiwanie i odtwarzania.

-   Wyskakujące okienka i okna dialogowe

-   [Wykonaj podstawowy kod JavaScript bez zwrotu typu](https://blogs.msdn.microsoft.com/devops/2013/01/18/introducing-javascript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test/)

-   Wyszukaj tolerancję (za pomocą inteligentnego dopasowania) i [ulepszenia wydajności](https://blogs.msdn.microsoft.com/devops/2012/01/31/guidelines-on-improving-performance-of-coded-ui-test-playback/)

## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>Dlaczego należy używać zakodowanych testów interfejsu użytkownika w kilku przeglądarkach sieci Web?

Testując aplikację internetową za pomocą przeglądarek internetowych różnego typu, można lepiej emulować doświadczenia z interfejsem użytkowników korzystających z różnych przeglądarek. Na przykład aplikacja może zawierać formant lub kod w Internet Explorer, który nie jest zgodny z innymi przeglądarkami sieci Web. Uruchamianie kodowanych testów interfejsu użytkownika w różnych przeglądarkach pozwoli wykryć i naprawić wszelkie problemy, zanim wpłyną one na doświadczenia klientów.

## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>Jak nagrywać i odtwarzać kodowane testy interfejsu użytkownika w aplikacjach internetowych przy użyciu obsługiwanych przeglądarek internetowych?

**Rejestrowanie:** Konstruktor kodowanego testu IU należy użyć, aby nagrać test aplikacji sieci web za pomocą programu Internet Explorer. Można opcjonalnie dodać sprawdzanie poprawności i niestandardowy kod dla formantów testowanych przy użyciu wstępnie zdefiniowanego zestawu właściwości, jak zwykle w przypadku kodowanych testów interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [automatyzacji w użyciu interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md).

> [!NOTE]
> Nie można zarejestrować zakodowanych testów interfejsu użytkownika przy użyciu przeglądarek Google Chrome i Mozilla Firefox.

 **Odtwarzanie z programem Internet Explorer:** Przeglądarka nie jest jawnie określona, testy będą uruchamiane w programie Internet Explorer domyślnie. Można jawnie określać przeglądarki, który będzie używany przez ustawienie **BrowserWindow.CurrentBrowser** właściwości w kodzie testowym. Dla programu Internet Explorer ta właściwość powinna być równa **IE** lub **programu Internet Explorer**.

 **Odtwarzanie z przeglądarek sieci web innych niż Internet Explorer:** Aby odtwarzać w przeglądarkach sieci web innych niż Internet Explorer, należy zmienić właściwość BrowserWindow.CurrentBrowser w kodzie testowym na albo **Firefox** lub **Chrome**.

 Aby odtwarzać testy w przeglądarkach sieci web-IE, należy zainstalować **Selenium components for Coded UI Cross Browser Testing**.

### <a name="install-selenium-components"></a>Instalowanie składników Selenium

1.  Na **narzędzia** menu, wybierz **rozszerzenia i aktualizacje**.

2.  W **rozszerzenia i aktualizacje** okno dialogowe, wyszukaj `Selenium components for Cross Browser Testing`.

3.  Zaznacz rozszerzenie i wybierz polecenie **Pobierz**.

    > [!TIP]
    > Możesz również pobrać narzędzie Selenium components for Coded UI Cross Browser Testing z [tutaj](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

Aby uzyskać więcej informacji na temat tworzenia i używania kodowanego interfejsu użytkownika, testów, zobacz [tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md).

### <a name="enable-debugging"></a>Włączanie debugowania

Aby włączyć debugowanie aplikacji internetowej, należy zastosować następujące opcje konfiguracji:

1.  Włączyć funkcję Tylko mój kod:

    1.  Na **narzędzia** menu, wybierz **opcje** , a następnie wybierz **debugowanie**.

    2.  Wybierz **Włącz tylko mój kod**.

2.  Wyłączyć wyjątki CLR:

    1.  Na **debugowania** menu, wybierz **wyjątki**.

    2.  Aby uzyskać **wyjątki środowiska uruchomieniowego języka wspólnego**, usuń zaznaczenie pola wyboru **User-unhandled**.

Jeśli nie jest widoczna opcja zmiany `BrowserWindow.CurrentBrowser` w kodowanym teście interfejsu użytkownika, być może używasz wersji programu Visual Studio, który nie obsługuje kodowanych testów interfejsu użytkownika za pomocą różnych przeglądarek sieci web. Aby używać takich kodowanych testów interfejsu użytkownika, należy użyć programu Visual Studio Enterprise edition.

Poniżej przedstawiono niektóre inne czynności, które należy znać:

- Przeglądarka Safari firmy Apple nie jest obsługiwana.

- Akcja uruchomienia przeglądarki sieci Web musi być częścią kodowanego testu interfejsu użytkownika.

   Jeśli masz już otwartą przeglądarkę sieci Web i chcesz wykonać w niej te czynności, odtwarzanie zakończy się niepowodzeniem, chyba że używasz Internet Explorer. Dlatego najlepiej uwzględniać uruchamianie przeglądarki sieci Web jako część zakodowanych testów interfejsu użytkownika.

- Automatyzacja funkcjonowania przeglądarki na podstawie działań interfejsu użytkownika, takich jak maksymalizowanie, minimalizowanie i przywracanie, nie jest obsługiwana.

## <a name="tips"></a>Porady

Można skonfigurować dane wyjściowe do uwzględnienia zrzutów ekranu w zakodowanych dziennikach interfejsu użytkownika. Aby to zrobić, należy ustawić niektóre ustawienia konfiguracji *QTAgent32.exe.config* pliku. Domyślnie ten plik jest instalowany w następującej lokalizacji:

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*

Ustaw następujące wartości:

- `EqtTraceLevel` w `system.diagnostics` sekcji.

- `<add name="EqtTraceLevel" value="4" />`

   Ustawiając wartość 3 lub większą, zrzuty ekranu są pobierane dla każdej akcji. Gdy wartość jest równa 1 lub 2, zrzuty ekranu są wykonywane tylko w przypadku błędów.

Aby uzyskać więcej informacji, zobacz [analizowanie kodowanych testów interfejsu użytkownika, za pomocą zakodowanych dziennikach testów interfejsu użytkownika](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="video-resources"></a>Zasoby wideo

 [Nagrywanie w przeglądarce IE i odtwarzanie wszędzie](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)

 [Autorskie testy krzyżowe przeglądarki za pomocą konstruktora kodowanego testu interfejsu użytkownika](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)

 [Autorskie testy krzyżowe przeglądarki za pomocą strony zwykłego kodowania bez mapy interfejsu użytkownika](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)

 [Uruchamianie krzyżowych testów przeglądarki kolejno w różnych przeglądarkach](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)

 [Rozwiązywanie problemów z wielu niepowodzeń testów przeglądarki](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)

## <a name="see-also"></a>Zobacz także

- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Analizowanie kodowanych testów interfejsu użytkownika za pomocą zakodowanych dziennikach testów interfejsu użytkownika](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)
