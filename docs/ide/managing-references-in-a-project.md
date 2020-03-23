---
title: Zarządzanie odwołaniami w projekcie
ms.date: 08/02/2019
ms.topic: conceptual
f1_keywords:
- vs.ProjectPropertiesReferencePaths
- cs.ProjectPropertiesReferencePaths
helpviewer_keywords:
- C# projects, references
- referencing objects, project references
- external component references
- referencing namespaces
- Visual Basic projects, references
- referencing components, external components
- Web references, types of project references
- namespaces [Visual Studio], referencing
- COM components, referencing
- objects [Visual Studio], referencing
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9623e8ffb6a315851d26cd06defb62899e429f44
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591258"
---
# <a name="manage-references-in-a-project"></a>Zarządzanie odwołaniami w projekcie

Przed napisaniem kodu względem zewnętrznego składnika lub połączonej usługi, projekt musi najpierw zawierać odwołanie do niego. Odwołanie jest zasadniczo wpis w pliku projektu, który zawiera informacje, które Visual Studio musi zlokalizować składnika lub usługi.

Aby dodać odwołanie, kliknij prawym przyciskiem myszy węzeł **Odwołania** lub **zależności** w **Eksploratorze rozwiązań** i wybierz polecenie **Dodaj odwołanie**. Można również kliknąć prawym przyciskiem myszy węzeł projektu i wybrać pozycję **Dodaj** > **odwołanie**. Aby uzyskać więcej informacji, zobacz [Jak: Dodawanie lub usuwanie odwołań](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

![Dodawanie odwołania w&#43;&#43; visual C](../ide/media/vs2015_cpp_add_reference.png)

Odwołanie można dodać do następujących typów składników i usług:

- Biblioteki lub zestawy klas .NET

- Aplikacje platformy UWP

- COM — Składniki

- Inne zestawy lub biblioteki klas projektów w tym samym rozwiązaniu

- Projekty udostępnione

- Usługi sieci Web XML

## <a name="uwp-app-references"></a>Odwołania do aplikacji platformy uniwersalnej systemu i platformy uniwersalnej systemu

### <a name="project-references"></a>Odwołania projektu

Projekty platformy uniwersalnej systemu Windows (UWP) mogą tworzyć odwołania do innych projektów platformy uniwersalnej systemu Windows w rozwiązaniu lub do projektów lub plików binarnych systemu Windows 8.1, pod warunkiem że projekty te nie używają interfejsów API, które zostały przestarzałe w systemie Windows 10. Aby uzyskać więcej informacji, zobacz [Przenoszenie z środowiska wykonawczego systemu Windows 8 na platformę uniwersalną](/windows/uwp/porting/w8x-to-uwp-root)systemu Windows .

Jeśli zdecydujesz się ponownie kierować projekty systemu Windows 8.1 do systemu Windows 10, zobacz [Port, migracja i uaktualnienie projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md).

### <a name="extension-sdk-references"></a>Odwołania do sdk rozszerzeń

Aplikacje visual basic, C#, C++ i JavaScript Universal Windows Platform (UWP) mogą odwoływać się do zestawów SDK rozszerzeń docelowych dla systemu Windows 8.1, o ile te zestawy SDK rozszerzeń nie używają interfejsów API, które zostały przestarzałe w systemie Windows 10. Sprawdź witrynę dostawcy SDK rozszerzenia, aby dowiedzieć się, czy mogą się do niego odwoływać aplikacje platformy uniwersalnej systemu Windows.

Jeśli stwierdzisz, że SDK rozszerzenia, do którego odwołuje się aplikacja, nie jest obsługiwany, musisz wykonać następujące kroki:

1. Spójrz na nazwę projektu, który jest przyczyną błędu. Platforma, na która kierowana jest platforma, na która jest kierowana przez projekt, jest zanotowana w nawiasach obok nazwy projektu. Na przykład **MyProjectName (Windows 8.1)** oznacza, że projekt **MyProjectName** jest przeznaczony dla platformy w wersji systemu Windows 8.1.

1. Przejdź do witryny dostawcy, który jest właścicielem nieobsługiwał sdk rozszerzenia i zainstalować wersję SDK rozszerzenia z zależności, które są zgodne z wersją platformy projektu jest kierowane.

    > [!NOTE]
    > Jednym ze sposobów, aby dowiedzieć się, czy SDK rozszerzenia ma zależności od innych SDK rozszerzenia jest patrząc w **Menedżerze odwołań**. Uruchom ponownie program Visual Studio, utwórz nowy projekt aplikacji platformy uniwersalnej systemu Wielowładnego w języku C#, a następnie kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj odwołanie**. Przejdź do karty **Windows,** a następnie podna karcie **Rozszerzenia** i wybierz sdk rozszerzeń. Spójrz na prawe okienko w **Menedżerze odwołań**. Jeśli ma zależności, zostaną one tam wymienione.

    > [!IMPORTANT]
    > Jeśli projekt jest ukierunkowany na system Windows 10, a pakiet SDK rozszerzenia zainstalowany w poprzednim kroku ma zależność od pakietu wykonawczego programu Microsoft Visual C++, wersja pakietu wykonawczego programu Microsoft Visual C++ zgodna z systemem Windows 10 jest w wersji 14.0 i jest zainstalowana z programem Visual Studio.

1. Jeśli pakiet SDK rozszerzenia zainstalowany w poprzednim kroku ma zależności od innych pakietów SDK rozszerzeń, przejdź do witryn dostawców, którzy są właścicielami zależności, i zainstaluj wersje tych zależności, które są zgodne z wersją platformy, na której jest projekt. Kierowania.

1. Uruchom ponownie program Visual Studio i otwórz aplikację.

1. Kliknij prawym przyciskiem myszy węzeł **Odwołania** lub **zależności** w projekcie, który spowodował błąd, i wybierz polecenie **Dodaj odwołanie**.

1. Kliknij kartę **Windows,** a następnie pod kartę **Rozszerzenia,** a następnie wyewidencjonuj pola wyboru starych zestawów SDK rozszerzeń i sprawdź pola wyboru dla nowych zestawów SDK rozszerzeń. Kliknij przycisk **OK**.

## <a name="add-a-reference-at-design-time"></a>Dodawanie odwołania w czasie projektowania

Po dodaniu odwołania do zestawu w projekcie visual studio wyszukuje zestaw w następujących lokalizacjach:

- Bieżący katalog projektów. (Te zestawy można znaleźć za pomocą karty **Przeglądaj).**

- Inne katalogi projektów w tym samym rozwiązaniu. (Te zestawy można znaleźć na karcie **Projekty).**

> [!NOTE]
> - Wszystkie projekty zawierają dorozumiane odwołanie do **mscorlib**.
> - Wszystkie projekty zawierają dorozumiane odwołanie do `System.Core`, nawet jeśli `System.Core` jest usuwany z listy odwołań.
> - Projekty języka Visual Basic <xref:Microsoft.VisualBasic>zawierają dorozumiane odwołanie do .

## <a name="references-to-shared-components-at-run-time"></a>Odwołania do udostępnionych składników w czasie wykonywania

W czasie wykonywania składniki muszą znajdować się w ścieżce wyjściowej projektu lub w globalnej pamięci podręcznej zestawów (GAC). Jeśli projekt zawiera odwołanie do obiektu, który nie znajduje się w jednej z tych lokalizacji, należy skopiować odwołanie do ścieżki wyjściowej projektu podczas tworzenia projektu. Właściwość <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> wskazuje, czy ta kopia musi być wykonana. Jeśli wartość **true**, odwołanie jest kopiowane do katalogu projektu podczas tworzenia projektu. Jeśli wartość jest **False**, odwołanie nie jest kopiowane.

Jeśli wdrożysz aplikację, która zawiera odwołanie do składnika niestandardowego, który jest zarejestrowany w pliku GAC, <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> składnik nie zostanie wdrożony z aplikacją, niezależnie od ustawienia. We wcześniejszych wersjach programu Visual <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> Studio można ustawić właściwość na odwołanie, aby upewnić się, że zestaw został wdrożony. Teraz należy ręcznie dodać zespół do folderu \Bin. To stawia cały kod niestandardowy pod kontrolą, zmniejszając ryzyko publikowania kodu niestandardowego, z którym nie są znane.

Domyślnie właściwość jest <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> **ustawiona** na False, jeśli zestaw lub komponent znajduje się w globalnej pamięci podręcznej zestawów lub jest składnikiem struktury. W przeciwnym razie wartość jest ustawiona na **True**. Odwołania do projektu są zawsze ustawione na **Wartość True**.

## <a name="reference-a-project-or-assembly-that-targets-a-different-version-of-net"></a>Odwoływanie się do projektu lub zestawu przeznaczonego dla innej wersji platformy .NET

Można tworzyć aplikacje, które odwołują się do projektów lub zestawów, które są przeznaczone dla innej wersji platformy .NET. Na przykład można utworzyć aplikację, która jest przeznaczona dla platformy .NET Framework 4.6, która odwołuje się do zestawu przeznaczonego dla platformy .NET Framework 4.5. Jeśli utworzysz projekt, który jest przeznaczony dla wcześniejszej wersji platformy .NET, nie można ustawić odwołania w tym projekcie do projektu lub zestawu, który jest przeznaczony dla nowszej wersji.

Aby uzyskać więcej informacji, zobacz [omówienie kierowania na ramy](../ide/visual-studio-multi-targeting-overview.md).

## <a name="project-to-project-references"></a>Odwołania do projektu

Odwołania do projektu są odwołaniami do projektów, które zawierają zestawy; odwołania do projektu można dodawać za pomocą karty **Projekty** w oknie dialogowym Menedżer odwołań. Visual Studio można znaleźć zestaw, gdy dana ścieżka do projektu.

Jeśli masz projekt, który tworzy zestaw, należy odwołać się do projektu i nie używać odwołania do pliku (patrz poniżej). Zaletą odwołania projektu do projektu jest to, że tworzy zależność między projektami w systemie kompilacji. Projekt zależny zostanie zbudowany, jeśli zmienił się od czasu ostatniego zbudowanego projektu odwołującego się. Odwołanie do pliku nie tworzy zależności kompilacji, więc jest możliwe do tworzenia projektu odwołującego się bez tworzenia projektu zależnego, a odwołanie może stać się przestarzałe. (Oznacza to, że projekt może odwoływać się do wcześniej utworzonej wersji projektu.) Może to spowodować, że kilka wersji pojedynczej biblioteki DLL jest wymagane w katalogu *bin,* co nie jest możliwe. Gdy wystąpi ten konflikt, zostanie wyświetlony komunikat, taki jak "Ostrzeżenie: zależność 'plik' w projekcie 'project' nie może być skopiowany do katalogu uruchamiania, ponieważ zastąpi odwołanie 'file.'". Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z uszkodzonymi odwołaniami](../ide/troubleshooting-broken-references.md) i [jak: Tworzenie i usuwanie zależności projektu](../ide/how-to-create-and-remove-project-dependencies.md).

> [!NOTE]
> Odwołanie do pliku zamiast odwołania do projektu jest tworzony, jeśli wersja docelowa .NET Framework jednego projektu jest w wersji 4.5, a wersja docelowa innego projektu jest w wersji 2, 3, 3.5 lub 4.0.

## <a name="shared-project-references"></a>Udostępnione odwołania do projektu

W przeciwieństwie do większości innych typów projektów *udostępnionego projektu* nie ma żadnych danych binarnych. Zamiast tego kod jest kompilowany do każdego projektu, który odwołuje się do niego. [Udostępnione projekty](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) umożliwiają pisanie wspólnego kodu, do którego odwołuje się wiele różnych projektów aplikacji. Kod jest kompilowany jako część każdego projektu odwołującego się i może zawierać dyrektywy kompilatora, aby ułatwić włączenie funkcji specyficznych dla platformy do bazy kodu udostępnionego. Dodaj odwołanie do udostępnionego projektu na karcie **Projekty udostępnione** w oknie dialogowym Menedżer odwołań.

## <a name="file-references"></a>Odwołania do plików

Odwołania do plików są bezpośrednie odwołania do zestawów poza kontekstem projektu programu Visual Studio. Można je utworzyć za pomocą karty **Przeglądaj** w oknie dialogowym Menedżer odwołań. Użyj odwołania do pliku, gdy masz tylko złożenia lub składnika, a nie projekt, który tworzy go jako dane wyjściowe.

## <a name="see-also"></a>Zobacz też

- [Rozwiązywanie problemów z przerwanymi odwołaniami](../ide/troubleshooting-broken-references.md)
- [Jak: Dodawanie lub usuwanie odwołań](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
