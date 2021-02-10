---
title: IntelliTrace dane
description: Dowiedz się, jak skonfigurować adapter danych diagnostycznych dla usługi IntelliTrace, aby zbierać informacje o śledzeniu diagnostycznym w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/13/2016
ms.topic: how-to
helpviewer_keywords:
- IntelliTrace, configuring test settings
- Diagnostic Data Adapter, InteliTrace
- debugging [Visual Studio ALM], difficult issues using IntelliTrace
- Test Runner, InteliTrace
ms.assetid: 02b6716f-569e-4961-938a-e790a0c74b5c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 6ecc16725913e159bb2dfeb45277c4555efa50a5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966789"
---
# <a name="how-to-collect-intellitrace-data-to-help-debug-difficult-issues"></a>Instrukcje: zbieranie danych IntelliTrace w celu ułatwienia debugowania trudnych problemów

Adapter danych diagnostycznych dla usługi IntelliTrace można skonfigurować w celu zbierania określonych informacji śledzenia diagnostycznego w programie Visual Studio. Adapter może być wykorzystywany przez testy do zbierania informacji o ważnych zdarzeniach diagnostycznych dotyczących aplikacji, na podstawie których deweloper później prześledzi kod i znajdzie przyczyny usterki. Adaptera danych diagnostycznych narzędzia IntelliTrace można używać w testach ręcznych i automatycznych.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Narzędzie IntelliTrace działa tylko wobec aplikacji napisanych przy użyciu kodu zarządzanego. Jeśli testujesz aplikację sieci Web, która używa przeglądarki jako klienta, nie należy włączać IntelliTrace dla klienta w ustawieniach testu, ponieważ nie jest dostępny żaden kod zarządzany do śledzenia. W takim przypadku możesz chcieć skonfigurować środowisko i zbierać dane IntelliTrace zdalnie na serwerze sieci Web.

Dane IntelliTrace są przechowywane w pliku, który ma rozszerzenie *. iTrace*. Gdy uruchamiasz test, a krok testu zakończy się niepowodzeniem, możesz utworzyć błąd. Plik narzędzia IntelliTrace zawierający informacje diagnostyczne jest automatycznie dołączany do tej usterki.

> [!NOTE]
> Adapter danych diagnostycznych narzędzia IntelliTrace nie tworzy pliku, jeśli test przyniesie wynik pomyślny. Plik jest zapisywany tylko po nieudanym teście albo po przesłaniu usterki.

Dane gromadzone w pliku narzędzia IntelliTrace usprawniają debugowanie, ponieważ umożliwiają szybsze odtwarzanie i diagnozowanie błędów w kodzie. Dodatkowo plik można udostępniać innym osobom w celu zreplikowania sesji na ich komputerach, co zmniejsza ryzyko, że usterki nie uda się odtworzyć.

> [!NOTE]
> W przypadku włączenia narzędzia IntelliTrace w ustawieniach testu funkcja zbierania danych o pokryciu kodu nie będzie działać.

> [!WARNING]
> Adapter danych diagnostycznych narzędzia IntelliTrace działa poprzez instrumentowanie zarządzanego procesu. Operację tę należy wykonać po załadowaniu testów dla przebiegu testowego. Jeśli proces, który ma być monitorowany, już się rozpoczął, nie będą zapisywane żadne pliki narzędzia IntelliTrace. Aby obejść ten problem, przed załadowaniem testów należy zatrzymać proces. Gdy tylko testy zostaną załadowane lub rozpocznie się pierwszy test, należy znów zainicjować proces.

::: moniker range="vs-2017"
Poniższa procedura opisuje konfigurowanie zbierania określonych danych przez narzędzie IntelliTrace. Te kroki dotyczą zarówno edytora konfiguracji w oknie dialogowym Microsoft Test Manager, jak i ustawienia testu w programie Visual Studio.
::: moniker-end
::: moniker range=">=vs-2019"
Poniższa procedura opisuje konfigurowanie zbierania określonych danych przez narzędzie IntelliTrace. Te kroki mają zastosowanie do okna dialogowego Ustawienia testu w programie Visual Studio.
::: moniker-end

> [!NOTE]
> Konto użytkownika agenta testów wykorzystywane do zbierania danych przez narzędzie IntelliTrace musi być członkiem grupy administratorów. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

## <a name="configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>Konfigurowanie danych do zbierania przy użyciu adaptera danych diagnostycznych IntelliTrace

::: moniker range="vs-2017"
Przed wykonaniem kroków opisanych w tej procedurze należy otworzyć ustawienia testu z poziomu Microsoft Test Manager lub programu Visual Studio i wybrać stronę **dane i Diagnostyka** .
::: moniker-end
::: moniker range=">=vs-2019"
Przed wykonaniem kroków opisanych w tej procedurze należy otworzyć ustawienia testu w programie Visual Studio i wybrać stronę **dane i Diagnostyka** .
::: moniker-end

### <a name="to-configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>Aby skonfigurować dane do zbierania przy użyciu adaptera danych diagnostycznych IntelliTrace

1. Wybierz rolę, na której narzędzie IntelliTrace będzie zbierać dane.

2. Wybierz pozycję **IntelliTrace**.

