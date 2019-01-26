---
title: Dane funkcji IntelliTrace
ms.date: 10/13/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliTrace, configuring test settings
- Diagnostic Data Adapter, InteliTrace
- debugging [Visual Studio ALM], difficult issues using IntelliTrace
- Test Runner, InteliTrace
ms.assetid: 02b6716f-569e-4961-938a-e790a0c74b5c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.openlocfilehash: 33dd1d131d85a066078d9e145ccbbc1fed6e98b9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932353"
---
# <a name="how-to-collect-intellitrace-data-to-help-debug-difficult-issues"></a>Instrukcje: Zbieranie danych IntelliTrace aby pomóc w debugowaniu trudnych problemów

Można skonfigurować adapter danych diagnostycznych narzędzia IntelliTrace do zbierania informacji diagnostycznych śledzenia w Visual stdio —. Adapter może być wykorzystywany przez testy do zbierania informacji o ważnych zdarzeniach diagnostycznych dotyczących aplikacji, na podstawie których deweloper później prześledzi kod i znajdzie przyczyny usterki. Adaptera danych diagnostycznych narzędzia IntelliTrace można używać w testach ręcznych i automatycznych.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Narzędzie IntelliTrace działa tylko wobec aplikacji napisanych przy użyciu kodu zarządzanego. Jeśli testujesz aplikację internetową, która używa przeglądarki jako klienta nie należy włączać funkcji IntelliTrace dla klienta w ustawieniach testu, ponieważ żaden kod zarządzany jest dostępna do śledzenia. W takim przypadku można skonfigurować środowisko i zbierać dane IntelliTrace zdalnie na serwerze sieci web.

Dane funkcji IntelliTrace są przechowywane w pliku, który ma rozszerzenie *.iTrace*. Kiedy uruchamiasz test i krok testu zakończy się niepowodzeniem, można utworzyć usterkę. Plik narzędzia IntelliTrace zawierający informacje diagnostyczne jest automatycznie dołączany do tej usterki.

> [!NOTE]
> Adapter danych diagnostycznych narzędzia IntelliTrace nie tworzy pliku, jeśli test przyniesie wynik pomyślny. Plik jest zapisywany tylko po nieudanym teście albo po przesłaniu usterki.

Dane gromadzone w pliku narzędzia IntelliTrace usprawniają debugowanie, ponieważ umożliwiają szybsze odtwarzanie i diagnozowanie błędów w kodzie. Dodatkowo plik można udostępniać innym osobom w celu zreplikowania sesji na ich komputerach, co zmniejsza ryzyko, że usterki nie uda się odtworzyć.

> [!NOTE]
> W przypadku włączenia narzędzia IntelliTrace w ustawieniach testu funkcja zbierania danych o pokryciu kodu nie będzie działać.

> [!WARNING]
> Adapter danych diagnostycznych narzędzia IntelliTrace działa poprzez instrumentowanie zarządzanego procesu. Operację tę należy wykonać po załadowaniu testów dla przebiegu testowego. Jeśli proces, który ma być monitorowany, już się rozpoczął, nie będą zapisywane żadne pliki narzędzia IntelliTrace. Aby obejść ten problem, przed załadowaniem testów należy zatrzymać proces. Gdy tylko testy zostaną załadowane lub rozpocznie się pierwszy test, należy znów zainicjować proces.

Poniższa procedura opisuje konfigurowanie zbierania określonych danych przez narzędzie IntelliTrace. Te kroki dotyczą zarówno edytora konfiguracji w okno dialogowe programu Microsoft Test Manager i ustawienia testu w programie Visual Studio.

> [!NOTE]
> Konto użytkownika agenta testów wykorzystywane do zbierania danych przez narzędzie IntelliTrace musi być członkiem grupy administratorów. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

## <a name="configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>Konfiguruj dane zbierane przez adapter danych diagnostycznych IntelliTrace

Przed wykonaniem kroków w tej procedurze należy otworzyć Ustawienia testu z programu Microsoft Test Manager lub programu Visual Studio i wybrać **dane i Diagnostyka** strony.

### <a name="to-configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>Aby skonfigurować dane zbierane przez adapter danych diagnostycznych IntelliTrace

1.  Wybierz rolę, na której narzędzie IntelliTrace będzie zbierać dane.

2.  Wybierz **IntelliTrace**.

3.  W przypadku dodawania funkcji IntelliTrace dla roli klienta sieci web lub aplikacji sieci web programu ASP.NET, należy również zaznaczyć **Proxy klienta ASP.NET dla IntelliTrace i wpływu Test**.

     Ten serwer proxy umożliwia zbieranie informacji na temat połączeń http od klienta do serwera sieci web dla adapterów danych diagnostycznych IntelliTrace i badanie wpływu.

    > [!WARNING]
    > Jeśli zdecydujesz się używać niestandardowego konta dla tożsamości, który jest używany dla puli aplikacji na Internet Information Server (IIS) mającym służyć do zbierania danych funkcji IntelliTrace, należy utworzyć lokalny profil użytkownika na komputerze z programem IIS dla konta niestandardowego jest on używany. W celu utworzenia profilu można się zalogować jeden raz lokalnie na komputerze z programem IIS albo wykonać następujące polecenie w wierszu polecenia, podając poświadczenia niestandardowego konta:
    >
    > **cmd.exe/profile /user:domain\name runas**

