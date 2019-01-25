---
title: Przy użyciu innej przeglądarki, za pomocą kodowanych testów interfejsu użytkownika | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: a859595f-6517-43f2-9d61-c706cb55a388
caps.latest.revision: 25
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c7245af090cfdaa8e4282677c8b5a052d63b63e2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54805537"
---
# <a name="using-different-web-browsers-with-coded-ui-tests"></a>Korzystanie z różnych przeglądarek sieci Web do przeprowadzania kodowanych testów interfejsu użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zakodowane testy interfejsu użytkownika mogą zautomatyzować testowanie aplikacji internetowych przez rejestrowanie testów przy użyciu przeglądarki Internet Explorer. Następnie można dostosować swoje badania i odtwarzać je za pomocą Internet Explorer lub innego typu przeglądarki dla tych aplikacji internetowych.  
  
 **Wymagania**  
  
- Visual Studio Enterprise  
  
- Systemy operacyjne:  
  
  -   Microsoft Windows 7  
  
  -   Microsoft Windows 8  
  
  -   Microsoft Windows Server 2008 R2 SP1  
  
- Wersje przeglądarki sieci Web:  
  
  -   Windows Internet Explorer 9  
  
  -   Windows Internet Explorer 10  
  
  -   Obsługiwane wersje Mozilla Firefox i Google Chrome, przejdź [tutaj](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/)  
  
- Zainstaluj [Selenium components for Coded UI Cross Browser Testing](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/).  
  
  **Co jest obsługiwane we wszystkich przeglądarkach sieci web?**  
  
