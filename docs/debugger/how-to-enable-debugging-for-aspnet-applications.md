---
title: Włączanie debugowania ASP.NET aplikacji | Microsoft Docs
description: Dowiedz się, jak włączyć debugowanie ASP.NET i ASP.NET Core w Visual Studio. Proces można uruchomić na serwerze IIS Express lokalnym serwerze usług IIS.
ms.custom: SEO-VS-2020
ms.date: 10/29/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 1fd620a0c7f4860421b6f8b1a15c0b708c1ba860
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729263"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Debugowanie aplikacji platformy ASP.NET lub ASP.NET Core w programie Visual Studio

Możesz debugować aplikacje ASP.NET i ASP.NET Core w Visual Studio. Proces różni się między ASP.NET i ASP.NET Core oraz od tego, czy jest uruchamiany na IIS Express lokalnym serwerze usług IIS.

>[!NOTE]
>Poniższe kroki i ustawienia dotyczą tylko debugowania aplikacji na serwerze lokalnym. Debugowanie aplikacji na zdalnym serwerze usług IIS używa **dołączania do procesu** i ignoruje te ustawienia. Aby uzyskać więcej informacji i instrukcji dotyczących zdalnego debugowania aplikacji ASP.NET w usługach IIS, zobacz Zdalne debugowanie ASP.NET na komputerze [usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) lub Zdalne debugowanie programu ASP.NET Core na zdalnym komputerze [usług IIS.](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)

Wbudowany serwer IIS Express jest dołączony do Visual Studio. IIS Express jest domyślnym serwerem debugowania dla ASP.NET i ASP.NET Core i jest wstępnie skonfigurowany. Jest to najprostszy sposób debugowania i idealny do początkowego debugowania i testowania.

Możesz również debugować aplikację ASP.NET lub ASP.NET Core na lokalnym serwerze usług IIS (w wersji 8.0 lub wyższej) skonfigurowanym do uruchamiania aplikacji. Aby debugować w lokalnych usługach IIS, należy spełnić następujące wymagania:

<a name="iis"></a>
- Jeśli nie jest on zainstalowany, zainstaluj pakiet ASP.NET **tworzenia aplikacji internetowych.** (Ponownie Instalator programu Visual Studio wybierz **pozycję Modyfikuj** i dodaj to obciążenie).

   ::: moniker range="vs-2017"
   W Visual Studio 2017 roku poszukaj składnika obsługi usług **IIS w czasie projektowania.** Upewnij się, że wybrano ją podczas dodawania obciążenia.
   ::: moniker-end
- Uruchom program Visual Studio jako administrator.
- Zainstaluj i poprawnie skonfiguruj usługi IIS przy użyciu odpowiednich wersji ASP.NET i/lub ASP.NET Core. Aby uzyskać więcej informacji na temat używania usług IIS z programem ASP.NET Core, zobacz Host ASP.NET Core on Windows with IIS (Hostowanie ASP.NET [Core w systemie Windows za pomocą usług IIS).](/aspnet/core/host-and-deploy/iis/index) Aby ASP.NET więcej informacji, [zobacz Instalowanie usług IIS i ASP.NET modułów](/iis/application-frameworks/scenario-build-an-aspnet-website-on-iis/configuring-step-1-install-iis-and-asp-net-modules).
- Upewnij się, że aplikacja działa w usługach IIS bez błędów.

## <a name="debug-aspnet-apps"></a>Debugowanie ASP.NET aplikacji

