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
ms.openlocfilehash: 380de9206b2dc4e78c3719919dfd78720de28129
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297647"
---
# <a name="troubleshooting-the-visual-studio-emulator-for-android"></a>Rozwiązywanie problemów z emulatorem programu Visual Studio dla systemu Android
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten temat zawiera informacje pomocne podczas rozwiązywania problemów, które mogą wystąpić podczas korzystania z programu Visual Studio Emulator for Android.

> [!WARNING]
> Po zainstalowaniu emulatora program instalacyjny sprawdza wymagania wstępne dotyczące uruchamiania oprogramowania. Wyświetla ostrzeżenia, jeśli wymagania wstępne nie są obecne, ale nie wymaga ich instalacji.

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
 Przed rozpoczęciem rozwiązywania problemów, warto przejrzeć następujące tematy:

- [Wymagania systemowe dotyczące emulatora programu Visual Studio dla systemu Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)

## <a name="NoInstall"></a>Nie można zainstalować emulatora
 Jeśli masz zainstalowany w funkcji Hyper-V, zostanie wyświetlony następujący komunikat, gdy próbują zainstalować emulator. Konieczne jest posiadanie maszynie, która obsługuje funkcji Hyper-v i musi być włączona.

 ![Problem&#95;z&#95;instalacją&#95;systemu Android UGW](../cross-platform/media/android-emu-install-issue.png "Android_Emu_Install_Issue")

> [!NOTE]
> Ten komunikat ma zastosowanie zarówno do programu Visual Studio Emulator for Android i Windows Phone Emulator. Windows 8.1 i Windows 10 obsługuje emulatora.

 Jeśli zobaczysz ten komunikat, sprawdź [wymagania systemowe emulatora programu Visual Studio dla systemu Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md) , aby sprawdzić, czy można uruchomić emulator.

## <a name="DomainNetwork"></a>Nie można nawiązać połączenia z lokalizacjami docelowymi sieci w domenie lub sieci firmowej
 Visual Studio Emulator for Android pojawia się w sieci jako osobne urządzenia przy użyciu adresu IP. Nie jest przyłączony do domeny Windows i nie udostępniać poświadczenia domeny lub grupy roboczej z komputera hosta.

 Jeśli sieć wymaga autoryzacji do domeny lub grupy roboczej dla podstawowych sieci i łączności z Internetem, skontaktuj się z administratorem IT, dla wyjątku. Ten wyjątek umożliwia programowanie ma pełnić rolę maszyny granic i do akceptowania połączeń z urządzeniami sieciowymi nieprzyłączonych do domeny, takich jak emulator.

 Visual Studio Emulator for Android używa również swój własny zestaw adresów MAC. Jeśli nie masz dostępu sieci lub zasobów w Internecie z emulatora, skontaktuj się z administratorem IT, aby upewnić się, czy adresy MAC to emulator autoryzowanych w sieci.

#### <a name="to-view-the-emulators-mac-addresses"></a>Aby wyświetlić to emulator MAC adresów

1. Uruchom emulator.

2. Na pasku narzędzi emulator, kliknij przycisk z podwójną strzałką (>>) aby otworzyć okno dodatkowe narzędzia.

3. W oknie dodatkowe narzędzia kliknij kartę sieci.

4. Na stronie sieci Znajdź wpisy adresów fizycznych.

## <a name="ManualNetworkConfig"></a>Nie można nawiązać połączenia z sieciami docelowymi, gdy ustawienia sieciowe wymagają ręcznej konfiguracji
 Aby połączyć się z sieci docelowych z emulatora, sieci musi spełniać następujące wymagania:

- DHCP. Emulator wymaga protokołu DHCP, ponieważ konfiguruje się jako osobne urządzenia do sieci za pomocą adresu IP.

- Automatycznie skonfigurowana DNS i ustawień bramy. Nie jest możliwe do skonfigurowania ustawień DNS i bramę ręcznie dla emulatora.

  Jeśli sieć wymaga ręcznie skonfigurowane ustawienia, skontaktuj się z administratorem IT, aby ustalić, jak włączyć łączność sieciową dla emulatora.

## <a name="SlowStart"></a>Emulator zaczyna działać powoli, nie można uruchomić z powodu przekroczenia limitu czasu lub wdrożenie aplikacji nie powiodło się
 W pewnych okolicznościach emulatora w ciągu kilku minut można uruchomić lub nie została uruchomiona z powodu przekroczenia limitu czasu. Kiedy emulator nie zostanie uruchomiony, zobaczysz następujący komunikat: `App deployment failed. Please try again`. Ten błąd może powodować następujące warunki.

- Uruchamianie emulatora programu Visual Studio dla systemu Android z rozruchowego dysku VHD. Ta konfiguracja nie jest obsługiwana.

- Uszkodzony dysk twardy. Rozważ uruchomienie programu chkdsk.

- Dysk twardy, który ma być defragmentacji. Należy wziąć pod uwagę defragmentacji dysku.

- Dysk twardy, który jest prawie pełna. Sprawdź ilość miejsca dostępnego na dysku.

- Nie ma wystarczającej ilości pamięci jest dostępna w związku z innych uruchomionych aplikacji. Zmniejsz liczbę aplikacji, które zużywają pamięci lub zwiększ ilość pamięci.

- Ogólnie rzecz biorąc wszelkie współczynnika, który jest przyczyniające się do niskiej wydajności w systemie. Rozpocznij rozwiązywanie problemów przy użyciu składnika, który ma najniższą częściowy indeksu środowiska Windows, w którym można znaleźć na stronie informacji o wydajności i narzędzia w Panelu sterowania.

## <a name="NoStart2"></a>Nie można uruchomić emulatora
 Jeśli emulator była praca wcześniej, ale nie działa, wykonaj następujące zadania. Jeśli używasz emulatora po raz pierwszy, zobacz [emulator nie można uruchomić (pierwsze użycie)](#NoStart) przed wykonaniem tych kroków.

- Usuń wszystkie wystąpienia funkcji Hyper-V emulatora.

    1. Zamknij program Visual Studio.

    2. Otwórz Menedżera funkcji Hyper-V i Zatrzymaj wszystkie wystąpienia funkcji Hyper-V emulatora (maszyn wirtualnych), które zostały już uruchomione i ewentualnie w stanie uszkodzenia.

    3. W Menedżerze funkcji Hyper-V należy usunąć wszelkie inne emulatora maszyn wirtualnych.

    4. Uruchom ponownie komputer.

- Upewnij się, że masz co najmniej 4 GB pamięci systemu i że jego jest nie są używane przez inne programy dużej ilości zasobów i procesów (np. Spróbuj zamknąć wszystkie okna przeglądarki).

- W Menedżerze funkcji Hyper-V Otwórz Menedżera przełącznika wirtualnego i sprawdź, czy masz dwa przełączników sieciowych; Sprawdź, czy pierwsza z nich to przełącznik wewnętrzny, i drugą jest zewnętrzny.

     ![Android&#95;—&#95;&#95;przełączanie z&#95;przełącznika euro](../cross-platform/media/android-emu-v-switch-man.png "Android_Emu_V_Switch_Man")

     Jeśli instalacja jest nieprawidłowa i używasz systemu Windows 10, możesz spróbować [ponownie zainstalować urządzenia sieciowe przy użyciu polecenia netcfg-d](https://support.microsoft.com/help/10741/windows-fix-network-connection-issues) (sekcja 6).

- Jeśli te kroki nie rozwiążą problemu, zobacz [emulator nie można uruchomić (pierwsze użycie)](#NoStart) , aby uzyskać informacje na temat oprogramowania innej firmy, które może zakłócać emulator.

## <a name="NoStart"></a>Nie można uruchomić emulatora (pierwsze użycie)
 Nie można uruchomić emulatora, wykonaj następujące zadania, aby zidentyfikować i rozwiązać problem.

- Upewnij się, że spełnione są wymagania dotyczące minimalnych wymagań sprzętowych i czy ustawienia systemu BIOS są poprawne.

   Emulatora i Windows 8 Hyper-V wymaga 64-bitowy procesor z adresów drugiego poziomu Translation (SLAT). Firmy Intel konieczne są zasadniczo i3 Core, i5 lub i7 procesora (lub jeden z wielu Xeons). Lista mikroukładów AMD jest dostępna [tutaj](https://www.amd.com/en/support).

  1. Upewnij się, że komputer spełnia [wymagania systemowe](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md).

  2. Sprawdź, czy [Narzędzie SLAT](https://slatstatuscheck.codeplex.com/) zgłasza, że komputer obsługuje translację SLAT.

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

       Aby uzyskać więcej informacji znajduje się w artykule: Technet: funkcja Hyper-V: jak można rozwiązać systemu BIOS błędy włączenie funkcji Hyper-V

  5. Upewnij się, że masz co najmniej 4 GB pamięci systemu i że jego jest nie są używane przez inne programy dużej ilości zasobów i procesów.

  6. Upewnij się, że używasz systemu Windows 8 Professional lub nowszy (system Windows Server 2008 nie jest obsługiwane). Jest obsługiwana w systemie Windows Server 2012, ale należy włączyć środowisko pulpitu.

     Można sprawdzić Podgląd zdarzeń, aby zobaczyć, czy istnieją błędy funkcji Hypervisor. W tym celu otwórz Podgląd zdarzeń (Uruchom klucz + R, a następnie wpisz `eventvwr`), a następnie wybierz pozycję **Dzienniki systemu Windows**, **system**. Następnie Przefiltruj dziennik według źródła zdarzeń, ustawiając źródło na **funkcji Hyper-V-funkcji hypervisor**. Sprawdź, czy błędy, aby ułatwić zidentyfikowanie przyczyny.

     Jeśli Twoje spełnia procesora minimalne wymagania, ale funkcja hypervisor nadal nie działa prawidłowo, należy wziąć pod uwagę wyszukiwanie po podjęciu występuje uaktualnienie systemu BIOS dostępnej dla komputera. Jeśli istnieje, i chcesz uaktualnić, pamiętaj obserwować wszystkie środki ostrożności od producenta, podczas uaktualniania do systemu BIOS (na przykład upewniając się, uaktualnienie oprogramowania układowego BIOS nie zostało przerwane przez utraty zasilania, które trwale może uszkodzić system BIOS).

- Upewnij się, że masz co najmniej 4 GB pamięci systemu i że jego jest nie są używane przez inne programy dużej ilości zasobów i procesów.

- Usuń/wyłączyć sterowników firm trzecich lub oprogramowania, które zakłócają sieci wirtualnej.

   Istnieją znane problemy z niektórych 3rd produktów innych firm, które są zainstalowane w systemie Windows 8, takie jak sterowniki/protokołów sieciowych, które nie są w pełni zgodny ze stosu sieciowego funkcji Hyper-V.

   Ogólnie rzecz biorąc będzie ona do tych produktów deweloperom aktualizacji oprogramowania, aby był zgodny z systemem Windows 8 i funkcji Hyper-V.

   Następujące produkty mogą wymagać uaktualnienia pod kątem zgodności z systemem Windows 8: VirtualBox, Virtual PC 7, VMWare, niektórzy klienci sieci VPN oprogramowania zapory, niektóre wersje klientów sieci VPN oprogramowania Cisco i innych systemów wirtualizacji. Praca z deweloper oprogramowania wirtualizacji wątpliwe zachęcania go do uaktualnienia oprogramowania, aby był zgodny z systemem Windows 8 i funkcji Hyper-V.

   W ramach **obejścia tego problemu**można wyłączyć wszystkie sterowniki i aplikacje innych firm, które mogą zakłócać działanie sieci wirtualnej używanej przez emulator do komunikowania się z programem Visual Studio. Aplikacje te mogą obejmować:

  - Aplikacje antywirusowe, (które dołączyć do stosu sieciowego)

  - Narzędzia do monitorowania sieci

  - Narzędzia rejestrowania w sieci

  - Inne oprogramowanie monitorujące systemu

    Innym możliwym obejściem ograniczony odinstalowaniu produktów w zapytania i żądanie developer produktu do wersji jest dostępna zaktualizowana wersja, ma wykonać następujące czynności.

  1. Uruchom Menedżera połączeń sieciowych (z ekranu startowego wpisz `View Network Connections` i wybierz tę opcję, aby wyświetlić połączenia sieciowe).

  2. W przypadku karty vEthernet (wewnętrzny port sieci Ethernet Windows Phone wewnętrzny przełącznik emulatora) wybierz pozycję **Właściwości** z menu kontekstowego.

      ![Karta wirtualna używana przez funkcję&#45;Hyper-V](../cross-platform/media/android-emu-virtual-adapter.png "Android_Emu_Virtual_Adapter")

      Właściwości karty są wyświetlane w tym miejscu.

      ![Właściwości karty wirtualnej](../cross-platform/media/android-emu-virtual-adapter-properties.png "Android_Emu_Virtual_Adapter_Properties")

  3. W przypadku tej karty jedynymi elementami, które powinny zostać wybrane w ramach **tego połączenia** , są następujące elementy:

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

  - Otwórz Hyper-V i przejdź do Menedżera przełącznika wirtualnego. Utwórz przełącznik wirtualny o nazwie "wewnętrzny przełącznik emulatora Windows Phone" i ustaw jego typ połączenia z **siecią wewnętrzną**.

     ![Menedżer przełącznika wirtualnego](../cross-platform/media/android-emu-virtual-switch-manager.png "Android_Emu_Virtual_Switch_Manager")

    Teraz uruchom emulator. Wszystko powinno działać.

## <a name="NoBoot"></a>Rozruch komputera po zainstalowaniu emulatora nie powiodło się
 Ten problem może wystąpić, gdy są spełnione następujące warunki:

- Komputer ma gigabajt płyty głównej.

- USB3 jest włączona na płycie głównej.

  Aby rozwiązać ten problem, wyłącz USB3 w ustawieniach systemu BIOS płyty głównej, a następnie uruchom ponownie komputer. Sprawdź, czy gigabajt wydała aktualizacji dla systemu BIOS z płyty głównej.

  Aby uzyskać więcej informacji, zobacz następujący artykuł bazy wiedzy: [błąd rozruchu po zainstalowaniu roli funkcji Hyper-V w systemach gigabajtów](https://support.microsoft.com/kb/2693144).

## <a name="ADB"></a>Program Visual Studio jest niezablokowany podczas próby wdrożenia aplikacji do emulatora lub emulator nie jest wyświetlany jako element docelowy debugowania w innych środowisk IDE
 Jeśli emulator jest uruchomiona, ale nie ma się połączyć z ADB (Android Debug Bridge) lub pojawia się narzędzia systemu Android, które korzystają z ADB (na przykład programu Android Studio lub Eclipse), może być konieczne dostosowanie, gdy emulator szuka ADB. Emulator używa klucza rejestru do identyfikowania podstawowa Lokalizacja zestawu Android SDK i szuka pliku \platform-tools\adb.exe, w tym katalogu. Aby zmodyfikować ścieżkę zestawu Android SDK używany przez emulator:

- Otwórz Edytor rejestru, wybierając opcję **Uruchom** z menu kontekstowego przyciski Start, wpisując `regedit` w oknie dialogowym, a następnie wybierając **przycisk OK**.

- Przejdź do HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Android SDK Tools w drzewie folderów po lewej stronie.

- Zmodyfikuj zmienną rejestru **Path** , aby była zgodna ze ścieżką do Android SDK.

  Ponowne uruchomienie emulatora i powinno być teraz możliwe emulator połączone ADB i skojarzonych narzędzi dla systemu Android.

## <a name="XamarinPlayer"></a>Emulator zawiesza się, ponieważ nie mógł skonfigurować portu UDP
 Może wystąpić problem związany z powodu niezgodności z odtwarzaczem Xamarin. Emulator zawiesi się lub jeśli zostanie wyświetlony ten komunikat o błędzie "emulator nie jest w stanie połączyć się z system operacyjny urządzenia: nie można ustawić port UDP.  Niektóre funkcje mogą być wyłączone", być może wystąpił problem. Wykonaj następujące kroki.

1. Odinstaluj program Xamarin Player.

2. Sprawdź, czy pole danej wirtualnej został usunięty (Xamarin Player działa na polu wirtualnego).

3. Przejdź do Menedżera urządzeń, wybierz opcję Pokaż ukryte urządzenia, a następnie usuń wszystkie elementy z wyjątkiem przypadków karty sieci fizycznej.

4. Możesz wypróbować, odinstalowanie/ponowne zainstalowanie funkcji Hyper-V po usunięciu niefizycznej sieciowe.

## <a name="Skylake"></a>Nie można dołączyć debugera do projektu Xamarin
 Jeśli używasz systemu Windows 10 z procesorów Intel Skylake, aplikacje platformy Xamarin może się nie powieść się uruchamianie w emulatorze lub debugera programu Visual Studio nie może dołączyć do nich. Jest to spowodowane problem z funkcją Hyper-V i procesorów Skylake. Wykonaj następujące kroki, aby uniknąć tego problemu.

1. Otwórz Menedżera funkcji Hyper-V i wybierz maszynę Wirtualną, dla emulatora profilu, czy przy użyciu.

2. Wybierz pozycję **Usuń zapisany stan** (dolny prawy).

3. Wybierz **Ustawienia...**

4. Rozwiń węzeł procesora i wybierz pozycję **zgodność**.

5. Włącz **migrację na komputer fizyczny z inną wersją procesora**.

6. Uruchom ponownie usługę (w obszarze **Akcje**) i spróbuj ponownie.

## <a name="GooglePlay"></a>Emulator nie może uruchomić aplikacji korzystającej z Usługi Google Play
 Emulator nie jest dostarczany z bibliotekami dostępność usług Google Play. Emulator obsługuje jednak instalacji przeciąganie i upuszczanie plików w pliku zip.

## <a name="DragAndDrop"></a>Przeciąganie i upuszczanie pliku, APK lub Flash plik zip nie działa
 Emulator używa ADB.exe w celu ułatwienia transferu plików, gdy przeciągnij i upuść plik na ekranie. Jeśli wystąpi błąd podczas próby przeciągnij i upuść plik, to prawdopodobnie oznacza to, czy emulator nie jest podłączony do ADB.exe. Aby rozwiązać ten problem, wykonaj kroki w programie [Visual Studio, które uniemożliwiają podjęcie próby wdrożenia aplikacji do emulatora lub emulator nie jest wyświetlany jako element docelowy debugowania w innym środowisk IDE](#ADB).

## <a name="Resolution"></a>Rozdzielczość zrzutu ekranu jest niepoprawna
 W przypadku zrzutu ekranu za pomocą karty zrzut ekranu w oknie **dodatkowe narzędzia** , gdy obraz z wynikiem jest nieoczekiwany, może być konieczne dostosowanie poziomu powiększenia ekranu przed wybraniem opcji **Przechwyć**. Emulator przyjmuje zrzuty ekranu w rozdzielczości ekranu na monitorze komputera hosta.

## <a name="OpenGL"></a>Nie można renderować zawartości OpenGL przez emulator
 Emulator renderuje zawartość ze specyfikacji OpenGL, przy użyciu procesora GPU na komputerze hosta i używa projektu kąt na konwertowanie tych wywołań programu DirectX. Jeśli aplikacja poprawnie renderowany na urządzeniu, ale niepoprawne w emulatorze, jest prawdopodobne, że urządzenie jest łagodzenia nieprawidłowe wywołanie OpenGL (na przykład za pomocą programu do cieniowania zmiennych, które nie są zgodne).

## <a name="Multitouch"></a>Emulator nie reaguje na Gesty wielodotykowe
 W niektórych przypadkach emulator uruchomi oraz nie odpowiada na wielodotyku albo za pomocą możliwości bezpośredniej interakcji z obsługą dotykową ekranu lub za pomocą narzędzia Obsługa wielodotyku na pasku narzędzi emulatora. W takim przypadku wybierz przycisk **Obróć** na pasku narzędzi emulatora i spróbuj ponownie użyć wielodotyku. Jeśli problem będzie nadal występować, Przeczytaj [emulator nie może renderować problemu z zawartością OpenGL](#OpenGL) .

## <a name="Support"></a>Zasoby pomocy technicznej
 Jeśli komputer-host spełnia wymagania systemowe i wystąpi problem, nie są uwzględnione w tym przewodniku rozwiązywania problemów:

- Zadawaj pytanie dotyczące StackOverflow przy użyciu tagów [emulatora systemu Android](https://stackoverflow.com/questions/tagged/android-emulator) i programu Visual Studio.

- Zgłoś problem za pomocą Wyślij uśmiech narzędzia programu Visual Studio lub w Menedżerze emulatorów.
