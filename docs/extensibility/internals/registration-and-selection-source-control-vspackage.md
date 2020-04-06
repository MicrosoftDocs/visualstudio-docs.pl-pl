---
title: Rejestracja i wybór (Kontrola źródła VSPackage) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 973eb19916a737dfa775fe79ee62cb3d11fe0123
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705718"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Rejestracja i wybór (pakiet VSPackage kontroli kodu źródłowego)
Formant źródła VSPackage musi być zarejestrowany, aby udostępnić go na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Jeśli zarejestrowana jest więcej niż jedna kontrolka źródła VSPackage, użytkownik może wybrać, który pakiet VSPackage należy załadować w odpowiednim czasie. Zobacz [VSPackages](../../extensibility/internals/vspackages.md) aby uzyskać więcej informacji na temat vspackages i jak je zarejestrować.

## <a name="registering-a-source-control-package"></a>Rejestrowanie pakietu kontroli źródła
 Pakiet kontroli źródła jest zarejestrowany, dzięki czemu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowisko może go znaleźć i kwerendy dla jego obsługiwanych funkcji. Jest to zgodne ze schematem ładowania opóźnienia, w którym wystąpienie pakietu jest tworzone tylko wtedy, gdy jego funkcje lub polecenia są wymagane lub są wymagane jawnie.

 Program VSPackages umieszcza informacje w kluczu rejestru specyficznym dla wersji,\\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio*X.Y*, gdzie *X* jest głównym numerem wersji, a *Y* jest numerem wersji pomocniczej. Praktyka ta zapewnia możliwość obsługi instalacji side-by-side wielu wersjach programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Interfejs [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] użytkownika (UI) obsługuje wybór spośród wielu zainstalowanych wtyczek sterujących źródłem (za pośrednictwem pakietu adaptera kontroli źródła) oraz vspackages kontroli źródła. W pewnym momencie może istnieć tylko jedna wtyczka kontroli aktywnego źródła lub VSPackage. Jednak jak opisano poniżej, IDE umożliwia przełączanie między wtyczkami kontroli źródła i VSPackages za pośrednictwem mechanizmu automatycznego przełączania pakietów opartych na rozwiązaniu. Istnieją pewne wymagania ze strony kontroli źródła VSPackage, aby włączyć ten mechanizm wyboru.

### <a name="registry-entries"></a>Wpisy rejestru
 Pakiet kontroli źródła wymaga trzech prywatnych identyfikatorów GUID:

- Identyfikator GUID pakietu: Jest to główny identyfikator GUID dla pakietu, który zawiera implementację kontroli źródła (o nazwie ID_Package w tej sekcji).

- Identyfikator GUID kontroli źródła: Jest to identyfikator GUID dla formantu źródłowego VSPackage używanego do rejestrowania się w wycinku kontroli źródła programu Visual Studio i jest również używany jako identyfikator GUID kontekstu interfejsu użytkownika polecenia. Identyfikator GUID usługi kontroli źródła jest zarejestrowany pod identyfikatorem GUID kontroli źródła. W tym przykładzie identyfikator GUID kontroli źródła jest nazywany ID_SccProvider.

- Identyfikator GUID usługi kontroli źródła: jest to identyfikator GUID usługi prywatnej używany przez program Visual Studio (o nazwie SID_SccPkgService w tej sekcji). Oprócz tego pakiet kontroli źródła musi zdefiniować inne identyfikatory GUID dla VSPackages, okna narzędzi i tak dalej.

  Następujące wpisy rejestru muszą być dokonywane przez formant źródła VSPackage:

