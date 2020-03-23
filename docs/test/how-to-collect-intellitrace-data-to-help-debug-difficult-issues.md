---
title: Dane IntelliTrace
ms.date: 10/13/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliTrace, configuring test settings
- Diagnostic Data Adapter, InteliTrace
- debugging [Visual Studio ALM], difficult issues using IntelliTrace
- Test Runner, InteliTrace
ms.assetid: 02b6716f-569e-4961-938a-e790a0c74b5c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 826d16fa316340226df042b0d762d923c43d39c9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594776"
---
# <a name="how-to-collect-intellitrace-data-to-help-debug-difficult-issues"></a>Jak: Zbieranie danych IntelliTrace, aby pomóc w debugowaniu trudnych problemów

Kartę danych diagnostycznych intellitrace można skonfigurować w celu zbierania określonych informacji śledzenia diagnostycznego w programie Visual Stdio. Adapter może być wykorzystywany przez testy do zbierania informacji o ważnych zdarzeniach diagnostycznych dotyczących aplikacji, na podstawie których deweloper później prześledzi kod i znajdzie przyczyny usterki. Adaptera danych diagnostycznych narzędzia IntelliTrace można używać w testach ręcznych i automatycznych.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Narzędzie IntelliTrace działa tylko wobec aplikacji napisanych przy użyciu kodu zarządzanego. Jeśli testujesz aplikację sieci web, która używa przeglądarki jako klienta, nie należy włączać IntelliTrace dla klienta w ustawieniach testu, ponieważ nie kod zarządzany jest dostępny do śledzenia. W takim przypadku można skonfigurować środowisko i zdalnie zbierać dane IntelliTrace na serwerze sieci web.

Dane IntelliTrace są przechowywane w pliku, który ma rozszerzenie *.iTrace*. Po uruchomieniu testu i krok testu kończy się niepowodzeniem, można utworzyć błąd. Plik narzędzia IntelliTrace zawierający informacje diagnostyczne jest automatycznie dołączany do tej usterki.

> [!NOTE]
> Adapter danych diagnostycznych narzędzia IntelliTrace nie tworzy pliku, jeśli test przyniesie wynik pomyślny. Plik jest zapisywany tylko po nieudanym teście albo po przesłaniu usterki.

Dane gromadzone w pliku narzędzia IntelliTrace usprawniają debugowanie, ponieważ umożliwiają szybsze odtwarzanie i diagnozowanie błędów w kodzie. Dodatkowo plik można udostępniać innym osobom w celu zreplikowania sesji na ich komputerach, co zmniejsza ryzyko, że usterki nie uda się odtworzyć.

> [!NOTE]
> W przypadku włączenia narzędzia IntelliTrace w ustawieniach testu funkcja zbierania danych o pokryciu kodu nie będzie działać.

> [!WARNING]
> Adapter danych diagnostycznych narzędzia IntelliTrace działa poprzez instrumentowanie zarządzanego procesu. Operację tę należy wykonać po załadowaniu testów dla przebiegu testowego. Jeśli proces, który ma być monitorowany, już się rozpoczął, nie będą zapisywane żadne pliki narzędzia IntelliTrace. Aby obejść ten problem, przed załadowaniem testów należy zatrzymać proces. Gdy tylko testy zostaną załadowane lub rozpocznie się pierwszy test, należy znów zainicjować proces.

Poniższa procedura opisuje konfigurowanie zbierania określonych danych przez narzędzie IntelliTrace. Te kroki dotyczą zarówno edytora konfiguracji w programie Microsoft Test Manager, jak i okna dialogowego Ustawienia testowe w programie Visual Studio.

> [!NOTE]
> Konto użytkownika agenta testów wykorzystywane do zbierania danych przez narzędzie IntelliTrace musi być członkiem grupy administratorów. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

## <a name="configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>Konfigurowanie danych do zbierania za pomocą karty danych diagnostycznych IntelliTrace

Przed wykonaniem kroków w tej procedurze należy otworzyć ustawienia testu z programu Microsoft Test Manager lub Visual Studio i wybrać stronę **Dane i diagnostyka.**

### <a name="to-configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>Aby skonfigurować dane do zbierania za pomocą karty danych diagnostycznych IntelliTrace

1. Wybierz rolę, na której narzędzie IntelliTrace będzie zbierać dane.

2. Wybierz **IntelliTrace**.

3. Jeśli dodajesz IntelliTrace dla roli klienta sieci Web lub dla ASP.NET aplikacji sieci web, należy również wybrać **ASP.NET serwera proxy klienta dla intellitrace i wpływu testu**.

     Ten serwer proxy umożliwia zbieranie informacji o wywołaniach http z klienta do serwera sieci web dla kart danych diagnostycznych IntelliTrace i Test Impact.

    > [!WARNING]
    > Jeśli zdecydujesz się użyć konta niestandardowego dla tożsamości używanej dla puli aplikacji na internetowym serwerze informacyjnym (IIS), w którym zamierzasz zbierać dane IntelliTrace, musisz utworzyć lokalny profil użytkownika na komputerze Usług IIS dla konta niestandardowego, które jest używany. W celu utworzenia profilu można się zalogować jeden raz lokalnie na komputerze z programem IIS albo wykonać następujące polecenie w wierszu polecenia, podając poświadczenia niestandardowego konta:
    >
    > **runas /user:domain\name /profile cmd.exe**

