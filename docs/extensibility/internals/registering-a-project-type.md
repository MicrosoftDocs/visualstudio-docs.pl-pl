---
title: Rejestrowanie typu projektu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05ac1f393632934f193f5f4efaaf9e5459ffbb14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705870"
---
# <a name="registering-a-project-type"></a>Rejestrowanie typu projektu
Podczas tworzenia nowego typu projektu należy utworzyć wpisy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rejestru, które umożliwiają rozpoznawanie i pracę z typem projektu. Te wpisy rejestru są zazwyczaj tworzą za pomocą pliku skryptu rejestru (.rgs).

 W poniższym przykładzie instrukcje z rejestru zawierają domyślne ścieżki i dane, w stosownych przypadkach, a następnie tabelę zawierającą wpisy ze skryptu rejestru dla każdej instrukcji. Tabele zawierają wpisy skryptu i dodatkowe informacje o instrukcjach.

> [!NOTE]
> Następujące informacje rejestru ma być przykładem typu i celów wpisów w skryptach rejestru, które będą zapisywane w celu zarejestrowania typu projektu. Rzeczywiste wpisy i ich zastosowania mogą się różnić w zależności od określonych wymagań typu projektu. Należy przejrzeć dostępne przykłady, aby znaleźć taki, który jest bardzo podobny do typu projektu, który tworzysz, a następnie przejrzyj skrypt rejestru dla tego przykładu.

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
|`@`|REG_SZ|`FigPrjFile`|Nazwa i opis plików typu projektu, które mają rozszerzenie .figp.|
|`Content Type`|REG_SZ|`Text/plain`|Typ zawartości dla plików projektu.|
|`NullFile`|REG_SZ|`Null`||
|`@`|REG_SZ|`%MODULE%,-206`|Domyślna ikona używana dla projektu tego typu. Instrukcja %MODULE% jest wypełniana w rejestrze do domyślnej lokalizacji biblioteki DLL typu projektu.|
|`@`|REG_SZ|`&Open in Visual Studio`|Domyślna aplikacja, w której zostanie otwarty ten typ projektu.|
|`@`|REG_SZ|`devenv.exe "%1"`|Domyślne polecenie, które zostanie uruchomione po otwarciu projektu tego typu.|

 Poniższe przykłady pochodzą z HKEY_LOCAL_MACHINE i znajdują się w rejestrze pod kluczem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages].

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
|`@`(Domyślnie)|REG_SZ|`FigPrj Project VSPackage`|Nazwa lokalizacji tego zarejestrowanego vspackage (typ projektu).|
|`InprocServer32`|REG_SZ|`%MODULE%`|Ścieżka biblioteki DLL typu projektu. IDE ładuje tę bibliotekę DLL i przekazuje `DllGetClassObject` VSPackage CLSID, aby uzyskać <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> możliwość konstruowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> obiektu.|
|`CompanyName`|REG_SZ|`Microsoft`|Nazwa firmy, która opracowała typ projektu.|
|`ProductName`|REG_SZ|`Figure Project Sample`|Nazwa typu projektu.|
|`ProductVersion`|REG_SZ|`9.0`|Numer wersji wersji typu projektu.|
|`MinEdition`|REG_SZ|`professional`|Edycja VSPackage jest zarejestrowany.|
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Klucz ładowania pakietu dla projektu VSPackage. Klucz jest sprawdzany po załadowaniu projektu po uruchomieniu środowiska.|
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Nazwa pliku biblioteki DLL satelity zawierającej zlokalizowane zasoby dla typu projektu.|
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Ścieżka biblioteki DLL satelity.|
|`FigProjectsEvents`|REG_SZ|Zobacz instrukcję dla wartości.|Określa ciąg tekstowy zwrócony dla tego zdarzenia automatyzacji.|
|`FigProjectItemsEvents`|REG_SZ|Zobacz instrukcję dla wartości.|Określa ciąg tekstowy zwrócony dla tego zdarzenia automatyzacji.|

 Wszystkie poniższe przykłady znajdują się w rejestrze pod kluczem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

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
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|Identyfikator zasobu nazwy, która ma zostać pobrana z biblioteki DLL satelity zarejestrowanej w obszarze Pakiety.|
|`Package`|REG_SZ|`%CLSID_Package%`|Identyfikator klasy VSPackage zarejestrowany w obszarze Pakiety.|
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Domyślna ścieżka plików szablonu projektu. Są to pliki wyświetlane przez szablon Nowy projekt.|
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Domyślna ścieżka plików szablonu elementu projektu. Są to pliki wyświetlane przez szablon Dodaj nowy element.|
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Umożliwia IDE zaimplementować okno dialogowe **Otwieranie.**|
|`PossibleProjectExtensions`|REG_SZ|`figp`|Używane przez IDE do określenia, czy projekt jest obsługiwany przez ten typ projektu (fabryka projektu). Format dla więcej niż jednego wpisu jest listą rozdzielanych średnikami. Na przykład "vdproj;vdp".|
|`DefaultProjectExtension`|REG_SZ|`.figp`|Używane przez IDE jako domyślne rozszerzenie nazwy pliku dla operacji Zapisz jako.|
|`Filter Settings`|REG_DWORD|Różne, zobacz oświadczenia i komentarze po tabeli.|Te ustawienia służą do ustawiania różnych filtrów do wyświetlania plików w oknach dialogowych interfejsu użytkownika.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Identyfikator zasobu dla szablonów dodaj elementy.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Ścieżka elementów projektu wyświetlana w oknie dialogowym szablonu **Dodawanie nowego elementu.**|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Określa kolejność sortowania w węźle drzewa plików wyświetlanych w oknie dialogowym **Dodawanie nowego elementu.**|

 W poniższej tabeli przedstawiono opcje filtrów dostępne w poprzednim segmencie kodu.

