---
title: Włącz debugowanie aplikacji ASP.NET | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: d383c559e605392b01ba2c476fd4ed5ae5d48625
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526662"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Debugowanie aplikacji ASP.NET lub ASP.NET Core w programie Visual Studio

Można debugować aplikacje programu ASP.NET i ASP.NET Core w programie Visual Studio. Ten proces różni się między ASP.NET i ASP.NET Core i tego, czy uruchomienie go na usług IIS Express lub lokalnego serwera IIS.

>[!NOTE]
>Następujące kroki i ustawienia dotyczą tylko debugowanie aplikacji na serwerze lokalnym. Debugowanie aplikacji na zdalnym serwerze IIS serwer używa **dołączyć do procesu**i ignoruje te ustawienia. Aby uzyskać więcej informacji oraz instrukcje dotyczące zdalnego debugowania aplikacji ASP.NET w usługach IIS, zobacz [platforma ASP.NET debugowania zdalnego na komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) lub [zdalne debugowanie platformy ASP.NET Core na komputerze zdalnym IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

Wbudowanego serwera usług IIS Express jest dołączana do programu Visual Studio. Usługi IIS Express jest domyślny serwer debugowania dla projektów ASP.NET i ASP.NET Core i jest wstępnie skonfigurowany. Jest najprostszym sposobem debugowania i idealne rozwiązanie dla początkowej debugowania i testowania.

Można również debugować aplikację platformy ASP.NET lub ASP.NET Core na lokalnym serwerze usług IIS (w wersji 8.0 lub nowszej), który jest skonfigurowany do uruchamiania aplikacji. Aby debugować na lokalnym serwerze IIS, musi spełniać następujące wymagania:

<a name="iis"></a>
- Wybierz **czas opracowywania usługi IIS obsługują** podczas instalowania programu Visual Studio. (Jeśli to konieczne, ponownie uruchom Instalatora programu Visual Studio, wybierz **Modyfikuj**i Dodaj ten składnik.)
- Należy uruchomić program Visual Studio jako administrator.
- Zainstaluj i poprawnie skonfigurować odpowiednie wersje programu ASP.NET lub ASP.NET Core w usługach IIS. Aby uzyskać więcej informacji oraz instrukcje, zobacz [3.5 przy użyciu platformy ASP.NET w programie IIS 8.0 i program ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) lub [hosta ASP.NET Core na Windows z programem IIS](https://docs.microsoft.com/aspnet/core/host-and-deploy/iis/index).
- Upewnij się, że aplikacja jest uruchamiana na serwerze IIS bez błędów.

## <a name="debug-aspnet-apps"></a>Debugowanie aplikacji ASP.NET

Usługi IIS Express jest ustawieniem domyślnym i jest wstępnie skonfigurowany. Jeśli debugujesz na lokalnym serwerze IIS, upewnij się, że spełniasz [wymagania dla debugowania lokalnego IIS](#iis).

1. Wybierz projekt platformy ASP.NET w programie Visual Studio **Eksploratora rozwiązań** i kliknij przycisk **właściwości** ikonę, naciśnij klawisz **Alt**+**Enter**, lub kliknij prawym przyciskiem myszy i wybierz pozycję **właściwości**.

1. Wybierz **Web** kartę.

1. W **właściwości** okienku w obszarze **serwerów**,
   - W przypadku usług IIS Express, wybrać **usług IIS Express** z listy rozwijanej.
   - Dla lokalnych usług IIS,
     1. Wybierz **lokalne usługi IIS** z listy rozwijanej.
     1. Obok pozycji **adres URL projektu** pól, zaznacz **Utwórz katalog wirtualny**, jeśli jeszcze nie skonfigurowano aplikacji w usługach IIS.

1. W obszarze **debugery**, wybierz opcję **ASP.NET**.

   ![Ustawienia debugera ASP.NET](media/dbg-aspnet-enable-debugging2.png "ustawień debugera platformy ASP.NET")

1. Użyj **pliku** > **Zapisz wybrane elementy** lub **Ctrl**+**S** umożliwia zapisanie wszelkich zmian.

1. Aby debugować aplikację, w projekcie, należy ustawić punkty przerwania na temat jakiegoś kodu. Na pasku narzędzi programu Visual Studio, upewnij się, konfiguracja została ustawiona na **debugowania**, a przeglądarka ma pojawia się w **usług IIS Express (\<nazwy przeglądarki >)** lub **lokalnych usług IIS (\< Nazwa przeglądarki >)** w polu emulatora.

1. Aby rozpocząć debugowanie, wybierz **usług IIS Express (\<nazwy przeglądarki >)** lub **lokalnych usług IIS (\<nazwy przeglądarki >)** na pasku narzędzi wybierz **Rozpocznij debugowanie**z **debugowania** menu lub naciśnij klawisz **F5**. Debuger zatrzymuje się w punktach przerwania. Jeśli debuger nie może identyfikować punkty przerwania, zobacz [Rozwiązywanie problemów dotyczących debugowania](#troubleshoot-debugging).

## <a name="debug-aspnet-core-apps"></a>Debugowanie aplikacji platformy ASP.NET Core

Usługi IIS Express jest ustawieniem domyślnym i jest wstępnie skonfigurowany. Jeśli debugujesz na lokalnym serwerze IIS, upewnij się, że spełniasz [wymagania dla debugowania lokalnego IIS](#iis).

1. Wybierz projekt platformy ASP.NET Core w programie Visual Studio **Eksploratora rozwiązań** i kliknij przycisk **właściwości** ikonę, naciśnij klawisz **Alt**+**Enter**, lub kliknij prawym przyciskiem myszy i wybierz pozycję **właściwości**.

1. Wybierz **debugowania** kartę.

1. W **właściwości** okienko, obok **profilu**,
   - W przypadku usług IIS Express, wybrać **usług IIS Express** z listy rozwijanej.
   - Dla lokalnych usług IIS, wybierz nazwę aplikacji z listy rozwijanej lub **New**, Utwórz nową nazwę profilu, a wybierz **OK**.

1. Obok pozycji **Uruchom**, wybierz opcję **usług IIS Express** lub **IIS** z listy rozwijanej.

1. Upewnij się, że **uruchamiania przeglądarki** jest zaznaczone.

1. W obszarze **zmienne środowiskowe**, upewnij się, że **ASPNETCORE_ENVIRONMENT** występuje z wartością **rozwoju**. Jeśli nie, wybierz **Dodaj** i dodaj go.

   ![Ustawienia debugera platformy ASP.NET Core](../debugger/media/dbg-aspnet-enable-debugging3.png "ustawienia debugera platformy ASP.NET Core")

1. Użyj **pliku** > **Zapisz wybrane elementy** lub **Ctrl**+**S** umożliwia zapisanie wszelkich zmian.

1. Aby debugować aplikację, w projekcie, należy ustawić punkty przerwania na temat jakiegoś kodu. Na pasku narzędzi programu Visual Studio, upewnij się, konfiguracja została ustawiona na **debugowania**oraz **usług IIS Express**, lub Nowa nazwa profilu usług IIS, pojawią się w polu emulatora.

1. Aby rozpocząć debugowanie, wybierz **usług IIS Express** lub  **\<nazwa profilu usługi IIS >** na pasku narzędzi wybierz **Rozpocznij debugowanie** z **debugowania** menu lub naciśnij klawisz **F5**. Debuger zatrzymuje się w punktach przerwania. Jeśli debuger nie może identyfikować punkty przerwania, zobacz [Rozwiązywanie problemów dotyczących debugowania](#troubleshoot-debugging).

## <a name="troubleshoot-debugging"></a>Rozwiązywanie problemów z debugowania

Jeśli lokalne debugowanie usług IIS nie postępu dla punktu przerwania, wykonaj następujące kroki, aby rozwiązać.

1. Uruchamiają aplikację sieci web za pomocą programu IIS i upewnij się, że działa on prawidłowo. Pozostaw jest uruchomiona aplikacja sieci web.

2. W programie Visual Studio, wybierz **debugowania > Dołącz do procesu** lub naciśnij **Ctrl**+**Alt**+**P**, i połączenia z procesem ASP.NET lub ASP.NET Core (zazwyczaj **w3wp.exe** lub **dotnet.exe**). Aby uzyskać więcej informacji, zobacz [dołączyć do procesu](attach-to-running-processes-with-the-visual-studio-debugger.md) i [sposoby znajdowania nazwy procesu ASP.NET](how-to-find-the-name-of-the-aspnet-process.md).

Jeśli umiesz nawiązywać połączenia i trafiony punkt przerwania przy użyciu **dołączyć do procesu**, ale nie przy użyciu **debugowania** > **Rozpocznij debugowanie** lub **F5**, to ustawienie jest prawdopodobnie nieprawidłowy we właściwościach projektu. Jeśli używasz pliku HOSTS, upewnij się, że również jest poprawnie skonfigurowany.

## <a name="configure-debugging-in-the-webconfig-file"></a>Konfigurowanie debugowania w pliku web.config

Projekty ASP.NET mają *web.config* pliki domyślne, które zawierają zarówno konfiguracji, a następnie uruchom informacje o aplikacji, w tym ustawienia debugowania. *Web.config* pliki muszą być prawidłowo skonfigurowane do debugowania. **Właściwości** ustawienia w poprzedniej sekcji aktualizacji *web.config* pliki, ale można również skonfigurować je ręcznie.

> [!NOTE]
> Nie masz początkowo projektów ASP.NET Core *web.config* plików, ale użyj *appsettings.json* i *launchSettings.json* pliki konfiguracji aplikacji, a następnie uruchom informacje. Wdrażanie aplikacji tworzy *web.config* plik lub pliki w projekcie, ale nie zwykle zawierają one informacje o debugowaniu.

> [!TIP]
> Proces wdrażania może aktualizować *web.config* ustawień, dlatego przed próbą debugowania, upewnij się, *web.config* jest skonfigurowany do debugowania.

**Aby ręcznie skonfigurować *web.config* plik na potrzeby debugowania:**

1. W programie Visual Studio, otwórz projekt ASP.NET *web.config* pliku.

2. *Plik Web.config* jest plikiem XML, więc zawiera zagnieżdżone sekcje oznaczone według tagów. Znajdź `configuration/system.web/compilation` sekcji. (Jeśli `compilation` element nie istnieje, utwórz go.)

3. Upewnij się, że `debug` atrybutu w `compilation` element jest ustawiony na wartość `true`. (Jeśli `compilation` nie zawiera elementu `debug` atrybutu, dodaj go i ustaw ją na `true`.)

   Jeśli używasz lokalnych usług IIS zamiast domyślnego serwera usług IIS Express, upewnij się, że `targetFramework` wartość atrybutu `compilation` pasującego elementu framework na serwerze usług IIS.

   `compilation` Elementu *web.config* plik powinien wyglądać podobnie jak w poniższym przykładzie:

   > [!NOTE]
   > W tym przykładzie jest częściowym *web.config* pliku. Są zazwyczaj dodatkowe sekcje XML `configuration` i `system.web` elementów, a `compilation` element może także zawierać inne atrybuty i elementy.

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

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] automatycznie wykrywa zmiany *web.config* plików i stosuje nowe ustawienia konfiguracji. Nie trzeba ponownie uruchomić komputer lub serwer IIS, aby zmiany zaczęły obowiązywać.

Witryny sieci Web mogą zawierać kilka wirtualne katalogi i podkatalogi, za pomocą *web.config* pliki w każdej z nich. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacje, dziedziczą ustawienia konfiguracji z *web.config* pliki na wyższym poziomie w ścieżce adresu URL. Hierarchiczna *web.config* ustawienia plików mają zastosowanie do wszystkich [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji pod nimi w hierarchii. Ustawienie różnych konfiguracji w *web.config* plik niżej w hierarchii zastępuje ustawienia w pliku wyższy.

Na przykład, jeśli określisz `debug="true"` w <em>www.microsoft.com/aaa/web.config</em>, dowolnej aplikacji w *aaa* folderze lub w jego podfolderze z *aaa* dziedziczy to ustawienie Jeśli jeden z tych aplikacji zastępuje ustawienie za pomocą własnego, z wyjątkiem *web.config* pliku.

## <a name="publish-in-debug-mode-using-the-file-system"></a>Publikowanie w trybie debugowania przy użyciu systemu plików

Istnieją różne sposoby publikować aplikacje dla usług IIS. Te kroki pokazują, jak utworzyć i wdrożyć debugowania profilu publikowania w systemie plików. Aby to zrobić, użytkownik musi działać program Visual Studio jako administrator.

> [!IMPORTANT]
> Jeśli zmienisz kodu lub ponownej kompilacji, należy powtórzyć te kroki, aby ponownie opublikować.

1. W programie Visual Studio, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj**.

3. Wybierz **usług IIS, FTP, etc** i kliknij przycisk **Publikuj**.

    ![Publikowanie w usługach IIS](media/dbg-aspnet-local-iis.png "publikowania w usługach IIS")

4. W **CustomProfile** okna dialogowego, aby uzyskać **metody publikowania**, wybierz **system plików**.

5. Aby uzyskać **lokalizacja docelowa**, wybierz opcję **Przeglądaj** (**...** ).

   - W technologii ASP.NET, wybierz **lokalne usługi IIS**, wybierz witrynę sieci Web została utworzona dla aplikacji, a następnie wybierz **Otwórz**.

     ![Publikowanie programu ASP.NET w usługach IIS](media/dbg-aspnet-local-iis1.png "publikowania programu ASP.NET w usługach IIS")

   - Dla platformy ASP.NET Core, wybierz **System plików**, wybierz folder dla aplikacji, a następnie wybierz **Otwórz**.

1. Wybierz opcję **Dalej**.

1. W obszarze **konfiguracji**, wybierz opcję **debugowania** z listy rozwijanej.

1. Wybierz pozycję **Zapisz**.

1. W **publikowania** okna dialogowego, upewnij się, że **CustomProfile** (lub nazwę utworzony właśnie profil) zostanie wyświetlony, i **LastUsedBuildConfiguration** jest ustawiona na  **Debugowanie**.

1. Wybierz **publikowania**.

    ![Publikowanie w usługach IIS](media/dbg-aspnet-local-iis-select-site.png "publikowania w usługach IIS")

> [!IMPORTANT]
> Tryb debugowania znacznie zmniejsza wydajność aplikacji. Aby uzyskać najlepszą wydajność, ustaw `debug="false"` w *web.config* i określić kompilację wydania, podczas wdrażania aplikacji produkcyjnych lub przeprowadzanie pomiarów wydajności.

## <a name="see-also"></a>Zobacz także
- [Debugowanie ASP.NET: wymagania systemowe](aspnet-debugging-system-requirements.md)
- [Instrukcje: Uruchamianie procesu roboczego w ramach konta użytkownika](how-to-run-the-worker-process-under-a-user-account.md)
- [Instrukcje: Znajdowanie nazwy procesu ASP.NET](how-to-find-the-name-of-the-aspnet-process.md)
- [Debugowanie wdrożonych aplikacji sieci web](debugging-deployed-web-applications.md)
- [Przewodnik: Debugowanie formularzy internetowych](walkthrough-debugging-a-web-form.md)
- [Instrukcje: Debugowanie wyjątków ASP.NET](how-to-debug-aspnet-exceptions.md)
- [Debugowanie aplikacji sieci web: Błędy i rozwiązywanie problemów](debugging-web-applications-errors-and-troubleshooting.md)
