---
title: 'Instrukcje: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ReferenceManager
helpviewer_keywords:
- Visual C# projects, references
- references [Visual Studio], adding
- assemblies [Visual Studio], references
- Visual Basic projects, references
- project references, adding
- referencing components, adding references
- project references, removing
- referencing assemblies
- referencing components, removing references
- references [Visual Studio], removing
- referencing components, assemblies not listed
ms.assetid: 1aabb520-99b0-46c6-9368-21b4d84793eb
caps.latest.revision: 48
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8d7d4524f1839179ac253265d95f191caf1c50af
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445675"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Instrukcje: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz użyć **Menadżer odwołań** okno dialogowe, aby dodać i zarządzać odwołaniami do składników przez użytkownika, Microsoft, lub dostosowywania innej firmy. Jeśli tworzysz aplikację Windows Universal projekt automatycznie odwołuje się do wszystkich poprawne dll Windows SDK. Jeśli tworzysz aplikację .NET, projekt automatycznie odwołuje się do biblioteki mscorlib.dll. Niektóre interfejsy API platformy .NET są widoczne w składnikach, które trzeba dodać ręcznie. Odwołania do składników modelu COM lub niestandardowe składniki trzeba dodać ręcznie.  
  
## <a name="adding-and-removing-a-reference"></a>Dodawanie i usuwanie odwołań  
  
#### <a name="to-add-a-reference"></a>Aby dodać odwołanie  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł odwołania i wybierz **Dodaj odwołanie**.  
  
2. Określ odwołania, aby dodać, a następnie wybierz **OK** przycisku.  
  
   **Menadżer odwołań** otwiera się i wyświetla dostępne odwołania wg grupy. Typ projektu określa, które z następujących grup się pojawiają:  
  
- Zestawy z podgrupami Framework i Rozszerzenia.  
  
- Rozwiązanie z podgrupą Projekty.  
  
- Okna z podgrupami Podstawowe i Rozszerzenia. Odwołania w Windows SDK lub SDK rozszerzeń można eksplorować przy użyciu **przeglądarki obiektów**.  
  
- Przeglądaj z podgrupą Ostatnie.  
  
