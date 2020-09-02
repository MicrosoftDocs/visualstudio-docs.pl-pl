---
title: Rejestrowanie typu projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 63e0140b752adda02aba6126580ec08ee1f7536a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64837603"
---
# <a name="registering-a-project-type"></a>Rejestrowanie typu projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podczas tworzenia nowego typu projektu należy utworzyć wpisy rejestru, które umożliwiają [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] rozpoznawanie i współpracują z typem projektu. Te wpisy rejestru są zwykle tworzone przy użyciu pliku skryptu rejestru (. RGS).  
  
 W poniższym przykładzie instrukcje z rejestru zawierają domyślne ścieżki i dane, a następnie tabelę zawierającą wpisy ze skryptu rejestru dla każdej instrukcji. Tabele zawierają wpisy skryptów i dodatkowe informacje dotyczące instrukcji.  
  
> [!NOTE]
> Poniższe informacje rejestru mają być przykładem typu i celów wpisów w skryptach rejestru, które będą zapisywane w celu zarejestrowania typu projektu. Rzeczywiste wpisy i ich zastosowania mogą się różnić w zależności od określonych wymagań typu projektu. Należy przejrzeć dostępne przykłady, aby znaleźć je, które są ściśle podobne do typu opracowywanego projektu, a następnie przejrzeć skrypt rejestru dla tego przykładu.  
  
 Poniższe przykłady pochodzą z HKEY_CLASSES_ROOT.  
  
## <a name="example"></a>Przykład  
  
```  
\.figp  
   @="FigPrjFile"  
   "Content Type"="text/plain"  
\.figp\ShellNew  
   "NullFile"=""  
\FigPrjFile  
   @="Figure Project File"  
\DefaultIcon  
   @="<Visual Studio SDK installation path>\\9.0VSIntegration\\SomeFolder\\FigPkgs\\FigPrj\\Debug\\FigPrj.dll,-206"  
\shell\open  
   @="&Open in Visual Studio"  
\shell\open\command  
   @="devenv.exe \"%1\""  
```  
  
|Nazwa|Typ|Dane|Opis|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrjFile`|Nazwa i Opis plików typu projektu, które mają rozszerzenie. figp.|  
|`Content Type`|REG_SZ|`Text/plain`|Typ zawartości dla plików projektu.|  
|`NullFile`|REG_SZ|`Null`||  
|`@`|REG_SZ|`%MODULE%,-206`|Domyślna ikona użyta dla projektu tego typu. Instrukcja% MODULE% została ukończona w rejestrze do domyślnej lokalizacji biblioteki DLL typu projektu.|  
|`@`|REG_SZ|`&Open in Visual Studio`|Domyślna aplikacja, w której zostanie otwarty ten typ projektu.|  
|`@`|REG_SZ|`devenv.exe "%1"`|Domyślne polecenie, które zostanie uruchomione, gdy zostanie otwarty projekt tego typu.|  
  
 Poniższe przykłady pochodzą z HKEY_LOCAL_MACHINE i znajdują się w rejestrze w kluczu [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages].  
  
## <a name="example"></a>Przykład  
  
```  
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)  
   @="FigPrj Project Package"  
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"  
   "CompanyName"="Microsoft"  
   "ProductName"="Figure Project Sample"  
   "ProductVersion"="9.0"  
   "MinEdition"="professional"  
   "ID"=dword:00000001  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\SatelliteDLL  
   "DllName"="FigPrjUI.dll"  
   "Path"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\Debug\\"  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\Automation  
   "FigProjects"=""  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\AutomationEvents  
   "FigProjectsEvents"="Returns the FigProjectsEvents Object"  
   "FigProjectItemsEvents"="Returns the FigProjectItemsEvents Object"  
