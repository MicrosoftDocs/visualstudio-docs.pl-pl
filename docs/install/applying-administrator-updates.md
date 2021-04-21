---
title: Stosowanie aktualizacji administratora do Visual Studio z Microsoft Endpoint Configuration Manager
titleSuffix: ''
description: Dowiedz się, jak stosować aktualizacje administratora do Visual Studio.
ms.date: 04/16/2021
ms.custom: ''
ms.topic: overview
ms.assetid: 9a3fdb28-db3d-4970-bc17-7417a985f0fb
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d7d2950b9495846693d5edee7790b8611cbca170
ms.sourcegitcommit: 367a2d9df789aa617abaa09b0cd0a18db7357d0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107800792"
---
# <a name="applying-administrator-updates-that-use-microsoft-endpoint-configuration-manager"></a>Stosowanie aktualizacji administratora, które używają Microsoft Endpoint Configuration Manager

W tym dokumencie opisano różne typy i cechy Visual Studio aktualizacji administratora. Poniżej znajdziesz informacje o tym, jak i kiedy powinny być dystrybuowane w całej organizacji, jakie opcje konfiguracji są dostępne oraz jak wyświetlać raporty i rozwiązywać problemy. Aby uzyskać więcej informacji na temat wymagań wstępnych dotyczących korzystania z aktualizacji administratora, zobacz [Włączanie aktualizacji administratora](../install/enabling-administrator-updates.md). Aktualizacje administratora zakładają, że Visual Studio jest już zainstalowany na komputerze. Zastosowanie aktualizacji administratora nie spowoduje zainicjowania zupełnie nowej instalacji.

## <a name="understanding-visual-studio-administrator-updates"></a>Informacje Visual Studio administratorów 

Pakiet aktualizacji Visual Studio administratora programu , który jest publikowany w programie Microsoft Update do użycia przez katalog firmy Microsoft i usługi WSUS, zawiera informacje, które program Menedżer konfiguracji musi mieć możliwość pobrania i rozpowszechniania aktualizacji programu Visual Studio na maszynach klienckich. Zawiera on również informacje, których administrator IT potrzebuje do podjęcia decyzji o tym, które aktualizacje mają być dystrybuowane w całej organizacji. Może również służyć do ułatwienia konserwacji układów sieci. Pakiety Visual Studio aktualizacji administratora programu nie zawierają wystarczających informacji, aby wykonać nową instalację produktu, ani nie zawierają żadnych rzeczywistych plików binarnych produktu opublikowanych w Content Delivery Network. Visual Studio są zbiorcze, podobnie jak regularne aktualizacje Visual Studio aktualizacji. Można założyć, że każda Visual Studio, która ma wyższy numer wersji produktu, a data późniejszej wersji jest narzutem starszej, starszej wersji. 

Visual Studio administratorów mają zastosowanie do Visual Studio wersji obsługi technicznej, które są w ramach pomocy technicznej. Aby uzyskać więcej informacji na temat Visual Studio linii bazowych obsługi technicznej w danym okresie, zobacz Visual Studio Cykl życia produktu i [obsługa techniczna.](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs) Wszystkie obsługiwane Visual Studio bazowe obsługi zostaną zabezpieczone.  

## <a name="types-and-characteristics-of-administrator-updates"></a>Typy i charakterystyki aktualizacji administratora 

Istnieją trzy typy aktualizacji administratora, które Visual Studio:

* **Aktualizacje zabezpieczeń** mają zastosowanie do wszystkich wersji Visual Studio (np. Enterprise, Professional, Community itp.) i zawierają ograniczone, wysoce ukierunkowane i zgodne zmiany poziomu obsługi. Aktualizacje zabezpieczeń nie przejdą klienta do nowszej wersji pomocniczej; Są one przeznaczone do dostarczania poprawek do luk w zabezpieczeniach dla klienta, który jest już na określonym poziomie wersji pomocniczej. Aktualizacje zabezpieczeń będą zawierać co najmniej jedną poprawkę zabezpieczeń, ale poprawka zabezpieczeń może lub nie może być w składniku lub obciążeniu zainstalowanym na komputerze klienckim. Na przykład możemy naprawić lukę w zabezpieczeniach składników .NET i oznaczylibyśmy ją jako aktualizację zabezpieczeń, ale tak naprawdę nie miałaby żadnego znaczącego wpływu na maszynę klienutową, na których zainstalowano tylko składniki języka C++. Aktualizacje zabezpieczeń mogą również zawierać inne poprawki niezawodności lub inne niezbędne aktualizacje składników. Aktualizacje zabezpieczeń są publikowane w katalogu [Microsoft Update](https://www.catalog.update.microsoft.com/Home.aspx) (MUC) i Windows Server Update Services [,](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus)gdzie są klasyfikowane jako "Aktualizacje zabezpieczeń".
 
* **Aktualizacje funkcji** umożliwiają administratorom IT zaawansowane komputery w organizacji do najnowszej wersji pomocniczej programu Visual Studio 2019. Aktualizacje funkcji dotyczą tylko wersji Visual Studio, które są często spotykane w przedsiębiorstwach, takich jak jednostki SKU Enterprise, Professional i Build Tools. Wszystkie aktualizacje funkcji zostaną opublikowane w katalogu usługi Microsoft Update jako "Pakiety funkcji" i będą dostępne do opcjonalnego ręcznego importowania do usługi Menedżer konfiguracji z katalogu [Microsoft Update.](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog) Aktualizacje funkcji są zbiorcze i będą zawierać dodatkowe poprawki zabezpieczeń dotyczące jakości i poprzednich. Zapoznaj się [z sekcją](#understanding-configuration-options) opcji konfiguracji poniżej, aby uzyskać instrukcje dotyczące sposobu konfigurowania maszyny klienckiej tak, aby pozostawała w planie bazowym obsługi i zapobiegać dostarczaniu aktualizacji funkcji do określonych klientów. 

* **Aktualizacje dotyczące jakości** mają również zastosowanie tylko do wersji Visual Studio, które są często stosowane w przedsiębiorstwach, i zawierają ograniczone, wysoce ukierunkowane i zgodne zmiany poziomu obsługi. Aktualizacje dotyczące jakości nie przejdą klienta do nowszej wersji pomocniczej; Są one przeznaczone do dostarczania poprawek wydajności i niezawodności lub innych niezbędnych aktualizacji składników do klienta, który jest już na określonym poziomie wersji pomocniczej. Aktualizacje dotyczące jakości kumulują się wraz z aktualizacjami zabezpieczeń i w związku z tym będą zawierać poprawki zabezpieczeń tylko wtedy, gdy poprawka zabezpieczeń została już wydana niezależnie. Aktualizacje dotyczące jakości są publikowane w katalogu Microsoft Update jako "Aktualizacje" i są również dostępne do opcjonalnego ręcznego importowania do [Menedżer konfiguracji](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog).

### <a name="decoding-the-titles-of-administrator-updates"></a>Dekodowanie tytułów aktualizacji administratora

Tytuł każdej aktualizacji administratora opisuje zarówno zakres odpowiednich wersji, jak i wynikową wersję aktualizacji.Na przykład

::: moniker range="vs-2017"

* **Visual Studio 2017 wersja od 15.9.0 do 15.9.35** sklasyfikowana jako "Aktualizacja zabezpieczeń" będzie mieć zastosowanie do dowolnej wersji programu Visual Studio 2017 na kliencie w wersjach od 15.9.0 do 15.9.35. Spowoduje to zaktualizowanie tych wersji klienta do wersji 15.9.35.

* Visual Studio 2017 r. z wersji **15.0.0 do 15.9.0** sklasyfikowanych jako "Dodatek Feature Pack" dotyczy wersji od Visual Studio 2017 licencjonowanych do użytku w przedsiębiorstwie na kliencie w całym zakresie wersji produktu od 15.0.0 do 15.9.0. Spowoduje to zaktualizowanie tych wersji klienta do wersji 15.9.0. Zastosowanie tego pakietu funkcji zasadniczo umożliwia klientom otrzymywanie aktualizacji zabezpieczeń. 

* Visual Studio aktualizacji z **wersji 2017 od 15.9.0 do 15.9.37** sklasyfikowanej jako "Aktualizacje" będą stosowane do wersji programu Visual Studio 2017 licencjonowanych do użytku w przedsiębiorstwie na kliencie w wersjach od 15.9.0 do 15.9.37 i zaktualizuje te wersje klienta do wersji 15.9.37. 

::: moniker-end

::: moniker range="vs-2019"

* Visual Studio aktualizacji z **wersji 2019 od 16.7.0 do 16.7.12** sklasyfikowanej jako "Aktualizacja zabezpieczeń" będzie dotyczyć wszystkich wersji programu Visual Studio 2019 na kliencie w wersjach od 16.7.0 do 16.7.12. Spowoduje to zaktualizowanie tych wersji klienta do wersji 16.7.12.  

* Visual Studio 2019 r. z wersji **16.0.0 do 16.9.0** sklasyfikowanych jako "Pakiet funkcji" będzie dotyczyć wersji od Visual Studio 2019 licencjonowanych do użytku w przedsiębiorstwie na kliencie w całym zakresie wersji produktu od 16.0.0 do 16.9.0, Program zaktualizuje te wersje klienta (które nie zostały skonfigurowane do pozostania we wcześniejszym planie bazowym obsługi) do wersji 16.9.0. 

* **Visual Studio 2019 w wersji od 16.8.0 do 16.8.7** sklasyfikowane jako "Aktualizacje" będą stosowane do wersji programu Visual Studio 2019 licencjonowanych do użytku w przedsiębiorstwie na kliencie w wersjach od 16.8.0 do 16.8.7 i zaktualizuje te wersje klienta do wersji 16.8.7. 

::: moniker-end

## <a name="using-configuration-manager-to-deploy-visual-studio-updates"></a>Wdrażanie Menedżer konfiguracji wdrażania Visual Studio aktualizacji

### <a name="understanding-configuration-options"></a>Omówienie opcji konfiguracji

Istnieje kilka opcji konfiguracji, których można użyć do dostosowania aktualizacji administratora programu Visual Studio w taki sposób, aby były zgodne i zgodne z preferencjami i wymaganiami organizacji w zakresie wdrażania. Poniżej wymieniono najbardziej typowe opcje konfiguracji. Aby uzyskać wyczerpującą listę wszystkich obsługiwanych zachowań aktualizacji administratora, zobacz Use [command-line parameters to](../install/use-command-line-parameters-to-install-visual-studio.md) install Visual Studio and pay attention to only those that correspond to the "update" action (Używanie parametrów wiersza polecenia do instalowania i zwracania uwagi tylko na te, które odnoszą się do akcji "aktualizuj").

* **[Rezygnacja z aktualizacji administratora:](../install/enabling-administrator-updates.md#encoding-administrator-intent-on-the-client-machines)** ten klucz rejestru jest wymagany, aby komputer kliencki mógł otrzymywać aktualizacje administratora. Jest to klucz dla całej maszyny, co oznacza, że ma zastosowanie do wszystkich wystąpień Visual Studio zainstalowanych w opakowaniu. 
 
* **Visual Studio** rezygnacji użytkownika: użytkownicy Visual Studio mogą używać oddzielnego klucza rejestru **AdministratorUpdatesOptOut**  na całej maszynie, aby zrezygnować z otrzymywania aktualizacji Visual Studio administratora. Celem tego klucza jest umożliwienie użytkownikowi Visual Studio kontroli nad tym, czy aktualizacje są automatycznie stosowane do maszyny. Aby skonfigurować komputer kliencki tak, aby blokował aktualizacje administratora, ustaw wartość klucza REG_DWORD **AdministratorUpdatesOptOut**   na wartość **1**. Brak klucza lub ustawiona wartość **0** oznacza, że użytkownik Visual Studio chce otrzymywać aktualizacje administratora Visual Studio.

    Pamiętaj, że **klucz AdministratorUpdatesOptOut** do kodowania preferencji użytkownika ma priorytet nad    **kluczem AdministratorUpdatesEnabled,** który koduje intencję   administratora IT. Jeśli dla ustawienia **AdministratorUpdatesOptOut** ustawiono wartość 1, aktualizacja zostanie zablokowana na kliencie, nawet jeśli dla klucza    **AdministratorUpdatesEnabled** ustawiono również wartość ****    **1**.W ramach tej akcji przyjęto założenie, że administratorzy IT mogą uzyskać dostęp i monitorować, którzy deweloperzy zrezygnują z rezygnacji, i że obie strony mogą następnie omówić, których potrzeby są ważniejsze.Administratorzy IT mogą w dowolnym momencie zmienić jeden z tych kluczy.
 
* **Lokalizacja zaktualizowanych bitów produktu:** w większości przypadków maszyny klienckie pobierają zaktualizowane bity produktów z Internetu za pośrednictwem usługi Microsoft CDN. W tym scenariuszu komputery klienckie muszą mieć dostęp do Internetu. Niektóre przedsiębiorstwa ograniczają jednak maszyny klienckie tylko do instalowania i aktualizowania bitów z lokalizacji układu sieci wewnętrznej. Aby upewnić się, że aktualizacje administratora mogą być stosowane przy użyciu zaktualizowanych bitów, które znajdują się w wewnętrznej lokalizacji sieciowej, przed pomyślnym wdrożeniem aktualizacji administratora muszą zostać spełnione następujące warunki: 

  - W pewnym momencie na komputerze klienckim musi być już uruchomiony program inicjujący z tej lokalizacji układu sieciowego. W idealnym przypadku pierwotna instalacja klienta byłaby możliwa przy użyciu programu inicjjącego z układu sieciowego, ale możliwe jest również zainstalowanie aktualizacji przy użyciu zaktualizowanego programu inicjjącego w tej samej lokalizacji sieciowej. Jedna z tych akcji osadzi na komputerze klienckim połączenie z określoną lokalizacją układu.   
  - Lokalizacja układu sieciowego (z którym klient [](../install/update-a-network-installation-of-visual-studio.md) jest połączony) musi zostać zaktualizowana tak, aby zawierała zaktualizowane bity produktów, które mają zostać wdrożone przez aktualizację administratora. 

::: moniker range="vs-2019"

* **Lepkość planu bazowego** obsługi: jak opisano powyżej, aktualizacje funkcji administratora Visual Studio instalacji do bardziej bieżącej wersji pomocniczej produktu. Czasami jednak użytkownicy Visual Studio muszą pozostać na konkretnym stabilnym i bezpiecznym poziomie odniesienia obsługi i chcą kontrolować, kiedy ich maszyny przejdą do bardziej aktualnej wersji pomocniczej. Aby skonfigurować komputer kliencki tak, aby pozostawał w planie bazowym obsługi i ignorował wysyłane do niego niepożądane aktualizacje funkcji administratora, należy utworzyć i ustawić wartość danych **baselineStickinessVersions2019** Reg_SZ na ciąg reprezentujący preferowany punkt odniesienia, na który powinien być przyciągany komputer kliencki i na nim pozostać. Ciąg może zawierać **16.7.0.**  

     Jeśli wartość rejestru jest źle sformułowana, instalacja wszystkich aktualizacji funkcji administratora na maszynie zostanie `BaselineStickinessVersions2019` zablokowana. Pamiętaj, aby zwrócić uwagę na obsługiwane harmonogramy dla aktualizacji [Visual Studio funkcji.](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs) Ponadto, niezależnie od obecności lub wartości klucza, chociaż technicznie jest możliwe zastosowanie aktualizacji funkcji administratora, które osiągają koniec okresu istnienia, nie zalecamy tego, ponieważ nie będą one dostępne, a tym samym potencjalnie `BaselineStickinessVersions2019` niezabezpieczone.

::: moniker-end

* **Wymusz aktualizację,** nawet jeśli Visual Studio jest w użyciu: Visual Studio należy zamknąć przed zainstalowaniem aktualizacji. Jeśli Visual Studio jest otwarty lub używany, instalacja aktualizacji zostanie przerwana. Łatwym sposobem zapewnienia zamknięcia Visual Studio jest skonfigurowanie menedżera potwierdzenia w celu zastosowania aktualizacji bezpośrednio po ponownym uruchomieniu komputera. Możesz również użyć `--force` parametru , aby wymusić zamknięcie Visual Studio. Wymuś zamknięcie Visual Studio może spowodować utratę pracy, dlatego używaj jej z rozwagą. Uruchomienie aktualizacji administratora w domyślnym kontekście systemowym spowoduje zignorowanie flagi , dlatego należy skonfigurować aktualizację administratora do uruchamiania `–-force` w kontekście użytkownika.

### <a name="methods-for-configuring-an-administrator-update"></a>Metody konfigurowania aktualizacji administratora

Istnieją trzy główne metody konfigurowania aktualizacji administratora: klucz rejestru, plik konfiguracji na komputerze klienckim lub modyfikacja samego pakietu Menedżer konfiguracji wdrożenia.   

* **Klucz rejestru:** aktualizacje administratora poszukaj określonych kluczy rejestru w dowolnych standardowych lokalizacjach Visual Studio zgodnie z opisem w części Ustawianie wartości domyślnych [dla wdrożeń przedsiębiorstwa.](../install/set-defaults-for-enterprise-deployments.md) Opcje kontrolowane przez klucze rejestru to takie elementy jak **AdministratorUpdatesOptOut** Reg_DWORD, **AdministratorUpdatesOptOut**   Reg_DWORD i **BaselineStickinessVersions2019** Reg_SZ. Aby utworzyć i ustawić wartość kluczy rejestru, wymagany jest dostęp administratora na komputerze klienckim. 
 
* **Plik konfiguracji:** niektóre ustawienia można zachować na komputerze klienckim w opcjonalnym pliku konfiguracji, co ma zaletę ustawienia go tylko raz i zastosowania go do wszystkich przyszłych aktualizacji administratora. Podejście do plików konfiguracji zachowuje się jak klucz rejestru i dotyczy całej maszyny, co oznacza, że będzie stosowane do wszystkich instalacji Visual Studio na komputerze klienckim. Standardowa lokalizacja pliku konfiguracji to `C:\ProgramData\Microsoft\VisualStudio\updates.config` . Jeśli jednak chcesz użyć innej lokalizacji do przechowywania pliku, możesz to zrobić, tworząc klucz rejestru usługi Reg_SZ o nazwie **UpdateConfigurationFile** i ustawiając wartość tego klucza na ścieżkę pliku konfiguracji. Ten klucz rejestru można umieścić w dowolnej lokalizacji rejestru Visual Studio zgodnie z opisem w tece Ustawianie wartości [domyślnych dla wdrożeń przedsiębiorstwa.](../install/set-defaults-for-enterprise-deployments.md) Jeśli zdecydujesz się dodać wartość rejestru dla niestandardowej lokalizacji pliku konfiguracji, będzie on szukać tego pliku; Jeśli plik nie istnieje, zostanie zgłoszony wyjątek i aktualizacja nie powiedzie się.    
 
     Plik konfiguracji, który jest w formacie JSON, obsługuje opcję , która jest tablicą ciągów oddzielonych przecinkami, określającą więcej przełączników, które można przekazać do Visual Studio `installerUpdateArgs` instalatora. Jeśli zawartość pliku zawiera nieprawidłowe pole lub opcję, która nie jest obsługiwana, aktualizacja nie powiedzie się. Aby uzyskać więcej informacji, zobacz [Use command-line parameters to install Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md).
 
   Oto przykładowy plik konfiguracji: 

   ```
   “installerUpdateArgs” : [“--quiet”, “--noWeb”], 

   “checkPendingReboot” :  “true” 
   ```

* Ręczne aktualizowanie pakietu aktualizacji administratora **w programie SCCM:** parametry wiersza polecenia pojedynczego pakietu aktualizacji administratora w programie SCCM można również zmodyfikować ręcznie.

## <a name="verification-reports-and-troubleshooting-error-codes"></a>Kody błędów weryfikacji, raportów i rozwiązywania problemów

### <a name="determining-that-visual-studio-was-updated"></a>Ustalanie, Visual Studio została zaktualizowana

Aby sprawdzić, czy aktualizacja administratora została zainstalowana poprawnie, można użyć jednej z następujących metod: 

* Na komputerze klienckim uruchom program Visual Studio 2019, wybierz pozycję Informacje o pomocy i sprawdź, czy numer wersji odpowiada ostatniej liczbie w tytule ****   >  **** zamierzonej aktualizacji. 

* Użyj narzędzia **vswhere** na komputerze klienckim, aby zidentyfikować różne wersje Visual Studio na komputerze. Aby uzyskać więcej informacji, zobacz [Narzędzia do wykrywania wystąpień](../install/tools-for-managing-visual-studio-instances.md)Visual Studio zarządzania nimi. 

* Każda próba aktualizacji administracyjnej generuje kilka plików dziennika w katalogu komputera klienckiego, które `%temp%` przechwytują postęp operacji aktualizacji.Posortuj folder według daty i poszukaj plików, które rozpoczynają się odpowiednio od , , , i dla aktualizacji  `dd_updatedriver`  `dd_bootstrapper`  `dd_client`  `dd_setup` administracyjnych, programu inicjjącego, Instalator programu Visual Studio i aparatu   konfiguracji.Sprawdź, czy te pliki dziennika zawierają 0, co oznacza, że aktualizacja została pomyślnie zastosowana. Należy pamiętać, że te pliki dziennika mogą również służyć do weryfikowania, czy plik konfiguracji jest używany. Zapoznaj się z [narzędziem Visual Studio Log Collection Tool,](https://www.microsoft.com/download/details.aspx?id=12493) aby uzyskać więcej informacji.     

### <a name="error-codes-and-conditions"></a>Kody błędów i warunki

>[!IMPORTANT]
> Pamiętaj, Visual Studio należy zamknąć przed zainstalowaniem aktualizacji. Jeśli Visual Studio jest otwarty lub używany, instalacja aktualizacji zostanie anulowana.

Aktualizacje administracyjne mogą zwracać następujące kody powrotne:  

| Kod błędu | Definicja |
|--|:-|
| 0 | Aktualizacja administracyjna została pomyślnie zainstalowana. |
| 1001 | Instalator programu Visual Studio lub powiązany proces konfiguracji jest uruchomiony. Aktualizacja nie jest stosowana. |
| 1002 | Instalator programu Visual Studio jest wstrzymana. Aktualizacja nie jest stosowana. |
| 1003 | Visual Studio jest uruchomiona. Aktualizacja nie jest stosowana. Ten warunek można przesłonić przy użyciu `--force` flagi . |
| 1004 | Nie wykryto Internetu.Aktualizacja nie mogła skontaktować się z lokalizacją internetową, w którym są w nim zaktualizowane pliki. Aktualizacja nie jest stosowana. |
| 1005 | Wartość  **rejestru AdministratorUpdatesEnabled** jest ustawiona na   **0** lub nie jest ustawiona w ogóle. Aktualizacja nie jest stosowana. |
| 1006 | Wartość  **rejestru AdministratorUpdatesOptOut**   jest ustawiona na **1**. Aktualizacja nie jest stosowana. Klucz jest przeznaczony dla komputerów klienckich, które nie powinny być aktualizowane przez administratora. |
| 1007 | Ten Instalator programu Visual Studio nie jest zainstalowany. |
| 1008 | Wartość **rejestru BaselineStickinessVersions2019** nie jest w formacie czytelnym. Wartość rejestru musi zawierać **wszystkie** lub prawidłowe wersje z numerem kompilacji ustawionym na 0 jawnie, na przykład X.Y.0. |
| 3010 | System wymaga ponownego uruchomienia.Aktualizacja może lub nie została zastosowana. Uruchom ponownie komputer i spróbuj ponownie zaktualizować. |
| Inne | Wystąpił błąd podczas próby zastosowania aktualizacji.Aktualizacja nie jest stosowana. |

Aby uzyskać wyczerpującą listę kodów błędów klienta, zobacz [Use command-line parameters to install Visual Studio](use-command-line-parameters-to-install-visual-studio.md). 

## <a name="feedback-and-support"></a>Opinie i pomoc techniczna
[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

Za pomocą następujących metod można przekazać opinię na temat Visual Studio administratorów lub zgłaszania problemów, które mają wpływ na aktualizacje:
* Zapoznaj się ze [wskazówkami Visual Studio rozwiązywania problemów z instalacją i uaktualnianiem.](../install/troubleshooting-installation-issues.md)
* Zadaj pytania społeczności na forum Visual Studio [Q&A.](https://docs.microsoft.com/answers/topics/vs-setup.html)
* Przejdź do strony [Visual Studio pomocy technicznej](https://visualstudio.microsoft.com/vs/support/)i sprawdź, czy problem znajduje się na liście często zadawanych pytań.  Możesz również wybrać przycisk [Link do pomocy technicznej,](https://visualstudio.microsoft.com/vs/support/#talktous) aby uzyskać pomoc w czacie.
* [Przekazać opinię na temat](https://aka.ms/vs/wsus/feedback) funkcji lub zgłosić problem Visual Studio w związku z tym doświadczeniem stosowania aktualizacji administratora.
* Skontaktuj się z kierownikiem ds. technicznych ds. konta w organizacji w firmie Microsoft.

## <a name="see-also"></a>Zobacz też
* [Włączanie aktualizacji administratora](../install/enabling-administrator-updates.md)    
* [Podręcznik administratora programu Visual Studio](../install/visual-studio-administrator-guide.md)
* [Cykl życia produktu i obsługa techniczna programu Visual Studio](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs)
* [Informacje o wersji programu Visual Studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/release-notes)
* [Informacje o wersji programu Visual Studio 2017](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes)
* [Instalowanie programu Visual Studio](../install/install-visual-studio.md)
* [Używanie parametrów wiersza polecenia do instalowania Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md)
* [Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi](../install/tools-for-managing-visual-studio-instances.md)
* [Tworzenie instalacji sieciowej Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
* [Jak zdefiniować ustawienia w pliku odpowiedzi](../install/automated-installation-with-response-file.md)
* [Kontrolowanie aktualizacji wdrożeń Visual Studio sieciowych](../install/controlling-updates-to-visual-studio-deployments.md)
* [Katalog Microsoft Update — często zadawane pytania](https://www.catalog.update.microsoft.com/faq.aspx)
* [Microsoft Endpoint Configuration Manager (SCCM)](https://docs.microsoft.com/mem/configmgr)
* [Importowanie aktualizacji z wykazu firmy Microsoft do Menedżer konfiguracji](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [Windows Server Update Services (WSUS)](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started-windows-server-update-services-wsus)