|Opcja filtru|Opis|
|-------------------|-----------------|
|`CommonFindFilesFilter`|Wskazuje, że filtr jest jednym z typowych filtrów w oknie dialogowym **Znajdowanie w plikach.** Typowe filtry są wymienione na liście filtrów, zanim filtry nie są oznaczone jako typowe.|
|`CommonOpenFilesFilter`|Wskazuje, że filtr jest jednym z typowych filtrów w oknie dialogowym **Otwieranie pliku.** Typowe filtry są wymienione na liście filtrów, zanim filtry nie są oznaczone jako typowe.|
|`FindInFilesFilter`|Wskazuje, że filtr będzie jednym z filtrów w oknie dialogowym **Znajdowanie w plikach** i będzie wyświetlany po popularnych filtrach.|
|`NotOpenFileFilter`|Wskazuje, że filtr nie będzie używany w oknie dialogowym **Otwieranie pliku.**|
|`NotAddExistingItemFilter`|Wskazuje, że filtr nie będzie używany w oknie dialogowym Dodawanie **istniejącego elementu.**|

 Domyślnie, jeśli filtr nie ma jednej lub więcej z tych flag ustawionych, filtr jest używany w oknie dialogowym **Dodawanie istniejącego elementu** i w oknie dialogowym **Otwórz plik** po wyświetleniach wspólnych filtrów. Filtr nie jest używany w oknie dialogowym **Znajdowanie w plikach.**

 Wszystkie poniższe przykłady znajdują się w rejestrze pod kluczem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

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
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|Identyfikator zasobu dla szablonów nowego projektu.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Domyślna ścieżka dla projektów zarejestrowanego typu projektu.|
|`SortPriority`|REG_DWORD|`41 (x29)`|Ustawia kolejność sortowania projektów wyświetlanych w oknie dialogowym Kreatora nowych projektów.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 oznacza, że projekty tego typu są wyświetlane tylko w oknie dialogowym Nowy projekt.|

 Wszystkie poniższe przykłady znajdują się w rejestrze pod kluczem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

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
|`@`|REG_SZ|Brak|Wartość domyślna wskazująca, że następujące wpisy są dla wpisów projektów różne pliki.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Wartość identyfikatora zasobu dla plików szablonów Dodaj nowe elementy.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Domyślna ścieżka elementów, które będą wyświetlane w oknie dialogowym **Dodawanie nowego elementu.**|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Ustanawia kolejność sortowania do wyświetlania w węźle drzewa okna dialogowego **Dodawanie nowego elementu.**|

 Poniższy przykład znajduje się w rejestrze pod kluczem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus].

