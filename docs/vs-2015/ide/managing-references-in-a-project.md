---
title: Zarządzanie odwołaniami w projekcie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ProjectPropertiesReferencePaths
- cs.ProjectPropertiesReferencePaths
helpviewer_keywords:
- Visual C# projects, references
- referencing objects, project references
- external component references
- referencing namespaces
- Visual Basic projects, references
- referencing components, external components
- Web references, types of project references
- namespaces [Visual Studio], referencing
- COM components, referencing
- objects [Visual Studio], referencing
ms.assetid: 05d1c51b-44f3-4973-8a11-6c919b08ad62
caps.latest.revision: 55
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3da4501d472949a89ad9120a07da99aaff3ebd1b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54763653"
---
# <a name="managing-references-in-a-project"></a>Zarządzanie odwołaniami w projekcie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pisanie kodu w stosunku do składnika zewnętrznego lub połączone usługi, projekt musi zawierać odwołanie do niej. Zasadniczo wpis w pliku projektu, który zawiera informacje o wymaganych przez program Visual Studio do zlokalizuj składnik lub usługa jest odwołaniem.  
  
 Aby dodać odwołanie, w węźle odwołania w Eksploratorze rozwiązań kliknij prawym przyciskiem myszy, a następnie wybierz **Dodaj odwołanie**. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).  
  
 ![Dodaj odwołanie w Visual C&#43;&#43;](../ide/media/vs2015-cpp-add-reference.png "vs2015_cpp_add_reference")  
  
 Można zrobić odnośnik do następujących typów składników i usług:  
  
-   Odwołania aplikacji Windows Store  
  
-   Biblioteki klas .NET framework lub zestawy  
  
-   COM — Składniki  
  
-   Inne zespoły lub biblioteki klas projektów w tym samym rozwiązaniu  
  
-   Usługi sieci Web XML  
  
## <a name="windows-store-app-references"></a>Odwołania aplikacji Windows Store  
  
### <a name="project-references"></a>Odwołania do projektu  
 Uniwersalne projekty platformy Windows (UWP), przeznaczonych dla systemu Windows 10 można utworzyć odwołania do innych projektów platformy uniwersalnej systemu Windows w rozwiązaniu lub do projektów Windows Store lub plików binarnych, których platformą docelową [!INCLUDE[win81](../includes/win81-md.md)]pod warunkiem, że te projekty nie należy używać interfejsów API, które zostały wycofane w systemie Windows 10. Aby uzyskać więcej informacji, zobacz [przenieść z 8 środowiska uruchomieniowego Windows do platformy uniwersalnej systemu Windows](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx).  
  
 Jeśli chcesz przekierować [!INCLUDE[win81](../includes/win81-md.md)] projektów dla systemu Windows 10, zobacz [przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)  
  
### <a name="extension-sdk-references"></a>Odwołania do zestawu SDK rozszerzenia  
 Projekty języka Visual Basic, C#, C++ i JavaScript Windows Store, przeznaczonych dla platformy Universal Windows (UWP) można odwoływać się do zestawów SDK rozszerzeń przeznaczonych [!INCLUDE[win81](../includes/win81-md.md)], tak długo, jak te zestawy SDK nie należy używać interfejsów API, które zostały zaniechane w systemie Windows 10. Sprawdź, czy witrynę dostawcy SDK rozszerzenie, aby dowiedzieć się, czy mogą być przywoływane przez projekty Windows Store przeznaczonych platformy uniwersalnej systemu Windows.  
  
 Jeśli stwierdzisz, że nie jest obsługiwany przez zestaw SDK rozszerzeń, do którego nastąpiło odwołanie przez aplikację, a następnie należy wykonać następujące czynności:  
  
1.  Sprawdź nazwę projektu, który jest przyczyną błędu. Platformy, dla której projekt jest adresowany jest podana w nawiasie obok nazwy projektu. Na przykład **Nazwamojegoprojektu (Windows 8.1)** oznacza, że projekt **Nazwamojegoprojektu** jest przeznaczony dla wersji platformy [!INCLUDE[win81](../includes/win81-md.md)].  
  
2.  Przejdź do witryny dostawcy, który jest właścicielem nieobsługiwanego zestawu SDK rozszerzeń i zainstaluj wersję zestawu SDK rozszerzeń z zależnościami, które są zgodne z wersją platformy, dla której projekt jest adresowany.  
  
    > [!NOTE]
    >  Jednym ze sposobów, aby dowiedzieć się, czy zestaw SDK rozszerzeń ma zależności od innych zestawów SDK rozszerzeń jest ponownie program Visual Studio, Utwórz nowy projekt C# Windows Store, kliknij prawym przyciskiem myszy nad projektem i wybierz **Dodaj odwołanie**, przejdź do  **Windows** karty, wróć do **rozszerzenia** podkartę, zaznacz SDK rozszerzeń i przyjrzyj się okienku po prawej stronie w **Menadżer odwołań**. Jeśli ma zależności, zostaną wyświetlone istnieje.  
  
    > [!IMPORTANT]
    >  Jeśli projekt jest przeznaczony dla systemu Windows 10 oraz zestaw SDK rozszerzeń zainstalowany w poprzednim kroku ma zależność od pakietu Microsoft Visual C++ Runtime wersja pakietu Microsoft Visual C++ Runtime zgodnego z systemem Windows 10 jest v14.0 i jest zainstalowany za pomocą programu Visual Studio 2015.  
  
3.  Jeśli zestaw SDK rozszerzeń zainstalowany w poprzednim kroku ma zależności od innych zestawów SDK rozszerzeń, przejdź do witryn dostawców, którzy są właścicielami zależności i zainstaluj wersje tych zależności, które są zgodne z wersją platformy, usługi Projekt jest adresowany.  
  
4.  Uruchom ponownie program Visual Studio i Otwórz swoją aplikację.  
  
5.  Kliknij prawym przyciskiem myszy **odwołania** węzeł w projekcie, który spowodował błąd, a następnie wybierz **Dodaj odwołanie**  
  
6.  Kliknij przycisk **Windows** kartę i następnie **rozszerzenia** podkartę, a następnie usuń zaznaczenie pola wyboru dla starego rozszerzenie SDK i zaznacz pola wyboru dla nowego rozszerzenie SDK. Kliknij przycisk **OK**.  
  
## <a name="adding-a-reference-at-design-time"></a>Dodawanie odwołania w czasie projektowania  
 Po wprowadzeniu odwołania do zestawu w projekcie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wyszukuje zestaw w następujących lokalizacjach:  
  
-   Katalog aktualnego projektu. (Zestawy te można znaleźć przy użyciu **Przeglądaj** karty.)  
  
-   Inne katalogi projektu w tym samym rozwiązaniu. (Zestawy te można znaleźć na **projektów** karty.)  
  
> [!NOTE]
>  Wszystkie projekty zawierają odwołanie domniemane do mscorlib. Projekty języka Visual Basic zawierają odwołanie domniemane do `Microsoft.VisualBasic`.  
>   
>  Wszystkie projekty w programie Visual Studio zawierają odwołanie domniemane do `System.Core`nawet wtedy, gdy `System.Core` zostanie usunięty z listy odwołań.  
  
## <a name="references-to-shared-components-at-run-time"></a>Odwołania do udostępnionych składników w czasie wykonywania  
 W czasie wykonywania, składniki muszą się znajdować albo w ścieżce wyjściowej projektu lub w [Global Assembly Cache](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) (GAC). Jeśli projekt zawiera odwołanie do obiektu, który nie znajduje się w jednej z tych lokalizacji, należy skopiować odwołanie do ścieżki wyjściowej projektu podczas kompilowania projektu. <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> Właściwość wskazuje, czy ta kopia musi zostać wykonana. Jeśli wartość jest **True**, odwołanie jest kopiowane do katalogu projektu podczas kompilowania projektu. Jeśli wartość jest **False**, odwołanie nie jest kopiowany.  
  
 W przypadku wdrożenia aplikacji, która zawiera odwołanie do składnika niestandardowego, który jest zarejestrowany w globalnej pamięci podręcznej zestawów, składnik nie zostanie wdrożony z aplikacją, bez względu na to <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> ustawienie. We wcześniejszych wersjach programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], można ustawić <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> właściwość w odwołaniu do zapewnienia, że zestaw został wdrożony. Teraz należy ręcznie dodać zestaw do folderu \Bin. Spowoduje to umieszczenie całego kodu niestandardowego, w ramach kontroli, zmniejszając ryzyko publikowania kodu niestandardowego za pomocą którego użytkownik nie jest zaznajomiony.  
  
 Domyślnie <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> właściwość jest ustawiona na **False** Jeśli zestaw lub składnik znajduje się w globalnej pamięci podręcznej lub jest składnikiem struktury. W przeciwnym razie wartość jest równa **True**. Odwołania projektu do projektu są zawsze ustawione na **True**.  
  