## <a name="assemblies-tab"></a>Karta Zestawy  
 **Zestawy** karta zawiera listę wszystkich zestawów .NET Framework, które są dostępne dla odwołań. **Zestawy** karty nie ma żadnych zestawów z globalnej pamięci podręcznej zestawów (GAC), ponieważ zestawy w pamięci podręcznej GAC są częścią środowiska czasu wykonywania. W przypadku wdrażania lub kopiowania aplikacji zawierającej odwołanie do zestawu, który jest zarejestrowany w GAC, zestaw nie zostanie wdrożony ani skopiowany z aplikacją, bez względu na wartość ustawienia Kopiuj lokalnie. Aby uzyskać więcej informacji, zobacz [odwołania do projektu](http://go.microsoft.com/fwlink/?LinkId=238512).  
  
 Podczas ręcznego dodawania odwołania do dowolnych przestrzeni nazw EnvDTE (EnvDTE, EnvDTE80, EnvDTE90, EnvDTE90a lub EnvDTE100), ustaw właściwość Osadź typy współdziałania na wartość False w oknie dialogowym Właściwości. Ustawienie tej właściwości na True może spowodować problemy z kompilacją ze względu na pewne właściwości EnvDTE, które nie mogą być osadzone.  
  
 Wszystkie projekty pulpitu zawierają niejawne odwołanie do mscorlib. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projekty zawierają niejawne odwołanie do Microsoft.VisualBasic. W [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], wszystkie projekty zawierają niejawne odwołanie do System.Core, nawet jeśli zostanie ono usunięte z listy odwołań.  
  
 Jeśli typ projektu nie obsługuje zestawów, karta nie pojawi się w **Menadżer odwołań** okno dialogowe.  
  
 Karta Zestawy zawiera dwie karty podrzędne:  
  
1. Framework zawiera listę wszystkich zestawów, które stanowią docelową platformę Framework.  
  
   - Zestawy anonsowane znajdują się liście Pełna platforma Framework i są wyliczone na liście Framework, gdy projekt jest ukierunkowany na Profil docelowej platformy Framework. Zestawy anonsowane są szare, aby odróżnić je od zestawów, które istnieją w profilu docelowej platformy Framework projektu. Na przykład, jeśli projekt jest ukierunkowany na klienta .NET Framework 4, lista zawiera zestawy anonsowane z .NET Framework 4. Gdy użytkownik dodaje zestaw anonsowany, użytkownik jest powiadamiany, po **Menadżer odwołań** po zamknięciu okna dialogowego, projekt zostanie ukierunkowany na .NET Framework 4 i zostanie dodany zestaw anonsowany.  
  
   - Projekty dla [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacje zawierają odwołania do wszystkich zestawów w docelowym [!INCLUDE[net_win8_profile](../includes/net-win8-profile-md.md)] domyślnie przy tworzeniu projektu. W projektach zarządzanych, węzeł tylko do odczytu folderze odwołania w **Eksploratora rozwiązań** wskazuje odwołanie do całej struktury Framework. W związku z tym na karcie Framework nie będzie wyliczony żaden zestaw z Framework i zamiast tego wyświetli się następujący komunikat: "Wszystkich zestawów Framework istnieją już odwołania. Użyj przeglądarki obiektów do zbadania odwołań w ramach." Dla projektów pulpitu karta Framework wylicza zestawy z docelowej platformy Framework i użytkownik musi dodać odwołania wymagane przez tę aplikację.  
  
2. Rozszerzenia wyświetla listę wszystkich zestawów, które opracowali zewnętrzni dostawcy składników i formantów, aby rozszerzyć docelową platformę Framework. W zależności od celu aplikacji użytkownika, może być konieczne użycie tych zestawów.  
  
   - Rozszerzenia jest wypełniane przez wyliczanie zestawów, które są zarejestrowane w następujących lokalizacjach:  
  
       ```  
       32-bit machine:  
       HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
       HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
       64-bit machine:  
       HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
       HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
       And older versions of the [Target Framework Identifier]  
       ```  
  
        Na przykład, jeśli projekt jest przeznaczony dla .NET Framework 4 na komputerze 32-bitowym, rozszerzenia wyliczą zestawy, które są zarejestrowane w ramach \Microsoft\\. NETFramework\v4.0\AssemblyFoldersEx\\, \Microsoft\\. NETFramework\v3.5\AssemblyFoldersEx\\, \Microsoft\\. NETFramework\v3.0\AssemblyFoldersEx\\i \Microsoft\\. NETFramework\v2.0\AssemblyFoldersEx\\.  
  
   Niektóre składniki na liście mogą nie być wyświetlane, w zależności od [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] wersji projektu. Taka sytuacja może wystąpić w następujących warunkach:  
  
- Składnik, który korzysta z najnowszej wersji programu .NET Framework jest niezgodny z projektem, który jest przeznaczony dla starszej wersji programu .NET Framework.  
  
     Aby uzyskać informacje o zmienianiu docelowej wersji .NET Framework dla projektu, zobacz [jak: Docelowa wersja systemu .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
- Składnik, który używa [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] jest niezgodny z projektem, który jest przeznaczony dla [!INCLUDE[net_v45](../includes/net-v45-md.md)].  
  
     Podczas tworzenia nowej aplikacji docelowej niektóre projekty kierują [!INCLUDE[net_v45](../includes/net-v45-md.md)] domyślnie. Aby uzyskać więcej informacji, zobacz [.NET Framework Client Profile](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).  
  
- Dodawanie odwołań do pliku do danych wyjściowych innego projektu w tym samym rozwiązaniu, należy unikać, ponieważ w ten sposób może spowodować błędy kompilacji. Zamiast tego należy użyć **projektów** karcie **Dodaj odwołanie** okno dialogowe, aby utworzyć odwołania projekt projekt. Ułatwia to Projektowanie zespołowe poprzez umożliwienie lepszego zarządzania bibliotekami klas, utworzone w projekcie. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z odwołaniami uszkodzone](../ide/troubleshooting-broken-references.md).  
  
- > [!NOTE]
    > W programie Visual Studio 2015 odwołanie pliku zamiast odwołania projektu jest tworzony, jeśli wersji docelowej programu .NET Framework jednego projektu jest wersja 4.5 i wersję docelową innego projektu jest w wersji 2, 3, 3.5 lub 4.0.  
  
#### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Aby wyświetlić zestaw w oknie dialogowym Dodawanie odwołania  
  
- Przenoszenie lub kopiowanie zestawu do jednej z następujących lokalizacji:  
  
  - Katalog aktualnego projektu. (Zestawy te można znaleźć przy użyciu **Przeglądaj** karty.)  
  
  - Inne katalogi projektu w tym samym rozwiązaniu. (Zestawy te można znaleźć przy użyciu **projektów** karty.)  
  
    \- lub —  
  
- Ustaw klucz rejestru, który określa lokalizację zestawów do wyświetlenia:  
  
   W przypadku 32-bitowym systemie operacyjnym należy dodać jeden z następujących kluczy rejestru.  
  
  - [HKEY_CURRENT_USER\SOFTWARE\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"  
  
  - [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"  
  
    Dla 64-bitowym systemie operacyjnym należy dodać jeden z następujących kluczy rejestru w gałęzi rejestru 32-bitowych.  
  
  - [HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"  
  
  - [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@= "*AssemblyLocation*"  
  
    *VersionMinimum* jest najniższą wersją .NET Framework, która ma zastosowanie. Jeśli *VersionMinimum* jest w wersji 3.0, foldery określone w AssemblyFoldersEx dotyczą projektów środowiska .NET Framework 3.0 lub nowszej.  
  
    *AssemblyLocation* to katalog zestawów, które mają być wyświetlane w **Dodaj odwołanie** okno dialogowe, na przykład C:\MyAssemblies\\.  
  
    Tworzenie klucza rejestru w węźle HKEY_LOCAL_MACHINE umożliwia wszystkim użytkownikom przeglądanie zestawów w określonej lokalizacji w **Dodaj odwołanie** okno dialogowe. Tworzenie klucza rejestru w węźle HKEY_CURRENT_USER wpływa na ustawienie dla bieżącego użytkownika.  
  
    Otwórz **Dodaj odwołanie** ponownie okno dialogowe. Zestawy powinny pojawić się na **.NET** kartę. Jeśli nie, upewnij się, że zestawy znajdują się w określonym *AssemblyLocation* katalogu, uruchom ponownie program Visual Studio i spróbuj ponownie.  
  
## <a name="com-tab"></a>Karta COM  
 Na karcie COM znajduje się lista wszystkich składników COM, które są dostępne dla odwołań. Jeśli chcesz dodać odwołanie do zarejestrowanej DLL modelu COM, zawierającej manifest wewnętrzny, najpierw wyrejestruj bibliotekę DLL. W przeciwnym razie Visual Studio dodaje odwołanie do zestawu jako formant ActiveX, a nie jako natywną DLL.  
  
 Jeśli typ projektu nie obsługuje COM, karta nie pojawi się w **Menadżer odwołań** okno dialogowe.  
  
## <a name="solution-tab"></a>Karta Rozwiązanie  
 Na karcie Rozwiązanie znajduje się lista wszystkich zgodnych projektów w obrębie bieżącego rozwiązania, na karcie podrzędnej Projekty.  
  
 Projekt może się odwoływać do innego projektu, który jest przeznaczony dla innej wersji platformy .NET Framework. Na przykład, można utworzyć projektu przeznaczonego [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] , ale która odwołuje się zestaw stworzonemu dla platformy .NET Framework 2. Jednak projekt .NET Framework 2 nie może odwoływać się [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] projektu. Aby uzyskać więcej informacji, zobacz [przeznaczonych dla określonej wersji programu .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
 Projekt, który jest przeznaczony dla [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] jest niezgodny z projektem, który jest przeznaczony dla [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)].  
  
 W [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], odwołanie pliku zamiast odwołania projektu jest tworzony, jeśli jeden projekt jest przeznaczony dla .NET Framework 4, a inny projekt jest przeznaczony dla starszej wersji.  
  
 Projekt, który jest przeznaczony dla [!INCLUDE[net_win8_profile](../includes/net-win8-profile-md.md)] nie można dodać odwołania projektu do projektu, który jest przeznaczony dla .NET Framework i na odwrót.  
  
## <a name="windows-tab"></a>Karta Windows  
 Na karcie Windows są wymienione wszystkie zestawy SDK specyficzne dla platform, na których jest uruchamiany system operacyjny Windows.  
  
 Można wygenerować plik WinMD w Visual Studio na dwa sposoby:  
  
- **[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] Projekty zarządzane aplikacji**: [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] projektów aplikacji może zapewniać dane wyjściowe pliki binarne WinMD przez ustawienie właściwości projektu &#124; typ danych wyjściowych = plik WinMD. Nazwa pliku WinMD musi być nadzbiorem przestrzeni nazw wszystkich przestrzeni nazw, które w nim istnieją. Na przykład, jeżeli projekt składa się z przestrzeni nazw A.B i A.B.C, możliwe nazwy dla wygenerowanego WinMD to A.winmd i A.B.winmd. Jeśli użytkownik wejdzie do właściwości projektu &#124; Nazwa zestawu lub właściwości projektu &#124; Namespace wartość, która jest odłączona od zestawu przestrzeni nazw w projekcie lub jest nadzbiorem przestrzeni nazw w ramach projektu, jest generowane ostrzeżenie kompilacji: 'A.winmd' nie jest prawidłową nazwą pliku .winmd dla tego zestawu. Wszystkie typy w pliku metadanych systemu Windows musi istnieć w podrzędnej przestrzeni nazw nazwy pliku. Typy, które nie istnieją w podrzędnej przestrzeni nazw nazwy pliku, nie mogą być zlokalizowane w czasie wykonywania. W tym zestawie najmniejszą wspólną przestrzenią nazw jest „CSWSClassLibrary1”. Projekt pulpitu języka Visual Basic lub Visual C# może używać tylko plików Winmd, które są generowane przy użyciu [!INCLUDE[win8](../includes/win8-md.md)] zestawów SDK, które są znane jako Winmd firmy Microsoft i nie można wygenerować plików Winmd.  
  
- **[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] macierzyste projekty aplikacji**: Macierzysty plik WinMD składa się z tylko metadanych. Jego realizacja istnieje w oddzielnym pliku DLL. Można produkować, aby przez wybranie szablonu projektu składnika wykonawczego Windows w natywnych plików binarnych **nowy projekt** okno dialogowe lub zaczynając od pustego projektu i modyfikując właściwości projektu, aby wygenerować plik WinMD. Jeżeli projekt zawiera rozłączne przestrzenie nazw, błąd kompilacji poinformuje użytkownika, że należy połączyć ich przestrzenie nazw lub uruchomić narzędzie MSMerge.  
  
  Karta Windows składa się z dwóch podgrup.  
  
### <a name="core-subgroup"></a>Podgrupa podstawowa (Core)  
 Podgrupa podstawowa zawiera listę wszystkich WinMD (dla elementów wykonawczych Windows) w zestawie SDK dla docelowej wersji systemu Windows.  
  
 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] Projekty aplikacji zawierają odwołania do wszystkich winmd w [!INCLUDE[win8](../includes/win8-md.md)] zestaw SDK domyślnie przy tworzeniu projektu. W projektach zarządzanych, węzeł tylko do odczytu folderze odwołania w **Eksploratora rozwiązań** wskazuje odwołanie do całej [!INCLUDE[win8](../includes/win8-md.md)] zestawu SDK. W związku z tym podgrupa podstawowa w Menedżerze odwołań nie będzie wyliczała żadnych zestawów z [!INCLUDE[win8](../includes/win8-md.md)] zestawu SDK i zamiast tego zostanie wyświetlony komunikat: "Z zestawu Windows SDK jest już przywoływany. Użyj przeglądarki obiektów do zbadania odwołań w zestawie SDK systemu Windows”.  
  
 W projektach pulpitu. podgrupa Podstawowa nie jest wyświetlana domyślnie. Można dodać środowisko wykonawcze Windows, otwierając menu skrótów dla węzła projektu, wybierając **Zwolnij projekt**, dodając poniższy fragment kodu i ponownie otwierając projekt (w węźle projektu wybierz **Załaduj ponownie projekt**). Gdy wywołujesz **Menadżer odwołań** pojawia się podgrupa podstawowa okno dialogowe.  
  
```  
<PropertyGroup>  
  <TargetPlatformVersion>8.0</TargetPlatformVersion>  
</PropertyGroup>  
```  
  
 Upewnij się, że wybrano **Windows** pole wyboru w tej podgrupie. Wówczas można używać elementów środowiska wykonawczego Windows. Jednak warto również dodać System.Runtime, w którym środowisko wykonawcze Windows definiuje kilka standardowych klas i interfejsów, takich jak IEnumerable, które są używane we wszystkich bibliotekach uruchomieniowych Windows. Aby uzyskać informacje o dodawaniu System.Runtime, zobacz [zarządzane aplikacje pulpitu i środowisko uruchomieniowe Windows](http://msdn.microsoft.com/library/windows/apps/jj856306.aspx#consuming_standard_windows_runtime_types).  
  
### <a name="extensions-subgroup"></a>Podgrupa Rozszerzenia  
 Rozszerzenia wyświetla pakiety SDK użytkownika, które rozszerzają docelową platformę Windows. Ta karta jest wyświetlana dla [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] wyłącznie dla projektów aplikacji. Projekty pulpitu nie będzie wyświetlały tej karty, ponieważ mogą one wykorzystywać tylko pliki .winmd pierwszego producenta.  
  
 Zestaw SDK jest zbiorem plików, który program Visual Studio traktuje jako samodzielny składnik. Na karcie rozszerzenia, SDK, które są stosowane do projektu, z których **Menadżer odwołań** zostało wywołane okno dialogowe są wymienione jako pojedyncze wpisy. Po dodaniu do projektu, cała zawartość zestawu SDK jest wykorzystywana przez program Visual Studio, aby użytkownik nie musiał podejmować dalszych działań, aby wykorzystać zawartość zestawu SDK w technologii IntelliSense, przyborniku, projektantach, przeglądarce obiektów, kompilacji, wdrażaniu, debugowaniu i pakowaniu. Aby uzyskać informacje o wyświetlaniu SDK na karcie rozszerzenia, zobacz [tworzenia Software Development Kit](../extensibility/creating-a-software-development-kit.md).  
  
> [!NOTE]
> Jeśli projekt odwołuje się do zestawu SDK, który zależy od innego zestawu SDK, Visual Studio nie wykorzystuje drugiego zestawu SDK, chyba że użytkownik ręcznie doda odwołanie do drugiego zestawu SDK. Gdy użytkownik wybierze SDK na **rozszerzenia** karcie **Menadżer odwołań** okno dialogowe pomaga użytkownikowi określić zależności zestawu SDK przez wymienienie nie tylko nazwę i wersję zestawu SDK, ale także nazwy wszelkich zestawu SDK zależności w okienku szczegółów. Jeśli użytkownik nie zauważy zależności i doda tylko zestaw SDK, program MSBuild będzie monitował użytkownika, aby dodać zależności.  
  
 Jeśli typ projektu nie obsługuje **rozszerzenia**, karta nie pojawi się w **Menadżer odwołań** okno dialogowe.  
  
## <a name="browse-button"></a>Przycisk Przeglądaj  
 Możesz użyć **Przeglądaj** przycisk, aby wyszukać składnik w systemie plików.  
  
 Projekt może się odwoływać do składnika, który jest przeznaczony dla innej wersji platformy .NET Framework. Na przykład, można utworzyć aplikację, która jest przeznaczona dla .NET Framework 4 Client Profile, który odwołuje się do składnika przeznaczonego dla .NET Framework 2. Aby uzyskać więcej informacji, zobacz [przeznaczonych dla określonej wersji programu .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
 Nie należy dodawać odwołań do pliku do danych wyjściowych innego projektu w tym samym rozwiązaniu, ponieważ takie rozwiązanie może spowodować błędy kompilacji. Zamiast tego należy użyć **rozwiązania** karcie **Menadżer odwołań** okno dialogowe, aby utworzyć odwołania projekt projekt. Takie podejście ułatwia projektowanie zespołowe poprzez umożliwienie lepszego zarządzania bibliotekami klas utworzonymi w projektach. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z odwołaniami uszkodzone](../ide/troubleshooting-broken-references.md).  
  
 Nie można przejść do zestawu SDK i dodać go do projektu. Można przeglądać tylko w poszukiwaniu pliku (na przykład zestawu lub .winmd) i dodać go do projektu.  
  
 Gdy tworzysz odwołanie pliku do WinMD, oczekiwany układ jest *FileName*.winmd, *FileName*.dll i *FileName*plików .pri są umieszczane obok siebie. Jeśli odwołujesz się do WinMD w następujących scenariuszach, niepełny zestaw plików zostanie skopiowany do katalogu wyjściowego projektu i, w związku z tym, wystąpią błędy kompilacji i czasu wykonywania.  
  
- **Składnik macierzysty**: macierzysty projekt utworzy jeden WinMD dla każdego rozłącznego zestawu przestrzeni nazw i jedną bibliotekę DLL, która składa się z implementacji. Pliki WinMD będą miały odmienne nazwy. Przy odwoływaniu się do tego pliku składnika macierzystego, MSBuild nie rozpozna, że pliki WinMD o różnych nazwach stanowią jeden składnik. W związku z tym, tylko identycznie nazwane pliki *FileName*.dll i *FileName*.winmd zostaną skopiowane i wystąpią błędy czasu wykonywania. Aby obejść ten problem, należy utworzyć SDK rozszerzenia. Aby uzyskać więcej informacji, zobacz [tworzenia Software Development Kit](../extensibility/creating-a-software-development-kit.md).  
  
- **Korzystanie z kontrolek**: co najmniej formant XAML składa się z *FileName*.winmd, *FileName*.dll, *FileName*.pri, *XamlName* .xaml i *ImageName*.jpg. Gdy projekt jest kompilowany, pliki zasobów, które są skojarzone z odwołaniem do pliku nie będą otrzymywać skopiowany do katalogu wyjściowego projektu, a tylko *FileName*.winmd, *FileName*.dll i *FileName*PRI zostaną skopiowane. Błąd kompilacji jest rejestrowany, aby informować użytkownika, zasoby *XamlName*.xaml i *ImageName*brakuje .jpg. Aby kompilacja się powiodła, trzeba ręcznie skopiować te pliki zasobów do katalogu wyjściowego projektu dla kompilacji i debugowania/czasu wykonywania. Aby obejść ten problem, albo utwórz rozszerzenie SDK, wykonując kroki opisane w [tworzenia Software Development Kit](../extensibility/creating-a-software-development-kit.md) lub edytowania pliku projektu, należy dodać następującą właściwość:  
  
    ```  
    <PropertyGroup>  
    <GenerateLibraryOutput>True</GenerateLibraryOutput>  
    </PropertyGroup>  
    ```  
  
    > [!NOTE]
    > Jeśli dodasz właściwość, kompilacja może być wolniejsza.  
  
## <a name="recent"></a>Ostatnie  
 Każda z kart Zestawy, COM, Windows i Przeglądaj obsługuje kartę Najnowsze, która wylicza listę składników ostatnio dodanych do projektów.  
  
## <a name="search"></a>Wyszukaj  
 Pasek wyszukiwania w **Menadżer odwołań** okno dialogowe działa przez kartę która jest w trybie koncentracji uwagi. Na przykład, jeśli użytkownik wpisze "System" na pasku wyszukiwania, gdy **rozwiązania** karta jest w trybie koncentracji uwagi, wyszukiwanie nie zwraca żadnych wyników, chyba że rozwiązanie składa się z nazwy projektu, który zawiera "System".  
  
## <a name="see-also"></a>Zobacz też  
 [NIB jak: Dodawanie lub usuwanie odwołań za pomocą okno dialogowe Dodawanie odwołania](http://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)