```  
  
|Nazwa|Typ|Dane|Opis|  
|----------|----------|----------|-----------------|  
|`@` Wartooć|REG_SZ|`FigPrj Project VSPackage`|Nazwa lokalizowalna tego zarejestrowanego pakietu VSPackage (typ projektu).|  
|`InprocServer32`|REG_SZ|`%MODULE%`|Ścieżka do biblioteki DLL typu projektu. IDE ładuje tę bibliotekę DLL i przekazuje identyfikator CLSID pakietu VSPackage do programu, aby `DllGetClassObject` uzyskać <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> do konstruowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> obiektu.|  
|`CompanyName`|REG_SZ|`Microsoft`|Nazwa firmy, która opracowała typ projektu.|  
|`ProductName`|REG_SZ|`Figure Project Sample`|Nazwa typu projektu.|  
|`ProductVersion`|REG_SZ|`9.0`|Numer wersji typu projektu.|  
|`MinEdition`|REG_SZ|`professional`|Zarejestrowana wersja pakietu VSPackage.|  
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Klucz ładowania pakietu dla projektu pakietu VSPackage. Klucz jest weryfikowany, gdy projekt zostanie załadowany po rozpoczęciu środowiska.|  
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Nazwa pliku satelickiej biblioteki DLL, która zawiera zlokalizowane zasoby dla typu projektu.|  
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Ścieżka do satelickiej biblioteki DLL.|  
|`FigProjectsEvents`|REG_SZ|Zobacz instrukcję Value.|Określa ciąg tekstowy zwracany dla tego zdarzenia automatyzacji.|  
|`FigProjectItemsEvents`|REG_SZ|Zobacz instrukcję Value.|Określa ciąg tekstowy zwracany dla tego zdarzenia automatyzacji.|  
  
 Wszystkie poniższe przykłady znajdują się w rejestrze w kluczu [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Przykład  
  
```  
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)  
   @="FigPrj Project"  
   "DisplayName"="#2"  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"  
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"  
   "DisplayProjectFileExtensions"="#3"  
   "PossibleProjectExtensions"="figp"  
   "DefaultProjectExtension"=".figp"  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)  
   @="#4"  
   "CommonOpenFilesFilter"=dword:00000000  
   "CommonFindFilesFilter"=dword:00000000  
   "NotAddExistingItemFilter"=dword:00000000  
   "FindInFilesFilter"=dword:00000000  
   "NotOpenFileFilter"=dword:00000000  
   "SortPriority"=dword:000003e8  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\2  
      (Folder 2 contains settings for Find in Files filters.)  
   @="#5"  
   "CommonOpenFilesFilter"=dword:00000000  
   "CommonFindFilesFilter"=dword:00000000  
   "NotAddExistingItemFilter"=dword:00000001  
   "FindInFilesFilter"=dword:00000001  
   "NotOpenFileFilter"=dword:00000000  
   "SortPriority"=dword:000003e8  