## <a name="example"></a>Przykład

```
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"
```

 Wpis menu wskazuje IDE do zasobu używanego do pobierania informacji o menu. Po scaleniu tych danych z bazą danych menu ten sam klucz zostanie dodany w sekcji MenusMerged rejestru. VSPackage nie należy modyfikować niczego w menuMerged sekcji bezpośrednio. W polu Dane w poniższej tabeli znajdują się trzy pola oddzielone przecinkami. Pierwsze pole identyfikuje pełną ścieżkę pliku zasobów menu:

- Jeśli pierwsze pole zostanie pominięte, zasób menu jest ładowany z biblioteki DLL satelity identyfikowanej przez identyfikator GUID VSPackage.

  Drugie pole identyfikuje identyfikator zasobu menu typu CTMENU:

- Jeśli określono identyfikator zasobu, a ścieżka pliku jest dostarczana przez pierwszy parametr, zasób menu jest ładowany z pełnej ścieżki pliku.

- Jeśli podano identyfikator zasobu, ale ścieżka pliku nie jest, zasób menu jest ładowany z biblioteki DLL satelity.

- Jeśli zostanie udostępniona pełna ścieżka pliku i pominięty identyfikator zasobu, oczekuje się, że plik, który ma zostać załadowany, będzie plikiem CTO.

  Ostatnie pole identyfikuje numer wersji zasobu CTMENU. Menu można scalić ponownie, zmieniając numer wersji.

|Nazwa|Typ|Dane|Opis|
|----------|----------|----------|-----------------|
|%CLSID_Package%|REG_SZ|`,1000,1`|Zasób do pobierania informacji o menu.|

 Wszystkie poniższe przykłady znajdują się w rejestrze pod kluczem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates].

```
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Nazwa|Typ|Dane|Opis|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Wartość identyfikatora zasobu dla szablonów projektu figures .|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Domyślna ścieżka katalogu Nowe projekty. Elementy w tym katalogu będą wyświetlane w oknie dialogowym **Kreator nowego projektu.**|
|`SortPriority`|REG_DWORD|`41 (x29)`|Ustanawia kolejność wyświetlania projektów w węźle drzewa okna dialogowego **Nowy projekt.**|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 oznacza, że projekty tego typu są wyświetlane tylko w oknie dialogowym **Nowy projekt.**|

 Poniższy przykład znajduje się w rejestrze pod kluczem [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts].

```
\FiguresProductSample
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "UseInterface"=dword:00000001
```

|Nazwa|Typ|Dane|Opis|
|----------|----------|----------|-----------------|
|`Package`|REG_SZ|`%CLSID_Package%`|Identyfikator klasy zarejestrowanego vspackage.|
|`UseInterface`|REG_DWORD|`1`|1 wskazuje, że interfejs użytkownika będzie używany do interakcji z tym projektem. 0 oznacza, że nie ma interfejsu użytkownika.|

 Pliki.vsz, które kontrolują nowe typy projektów, często zawierają RELATIVE_PATH wpis. Ta ścieżka jest względna do ścieżki określonej w \ProductDir wpis typu projektu w następującym kluczu instalacji:

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup

 Na przykład szablony projektów programu Enterprise Frameworks dodają następujące wpisy rejestru:

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\

 Oznacza to, że jeśli wpis PROJECT_TYPE=EF zostanie uwzględnione w pliku vsz, środowisko znajdzie pliki .vsz w określonym wcześniej katalogu ProductDir.

## <a name="see-also"></a>Zobacz też
- [Lista kontrolna: tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)
- [Tworzenie wystąpień projektów przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
