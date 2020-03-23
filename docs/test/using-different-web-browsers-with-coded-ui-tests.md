---
title: Korzystanie z różnych przeglądarek sieci Web do przeprowadzania kodowanych testów interfejsu użytkownika
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 104bdcc7a3f609456d521e710ac6ec2aeda2bb75
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585577"
---
# <a name="use-different-web-browsers-with-coded-ui-tests"></a>Używanie różnych przeglądarek internetowych z kodami testów interfejsu użytkownika

Zakodowane testy interfejsu użytkownika mogą zautomatyzować testowanie aplikacji internetowych przez rejestrowanie testów przy użyciu przeglądarki Internet Explorer. Następnie można dostosować swoje badania i odtwarzać je za pomocą Internet Explorer lub innego typu przeglądarki dla tych aplikacji internetowych.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

Najpierw zainstaluj [składniki Selenu do kodowanych testów przeglądarki interfejsu użytkownika](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

## <a name="whats-supported-across-all-web-browsers"></a>Co jest obsługiwane we wszystkich przeglądarkach internetowych?

- [Dodaj niestandardowy kod do kontrolowania funkcji,](https://devblogs.microsoft.com/devops/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer/) takich jak właściwości, wyszukiwanie i kelnerzy odtwarzania.

- Wyskakujące okienka i okna dialogowe

- [Wykonywanie podstawowego języka JavaScript bez typu zwracania](https://devblogs.microsoft.com/devops/introducing-javascript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test/)

- Odporność wyszukiwania (przy użyciu dopasowania inteligentnego) i [poprawa wydajności](https://devblogs.microsoft.com/devops/guidelines-on-improving-performance-of-coded-ui-test-playback/)

## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>Dlaczego należy używać zakodowanych testów interfejsu użytkownika w kilku przeglądarkach sieci Web?

Testując aplikację internetową za pomocą przeglądarek internetowych różnego typu, można lepiej emulować doświadczenia z interfejsem użytkowników korzystających z różnych przeglądarek. Na przykład aplikacja może zawierać formant lub kod w Internet Explorer, który nie jest zgodny z innymi przeglądarkami sieci Web. Uruchamianie kodowanych testów interfejsu użytkownika w różnych przeglądarkach pozwoli wykryć i naprawić wszelkie problemy, zanim wpłyną one na doświadczenia klientów.

## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>Jak nagrywać i odtwarzać kodowane testy interfejsu użytkownika w aplikacjach internetowych przy użyciu obsługiwanych przeglądarek internetowych?

**Nagrywanie:** Do rejestrowania testu aplikacji sieci web za pomocą programu Internet Explorer należy użyć konstruktora kodowanych testów interfejsu użytkownika. Można opcjonalnie dodać sprawdzanie poprawności i niestandardowy kod dla formantów testowanych przy użyciu wstępnie zdefiniowanego zestawu właściwości, jak zwykle w przypadku kodowanych testów interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md).

> [!NOTE]
> Nie można zarejestrować zakodowanych testów interfejsu użytkownika przy użyciu przeglądarek Google Chrome i Mozilla Firefox.

**Odtwarzanie za pomocą programu Internet Explorer:** Jeśli żadna przeglądarka nie jest jawnie określona, testy będą domyślnie uruchamiane w programie Internet Explorer. Można jawnie podać przeglądarkę, która ma być używana przez ustawienie **BrowserWindow.CurrentBrowser** właściwości w kodzie testowym. W programie Internet Explorer ta właściwość powinna być ustawiona na **IE** lub **Internet Explorer**.

**Odtwarzanie w przeglądarkach internetowych innych niż Internet Explorer:** Aby odtworzyć w przeglądarkach internetowych innych niż Internet Explorer, zmień właściwość BrowserWindow.CurrentBrowser w kodzie testowym na **Firefox** lub **Chrome**.

Aby odtworzyć testy w przeglądarkach internetowych innych niż IE, należy zainstalować **składniki Selenu do testowania przeglądarki kodowanych interfejsów użytkownika.**

### <a name="install-selenium-components"></a>Instalowanie komponentów Selenu

::: moniker range="vs-2017"

1. W menu **Narzędzia** wybierz polecenie **Rozszerzenia i aktualizacje**.

2. W oknie dialogowym Rozszerzenia i `Selenium components for Cross Browser Testing` **aktualizacje** wyszukaj hasło .

::: moniker-end

::: moniker range=">=vs-2019"

1. W menu **Rozszerzenia** wybierz polecenie **Zarządzaj rozszerzeniami**.

2. W oknie dialogowym **Zarządzanie rozszerzeniami** wyszukaj hasło `Selenium components for Cross Browser Testing`.

::: moniker-end

3. Wyróżnij rozszerzenie i wybierz pozycję **Pobierz**.

    > [!TIP]
    > Można również pobrać składniki Selenu dla kodowanych testów przeglądarki krzyżowej interfejsu [użytkownika tutaj](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

Aby uzyskać więcej informacji na temat tworzenia kodowanych testów interfejsu użytkownika i używania ich, zobacz [Tworzenie kodowanych testów interfejsu użytkownika.](../test/use-ui-automation-to-test-your-code.md)

### <a name="enable-debugging"></a>Włączanie debugowania

Aby włączyć debugowanie aplikacji internetowej, należy zastosować następujące opcje konfiguracji:

1. Włączyć funkcję Tylko mój kod:

    1. W menu **Narzędzia** wybierz polecenie **Opcje,** a następnie wybierz polecenie **Debugowanie**.

    2. Wybierz **pozycję Włącz tylko mój kod**.

2. Wyłączyć wyjątki CLR:

    1. W menu **Debugowanie** wybierz polecenie **Wyjątki**.

    2. W przypadku **wyjątków środowiska uruchomieniowego języka wspólnego**odznacz niezachwyć nieobsługiwalne **opcje użytkownika**.

Jeśli nie widzisz opcji zmiany `BrowserWindow.CurrentBrowser` w kodowany test interfejsu użytkownika, może być przy użyciu wersji programu Visual Studio, która nie obsługuje kodowanych testów interfejsu użytkownika przy użyciu różnych przeglądarek sieci web. Aby użyć takich kodowanych testów interfejsu użytkownika, należy użyć programu Visual Studio Enterprise edition.

Oto kilka innych rzeczy, które powinieneś wiedzieć:

- Przeglądarka Safari firmy Apple nie jest obsługiwana.

- Akcja uruchomienia przeglądarki sieci Web musi być częścią kodowanego testu interfejsu użytkownika.

   Jeśli masz już otwartą przeglądarkę sieci Web i chcesz wykonać w niej te czynności, odtwarzanie zakończy się niepowodzeniem, chyba że używasz Internet Explorer. Dlatego najlepiej uwzględniać uruchamianie przeglądarki sieci Web jako część zakodowanych testów interfejsu użytkownika.

- Automatyzacja funkcjonowania przeglądarki na podstawie działań interfejsu użytkownika, takich jak maksymalizowanie, minimalizowanie i przywracanie, nie jest obsługiwana.

## <a name="tips"></a>Porady

Można skonfigurować dane wyjściowe do uwzględnienia zrzutów ekranu w zakodowanych dziennikach interfejsu użytkownika. Aby to zrobić, należy ustawić niektóre ustawienia konfiguracji w pliku *QTAgent32.exe.config.* Domyślnie ten plik jest instalowany w następującej lokalizacji:

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*

Ustaw następujące wartości:

- `EqtTraceLevel`w `system.diagnostics` sekcji.

- `<add name="EqtTraceLevel" value="4" />`

   Ustawiając wartość na 3 lub wyższą, dla każdej akcji są pobierane zrzuty ekranu. Gdy wartość jest równa 1 lub 2, zrzuty ekranu są wykonywane tylko w przypadku błędów.

Aby uzyskać więcej informacji, zobacz [Analizowanie zakodowanych testów interfejsu użytkownika przy użyciu kodowanych dzienników testów interfejsu użytkownika](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="video-resources"></a>Zasoby wideo

[Nagrywanie na IE i odtwarzanie wszędzie](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)

[Autor testów przeglądarki krzyżowej z kodowanym konstruktorem testów interfejsu użytkownika](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)

[Autor cross browser testy przy użyciu zwykłego kodowania ręcznego bez mapy interfejsu użytkownika](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)

[Uruchamianie testów między przeglądarkami sekwencyjnie w wielu przeglądarkach](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)

[Rozwiązywanie problemów z błędami testów między przeglądarkami](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)

## <a name="see-also"></a>Zobacz też

- [Użyj automatyzacji interfejsu użytkownika, aby przetestować kod](../test/use-ui-automation-to-test-your-code.md)
- [Obsługiwane konfiguracje i platformy dla zakodowanych testów interfejsu użytkownika i nagrań akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Analizowanie zakodowanych testów interfejsu użytkownika przy użyciu kodowanych dzienników testów interfejsu użytkownika](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)