IIS Express jest wartością domyślną i jest wstępnie skonfigurowana. Jeśli debugujesz w lokalnych usługach IIS, upewnij się, że spełniasz wymagania dotyczące [lokalnego debugowania usług IIS.](#iis)

1. Wybierz projekt ASP.NET w programie Visual Studio **Eksplorator rozwiązań** kliknij ikonę Właściwości lub naciśnij klawisz **Alt** Enter lub kliknij prawym przyciskiem myszy i wybierz polecenie  +  **Właściwości.**

1. Wybierz **kartę** Sieć Web.

1. W **okienku Właściwości** w obszarze **Serwery**
   - W IIS Express wybierz pozycję **IIS Express** z listy rozwijanej.
   - W przypadku lokalnych usług IIS:
     1. Wybierz **pozycję Lokalne program IIS** z listy rozwijanej.
     1. Obok pola **Project URL (Adres URL** projektu) wybierz pozycję Create Virtual Directory (Utwórz katalog **wirtualny),** jeśli aplikacja nie została jeszcze ustawiona w usługach IIS.

1. W **obszarze Debuggers (Debuger)** **wybierz pozycję ASP.NET**.

   ![ASP.NET ustawień debugera](media/dbg-aspnet-enable-debugging2.png "ASP.NET ustawień debugera")

1. Wybierz **pozycję Plik** Zapisz wybrane  >  **elementy** (lub naciśnij klawisze **Ctrl** + **S),** aby zapisać wszelkie zmiany.

1. Aby debugować aplikację, w projekcie ustaw punkty przerwania dla kodu. Na pasku Visual Studio upewnij się, że konfiguracja jest ustawiona na debugowanie **,** a przeglądarka jest wyświetlana w IIS Express **( \<Browser name> )** lub Lokalne usługi **IIS ( \<Browser name> )** w polu emulatora.

1. Aby rozpocząć debugowanie, **wybierz pozycję IIS Express ( \<Browser name> )** lub Lokalne **program IIS ( \<Browser name> )** na pasku narzędzi, wybierz pozycję **Rozpocznij** debugowanie z menu **Debugowanie** lub naciśnij **klawisz F5.** Debuger jest wstrzymywany w punktach przerwania. Jeśli debuger nie może trafić punktów przerwania, zobacz [Rozwiązywanie problemów z debugowaniem](#troubleshoot-debugging).

## <a name="debug-aspnet-core-apps"></a>Debugowanie ASP.NET Core

IIS Express jest wartością domyślną i jest wstępnie skonfigurowana. Jeśli debugujesz w lokalnych usługach IIS, upewnij się, że spełniasz wymagania [dotyczące lokalnego debugowania usług IIS.](#iis)

1. Wybierz projekt ASP.NET Core w programie Visual Studio **Eksplorator rozwiązań** kliknij ikonę Właściwości lub naciśnij klawisz **Alt** Enter lub kliknij prawym przyciskiem myszy i wybierz polecenie  +  **Właściwości.**

1. Wybierz **kartę Debugowanie.**

1. W **okienku** Właściwości obok przycisku Profil wybierz **pozycję**
   - W IIS Express wybierz pozycję **IIS Express** z listy rozwijanej.
   - W przypadku lokalnych usług IIS wybierz nazwę aplikacji z listy rozwijanej lub wybierz pozycję **Nowy,** utwórz nową nazwę profilu i wybierz przycisk **OK.**

1. Obok opcji **Uruchom** wybierz pozycję **IIS Express** **lub IIS** z listy rozwijanej.

1. Upewnij się, **że wybrano opcję Uruchom** przeglądarkę.

1. W **obszarze Zmienne środowiskowe** upewnij się, że **ASPNETCORE_ENVIRONMENT** jest obecna z wartością **Development**. Jeśli nie, wybierz **pozycję Dodaj** i dodaj ją.

   ![ASP.NET ustawień debugera Core](../debugger/media/dbg-aspnet-enable-debugging3.png "ASP.NET ustawień debugera core")

1. Użyj **opcji Zapisz** wybrane elementy w  >  **pliku** lub naciśnij klawisze **Ctrl** + **S,** aby zapisać zmiany.

1. Aby debugować aplikację, w projekcie ustaw punkty przerwania dla kodu. Na pasku Visual Studio upewnij się, że konfiguracja jest ustawiona na wartość **Debuguj,** a w polu emulatora zostanie wyświetlona wartość **IIS Express** lub nowa nazwa profilu usług IIS.

1. Aby rozpocząć debugowanie, **wybierz IIS Express** lub na pasku narzędzi wybierz pozycję Rozpocznij debugowanie z **\<IIS profile name>** menu **Debugowanie** lub naciśnij **klawisz F5.**  Debuger jest wstrzymywany w punktach przerwania. Jeśli debuger nie może trafić punktów przerwania, zobacz [Rozwiązywanie problemów z debugowaniem](#troubleshoot-debugging).

## <a name="troubleshoot-debugging"></a>Rozwiązywanie problemów z debugowaniem

Jeśli lokalne debugowanie usług IIS nie może przejść do punktu przerwania, wykonaj następujące kroki, aby rozwiązać problem.

1. Uruchom aplikację internetową z usług IIS i upewnij się, że działa prawidłowo. Pozostaw aplikację internetową uruchomiona.

2. Z Visual Studio wybierz pozycję  Debuguj > Dołącz do procesu lub naciśnij klawisze **Ctrl** Alt P i połącz się z procesem ASP.NET lub ASP.NET Core (zazwyczajw3wp.exelub +  +  **dotnet.exe).**  Aby uzyskać więcej informacji, zobacz [Attach to Process](attach-to-running-processes-with-the-visual-studio-debugger.md) (Dołączanie do procesu) i How to find the name of the ASP.NET process (Jak znaleźć nazwę ASP.NET [procesu).](how-to-find-the-name-of-the-aspnet-process.md)

Jeśli możesz nawiązać połączenie i trafić punkt przerwania za pomocą polecenia Attach **to Process**(Dołącz do procesu), ale nie przy użyciu polecenia   >  **Debuguj rozpocznij** debugowanie ani **klawisza F5**, ustawienie jest prawdopodobnie nieprawidłowe we właściwościach projektu. Jeśli używasz pliku HOSTS, upewnij się, że jest on również poprawnie skonfigurowany.

## <a name="configure-debugging-in-the-webconfig-file"></a>Konfigurowanie debugowania w web.config pliku

ASP.NET mają domyślnie *web.config,* które zawierają informacje o konfiguracji aplikacji i uruchomieniu, w tym ustawienia debugowania. Pliki *web.config* muszą być poprawnie skonfigurowane do debugowania. Ustawienia **właściwości** w poprzednich sekcjach *aktualizują plikiweb.config,* ale można je również skonfigurować ręcznie.

> [!NOTE]
> ASP.NET Core nie mają początkowo plików web.config, ale używają  funkcjiappsettings.jsi *launchSettings.js* na plikach w celu konfigurowania i uruchamiania aplikacji. Wdrożenie aplikacji powoduje *utworzenie* web.configlub plików w projekcie, ale zwykle nie zawierają one informacji debugowania.

> [!TIP]
> Proces wdrażania może zaktualizować *ustawieniaweb.config,* dlatego przed próbą debugowania upewnij się, *web.config* skonfigurowano debugowanie.

**Aby ręcznie skonfigurować plik *web.config* debugowania:**

1. W Visual Studio otwórz ASP.NET plikuweb.config *projektu.*

2. *Web.config* jest plikiem XML, dlatego zawiera zagnieżdżone sekcje oznaczone tagami. Znajdź sekcję `configuration/system.web/compilation`. (Jeśli `compilation` element nie istnieje, utwórz go).

3. Upewnij się, `debug` że atrybut w `compilation` elemencie jest ustawiony na wartość `true` . (Jeśli `compilation` element nie zawiera atrybutu, dodaj `debug` go i ustaw go na `true` .)

   Jeśli używasz lokalnych usług IIS zamiast domyślnego serwera IIS Express, upewnij się, że wartość atrybutu w elemencie jest taka sam jak w przypadku struktury `targetFramework` `compilation` na serwerze usług IIS.

   Element `compilation` pliku *web.config* powinien wyglądać podobnie do poniższego przykładu:

   > [!NOTE]
   > Ten przykład to *częściowyweb.config* plików. W elementach i znajdują się zazwyczaj dodatkowe sekcje XML, a `configuration` element może również zawierać inne atrybuty i `system.web` `compilation` elementy.

   ```xml
   <configuration>
      ...
      <system.web>
          <compilation  debug="true"  targetFramework="4.6.1" ... >
             ...
          </compilation>
      </system.web>
   </configuration>
   ```

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] program automatycznie wykrywa wszelkie zmiany *web.config* plików i stosuje nowe ustawienia konfiguracji. Aby zmiany zostały wprowadzone, nie trzeba ponownie uruchamiać komputera ani serwera usług IIS.

Witryna internetowa może zawierać kilka katalogów wirtualnych i podkatalogów, z *web.config* plików w każdym z nich. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Aplikacje dziedziczą ustawienia konfiguracji *web.config* plików na wyższych poziomach w ścieżce adresu URL. Hierarchiczne *ustawieniaweb.config* mają zastosowanie do wszystkich [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji w hierarchii. Ustawienie innej konfiguracji w pliku *web.config* niżej w hierarchii zastępuje ustawienia w wyższym pliku.

Jeśli na przykład określisz w pliku www.microsoft.com/aaa/web.config, każda aplikacja w `debug="true"` folderze *aaa* <em></em>lub w dowolnym podfolderze *aaa* dziedziczy  to ustawienie, z wyjątkiem sytuacji, gdy jedna z tych aplikacji zastępuje to ustawienie własnymweb.configpliku.

## <a name="publish-in-debug-mode-using-the-file-system"></a>Publikowanie w trybie debugowania przy użyciu systemu plików

Istnieją różne sposoby publikowania aplikacji w usługach IIS. Te kroki pokazują, jak utworzyć i wdrożyć debugowanie profilu publikowania przy użyciu systemu plików. Aby to zrobić, musisz mieć uruchomione konto Visual Studio jako administrator.

> [!IMPORTANT]
> Jeśli zmienisz kod lub ponownie skompilowasz, musisz powtórzyć te kroki, aby ponownie opublikować.

1. W Visual Studio kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj.**

3. Wybierz **pozycję IIS, FTP itp., a** następnie kliknij pozycję **Opublikuj.**

    ![Zrzut ekranu przedstawiający okno dialogowe Wybieranie celu publikacji w Visual Studio. Wybrane są usługi IIS, Web Deploy FTP i wyróżniony przycisk Publikuj.](media/dbg-aspnet-local-iis.png)

4. W **oknie dialogowym CustomProfile** dla **opcji Metoda publikowania** wybierz **pozycję System plików**.

5. W **pozycji Lokalizacja docelowa** wybierz **pozycję Przeglądaj** (**...**).

   - Aby ASP.NET, wybierz pozycję **Lokalne usługi IIS,** wybierz witrynę internetową utworzoną dla aplikacji, a następnie wybierz **pozycję Otwórz.**

     ![Publikowanie w ASP.NET w usługach IIS](media/dbg-aspnet-local-iis1.png "Publikowanie ASP.NET w usługach IIS")

   - W ASP.NET Core wybierz pozycję **System plików,** wybierz folder, który został ustawiony dla aplikacji, a następnie wybierz pozycję **Otwórz.**

1. Wybierz opcję **Dalej**.

1. W **obszarze Konfiguracja** wybierz pozycję **Debuguj** z listy rozwijanej.

1. Wybierz pozycję **Zapisz**.

1. W **oknie dialogowym** Publikowanie upewnij się, że jest wyświetlany profil **CustomProfile** (lub nazwa właśnie utworzonego profilu), a dla ustawienia **LastUsedBuildConfiguration** ustawiono wartość **Debuguj**.

1. Kliknij pozycję **Opublikuj**.

    ![Zrzut ekranu przedstawiający okno dialogowe Publikowanie z wybraną aplikacją CustomProfile, wyróżnionym przyciskiem Publikuj i ustawieniem LastBuildConfiguration na debugowanie.](media/dbg-aspnet-local-iis-select-site.png)

> [!IMPORTANT]
> Tryb debugowania znacznie zmniejsza wydajność aplikacji. Aby uzyskać najlepszą wydajność, ustaw wweb.configi określ kompilację wydania podczas wdrażania aplikacji produkcyjnej lub `debug="false"` przeprowadzania pomiarów  wydajności.

## <a name="see-also"></a>Zobacz też
- [Debugowanie ASP.NET: wymagania systemowe](aspnet-debugging-system-requirements.md)
- [Instrukcje: uruchamianie procesu roboczego z konta użytkownika](how-to-run-the-worker-process-under-a-user-account.md)
- [Porada: znajdowanie nazwy procesu ASP.NET](how-to-find-the-name-of-the-aspnet-process.md)
- [Debugowanie wdrożonych aplikacji internetowych](debugging-deployed-web-applications.md)
- [Przewodnik: debugowanie formularza internetowego](walkthrough-debugging-a-web-form.md)
- [Jak debugować ASP.NET wyjątków](how-to-debug-aspnet-exceptions.md)
- [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](debugging-web-applications-errors-and-troubleshooting.md)