## <a name="referencing-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Odwołanie do projektu lub zestawu, który jest przeznaczony dla innej wersji programu .NET Framework  
 Możesz tworzyć aplikacje, które odwołują się projektów lub zestawów, których docelowa była inna wersja programu .NET Framework. Na przykład, możesz utworzyć aplikację przeznaczonego [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] która odwołuje się do zestawu, który jest przeznaczony dla [!INCLUDE[dnprdnext](../includes/dnprdnext-md.md)]. Jeśli tworzysz projekt, który jest przeznaczony dla starszej wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], nie można ustawić odwołania w tym projekcie do projektu lub zestawu przeznaczonego [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] lub .NET Framework w wersji 4.  
  
 Aby uzyskać więcej informacji, zobacz [przeznaczonych dla określonej wersji programu .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
## <a name="project-to-project-references"></a>Odwołania projektu do projektu  
 Odwołania projektu do projektu są odwołaniami do projektów, które zawierają zestawy; Tworzenie przy użyciu **projektu** kartę. Program Visual Studio można znaleźć zestawu przy podanej ścieżki do projektu.  
  
 Jeśli masz projekt, który tworzy zestaw, należy odwoływać się do projektu i używaj odwołanie do pliku (patrz poniżej). Zaletą odwołania projektu do projektu jest to, że tworzy ono zależność między projektami w systemie kompilacji. Projekt zależny zostanie skompilowany, jeśli została zmieniona od czasu ostatniego konstruowania projektu z odwołaniem. Odwołanie pliku nie tworzy zależność kompilacji, więc istnieje możliwość skompilowania projektu z odwołaniem bez kompilowania projektu zależnego, a odwołanie może się okazać zbędne. (Oznacza to, że projekt może odwoływać się do uprzednio utworzonej wersji projektu.) Może to spowodować, że kilka wersjach pojedynczego pliku DLL jest wymagana w katalogu bin, który nie jest możliwe. Po wystąpieniu takiego konfliktu pojawi komunikat takich jak [Ostrzeżenie: nie można skopiować zależności 'Plik' w projekcie 'projekt' do katalogu uruchomienia, ponieważ zastąpiłaby ona odwołanie 'Plik'. ](/visualstudio/vs-2015/misc/warning-the-dependency-file-in-project-project-cannot-be-copied). Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z odwołaniami uszkodzone](../ide/troubleshooting-broken-references.md) i [jak: Tworzenie i usuwanie zależności projektu](../ide/how-to-create-and-remove-project-dependencies.md).  
  
> [!NOTE]
>  Odwołanie pliku zamiast odwołania projektu do projektu jest tworzony, jeśli wersji docelowej programu .NET Framework jednego projektu jest wersja 4.5 i wersję docelową innego projektu jest w wersji 2, 3, 3.5 lub 4.0.  
  
## <a name="file-references"></a>Odwołania do pliku  
 Odwołania do plików są bezpośrednimi odwołaniami do zestawów poza kontekstem projektu programu Visual Studio; Tworzenie przy użyciu **Przeglądaj** karcie **Menadżer odwołań**. Użyj odwołania pliku po po prostu zestaw lub składnik i nie masz projektu, który tworzy go jako dane wyjściowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązywanie problemów z przerwanymi odwołaniami](../ide/troubleshooting-broken-references.md)   
 [Programowanie za pomocą zestawów](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6)   
 [Instrukcje: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