4. Wybierz **pozycję Konfiguruj** dla **intellitrace,** aby zmodyfikować domyślne ustawienia IntelliTrace.

     Zostanie wyświetlone okno dialogowe z opcjami określenia danych, które mają być zbierane.

    > [!WARNING]
    > Po włączeniu funkcji gromadzenia danych przez narzędzie IntelliTrace funkcja zbierania danych o pokryciu kodu nie będzie działać.

5. Wybierz kartę **Ogólne.** Wybierz **intellitrace zdarzenia tylko** do rejestrowania znaczących zdarzeń diagnostycznych, które mają minimalny wpływ na wydajność podczas testowania.

     — lub —

     Wybierz **IntelliTrace zdarzenia i informacje o wywołaniu,** aby rejestrować zdarzenia diagnostyczne i śledzenie poziomu metody, który pokazuje informacje o wywołaniu. Ten poziom śledzenia może podczas wykonywania testów odczuwalnie obciążać system.

6. Aby zbierać dane z aplikacji ASP.NET uruchomionej w internetowych usługach informacyjnych, wybierz opcję **Zbieraj dane z ASP.NET aplikacji uruchomionych w internetowych usługach informacyjnych**. Skonfiguruj i skonfiguruj agenta testowego w roli serwera sieci web. Zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

7. Wybierz kartę **Moduły.** Wybierz opcję **Zbieraj dane ze wszystkich modułów z wyjątkiem następujących opcji** i użyj opcji **Dodaj,** aby dodać je do listy modułów, i **usuń,** aby usunąć moduł. Ta opcja pozwala objąć wszystkie moduły działające w systemie poza konkretnie wskazanymi.

     — lub —

     Wybierz **opcję Zbierz dane tylko z następujących modułów** i użyj **dodaj,** aby dodać do listy modułów i **Usuń,** aby usunąć moduł. Ta opcja pozwala wskazać konkretne moduły, z których mają być gromadzone dane.

    > [!NOTE]
    > O ile to tylko możliwe, należy zaznaczać konkretne procesy, które mają być monitorowane. Zapewni to optymalne działanie systemu.

8. Wybierz kartę **Procesy.** Wybierz pozycję **Zbierz dane ze wszystkich procesów, z wyjątkiem następujących czynności,** a następnie użyj opcji **Dodaj,** aby dodać je do listy procesów, a następnie **usuń,** aby usunąć proces. Ta opcja pozwala objąć gromadzeniem danych wszystkie procesy działające w systemie poza konkretnie wskazanymi.

     — lub —

     Wybierz **opcję Zbieraj dane tylko z określonych procesów** i użyj **dodaj,** aby dodać do listy procesów i **Usuń,** aby usunąć proces. Ta opcja pozwala wskazać konkretne procesy, z których mają być gromadzone dane.

9. (Opcjonalnie) Wybierz kartę **Zdarzenia IntelliTrace.** Wybierz lub wyczyść każdą kategorię zdarzeń IntelliTrace, którą chcesz uwzględnić lub wykluczyć podczas zbierania zdarzeń diagnostycznych.

10. (Opcjonalnie) Rozwiń każdą kategorię zdarzeń narzędzia IntelliTrace i zaznacz lub wyczyść konkretne zdarzenia, o których narzędzie ma zbierać informacje.

11. (Opcjonalnie) Wybierz kartę **Zaawansowane.** Następnie wybierz strzałkę obok **pozycji Maksymalna ilość miejsca na dysku do nagrywania** i wybierz maksymalny rozmiar, który chcesz włączyć dla pliku IntelliTrace do użycia.

    > [!NOTE]
    > Zbyt wysoki limit ilości rejestrowanych danych może sprawić, że podczas zapisywania danych razem z wynikami testu upłynie limit czasu.

12. Jeśli korzystasz z Menedżera testów firmy Microsoft, wybierz pozycję **Zapisz**. Jeśli używasz programu Visual Studio, wybierz przycisk **OK**. Ustawienia narzędzia IntelliTrace są teraz skonfigurowane i zapisane w ustawieniach testu.

    > [!NOTE]
    > Aby zresetować konfigurację tej karty danych diagnostycznych, wybierz pozycję **Resetuj do domyślnej konfiguracji** programu Visual Studio lub **Resetuj domyślnie** dla menedżera testów firmy Microsoft.

## <a name="see-also"></a>Zobacz też

- [Zbieranie danych diagnostycznych podczas testowania (plany testów platformy Azure)](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [Zbieranie danych diagnostycznych w testach ręcznych (plany testów platformy Azure)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [Zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md)
- [Zbieranie danych funkcji IntelliTrace](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)