- [Dodawanie kodu niestandardowego w celu kontrolowania funkcji](http://blogs.msdn.com/b/visualstudioalm/archive/2012/12/10/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer.aspx) takie jak obiekty właściwości, wyszukiwanie i odtwarzania.  
  
- Wyskakujące okienka i okna dialogowe  
  
- [Wykonaj podstawowy kod JavaScript bez zwrotu typu](http://blogs.msdn.com/b/visualstudioalm/archive/2013/01/18/introducing-jscript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test.aspx)  
  
- Wyszukaj tolerancję (za pomocą inteligentnego dopasowania) i [ulepszenia wydajności](http://blogs.msdn.com/b/visualstudioalm/archive/2012/02/01/guidelines-on-improving-performance-of-coded-ui-test-playback.aspx)  
  
## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>Dlaczego należy używać zakodowanych testów interfejsu użytkownika w kilku przeglądarkach sieci Web?  
 Testując aplikację internetową za pomocą przeglądarek internetowych różnego typu, można lepiej emulować doświadczenia z interfejsem użytkowników korzystających z różnych przeglądarek. Na przykład aplikacja może zawierać formant lub kod w Internet Explorer, który nie jest zgodny z innymi przeglądarkami sieci Web. Uruchamianie kodowanych testów interfejsu użytkownika w różnych przeglądarkach pozwoli wykryć i naprawić wszelkie problemy, zanim wpłyną one na doświadczenia klientów.  
  
## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>Jak nagrywać i odtwarzać kodowane testy interfejsu użytkownika w aplikacjach internetowych przy użyciu obsługiwanych przeglądarek internetowych?  
 **Rejestrowanie:** Konstruktor kodowanego testu IU należy użyć, aby nagrać test aplikacji sieci web za pomocą programu Internet Explorer. Można opcjonalnie dodać sprawdzanie poprawności i niestandardowy kod dla formantów testowanych przy użyciu wstępnie zdefiniowanego zestawu właściwości, jak zwykle w przypadku kodowanych testów interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [Użyj interfejsu użytkownika do testów Your kodu automatyzacji](../test/use-ui-automation-to-test-your-code.md).  
  
> [!NOTE]
>  Nie można zarejestrować zakodowanych testów interfejsu użytkownika przy użyciu przeglądarek Google Chrome i Mozilla Firefox.  
  
 **Odtwarzanie z programem Internet Explorer:** Przeglądarka nie jest jawnie określona, testy będą uruchamiane w programie Internet Explorer domyślnie. Można jawnie określać przeglądarki, który będzie używany przez ustawienie **BrowserWindow.CurrentBrowser** właściwości w kodzie testowym. Dla programu Internet Explorer ta właściwość powinna być równa **IE** lub **programu Internet Explorer**.  
  
 **Odtwarzanie z przeglądarek sieci web innych niż Internet Explorer:** Aby odtwarzać w przeglądarkach sieci web innych niż Internet Explorer, należy zmienić właściwość BrowserWindow.CurrentBrowser w kodzie testowym na albo **Firefox** lub **Chrome**.  
  
 Aby odtwarzać testy w przeglądarkach sieci web-IE, należy zainstalować **Selenium components for Coded UI Cross Browser Testing**.  
  
#### <a name="installing-selenium-components"></a>Instalowanie składników środowiska Selenium  
  
1. Na **narzędzia** menu, wybierz **rozszerzenia i aktualizacje**.  
  
2. W oknie dialogowym rozszerzenia i aktualizacje Wyszukaj `Selenium components for Cross Browser Testing`.  
  
3. Zaznacz rozszerzenie i wybierz polecenie **Pobierz**.  
  
   > [!TIP]
   >  Możesz również pobrać narzędzie Selenium components for Coded UI Cross Browser Testing z [tutaj](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/).  
  
   Aby uzyskać więcej informacji na temat tworzenia i używania kodowanego interfejsu użytkownika, testów, zobacz [tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
### <a name="enable-debugging"></a>Włączanie debugowania  
 Aby włączyć debugowanie aplikacji internetowej, należy zastosować następujące opcje konfiguracji:  
  
1.  Włączyć funkcję Tylko mój kod:  
  
    1.  Na **narzędzia** menu, wybierz **opcje** , a następnie wybierz **debugowanie**.  
  
    2.  Wybierz **Włącz tylko mój kod**.  
  
2.  Wyłączyć wyjątki CLR:  
  
    1.  Na **debugowania** menu, wybierz **wyjątki**.  
  
    2.  Aby uzyskać **wyjątki środowiska uruchomieniowego języka wspólnego**, usuń zaznaczenie pola wyboru **User-unhandled**.  
  
##  <a name="generate"></a> *Opcja zmiany BrowserWindow.CurrentBrowser w kodowanym teście interfejsu użytkownika nie jest widoczna.*  
 Być może używasz wersji [!INCLUDE[vs2011_first](../includes/vs2011-first-md.md)] , który nie obsługuje kodowanych testów interfejsu użytkownika za pomocą różnych przeglądarek sieci web. Aby używać takich kodowanych testów interfejsu użytkownika, należy użyć programu Visual Studio Enterprise.  
  
 *Co jeszcze muszę wiedzieć?*  
 **Uwagi**  
  
- ![Wymagań wstępnych](../test/media/prereq.png "wstępnie wymagany składnik") przeglądarka Safari firmy Apple nie jest obsługiwana.  
  
- ![Wymagań wstępnych](../test/media/prereq.png "wstępnie wymagany składnik") Akcja uruchomienia przeglądarki sieci web muszą być częścią kodowanego testu interfejsu użytkownika.  
  
   Jeśli masz już otwartą przeglądarkę sieci Web i chcesz wykonać w niej te czynności, odtwarzanie zakończy się niepowodzeniem, chyba że używasz Internet Explorer. Dlatego najlepiej uwzględniać uruchamianie przeglądarki sieci Web jako część zakodowanych testów interfejsu użytkownika.  
  
- ![Wymagań wstępnych](../test/media/prereq.png "wstępnie wymagany składnik") Automating określonych w przeglądarce działania interfejsu użytkownika, takich jak maksymalizowanie, minimalizowanie i przywracanie nie jest obsługiwane.  
  
  **Porady**  
  
- ![Porada](../test/media/tip.png "Porada") można skonfigurować dane wyjściowe do uwzględnienia zrzutów ekranu w zakodowanych dziennikach interfejsu użytkownika. Aby to zrobić, należy zmienić kilka ustawień konfiguracji w pliku QTAgent32.exe.config. Domyślnie ten plik jest instalowany w następującej lokalizacji:  
  
   **C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE**  
  
   Ustaw następujące wartości:  
  
  - `EqtTraceLevel` w `system.diagnostics` sekcji.  
  
  - `<add name="EqtTraceLevel" value="4" />`  
  
     Ustawiając wartość 3 lub większą, zrzuty ekranu są pobierane dla każdego działania. Gdy wartość jest równa 1 lub 2, zrzuty ekranu są wykonywane tylko w przypadku błędów.  
  
    Aby uzyskać więcej informacji, zobacz [analizowanie kodowanych testów przy użyciu kodowanego interfejsu użytkownika dzienników testów interfejsu użytkownika](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
### <a name="videos"></a>Wideo  
 [Nagrywanie w przeglądarce IE i odtwarzanie wszędzie](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)  
  
 [Autorskie testy krzyżowe przeglądarki za pomocą konstruktora kodowanego testu interfejsu użytkownika](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)  
  
 [Autorskie testy krzyżowe przeglądarki za pomocą strony zwykłego kodowania bez mapy interfejsu użytkownika](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)  
  
 [Uruchamianie krzyżowych testów przeglądarki kolejno w różnych przeglądarkach](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)  
  
 [Rozwiązywanie problemów z wielu niepowodzeń testów przeglądarki](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)  
  
### <a name="guidance"></a>Wskazówki  
 [Testowanie dostarczania ciągłego w programie Visual Studio 2012 — rozdział 2: Testy jednostkowe: Testowanie wnętrza](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
 [Testowanie dostarczania ciągłego w programie Visual Studio 2012 — rozdział 5: Automatyzacja testów systemowych](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
### <a name="faq"></a>Najczęściej zadawane pytania  
 [Kodowane testy interfejsu użytkownika — często zadawane pytania — 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [Kodowanych testów interfejsu użytkownika — często zadawane pytania -2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### <a name="forum"></a>Forum  
 [Visual Studio automatyczne testowanie interfejsu użytkownika (w tym kodowanego interfejsu użytkownika)](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)   
 [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [Analizowanie kodowanych testów interfejsu użytkownika za pomocą dzienników zakodowanych testów interfejsu użytkownika](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)
