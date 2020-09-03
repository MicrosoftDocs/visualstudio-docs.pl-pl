---
title: Korzystanie z różnych przeglądarek sieci Web z kodowanymi testami interfejsu użytkownika | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: a859595f-6517-43f2-9d61-c706cb55a388
caps.latest.revision: 25
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5234dddad13ccb52cc653a68ad1c35370a4eae18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "82586333"
---
# <a name="using-different-web-browsers-with-coded-ui-tests"></a>Korzystanie z różnych przeglądarek sieci Web do przeprowadzania kodowanych testów interfejsu użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zakodowane testy interfejsu użytkownika mogą zautomatyzować testowanie aplikacji internetowych przez rejestrowanie testów przy użyciu przeglądarki Internet Explorer. Następnie można dostosować swoje badania i odtwarzać je za pomocą Internet Explorer lub innego typu przeglądarki dla tych aplikacji internetowych.

 **Wymagania**

- Visual Studio Enterprise

- Systemy operacyjne:

  - Microsoft Windows 7

  - System Microsoft Windows 8

  - Microsoft Windows Server 2008 R2 SP1

- Wersje przeglądarki sieci Web:

  - Windows Internet Explorer 9

  - Windows Internet Explorer 10

  - Aby zapoznać się z obsługiwanymi wersjami przeglądarki Mozilla Firefox i Google Chrome, przejdź [tutaj](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting)

