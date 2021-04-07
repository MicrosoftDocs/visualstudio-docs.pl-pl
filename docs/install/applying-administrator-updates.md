---
title: Stosowanie aktualizacji administratorów do programu Visual Studio przy użyciu programu Microsoft Endpoint Configuration Manager
titleSuffix: ''
description: Dowiedz się, jak stosować aktualizacje administratorów do programu Visual Studio.
ms.date: 04/06/2021
ms.custom: ''
ms.topic: overview
ms.assetid: 9a3fdb28-db3d-4970-bc17-7417a985f0fb
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d316fc35df8c571a9112d7a653737e099df80559
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547456"
---
# <a name="applying-administrator-updates-that-use-microsoft-endpoint-configuration-manager"></a>Stosowanie aktualizacji administratorów korzystających z programu Microsoft Endpoint Configuration Manager

W tym dokumencie opisano różne typy i cechy aktualizacji administratora programu Visual Studio. Poniżej znajdują się informacje o tym, jak i kiedy powinny być dystrybuowane w całej organizacji, jakie są dostępne opcje konfiguracji oraz jak wyświetlać raporty i rozwiązywać problemy. Więcej informacji o wymaganiach wstępnych dotyczących korzystania z aktualizacji administratorów znajduje się w temacie [Włączanie aktualizacji administratora](../install/enabling-administrator-updates.md).

## <a name="understanding-visual-studio-administrator-updates"></a>Informacje o aktualizacjach administratorów programu Visual Studio 

Pakiet aktualizacji administratora programu Visual Studio, który został opublikowany w Microsoft Update do użycia przez wykaz Microsoft i usługi WSUS, zawiera informacje o tym, że Configuration Manager musi być w stanie pobrać i rozesłać aktualizację do programu Visual Studio na komputerach klienckich. Zawiera również informacje wymagane przez administratora IT w celu podjęcia decyzji o tym, które aktualizacje mają być dystrybuowane w całej organizacji, i ułatwiają konserwację układów sieciowych. Pakiety aktualizacji administratora programu Visual Studio nie zawierają wystarczającej ilości informacji do wykonania nowej instalacji produktu ani nie zawierają żadnych rzeczywistych plików binarnych produktu opublikowanych w Content Delivery Network. Aktualizacje administratorów programu Visual Studio są rozłączne, podobnie jak zwykłe aktualizacje programu Visual Studio. Można założyć, że wszystkie aktualizacje programu Visual Studio, które mają wyższy numer wersji produktu i późniejszą datę wydania, są nadzbiorem starszej, niższej wersji. 

Aktualizacje administratorów programu Visual Studio mają zastosowanie do wersji obsługiwanych przez program Visual Studio. Aby uzyskać więcej informacji o tym, które linie bazowe obsługi programu Visual Studio są nadal obsługiwane w określonym przedziale czasu, zobacz [cykl życia produktu Visual Studio i obsługa](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs). Wszystkie obsługiwane linie bazowe obsługi programu Visual Studio będą bezpieczne.  

## <a name="types-and-characteristics-of-administrator-updates"></a>Typy i cechy aktualizacji administratorów 

Istnieją trzy typy aktualizacji administratorów do programu Visual Studio:

