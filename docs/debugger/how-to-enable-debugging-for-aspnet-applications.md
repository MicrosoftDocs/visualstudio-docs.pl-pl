---
title: Włącz debugowanie dla aplikacji ASP.NET | Microsoft Docs
description: Dowiedz się, jak włączyć debugowanie dla aplikacji ASP.NET i ASP.NET Core w programie Visual Studio. Proces ten można uruchomić na serwerze IIS Express lub na lokalnym serwerze IIS.
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
ms.openlocfilehash: 8ef65fbd9452aef52d807210f84928a4eef14100
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877749"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Debugowanie aplikacji platformy ASP.NET lub ASP.NET Core w programie Visual Studio

Możesz debugować ASP.NET i ASP.NET Core aplikacje w programie Visual Studio. Proces ten różni się między ASP.NET i ASP.NET Core i niezależnie od tego, czy jest on uruchamiany na IIS Express czy na lokalnym serwerze usług IIS.

>[!NOTE]
>Poniższe kroki i ustawienia dotyczą tylko debugowania aplikacji na serwerze lokalnym. Debugowanie aplikacji na zdalnym serwerze IIS korzysta **z dołączania do procesu** i ignoruje te ustawienia. Aby uzyskać więcej informacji i instrukcje dotyczące zdalnego debugowania aplikacji ASP.NET w usługach IIS, zobacz [Remote debug ASP.NET na komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) lub [zdalne debugowanie ASP.NET Core na zdalnym komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

Wbudowany serwer IIS Express jest dołączony do programu Visual Studio. IIS Express jest domyślnym serwerem debugowania dla projektów ASP.NET i ASP.NET Core i jest wstępnie skonfigurowany. Jest to najprostszy sposób na Debugowanie i idealny do wstępnego debugowania i testowania.

Możesz również debugować aplikację ASP.NET lub ASP.NET Core na lokalnym serwerze IIS (w wersji 8,0 lub nowszej), która jest skonfigurowana do uruchamiania aplikacji. Aby debugować lokalne usługi IIS, należy spełnić następujące wymagania:

<a name="iis"></a>
- Jeśli nie jest zainstalowana, zainstaluj **obciążenie ASP.NET i programowanie dla sieci Web**. (Uruchom ponownie Instalator programu Visual Studio, wybierz pozycję **Modyfikuj** i Dodaj to obciążenie).

   ::: moniker range="vs-2017"
   W programie Visual Studio 2017 poszukaj składnika **Obsługa usług IIS w czasie opracowywania** . Upewnij się, że jest ono zaznaczone podczas dodawania obciążenia.
   ::: moniker-end
- Uruchom program Visual Studio jako administrator.
- Zainstaluj i poprawnie Skonfiguruj usługi IIS przy użyciu odpowiednich wersji ASP.NET i/lub ASP.NET Core. Aby uzyskać więcej informacji na temat korzystania z usług IIS z ASP.NET Core, zobacz [hostowanie ASP.NET Core w systemie Windows za pomocą usług IIS](/aspnet/core/host-and-deploy/iis/index). Aby uzyskać ASP.NET, zobacz [Install IIS and ASP.NET modules](/iis/application-frameworks/scenario-build-an-aspnet-website-on-iis/configuring-step-1-install-iis-and-asp-net-modules).
- Upewnij się, że aplikacja działa na serwerze IIS bez błędów.

## <a name="debug-aspnet-apps"></a>Debuguj aplikacje ASP.NET

IIS Express jest to ustawienie domyślne i wstępnie skonfigurowane. W przypadku debugowania w lokalnych usługach IIS upewnij się, że spełniasz [wymagania dotyczące lokalnego debugowania usług IIS](#iis).

1. Wybierz projekt ASP.NET w programie Visual Studio **Eksplorator rozwiązań** i kliknij ikonę **Właściwości** , naciśnij klawisz **Alt** + **Enter** lub kliknij prawym przyciskiem myszy i wybierz polecenie **Właściwości**.

1. Wybierz kartę **Sieć Web** .

1. W okienku **Właściwości** w obszarze **serwery**
   - W obszarze IIS Express wybierz pozycję **IIS Express** z listy rozwijanej.
   - W przypadku lokalnych usług IIS
     1. Na liście rozwijanej wybierz pozycję **lokalne usługi IIS** .
     1. W polu **adres URL projektu** wybierz pozycję **Utwórz katalog wirtualny**, jeśli aplikacja nie została jeszcze skonfigurowana w usługach IIS.

1. W obszarze **debugery** wybierz pozycję **ASP.NET**.

   ![Ustawienia debugera ASP.NET](media/dbg-aspnet-enable-debugging2.png "Ustawienia debugera ASP.NET")

1. Użyj **pliku**  >  **Zapisz wybrane elementy** lub **Ctrl** + **S** , aby zapisać zmiany.

1. Aby debugować aplikację, w projekcie Ustaw punkty przerwania w kodzie. Na pasku narzędzi programu Visual Studio upewnij się, że konfiguracja jest ustawiona na **Debuguj**, a w polu emulator pojawia się przeglądarka, która ma być wyświetlana w **IIS Express ( \<Browser name> )** lub **lokalnych usługach IIS ( \<Browser name> )** .

1. Aby rozpocząć debugowanie, wybierz **pozycję IIS Express ( \<Browser name> )** lub **lokalne usługi IIS ( \<Browser name> )** na pasku narzędzi, wybierz pozycję **Rozpocznij debugowanie** z menu **Debuguj** lub naciśnij klawisz **F5**. Debuger wstrzymuje się do punktów przerwania. Jeśli debuger nie może trafiać punktów przerwania, zobacz [Rozwiązywanie problemów z debugowaniem](#troubleshoot-debugging).

## <a name="debug-aspnet-core-apps"></a>Debuguj ASP.NET Core aplikacje

IIS Express jest to ustawienie domyślne i wstępnie skonfigurowane. W przypadku debugowania w lokalnych usługach IIS upewnij się, że spełniasz [wymagania dotyczące lokalnego debugowania usług IIS](#iis).

1. Wybierz projekt ASP.NET Core w programie Visual Studio **Eksplorator rozwiązań** i kliknij ikonę **Właściwości** , naciśnij klawisz **Alt** + **Enter** lub kliknij prawym przyciskiem myszy i wybierz polecenie **Właściwości**.

1. Wybierz kartę **debugowanie** .

1. W okienku **Właściwości** obok pozycji **profil**
   - W obszarze IIS Express wybierz pozycję **IIS Express** z listy rozwijanej.
   - W przypadku lokalnych usług IIS wybierz z listy rozwijanej nazwę aplikacji lub wybierz pozycję **Nowy**, Utwórz nową nazwę profilu, a następnie wybierz **przycisk OK**.

1. Obok pozycji **Uruchom** wybierz opcję **IIS Express** lub **IIS** z listy rozwijanej.

1. Upewnij się, że jest wybrana **przeglądarka uruchamiania** .

1. W obszarze **zmienne środowiskowe** upewnij się, że **ASPNETCORE_ENVIRONMENT** jest obecny z wartością **opracowywania**. W przeciwnym razie wybierz pozycję **Dodaj** i Dodaj.

   ![Ustawienia debugera ASP.NET Core](../debugger/media/dbg-aspnet-enable-debugging3.png "Ustawienia debugera ASP.NET Core")

1. Użyj **pliku**  >  **Zapisz wybrane elementy** lub **Ctrl** + **S** , aby zapisać zmiany.

1. Aby debugować aplikację, w projekcie Ustaw punkty przerwania w kodzie. Na pasku narzędzi programu Visual Studio upewnij się, że konfiguracja ma ustawioną wartość **Debuguj**, a w polu emulator zostanie wyświetlona wartość **IIS Express** lub Nowa nazwa profilu usług IIS.

1. Aby rozpocząć debugowanie, wybierz pozycję **IIS Express** lub **\<IIS profile name>** na pasku narzędzi wybierz pozycję **Rozpocznij debugowanie** z menu **Debuguj** lub naciśnij klawisz **F5**. Debuger wstrzymuje się do punktów przerwania. Jeśli debuger nie może trafiać punktów przerwania, zobacz [Rozwiązywanie problemów z debugowaniem](#troubleshoot-debugging).

## <a name="troubleshoot-debugging"></a>Rozwiązywanie problemów z debugowaniem

Jeśli lokalne debugowanie usług IIS nie może postępować w punkcie przerwania, wykonaj następujące kroki, aby rozwiązać problem.

1. Uruchom aplikację internetową z usług IIS i upewnij się, że działa poprawnie. Pozostaw uruchomioną aplikację sieci Web.

2. W programie Visual Studio wybierz kolejno opcje **Debuguj > Dołącz do procesu** lub naciśnij **klawisze CTRL** + **Alt** + **P**, a następnie połącz się z procesem ASP.NET lub ASP.NET Core (zazwyczaj **w3wp.exe** lub **dotnet.exe**). Aby uzyskać więcej informacji, zobacz [dołączanie do procesu](attach-to-running-processes-with-the-visual-studio-debugger.md) i [znajdowanie nazwy procesu ASP.NET](how-to-find-the-name-of-the-aspnet-process.md).

Jeśli można nawiązać połączenie i napotkać punkt przerwania za pomocą **dołączania do procesu**, ale nie **za pomocą debugowania**  >  **Rozpocznij debugowanie** lub **F5**, ustawienie jest prawdopodobnie nieprawidłowe we właściwościach projektu. Jeśli używasz pliku HOSTs, upewnij się, że jest on również skonfigurowany prawidłowo.

## <a name="configure-debugging-in-the-webconfig-file"></a>Konfigurowanie debugowania w pliku web.config

Projekty ASP.NET mają domyślnie pliki *web.config* , które zawierają zarówno konfigurację aplikacji, jak i informacje o uruchamianiu, w tym ustawienia debugowania. Pliki *web.config* muszą być poprawnie skonfigurowane do debugowania. Ustawienia **Właściwości** w poprzednich sekcjach aktualizują pliki *web.config* , ale można je również skonfigurować ręcznie.

> [!NOTE]
> Projekty ASP.NET Core nie mają początkowo plików *web.config* , ale w celu konfigurowania i uruchamiania aplikacji należy używać *appsettings.jsna* i *launchSettings.jsna* plikach. Wdrożenie aplikacji tworzy plik *web.config* lub plików w projekcie, ale nie zawiera zwykle informacji o debugowaniu.

> [!TIP]
> Proces wdrażania może zaktualizować ustawienia *web.config* , więc przed podjęciem próby debugowania upewnij się, że *web.config* jest skonfigurowany do debugowania.

**Aby ręcznie skonfigurować plik *web.config* do debugowania:**

1. W programie Visual Studio Otwórz plik *web.config* projektu programu ASP.NET.

2. *Web.config* jest plikiem XML, dlatego zawiera zagnieżdżone sekcje oznaczone przez Tagi. Znajdź sekcję `configuration/system.web/compilation`. (Jeśli `compilation` element nie istnieje, utwórz go).

3. Upewnij się, że `debug` atrybut w `compilation` elemencie jest ustawiony na `true` . (Jeśli `compilation` element nie zawiera `debug` atrybutu, Dodaj go i ustaw go na `true` ).

   Jeśli używasz lokalnych usług IIS zamiast domyślnego serwera IIS Express, upewnij się, że `targetFramework` wartość atrybutu w `compilation` elemencie jest zgodna z strukturą na serwerze usług IIS.

   `compilation`Element pliku *web.config* powinien wyglądać podobnie do poniższego przykładu:

   > [!NOTE]
   > Ten przykład jest częściowym plikiem *web.config* . W elementach i są zwykle dodatkowe sekcje `configuration` XML `system.web` , a `compilation` element może również zawierać inne atrybuty i elementy.

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

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Program automatycznie wykrywa wszelkie zmiany w plikach *web.config* i stosuje nowe ustawienia konfiguracji. Aby zmiany zaczęły obowiązywać, nie trzeba ponownie uruchamiać komputera ani serwera usług IIS.

Witryna sieci Web może zawierać kilka katalogów wirtualnych i podkatalogów, w których *web.config* pliki w każdym z nich. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacje dziedziczą ustawienia konfiguracji z plików *web.config* na wyższych poziomach w ścieżce URL. Ustawienia hierarchicznych plików *web.config* są stosowane do wszystkich [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji znajdujących się poniżej w hierarchii. Ustawienie innej konfiguracji w pliku *web.config* dolnym w hierarchii przesłania ustawienia w wyższym pliku.

Na przykład w przypadku określenia `debug="true"` w <em>www.Microsoft.com/AAA/web.config</em>każda aplikacja w folderze *AAA* lub w dowolnym podfolderze *AAA* dziedziczy to ustawienie, z wyjątkiem tego, że jedna z tych aplikacji zastępuje ustawienie własnym *web.config* plikiem.

## <a name="publish-in-debug-mode-using-the-file-system"></a>Publikowanie w trybie debugowania przy użyciu systemu plików

Istnieją różne sposoby publikowania aplikacji w usługach IIS. W tych krokach pokazano, jak utworzyć i wdrożyć profil publikowania debugowania przy użyciu systemu plików. Aby to zrobić, musisz mieć uruchomiony program Visual Studio jako administrator.

> [!IMPORTANT]
> Jeśli zmienisz kod lub Skompiluj ponownie, musisz powtórzyć te kroki, aby ponownie opublikować.

1. W programie Visual Studio kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj**.

3. Wybierz opcję **IIS, FTP itp.** , a następnie kliknij przycisk **Publikuj**.

    ![Zrzut ekranu przedstawiający okno dialogowe Wybieranie elementu docelowego publikowania w programie Visual Studio. Wybrano opcję IIS, FTP, Web Deploy i przycisk Publikuj jest wyróżniony.](media/dbg-aspnet-local-iis.png)

4. W oknie dialogowym **CustomProfile** w polu **Metoda publikowania** wybierz pozycję **system plików**.

5. W obszarze **Lokalizacja docelowa** wybierz pozycję **Przeglądaj** (**...**).

   - W polu ASP.NET wybierz pozycję **lokalne usługi IIS**, wybierz witrynę sieci Web utworzoną dla aplikacji, a następnie wybierz pozycję **Otwórz**.

     ![Publikowanie w usłudze ASP.NET w usługach IIS](media/dbg-aspnet-local-iis1.png "Publikowanie ASP.NET w usługach IIS")

   - W obszarze ASP.NET Core wybierz pozycję **system plików**, wybierz folder, który został skonfigurowany dla aplikacji, a następnie wybierz pozycję **Otwórz**.

1. Wybierz opcję **Dalej**.

1. W obszarze **Konfiguracja** wybierz pozycję **Debuguj** z listy rozwijanej.

1. Wybierz pozycję **Zapisz**.

1. W oknie dialogowym **Publikowanie** upewnij się, że jest wyświetlana **CustomProfile** (lub nazwa utworzonego właśnie profilu), a **LastUsedBuildConfiguration** jest ustawiona na **Debuguj**.

1. Kliknij pozycję **Opublikuj**.

    ![Zrzut ekranu okna dialogowego publikowanie z wybraną aplikacją CustomProfile, wyróżniony przycisk Publikuj i LastBuildConfiguration ustawiony na wartość Debuguj.](media/dbg-aspnet-local-iis-select-site.png)

> [!IMPORTANT]
> Tryb debugowania znacznie zmniejsza wydajność aplikacji. Aby uzyskać najlepszą wydajność, ustaw `debug="false"` w *web.config* i określ kompilację wydania podczas wdrażania aplikacji produkcyjnej lub przeprowadź pomiary wydajności.

## <a name="see-also"></a>Zobacz też
- [Debugowanie ASP.NET: wymagania systemowe](aspnet-debugging-system-requirements.md)
- [Instrukcje: uruchamianie procesu roboczego z konta użytkownika](how-to-run-the-worker-process-under-a-user-account.md)
- [Porada: znajdowanie nazwy procesu ASP.NET](how-to-find-the-name-of-the-aspnet-process.md)
- [Debuguj wdrożone aplikacje sieci Web](debugging-deployed-web-applications.md)
- [Przewodnik: debugowanie formularza sieci Web](walkthrough-debugging-a-web-form.md)
- [Instrukcje: debugowanie wyjątków ASP.NET](how-to-debug-aspnet-exceptions.md)
- [Debugowanie aplikacji sieci Web: Błędy i rozwiązywanie problemów](debugging-web-applications-errors-and-troubleshooting.md)
