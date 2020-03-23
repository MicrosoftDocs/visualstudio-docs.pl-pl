---
title: Rozwiązywanie problemów z emulatorem programu Visual Studio dla systemu Android | Dokumenty firmy Microsoft
ms.custom: ''
ms.prod: visual-studio-dev15
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: f3fb5df4-3aae-40e4-9450-bbe15b0c5af5
author: conceptdev
ms.author: crdun
manager: crdun
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 85a7748f25e284a7c746d5779b3d177a15e1d37b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77272071"
---
# <a name="troubleshoot-the-visual-studio-emulator-for-android"></a>Rozwiązywanie problemów z narzędziem Visual Studio Emulator for Android
Ten temat zawiera informacje ułatwiające rozwiązywanie problemów, które mogą wystąpić podczas korzystania z emulatora programu Visual Studio dla systemu Android.

> [!WARNING]
> Po zainstalowaniu emulatora program instalacyjny sprawdza wymagania wstępne dotyczące uruchamiania oprogramowania. Wyświetla ostrzeżenia, jeśli wymagania wstępne nie są obecne, ale nie wymaga ich do instalacji.

 Ten temat zawiera poniższe sekcje.

- [Przed rozpoczęciem](#BeforeYouStart)

- [Instalacji emulatora nie można zainstalować](#NoInstall)

- [Nie można połączyć się z miejscami docelowymi sieci w domenie lub sieci firmowej](#DomainNetwork)

- [Nie można połączyć się z miejscami docelowymi sieci, gdy ustawienia sieciowe wymagają ręcznej konfiguracji](#ManualNetworkConfig)

- [Emulator uruchamia się powoli, nie można uruchomić z powodu przeterminu lub wdrożenie aplikacji kończy się niepowodzeniem](#SlowStart)

- [Nie można uruchomić emulatora](#NoStart2)

- [Nie można uruchomić emulatora (pierwsze użycie)](#NoStart)

- [Uruchomienie komputera nie powiedzie się po zainstalowaniu emulatora](#NoBoot)

- [Visual Studio utknie próbuje wdrożyć aplikację do emulatora lub emulator nie jest wyświetlany jako miejsce docelowe debugowania w innych IDE](#ADB)

- [Emulator zawiesza się, ponieważ nie można skonfigurować portu UDP](#XamarinPlayer)

- [Nie można dołączyć debugera do projektu platformy Xamarin](#Skylake)

- [Emulator nie uruchamia aplikacji korzystającej z usług Google Play](#GooglePlay)

- [Przeciąganie i upuszczanie pliku, pliku APK lub miganego pliku zip nie działa](#DragAndDrop)

- [Rozdzielczość zrzutu ekranu jest niepoprawna](#Resolution)

- [Emulator nie może renderować zawartości OpenGL](#OpenGL)

- [Emulator nie reaguje na gesty wielodotykowe](#Multitouch)

- [Zasoby pomocnicze](#Support)

## <a name="before-you-start"></a><a name="BeforeYouStart"></a>Przed rozpoczęciem
 Przed rozpoczęciem rozwiązywania problemów może być przydatne przejrzenie następujących tematów:

- [Wymagania systemowe dla emulatora programu Visual Studio dla systemu Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)

## <a name="emulator-fails-to-install"></a><a name="NoInstall"></a>Instalacji emulatora nie można zainstalować
 Jeśli nie masz zainstalowanego funkcji Hyper-V, podczas próby zainstalowania emulatora zostanie wyświetlony następujący komunikat. Musisz mieć komputer, który obsługuje funkcję HyperV i musi być włączony.

 ![Android&#95;Emu&#95;zainstalować&#95;problem](../cross-platform/media/android_emu_install_issue.png "Android_Emu_Install_Issue")

> [!NOTE]
> Ten komunikat dotyczy zarówno visual studio emulator dla systemu Android i emulatora systemu Windows Phone. System Windows 8.1 i Windows 10 obsługują emulator.

 Jeśli widzisz ten komunikat, sprawdź [wymagania systemowe dla visual studio emulator dla systemu Android,](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md) aby zobaczyć, czy można uruchomić emulator.

## <a name="cannot-connect-to-network-destinations-on-a-domain-or-corporate-network"></a><a name="DomainNetwork"></a>Nie można połączyć się z miejscami docelowymi sieci w domenie lub sieci firmowej
 Emulator programu Visual Studio dla systemu Android pojawia się w sieci jako oddzielne urządzenie z własnym adresem IP. Nie jest przyłączony do domeny systemu Windows i nie udostępnia poświadczeń domeny ani grupy roboczej z komputerem-hostem.

 Jeśli sieć wymaga autoryzacji domeny lub grupy roboczej dla podstawowej łączności sieciowej i internetowej, skontaktuj się z administratorem IT, aby uzyskać wyjątek. Ten wyjątek umożliwia komputerowi dewelopera służyć jako komputer graniczny i akceptować połączenia z urządzeń sieciowych nieprzyłączonych do domeny, takich jak emulator.

 Visual Studio Emulator dla systemu Android używa również własnego zestawu adresów MAC. Jeśli nie możesz uzyskać dostępu do zasobów sieciowych lub internetowych z emulatora, skontaktuj się z administratorem IT, aby upewnić się, że adresy MAC emulatora zostały autoryzowane w sieci.

#### <a name="to-view-the-emulators-mac-addresses"></a>Aby wyświetlić adresy MAC emulatora

1. Uruchom emulator.

2. Na pasku narzędzi emulatora kliknij przycisk szewronu (>>), aby otworzyć okno Dodatkowe narzędzia.

3. W oknie Dodatkowe narzędzia kliknij kartę Sieć.

4. Na stronie Sieć znajdź wpisy adresu fizycznego.

## <a name="cannot-connect-to-network-destinations-when-network-settings-require-manual-configuration"></a><a name="ManualNetworkConfig"></a>Nie można połączyć się z miejscami docelowymi sieci, gdy ustawienia sieciowe wymagają ręcznej konfiguracji
 Aby połączyć się z miejscami docelowymi sieci z emulatora, sieć musi spełniać następujące wymagania:

- Dhcp. Emulator wymaga usługi DHCP, ponieważ konfiguruje się jako oddzielne urządzenie w sieci z własnym adresem IP.

- Automatycznie skonfigurowane ustawienia DNS i bramy. Nie można ręcznie skonfigurować ustawień DNS i bramy dla emulatora.

  Jeśli sieć wymaga ręcznie skonfigurowanych ustawień, skontaktuj się z administratorem IT, aby ustalić, w jaki sposób można włączyć łączność sieciową dla emulatora.

## <a name="emulator-starts-slowly-fails-to-start-due-to-a-timeout-or-app-deployment-fails"></a><a name="SlowStart"></a>Emulator uruchamia się powoli, nie można uruchomić z powodu przeterminu lub wdrożenie aplikacji kończy się niepowodzeniem
 Pod pewnymi warunkami emulator trwa kilka minut, aby uruchomić lub nie można uruchomić z powodu limitu czasu. Gdy emulator nie uruchamia się, zostanie `App deployment failed. Please try again`wyświetlony następujący komunikat: . Następujące warunki mogą spowodować ten błąd.

- Uruchamianie emulatora programu Visual Studio dla systemu Android z rozruchowego dysku VHD. Ta konfiguracja nie jest obsługiwana.

- Uszkodzony dysk twardy. Rozważ uruchomienie programu chkdsk.

- Dysk twardy, który musi zostać zdefragmentowany. Rozważ defragmentację dysku.

- Dysk twardy, który jest prawie pełny. Sprawdź miejsce dostępne na dysku.

- Za mało pamięci jest dostępna z powodu innych uruchomionych aplikacji. Zmniejsz liczbę aplikacji, które zużywają pamięć lub zwiększ ilość pamięci.

- Ogólnie rzecz biorąc, każdy czynnik, który przyczynia się do niskiej wydajności w systemie. Rozpocznij rozwiązywanie problemów ze składnikiem, który ma najniższy wynik cząstkowy w indeksie wydajności systemu Windows, który można znaleźć na stronie Informacje o wydajności i narzędzia w Panelu sterowania.

## <a name="emulator-fails-to-start"></a><a name="NoStart2"></a>Nie można uruchomić emulatora
 Jeśli emulator działał wcześniej, ale nie działa teraz, przejdź przez następujące zadania. Jeśli używasz emulatora po raz pierwszy, zobacz [Emulator nie można uruchomić (pierwsze użycie)](#NoStart) przed wypróbowaniem tych kroków.

- Usuń wszystkie inne wystąpienia funkcji Hyper-V emulatora.

    1. Zamknij program Visual Studio.

    2. Otwórz Menedżera funkcji Hyper-V i zatrzymaj wszystkie wystąpienia funkcji Hyper-V emulatora (maszyn wirtualnych), które są już uruchomione i prawdopodobnie w stanie uszkodzonym.

    3. W Menedżerze funkcji Hyper-V usuń wszystkie inne maszyny wirtualne emulatora.

    4. Uruchom ponownie komputer.

- Upewnij się, że masz co najmniej 4 GB pamięci systemowej i że nie jest zużywana przez inne programy i procesy intensywnie korzystające z zasobów (na przykład spróbuj zamknąć wszystkie okna przeglądarki).

- W Menedżerze funkcji Hyper-V otwórz Menedżera przełączników wirtualnych i sprawdź, czy masz dwa przełączniki sieciowe; sprawdzić, czy pierwszy z nich jest przełącznikiem wewnętrznym, a drugi jest zewnętrzny.

     ![Android&#95;Emu&#95;V przełącznik&#95;&#95;Man](../cross-platform/media/android_emu_v_switch_man.png "Android_Emu_V_Switch_Man")

     Jeśli konfiguracja jest nieprawidłowa i używasz systemu Windows 10, możesz spróbować [ponownie zainstalować urządzenia sieciowe za pomocą polecenia netcfg -d](https://support.microsoft.com/help/10741/windows-fix-network-connection-issues) (sekcja 6).

- Jeśli te kroki nie rozwiążą problemu, zobacz [Emulator nie można uruchomić (pierwsze użycie)](#NoStart) informacji na temat oprogramowania innych firm, które mogą zakłócać emulator.

## <a name="emulator-fails-to-start-first-use"></a><a name="NoStart"></a>Nie można uruchomić emulatora (pierwsze użycie)
 Jeśli emulator nie uruchamia się, przejdź przez następujące zadania, aby zidentyfikować i rozwiązać problem.

- Upewnij się, że spełnione są minimalne wymagania sprzętowe i że ustawienia systemu BIOS są poprawne.

   Emulator i Windows 8 Hyper-V wymagają 64-bitowego procesora z tłumaczeniem adresu drugiego poziomu (SLAT). Dla Intela, zasadniczo potrzebujesz procesora Core i3, i5 lub i7 (lub jednego z wielu Xeonów). Lista układów AMD jest dostępna [tutaj](https://www.amd.com/en/support).

  1. Upewnij się, że komputer spełnia [wymagania systemowe](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md).

  2. Sprawdź, czy [narzędzie SLAT](https://slatstatuscheck.codeplex.com/) zgłasza, że komputer jest zdolny do sieci SLAT.

  3. W ustawieniach systemu BIOS komputera upewnij się, że cała technologia wirtualizacji jest włączona. Dokładne opisy systemu BIOS mogą się różnić w zależności od producenta sprzętu. Ogólnie rzecz biorąc, włącz funkcje związane z:

     - SLAT (tłumaczenie adresów drugiego poziomu)

     - EPT (rozszerzone tabele stron) (Intel)

     - NPT (zagnieżdżone tabele stron) (AMD)

     - RVI (szybkie indeksowanie wirtualizacji) (AMD)

     - VMX (skrót od Intel wskazujący obsługę wirtualizacji wspomaganej sprzętowo)

     - SVM (skrót OD AMD wskazujący obsługę wirtualizacji wspomaganej sprzętowo)

     - XD (Execute Disable) (Intel); musi to być włączone

     - NX (bez wykonania) (AMD); musi być włączona.

  4. Jeśli w systemie BIOS znajdują się następujące opcje, wyłącz je.

     - Wyłącz intel VT-d

     - Wyłącz zaufane wykonanie

       Aby uzyskać więcej informacji, zobacz ten artykuł: Technet: Hyper-V: Jak naprawić błędy SYSTEMU BIOS włączanie funkcji Hyper-V

  5. Upewnij się, że masz co najmniej 4 GB pamięci systemowej i że nie jest zużywana przez inne programy i procesy intensywnie korzystające z zasobów.

  6. Upewnij się, że korzystasz z systemu Windows 8 Professional lub lepszego (system Windows Server 2008 nie jest obsługiwany). System Windows Server 2012 jest obsługiwany, ale należy włączyć środowisko pulpitu.

     Podgląd zdarzeń można sprawdzić, czy nie występują błędy funkcji Hypervisor. Aby to zrobić, otwórz Podgląd zdarzeń **(Przycisk startowy**+**R**, a następnie `eventvwr`wpisz ), a następnie wybierz pozycję **Dzienniki systemu Windows**, **System**. Następnie przefiltruj dziennik według źródła zdarzeń, ustawiając źródło na **Hyper-V-Hypervisor**. Sprawdź, czy nie ma błędów, aby zidentyfikować główną przyczynę.

     Jeśli procesor spełnia minimalne wymagania, ale funkcja hypervisor nadal zawodzi, należy rozważyć ustalenie, czy dla komputera jest dostępne uaktualnienie systemu BIOS. Jeśli istnieje, i zdecydujesz się uaktualnić, należy przestrzegać wszystkich środków ostrożności od producenta podczas uaktualniania SYSTEMU BIOS (na przykład upewniając się, że aktualizacja oprogramowania układowego BIOS nie jest przerywana przez utratę zasilania, które mogą trwale uszkodzić BIOS).

- Upewnij się, że masz co najmniej 4 GB pamięci systemowej i że nie jest zużywana przez inne programy i procesy intensywnie korzystające z zasobów.

- Usuń/Wyłącz sterowniki lub oprogramowanie innych firm, które mogą zakłócać działanie sieci wirtualnej.

   Istnieją pewne znane problemy z niektórymi produktami innych firm zainstalowanymi w systemie Windows 8, takimi jak sterowniki/protokoły sieciowe, które nie są w pełni zgodne ze stosem sieciowym funkcji Hyper-V.

   Ogólnie rzecz biorąc, to do twórców tych produktów, aby zaktualizować swoje oprogramowanie, aby być zgodne z Windows 8 i Hyper-V.

   Następujące produkty mogą wymagać uaktualnienia pod kątem zgodności z systemem Windows 8: VirtualBox, Virtual PC 7, VMWare, niektórzy klienci sieci VPN, zapory oprogramowania, niektóre wersje klientów sieci VPN Cisco i inne systemy wirtualizacji. Współpracuj z twórcą wątpliwego oprogramowania do wirtualizacji, aby zachęcić go do uaktualnienia oprogramowania, aby było zgodne z systemami Windows 8 i Hyper-V.

   W *ramach obejścia*można wyłączyć wszystkie sterowniki i aplikacje innych firm, które mogą zakłócać działanie sieci wirtualnej używanej przez emulator do komunikowania się z programem Visual Studio. Aplikacje te mogą obejmować:

  - Aplikacje antywirusowe (które podłączają się do stosu sieciowego)

  - Narzędzia do monitorowania sieci

  - Narzędzia do rejestrowania sieci

  - Inne oprogramowanie do monitorowania systemu

    Innym możliwym rozwiązaniem, które nie można odinstalować danego produktu (i poprosić dewelopera produktu o wydanie zaktualizowanej wersji), jest wykonanie następujących kroków.

  1. Uruchom Menedżera połączeń sieciowych (na ekranie startowym wpisz `View Network Connections` i wybierz tę opcję, aby wyświetlić połączenia sieciowe).

  2. W przypadku karty vEthernet (Internal Ethernet Port Windows Phone Emulator Internal Switch) wybierz polecenie **Właściwości** z menu kontekstowego.

      ![Wirtualna karta używana przez Hyper&#45;V](../cross-platform/media/android_emu_virtual_adapter.png "Android_Emu_Virtual_Adapter")

      Właściwości karty są wyświetlane w tym miejscu.

      ![Właściwości karty wirtualnej](../cross-platform/media/android_emu_virtual_adapter_properties.png "Android_Emu_Virtual_Adapter_Properties")

  3. W przypadku tej karty jedynymi **elementami,** które powinny być wybrane w obszarze To połączenie, następujące elementy powinny być następujące:

     - Klient sieci Microsoft Networks

     - Harmonogram pakietów QoS

     - Udostępnianie plików i drukarek w sieciach Microsoft Networks

     - Sterownik protokołu MICROSOFT LLDP

     - Sterownik we/wy mapowania mapowania mapowania warstwy łącza

     - Obiekt odpowiadający odnajdowania topologii warstwy łącza

     - Protokół internetowy w wersji 6 (TCP/IPv6)

     - Protokół internetowy w wersji 4 (TCP/IPv4)

  4. Usuń zaznaczenie innych elementów.

     Wadą korzystania z tej techniki jest to, że za każdym razem, gdy nowy produkt innej firmy instaluje nieobsługiwał sterowniki lub za każdym razem, gdy emulator jest zainstalowany, te kroki będą musiały zostać powtórzone.

     Po odinstalowaniu produktów innych firm może być konieczne przywrócenie przełącznika wewnętrznego emulatora systemu Windows Phone. W tym celu:

  - Otwórz hyper V i przejdź do Menedżera przełączników wirtualnych. Utwórz przełącznik wirtualny o nazwie "Windows Phone Emulator Internal Switch" i ustaw jego typ połączenia na **Sieć Wewnętrzna**.

     ![Wirtualny menedżer przełączników](../cross-platform/media/android_emu_virtual_switch_manager.png "Android_Emu_Virtual_Switch_Manager")

    Teraz uruchom emulator. To powinno działać.

## <a name="computer-fails-to-boot-after-installing-the-emulator"></a><a name="NoBoot"></a>Uruchomienie komputera nie powiedzie się po zainstalowaniu emulatora
 Ten problem może wystąpić, gdy spełnione są następujące warunki:

- Komputer jest na komputerze z płytą główną Gigabyte.

- USB3 jest włączony na płycie głównej.

  Aby rozwiązać ten problem, wyłącz USB3 w ustawieniach BIOS płyty głównej i uruchom ponownie komputer. Następnie sprawdź, czy Gigabyte wydał aktualizację biosu płyty głównej.

  Aby uzyskać więcej informacji, zobacz następujący artykuł bazy wiedzy Knowledge Base: [Awaria rozruchu po zainstalowaniu roli funkcji funkcji Funkcji Hyper-V w systemach Gigabyte](https://support.microsoft.com/en-us/kb/2693144).

## <a name="visual-studio-gets-stuck-trying-to-deploy-the-app-to-the-emulator-or-the-emulator-does-not-appear-as-a-debug-target-in-other-ides"></a><a name="ADB"></a>Visual Studio utknie próbuje wdrożyć aplikację do emulatora lub emulator nie jest wyświetlany jako miejsce docelowe debugowania w innych IDE
 Jeśli emulator jest uruchomiony, ale nie wydaje się być podłączony do bazy danych ADB (Most debugowy systemu Android) lub nie pojawia się w narzędziach systemu Android, które korzystają z ADB (na przykład Android Studio lub Eclipse), może być konieczne dostosowanie, gdzie emulator szuka ADB. Emulator używa klucza rejestru do identyfikowania lokalizacji podstawowej zestawu SDK systemu Android i wyszukuje plik \platform-tools\adb.exe w tym katalogu. Aby zmodyfikować ścieżkę SDK systemu Android używaną przez emulator:

- Otwórz Edytor rejestru, wybierając **polecenie Uruchom** z menu `regedit` kontekstowego przycisków startowych, wpisując w oknie dialogowym i wybierając przycisk **OK**.

- Przejdź do *HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Android SDK Tools* w drzewie folderów po lewej stronie.

- Zmodyfikuj zmienną rejestru **ścieżki,** aby dopasować ścieżkę do sdk systemu Android.

  Uruchom ponownie emulator i powinieneś teraz być w stanie zobaczyć emulator podłączony do bazy danych ADB i skojarzonych narzędzi systemu Android.

## <a name="emulator-hangs-because-it-couldnt-set-up-the-udp-port"></a><a name="XamarinPlayer"></a>Emulator zawiesza się, ponieważ nie można skonfigurować portu UDP
 Ten problem może wystąpić z powodu niezgodności z programem Xamarin Player. Jeśli emulator wydaje się zawiesić lub jeśli zostanie wyświetlony ten komunikat o błędzie, "Emulator nie może połączyć się z systemem operacyjnym urządzenia: Nie można skonfigurować portu UDP.  Niektóre funkcje mogą być wyłączone", może występować ten problem. Podejmij następujące kroki.

1. Odinstaluj odtwarzacz Xamarin.

2. Sprawdź, czy pole wirtualne zostało usunięte (Xamarin Player działa na górze wirtualnego pola).

3. Przejdź do menedżera urządzeń, wybierz opcję pokazywania ukrytych urządzeń, a następnie usuń wszystko z wyjątkiem fizycznych kart sieciowych.

4. Po usunięciu niefizowych kart sieciowych można spróbować odinstalować/ponownie zainstalować funkcja Hyper-V.

## <a name="cannot-attach-debugger-to-a-xamarin-project"></a><a name="Skylake"></a>Nie można dołączyć debugera do projektu platformy Xamarin
 Jeśli używasz systemu Windows 10 z procesorami Intel Skylake, aplikacje platformy Xamarin może nie działać w emulatorze lub debuger programu Visual Studio może nie dołączyć do nich. Jest to spowodowane problemem z procesorami Hyper-V i Skylake. Aby obejść następujące czynności, należy wykonać następujące czynności.

1. Otwórz Menedżera funkcji Hyper-V i wybierz maszynę wirtualną dla profilu emulatora, z których korzystasz.

2. Wybierz **pozycję Usuń zapisany stan** (prawy dolny r.).

3. Wybierz **ustawienia...**

4. Rozwiń węzeł procesora i wybierz pozycję **Zgodność**.

5. Włącz **migrację na komputer fizyczny z inną wersją procesora**.

6. Uruchom ponownie usługę (w obszarze **Akcje)** i spróbuj ponownie.

## <a name="emulator-fails-to-run-app-that-uses-google-play-services"></a><a name="GooglePlay"></a>Emulator nie uruchamia aplikacji korzystającej z usług Google Play
 Emulator nie jest dostarczany z bibliotekami usług Google Play. Jednak emulator obsługuje instalację typu "przeciągnij i upuść" plików zip flashable.

## <a name="drag-and-drop-of-a-file-apk-or-flashable-zip-file-does-not-work"></a><a name="DragAndDrop"></a>Przeciąganie i upuszczanie pliku, pliku APK lub miganego pliku zip nie działa
 Emulator używa programu ADB.exe w celu ułatwienia transferu plików podczas przeciągania i upuszczania pliku na ekranie. Jeśli podczas próby przeciągania i upuszczania pliku wystąpi błąd, prawdopodobnie oznacza to, że emulator nie jest połączony z programem ADB.exe. Aby rozwiązać, wykonaj kroki w [programie Visual Studio utknie próbuje wdrożyć aplikację do emulatora lub emulator nie jest wyświetlany jako cel debugowania w innych identyfikatorach.](#ADB)

## <a name="resolution-of-screenshot-is-incorrect"></a><a name="Resolution"></a>Rozdzielczość zrzutu ekranu jest niepoprawna
 Jeśli zrobisz zrzut ekranu za pomocą karty Zrzut ekranu w oknie **Narzędzia dodatkowe,** a wynikowy obraz ma nieoczekiwany rozmiar, może być konieczne dostosowanie poziomu powiększenia ekranu przed **wybraniem opcji Przechwytywanie**. Emulator wykonuje zrzuty ekranu w rozdzielczości ekranu na monitorze komputera hosta.

## <a name="emulator-fails-to-render-opengl-content"></a><a name="OpenGL"></a>Emulator nie może renderować zawartości OpenGL
 Emulator renderuje zawartość OpenGL przy użyciu procesora graficznego komputera hosta i używa projektu ANGLE do konwersji tych wywołań do i z directx. Jeśli aplikacja renderuje poprawnie na urządzeniu, ale niepoprawnie na emulatorze, jest prawdopodobne, że urządzenie jest łagodzenie niepoprawne wywołanie OpenGL (na przykład przy użyciu zmiennych modułu cieniującego, które nie są zgodne).

## <a name="emulator-does-not-respond-to-multi-touch-gestures"></a><a name="Multitouch"></a>Emulator nie reaguje na gesty wielodotykowe
 W niektórych przypadkach emulator zostanie uruchomiony i nie będzie reagował na multi-touch za pośrednictwem bezpośredniej interakcji z wyświetlaczem dotykowym lub za pomocą narzędzia Multi-Touch na pasku narzędzi emulatora. W takim przypadku wybierz przycisk **Obróć** na pasku narzędzi emulatora i spróbuj ponownie użyć funkcji multi-touch. Jeśli problem będzie się powtarzał, odczyt [emulatora nie może renderować problemu z zawartością OpenGL.](#OpenGL)

## <a name="support-resources"></a><a name="Support"></a>Zasoby pomocnicze
 Jeśli komputer-host spełnia wymagania systemowe i wystąpi problem, który nie został omówiony w tym przewodniku rozwiązywania problemów:

- Zadaj pytanie na StackOverflow przy użyciu [android-emulator](https://stackoverflow.com/questions/tagged/android-emulator) i visual-studio tagów.

- Zgłoś problem przy użyciu narzędzia Wyślij uśmiech w programie Visual Studio lub w Menedżerze emulatora.