* **Aktualizacje zabezpieczeń** mają zastosowanie do wszystkich wersji programu Visual Studio (np. Enterprise, Professional, Community itp.) i zawierają ograniczone, wysoce związane i zgodne ze sobą zmiany poziomu obsługi. Aktualizacje zabezpieczeń nie spowodują przejścia klienta do nowszej wersji pomocniczej; są one przeznaczone do dostarczania poprawek do luk w zabezpieczeniach klienta, który jest już na określonym poziomie wersji pomocniczej. Aktualizacje zabezpieczeń będą zawierać co najmniej jedną poprawkę zabezpieczeń, ale Poprawka zabezpieczeń może lub nie musi znajdować się w składniku lub obciążeniu, który jest zainstalowany na komputerze klienckim. Na przykład możemy naprawić lukę w zabezpieczeniach składników .NET i oznaczyć aktualizację jako aktualizację zabezpieczeń, ale nie będzie to miało znaczącego wpływu na komputer kliencki, na którym zainstalowano tylko składniki języka C++. Aktualizacje zabezpieczeń mogą również zawierać inne poprawki niezawodności lub inne niezbędne aktualizacje składników. Aktualizacje zabezpieczeń są publikowane zarówno w [wykazie Microsoft Update](https://www.catalog.update.microsoft.com/Home.aspx) (MUC), jak i [Windows Server Update Services](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus), gdzie są klasyfikowane jako "aktualizacje zabezpieczeń".
 
* **Aktualizacje funkcji** umożliwiają ADMINISTRATORom IT zaawansowanie komputerów w organizacji do nowszej wersji pomocniczej programu Visual Studio 2019. Aktualizacje funkcji mają zastosowanie tylko do wersji programu Visual Studio, które są powszechnie dostępne w przedsiębiorstwach, takich jak jednostki SKU narzędzi Enterprise, Professional i Build. Wszystkie aktualizacje funkcji zostaną opublikowane w wykazie Microsoft Update jako "pakiety funkcji" i są dostępne do opcjonalnego ręcznego [zaimportowania do Configuration Manager z wykazu Microsoft Update](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog). Aktualizacje funkcji są kumulatywne i będą zawierać dodatkowe funkcje jakości i wcześniejsze poprawki. Zapoznaj się z [sekcją opcje konfiguracji](#understanding-configuration-options) poniżej, aby uzyskać instrukcje dotyczące konfigurowania komputera klienckiego w celu pozostawania w linii bazowej obsługi i zapobiegania dostarczaniu aktualizacji funkcji do określonych klientów. 

* **Aktualizacje dotyczące jakości** są również stosowane tylko do tych wersji programu Visual Studio, które są powszechnie dostępne w przedsiębiorstwach. zawierają one ograniczone, wysoce skierowane i zgodne zmiany poziomu obsługi. Aktualizacje dotyczące jakości nie spowodują przejścia klienta do nowszej wersji pomocniczej; są one przeznaczone do dostarczania poprawek wydajności i niezawodności lub innych niezbędnych aktualizacji składników do klienta, który znajduje się już na określonym poziomie wersji pomocniczej. Aktualizacje dotyczące jakości są gromadzone wraz z aktualizacjami zabezpieczeń i w ten sposób zawierają poprawki zabezpieczeń tylko wtedy, gdy Poprawka zabezpieczeń została już niezależnie wydana. Aktualizacje dotyczące jakości są publikowane w katalogu Microsoft Update jako "aktualizacje" i są także dostępne do opcjonalnego ręcznego [importowania do Configuration Manager](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog).

### <a name="decoding-the-titles-of-administrator-updates"></a>Dekodowanie tytułów aktualizacji administratorów

Tytuł każdej aktualizacji administratora obejmuje zarówno odpowiedni zakres wersji, jak i wynikową wersję aktualizacji.Na przykład

::: moniker range="vs-2017"

* **Program Visual studio 2017 w wersji 15.9.0 do 15.9.35 Update** sklasyfikowany jako "Aktualizacja zabezpieczeń" dotyczy wszystkich wersji programu visual Studio 2017 na kliencie między wersjami 15.9.0 za pomocą 15.9.35 i zaktualizuje te wersje klienta do 15.9.35.

* **Program Visual studio 2017 w wersji 15.0.0 do 15.9.0 Update** sklasyfikowany jako "Feature Pack" będzie miał zastosowanie do wersji programu visual Studio 2017 licencjonowanej na użytek przedsiębiorstwa na kliencie między całym zakresem wersji produktu 15.0.0 za pomocą 15.9.0 i zaktualizuje te wersje klienta do 15.9.0. Zastosowanie tego pakietu funkcji w istocie umożliwia klientom otrzymywanie aktualizacji zabezpieczeń. 

* **Program Visual studio 2017 w wersji 15.9.0 do 15.9.37 Update** sklasyfikowany jako "Updates" będzie miał zastosowanie do wersji programu visual Studio 2017 licencjonowanej do użycia w przedsiębiorstwie między wersjami 15.9.0 za pomocą 15.9.37 i zaktualizuje te wersje klienta do 15.9.37. 

::: moniker-end

::: moniker range="vs-2019"

* **Program Visual studio 2019 w wersji 16.7.0 do 16.7.12 Update** sklasyfikowany jako "Aktualizacja zabezpieczeń" dotyczy wszystkich wersji programu visual Studio 2019 na kliencie między wersjami 16.7.0 za pomocą 16.7.12 i zaktualizuje te wersje klienta do 16.7.12.  

* **Program Visual studio 2019 w wersji 16.0.0 do 16.9.0 Update** sklasyfikowany jako "Feature Pack" będzie miał zastosowanie do wersji programu visual Studio 2019 licencjonowanej do użycia w przedsiębiorstwie między całym zakresem wersji produktu 16.0.0 za pomocą 16.9.0 i zaktualizuje te wersje klienta (które nie zostały skonfigurowane tak, aby pozostawały w poprzedniej linii bazowej obsługi) do 16.9.0. 

* **Program Visual studio 2019 w wersji 16.8.0 do 16.8.7 Update** sklasyfikowany jako "Updates" będzie miał zastosowanie do wersji programu visual Studio 2019 licencjonowanej do użycia w przedsiębiorstwie między wersjami 16.8.0 za pomocą 16.8.7 i zaktualizuje te wersje klienta do 16.8.7. 

::: moniker-end

## <a name="using-configuration-manager-to-deploy-visual-studio-updates"></a>Wdrażanie aktualizacji programu Visual Studio za pomocą Configuration Manager

### <a name="understanding-configuration-options"></a>Informacje o opcjach konfiguracji

Istnieje kilka opcji konfiguracji, których można użyć do dostosowywania aktualizacji administratora programu Visual Studio, dzięki czemu są one zgodne z preferencjami i wymaganiami organizacji. Poniżej wymieniono najbardziej typowe opcje konfiguracji. Aby uzyskać wyczerpującą listę wszystkich obsługiwanych zachowań aktualizacji administratora, zobacz [Używanie parametrów wiersza polecenia do instalowania programu Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) i płatność tylko za te, które odpowiadają akcjom "Update".

* **[Zgoda na aktualizację administratora](../install/enabling-administrator-updates.md#encoding-administrator-intent-on-the-client-machines)**: ten klucz rejestru jest wymagany, aby komputer kliencki otrzymywał aktualizacje administratorów. Jest to klucz dla całej maszyny, co oznacza, że ma zastosowanie do wszystkich wystąpień programu Visual Studio zainstalowanych w tym polu. 
 
* Niezależny **użytkownik programu Visual Studio**: Użytkownicy programu Visual Studio mogą używać oddzielnego klucza rejestru **AdministratorUpdatesOptOut** na całym komputerze, aby *zrezygnować* z otrzymywania aktualizacji administratora programu Visual Studio. Celem tego klucza jest umożliwienie użytkownikowi programu Visual Studio pewnej kontroli nad aktualizacjami, które są automatycznie stosowane do komputera. Aby skonfigurować komputer kliencki do blokowania aktualizacji administratora, Ustaw klucz REG_DWORD **AdministratorUpdatesOptOut**   na **1**. Brak klucza lub ustawiona wartość **0** oznacza, że użytkownik programu Visual Studio chce otrzymywać aktualizacje administratorów do programu Visual Studio.

    Należy pamiętać, że klucz **AdministratorUpdatesOptOut**   do kodowania preferencji użytkownika jest określany za pomocą klucza **AdministratorUpdatesEnabled**   , który koduje zamiar administratora IT. Jeśli **AdministratorUpdatesOptOut**   jest ustawiona na **1**, aktualizacja zostanie zablokowana na kliencie, nawet jeśli klucz **AdministratorUpdatesEnabled**   jest również ustawiony na **1**.W tej akcji przyjęto założenie, że administratorzy IT mogą uzyskać dostęp do wybranych deweloperów i monitorować je, a następnie mogą omówić, których potrzebami są ważniejsze.Administratorzy IT mogą zawsze zmieniać każdy klucz w dowolnym momencie.
 
* **Lokalizacja zaktualizowanych bitów produktu**: większość czasu komputery klienckie pobierają zaktualizowane bity produktu z Internetu za pośrednictwem sieci CDN firmy Microsoft. Ten scenariusz wymaga, aby komputery klienckie miały dostęp do Internetu. Niektóre przedsiębiorstwa ograniczają jednak komputery klienckie tylko do instalowania i aktualizowania usługi BITS z lokalizacji wewnętrznej układu sieciowego. Aby mieć pewność, że aktualizacje administratorów można zastosować przy użyciu zaktualizowanych bitów, które znajdują się w wewnętrznej lokalizacji sieciowej, aby można było pomyślnie wdrożyć aktualizację administratora, muszą być spełnione następujące warunki: 

  - Komputer kliencki musi mieć w pewnym momencie uruchomiony program inicjujący z tej lokalizacji układu sieciowego. W idealnym przypadku oryginalną instalację klienta nastąpiło przy użyciu programu inicjującego z układu sieciowego, ale po prostu można zainstalować aktualizację przy użyciu zaktualizowanego programu inicjującego w tej samej lokalizacji sieciowej. Jedna z tych akcji zostałaby osadzona na komputerze klienckim, a połączenie z tą konkretną lokalizacją układu.   
  - Lokalizację układu sieciowego (z którym jest połączony klient) należy [zaktualizować, aby zawierała zaktualizowane bity produktu](../install/update-a-network-installation-of-visual-studio.md) , które aktualizacja administratora chce wdrożyć. 

::: moniker range="vs-2019"

* **Obsługa linii bazowej lepkość**: zgodnie z powyższym opisem, aktualizacje administratorów, które są aktualizacjami funkcji, zastąpią instalację programu Visual Studio nowszą wersję pomocniczą produktu. Czasami jednak zespoły deweloperów, takie jak pozostały, pozostają w określonym stabilnym i bezpiecznym poziomie linii bazowej, i chcą kontrolować, kiedy ich klienci zaawansowani do bardziej aktualnej wersji pomocniczej. W celu skonfigurowania komputera klienckiego w celu pozostawania w linii bazowej obsługi i ignorowania nieżądanych aktualizacji funkcji administratora, należy utworzyć i ustawić wartość danych **BaselineStickinessVersions2019** Reg_SZ na ciąg, który reprezentuje dozwolone linie bazowe, do których można przyciągnąć i pozostawić komputer kliencki.  Ciąg może zawierać sekwencję wersji linii bazowej obsługi, rozdzielonych przecinkami, takimi jak **16.4.0, 16.7.0**. Dowolna liczba wersji linii bazowej obsługi może być uwzględniona w ciągu, a słowo **All**, które jest skrótem dla wszystkich obsługiwanych linii bazowych obsługi, jest również obsługiwane. 

     Jeśli `BaselineStickinessVersions2019` wartość rejestru jest źle sformułowana, wszystkie aktualizacje funkcji zostaną zablokowane na komputerze. Należy również zwrócić uwagę na [obsługiwane przedziały czasu dla aktualizacji funkcji programu Visual Studio](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs). Mimo że jest to technicznie możliwe, aby zastosować aktualizacje funkcji, które osiągnęły koniec ich okresów istnienia, nie zalecamy tego, ponieważ nie są one wspierane i w związku z tym potencjalnie niebezpieczne.

::: moniker-end

* **Wymuś tę aktualizację, nawet jeśli program Visual Studio jest w użyciu**: program Visual Studio musi zostać zamknięty przed zainstalowaniem aktualizacji. Jeśli program Visual Studio jest otwarty lub używany, instalacja aktualizacji zostanie przerwana. Łatwym sposobem upewnienia się, że program Visual Studio jest zamknięty, jest skonfigurowanie Menedżera potwierdzenia w celu zastosowania aktualizacji bezpośrednio po ponownym uruchomieniu komputera. Możesz również użyć parametru, `--force` Aby wymusić zamknięcie programu Visual Studio. Wymuszenie zamknięcia programu Visual Studio może spowodować utratę pracy, dlatego należy używać jej z zachowaniem ostrożności. Uruchomienie aktualizacji administratora w domyślnym kontekście systemowym spowoduje zignorowanie `–-force` flagi, dlatego należy skonfigurować aktualizację administratora tak, aby była uruchamiana w kontekście użytkownika.

### <a name="methods-for-configuring-an-administrator-update"></a>Metody konfigurowania aktualizacji administratora

Istnieją trzy główne metody konfigurowania aktualizacji administratorów: klucz rejestru, plik konfiguracyjny na komputerze klienckim lub modyfikacja Configuration Manager samym pakietem wdrożeniowym.   

* **Klucz rejestru**: aktualizacje administratorów Szukaj określonych kluczy rejestru w dowolnej standardowej lokalizacji programu Visual Studio zgodnie z opisem w temacie [Set Defaults for Enterprise Deployments](../install/set-defaults-for-enterprise-deployments.md). Opcje, które są kontrolowane przez klucze rejestru, to takie elementy, jak **AdministratorUpdatesOptOut** REG_DWORD, **AdministratorUpdatesOptOut**   REG_DWORD i **BaselineStickinessVersions2019** Reg_SZ. Do utworzenia i ustawienia wartości kluczy rejestru wymagane są uprawnienia administratora na komputerze klienckim. 
 
* **Plik konfiguracji**: niektóre ustawienia można zachować na komputerze klienckim w opcjonalnym pliku konfiguracji, który umożliwia ustawienie go tylko raz i ma zastosowanie do wszystkich przyszłych aktualizacji administratora. Podejście do pliku konfiguracji zachowuje się jak klucz rejestru i jest dla całej maszyny, co oznacza, że zostanie zastosowane do wszystkich instalacji programu Visual Studio zainstalowanych na komputerze klienckim. Standardowa lokalizacja pliku konfiguracji to `C:\ProgramData\Microsoft\VisualStudio\updates.config` . Jeśli jednak chcesz użyć innej lokalizacji do przechowywania pliku, możesz to zrobić, tworząc klucz rejestru Reg_SZ o nazwie **UpdateConfigurationFile** i ustawiając wartość tego klucza na ścieżkę do pliku konfiguracji. Ten klucz rejestru może być umieszczony w dowolnej lokalizacji w rejestrze programu Visual Studio, zgodnie z opisem w temacie [Set Defaults for Enterprise Deployments](../install/set-defaults-for-enterprise-deployments.md). Jeśli zdecydujesz się dodać wartość rejestru dla niestandardowej lokalizacji pliku konfiguracji, będzie ona wyglądała na ten plik. Jeśli plik nie istnieje, zostanie zgłoszony wyjątek, a aktualizacja zakończy się niepowodzeniem.    
 
     Plik konfiguracji, który jest w formacie JSON, obsługuje opcję, `installerUpdateArgs` która jest tablicą ciągów rozdzielonych przecinkami, które określają więcej przełączników, które można przekazać do Instalatora programu Visual Studio. Jeśli zawartość pliku zawiera nieprawidłowe pole lub opcję, która nie jest obsługiwana, aktualizacja zakończy się niepowodzeniem. Aby uzyskać więcej informacji, zobacz [Używanie parametrów wiersza polecenia do instalowania programu Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md).
 
   Oto przykładowy plik konfiguracyjny: 

   ```
   “installerUpdateArgs” : [“--quiet”, “--noWeb”], 

   “checkPendingReboot” :  “true” 
   ```

* **Ręczne aktualizowanie pakietu aktualizacji administratora w programie SCCM**: można także ręcznie zmodyfikować parametry wiersza polecenia poszczególnych pakietów aktualizacji administratora w programie SCCM.

## <a name="verification-reports-and-troubleshooting-error-codes"></a>Weryfikacja, raporty i rozwiązywanie problemów z kodami błędów

### <a name="determining-that-visual-studio-was-updated"></a>Określanie, czy program Visual Studio został zaktualizowany

Aby sprawdzić, czy aktualizacja administratora została zainstalowana prawidłowo, można użyć jednej z następujących metod: 

* Na komputerze klienckim uruchom program Visual Studio 2019, wybierz pozycję **Pomoc**   >  **** i sprawdź, czy numer wersji jest zgodny z ostatnią liczbą w tytule zamierzonej aktualizacji. 

* Użyj narzędzia **vswhere** na komputerze klienckim, aby zidentyfikować różne wersje programu Visual Studio na komputerze. Aby uzyskać więcej informacji, zobacz [Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi](../install/tools-for-managing-visual-studio-instances.md). 

* Każda próbka aktualizacji administracyjnej generuje kilka plików dziennika w katalogu komputera klienckiego `%temp%` , który przechwytuje postęp operacji aktualizacji.Posortuj folder według daty i Wyszukaj pliki, które zaczynają się  `dd_updatedriver` ,  `dd_bootstrapper` ,  `dd_client` i  `dd_setup`   odpowiednio do aktualizacji administracyjnych, programu inicjującego, Instalator programu Visual Studio i aparatu Instalatora.Sprawdź, czy te pliki dziennika zawierają 0, co oznacza, że aktualizacja została pomyślnie zastosowana. Należy zauważyć, że te pliki dzienników mogą być również używane do sprawdzenia, czy plik konfiguracji jest używany. Więcej informacji można znaleźć w [narzędziu do zbierania dzienników programu Visual Studio](https://www.microsoft.com/download/details.aspx?id=12493) .     

### <a name="error-codes-and-conditions"></a>Kody błędów i warunki

>[!IMPORTANT]
> Należy pamiętać, że program Visual Studio musi być zamknięty przed zainstalowaniem aktualizacji. Jeśli program Visual Studio jest otwarty lub używany, instalacja aktualizacji zostanie anulowana.

Aktualizacje administracyjne mogą zwrócić następujące kody powrotne:  

| Kod błędu | Definicja |
|--|:-|
| 0 | Aktualizacja administracyjna została pomyślnie zainstalowana. |
| 1001 | Instalator programu Visual Studio lub proces instalacji powiązanej jest uruchomiony. Aktualizacja nie jest stosowana. |
| 1002 | Instalator programu Visual Studio jest wstrzymana. Aktualizacja nie jest stosowana. |
| 1003 | Program Visual Studio jest uruchomiony. Aktualizacja nie jest stosowana. Ten warunek można obsłużyć przy użyciu `--force` flagi. |
| 1004 | Nie wykryto Internetu.Aktualizacja nie mogła skontaktować się z lokalizacją internetową zawierającą zaktualizowane pliki. Aktualizacja nie jest stosowana. |
| 1005 |  ****   Wartość rejestru AdministratorUpdatesEnabled jest ustawiona na **0** lub nie została ustawiona wcale. Aktualizacja nie jest stosowana. |
| 1006 |  ****   Wartość rejestru AdministratorUpdatesOptOut jest ustawiona na **1**. Aktualizacja nie jest stosowana. Klucz jest przeznaczony dla komputerów klienckich, które nie powinny być aktualizowane przez administratora. |
| 1007 | Nie zainstalowano Instalator programu Visual Studio. |
| 1008 | Wartość rejestru **BaselineStickinessVersions2019** nie jest w formacie możliwym do odczytu. Wartość rejestru musi zawierać **wszystkie** lub prawidłowe wersje z numerem kompilacji ustawionym na 0 jawnie, na przykład X. Y. 0. |
| 3010 | System wymaga ponownego uruchomienia.Aktualizacja mogła nie zostać zastosowana. Uruchom ponownie komputer i ponów próbę aktualizacji. |
| Inne | Wystąpił błąd podczas próby zastosowania aktualizacji.Aktualizacja nie jest stosowana. |

Aby uzyskać wyczerpującą listę kodów błędów klientów, zobacz [Używanie parametrów wiersza polecenia do instalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md). 

## <a name="feedback-and-support"></a>Opinie i pomoc techniczna
[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

Poniższe metody umożliwiają przesłanie opinii na temat aktualizacji administratora programu Visual Studio lub raportów dotyczących problemów, które mają wpływ na aktualizacje:
* Zapoznaj się ze wskazówkami dotyczącymi [rozwiązywania problemów dotyczących instalacji i uaktualniania programu Visual Studio](../install/troubleshooting-installation-issues.md) .
* Zadawaj pytania do społeczności w witrynie [Visual Studio Setup Q&forum](https://docs.microsoft.com/answers/topics/vs-setup.html).
* Przejdź do [strony pomocy technicznej programu Visual Studio](https://visualstudio.microsoft.com/vs/support/)i sprawdź, czy Twój problem znajduje się na liście często zadawanych pytań.  Można również wybrać przycisk [link do pomocy technicznej](https://visualstudio.microsoft.com/vs/support/#talktous) , aby uzyskać pomoc dotyczącą rozmowy.
* Zapoznaj się z [opiniami dotyczącymi funkcji lub Zgłoś problem](https://aka.ms/vs/wsus/feedback) do zespołu programu Visual Studio, w którym można zastosować aktualizacje administratorów.
* Skontaktuj się z kierownikiem ds. klientów firmy Microsoft.

## <a name="see-also"></a>Zobacz też
* [Włączanie aktualizacji administratorów](../install/enabling-administrator-updates.md)    
* [Podręcznik administratora programu Visual Studio](../install/visual-studio-administrator-guide.md)
* [Cykl życia produktu i obsługa techniczna programu Visual Studio](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs)
* [Informacje o wersji programu Visual Studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/release-notes)
* [Informacje o wersji programu Visual Studio 2017](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes)
* [Instalowanie programu Visual Studio](../install/install-visual-studio.md)
* [Używanie parametrów wiersza polecenia do instalowania programu Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md)
* [Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi](../install/tools-for-managing-visual-studio-instances.md)
* [Tworzenie instalacji sieciowej programu Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
* [Jak zdefiniować ustawienia w pliku odpowiedzi](../install/automated-installation-with-response-file.md)
* [Sterowanie aktualizacjami wdrożeń programu Visual Studio opartych na sieci](../install/controlling-updates-to-visual-studio-deployments.md)
* [Wykaz Microsoft Update — często zadawane pytania](https://www.catalog.update.microsoft.com/faq.aspx)
* [Dokumentacja programu Microsoft Endpoint Configuration Manager (SCCM)](https://docs.microsoft.com/mem/configmgr)
* [Importuj aktualizacje z usługi Microsoft Catalog do Configuration Manager](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [Dokumentacja programu Windows Server Update Services (WSUS)](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started-windows-server-update-services-wsus)