| Nazwa klucza | Wpisy |
| - | - |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\` | (domyślnie) = rg_sz:{ID_SccProvider} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\` | (domyślnie) = rg_sz:\<Przyjazna nazwa pakietu><br /><br /> Usługa = rg_sz:{SID_SccPkgService} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\` | (domyślnie) = rg_sz:#\<Identyfikator zasobu dla zlokalizowanych nazw><br /><br /> Pakiet = rg_sz:{ID_Package} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Należy zauważyć, że `SourceCodeControl`nazwa klucza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , jest już używany \<przez i nie jest dostępny jako wybór dla PackageName>.) | (domyślnie) = rg_sz:{ID_Package} |

## <a name="selecting-a-source-control-package"></a>Wybieranie pakietu kontroli źródła
 Kilka wtyczek interfejsu API opartych na usłudze Source Control i formancie źródłowym VSPackages mogą być jednocześnie zarejestrowane. Proces wybierania wtyczki formantu źródła lub VSPackage musi upewnić się, że [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ładuje wtyczkę lub VSPackage w odpowiednim czasie i może odroczyć ładowanie niepotrzebnych składników, dopóki nie są wymagane. Ponadto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] należy usunąć wszystkie interfejsu użytkownika z innych nieaktywnych VSPackages, w tym elementy menu, okna dialogowe i paski narzędzi i wyświetlić interfejsu użytkownika dla aktywnego VSPackage.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ładuje formant źródła VSPackage, gdy wykonywana jest dowolna z następujących operacji:

- Rozwiązanie jest otwarte (gdy rozwiązanie jest pod kontrolą źródła).

   Po otwarciu rozwiązania lub projektu pod kontrolą źródła IDE powoduje, że formant źródła VSPackage, który został wyznaczony dla tego rozwiązania do załadowania.

- Wykonywane są polecenia menu formantu źródłowego VSPackage.

  Formant źródła VSPackage należy załadować wszystkie składniki, których potrzebuje tylko wtedy, gdy są one rzeczywiście będzie używany (inaczej znany jako opóźnione ładowanie).

### <a name="automatic-solution-based-vspackage-swapping"></a>Automatyczne zamienianie vspackage oparte na rozwiązaniach
 Formant źródła można ręcznie zamienić za [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pomocą okna dialogowego **Opcje** w kategorii **Kontrola źródła.** Automatyczna zamiana pakietów oparta na rozwiązaniach oznacza, że pakiet kontroli źródła, który został wyznaczony dla określonego rozwiązania, jest automatycznie ustawiany na aktywny po otwarciu tego rozwiązania. Każdy pakiet kontroli <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> źródła <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>powinien zostać zaimplementowany i . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]obsługuje przełącznik między wtyczkami kontroli źródła (implementacja interfejsu API wtyczki kontroli źródła) i kontrolą źródła VSPackages.

 Pakiet adaptera kontroli źródła służy do przełączania się do dowolnej wtyczki opartej na interfejsie API w usłudze Source Control Plug-in. Proces przełączania na pośredni pakiet karty kontroli źródła i określania, która wtyczka kontroli źródła musi być ustawiona na aktywna lub nieaktywna, jest nieprzejrzysta dla użytkownika. Pakiet karty jest zawsze aktywny, gdy aktywna jest dowolna wtyczka kontroli źródła. Przełączanie między dwiema wtyczkami kontroli źródła oznacza zwykłe ładowanie i rozładunek biblioteki DLL wtyczki. Przełączanie do formantu źródła VSPackage, jednak obejmuje interakcję z IDE załadować odpowiednie VSPackage.

 Formant źródła VSPackage jest wywoływana, gdy każde rozwiązanie jest otwarty i klucz rejestru dla VSPackage jest w pliku rozwiązania. Po otwarciu rozwiązania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] znajduje wartość rejestru i ładuje odpowiednią kontrolę źródła VSPackage. Wszystkie vspackages kontroli źródła musi mieć wpisy rejestru opisane powyżej. Rozwiązanie, które jest pod kontrolą źródła jest oznaczony jako skojarzone z określonego źródła kontroli VSPackage. Kontrola źródła VSPackages <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> należy zaimplementować, aby włączyć automatyczne rozwiązanie oparte vspackage wymiany.

### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Interfejs użytkownika programu Visual Studio do wyboru i przełączania pakietów
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]udostępnia interfejs użytkownika dla kontroli źródła VSPackage i wybór wtyczki w oknie dialogowym **Opcje** w kategorii **Kontrola źródła.** Umożliwia użytkownikowi wybranie aktywnej wtyczki formantu źródła lub VSPackage. Lista rozwijana obejmuje:

- Wszystkie zainstalowane pakiety kontroli źródła

- Wszystkie zainstalowane wtyczki sterowania źródłem

- Opcja "brak", która wyłącza kontrolę kodu źródłowego

  Widoczny jest tylko interfejs użytkownika dla wyboru kontroli aktywnego źródła. VsPackage zaznaczenie ukrywa interfejsu użytkownika dla poprzedniego VSPackage i pokazuje interfejsu użytkownika dla nowego. Aktywny VSPackage jest wybierany na podstawie dla użytkownika. Jeśli użytkownik ma wiele [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kopii otwartych jednocześnie, każdy z nich może potencjalnie użyć innego aktywnego VSPackage. Jeśli wielu użytkowników są zalogowani na tym samym komputerze, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] każdy użytkownik może mieć oddzielne wystąpienia otwarte, każdy z innym aktywnym VSPackage. Gdy wiele wystąpień [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] są zamknięte przez użytkownika, formant źródła VSPackage, który był aktywny dla ostatniego otwartego rozwiązania staje się domyślną formantem źródła VSPackage, aby ustawić aktywne przy ponownym uruchomieniu.

  W przeciwieństwie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]do poprzednich wersji, ponowne uruchomienie IDE nie jest już jedynym sposobem przełączania kontroli źródła VSPackages. Wybór vspackage jest automatyczny. Przełączanie pakietów wymaga uprawnień użytkownika systemu Windows (nie administratora lub użytkownika zaaukajek).

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
- [Funkcje](../../extensibility/internals/source-control-vspackage-features.md)
- [Tworzenie wtyczki kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Pakiety VSPackage](../../extensibility/internals/vspackages.md)
