---
title: Rozwiązywanie problemów z emulatorem dla systemu Android | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: troubleshooting
ms.assetid: f3fb5df4-3aae-40e4-9450-bbe15b0c5af5
caps.latest.revision: 25
ms.author: crdun
manager: crdun
ms.openlocfilehash: a1fc24d27d079576128cf437fb1ee05c2fc78404
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60081557"
---
# <a name="troubleshooting-the-visual-studio-emulator-for-android"></a>Rozwiązywanie problemów z emulatorem programu Visual Studio dla systemu Android
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten temat zawiera informacje pomocne podczas rozwiązywania problemów, które mogą wystąpić podczas korzystania z programu Visual Studio Emulator for Android.

> [!WARNING]
>  Po zainstalowaniu emulatora program instalacyjny sprawdza wymagania wstępne dotyczące uruchamiania oprogramowania. Wyświetla ostrzeżenia, jeśli wymagania wstępne nie są obecne, ale nie wymaga ich instalacji.

 Ten temat zawiera następujące sekcje.

- [Przed rozpoczęciem](#BeforeYouStart)

- [Emulator nie można zainstalować](#NoInstall)

- [Nie można nawiązać połączenia z sieci docelowych w domenie lub sieci firmowej](#DomainNetwork)

- [Nie można połączyć z sieci docelowych, jeśli ustawienia sieciowe wymagają ręcznej konfiguracji](#ManualNetworkConfig)

- [Emulator uruchamia się powoli, nie można uruchomić z powodu przekroczenia limitu czasu lub wdrożenia aplikacji nie powiedzie się.](#SlowStart)

- [Emulator nie została uruchomiona](#NoStart2)

- [Emulator nie powiedzie się (pierwszym użyciu)](#NoStart)

- [Komputerowi nie uda się uruchomić po zainstalowaniu emulatora](#NoBoot)

- [Program Visual Studio zablokowania próby wdrożenia aplikacji w emulatorze lub emulator nie jest wyświetlany jako element docelowy debugowania w innych środowiskach IDE](#ADB)

- [Emulator zawiesza się, ponieważ nie można ustawić port UDP](#XamarinPlayer)

- [Nie można dołączyć debugera do projektu Xamarin](#Skylake)

- [Emulator nie powiedzie się uruchomić aplikację, która używa usług Google Play](#GooglePlay)

- [Przeciąganie i upuszczanie plików, APK lub pliku w pliku zip nie działa](#DragAndDrop)

- [Rozdzielczość zrzut ekranu jest nieprawidłowa](#Resolution)

- [Emulator nie powiedzie się do renderowania zawartości ze specyfikacji OpenGL](#OpenGL)

- [Emulator nie odpowiada na gestów dotykowych wielu](#Multitouch)

- [Zasoby pomocy technicznej](#Support)

## <a name="BeforeYouStart"></a> Przed rozpoczęciem
 Przed rozpoczęciem rozwiązywania problemów, warto przejrzeć następujące tematy:

- [Wymagania systemowe dotyczące emulatora programu Visual Studio dla systemu Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)

## <a name="NoInstall"></a> Emulator nie można zainstalować
 Jeśli masz zainstalowany w funkcji Hyper-V, zostanie wyświetlony następujący komunikat, gdy próbują zainstalować emulator. Konieczne jest posiadanie maszynie, która obsługuje funkcji Hyper-v i musi być włączona.

 ![Android&#95;Emu&#95;zainstalować&#95;problem](../cross-platform/media/android-emu-install-issue.png "Android_Emu_Install_Issue")

> [!NOTE]
>  Ten komunikat ma zastosowanie zarówno do programu Visual Studio Emulator for Android i Windows Phone Emulator. Windows 8.1 i Windows 10 obsługuje emulatora.

 Jeśli ten komunikat jest wyświetlony, sprawdź [wymagania systemowe programu Visual Studio Emulator for Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md) aby zobaczyć, czy można uruchomić emulatora.

## <a name="DomainNetwork"></a> Nie można nawiązać połączenia z sieci docelowych w domenie lub sieci firmowej
 Visual Studio Emulator for Android pojawia się w sieci jako osobne urządzenia przy użyciu adresu IP. Nie jest przyłączony do domeny Windows i nie udostępniać poświadczenia domeny lub grupy roboczej z komputera hosta.

 Jeśli sieć wymaga autoryzacji do domeny lub grupy roboczej dla podstawowych sieci i łączności z Internetem, skontaktuj się z administratorem IT, dla wyjątku. Ten wyjątek umożliwia programowanie ma pełnić rolę maszyny granic i do akceptowania połączeń z urządzeniami sieciowymi nieprzyłączonych do domeny, takich jak emulator.

 Visual Studio Emulator for Android używa również swój własny zestaw adresów MAC. Jeśli nie masz dostępu sieci lub zasobów w Internecie z emulatora, skontaktuj się z administratorem IT, aby upewnić się, czy adresy MAC to emulator autoryzowanych w sieci.

#### <a name="to-view-the-emulators-mac-addresses"></a>Aby wyświetlić to emulator MAC adresów

1. Uruchom emulator.

2. Na pasku narzędzi emulator, kliknij przycisk z podwójną strzałką (>>) aby otworzyć okno dodatkowe narzędzia.

3. W oknie dodatkowe narzędzia kliknij kartę sieci.

4. Na stronie sieci Znajdź wpisy adresów fizycznych.

## <a name="ManualNetworkConfig"></a> Nie można połączyć z sieci docelowych, jeśli ustawienia sieciowe wymagają ręcznej konfiguracji
 Aby połączyć się z sieci docelowych z emulatora, sieci musi spełniać następujące wymagania:

- DHCP. Emulator wymaga protokołu DHCP, ponieważ konfiguruje się jako osobne urządzenia do sieci za pomocą adresu IP.

- Automatycznie skonfigurowana DNS i ustawień bramy. Nie jest możliwe do skonfigurowania ustawień DNS i bramę ręcznie dla emulatora.

  Jeśli sieć wymaga ręcznie skonfigurowane ustawienia, skontaktuj się z administratorem IT, aby ustalić, jak włączyć łączność sieciową dla emulatora.

## <a name="SlowStart"></a> Emulator uruchamia się powoli, nie można uruchomić z powodu przekroczenia limitu czasu lub wdrożenia aplikacji nie powiedzie się.
 W pewnych okolicznościach emulatora w ciągu kilku minut można uruchomić lub nie została uruchomiona z powodu przekroczenia limitu czasu. Jeśli emulator nie powiedzie się, zostanie wyświetlony następujący komunikat: `App deployment failed. Please try again`. Ten błąd może powodować następujące warunki.

- Uruchamianie emulatora programu Visual Studio dla systemu Android z rozruchowego dysku VHD. Ta konfiguracja nie jest obsługiwana.

- Uszkodzony dysk twardy. Rozważ uruchomienie programu chkdsk.

- Dysk twardy, który ma być defragmentacji. Należy wziąć pod uwagę defragmentacji dysku.

- Dysk twardy, który jest prawie pełna. Sprawdź ilość miejsca dostępnego na dysku.

- Nie ma wystarczającej ilości pamięci jest dostępna w związku z innych uruchomionych aplikacji. Zmniejsz liczbę aplikacji, które zużywają pamięci lub zwiększ ilość pamięci.

- Ogólnie rzecz biorąc wszelkie współczynnika, który jest przyczyniające się do niskiej wydajności w systemie. Rozpocznij rozwiązywanie problemów przy użyciu składnika, który ma najniższą częściowy indeksu środowiska Windows, w którym można znaleźć na stronie informacji o wydajności i narzędzia w Panelu sterowania.

## <a name="NoStart2"></a> Emulator nie została uruchomiona
 Jeśli emulator była praca wcześniej, ale nie działa, wykonaj następujące zadania. Jeśli używasz emulatora po raz pierwszy, zobacz [emulatora uruchomienie nie powiedzie się (pierwszym użyciu)](#NoStart) przed podjęciem próby wykonania tych kroków.

- Usuń wszystkie wystąpienia funkcji Hyper-V emulatora.

    1. Zamknij program Visual Studio.

    2. Otwórz Menedżera funkcji Hyper-V i Zatrzymaj wszystkie wystąpienia funkcji Hyper-V emulatora (maszyn wirtualnych), które zostały już uruchomione i ewentualnie w stanie uszkodzenia.

    3. W Menedżerze funkcji Hyper-V należy usunąć wszelkie inne emulatora maszyn wirtualnych.

    4. Uruchom ponownie komputer.

- Upewnij się, że masz co najmniej 4 GB pamięci systemu i że jego jest nie są używane przez inne programy dużej ilości zasobów i procesów (np. Spróbuj zamknąć wszystkie okna przeglądarki).

- W Menedżerze funkcji Hyper-V Otwórz Menedżera przełącznika wirtualnego i sprawdź, czy masz dwa przełączników sieciowych; Sprawdź, czy pierwsza z nich to przełącznik wewnętrzny, i drugą jest zewnętrzny.

     ![Android&#95;Emu&#95;V&#95;Switch&#95;Man](../cross-platform/media/android-emu-v-switch-man.png "Android_Emu_V_Switch_Man")

     Jeśli konfiguracja jest nieprawidłowa w przypadku korzystania z systemu Windows 10, użytkownik może próbować [ponownej instalacji urządzeń sieciowych przy użyciu polecenia – d netcfg](http://windows.microsoft.com/windows-10/fix-network-connection-issues) (sekcja 6).

- Jeśli te kroki nie rozwiązują problemu, zobacz [emulatora uruchomienie nie powiedzie się (pierwszym użyciu)](#NoStart) uzyskać informacji na temat 3 oprogramowania innych firm, które mogą powodować konflikt z emulatorem.

## <a name="NoStart"></a> Emulator nie powiedzie się (pierwszym użyciu)
 Nie można uruchomić emulatora, wykonaj następujące zadania, aby zidentyfikować i rozwiązać problem.

- Upewnij się, że spełnione są wymagania dotyczące minimalnych wymagań sprzętowych i czy ustawienia systemu BIOS są poprawne.

   Emulatora i Windows 8 Hyper-V wymaga 64-bitowy procesor z adresów drugiego poziomu Translation (SLAT). Firmy Intel konieczne są zasadniczo i3 Core, i5 lub i7 procesora (lub jeden z wielu Xeons). Dostępna jest lista mikroukładami AMD [tutaj](http://support.amd.com/en-us).

  1. Upewnić się, że Twoje komputer spełnia [wymagania systemowe](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md).

  2. Upewnij się, że [narzędzie SLAT](https://slatstatuscheck.codeplex.com/) zgłasza, że komputer jest w stanie SLAT.

  3. W ustawieniach systemu BIOS komputera upewnij się, że włączono wszystkich technologii wirtualizacji. Dokładne opisy systemu BIOS mogą się różnić dla każdego producenta sprzętu. Ogólnie rzecz biorąc Włącz funkcje związane z programem:

     - SLAT (translacji adresów drugiego poziomu)

     - EPT (Extended Page Tables) (Intel)

     - NPT (zagnieżdżona strona tabele) (AMD)

     - RVI (Rapid Virtualization Indexing) (AMD)

     - VMX (wskazująca, obsługa wirtualizacji sprzętowej akronim Intel)

     - SVM (akronim AMD wskazujący Obsługa wirtualizacji sprzętowej)

     - XD (wykonywania Wyłącz) (Intel); musi być włączona

     - NX (nie Execute)(AMD); musi być włączona.

  4. Jeśli poniższe opcje są obecne w systemie BIOS, należy je wyłączyć.

     - Wyłącz Intel VT-d

     - Wyłącz zaufane wykonywanie

       Aby uzyskać więcej informacji znajduje się w artykule: TechNet: Funkcja Hyper-V: Jak naprawić błędy systemu BIOS, włączenie funkcji Hyper-V

  5. Upewnij się, że masz co najmniej 4 GB pamięci systemu i że jego jest nie są używane przez inne programy dużej ilości zasobów i procesów.

  6. Upewnij się, że używasz systemu Windows 8 Professional lub nowszy (system Windows Server 2008 nie jest obsługiwane). Jest obsługiwana w systemie Windows Server 2012, ale należy włączyć środowisko pulpitu.

     Można sprawdzić Podgląd zdarzeń, aby zobaczyć, czy istnieją błędy funkcji Hypervisor. Aby to zrobić, otwórz Podgląd zdarzeń (klucz rozpoczęcia + R, a następnie wpisz `eventvwr`), a następnie wybierz **Dzienniki Windows**, **systemu**. Następnie przeprowadź filtrowanie dziennika przez źródło zdarzenia, ustawienie źródła **funkcji Hyper-V-funkcji Hypervisor**. Sprawdź, czy błędy, aby ułatwić zidentyfikowanie przyczyny.

     Jeśli Twoje spełnia procesora minimalne wymagania, ale funkcja hypervisor nadal nie działa prawidłowo, należy wziąć pod uwagę wyszukiwanie po podjęciu występuje uaktualnienie systemu BIOS dostępnej dla komputera. Jeśli istnieje, i chcesz uaktualnić, pamiętaj obserwować wszystkie środki ostrożności od producenta, podczas uaktualniania do systemu BIOS (na przykład upewniając się, uaktualnienie oprogramowania układowego BIOS nie zostało przerwane przez utraty zasilania, które trwale może uszkodzić system BIOS).

- Upewnij się, że masz co najmniej 4 GB pamięci systemu i że jego jest nie są używane przez inne programy dużej ilości zasobów i procesów.

- Usuń/wyłączyć sterowników firm trzecich lub oprogramowania, które zakłócają sieci wirtualnej.

   Istnieją znane problemy z niektórych 3rd produktów innych firm, które są zainstalowane w systemie Windows 8, takie jak sterowniki/protokołów sieciowych, które nie są w pełni zgodny ze stosu sieciowego funkcji Hyper-V.

   Ogólnie rzecz biorąc będzie ona do tych produktów deweloperom aktualizacji oprogramowania, aby był zgodny z systemem Windows 8 i funkcji Hyper-V.

   Następujące produkty mogą wymagać uaktualnienia pod kątem zgodności z systemem Windows 8: VirtualBox, Virtual PC 7, VMWare, niektórzy klienci sieci VPN, zapór programowych, niektóre wersje klientów sieci VPN oprogramowania Cisco i innych systemów wirtualizacji. Praca z deweloper oprogramowania wirtualizacji wątpliwe zachęcania go do uaktualnienia oprogramowania, aby był zgodny z systemem Windows 8 i funkcji Hyper-V.

   Jako **obejście**, można wyłączyć wszystkie sterowniki innych firm i aplikacje, które zakłócają sieci wirtualnej, używanego przez Emulator do komunikowania się z programem Visual Studio. Aplikacje te mogą obejmować:

  - Aplikacje antywirusowe, (które dołączyć do stosu sieciowego)

  - Narzędzia do monitorowania sieci

  - Narzędzia rejestrowania w sieci

  - Inne oprogramowanie monitorujące systemu

    Innym możliwym obejściem ograniczony odinstalowaniu produktów w zapytania i żądanie developer produktu do wersji jest dostępna zaktualizowana wersja, ma wykonać następujące czynności.

  1. Uruchom Menedżera połączeń sieciowych (na ekranie startowym wpisz `View Network Connections` i wybierz tę opcję, aby wyświetlić połączenia sieciowego.)

  2. Dla karty vEthernet (wewnętrzny Ethernet portu Windows Phone Emulator wewnętrznego przełącznika), wybierz **właściwości** z menu kontekstowego.

      ![Wirtualną kartę sieciową, używane przez Hyper&#45;V](../cross-platform/media/android-emu-virtual-adapter.png "Android_Emu_Virtual_Adapter")

      Właściwości karty są wyświetlane w tym miejscu.

      ![Właściwości karty wirtualnego](../cross-platform/media/android-emu-virtual-adapter-properties.png "Android_Emu_Virtual_Adapter_Properties")

  3. Dla tej karty, tylko elementy, które należy wybrać w obszarze **to połączenie wykorzystuje następujące elementy** powinny być następujące:

     - Klient sieci Microsoft Networks

     - Harmonogram pakietów QoS

     - Udostępnianie plików i drukarek w sieciach Microsoft Networks

     - Sterownik protokołu LLDP firmy Microsoft

     - Warstwa łącza sterownik mapowania topologii odnajdowania

     - Obiekt odpowiadający odnajdywania topologii warstwy linku

     - Protokół internetowy w wersji 6 (TCP/IPv6)

     - Protokół internetowy w wersji 4 (TCP/IPv4)

  4. Usuń zaznaczenie wszystkich innych elementów.

     Wadą się przy użyciu tej metody polega na ilekroć nowych produktów innych firm 3 instaluje sterowniki nieobsługiwana lub każdym razem, gdy emulator jest zainstalowany, te kroki należy powtórzyć.

     Po odinstalowaniu produktów innych firm może być konieczne przywrócić przełącznika wewnętrznego Emulator Windows Phone. Aby to zrobić:

  - Otwórz Hyper-V i przejdź do Menedżera przełącznika wirtualnego. Utwórz przełącznik wirtualny o nazwie "Windows Phone Emulator wewnętrznego przełącznika" i ustaw jej typ połączenia na **sieci wewnętrznej**.

     ![Menedżer przełącznika wirtualnego](../cross-platform/media/android-emu-virtual-switch-manager.png "Android_Emu_Virtual_Switch_Manager")

    Teraz uruchom emulator. Wszystko powinno działać.

## <a name="NoBoot"></a> Komputerowi nie uda się uruchomić po zainstalowaniu emulatora
 Ten problem może wystąpić, gdy są spełnione następujące warunki:

- Komputer ma gigabajt płyty głównej.

- USB3 jest włączona na płycie głównej.

  Aby rozwiązać ten problem, wyłącz USB3 w ustawieniach systemu BIOS płyty głównej, a następnie uruchom ponownie komputer. Sprawdź, czy gigabajt wydała aktualizacji dla systemu BIOS z płyty głównej.

  Aby uzyskać więcej informacji zobacz następujący artykuł bazy wiedzy: [Rozruch awarii po zakończeniu instalacji roli funkcji Hyper-V w systemach gigabajt](https://support.microsoft.com/kb/2693144).

## <a name="ADB"></a> Program Visual Studio zablokowania próby wdrożenia aplikacji w emulatorze lub emulator nie jest wyświetlany jako element docelowy debugowania w innych środowiskach IDE
 Jeśli emulator jest uruchomiona, ale nie ma się połączyć z ADB (Android Debug Bridge) lub pojawia się narzędzia systemu Android, które korzystają z ADB (na przykład programu Android Studio lub Eclipse), może być konieczne dostosowanie, gdy emulator szuka ADB. Emulator używa klucza rejestru do identyfikowania podstawowa Lokalizacja zestawu Android SDK i szuka pliku \platform-tools\adb.exe, w tym katalogu. Aby zmodyfikować ścieżkę zestawu Android SDK używany przez emulator:

- Otwórz Edytor rejestru, wybierając **Uruchom** z menu kontekstowego przyciski Start, wpisując `regedit` w oknie dialogowym i wybierając pozycję **OK**.

- Przejdź do HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Android SDK Tools w drzewie folderów po lewej stronie.

- Modyfikowanie **ścieżki** zmiennej rejestru, aby dopasować ścieżkę do zestawu SDK systemu Android.

  Ponowne uruchomienie emulatora i powinno być teraz możliwe emulator połączone ADB i skojarzonych narzędzi dla systemu Android.

## <a name="XamarinPlayer"></a> Emulator zawiesza się, ponieważ nie można ustawić port UDP
 Może wystąpić problem związany z powodu niezgodności z odtwarzaczem Xamarin. Emulator zawiesi się lub jeśli zostanie wyświetlony ten komunikat o błędzie "emulator nie jest w stanie połączyć się z system operacyjny urządzenia: Nie można skonfigurować pod kątem portu UDP.  Niektóre funkcje mogą być wyłączone", być może wystąpił problem. Wykonaj następujące kroki.

1. Odinstaluj program Xamarin Player.

2. Sprawdź, czy pole danej wirtualnej został usunięty (Xamarin Player działa na polu wirtualnego).

3. Przejdź do Menedżera urządzeń, wybierz opcję Pokaż ukryte urządzenia, a następnie usuń wszystkie elementy z wyjątkiem przypadków karty sieci fizycznej.

4. Możesz wypróbować, odinstalowanie/ponowne zainstalowanie funkcji Hyper-V po usunięciu niefizycznej sieciowe.

## <a name="Skylake"></a> Nie można dołączyć debugera do projektu Xamarin
 Jeśli używasz systemu Windows 10 z procesorów Intel Skylake, aplikacje platformy Xamarin może się nie powieść się uruchamianie w emulatorze lub debugera programu Visual Studio nie może dołączyć do nich. Jest to spowodowane problem z funkcją Hyper-V i procesorów Skylake. Wykonaj następujące kroki, aby uniknąć tego problemu.

1. Otwórz Menedżera funkcji Hyper-V i wybierz maszynę Wirtualną, dla emulatora profilu, czy przy użyciu.

2. Wybierz **usunięcia zapisanego stanu** (w lewym dolnym rogu).

3. Wybierz **ustawień...**

4. Rozwiń węzeł procesora, a następnie wybierz **zgodności**.

5. Włącz **Migruj do komputera fizycznego z inną wersją procesora**.

6. Uruchom ponownie usługę (w obszarze **akcje**), a następnie spróbuj ponownie.

## <a name="GooglePlay"></a> Emulator nie powiedzie się uruchomić aplikację, która używa usług Google Play
 Emulator nie jest dostarczany z bibliotekami dostępność usług Google Play. Emulator obsługuje jednak instalacji przeciąganie i upuszczanie plików w pliku zip.

## <a name="DragAndDrop"></a> Przeciąganie i upuszczanie plików, APK lub pliku w pliku zip nie działa
 Emulator używa ADB.exe w celu ułatwienia transferu plików, gdy przeciągnij i upuść plik na ekranie. Jeśli wystąpi błąd podczas próby przeciągnij i upuść plik, to prawdopodobnie oznacza to, czy emulator nie jest podłączony do ADB.exe. Aby rozwiązać problem, wykonaj kroki opisane w [zablokowania programu Visual Studio, w trakcie wdrażania aplikacji w emulatorze lub emulator nie jest wyświetlany jako element docelowy debugowania w innych środowiskach IDE](#ADB).

## <a name="Resolution"></a> Rozdzielczość zrzut ekranu jest nieprawidłowa
 Jeśli wykonujesz zrzut ekranu za pomocą karty zrzut ekranu w **dodatkowe narzędzia** okna i obraz wynikowy jest nieoczekiwany rozmiar, konieczne może być dostosować poziom powiększenia ekranu przed wybraniem **przechwytywania**. Emulator przyjmuje zrzuty ekranu w rozdzielczości ekranu na monitorze komputera hosta.

## <a name="OpenGL"></a> Emulator nie powiedzie się do renderowania zawartości ze specyfikacji OpenGL
 Emulator renderuje zawartość ze specyfikacji OpenGL, przy użyciu procesora GPU na komputerze hosta i używa projektu kąt na konwertowanie tych wywołań programu DirectX. Jeśli aplikacja poprawnie renderowany na urządzeniu, ale niepoprawne w emulatorze, jest prawdopodobne, że urządzenie jest łagodzenia nieprawidłowe wywołanie OpenGL (na przykład za pomocą programu do cieniowania zmiennych, które nie są zgodne).

## <a name="Multitouch"></a> Emulator nie odpowiada na gestów dotykowych wielu
 W niektórych przypadkach emulator uruchomi oraz nie odpowiada na wielodotyku albo za pomocą możliwości bezpośredniej interakcji z obsługą dotykową ekranu lub za pomocą narzędzia Obsługa wielodotyku na pasku narzędzi emulatora. Jeśli jest to możliwe, wybierz opcję **Obróć** znajdujący się na pasku narzędzi emulatora i spróbuj ponownie wykorzystać wielodotyku. Jeśli problem będzie się powtarzać, zapoznaj się z [emulatora zakończy się niepowodzeniem do renderowania zawartości ze specyfikacji OpenGL](#OpenGL) problem.

## <a name="Support"></a> Zasoby pomocy technicznej
 Jeśli komputer-host spełnia wymagania systemowe i wystąpi problem, nie są uwzględnione w tym przewodniku rozwiązywania problemów:

- Zadaj pytanie na temat korzystania z StackOverflow [emulator systemu android](http://stackoverflow.com/questions/tagged/android-emulator) znacznikami visual studio.

- Zgłoś problem za pomocą Wyślij uśmiech narzędzia programu Visual Studio lub w Menedżerze emulatorów.
