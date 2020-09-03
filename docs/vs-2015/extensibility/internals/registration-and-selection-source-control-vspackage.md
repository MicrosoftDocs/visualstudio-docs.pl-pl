---
title: Rejestracja i wybór (pakietu VSPackage kontroli źródła) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 692f2a9f34edd41839179f7229e079ec8e791800
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185819"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Rejestracja i wybór (pakiet VSPackage kontroli kodu źródłowego)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pakietu VSPackage kontroli źródła musi być zarejestrowany, aby można było go udostępnić [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Jeśli zarejestrowano więcej niż jeden pakietu VSPackage kontroli źródła, użytkownik może wybrać pakietu VSPackage do załadowania w odpowiednim czasie. Zobacz [pakietów VSPackage](../../extensibility/internals/vspackages.md) , aby uzyskać więcej informacji o pakietów VSPackage i sposobach ich rejestracji.  
  
## <a name="registering-a-source-control-package"></a>Rejestrowanie pakietu kontroli źródła  
 Pakiet kontroli źródła jest zarejestrowany, aby [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] środowisko mógł je znaleźć i wykonać zapytanie dotyczące obsługiwanych funkcji. Jest to zgodne z schematem ładowania opóźnionego, w którym wystąpienie pakietu jest tworzone tylko wtedy, gdy jego funkcje lub polecenia są wymagane lub zostały jawnie zażądane.  
  
 Pakietów VSPackage umieścić informacje w kluczu rejestru specyficznym dla wersji, HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *x. Y*, gdzie *X* jest głównym numerem wersji, a *Y* to numer wersji pomocniczej. Ta metoda zapewnia możliwość obsługi instalacji równoległej wielu wersji programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Interfejs użytkownika (UI) obsługuje wybór spośród wielu zainstalowanych wtyczek kontroli źródła (za pośrednictwem pakietu adaptera kontroli źródła), a także pakietów VSPackage kontroli źródła. W danym momencie może istnieć tylko jedna wtyczka lub pakietu VSPackage aktywnej kontroli źródła. Jednakże, jak opisano poniżej, IDE umożliwia przełączanie się między wtyczkami kontroli źródła i pakietów VSPackage za pośrednictwem automatycznego mechanizmu zamiany pakietów na podstawie rozwiązania. Aby włączyć ten mechanizm wyboru, należy wykonać pewne wymagania dotyczące części kontroli źródła pakietu VSPackage.  
  
### <a name="registry-entries"></a>Wpisy rejestru  
 Pakiet kontroli źródła wymaga trzech prywatnych identyfikatorów GUID:  
  
- Identyfikator GUID pakietu: jest to główny identyfikator GUID pakietu zawierającego implementację kontroli źródła (o nazwie ID_Package w tej sekcji).  
  
- Identyfikator GUID kontroli źródła: jest to identyfikator GUID dla pakietu VSPackage kontroli źródła używany do rejestrowania z klasą zastępczą kontroli źródła programu Visual Studio i jest również używany jako identyfikator GUID kontekstu interfejsu użytkownika polecenia. Identyfikator GUID usługi kontroli źródła jest zarejestrowany pod identyfikatorem GUID kontroli źródła. W przykładzie identyfikator GUID kontroli źródła jest nazywany ID_SccProvider.  
  
- Identyfikator GUID usługi kontroli źródła: jest to identyfikator GUID usługi prywatnej używany przez program Visual Studio (o nazwie SID_SccPkgService w tej sekcji). Oprócz tego pakiet kontroli źródła musi definiować inne identyfikatory GUID dla pakietów VSPackage, okien narzędzi i tak dalej.  
  
  Następujące wpisy rejestru muszą zostać wykonane przez pakietu VSPackage kontroli źródła:  
  
