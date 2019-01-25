---
title: Rejestrowanie typu projektu | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 9f56de9b3ce3f1faf5a63fa6b8fd8574a57b82f3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54774309"
---
# <a name="registering-a-project-type"></a>Rejestrowanie typu projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gdy tworzysz nowy typ projektu, należy utworzyć wpisy rejestru, które umożliwiają [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] rozpoznaje i pracować z danego typu projektu. Wpisy rejestru są zazwyczaj tworzone przy użyciu pliku skryptu (.rgs) z rejestru.  
  
 W poniższym przykładzie instrukcji z rejestru zapewnienia domyślnych ścieżek i danych w przypadku, gdy to stosowne, a następnie tabeli, która zawiera wpisy z rejestru skryptu dla każdej instrukcji. Tabele zawierają wpisy skryptu i dodatkowe informacje na temat oświadczeń.  
  
> [!NOTE]
>  Następujące informacje do rejestru jest przeznaczonych do przykładu i celów wpisów w skryptach rejestru, który będzie zapisywać do zarejestrowania typu projektu. Rzeczywiste wpisy i ich zastosowań mogą się różnić w zależności od określonych wymagań tego typu projektu. Należy przejrzeć przykłady można znaleźć taki, który przypomina typu projektu, które tworzysz, a następnie przejrzyj skrypt rejestru dla tego przykładu.  
  
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
|`@`|REG_SZ|`FigPrjFile`|Nazwa i opis projektu typu plików, które mają .figp rozszerzenia.|  
|`Content Type`|REG_SZ|`Text/plain`|Typ zawartości plików projektu.|  
|`NullFile`|REG_SZ|`Null`||  
|`@`|REG_SZ|`%MODULE%,-206`|Ikona domyślna używana dla projektu tego typu. Instrukcja % modułu % zakończeniu w rejestrze w domyślnej lokalizacji projektu typu DLL.|  
|`@`|REG_SZ|`&Open in Visual Studio`|Domyślna aplikacja, w którym zostanie otwarty ten typ projektu.|  
|`@`|REG_SZ|`devenv.exe "%1"`|Polecenie domyślnej, która będzie uruchamiana po otwarciu projektu tego typu.|  
  
 Poniższe przykłady pochodzą z HKEY_LOCAL_MACHINE i znajdują się w rejestrze w kluczu [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages].  
  
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
|`@` (Ustawienie domyślne)|REG_SZ|`FigPrj Project VSPackage`|Możliwa do zlokalizowania nazwę tego zarejestrowany pakietu VSPackage (typ projektu).|  
|`InprocServer32`|REG_SZ|`%MODULE%`|Ścieżka projektu typu DLL. IDE ładuje tę bibliotekę DLL i przekazuje CLSID pakietu VSPackage do `DllGetClassObject` można pobrać <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> do konstruowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> obiektu.|  
|`CompanyName`|REG_SZ|`Microsoft`|Nazwa firmy, która opracowała typu projektu.|  
|`ProductName`|REG_SZ|`Figure Project Sample`|Nazwa typu projektu.|  
|`ProductVersion`|REG_SZ|`9.0`|Zwolnij numer wersji typu projektu.|  
|`MinEdition`|REG_SZ|`professional`|Wersja pakietu VSPackage, jest zarejestrowany.|  
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Pakiet załadować klucza dla projektu pakietu VSPackage. Klucz jest weryfikowana, gdy projekt jest ładowany po uruchomieniu środowiska.|  
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Nazwa pliku satelitarnej biblioteki DLL zawierającej zlokalizowane zasoby dla tego typu projektu.|  
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Ścieżka satelitarną bibliotekę DLL.|  
|`FigProjectsEvents`|REG_SZ|Zobacz poufności informacji dla wartości.|Określa ciąg tekstowy, zwrócony dla tego zdarzenia automatyzacji.|  
|`FigProjectItemsEvents`|REG_SZ|Zobacz poufności informacji dla wartości.|Określa ciąg tekstowy, zwrócony dla tego zdarzenia automatyzacji.|  
  
 Poniższe przykłady znajdują się w rejestrze w kluczu [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
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
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|Identyfikator zasobu o nazwie mają zostać pobrane satelitarną bibliotekę DLL jest zarejestrowany w ramach pakietów.|  
|`Package`|REG_SZ|`%CLSID_Package%`|Identyfikator pakietu VSPackage zarejestrowany w ramach pakietów.|  
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Domyślna ścieżka pliku szablonu projektu. Są to pliki wyświetlane przez szablon nowego projektu.|  
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Domyślna ścieżka pliku szablonu elementu projektu. Są to pliki wyświetlane przez szablon Dodaj nowy element.|  
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Włącza środowisko IDE do zaimplementowania **Otwórz** okno dialogowe.|  
|`PossibleProjectExtensions`|REG_SZ|`figp`|Używane przez IDE, aby ustalić, czy projektu otwierany jest obsługiwany przez ten typ projektu (project factory). Format dla więcej niż jeden wpis jest rozdzielaną średnikami listę. Na przykład "vdproj; vdp".|  
|`DefaultProjectExtension`|REG_SZ|`.figp`|IDE używa jako domyślne rozszerzenie nazwy pliku dla operacji Zapisz jako.|  
|`Filter Settings`|REG_DWORD|Różne, zobacz instrukcje i uwagi pod tabelą.|Te ustawienia są używane do definiowania różnych filtrów do wyświetlania plików w oknach dialogowych interfejsu użytkownika.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Identyfikator zasobu dla szablonów Dodaj element.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Ścieżka wyświetlanych w oknie dialogowym dla elementów projektu **Dodaj nowy element** szablonu.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Określa porządek sortowania w węźle drzewa pliki wyświetlane w **Dodaj nowy element** okno dialogowe.|  
  
 W poniższej tabeli przedstawiono opcje filtry dostępne w poprzedniego segmentu kodu.  
  
|Opcja filtra|Opis|  
|-------------------|-----------------|  
|`CommonFindFilesFilter`|Wskazuje, że filtr jest jednym z typowych filtrów w **Znajdź w plikach** okno dialogowe. Wspólne filtry są wymienione na liście filtrów przed filtrami niezaznaczonych jako wspólne.|  
|`CommonOpenFilesFilter`|Wskazuje, że filtr jest jednym z typowych filtrów w **Otwórz plik** okno dialogowe. Wspólne filtry są wymienione na liście filtrów przed filtrami niezaznaczonych jako wspólne.|  
|`FindInFilesFilter`|Wskazuje, że filtr będzie jednego z filtrów w **Znajdź w plikach** okna dialogowego pole, a zostaną wyświetlone po wspólnych filtrów.|  
|`NotOpenFileFilter`|Wskazuje, że filtr nie zostanie użyty w **Otwórz plik** okno dialogowe.|  
|`NotAddExistingItemFilter`|Wskazuje, że filtr nie zostanie użyty w dodawania **istniejący element** okno dialogowe.|  
  
 Domyślnie, jeśli filtr nie mieć co najmniej jeden z tych flag zestawu, filtr jest używany w **Dodaj istniejący element** okno dialogowe i **Otwórz plik** po wspólne filtry są wyświetlane okno dialogowe. Filtr nie jest używany w **Znajdź w plikach** okno dialogowe.  
  
 Poniższe przykłady znajdują się w rejestrze w kluczu [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
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
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|Identyfikator zasobu dla szablonów nowy projekt.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Domyślna ścieżka dla projektów typu projektu zarejestrowane.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Ustawia sortowania kolejności projektów wyświetlane w oknie dialogowym Kreatora nowych projektów.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|wartość 0 wskazuje, że projekty tego typu są wyświetlane tylko w oknie dialogowym Nowy projekt.|  
  
 Poniższe przykłady znajdują się w rejestrze w kluczu [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
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
|`@`|REG_SZ|Brak|Domyślna wartość oznacza, że następujące wpisy są wpisy projektów różne pliki.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Wartość Identyfikatora zasobu dla plików szablonów Dodaj nowe elementy.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Domyślna ścieżka elementów, które będą wyświetlane w **Dodaj nowy element** okno dialogowe.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Określa porządek sortowania w celu wyświetlenia w węźle drzewa **Dodaj nowy element** okno dialogowe.|  
  
 Poniższy przykład znajduje się w rejestrze w kluczu [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus].  
  
## <a name="example"></a>Przykład  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 Wpis menu wskazuje IDE zasobów do pobierania informacji menu. Gdy te dane zostały połączone w bazie danych menu, ten sam klucz zostanie dodana w sekcji MenusMerged rejestru. Pakietu VSPackage niczego w sekcji MenusMerged nie należy modyfikować bezpośrednio. W polu danych w tabeli poniżej istnieją trzy przecinkami oddzielone — pola. Pierwsze pole określa pełną ścieżkę pliku zasobu menu:  
  
- Jeśli pierwsze pole zostanie pominięty, zasobu menu jest ładowany z satelitarnej biblioteki DLL identyfikowany przez identyfikator GUID pakietu VSPackage.  
  
  Drugie pole określa identyfikator zasobu menu o typie CTMENU:  
  
- Jeśli określono identyfikator zasobu, a ścieżka pliku jest dostarczany za pomocą pierwszego parametru, zasobu menu jest ładowany z pełną ścieżką do pliku.  
  
- Jeśli ścieżka pliku jest, ale określono identyfikator zasobu, zasobu menu jest ładowany z satelitarną bibliotekę DLL.  
  
- Jeśli podano pełną ścieżkę pliku i identyfikator zasobu pominięty, plik do załadowania powinien być plikiem Dyrektor ds. technologii.  
  
  Ostatnie pole określa numer wersji dla zasobu CTMENU. Menu można scalać ponownie, zmieniając numer wersji.  
  
|Nazwa|Typ|Dane|Opis|  
|----------|----------|----------|-----------------|  
|CLSID_Package %|REG_SZ|`,1000,1`|Zasób, który można pobrać informacji o menu.|  
  
 Poniższe przykłady znajdują się w rejestrze w kluczu [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates].  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Nazwa|Typ|Dane|Opis|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Wartość Identyfikatora zasobu dla szablonów rysunki nowy projekt.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Domyślna ścieżka katalogu nowych projektów. Elementy w tym katalogu będą wyświetlane w **Kreatora nowego projektu** okno dialogowe.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Określa kolejność wyświetlania projektów w węźle drzewa **nowy projekt** okno dialogowe.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|wartość 0 wskazuje, że projekty tego typu nie są wyświetlane tylko w **nowy projekt** okno dialogowe.|  
  
 Poniższy przykład znajduje się w rejestrze w kluczu [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts].  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|Nazwa|Typ|Dane|Opis|  
|----------|----------|----------|-----------------|  
|`Package`|REG_SZ|`%CLSID_Package%`|Identyfikator klasy zarejestrowanych pakietu VSPackage.|  
|`UseInterface`|REG_DWORD|`1`|1 wskazuje, że interfejs użytkownika będzie służyć do interakcji z tego projektu. wartość 0 wskazuje, że nie ma żadnych interfejs użytkownika.|  
  
 Pliki the.vsz, określające nowych typów projektów często zawierają wpis RELATIVE_PATH. Ta ścieżka jest określana względem ścieżki określonej wpisie \ProductDir typu projektu w następującym kluczu instalacji:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup  
  
 Na przykład szablony projektów Enterprise Frameworks Dodaj następujące wpisy rejestru:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\  
  
 Oznacza to, że Jeśli dołączysz PROJECT_TYPE = EF wpisu w pliku .vsz znajduje środowiska .vsz swoje pliki w katalogu ProductDir określony wcześniej.  
  
## <a name="see-also"></a>Zobacz też  
 [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)   
 [Tworzenie wystąpień projektów przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
