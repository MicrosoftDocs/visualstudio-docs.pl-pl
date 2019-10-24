---
title: Rozwiązywanie problemów z emulatorem programu Visual Studio dla systemu Android | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: f3fb5df4-3aae-40e4-9450-bbe15b0c5af5
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- multiple
ms.openlocfilehash: 56978bfee49bc3a38e900eb41004307ef40d0403
ms.sourcegitcommit: 57bc1c3887838d707c13feff72a677b3bad3be4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72777810"
---
# <a name="troubleshoot-the-visual-studio-emulator-for-android"></a>Rozwiązywanie problemów z narzędziem Visual Studio Emulator for Android
Ten temat zawiera informacje ułatwiające rozwiązywanie problemów, które mogą wystąpić podczas korzystania z emulatora programu Visual Studio dla systemu Android.

> [!WARNING]
> Po zainstalowaniu emulatora program instalacyjny sprawdza wymagania wstępne dotyczące uruchamiania oprogramowania. Wyświetla ostrzeżenia, jeśli wymagania wstępne nie są obecne, ale nie wymagają ich instalacji.

 Ten temat zawiera następujące sekcje.

- [Przed rozpoczęciem](#BeforeYouStart)

- [Nie można zainstalować emulatora](#NoInstall)

- [Nie można nawiązać połączenia z lokalizacjami docelowymi sieci w domenie lub sieci firmowej](#DomainNetwork)

- [Nie można nawiązać połączenia z sieciami docelowymi, gdy ustawienia sieciowe wymagają ręcznej konfiguracji](#ManualNetworkConfig)

- [Emulator zaczyna działać powoli, nie można uruchomić z powodu przekroczenia limitu czasu lub wdrożenie aplikacji nie powiodło się](#SlowStart)

- [Nie można uruchomić emulatora](#NoStart2)

- [Nie można uruchomić emulatora (pierwsze użycie)](#NoStart)

- [Rozruch komputera po zainstalowaniu emulatora nie powiodło się](#NoBoot)

- [Program Visual Studio jest niezablokowany podczas próby wdrożenia aplikacji do emulatora lub emulator nie jest wyświetlany jako element docelowy debugowania w innych środowisk IDE](#ADB)

- [Emulator zawiesza się, ponieważ nie mógł skonfigurować portu UDP](#XamarinPlayer)

- [Nie można dołączyć debugera do projektu Xamarin](#Skylake)

- [Emulator nie może uruchomić aplikacji korzystającej z Usługi Google Play](#GooglePlay)

- [Przeciąganie i upuszczanie pliku, APK lub Flash plik zip nie działa](#DragAndDrop)

- [Rozdzielczość zrzutu ekranu jest niepoprawna](#Resolution)

- [Nie można renderować zawartości OpenGL przez emulator](#OpenGL)

- [Emulator nie reaguje na Gesty wielodotykowe](#Multitouch)

- [Zasoby pomocy technicznej](#Support)

## <a name="BeforeYouStart"></a>Przed rozpoczęciem
 Przed rozpoczęciem rozwiązywania problemów warto zapoznać się z następującymi tematami:

- [Wymagania systemowe dla emulatora programu Visual Studio dla systemu Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)

## <a name="NoInstall"></a>Nie można zainstalować emulatora
 Jeśli nie zainstalowano funkcji Hyper-V, podczas próby zainstalowania emulatora zostanie wyświetlony następujący komunikat. Musisz mieć maszynę obsługującą funkcję HyperV, która musi być włączona.

 ![Problem&#95;z&#95;instalacją&#95;systemu Android UGW](../cross-platform/media/android_emu_install_issue.png "Android_Emu_Install_Issue")

> [!NOTE]
> Ten komunikat ma zastosowanie do emulatora programu Visual Studio dla systemu Android i emulatora Windows Phone. Windows 8.1 i Windows 10 obsługują emulator.

 Jeśli zobaczysz ten komunikat, sprawdź [wymagania systemowe emulatora programu Visual Studio dla systemu Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md) , aby sprawdzić, czy można uruchomić emulator.

## <a name="DomainNetwork"></a>Nie można nawiązać połączenia z lokalizacjami docelowymi sieci w domenie lub sieci firmowej
 Emulator programu Visual Studio dla systemu Android pojawia się w sieci jako oddzielne urządzenie z własnym adresem IP. Nie jest on przyłączony do domeny systemu Windows i nie udostępnia poświadczeń domeny lub grupy roboczej na komputerze-hoście.

 Jeśli sieć wymaga autoryzacji domeny lub grupy roboczej dla podstawowej sieci i łączności z Internetem, skontaktuj się z administratorem IT, aby uzyskać wyjątek. Ten wyjątek umożliwia komputerowi Deweloperskiemu pełnienie jako maszynę graniczną i akceptowanie połączeń z urządzeń sieciowych, które nie są przyłączone do domeny, takich jak emulator.

 Emulator programu Visual Studio dla systemu Android używa również własnego zestawu adresów MAC. Jeśli nie możesz uzyskać dostępu do zasobów sieci lub Internetu z emulatora, skontaktuj się z administratorem IT, aby upewnić się, że adresy MAC emulatora zostały autoryzowane w sieci.

#### <a name="to-view-the-emulators-mac-addresses"></a>Aby wyświetlić adresy MAC emulatora

1. Uruchom emulator.

2. Na pasku narzędzi emulatora kliknij przycisk Pagon (> >), aby otworzyć okno dodatkowe narzędzia.

3. W oknie dodatkowe narzędzia kliknij kartę Sieć.

4. Na stronie sieć Znajdź pozycje adresów fizycznych.

## <a name="ManualNetworkConfig"></a>Nie można nawiązać połączenia z sieciami docelowymi, gdy ustawienia sieciowe wymagają ręcznej konfiguracji
 Aby nawiązać połączenie z sieciami docelowymi z emulatora, Sieć musi spełniać następujące wymagania:

- Protokoł. Emulator wymaga protokołu DHCP, ponieważ konfiguruje go jako oddzielne urządzenie w sieci przy użyciu własnego adresu IP.

- Automatycznie skonfigurowane ustawienia DNS i bramy. Nie można skonfigurować ustawień DNS i bramy ręcznie dla emulatora.

  Jeśli sieć wymaga ręcznie skonfigurowanych ustawień, należy skontaktować się z administratorem IT, aby określić, w jaki sposób można włączyć łączność sieciową dla emulatora.

## <a name="SlowStart"></a>Emulator zaczyna działać powoli, nie można uruchomić z powodu przekroczenia limitu czasu lub wdrożenie aplikacji nie powiodło się
 W pewnych warunkach emulator może rozpocząć pracę lub nie może zostać uruchomiony z powodu przekroczenia limitu czasu. Kiedy emulator nie zostanie uruchomiony, zobaczysz następujący komunikat: `App deployment failed. Please try again`. Przyczyną tego błędu mogą być poniższe warunki.

- Uruchamianie emulatora programu Visual Studio dla systemu Android z rozruchowego dysku VHD. Ta konfiguracja nie jest obsługiwana.

- Uszkodzony dysk twardy. Rozważ uruchomienie programu Chkdsk.

- Dysk twardy, który musi być pofragmentowany. Rozważ defragmentację dysku.

- Dysk twardy, który jest prawie pełny. Sprawdź miejsce dostępne na dysku.

- Za mało dostępnej pamięci z powodu innych uruchomionych aplikacji. Zmniejsz liczbę aplikacji zużywających pamięć lub Zwiększ ilość pamięci.

- Ogólnie rzecz biorąc, każdy czynnik, który ma wpływ na niską wydajność w systemie. Rozpocznij Rozwiązywanie problemów ze składnikiem, który ma najniższy wynik podkreślenia w indeksie wydajności systemu Windows, który można znaleźć na stronie informacje o wydajności i narzędzia w panelu sterowania.

## <a name="NoStart2"></a>Nie można uruchomić emulatora
 Jeśli emulator działał wcześniej, ale nie działa teraz, wykonaj poniższe zadania. Jeśli używasz emulatora po raz pierwszy, zobacz [emulator nie można uruchomić (pierwsze użycie)](#NoStart) przed wykonaniem tych kroków.

- Usuń wszystkie inne wystąpienia funkcji Hyper-V emulatora.

    1. Zamknij program Visual Studio.

    2. Otwórz Menedżera funkcji Hyper-V i Zatrzymaj wszystkie wystąpienia funkcji Hyper-V emulatora (Virtual Machines), które są już uruchomione i prawdopodobnie w stanie uszkodzenia.

    3. W Menedżerze funkcji Hyper-V Usuń wszystkie inne maszyny wirtualne emulatora.

    4. Uruchom ponownie komputer.

- Upewnij się, że masz co najmniej 4 GB pamięci systemowej i że nie są używane przez inne programy i procesy czasochłonne w ramach zasobów (na przykład spróbuj zamknąć wszystkie okna przeglądarki).

- W Menedżerze funkcji Hyper-V Otwórz Menedżera przełącznika wirtualnego i sprawdź, czy masz dwa przełączniki sieciowe; Upewnij się, że pierwszy z nich jest przełącznikiem wewnętrznym, a drugi jest zewnętrzny.

     ![Android&#95;—&#95;&#95;przełączanie z&#95;przełącznika euro](../cross-platform/media/android_emu_v_switch_man.png "Android_Emu_V_Switch_Man")

     Jeśli instalacja jest nieprawidłowa i używasz systemu Windows 10, możesz spróbować [ponownie zainstalować urządzenia sieciowe przy użyciu polecenia netcfg-d](https://support.microsoft.com/help/10741/windows-fix-network-connection-issues) (sekcja 6).

- Jeśli te kroki nie rozwiążą problemu, zobacz [emulator nie można uruchomić (pierwsze użycie)](#NoStart) , aby uzyskać informacje na temat oprogramowania innej firmy, które może zakłócać emulator.

## <a name="NoStart"></a>Nie można uruchomić emulatora (pierwsze użycie)
 Jeśli emulator nie zostanie uruchomiony, wykonaj następujące zadania, aby zidentyfikować i rozwiązać problem.

- Upewnij się, że spełnione są minimalne wymagania sprzętowe oraz że ustawienia systemu BIOS są poprawne.

   Emulator i funkcja Hyper-V systemu Windows 8 wymagają procesora 64-bitowego z translacją adresów drugiego poziomu (SLAT). W przypadku technologii Intel należy zasadniczo potrzebować podstawowego procesora i3, i5 lub i7 (lub jednego z wielu rdzeni). Lista mikroukładów AMD jest dostępna [tutaj](https://www.amd.com/en/support).

  1. Upewnij się, że komputer spełnia [wymagania systemowe](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md).

  2. Sprawdź, czy [Narzędzie SLAT](https://slatstatuscheck.codeplex.com/) zgłasza, że komputer obsługuje translację SLAT.

  3. Upewnij się, że w ustawieniach systemu BIOS komputera jest włączona cała Technologia wirtualizacji. Dokładne opisy systemu BIOS mogą się różnić w zależności od producenta sprzętu. Ogólnie rzecz biorąc, Włącz funkcje związane z:

     - SLAT (translacja adresów drugiego poziomu)

     - EPT (rozszerzone tabele stron) (Intel)

     - NPT (zagnieżdżone tabele stron) (AMD)

     - RVI (Szybkie indeksowanie wirtualizacji) (AMD)

     - VMX (oznaczenie firmy Intel z obsługą wirtualizacji)

     - SVM (oznaczenie AMD z obsługą wirtualizacji sprzętowej)

     - XD (wykonaj wyłączenie) (Intel); to musi być włączone

     - NX (bez wykonywania) (AMD); to musi być włączone.

  4. Jeśli w systemie BIOS znajdują się poniższe opcje, wyłącz je.

     - Wyłączanie technologii Intel VT-d

     - Wyłącz wykonywanie zaufanego

       Aby uzyskać więcej informacji, zobacz ten artykuł: TechNet: Hyper-V: jak naprawić błędy systemu BIOS Włączanie funkcji Hyper-V

  5. Upewnij się, że masz co najmniej 4 GB pamięci systemowej i że nie są używane przez inne programy i procesy korzystające z zasobów.

  6. Upewnij się, że korzystasz z systemu Windows 8 Professional lub lepszego (system Windows Server 2008 nie jest obsługiwany). System Windows Server 2012 jest obsługiwany, ale należy włączyć środowisko pulpitu.

     Możesz sprawdzić Podgląd zdarzeń, aby sprawdzić, czy występują błędy funkcji hypervisor. W tym celu otwórz Podgląd zdarzeń (**klucz początkowy** +**R**, a następnie wpisz `eventvwr`), a następnie wybierz pozycję **Dzienniki systemu Windows**, **system**. Następnie Przefiltruj dziennik według źródła zdarzeń, ustawiając źródło na **funkcji Hyper-V-funkcji hypervisor**. Sprawdź, czy są błędy, aby ułatwić zidentyfikowanie przyczyny głównej.

     Jeśli procesor spełnia minimalne wymagania, ale funkcja hypervisor nadal kończy się niepowodzeniem, należy rozważyć znalezienie tego, czy dla komputera jest dostępne uaktualnienie systemu BIOS. Jeśli istnieje, a użytkownik zdecyduje się na uaktualnienie, należy przestrzegać wszystkich środków ostrożności od producenta podczas uaktualniania systemu BIOS (na przykład w celu upewnienia się, że uaktualnienie oprogramowania układowego BIOS nie zostało przerwane przez utratę mocy, co może spowodować nieodwracalne uszkodzenie systemu BIOS).

- Upewnij się, że masz co najmniej 4 GB pamięci systemowej i że nie są używane przez inne programy i procesy korzystające z zasobów.

- Usuwanie/wyłączanie sterowników lub oprogramowania innych firm, które mogą zakłócać pracę z sieciami wirtualnymi.

   Istnieją pewne znane problemy z produktami innych firm, które są zainstalowane w systemie Windows 8, takie jak sterowniki sieciowe/protokoły, które nie są w pełni zgodne ze stosem sieci funkcji Hyper-V.

   Ogólnie rzecz biorąc, wszyscy deweloperzy tych produktów mogą zaktualizować swoje oprogramowanie, aby były zgodne z systemem Windows 8 i funkcją Hyper-V.

   Następujące produkty mogą wymagać uaktualnienia do zgodności z systemem Windows 8: VirtualBox, Virtual PC 7, VMWare, niektórzy klienci sieci VPN, zapory oprogramowania, niektóre wersje klientów Cisco VPN i inne systemy wirtualizacji. Współpracuj z deweloperem oprogramowania do wirtualizacji umożliwiającej ich uaktualnienie, aby zapewnić zgodność z systemem Windows 8 i funkcją Hyper-V.

   W ramach *obejścia tego problemu*można wyłączyć wszystkie sterowniki i aplikacje innych firm, które mogą zakłócać działanie sieci wirtualnej używanej przez emulator do komunikowania się z programem Visual Studio. Mogą to być następujące aplikacje:

  - Aplikacje antywirusowe (które są podłączane do stosu sieciowego)

  - Narzędzia do monitorowania sieci

  - Narzędzia do rejestrowania w sieci

  - Inne oprogramowanie do monitorowania systemu

    Innym możliwym obejściem jest to, że przed odinstalowaniem produktu (i zażądaniem dewelopera produktu w celu wydania zaktualizowanej wersji), należy wykonać następujące czynności.

  1. Uruchom Menedżera połączeń sieciowych (z ekranu startowego wpisz `View Network Connections` i wybierz tę opcję, aby wyświetlić połączenia sieciowe).

  2. W przypadku karty vEthernet (wewnętrzny port sieci Ethernet Windows Phone wewnętrzny przełącznik emulatora) wybierz pozycję **Właściwości** z menu kontekstowego.

      ![Karta wirtualna używana przez funkcję&#45;Hyper-V](../cross-platform/media/android_emu_virtual_adapter.png "Android_Emu_Virtual_Adapter")

      Właściwości karty są wyświetlane w tym miejscu.

      ![Właściwości karty wirtualnej](../cross-platform/media/android_emu_virtual_adapter_properties.png "Android_Emu_Virtual_Adapter_Properties")

  3. W przypadku tej karty jedynymi elementami, które powinny zostać wybrane w ramach **tego połączenia** , są następujące elementy:

     - Klient sieci Microsoft Networks

     - Harmonogram pakietów QoS

     - Udostępnianie plików i drukarek w sieciach Microsoft Networks

     - Sterownik protokołu LLDP firmy Microsoft

     - Sterownik we/wy mapowania odnajdywania topologii warstwy linku

     - Obiekt odpowiadający odnajdywania topologii warstwy linku

     - Protokół internetowy w wersji 6 (TCP/IPv6)

     - Protokół internetowy w wersji 4 (TCP/IPv4)

  4. Usuń zaznaczenie innych elementów.

     Minusem do korzystania z tej techniki polega na tym, że gdy nowy produkt innej firmy instaluje nieobsługiwane sterowniki lub gdy emulator jest zainstalowany, należy powtórzyć te kroki.

     Po odinstalowaniu produktów innych firm może być konieczne przywrócenie wewnętrznego przełącznika emulatora Windows Phone. W tym celu:

  - Otwórz funkcję Hyper V i przejdź do Menedżera przełącznika wirtualnego. Utwórz przełącznik wirtualny o nazwie "wewnętrzny przełącznik emulatora Windows Phone" i ustaw jego typ połączenia z **siecią wewnętrzną**.

     ![Menedżer przełącznika wirtualnego](../cross-platform/media/android_emu_virtual_switch_manager.png "Android_Emu_Virtual_Switch_Manager")

    Teraz uruchom emulator. Powinna ona być zadziałała.

## <a name="NoBoot"></a>Rozruch komputera po zainstalowaniu emulatora nie powiodło się
 Ten problem może wystąpić, gdy spełnione są następujące warunki:

- Komputer ma gigabajtową płytę główną.

- USB3 jest włączona na płycie głównej.

  Aby rozwiązać ten problem, należy wyłączyć USB3 w ustawieniach systemu BIOS płyty głównej i uruchomić ponownie komputer. Następnie sprawdź, czy gigabajt wydał aktualizację systemu BIOS płyty głównej.

  Aby uzyskać więcej informacji, zobacz następujący artykuł bazy wiedzy: [błąd rozruchu po zainstalowaniu roli funkcji Hyper-V w systemach gigabajtów](https://support.microsoft.com/en-us/kb/2693144).

## <a name="ADB"></a>Program Visual Studio jest niezablokowany podczas próby wdrożenia aplikacji do emulatora lub emulator nie jest wyświetlany jako element docelowy debugowania w innych środowisk IDE
 Jeśli emulator jest uruchomiony, ale nie jest on połączony z ADB (Android Debug Bridge) lub nie jest wyświetlany w narzędziach systemu Android, które korzystają z ADB (na przykład Android Studio lub zaćmienie), może być konieczne dostosowanie lokalizacji emulatora dla ADB. Emulator używa klucza rejestru do identyfikowania podstawowej lokalizacji Android SDK i szuka pliku \platform-tools\adb.exe w tym katalogu. Aby zmodyfikować Android SDK ścieżkę używaną przez emulator:

- Otwórz Edytor rejestru, wybierając opcję **Uruchom** z menu kontekstowego przyciski Start, wpisując `regedit` w oknie dialogowym, a następnie wybierając **przycisk OK**.

- Przejdź do *HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Android SDK Tools* w drzewie folderów po lewej stronie.

- Zmodyfikuj zmienną rejestru **Path** , aby była zgodna ze ścieżką do Android SDK.

  Uruchom ponownie emulator i teraz będzie można zobaczyć emulator podłączony do ADB i skojarzonych narzędzi systemu Android.

## <a name="XamarinPlayer"></a>Emulator zawiesza się, ponieważ nie mógł skonfigurować portu UDP
 Ten problem może wystąpić z powodu niezgodności z programem Xamarin Player. Jeśli emulator prawdopodobnie się zawiesza lub jeśli zostanie wyświetlony komunikat o błędzie "emulator nie może nawiązać połączenia z systemem operacyjnym urządzenia: nie można skonfigurować portu UDP.  Niektóre funkcje mogą być wyłączone — może to być przyczyną problemu. Wykonaj następujące czynności.

1. Odinstaluj program Xamarin Player.

2. Sprawdź, czy pole wirtualne zostało usunięte (program Xamarin Player jest uruchamiany w górnej części pola wirtualnego).

3. Przejdź do Menedżera urządzeń, wybierz opcję wyświetlania ukrytych urządzeń, a następnie Usuń wszystko z wyjątkiem fizycznych kart sieciowych.

4. Przed usunięciem kart sieciowych, które nie są fizyczne, można spróbować odinstalować/ponownie zainstalować funkcję Hyper-V.

## <a name="Skylake"></a>Nie można dołączyć debugera do projektu Xamarin
 Jeśli korzystasz z systemu Windows 10 z procesorami Intel Skylake, aplikacje Xamarin mogą nie działać w emulatorze lub debuger programu Visual Studio może nie dołączyć do nich. Jest to spowodowane problemem z procesorami funkcji Hyper-V i Skylake. W celu obejścia tego problemu wykonaj następujące czynności.

1. Otwórz Menedżera funkcji Hyper-V i wybierz maszynę wirtualną dla profilu emulatora używanego przez użytkownika.

2. Wybierz pozycję **Usuń zapisany stan** (dolny prawy).

3. Wybierz **Ustawienia...**

4. Rozwiń węzeł procesora i wybierz pozycję **zgodność**.

5. Włącz **migrację na komputer fizyczny z inną wersją procesora**.

6. Uruchom ponownie usługę (w obszarze **Akcje**) i spróbuj ponownie.

## <a name="GooglePlay"></a>Emulator nie może uruchomić aplikacji korzystającej z Usługi Google Play
 Emulator nie jest dostarczany z bibliotekami programu dla Usługi Google Play. Emulator obsługuje jednak instalację plików zip z metodą przeciągania i upuszczania.

## <a name="DragAndDrop"></a>Przeciąganie i upuszczanie pliku, APK lub Flash plik zip nie działa
 Emulator używa programu ADB. exe, aby ułatwić transfer plików podczas przeciągania i upuszczania pliku na ekranie. Jeśli wystąpi błąd podczas próby przeciągnięcia i upuszczenia pliku, prawdopodobnie oznacza to, że emulator nie jest połączony z ADB. exe. Aby rozwiązać ten problem, wykonaj kroki w programie [Visual Studio, które uniemożliwiają podjęcie próby wdrożenia aplikacji do emulatora lub emulator nie jest wyświetlany jako element docelowy debugowania w innym środowisk IDE](#ADB).

## <a name="Resolution"></a>Rozdzielczość zrzutu ekranu jest niepoprawna
 W przypadku zrzutu ekranu za pomocą karty zrzut ekranu w oknie **dodatkowe narzędzia** , gdy obraz z wynikiem jest nieoczekiwany, może być konieczne dostosowanie poziomu powiększenia ekranu przed wybraniem opcji **Przechwyć**. Emulator pobiera zrzuty ekranu na ekranie monitora komputera hosta.

## <a name="OpenGL"></a>Nie można renderować zawartości OpenGL przez emulator
 Emulator renderuje zawartość OpenGL przy użyciu procesora GPU maszyny hosta i używa projektu kąta do konwersji tych wywołań do i z DirectX. Jeśli aplikacja jest renderowana prawidłowo na urządzeniu, ale nieprawidłowo na emulatorze, prawdopodobnie urządzenie zmniejsza nieprawidłowe wywołanie OpenGL (na przykład przy użyciu zmiennych modułu cieniującego, które nie pasują).

## <a name="Multitouch"></a>Emulator nie reaguje na Gesty wielodotykowe
 W niektórych przypadkach emulator rozpocznie działanie i nie odpowie na wiele dotyku za pośrednictwem bezpośredniej interakcji z wyświetlaczem z obsługą dotyku lub przy użyciu narzędzia wielodotykowego na pasku narzędzi emulatora. W takim przypadku wybierz przycisk **Obróć** na pasku narzędzi emulatora i spróbuj ponownie użyć wielodotyku. Jeśli problem będzie nadal występować, Przeczytaj [emulator nie może renderować problemu z zawartością OpenGL](#OpenGL) .

## <a name="Support"></a>Zasoby pomocy technicznej
 Jeśli komputer hosta spełnia wymagania systemowe i wystąpi problem, który nie został uwzględniony w tym przewodniku rozwiązywania problemów:

- Zadawaj pytanie dotyczące StackOverflow przy użyciu tagów [emulatora systemu Android](https://stackoverflow.com/questions/tagged/android-emulator) i programu Visual Studio.

- Zgłoś problem przy użyciu narzędzia Wyślij uśmiech w programie Visual Studio lub w Menedżerze emulatorów.