- Zainstaluj [składniki selenu do kodowanego testowania wielu przeglądarek interfejsu użytkownika](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

  **Co jest obsługiwane we wszystkich przeglądarkach sieci Web?**

- [Dodaj niestandardowy kod służący do sterowania funkcjami](https://devblogs.microsoft.com/devops/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer/) , takimi jak właściwości, wyszukiwanie i odczekania odtwarzania.

- Wyskakujące okienka i okna dialogowe

- [Wykonaj podstawowe skrypty JavaScript bez zwracanego typu](https://devblogs.microsoft.com/devops/introducing-javascript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test/)

- Odporność wyszukiwania (przy użyciu inteligentnych odpowiedników) i [ulepszenia wydajności](https://devblogs.microsoft.com/devops/guidelines-on-improving-performance-of-coded-ui-test-playback/)

## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>Dlaczego należy używać zakodowanych testów interfejsu użytkownika w kilku przeglądarkach sieci Web?
 Testując aplikację internetową za pomocą przeglądarek internetowych różnego typu, można lepiej emulować doświadczenia z interfejsem użytkowników korzystających z różnych przeglądarek. Na przykład aplikacja może zawierać formant lub kod w Internet Explorer, który nie jest zgodny z innymi przeglądarkami sieci Web. Uruchamianie kodowanych testów interfejsu użytkownika w różnych przeglądarkach pozwoli wykryć i naprawić wszelkie problemy, zanim wpłyną one na doświadczenia klientów.

## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>Jak nagrywać i odtwarzać kodowane testy interfejsu użytkownika w aplikacjach internetowych przy użyciu obsługiwanych przeglądarek internetowych?
 **Nagrywanie:** Musisz użyć konstruktora kodowanego testu interfejsu użytkownika, aby nagrać test aplikacji sieci Web przy użyciu programu Internet Explorer. Można opcjonalnie dodać sprawdzanie poprawności i niestandardowy kod dla formantów testowanych przy użyciu wstępnie zdefiniowanego zestawu właściwości, jak zwykle w przypadku kodowanych testów interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md).

> [!NOTE]
> Nie można zarejestrować zakodowanych testów interfejsu użytkownika przy użyciu przeglądarek Google Chrome i Mozilla Firefox.

 **Odtwórz z programem Internet Explorer:** Jeśli żadna przeglądarka nie jest jawnie określona, testy będą domyślnie uruchamiane w programie Internet Explorer. Można jawnie ustawić przeglądarkę, aby była używana przez ustawienie właściwości **BrowserWindow. CurrentBrowser** w kodzie testowym. W przypadku programu Internet Explorer ta właściwość powinna być ustawiona na **IE** lub **Internet Explorer**.

 **Odtwórz w przeglądarkach sieci Web programu innych niż Internet Explorer:** Aby odtwarzać w przeglądarkach sieci Web innych niż Internet Explorer, Zmień właściwość BrowserWindow. CurrentBrowser w kodzie testowym na **Firefox** lub **Chrome**.

 Aby odtworzyć testy w przeglądarkach sieci Web bez programu IE, należy zainstalować **składniki selenu dla kodowanego testowania między przeglądarkami interfejsu użytkownika**.

#### <a name="installing-selenium-components"></a>Instalowanie składników środowiska Selenium

1. W menu **Narzędzia** wybierz pozycję **rozszerzenia i aktualizacje**.

2. W oknie dialogowym rozszerzenia i aktualizacje Wyszukaj ciąg `Selenium components for Cross Browser Testing` .

3. Zaznacz rozszerzenie i wybierz pozycję **Pobierz**.

   > [!TIP]
   > Możesz również pobrać składniki selenu dla kodowanego testowania międzyprzeglądarki interfejsu użytkownika z tego [miejsca](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

   Aby uzyskać więcej informacji na temat tworzenia i używania kodowanych testów interfejsu użytkownika, zobacz [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).

### <a name="enable-debugging"></a>Włączanie debugowania
 Aby włączyć debugowanie aplikacji internetowej, należy zastosować następujące opcje konfiguracji:

1. Włączyć funkcję Tylko mój kod:

    1. W menu **Narzędzia** wybierz polecenie **Opcje** , a następnie wybierz **debugowanie**.

    2. Wybierz pozycję **włącz tylko mój kod**.

2. Wyłączyć wyjątki CLR:

    1. W menu **debugowanie** wybierz **wyjątki**.

    2. W przypadku **wyjątków środowiska uruchomieniowego języka wspólnego**Usuń zaznaczenie pola **nieobsługiwane przez użytkownika**.

## <a name="i-dont-see-the-option-to-change-browserwindowcurrentbrowser-in-the-coded-ui-test"></a><a name="generate"></a>*Nie widzę opcji zmiany BrowserWindow. CurrentBrowser w kodowanym teście interfejsu użytkownika.*
 Być może używasz wersji programu [!INCLUDE[vs2011_first](../includes/vs2011-first-md.md)] , która nie obsługuje kodowanych testów interfejsu użytkownika przy użyciu różnych przeglądarek sieci Web. Aby użyć takich kodowanych testów interfejsu użytkownika, należy użyć Visual Studio Enterprise.

 *Co jeszcze mam wiedzieć?*
 **Uwagi**

- ![Prerequsite](../test/media/prereq.png "Ignoruj") Przeglądarka internetowa Apple Safari nie jest obsługiwana.

- ![Prerequsite](../test/media/prereq.png "Ignoruj") Akcja uruchamiania przeglądarki sieci Web musi być częścią kodowanego testu interfejsu użytkownika.

   Jeśli masz już otwartą przeglądarkę sieci Web i chcesz wykonać w niej te czynności, odtwarzanie zakończy się niepowodzeniem, chyba że używasz Internet Explorer. Dlatego najlepiej uwzględniać uruchamianie przeglądarki sieci Web jako część zakodowanych testów interfejsu użytkownika.

- ![Prerequsite](../test/media/prereq.png "Ignoruj") Automatyzacja specyficznych dla przeglądarki akcji interfejsu użytkownika, takich jak Maksymalizuj, Minimalizuj i Przywróć nie jest obsługiwana.

  **Pomoc**

- ![Porada](../test/media/tip.png "Porada") Dane wyjściowe można skonfigurować tak, aby obejmowały zrzuty ekranu w kodowanych dziennikach interfejsu użytkownika. Aby to zrobić, należy zmienić kilka ustawień konfiguracji w pliku QTAgent32.exe.config. Domyślnie ten plik jest instalowany w następującej lokalizacji:

   **C:\Program Files (x86) \Microsoft Visual Studio 11.0 \ Common7\IDE**

   Ustaw następujące wartości:

  - `EqtTraceLevel` w `system.diagnostics` sekcji.

  - `<add name="EqtTraceLevel" value="4" />`

     Ustawiając wartość 3 lub większą, zrzuty ekranu są pobierane dla każdego działania. Gdy wartość jest równa 1 lub 2, zrzuty ekranu są wykonywane tylko w przypadku błędów.

    Aby uzyskać więcej informacji, zobacz [Analizowanie kodowanych testów interfejsu użytkownika za pomocą dzienników kodowanych testów interfejsu użytkownika](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="external-resources"></a>Zasoby zewnętrzne

### <a name="videos"></a>Filmy wideo
 [Rejestruj w programie IE i Odtwarzaj wszędzie](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)

 [Twórz testy między przeglądarkami za pomocą konstruktora kodowanego testu interfejsu użytkownika](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)

 [Twórz testy między przeglądarkami przy użyciu zwykłego kodowania bez mapowania interfejsu użytkownika](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)

 [Uruchamiaj testy wielu przeglądarek sekwencyjnie w wielu przeglądarkach](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)

 [Rozwiązywanie problemów z niepowodzeniem testów między przeglądarkami](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)

### <a name="guidance"></a>Wskazówki
 [Testowanie w celu ciągłego dostarczania za pomocą programu Visual Studio 2012 — Rozdział 2: testowanie jednostkowe: testowanie wewnątrz](https://msdn.microsoft.com/library/jj159340.aspx)

 [Testowanie w celu ciągłego dostarczania za pomocą programu Visual Studio 2012 — Rozdział 5: Automatyzowanie testów systemowych](https://msdn.microsoft.com/library/jj159335.aspx)

### <a name="faq"></a>Najczęściej zadawane pytania
 [Kodowane testy interfejsu użytkownika — często zadawane pytania — 1](https://docs.microsoft.com/archive/blogs/mathew_aniyan/content-index-for-coded-ui-test)

 [Kodowane testy interfejsu użytkownika — często zadawane pytania — 2](https://social.msdn.microsoft.com/Forums/en-US/vsautotest/thread/3a74dd2c-cef8-4923-abbf-7a91f489e6c4)

### <a name="forum"></a>Forum
 [Testowanie automatyzacji interfejsu użytkownika programu Visual Studio (w tym kodowany interfejs użytkownika)](https://social.msdn.microsoft.com/Forums/en-US/vsautotest)

## <a name="see-also"></a>Zobacz też
 [Używanie automatyzacji interfejsu użytkownika do testowania](../test/use-ui-automation-to-test-your-code.md) [konfiguracji i platform obsługiwanych przez kod dla KODOWANYCH testów interfejsu użytkownika oraz nagrań akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md) [Analizowanie kodowanych testów interfejsu użytkownika za pomocą dzienników kodowanych](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md) testów interfejsu użytkownika