|Nazwa klucza|Przedpł|  
|--------------|-------------|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\`|(domyślnie) = rg_sz: {ID_SccProvider}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\`|(domyślnie) = rg_sz:\<Friendly name of Package><br /><br /> Usługa = rg_sz: {SID_SccPkgService}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\`|(domyślnie) = rg_sz: #\<Resource ID for localized name><br /><br /> Pakiet = rg_sz: {ID_Package}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Należy zauważyć, że nazwa klucza, `SourceCodeControl` , jest już używana przez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] i nie jest dostępna jako wybór dla \<PackageName> .)|(domyślnie) = rg_sz: {ID_Package}|  
  
## <a name="selecting-a-source-control-package"></a>Wybieranie pakietu kontroli źródła  
 Kilka wtyczek opartych na interfejsie API kontroli źródła i pakietów VSPackage kontroli źródła może być jednocześnie zarejestrowanych. Proces wyboru wtyczki lub pakietu VSPackage kontroli źródła musi zapewnić, że program [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] załaduje wtyczkę lub pakietu VSPackage w odpowiednim czasie i może opóźnić ładowanie zbędnych składników do momentu, gdy są wymagane. Ponadto [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] należy usunąć wszystkie interfejs użytkownika z innych nieaktywnych pakietów VSPackage, w tym elementy menu, okna dialogowe i paski narzędzi, a także wyświetlić interfejs użytkownika dla aktywnego pakietu VSPackage.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ładuje pakietu VSPackage kontroli źródła podczas wykonywania jednej z następujących operacji:  
  
- Rozwiązanie jest otwarte (gdy rozwiązanie jest pod kontrolą źródła).  
  
   W przypadku otwarcia rozwiązania lub projektu pod kontrolą źródła IDE powoduje załadowanie pakietu VSPackage kontroli źródła, który został wyznaczono dla tego rozwiązania.  
  
- Wszystkie polecenia menu pakietu VSPackage kontroli źródła są wykonywane.  
  
  Pakietu VSPackage kontroli źródła powinno ładować wszystkie składniki, których potrzebują, tylko wtedy, gdy rzeczywiście będą używane (nazywane opóźnionym ładowaniem).  
  
### <a name="automatic-solution-based-vspackage-swapping"></a>Automatyczne zamienianie pakietu VSPackage oparte na rozwiązaniach  
 Można ręcznie zamienić pakietów VSPackage kontroli źródła za pomocą [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] okna dialogowego **Opcje** w kategorii **kontroli źródła** . Automatyczne zamienianie pakietów opartych na rozwiązaniach oznacza, że pakiet kontroli źródła, który został wyznaczony dla danego rozwiązania, jest automatycznie ustawiany jako aktywny po otwarciu tego rozwiązania. Każdy pakiet kontroli źródła powinien implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> . [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] obsługuje przełącznik między obydwoma wtyczkami kontroli źródła (implementującymi interfejs API kontroli źródła) i pakietów VSPackage kontroli źródła.  
  
 Pakiet adaptera kontroli źródła jest używany do przełączania do dowolnej wtyczki kontroli źródła z wtyczką opartą na interfejsie API. Proces przełączania do pośredniego pakietu adaptera kontroli źródła i określenia, która Wtyczka kontroli źródła musi być ustawiona jako aktywna lub nieaktywna, jest niewidoczna dla użytkownika. Pakiet adaptera jest zawsze aktywny, gdy jest aktywna jakakolwiek wtyczka do kontroli źródła. Przełączanie między dwoma wtyczkami kontroli źródła polega na załadowaniu i rozładowaniu biblioteki DLL. Przełączenie do pakietu VSPackage kontroli źródła jednak obejmuje współdziałanie z IDE w celu załadowania odpowiedniej pakietu VSPackage.  
  
 Pakietu VSPackage kontroli źródła jest wywoływana, gdy dowolne rozwiązanie zostanie otwarte i klucz rejestru dla pakietu VSPackage znajduje się w pliku rozwiązania. Po otwarciu rozwiązania program [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] znajdzie wartość rejestru i załaduje odpowiednie pakietu VSPackage kontroli źródła. Wszystkie pakietów VSPackage kontroli źródła muszą mieć opisane powyżej wpisy rejestru. Rozwiązanie znajdujące się pod kontrolą źródła jest oznaczone jako skojarzone z konkretną pakietu VSPackage kontroli źródła. Pakietów VSPackage kontroli źródła musi zaimplementować, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> Aby włączyć automatyczne zamienianie pakietu VSPackage oparte na rozwiązaniach.  
  
### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Interfejs użytkownika programu Visual Studio na potrzeby wyboru i przełączania pakietów  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] udostępnia interfejs użytkownika dla pakietu VSPackage kontroli źródła i wybór wtyczki w oknie dialogowym **Opcje** w kategorii **kontroli źródła** . Pozwala użytkownikowi wybrać aktywną wtyczkę lub pakietu VSPackage kontroli źródła. Lista rozwijana zawiera:  
  
- Wszystkie zainstalowane pakiety kontroli źródła  
  
- Wszystkie zainstalowane wtyczki kontroli źródła  
  
- Opcja "Brak", która wyłącza kontrolę kodu źródłowego  
  
  Widoczny jest tylko interfejs użytkownika dla wyboru aktywnej kontroli źródła. Wybór pakietu VSPackage ukrywa interfejs użytkownika dla poprzedniego pakietu VSPackage i pokazuje interfejs użytkownika dla nowego. Aktywna pakietu VSPackage jest wybierana dla poszczególnych użytkowników. Jeśli użytkownik ma wiele kopii [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] otwartych współbieżnie, każdy z nich może potencjalnie korzystać z różnych aktywnych pakietu VSPackage. Jeśli wielu użytkowników jest zalogowanych na tym samym komputerze, każdy użytkownik może mieć osobne wystąpienia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] otwarte, z których każdy ma inne aktywne pakietu VSPackage. W przypadku zamknięcia wielu wystąpień [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] przez użytkownika, pakietu VSPackage kontroli źródła, który był aktywny dla ostatniego otwartego rozwiązania, zmieni się na domyślny pakietu VSPackage kontroli źródła, aby ustawić aktywny przy ponownym uruchomieniu.  
  
  W przeciwieństwie do poprzednich wersji programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , ponowne uruchomienie IDE nie jest już jedynym sposobem przełączania pakietów VSPackage kontroli źródła. Pakietu VSPackage zaznaczenie jest automatyczne. Przełączanie pakietów wymaga uprawnień użytkownika systemu Windows (nie administratora ani użytkownika zaawansowanego).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>   
 [Oferowanych](../../extensibility/internals/source-control-vspackage-features.md)   
 [Tworzenie wtyczki kontroli źródła](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Pakiety VSPackage](../../extensibility/internals/vspackages.md)
