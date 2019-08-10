---
title: Korzystanie z różnych przeglądarek sieci Web do przeprowadzania kodowanych testów interfejsu użytkownika
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 1b7cad6d52dc3fabc182881b99163cf15e1a260c
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926570"
---
# <a name="use-different-web-browsers-with-coded-ui-tests"></a>Korzystanie z różnych przeglądarek sieci Web z kodowanymi testami interfejsu użytkownika

Zakodowane testy interfejsu użytkownika mogą zautomatyzować testowanie aplikacji internetowych przez rejestrowanie testów przy użyciu przeglądarki Internet Explorer. Następnie można dostosować swoje badania i odtwarzać je za pomocą Internet Explorer lub innego typu przeglądarki dla tych aplikacji internetowych.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

Najpierw zainstaluj [składniki selenu w celu kodowanego testowania wielu przeglądarek interfejsu użytkownika](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

## <a name="whats-supported-across-all-web-browsers"></a>Co jest obsługiwane we wszystkich przeglądarkach sieci Web?

- [Dodaj niestandardowy kod służący do sterowania funkcjami](https://devblogs.microsoft.com/devops/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer/) , takimi jak właściwości, wyszukiwanie i odczekania odtwarzania.

- Wyskakujące okienka i okna dialogowe

- [Wykonaj podstawowe skrypty JavaScript bez zwracanego typu](https://devblogs.microsoft.com/devops/introducing-javascript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test/)

- Odporność wyszukiwania (przy użyciu inteligentnych odpowiedników) i [ulepszenia wydajności](https://devblogs.microsoft.com/devops/guidelines-on-improving-performance-of-coded-ui-test-playback/)

## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>Dlaczego należy używać zakodowanych testów interfejsu użytkownika w kilku przeglądarkach sieci Web?

Testując aplikację internetową za pomocą przeglądarek internetowych różnego typu, można lepiej emulować doświadczenia z interfejsem użytkowników korzystających z różnych przeglądarek. Na przykład aplikacja może zawierać formant lub kod w Internet Explorer, który nie jest zgodny z innymi przeglądarkami sieci Web. Uruchamianie kodowanych testów interfejsu użytkownika w różnych przeglądarkach pozwoli wykryć i naprawić wszelkie problemy, zanim wpłyną one na doświadczenia klientów.

## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>Jak nagrywać i odtwarzać kodowane testy interfejsu użytkownika w aplikacjach internetowych przy użyciu obsługiwanych przeglądarek internetowych?

**Zapisywanie** Musisz użyć konstruktora kodowanego testu interfejsu użytkownika, aby nagrać test aplikacji sieci Web przy użyciu programu Internet Explorer. Można opcjonalnie dodać sprawdzanie poprawności i niestandardowy kod dla formantów testowanych przy użyciu wstępnie zdefiniowanego zestawu właściwości, jak zwykle w przypadku kodowanych testów interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md).

> [!NOTE]
> Nie można zarejestrować zakodowanych testów interfejsu użytkownika przy użyciu przeglądarek Google Chrome i Mozilla Firefox.

**Odtwórz z programem Internet Explorer:** Jeśli żadna przeglądarka nie jest jawnie określona, testy będą domyślnie uruchamiane w programie Internet Explorer. Można jawnie ustawić przeglądarkę, aby była używana przez ustawienie właściwości **BrowserWindow. CurrentBrowser** w kodzie testowym. W przypadku programu Internet Explorer ta właściwość powinna być ustawiona na **IE** lub **Internet Explorer**.

**Odtwórz w przeglądarkach sieci Web programu innych niż Internet Explorer:** Aby odtwarzać w przeglądarkach sieci Web innych niż Internet Explorer, Zmień właściwość BrowserWindow. CurrentBrowser w kodzie testowym na **Firefox** lub **Chrome**.

Aby odtworzyć testy w przeglądarkach sieci Web bez programu IE, należy zainstalować **składniki selenu dla kodowanego testowania między przeglądarkami interfejsu użytkownika**.

### <a name="install-selenium-components"></a>Zainstaluj składniki selenu

::: moniker range="vs-2017"

1. W menu **Narzędzia** wybierz pozycję **rozszerzenia i aktualizacje**.

2. W oknie dialogowym **rozszerzenia i aktualizacje** Wyszukaj ciąg `Selenium components for Cross Browser Testing`.

::: moniker-end

::: moniker range=">=vs-2019"

1. W menu **rozszerzenia** , wybierz **Zarządzanie rozszerzeniami**.

2. W oknie dialogowym **Zarządzanie rozszerzeniami** Wyszukaj ciąg `Selenium components for Cross Browser Testing`.

::: moniker-end

3. Zaznacz rozszerzenie i wybierz pozycję **Pobierz**.

    > [!TIP]
    > Możesz również pobrać składniki selenu dla kodowanego testowania międzyprzeglądarki interfejsu użytkownika z tego [miejsca](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

Aby uzyskać więcej informacji na temat tworzenia i używania kodowanych testów interfejsu użytkownika, zobacz [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md).

### <a name="enable-debugging"></a>Włączanie debugowania

Aby włączyć debugowanie aplikacji internetowej, należy zastosować następujące opcje konfiguracji:

1. Włączyć funkcję Tylko mój kod:

    1. W menu **Narzędzia** wybierz polecenie **Opcje** , a następnie wybierz **debugowanie**.

    2. Wybierz pozycję **włącz tylko mój kod**.

2. Wyłączyć wyjątki CLR:

    1. W menu **debugowanie** wybierz **wyjątki**.

    2. W przypadku **wyjątków środowiska uruchomieniowego języka wspólnego**Usuń zaznaczenie pola nieobsługiwane przez **użytkownika**.

Jeśli nie widzisz opcji zmiany `BrowserWindow.CurrentBrowser` w kodowanym teście interfejsu użytkownika, być może używasz wersji programu Visual Studio, która nie obsługuje kodowanych testów interfejsu użytkownika przy użyciu różnych przeglądarek sieci Web. Aby użyć takich kodowanych testów interfejsu użytkownika, należy użyć wersji Visual Studio Enterprise.

Oto kilka innych rzeczy, które należy znać:

- Przeglądarka Safari firmy Apple nie jest obsługiwana.

- Akcja uruchomienia przeglądarki sieci Web musi być częścią kodowanego testu interfejsu użytkownika.

   Jeśli masz już otwartą przeglądarkę sieci Web i chcesz wykonać w niej te czynności, odtwarzanie zakończy się niepowodzeniem, chyba że używasz Internet Explorer. Dlatego najlepiej uwzględniać uruchamianie przeglądarki sieci Web jako część zakodowanych testów interfejsu użytkownika.

- Automatyzacja funkcjonowania przeglądarki na podstawie działań interfejsu użytkownika, takich jak maksymalizowanie, minimalizowanie i przywracanie, nie jest obsługiwana.

## <a name="tips"></a>Porady

Można skonfigurować dane wyjściowe do uwzględnienia zrzutów ekranu w zakodowanych dziennikach interfejsu użytkownika. Aby to zrobić, należy ustawić niektóre ustawienia konfiguracji w pliku *QTAgent32. exe. config* . Domyślnie ten plik jest instalowany w następującej lokalizacji:

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*

Ustaw następujące wartości:

- `EqtTraceLevel``system.diagnostics` w sekcji.

- `<add name="EqtTraceLevel" value="4" />`

   Ustawiając wartość na 3 lub wyższą, zrzuty ekranu są pobierane dla każdej akcji. Gdy wartość jest równa 1 lub 2, zrzuty ekranu są wykonywane tylko w przypadku błędów.

Aby uzyskać więcej informacji, zobacz [Analizowanie kodowanych testów interfejsu użytkownika za pomocą dzienników kodowanych testów interfejsu użytkownika](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="video-resources"></a>Zasoby wideo

[Rejestruj w programie IE i Odtwarzaj wszędzie](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)

[Twórz testy między przeglądarkami za pomocą konstruktora kodowanego testu interfejsu użytkownika](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)

[Twórz testy między przeglądarkami przy użyciu zwykłego kodowania bez mapowania interfejsu użytkownika](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)

[Uruchamiaj testy wielu przeglądarek sekwencyjnie w wielu przeglądarkach](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)

[Rozwiązywanie problemów z niepowodzeniem testów między przeglądarkami](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)

## <a name="see-also"></a>Zobacz także

- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Analizowanie kodowanych testów interfejsu użytkownika za pomocą dzienników kodowanych testów interfejsu użytkownika](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)
