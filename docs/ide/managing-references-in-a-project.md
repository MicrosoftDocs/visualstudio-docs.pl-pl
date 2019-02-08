---
title: Zarządzanie odwołaniami w projekcie
ms.date: 04/11/2018
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d04e5703c96b710208cc1ecc79a169a458463497
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55921058"
---
# <a name="manage-references-in-a-project"></a>Zarządzanie odwołaniami w projekcie

Pisanie kodu w stosunku do składnika zewnętrznego lub połączone usługi, projekt musi zawierać odwołanie do niej. Zasadniczo wpis w pliku projektu, który zawiera informacje o wymaganych przez program Visual Studio do zlokalizuj składnik lub usługa jest odwołaniem.

Aby dodać odwołanie, kliknij prawym przyciskiem myszy **odwołania** lub **zależności** węzła w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj odwołanie**. Możesz również kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Dodaj** > **odwołania**. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie lub usuwanie odwołań](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

![Dodaj odwołanie w Visual C&#43;&#43;](../ide/media/vs2015_cpp_add_reference.png)

Można dodać odwołania do następujących typów składników i usług:

- Biblioteki klas .NET framework lub zestawy

- Aplikacje platformy uniwersalnej systemu Windows

- COM — Składniki

- Inne zespoły lub biblioteki klas projektów w tym samym rozwiązaniu

- Usługi sieci Web XML

## <a name="uwp-app-references"></a>Odwołania do aplikacji platformy uniwersalnej systemu Windows

### <a name="project-references"></a>Odwołania do projektu

Uniwersalne projekty platformy Windows (UWP) można utworzyć odwołania do innych projektów platformy uniwersalnej systemu Windows w rozwiązaniu lub do projektów Windows 8.1 lub plików binarnych, pod warunkiem, że te projekty nie używają interfejsów API, które zostały zaniechane w systemie Windows 10. Aby uzyskać więcej informacji, zobacz [przenieść z 8 środowiska uruchomieniowego Windows do platformy uniwersalnej systemu Windows](/windows/uwp/porting/w8x-to-uwp-root).

Jeśli chcesz przekierować projekty Windows 8.1 do systemu Windows 10, zobacz [Port, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md).

### <a name="extension-sdk-references"></a>Odwołania do zestawu SDK rozszerzenia

Visual Basic C#, C++ i JavaScript Windows platformy Uniwersalnej aplikacji może odwoływać się zestawów SDK rozszerzeń, przeznaczonych dla Windows 8.1, tak długo, jak te zestawy SDK nie należy używać interfejsów API, które zostały zaniechane w systemie Windows 10. Sprawdź, czy witrynę dostawcy SDK rozszerzenie, aby dowiedzieć się, czy mogą być przywoływane przez aplikacje platformy uniwersalnej systemu Windows.

Jeśli stwierdzisz, że nie jest obsługiwany przez zestaw SDK rozszerzeń, do którego nastąpiło odwołanie przez aplikację, a następnie należy wykonać następujące czynności:

1. Sprawdź nazwę projektu, który jest przyczyną błędu. Platformy, dla której projekt jest adresowany jest podana w nawiasie obok nazwy projektu. Na przykład **Nazwamojegoprojektu (Windows 8.1)** oznacza, że projekt **Nazwamojegoprojektu** jest przeznaczony dla wersji platformy Windows 8.1.

1. Przejdź do witryny dostawcy, który jest właścicielem nieobsługiwanego zestawu SDK rozszerzeń, a następnie zainstalować wersję zestawu SDK rozszerzeń z zależnościami, które są zgodne z wersją platformy, dla której projekt jest adresowany.

    > [!NOTE]
    > Jednym ze sposobów, aby dowiedzieć się, czy zestaw SDK rozszerzeń ma zależności od innych zestawów SDK rozszerzeń jest wyszukiwanie w **Menadżer odwołań**. Uruchom ponownie program Visual Studio, Utwórz nową C# aplikacji platformy uniwersalnej systemu Windows projektu, a następnie kliknij prawym przyciskiem myszy nad projektem i wybierz **Dodaj odwołanie**. Przejdź do **Windows** kartę, a następnie **rozszerzenia** karcie podrzędnej, a następnie wybierz zestaw SDK rozszerzeń. Przyjrzyj się okienku po prawej stronie w **Menadżer odwołań**. Jeśli ma zależności, zostaną wyświetlone istnieje.

    > [!IMPORTANT]
    > Jeśli projekt jest przeznaczony dla systemu Windows 10 oraz zestaw SDK rozszerzeń zainstalowany w poprzednim kroku ma zależność od pakietu Microsoft Visual C++ Runtime wersja pakietu Microsoft Visual C++ Runtime zgodnego z systemem Windows 10 jest v14.0 i jest zainstalowany za pomocą programu Visual Studio.

1. Jeśli zestaw SDK rozszerzeń zainstalowany w poprzednim kroku ma zależności od innych zestawów SDK rozszerzeń, przejdź do witryn dostawców, którzy są właścicielami zależności, a następnie zainstaluj wersje tych zależności, które są zgodne z wersją platformy, dla której projekt jest Określanie wartości docelowej.

1. Uruchom ponownie program Visual Studio i Otwórz swoją aplikację.

1. Kliknij prawym przyciskiem myszy **odwołania** lub **zależności** węzeł w projekcie, który spowodował błąd, a następnie wybierz **Dodaj odwołanie**.

1. Kliknij przycisk **Windows** kartę i następnie **rozszerzenia** podkartę, a następnie usuń zaznaczenie pola wyboru dla starego rozszerzenie SDK i zaznacz pola wyboru dla nowego rozszerzenie SDK. Kliknij przycisk **OK**.

## <a name="add-a-reference-at-design-time"></a>Dodaj odwołanie w czasie projektowania

Po wprowadzeniu odwołania do zestawu w projekcie programu Visual Studio wyszukuje zestaw w następujących lokalizacjach:

- Katalog aktualnego projektu. (Zestawy te można znaleźć przy użyciu **Przeglądaj** karty.)

- Inne katalogi projektu w tym samym rozwiązaniu. (Zestawy te można znaleźć na **projektów** karty.)

> [!NOTE]
> - Wszystkie projekty zawierają odwołanie domniemane do **mscorlib**.
> - Wszystkie projekty zawierają odwołanie domniemane do `System.Core`nawet wtedy, gdy `System.Core` zostanie usunięty z listy odwołań.
> - Projekty języka Visual Basic zawierają odwołanie domniemane do <xref:Microsoft.VisualBasic>.

## <a name="references-to-shared-components-at-run-time"></a>Odwołania do udostępnionych składników w czasie wykonywania

W czasie wykonywania składniki musi być w ścieżce wyjściowej projektu lub w globalnej pamięci podręcznej zestawów (GAC). Jeśli projekt zawiera odwołanie do obiektu, który nie znajduje się w jednej z tych lokalizacji, należy skopiować odwołanie do ścieżki wyjściowej projektu podczas kompilowania projektu. <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> Właściwość wskazuje, czy ta kopia musi zostać wykonana. Jeśli wartość jest **True**, odwołanie jest kopiowane do katalogu projektu podczas kompilowania projektu. Jeśli wartość jest **False**, odwołanie nie jest kopiowany.

W przypadku wdrożenia aplikacji, która zawiera odwołanie do składnika niestandardowego, który jest zarejestrowany w globalnej pamięci podręcznej zestawów, składnik nie zostanie wdrożony z aplikacją, bez względu na to <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> ustawienie. We wcześniejszych wersjach programu Visual Studio, można ustawić <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> właściwość w odwołaniu do zapewnienia, że zestaw został wdrożony. Teraz należy ręcznie dodać zestaw do folderu \Bin. Spowoduje to umieszczenie całego kodu niestandardowego, w ramach kontroli, zmniejszając ryzyko publikowania kodu niestandardowego za pomocą którego użytkownik nie jest zaznajomiony.

Domyślnie <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> właściwość jest ustawiona na **False** Jeśli zestaw lub składnik znajduje się w globalnej pamięci podręcznej lub jest składnikiem struktury. W przeciwnym razie wartość jest równa **True**. Odwołania projektu do projektu są zawsze ustawione na **True**.

## <a name="reference-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Odwołania projektu lub zestawu, który jest przeznaczony dla innej wersji programu .NET Framework

Możesz tworzyć aplikacje, które odwołują się projektów lub zestawów, których docelowa była inna wersja programu .NET Framework. Na przykład można utworzyć aplikację współpracującego .NET Framework 4.6, które odwołuje się do zestawu, który jest przeznaczony dla .NET Framework 4.5. Jeśli tworzysz projekt, który jest przeznaczony dla starszej wersji programu .NET Framework, nie można ustawić odwołania w tym projekcie do projektu lub zestawu, który jest przeznaczony dla nowszej wersji.

Aby uzyskać więcej informacji, zobacz [wielowersyjnością kodu – Przegląd](../ide/visual-studio-multi-targeting-overview.md).

## <a name="project-to-project-references"></a>Odwołania do projektu do projektu

Odwołania projektu do projektu są odwołaniami do projektów, które zawierają zestawy; Tworzenie przy użyciu **projektu** kartę. Program Visual Studio można znaleźć zestawu przy podanej ścieżki do projektu.

Jeśli masz projekt, który tworzy zestaw, należy odwoływać się do projektu i używaj odwołanie do pliku (patrz poniżej). Zaletą odwołania projektu do projektu jest to, że tworzy ono zależność między projektami w systemie kompilacji. Projekt zależny zostanie skompilowany, jeśli została zmieniona od czasu ostatniego konstruowania projektu z odwołaniem. Odwołanie pliku nie tworzy zależność kompilacji, więc istnieje możliwość skompilowania projektu z odwołaniem bez kompilowania projektu zależnego, a odwołanie może się okazać zbędne. (Oznacza to, że projekt może odwoływać się do uprzednio utworzonej wersji projektu.) Może to spowodować kilka wersjach pojedynczego pliku DLL jest wymagany w *bin* katalogu, który nie jest możliwe. Po wystąpieniu takiego konfliktu pojawi komunikat takich jak "Ostrzeżenie: nie można skopiować zależności 'Plik' w projekcie 'projekt' do katalogu uruchomienia, ponieważ zastąpiłaby ona odwołanie 'Plik'.". Aby uzyskać więcej informacji, zobacz [rozwiązywanie uszkodzenie odwołań](../ide/troubleshooting-broken-references.md) i [jak: Tworzenie i usuwanie zależności projektu](../ide/how-to-create-and-remove-project-dependencies.md).

> [!NOTE]
> Odwołanie pliku zamiast odwołania projektu do projektu jest tworzony, jeśli wersji docelowej programu .NET Framework jednego projektu jest wersja 4.5 i wersję docelową innego projektu jest w wersji 2, 3, 3.5 lub 4.0.

## <a name="file-references"></a>Odwołania do pliku

Odwołania do plików są bezpośrednimi odwołaniami do zestawów poza kontekstem projektu programu Visual Studio. Tworzenie przy użyciu **Przeglądaj** karcie **Menadżer odwołań**. Odwołanie do pliku należy użyć, gdy konieczne jest tylko zestaw lub składnik, a nie projekt, który tworzy go jako dane wyjściowe.

## <a name="see-also"></a>Zobacz także

- [Rozwiązywanie problemów z przerwanymi odwołaniami](../ide/troubleshooting-broken-references.md)
- [Instrukcje: Dodawanie lub usuwanie odwołań](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