\{C061DB26-5833-11D2-96F5-000000000000}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (Second GUID indicates the registered project type for the Add Items templates.)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|Nazwa|Typ|Dane|Opis|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrj Project`|Domyślna nazwa projektów tego typu.|  
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|Identyfikator zasobu, który ma zostać pobrany z satelickiej biblioteki DLL zarejestrowanej w pakietach.|  
|`Package`|REG_SZ|`%CLSID_Package%`|Identyfikator klasy pakietu VSPackage zarejestrowanych w pakietach.|  
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Domyślna ścieżka do plików szablonów projektu. Są to pliki wyświetlane przez nowy szablon projektu.|  
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Domyślna ścieżka do plików szablonu elementu projektu. Są to pliki wyświetlane przez szablon Dodaj nowy element.|  
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Umożliwia środowisku IDE zaimplementowanie okna dialogowego **Otwórz** .|  
|`PossibleProjectExtensions`|REG_SZ|`figp`|Używane przez IDE do określenia, czy otwierany projekt jest obsługiwany przez ten typ projektu (fabryka projektów). Format dla więcej niż jednego wpisu jest listą rozdzielaną średnikami. Na przykład "VDPROJ; VDP".|  
|`DefaultProjectExtension`|REG_SZ|`.figp`|Używany przez IDE jako domyślne rozszerzenie nazwy pliku dla operacji Zapisz jako.|  
|`Filter Settings`|REG_DWORD|Różne, zobacz instrukcje i komentarze w poniższej tabeli.|Te ustawienia służą do ustawiania różnych filtrów do wyświetlania plików w oknach dialogowych interfejsu użytkownika.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Identyfikator zasobu dla szablonów dodawania elementów.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Ścieżka elementów projektu wyświetlanych w oknie dialogowym dla szablonu **Dodaj nowy element** .|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Określa kolejność sortowania w węźle drzewa plików wyświetlanych w oknie dialogowym **Dodaj nowy element** .|  
  
 W poniższej tabeli przedstawiono opcje filtrów dostępne w poprzednim segmencie kodu.  
  
|Opcja filtru|Opis|  
|-------------------|-----------------|  
|`CommonFindFilesFilter`|Oznacza, że filtr jest jednym ze wspólnych filtrów w oknie dialogowym **Znajdź w plikach** . Filtry wspólne są wymienione na liście filtrów przed filtrami, które nie są oznaczone jako wspólne.|  
|`CommonOpenFilesFilter`|Oznacza, że filtr jest jednym ze wspólnych filtrów w oknie dialogowym **Otwórz plik** . Filtry wspólne są wymienione na liście filtrów przed filtrami, które nie są oznaczone jako wspólne.|  
|`FindInFilesFilter`|Oznacza, że filtr będzie jednym z filtrów w oknie dialogowym **Znajdź w plikach** i zostanie wyświetlony po wspólnych filtrach.|  
|`NotOpenFileFilter`|Oznacza, że filtr nie zostanie użyty w oknie dialogowym **Otwórz plik** .|  
|`NotAddExistingItemFilter`|Wskazuje, że filtr nie będzie używany w oknie dialogowym Dodaj **istniejący element** .|  
  
 Domyślnie jeśli filtr nie ma co najmniej jednego zestawu flag, filtr jest używany w oknie dialogowym **Dodaj istniejący element** i oknie dialogowym **Otwórz plik** po wyświetleniu wspólnych filtrów. Filtr nie jest używany w oknie dialogowym **Znajdź w plikach** .  
  
 Wszystkie poniższe przykłady znajdują się w rejestrze w kluczu [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Przykład  
  
```  
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)  
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Nazwa|Typ|Dane|Opis|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|Identyfikator zasobu dla nowych szablonów projektu.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Domyślna ścieżka dla projektów typu zarejestrowanego projektu.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Ustawia kolejność sortowania projektów wyświetlanych w oknie dialogowym Kreatora nowych projektów.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|wartość 0 oznacza, że projekty tego typu są wyświetlane tylko w oknie dialogowym Nowy projekt.|  
  
 Wszystkie poniższe przykłady znajdują się w rejestrze w kluczu [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Przykład  
  
```  
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)  
   @="Miscellaneous Files Project"  
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1  
                                 (CLSID for Figures Project projects)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|Nazwa|Typ|Dane|Opis|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|Brak|Wartość domyślna, która wskazuje, że następujące wpisy są przeznaczone dla wpisów projektów różne pliki.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Wartość identyfikatora zasobu dla plików szablonów Dodaj nowe elementy.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Domyślna ścieżka elementów, które będą wyświetlane w oknie dialogowym **Dodaj nowy element** .|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Ustala porządek sortowania do wyświetlania w węźle drzewa okna dialogowego **Dodaj nowy element** .|  
  
 Poniższy przykład znajduje się w rejestrze w kluczu [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus].  
  
## <a name="example"></a>Przykład  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 Pozycja menu wskazuje, że IDE jest zasobem używanym do pobierania informacji z menu. Po scaleniu tych danych z bazą danych menu ten sam klucz zostanie dodany w sekcji MenusMerged rejestru. Pakietu VSPackage nie powinna modyfikować żadnych elementów bezpośrednio w sekcji MenusMerged. W polu dane w poniższej tabeli znajdują się trzy pola rozdzielane przecinkami. Pierwsze pole określa pełną ścieżkę pliku zasobów menu:  
  
- Jeśli pierwsze pole zostanie pominięte, zasób menu jest ładowany z satelickiej biblioteki DLL identyfikowanej przez identyfikator GUID pakietu VSPackage.  
  
  Drugie pole określa identyfikator zasobu menu typu CTMENU:  
  
- Jeśli identyfikator zasobu jest określony, a ścieżka pliku jest dostarczana przez pierwszy parametr, zasób menu jest ładowany z pełnej ścieżki pliku.  
  
- Jeśli podano identyfikator zasobu, ale ścieżka pliku nie jest, zasób menu jest ładowany z satelickiej biblioteki DLL.  
  
- Jeśli podano pełną ścieżkę pliku i pominięto identyfikator zasobu, oczekiwany jest plik dyrektor ds.  
  
  Ostatnie pole określa numer wersji zasobu CTMENU. Możesz ponownie scalić menu, zmieniając numer wersji.  
  
|Nazwa|Typ|Dane|Opis|  
|----------|----------|----------|-----------------|  
|% CLSID_Package%|REG_SZ|`,1000,1`|Zasób do pobrania informacji z menu.|  
  
 Wszystkie poniższe przykłady znajdują się w rejestrze w kluczu [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates].  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Nazwa|Typ|Dane|Opis|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Wartość identyfikatora zasobu dla nowych szablonów projektu.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Domyślna ścieżka do katalogu nowych projektów. Elementy w tym katalogu będą wyświetlane w oknie dialogowym **Kreator nowego projektu** .|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Określa kolejność, w której projekty będą wyświetlane w węźle drzewa okna dialogowego **Nowy projekt** .|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|wartość 0 oznacza, że projekty tego typu są wyświetlane tylko w oknie dialogowym **Nowy projekt** .|  
  
 Poniższy przykład znajduje się w rejestrze w kluczu [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts].  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|Nazwa|Typ|Dane|Opis|  
|----------|----------|----------|-----------------|  
|`Package`|REG_SZ|`%CLSID_Package%`|Identyfikator klasy zarejestrowanej pakietu VSPackage.|  
|`UseInterface`|REG_DWORD|`1`|1 oznacza, że interfejs użytkownika będzie używany do współpracy z tym projektem. wartość 0 oznacza, że nie ma interfejsu interfejsu użytkownika.|  
  
 Pliki. vsz kontrolujące nowe typy projektów często zawierają wpis RELATIVE_PATH. Ta ścieżka jest względna dla ścieżki określonej w \ProductDir wpis typu projektu w następującym kluczu instalacji:  
  
 HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup  
  
 Na przykład szablony projektów platformy Enterprise Framework dodają następujące wpisy rejestru:  
  
 HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\  
  
 Oznacza to, że jeśli w pliku VSZ znajduje się wpis PROJECT_TYPE = EF, środowisko odnajdzie pliki. vsz w katalogu ProductDir określonym wcześniej.  
  
## <a name="see-also"></a>Zobacz też  
 [Lista kontrolna: tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)   
 [Tworzenie wystąpień projektów przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