4.  Wybierz **Konfiguruj** dla **IntelliTrace** Aby zmodyfikować domyślne ustawienia narzędzia IntelliTrace.

     Zostanie wyświetlone okno dialogowe z opcjami określenia danych, które mają być zbierane.

    > [!WARNING]
    > Po włączeniu funkcji gromadzenia danych przez narzędzie IntelliTrace funkcja zbierania danych o pokryciu kodu nie będzie działać.

5.  Wybierz **ogólne** kartę. Wybierz **tylko zdarzenia funkcji IntelliTrace** Aby rejestrować ważne zdarzenia diagnostyczne, które mają minimalny wpływ na wydajność podczas testowania.

     —lub—

     Wybierz **zdarzenia IntelliTrace i wywołania informacji** Aby rejestrować zdarzenia diagnostyczne i metody śledzenia na poziomie pokazujące informacje o wywołaniach. Ten poziom śledzenia może podczas wykonywania testów odczuwalnie obciążać system.

6.  Aby zebrać dane z poziomu aplikacji ASP.NET, który jest uruchomiony w programie Internet Information Services, wybierz **zbieranie danych z aplikacji ASP.NET, które są uruchomione w Internetowych usługach informacyjnych**. Instalowanie i Konfigurowanie agenta testowego w roli serwera sieci web. Zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

7.  Wybierz **modułów** kartę. Wybierz opcję **zbierać dane ze wszystkich modułów oprócz następujących** i użyj **Dodaj** do dodania do listy modułów i **Usuń** można usunąć modułu. Ta opcja pozwala objąć wszystkie moduły działające w systemie poza konkretnie wskazanymi.

     —lub—

     Wybierz **zbierać dane z następujących modułów** i użyj **Dodaj** do dodania do listy modułów i **Usuń** można usunąć modułu. Ta opcja pozwala wskazać konkretne moduły, z których mają być gromadzone dane.

    > [!NOTE]
    > O ile to tylko możliwe, należy zaznaczać konkretne procesy, które mają być monitorowane. Zapewni to optymalne działanie systemu.

8.  Wybierz **procesy** kartę. Wybierz **zbieranie danych od wszystkich procesów oprócz następujących** i użyj **Dodaj** do dodania do listy procesów i **Usuń** Usuń. Ta opcja pozwala objąć gromadzeniem danych wszystkie procesy działające w systemie poza konkretnie wskazanymi.

     —lub—

     Wybierz **zbierać dane tylko z określonych procesów** i użyj **Dodaj** do dodania do listy procesów i **Usuń** Usuń. Ta opcja pozwala wskazać konkretne procesy, z których mają być gromadzone dane.

9. (Opcjonalnie) Wybierz **zdarzenia IntelliTrace** kartę. Zaznacz lub wyczyść każdą kategorię zdarzeń narzędzia IntelliTrace, która ma być uwzględniona lub pominięta przy zbieraniu informacji o ważnych zdarzeniach diagnostycznych.

10. (Opcjonalnie) Rozwiń każdą kategorię zdarzeń narzędzia IntelliTrace i zaznacz lub wyczyść konkretne zdarzenia, o których narzędzie ma zbierać informacje.

11. (Opcjonalnie) Wybierz **zaawansowane** kartę. Następnie wybierz strzałkę obok **maksymalna ilość miejsca na dysku dla nagrywania** i zaznacz maksymalny rozmiar, który chcesz włączyć plik narzędzia IntelliTrace do użycia.

    > [!NOTE]
    > Zbyt wysoki limit ilości rejestrowanych danych może sprawić, że podczas zapisywania danych razem z wynikami testu upłynie limit czasu.

12. Jeśli używasz Microsoft Test Manager, wybierz opcję **Zapisz**. Jeśli używasz programu Visual Studio, wybierz opcję **OK**. Ustawienia narzędzia IntelliTrace są teraz skonfigurowane i zapisane w ustawieniach testu.

    > [!NOTE]
    > Aby zresetować konfigurację tego adaptera danych diagnostycznych, wybierz opcję **Przywróć domyślną konfigurację** dla programu Visual Studio lub **Przywróć domyślne** dla programu Microsoft Test Manager.

## <a name="see-also"></a>Zobacz także

- [Zbieranie danych diagnostycznych podczas testowania (planów testowych platformy Azure)](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [Zbieranie danych diagnostycznych podczas wykonywania testów ręcznych (planów testowych platformy Azure)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [Zbieranie informacji diagnostycznych za pomocą ustawień testów](../test/collect-diagnostic-information-using-test-settings.md)
- [Zbieranie danych funkcji IntelliTrace](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)