3. W przypadku dodawania IntelliTrace dla roli klienta sieci Web lub aplikacji sieci Web ASP.NET należy również wybrać opcję **ASP.NET Client proxy dla IntelliTrace i wpływu na testowanie**.

     Ten serwer proxy umożliwia zbieranie informacji o wywołaniach http z klienta do serwera sieci Web dla IntelliTrace i adapterów danych diagnostycznych dotyczących efektów testowych.

    > [!WARNING]
    > Jeśli zdecydujesz się użyć konta niestandardowego dla tożsamości, która jest używana dla puli aplikacji na serwerze Internet Information Server (IIS), gdzie chcesz zbierać dane IntelliTrace, musisz utworzyć profil użytkownika lokalnego na komputerze IIS dla niestandardowego konta, które jest używane. W celu utworzenia profilu można się zalogować jeden raz lokalnie na komputerze z programem IIS albo wykonać następujące polecenie w wierszu polecenia, podając poświadczenia niestandardowego konta:
    >
    > **runas/user: DOMENA\nazwa/profile cmd.exe**

4. Wybierz pozycję **Konfiguruj** dla **IntelliTrace** , aby zmodyfikować domyślne ustawienia IntelliTrace.

     Zostanie wyświetlone okno dialogowe z opcjami określenia danych, które mają być zbierane.

    > [!WARNING]
    > Po włączeniu funkcji gromadzenia danych przez narzędzie IntelliTrace funkcja zbierania danych o pokryciu kodu nie będzie działać.

5. Wybierz kartę **Ogólne** . Wybierz pozycję **zdarzenia IntelliTrace tylko** do rejestrowania znaczących zdarzeń diagnostycznych, które mają minimalny wpływ na wydajność podczas testowania.

     -lub-

     Wybierz **zdarzenia IntelliTrace i Wywołaj informacje** , aby zarejestrować zdarzenia diagnostyczne i śledzenie na poziomie metody, które wyświetla informacje o wywołaniu. Ten poziom śledzenia może podczas wykonywania testów odczuwalnie obciążać system.

6. Aby zbierać dane z aplikacji ASP.NET działającej na Internet Information Services, wybierz pozycję **Zbierz dane z aplikacji ASP.NET, które działają w Internet Information Services**. Skonfiguruj i Skonfiguruj agenta testowego w roli serwera sieci Web. Zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

7. Wybierz kartę **moduły** . Wybierz opcję **Zbierz dane ze wszystkich modułów, z wyjątkiem następujących** , a następnie użyj opcji **Dodaj** , aby dodać do listy modułów i **usunąć** go w celu usunięcia modułu. Ta opcja pozwala objąć wszystkie moduły działające w systemie poza konkretnie wskazanymi.

     -lub-

     Wybierz pozycję **Zbierz dane tylko z następujących modułów** i użyj opcji **Dodaj** , aby dodać do listy modułów i **usunąć** go w celu usunięcia modułu. Ta opcja pozwala wskazać konkretne moduły, z których mają być gromadzone dane.

    > [!NOTE]
    > O ile to tylko możliwe, należy zaznaczać konkretne procesy, które mają być monitorowane. Zapewni to optymalne działanie systemu.

8. Wybierz kartę **procesy** . Wybierz pozycję **Zbierz dane ze wszystkich procesów z wyjątkiem następujących** i użyj opcji **Dodaj** , aby dodać do listy procesów i **usunąć** je w celu usunięcia procesu. Ta opcja pozwala objąć gromadzeniem danych wszystkie procesy działające w systemie poza konkretnie wskazanymi.

     -lub-

     Wybierz opcję **Zbierz dane tylko z określonych procesów** , a następnie użyj opcji **Dodaj** , aby dodać do listy procesów i **usunąć** , aby usunąć proces. Ta opcja pozwala wskazać konkretne procesy, z których mają być gromadzone dane.

9. Obowiązkowe Wybierz kartę **zdarzenia IntelliTrace** . Zaznacz lub usuń zaznaczenie każdej kategorii zdarzeń IntelliTrace, która ma zostać dołączona lub wykluczona podczas zbierania zdarzeń diagnostycznych.

10. (Opcjonalnie) Rozwiń każdą kategorię zdarzeń narzędzia IntelliTrace i zaznacz lub wyczyść konkretne zdarzenia, o których narzędzie ma zbierać informacje.

11. Obowiązkowe Wybierz kartę **Zaawansowane** . Następnie wybierz strzałkę obok pozycji **Maksymalna ilość miejsca na dysku do nagrania** i wybierz maksymalny rozmiar, który ma zostać włączony dla pliku IntelliTrace.

    > [!NOTE]
    > Zbyt wysoki limit ilości rejestrowanych danych może sprawić, że podczas zapisywania danych razem z wynikami testu upłynie limit czasu.

12. Jeśli używasz Microsoft Test Manager (przestarzałe w programie Visual Studio 2017), wybierz pozycję **Zapisz**. Jeśli używasz programu Visual Studio, wybierz **przycisk OK**. Ustawienia narzędzia IntelliTrace są teraz skonfigurowane i zapisane w ustawieniach testu.

    ::: moniker range="vs-2017"
    > [!NOTE]
    > Aby zresetować konfigurację dla tego adaptera danych diagnostycznych, wybierz opcję **Zresetuj do konfiguracji domyślnej** dla programu Visual Studio lub **Przywróć wartość domyślną** dla Microsoft Test Manager.
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    > [!NOTE]
    > Aby zresetować konfigurację tego adaptera danych diagnostycznych, wybierz pozycję **Zresetuj do konfiguracji domyślnej** w programie Visual Studio.
    ::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Zbieraj dane diagnostyczne podczas testowania (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true)
- [Zbieranie danych diagnostycznych w testach ręcznych (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)
- [Zbieranie informacji diagnostycznych za pomocą ustawień testu](../test/collect-diagnostic-information-using-test-settings.md)
- [Zbieranie danych funkcji IntelliTrace](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)
