---
title: Rejestracja i wybór (pakiet VSPackage kontroli) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e86b6163a581a2bd7233596b3871a82f356b3ca
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54988769"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Rejestracja i wybór (pakiet VSPackage kontroli kodu źródłowego)
Pakietu VSPackage musi być zarejestrowana do udostępnienia go do kontroli źródła [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Jeśli nie zarejestrowano więcej niż jeden formant źródła pakietu VSPackage, użytkownik może wybrać VSPackage, który można załadować w odpowiednim czasie. Zobacz [pakietów VSPackage](../../extensibility/internals/vspackages.md) więcej informacji na temat pakietów VSPackage i jak je zarejestrować.  
  
## <a name="registering-a-source-control-package"></a>Rejestrowanie pakietu kontroli źródła  
 Pakiet kontroli źródła jest zarejestrowany, aby [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowiska można znaleźć go i zapytań obsługiwanych funkcji. To jest zgodna z schemat ładowanych z opóźnieniem, w której tworzone jest wystąpienie pakietu, tylko wtedy, gdy jego funkcje polecenia są wymagane lub są żądane w sposób jawny.  
  
 Pakietów VSPackage umieść informacje w kluczu rejestru specyficzny dla wersji, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, gdzie *X* to główny numer wersji i *Y* jest pomocniczy numer wersji. Praktyka ta zapewnia możliwość aby możliwa była instalacja side-by-side wielu wersji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Interfejsu użytkownika (UI) obsługuje wybór spośród wielu źródła zainstalowanych wtyczek kontroli (za pośrednictwem pakietu karty kontroli źródła), a także kontroli źródła pakietów VSPackage. Może istnieć tylko jeden wtyczka do kontroli źródła active lub pakietu VSPackage w danym momencie. Jednak zgodnie z poniższym opisem IDE zezwala na przełączanie między wtyczek kontroli kodu źródłowego i pakietów VSPackage przy użyciu automatycznego oparte na rozwiązaniach zamianę pakietów mechanizmu. Istnieją pewne wymagania rekompensatę pakietu VSPackage kontroli źródła, aby włączyć ten mechanizm zaznaczania.  
  
### <a name="registry-entries"></a>Wpisy rejestru  
 Pakiet kontrolki źródła wymaga trzech prywatnych identyfikatorów GUID:  
  
- Identyfikator GUID pakietu: Jest to główny identyfikator GUID pakietu, który zawiera implementację kontroli źródła (nazywane ID_Package w tej sekcji).  
  
- Identyfikator GUID kontrolki źródła To jest identyfikator GUID dla pakietu VSPackage używane do rejestrowania w usłudze Visual Studio wycinka kontroli źródła do kontroli źródła i jest również używane jako kontekst interfejsu użytkownika poleceń identyfikatora GUID. Identyfikator GUID usługi kontroli źródła jest zarejestrowany pod kontrolą źródła, identyfikatora GUID. W tym przykładzie identyfikator GUID do kontroli źródła jest wywoływana ID_SccProvider.  
  
- Identyfikator GUID usługi kontroli źródła: To jest usługa prywatny identyfikator GUID używany przez program Visual Studio (nazywanych SID_SccPkgService w tej sekcji). Oprócz tego pakietu kontroli źródła trzeba zdefiniować inne identyfikatory GUID pakietów VSPackage, okien narzędzi i tak dalej.  
  
  Przez kontrolę źródła pakietu VSPackage przeprowadza się następujące wpisy rejestru:  
  
| Nazwa klucza | Wpisy |
| - | - |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\` | (ustawienie domyślne) = rg_sz: {ID_SccProvider} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\` | (ustawienie domyślne) = rg_sz:\<przyjazną nazwę pakietu ><br /><br /> Usługa = rg_sz: {SID_SccPkgService} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\` | (ustawienie domyślne) = rg_sz: #\<identyfikator zasobu dla zlokalizowana nazwa ><br /><br /> Pakiet = rg_sz: {ID_Package} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Należy pamiętać, że nazwa klucza `SourceCodeControl`, jest już używany przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i nie jest dostępna jako opcja dla \<Nazwa_pakietu >.) | (ustawienie domyślne) = rg_sz: {ID_Package} |
  
## <a name="selecting-a-source-control-package"></a>Wybranie pakietów kontroli źródła  
 Kilka oparte na interfejsie API wtyczki kontroli źródła wtyczek i pakietów VSPackage mogą być jednocześnie zarejestrowane kontroli źródła. Proces wyboru wtyczka do kontroli źródła lub pakietu VSPackage musi zapewnić, że [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ładowania dodatku typu plug-in lub pakietu VSPackage w odpowiednim czasie i może odroczyć ładowania składników niepotrzebne, dopóki nie są one wymagane. Ponadto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usunąć wszystkie interfejsu użytkownika z innych nieaktywne pakietów VSPackage, łącznie z elementami menu, okna dialogowe i paski narzędzi i wyświetlić interfejs użytkownika dla aktywnego pakietu VSPackage.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ładuje pakietu VSPackage kontroli źródła, gdy przeprowadzane jest jednym z następujących czynności:  
  
- Rozwiązanie jest otwierane (Jeśli rozwiązanie podlega kontroli źródła).  
  
   Po otwarciu rozwiązania lub projektu objętego kontrolą źródła, IDE powoduje, że pakietu VSPackage, który został wybrany dla tego rozwiązania, należy załadować do kontroli źródła.  
  
- Dowolne polecenia menu kontroli źródła pakietu VSPackage są wykonywane.  
  
  Kontroli źródła pakietu VSPackage powinny zostać załadowane wszystkie składniki potrzebne tylko wtedy, gdy są naprawdę mają zostać użyte (w przeciwnym razie nazywane opóźnionego ładowania).  
  
### <a name="automatic-solution-based-vspackage-swapping"></a>Trwa zamienianie automatyczne oparte na rozwiązaniach pakietu VSPackage  
 Można ręcznie wymienić kontroli źródła pakietów VSPackage przy użyciu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **opcje** okno dialogowe, w obszarze **kontroli źródła** kategorii. Automatyczne rozwiązanie pakiet zamianę oznacza, że pakiet do kontroli źródła, który zostały wyznaczone dla danego rozwiązania jest automatycznie ustawiana na aktywny, po otwarciu tego rozwiązania. Należy wdrożyć każdy pakiet kontrolki źródła <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsługuje przełącznik między obiema źródła wtyczek kontroli (Implementowanie API wtyczki kontroli źródła) i pakietów VSPackage kontroli źródła.  
  
 Jest używany pakiet karty kontroli źródła, aby przełączyć się do żadnych interfejsów API wtyczki kontroli źródła na podstawie wtyczki. Musi być równa proces przełączanie do pośredniego pakietu karty kontroli źródła i określanie, które wtyczka do kontroli źródła, aktywne lub nieaktywne jest niewidoczne dla użytkownika. Pakiet karty jest zawsze aktywny, gdy wtyczka kontroli źródła jest aktywny. Przełączanie między dwiema kwotami wtyczki kontroli źródła można po prostu ładowanie i zwalnianie biblioteki DLL dodatku plug-in. Jednak przełączenie do kontroli źródła pakietu VSPackage, wymaga interakcji z IDE, które można załadować odpowiedniego pakietu VSPackage.  
  
 Kontroli źródła pakietu VSPackage jest wywoływana, gdy żadne rozwiązanie jest otwarta, a klucz rejestru dla pakietu VSPackage znajduje się w pliku rozwiązania. Po otwarciu rozwiązania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] znajduje wartość rejestru i ładuje kontroli źródła odpowiedniego pakietu VSPackage. Wszystkie kontroli źródła pakietów VSPackage musi mieć wpisy rejestru opisanych powyżej. Rozwiązanie, które jest pod kontrolą źródła jest oznaczona jako skojarzeniem go z kontroli źródła określonego pakietu VSPackage. Musisz zaimplementować pakietów VSPackage kontroli źródła <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> umożliwiające automatyczne oparte na rozwiązaniach pakietu VSPackage zamianę.  
  
### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Program Visual Studio interfejsu użytkownika dla wybór pakietów i przełączania  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] udostępnia interfejs użytkownika dla kontroli źródła pakietu VSPackage i wybór wtyczki w **opcje** okno dialogowe, w obszarze **kontroli źródła** kategorii. Umożliwia użytkownikowi wybranie wtyczka do kontroli źródła active lub pakietu VSPackage. Zawiera listy rozwijanej:  
  
- Wszystkie zainstalowane pakietów kontroli kodu źródłowego  
  
- Wszystkie zainstalowane wtyczek kontroli kodu źródłowego  
  
- Opcję "Brak", która wyłącza kontroli kodu źródłowego  
  
  Tylko w interfejsie użytkownika dla wybranego formantu aktywne źródłowe są widoczne. Wybór pakietu VSPackage ukrycie interfejsu użytkownika dla poprzedniego pakietu VSPackage i pokazuje interfejsu użytkownika dla nowego. Aktywne pakietu VSPackage wybranego na poszczególnych użytkowników. Jeśli użytkownik ma wiele kopii [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Otwórz jednocześnie, każdy z nich mogą za pomocą inną aktywnych pakietu VSPackage. Jeśli wielu użytkowników jest zalogowany na tym samym komputerze, każdy użytkownik może mieć różne wystąpienia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Otwórz każdy z inną aktywnych pakietu VSPackage. Jeśli wiele wystąpień [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] są zamknięte przez użytkownika, do kontroli źródła pakietu VSPackage, który był aktywny dla ostatniego, otwórz rozwiązanie staje się domyślne do kontroli źródła pakietu VSPackage, należy ustawić aktywny na ponowne uruchomienie.  
  
  W przeciwieństwie do poprzednich wersji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ponowne uruchamianie środowiska IDE nie jest już jedynym sposobem, aby przełączyć kontroli źródła pakietów VSPackage. Wybór pakietu VSPackage odbywa się automatycznie. Przełączanie pakietów wymaga uprawnień użytkownika Windows (nie Administrator lub użytkownik zaawansowany).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>   
 [Funkcje](../../extensibility/internals/source-control-vspackage-features.md)   
 [Tworzenie wtyczki kontroli źródła](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Pakiety VSPackage](../../extensibility/internals/vspackages.md)