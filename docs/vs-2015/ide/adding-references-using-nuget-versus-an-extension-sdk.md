---
title: Dodawaniem odwołań za pomocą NuGet a Extension SDK | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.toolsoptionspages.nuget_package_manager.general
- vs.toolsoptionspages.nuget_package_manager.package_sources
ms.assetid: 2175581e-83cb-444c-bb52-cc1fca8ea196
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 29590b96a8d8d2ad8fbddaf0d97b9ed55e6aadf2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54763601"
---
# <a name="adding-references-using-nuget-versus-an-extension-sdk"></a>Różnice pomiędzy dodawaniem odwołań za pomocą NuGet a Extension SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz podać pakiet do użycia w ramach projektów programu Visual Studio za pomocą rozszerzenie NuGet w programie Visual Studio albo zestaw software development kit (SDK). Poprzez opisanie podobieństwa i różnice między dwa mechanizmy, w tym temacie mogą pomóc wybrać najlepszy dla zadania.  
  
-   NuGet jest systemem zarządzania pakietami open source, który upraszcza dołączanie biblioteki do rozwiązania projektu. Aby uzyskać więcej informacji, zobacz [Przegląd NuGet](http://go.microsoft.com/fwlink/?LinkId=254877).  
  
-   Zestaw SDK to zbiór plików, które program Visual Studio traktuje jako element jedno odwołanie. **Menadżer odwołań** okno dialogowe wyświetla listę wszystkich zestawów SDK, które są istotne dla projektu, który został otwarty podczas tego okna dialogowego. Po dodaniu zestawu SDK do projektu, możesz uzyskać dostęp do wszystkich zawartość tego zestawu SDK za pomocą funkcji IntelliSense, **przybornika**, projektantów oraz **przeglądarki obiektów**, MSBuild, wdrażania, debugowaniu i pakowaniu. Aby uzyskać więcej informacji na temat zestawów SDK, zobacz [tworzenia Software Development Kit](../extensibility/creating-a-software-development-kit.md).  
  
## <a name="which-mechanism-should-i-use"></a>Jakie działania należy używać?  
 Poniższa tabela ułatwia porównanie odwołujący się funkcji odwołujący się funkcje pakietu nuget zestawu SDK.  
  
|Funkcja|Obsługa zestawu SDK|Informacje o zestawu SDK|Obsługę pakietów NuGet|Informacje o NuGet|  
|-------------|-----------------|---------------|-------------------|-----------------|  
|Mechanizm odwołuje się do jednej jednostki, a następnie wszystkie pliki i funkcje są dostępne.|T|Dodawanie zestawu SDK przy użyciu **Menadżer odwołań** okno dialogowe, a wszystkie pliki i funkcje są dostępne podczas tworzenia przepływu pracy.|T||  
|Program MSBuild używa automatycznie zestawów i plików metadanych (.winmd) Windows.|T|Odwołania do zestawu SDK są automatycznie przekazywane do kompilator.|T||  
|Program MSBuild używa automatycznie pliki .h lub lib.|T|*SDKName*plik .props programu Visual Studio zawiera informacje dotyczące konfigurowania katalogu Visual C++ i tak dalej do automatycznego przez plik .h lub lib.|N||  
|Program MSBuild automatycznie wykorzystuje plików .js lub CSS.|T|W **Eksploratora rozwiązań**, można rozwinąć węzeł odniesienia zestaw SDK języka JavaScript, aby pokazać poszczególne js lub pliki CSS, a następnie wygenerować `<source include/>` tagów, przeciągając tych plików do ich plików źródłowych. Zestaw SDK obsługuje klawisza F5 i automatyczne pakiet Instalatora.|T||  
|Program MSBuild automatycznie doda do formantu w **przybornika**.|T|**Przybornika** można używać zestawów SDK i pokazać kontrolki na kartach, które określisz.|N||  
|Ten mechanizm obsługuje Instalatora programu Visual Studio rozszerzenia (VSIX).|T|VSIX ma specjalne manifestu i logiki, aby utworzyć pakiety zestawu SDK|T|VSIX może być osadzony w inny program instalacyjny.|  
|**Przeglądarki obiektów** wylicza odwołania.|T|**Przeglądarki obiektów** pobiera listę odwołań do zestawów SDK i wylicza je automatycznie.|N||  
|Pliki i łącza automatycznie dodane do **Menadżer odwołań** okno dialogowe (łącza pomocy i tak dalej automatycznego wypełniania)|T|**Menadżer odwołań** okno dialogowe automatycznie wylicza zestawy SDK, oraz łącza pomocy i Lista składników zależnych zestawu SDK.|N|NuGet udostępnia swoje własne **Zarządzaj pakietami NuGet** okno dialogowe.|  
|Ten mechanizm obsługuje wielu architektur.|T|Zestawy SDK może wysłać wiele konfiguracji. Program MSBuild używa odpowiednich plików dla każdej konfiguracji projektu.|N||  
|Ten mechanizm obsługuje wiele konfiguracji.|T|Zestawy SDK może wysłać wiele konfiguracji. W zależności od architektury projektu MSBuild zużywa odpowiednie pliki dla każdej architektury projektu.|N||  
|Mechanizm określić, czy "nie kopia."|T|W zależności od tego, czy pliki są porzucane w folderze \redist lub \designtime można kontrolować, które pliki do skopiowania do pakietu aplikacja odbierająca komunikaty.|N|Możesz deklarować plików do skopiowania w manifeście pakietu.|  
|Zawartość jest wyświetlana w zlokalizowanych plików.|T|Zlokalizowane dokumenty XML w zestawy SDK są automatycznie dołączane do lepszego środowiska czasu projektowania.|N||  
|Program MSBuild obsługuje jednoczesnego używania wielu wersji zestawu SDK.|T|Zestaw SDK obsługuje jednoczesnego używania wielu wersji.|N|To nie odwołuje się do. W czasie, nie może mieć więcej niż jedna wersja plików NuGet w projekcie.|  
|Ten mechanizm obsługuje określenie odpowiednich docelowych struktur, wersji programu Visual Studio i typów projektów.|T|**Menadżer odwołań** okno dialogowe i **przybornika** Pokaż tylko zestawy SDK, które mają zastosowanie do projektu tak, aby użytkownicy mogą łatwiej wybrać odpowiednich zestawów SDK.|T (częściowa Obsługa)|Element przestawny jest platformę docelową. Nie ma żadnych filtrowania w interfejsie użytkownika. W trakcie instalacji może zwrócić błąd.|  
|Mechanizm obsługuje określanie informacje o rejestracji Winmd natywnych.|T|Korelacja plik winmd i plik .dll można określić w SDKManifest.xml.|N||  
|Ten mechanizm obsługuje określanie zależności od innych zestawów SDK.|T|Zestaw SDK powiadomi tylko użytkownika; Użytkownik nadal należy je zainstalować i odwoływać się do nich ręcznie.|T|NuGet pobiera je automatycznie. użytkownik nie jest powiadamiany.|  
|Mechanizm integruje się z usługą [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)] pojęć, takich jak manifest aplikacji i identyfikator Framework.|T|Zestaw SDK musi pomyślnie przejść pojęcia, które są specyficzne dla [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)] pakowania i F5 poprawnie pracować przy użyciu zestawów SDK, które są dostępne w[!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)].|N||  
|Mechanizm integruje się z potoku na potrzeby debugowania aplikacji [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji.|T|Zestaw SDK musi pomyślnie przejść [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)]-określonych tak, aby tworzenie pakietów i F5 działać poprawnie, przez zestawy SDK dostępne w [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)].|T|Zawartość NuGet staje się częścią projektu. Nie szczególną ostrożność F5 jest wymagana.|  
|Mechanizm integruje się z manifesty aplikacji.|T|Zestaw SDK musi pomyślnie przejść [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)]-określonych tak, aby tworzenie pakietów i F5 działać poprawnie, przez zestawy SDK dostępne w [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)].|T|Zawartość NuGet staje się częścią projektu. Nie szczególną ostrożność F5 jest wymagana.|  
|Mechanizm wdraża pliki-reference (na przykład wdrożyć struktury testowej, na których można uruchomić testy z [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji).|T|Jeśli usuniesz pliki w folderze \redist pliki są automatycznie wdrażane.|T||  
|Mechanizm automatycznie dodaje zestawów SDK dla platformy w programie Visual Studio IDE.|T|Jeśli usuniesz [!INCLUDE[win8](../includes/win8-md.md)] zestawu SDK lub SDK Windows Phone w określonej lokalizacji przy użyciu określonego układu, zestaw SDK automatycznie jest zintegrowany ze wszystkimi funkcjami programu Visual Studio.|N||  
|Ten mechanizm obsługuje maszyny dewelopera czyste. (Oznacza to, że instalacja nie jest wymagana i będzie działać proste pobieranie z kontroli kodu źródłowego.)|N|Ponieważ można odwoływać się do zestawu SDK, należy zaewidencjonować rozwiązanie i zestawu SDK oddzielnie. Możesz sprawdzić w zestawie SDK z dwóch lokalizacji rejestru innego niż domyślny, z których program MSBuild wykonuje iteracje zestawów SDK (Aby uzyskać więcej informacji, zobacz [tworzenia Software Development Kit](../extensibility/creating-a-software-development-kit.md)). Alternatywnie Jeśli niestandardowej lokalizacji składa się z zestawów SDK, można określić następujący kod w pliku projektu:<br /><br /> `<PropertyGroup>    <SDKReferenceDirectoryRoot>C:\MySDKs</SDKReferenceDirectoryRoot>   </PropertyGroup>`<br /><br /> Następnie sprawdź zestawy SDK do tej lokalizacji.|T|Można wyewidencjonować rozwiązania, a program Visual Studio od razu rozpoznaje i działa na plikach.|  
|Możesz dołączyć dużą społeczność istniejących autorom pakietów.|Brak|Społeczność jest nowa.|T||  
|Możesz dołączyć dużą społeczność istniejących konsumentów pakietu.|Brak|Społeczność jest nowa.|T||  
|Możesz dołączyć ekosystemem partnerów (galerie niestandardowe, repozytoriów i tak dalej).|Brak|Dostępne repozytoriów obejmują galerii w programie Visual Studio, Microsoft Download Center, i [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)].|T||  
|Mechanizm integruje się z serwerów kompilacji ciągłej integracji, zarówno dla operacji tworzenia pakietu i użycia.|T|Zestaw SDK musi pomyślnie przejść zaewidencjonowanej w lokalizacji (właściwość SDKReferenceDirectoryRoot) w wierszu polecenia do programu MSBuild.|T||  
|Ten mechanizm obsługuje obie wersje pakietu stabilne i wersji wstępnej.|T|Zestaw SDK obsługuje dodawanie odwołania do wielu wersji.|T||  
|Ten mechanizm obsługuje automatyczne aktualizowanie zainstalowanych pakietów.|T|Jeśli dostarczane jako VSIX lub jej część automatyczne aktualizacje programu Visual Studio, zestaw SDK zapewnia automatyczne powiadomienia.|T||  
|Mechanizm znajduje się plik .exe autonomicznej do tworzenia i używania pakietów.|T|Zestaw SDK zawiera MSBuild.exe.|T||  
|Pakietów można sprawdzić w taki sposób, w ramach kontroli wersji.|T|Nie można zaewidencjonować niczego poza węzeł dokumentów, co oznacza, że zestawów SDK rozszerzeń mogą nie zostać zaewidencjonowane. Rozmiar zestawu SDK rozszerzeń, może być duża.|T||  
|Interfejs programu PowerShell umożliwia tworzenie i korzystanie z pakietów.|T (zużycie), N (Tworzenie)|Nie narzędzia do tworzenia zestawu SDK. Użycie jest wykonywanie programu MSBuild w wierszu polecenia.|T||  
|Pakiet symboli służy do obsługi debugowania.|T|Jeśli usuniesz pliki .pdb w zestawie SDK, pliki Pobierz pobierane automatycznie.|T||  
|Ten mechanizm obsługuje pakiet manager jest aktualizowany automatycznie.|Brak|Zestaw SDK pobiera zmian za pomocą narzędzia MSBuild.|T||  
|Ten mechanizm obsługuje lekki format manifestu.|T|SDKManifest.xml obsługuje wiele atrybutów, ale zazwyczaj konieczne jest niewielki ułamek.|T||  
|Ten mechanizm jest dostępna dla wszystkich wersji programu Visual Studio.|T|Zestaw SDK obsługuje wszystkie wersje programu Visual Studio z programu Visual Studio Express przy użyciu [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)].|T|NuGet obsługuje wszystkich wersji programu Visual Studio Express się za pośrednictwem [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)].|  
|Ten mechanizm jest dostępna dla wszystkich typów projektów.|N|Zestaw SDK obsługuje [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacje, począwszy od [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|N|Możesz przejrzeć listę dozwolonych projektów.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)
