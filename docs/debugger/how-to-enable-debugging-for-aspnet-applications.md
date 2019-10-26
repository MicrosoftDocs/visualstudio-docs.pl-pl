---
title: Włącz debugowanie dla aplikacji ASP.NET | Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: a6f20a2272214a525b00ebf07ebc6e5e803b138c
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911350"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Debuguj ASP.NET lub ASP.NET Core aplikacje w programie Visual Studio

Możesz debugować ASP.NET i ASP.NET Core aplikacje w programie Visual Studio. Proces ten różni się między ASP.NET i ASP.NET Core i niezależnie od tego, czy jest on uruchamiany na IIS Express czy na lokalnym serwerze usług IIS.

>[!NOTE]
>Poniższe kroki i ustawienia dotyczą tylko debugowania aplikacji na serwerze lokalnym. Debugowanie aplikacji na zdalnym serwerze IIS korzysta **z dołączania do procesu**i ignoruje te ustawienia. Aby uzyskać więcej informacji i instrukcje dotyczące zdalnego debugowania aplikacji ASP.NET w usługach IIS, zobacz [Remote debug ASP.NET na komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) lub [zdalne debugowanie ASP.NET Core na zdalnym komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

Wbudowany serwer IIS Express jest dołączony do programu Visual Studio. IIS Express jest domyślnym serwerem debugowania dla projektów ASP.NET i ASP.NET Core i jest wstępnie skonfigurowany. Jest to najprostszy sposób na Debugowanie i idealny do wstępnego debugowania i testowania.

Możesz również debugować aplikację ASP.NET lub ASP.NET Core na lokalnym serwerze IIS (w wersji 8,0 lub nowszej), która jest skonfigurowana do uruchamiania aplikacji. Aby debugować lokalne usługi IIS, należy spełnić następujące wymagania:

<a name="iis"></a>
- Wybierz opcję **czas projektowania obsługa usług IIS** podczas instalowania programu Visual Studio. (W razie potrzeby uruchom ponownie Instalator programu Visual Studio, wybierz pozycję **Modyfikuj**i Dodaj ten składnik).
- Program Visual Studio jest uruchomiony jako administrator.
- Zainstaluj i poprawnie Skonfiguruj usługi IIS przy użyciu odpowiednich wersji ASP.NET i/lub ASP.NET Core. Aby uzyskać więcej informacji i instrukcje, zobacz [iis 8,0 przy użyciu ASP.NET 3,5 i ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) lub [ASP.NET Core hosta w systemie Windows z usługami IIS](/aspnet/core/host-and-deploy/iis/index).
- Upewnij się, że aplikacja działa na serwerze IIS bez błędów.

## <a name="debug-aspnet-apps"></a>Debuguj aplikacje ASP.NET

IIS Express jest to ustawienie domyślne i wstępnie skonfigurowane. W przypadku debugowania w lokalnych usługach IIS upewnij się, że spełniasz [wymagania dotyczące lokalnego debugowania usług IIS](#iis).

1. Wybierz projekt ASP.NET w programie Visual Studio **Eksplorator rozwiązań** i kliknij ikonę **Właściwości** , naciśnij klawisz **Alt**+**Enter**lub kliknij prawym przyciskiem myszy i wybierz polecenie **Właściwości**.

1. Wybierz kartę **Sieć Web** .

1. W okienku **Właściwości** w obszarze **serwery**
   - W obszarze IIS Express wybierz pozycję **IIS Express** z listy rozwijanej.
   - W przypadku lokalnych usług IIS
     1. Na liście rozwijanej wybierz pozycję **lokalne usługi IIS** .
     1. W polu **adres URL projektu** wybierz pozycję **Utwórz katalog wirtualny**, jeśli aplikacja nie została jeszcze skonfigurowana w usługach IIS.

1. W obszarze **debugery**wybierz pozycję **ASP.NET**.

   ![Ustawienia debugera ASP.NET](media/dbg-aspnet-enable-debugging2.png "Ustawienia debugera ASP.NET")

1. Użyj **pliku** > **Zapisz wybrane elementy** lub **Ctrl**+**S** , aby zapisać zmiany.

1. Aby debugować aplikację, w projekcie Ustaw punkty przerwania w kodzie. Na pasku narzędzi programu Visual Studio upewnij się, że konfiguracja ma ustawioną wartość **Debuguj**, a w polu emulator wyświetlana jest przeglądarka, która ma zostać wyświetlona w **IIS Express (\<Nazwa przeglądarki >)** lub **lokalnych usług IIS (\<Nazwa przeglądarki >)** .

1. Aby rozpocząć debugowanie, wybierz **IIS Express (\<Nazwa przeglądarki >)** lub **lokalnych usług IIS (\<Nazwa przeglądarki >)** na pasku narzędzi wybierz pozycję **Rozpocznij debugowanie** z menu **Debuguj** lub naciśnij klawisz **F5**. Debuger wstrzymuje się do punktów przerwania. Jeśli debuger nie może trafiać punktów przerwania, zobacz [Rozwiązywanie problemów z debugowaniem](#troubleshoot-debugging).

## <a name="debug-aspnet-core-apps"></a>Debuguj ASP.NET Core aplikacje

IIS Express jest to ustawienie domyślne i wstępnie skonfigurowane. W przypadku debugowania w lokalnych usługach IIS upewnij się, że spełniasz [wymagania dotyczące lokalnego debugowania usług IIS](#iis).

1. Wybierz projekt ASP.NET Core w programie Visual Studio **Eksplorator rozwiązań** i kliknij ikonę **Właściwości** , naciśnij klawisze **Alt**+**Enter**lub kliknij prawym przyciskiem myszy i wybierz polecenie **Właściwości**.

1. Wybierz kartę **debugowanie** .

1. W okienku **Właściwości** obok pozycji **profil**
   - W obszarze IIS Express wybierz pozycję **IIS Express** z listy rozwijanej.
   - W przypadku lokalnych usług IIS wybierz z listy rozwijanej nazwę aplikacji lub wybierz pozycję **Nowy**, Utwórz nową nazwę profilu, a następnie wybierz **przycisk OK**.

1. Obok pozycji **Uruchom**wybierz opcję **IIS Express** lub **IIS** z listy rozwijanej.

1. Upewnij się, że jest wybrana **przeglądarka uruchamiania** .

1. W obszarze **zmienne środowiskowe**upewnij się, że **ASPNETCORE_ENVIRONMENT** ma wartość **programowanie**. W przeciwnym razie wybierz pozycję **Dodaj** i Dodaj.

   ![Ustawienia debugera ASP.NET Core](../debugger/media/dbg-aspnet-enable-debugging3.png "Ustawienia debugera ASP.NET Core")

1. Użyj **pliku** > **Zapisz wybrane elementy** lub **Ctrl**+**S** , aby zapisać zmiany.

1. Aby debugować aplikację, w projekcie Ustaw punkty przerwania w kodzie. Na pasku narzędzi programu Visual Studio upewnij się, że konfiguracja ma ustawioną wartość **Debuguj**, a w polu emulator zostanie wyświetlona wartość **IIS Express**lub Nowa nazwa profilu usług IIS.

1. Aby rozpocząć debugowanie, wybierz **IIS Express** lub **\<nazwę profilu usług IIS >** na pasku narzędzi wybierz pozycję **Rozpocznij debugowanie** z menu **Debuguj** lub naciśnij klawisz **F5**. Debuger wstrzymuje się do punktów przerwania. Jeśli debuger nie może trafiać punktów przerwania, zobacz [Rozwiązywanie problemów z debugowaniem](#troubleshoot-debugging).

## <a name="troubleshoot-debugging"></a>Rozwiązywanie problemów z debugowaniem

Jeśli lokalne debugowanie usług IIS nie może postępować w punkcie przerwania, wykonaj następujące kroki, aby rozwiązać problem.

1. Uruchom aplikację internetową z usług IIS i upewnij się, że działa poprawnie. Pozostaw uruchomioną aplikację sieci Web.

2. W programie Visual Studio wybierz kolejno opcje **debuguj > Dołącz do procesu** lub naciśnij **klawisze Ctrl**+**Alt**+**P**, a następnie połącz się z procesem ASP.NET lub ASP.NET Core (zazwyczaj **w3wp. exe** lub **dotnet. exe**). Aby uzyskać więcej informacji, zobacz [dołączanie do procesu](attach-to-running-processes-with-the-visual-studio-debugger.md) i [znajdowanie nazwy procesu ASP.NET](how-to-find-the-name-of-the-aspnet-process.md).

Jeśli można nawiązać połączenie i napotkać punkt przerwania za pomocą **dołączania do procesu**, ale nie za pomocą **debugowania** > **rozpocząć debugowanie** lub **F5**, ustawienie jest prawdopodobnie nieprawidłowe we właściwościach projektu. Jeśli używasz pliku HOSTs, upewnij się, że jest on również skonfigurowany prawidłowo.

## <a name="configure-debugging-in-the-webconfig-file"></a>Konfigurowanie debugowania w pliku Web. config

Projekty ASP.NET mają domyślnie pliki *Web. config* , które zawierają zarówno konfigurację aplikacji, jak i informacje o uruchamianiu, w tym ustawienia debugowania. Pliki *Web. config* muszą być poprawnie skonfigurowane na potrzeby debugowania. Ustawienia **Właściwości** w poprzednich sekcjach aktualizują pliki *Web. config* , ale można je również skonfigurować ręcznie.

> [!NOTE]
> Projekty ASP.NET Core nie mają początkowo plików *Web. config* , ale używają plików *appSettings. JSON* i *profilu launchsettings. JSON* na potrzeby konfiguracji i uruchamiania aplikacji. Wdrożenie aplikacji tworzy plik *Web. config* lub pliki w projekcie, ale zazwyczaj nie zawierają one informacji o debugowaniu.

> [!TIP]
> Proces wdrażania może zaktualizować ustawienia *Web. config* , aby przed podjęciem próby debugowania upewnić się, że *plik Web. config* jest skonfigurowany do debugowania.

**Aby ręcznie skonfigurować plik *Web. config* na potrzeby debugowania:**

1. W programie Visual Studio Otwórz plik *Web. config* projektu ASP.NET.

2. Plik *Web. config* jest plikiem XML, dlatego zawiera zagnieżdżone sekcje oznaczone przez Tagi. Znajdź sekcję `configuration/system.web/compilation`. (Jeśli element `compilation` nie istnieje, utwórz go).

3. Upewnij się, że atrybut `debug` w elemencie `compilation` jest ustawiony na `true`. (Jeśli element `compilation` nie zawiera atrybutu `debug`, Dodaj go i ustaw go na `true`).

   Jeśli używasz lokalnych usług IIS zamiast domyślnego serwera IIS Express, upewnij się, że wartość atrybutu `targetFramework` w elemencie `compilation` jest zgodna z strukturą na serwerze usług IIS.

   Element `compilation` pliku *Web. config* powinien wyglądać podobnie do poniższego przykładu:

   > [!NOTE]
   > Ten przykład to częściowy plik *Web. config* . Istnieją zwykle dodatkowe sekcje XML w elementach `configuration` i `system.web`, a element `compilation` może również zawierać inne atrybuty i elementy.

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

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] automatycznie wykrywa wszelkie zmiany w plikach *Web. config* i stosuje nowe ustawienia konfiguracji. Aby zmiany zaczęły obowiązywać, nie trzeba ponownie uruchamiać komputera ani serwera usług IIS.

Witryna sieci Web może zawierać kilka katalogów wirtualnych i podkatalogów z plikami *Web. config* w każdej z nich. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Apps dziedziczą ustawienia konfiguracji z plików *Web. config* na wyższych poziomach w ścieżce URL. Hierarchiczne ustawienia pliku *Web. config* mają zastosowanie do wszystkich [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji znajdujących się poniżej w hierarchii. Ustawienie innej konfiguracji w pliku *Web. config* poniżej hierarchii zastępuje ustawienia w wyższym pliku.

Na przykład jeśli określisz `debug="true"` w <em>www.Microsoft.com/AAA/Web.config</em>, dowolna aplikacja w folderze *AAA* lub w dowolnym podfolderze *AAA* dziedziczy to ustawienie, chyba że jedna z tych aplikacji zastępuje ustawienie własnym *plik Web. config.* rozszerzeniem.

## <a name="publish-in-debug-mode-using-the-file-system"></a>Publikowanie w trybie debugowania przy użyciu systemu plików

Istnieją różne sposoby publikowania aplikacji w usługach IIS. W tych krokach pokazano, jak utworzyć i wdrożyć profil publikowania debugowania przy użyciu systemu plików. Aby to zrobić, musisz mieć uruchomiony program Visual Studio jako administrator.

> [!IMPORTANT]
> Jeśli zmienisz kod lub Skompiluj ponownie, musisz powtórzyć te kroki, aby ponownie opublikować.

1. W programie Visual Studio kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj**.

3. Wybierz opcję **IIS, FTP itp.** , a następnie kliknij przycisk **Publikuj**.

    ![Publikowanie w usługach IIS](media/dbg-aspnet-local-iis.png "Publikowanie w usługach IIS")

4. W oknie dialogowym **CustomProfile** w polu **Metoda publikowania**wybierz pozycję **system plików**.

5. W obszarze **Lokalizacja docelowa**wybierz pozycję **Przeglądaj** ( **...** ).

   - W polu ASP.NET wybierz pozycję **lokalne usługi IIS**, wybierz witrynę sieci Web utworzoną dla aplikacji, a następnie wybierz pozycję **Otwórz**.

     ![Publikowanie w usłudze ASP.NET w usługach IIS](media/dbg-aspnet-local-iis1.png "Publikowanie ASP.NET w usługach IIS")

   - W obszarze ASP.NET Core wybierz pozycję **system plików**, wybierz folder, który został skonfigurowany dla aplikacji, a następnie wybierz pozycję **Otwórz**.

1. Wybierz pozycję **dalej**.

1. W obszarze **Konfiguracja**wybierz pozycję **Debuguj** z listy rozwijanej.

1. Wybierz pozycję **Zapisz**.

1. W oknie dialogowym **Publikowanie** upewnij się, że jest wyświetlana **CustomProfile** (lub nazwa utworzonego właśnie profilu), a **LastUsedBuildConfiguration** jest ustawiona na **Debuguj**.

1. Wybierz pozycję **Publikuj**.

    ![Publikowanie w usługach IIS](media/dbg-aspnet-local-iis-select-site.png "Publikowanie w usługach IIS")

> [!IMPORTANT]
> Tryb debugowania znacznie zmniejsza wydajność aplikacji. Aby uzyskać najlepszą wydajność, należy ustawić `debug="false"` w *pliku Web. config* i określić kompilację wydania podczas wdrażania aplikacji produkcyjnej lub przeprowadzać pomiary wydajności.

## <a name="see-also"></a>Zobacz także
- [Debugowanie ASP.NET: wymagania systemowe](aspnet-debugging-system-requirements.md)
- [Instrukcje: uruchamianie procesu roboczego z konta użytkownika](how-to-run-the-worker-process-under-a-user-account.md)
- [Porada: znajdowanie nazwy procesu ASP.NET](how-to-find-the-name-of-the-aspnet-process.md)
- [Debuguj wdrożone aplikacje sieci Web](debugging-deployed-web-applications.md)
- [Przewodnik: debugowanie formularza sieci Web](walkthrough-debugging-a-web-form.md)
- [Instrukcje: debugowanie wyjątków ASP.NET](how-to-debug-aspnet-exceptions.md)
- [Debugowanie aplikacji sieci Web: Błędy i rozwiązywanie problemów](debugging-web-applications-errors-and-troubleshooting.md)
