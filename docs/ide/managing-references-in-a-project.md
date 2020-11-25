---
title: Zarządzanie odwołaniami w projekcie
description: Dowiedz się, jak zarządzać odwołaniami do składników zewnętrznych i połączonych usług w projekcie.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: fdf737d26ec14c2a108125425a3b66cdf4a0e519
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "95870953"
---
# <a name="manage-references-in-a-project"></a>Zarządzanie odwołaniami w projekcie

Przed napisaniem kodu w składniku zewnętrznym lub połączonej usłudze, projekt musi zawierać odwołanie do niego. Odwołanie jest zasadniczo wpisem w pliku projektu, który zawiera informacje, które program Visual Studio musi zlokalizować składnik lub usługę.

Aby dodać odwołanie, kliknij prawym przyciskiem myszy węzeł **odwołania** lub **zależności** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj odwołanie**. Możesz również kliknąć prawym przyciskiem myszy węzeł projektu i wybrać polecenie **Dodaj**  >  **odwołanie**. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie lub usuwanie odwołań](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

![Dodaj odwołanie w&#43;&#43; Visual C](../ide/media/vs2015_cpp_add_reference.png)

Można dodać odwołanie do następujących typów składników i usług:

- Biblioteki lub zestawy klas .NET

- Aplikacje platformy UWP

- COM — Składniki

- Inne zestawy lub biblioteki klas projektów w tym samym rozwiązaniu

- Projekty udostępnione

- Usługi sieci Web XML

## <a name="uwp-app-references"></a>Odwołania do aplikacji platformy UWP

### <a name="project-references"></a>Odwołania projektu

Projekty platforma uniwersalna systemu Windows (platformy UWP) mogą tworzyć odwołania do innych projektów platformy UWP w rozwiązaniu lub Windows 8.1 projektów lub plików binarnych, pod warunkiem, że te projekty nie używają interfejsów API przestarzałych w systemie Windows 10. Aby uzyskać więcej informacji, zobacz [przenoszenie z środowisko wykonawcze systemu Windows 8 do platformy UWP](/windows/uwp/porting/w8x-to-uwp-root).

Jeśli zdecydujesz się przekierować projekty Windows 8.1 do systemu Windows 10, zobacz [port, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md).

### <a name="extension-sdk-references"></a>Odwołania do zestawu SDK rozszerzeń

Aplikacje Visual Basic, C#, C++ i JavaScript platforma uniwersalna systemu Windows (platformy UWP) mogą odwoływać się do zestawów SDK rozszerzeń, które są przeznaczone dla Windows 8.1, pod warunkiem, że te zestawy SDK rozszerzenia nie używają interfejsów API przestarzałych w systemie Windows 10. Sprawdź witrynę dostawcy zestawu SDK rozszerzenia, aby dowiedzieć się, czy można odwoływać się do niej aplikacje platformy UWP.

Jeśli określisz, że zestaw SDK, do którego odwołuje się aplikacja, nie jest obsługiwany, należy wykonać następujące czynności:

1. Spójrz na nazwę projektu, który powoduje błąd. Platforma, do której należy projekt, jest zapisywana w nawiasach obok nazwy projektu. Na przykład, **. ProjectName (Windows 8.1)** oznacza, że projekt **ProjectName jest** ukierunkowany na wersję platformy Windows 8.1.

1. Przejdź do lokacji dostawcy, który jest właścicielem nieobsługiwanego zestawu SDK rozszerzenia, i Zainstaluj wersję zestawu SDK rozszerzenia z zależnościami, które są zgodne z wersją platformy, dla której projekt jest docelowy.

    > [!NOTE]
    > Jednym ze sposobów ustalenia, czy rozszerzenie SDK ma zależności od innych zestawów SDK rozszerzeń, jest wyszukiwanie w **Menedżerze odwołań**. Uruchom ponownie program Visual Studio, Utwórz nowy projekt aplikacji C# platformy UWP, a następnie kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj odwołanie**. Przejdź do karty **Windows** , a następnie podkartę **rozszerzenia** i wybierz zestaw SDK rozszerzenia. Poszukaj w prawym okienku w **Menedżerze odwołań**. Jeśli ma zależności, zostaną one wyświetlone.

    > [!IMPORTANT]
    > Jeśli projekt jest przeznaczony dla systemu Windows 10, a rozszerzenie SDK zainstalowane w poprzednim kroku ma zależność od pakietu środowiska uruchomieniowego Microsoft Visual C++, wersja pakietu Microsoft Visual C++ Runtime, która jest zgodna z systemem Windows 10, to v 14.0 i jest instalowana z programem Visual Studio.

1. Jeśli zestaw SDK rozszerzenia zainstalowany w poprzednim kroku ma zależności od innych zestawów SDK rozszerzeń, przejdź do witryn dostawców, którzy są właścicielami zależności, i zainstaluj wersje tych zależności, które są zgodne z wersją platformy, do której należy projekt.

1. Uruchom ponownie program Visual Studio i Otwórz aplikację.

1. Kliknij prawym przyciskiem myszy węzeł **odwołania** lub **zależności** w projekcie, który spowodował błąd, i wybierz polecenie **Dodaj odwołanie**.

1. Kliknij kartę **Windows** , a następnie podkartę **rozszerzenia** , usuń zaznaczenie pól wyboru dla starych zestawów SDK rozszerzeń i zaznacz pola wyboru dla nowych zestawów SDK rozszerzenia. Kliknij przycisk **OK**.

## <a name="add-a-reference-at-design-time"></a>Dodaj odwołanie w czasie projektowania

Po wprowadzeniu odwołania do zestawu w projekcie program Visual Studio wyszukuje zestaw w następujących lokalizacjach:

- Bieżący katalog projektu. (Zestawy te można znaleźć za pomocą karty **Przeglądaj** ).

- Inne katalogi projektu w tym samym rozwiązaniu. (Te zestawy można znaleźć na karcie **projekty** ).

> [!NOTE]
> - Wszystkie projekty zawierają implikowane odwołanie do **biblioteki mscorlib**.
> - Wszystkie projekty zawierają implikowane odwołanie do `System.Core` , nawet jeśli `System.Core` jest usuwany z listy odwołań.
> - Projekty Visual Basic zawierają implikowane odwołanie do <xref:Microsoft.VisualBasic> .

## <a name="references-to-shared-components-at-run-time"></a>Odwołania do współużytkowanych składników w czasie wykonywania

W czasie wykonywania składniki muszą znajdować się w ścieżce wyjściowej projektu lub w globalnej pamięci podręcznej zestawów (GAC). Jeśli projekt zawiera odwołanie do obiektu, który nie znajduje się w jednej z tych lokalizacji, należy skopiować odwołanie do ścieżki wyjściowej projektu podczas kompilowania projektu. <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A>Właściwość wskazuje, czy należy wykonać tę kopię. Jeśli wartość jest **równa true**, odwołanie jest kopiowane do katalogu projektu podczas kompilowania projektu. Jeśli wartość jest równa **false**, odwołanie nie jest kopiowane.

W przypadku wdrożenia aplikacji, która zawiera odwołanie do składnika niestandardowego, który jest zarejestrowany w pamięci podręcznej GAC, składnik nie zostanie wdrożony z aplikacją, bez względu na <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> ustawienie. We wcześniejszych wersjach programu Visual Studio można ustawić <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> Właściwość odwołania, aby upewnić się, że zestaw został wdrożony. Teraz musisz ręcznie dodać zestaw do folderu \Bin. Powoduje to umieszczenie całego niestandardowego kodu w ramach kontroli, co zmniejsza ryzyko związane z publikowaniem niestandardowego kodu, którego nie znasz.

Domyślnie <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> Właściwość jest ustawiona na **false** , jeśli zestaw lub składnik znajduje się w globalnej pamięci podręcznej zestawów lub jest składnikiem struktury. W przeciwnym razie wartość jest równa **true**. Odwołania między projektami są zawsze ustawione na **wartość true**.

## <a name="reference-a-project-or-assembly-that-targets-a-different-version-of-net"></a>Odwołuje się do projektu lub zestawu, który jest przeznaczony dla innej wersji platformy .NET.

Można tworzyć aplikacje odwołujące się do projektów lub zestawów przeznaczonych dla różnych wersji platformy .NET. Można na przykład utworzyć aplikację, która jest przeznaczona dla .NET Framework 4,6, która odwołuje się do zestawu, który jest przeznaczony dla .NET Framework 4,5. Jeśli tworzysz projekt, który jest przeznaczony dla starszej wersji programu .NET, nie można ustawić odwołania w tym projekcie do projektu lub zestawu, który jest przeznaczony dla nowszej wersji.

Aby uzyskać więcej informacji, zobacz temat [Omówienie funkcji określania wartości docelowej](../ide/visual-studio-multi-targeting-overview.md).

## <a name="project-to-project-references"></a>Odwołania projektu do projektu

Odwołania między projektami są odwołaniami do projektów, które zawierają zestawy; odwołania do projektu można dodać przy użyciu karty **projekty** w oknie dialogowym Menedżer odwołań. Program Visual Studio może znaleźć zestaw, gdy nadana ścieżka do projektu.

W przypadku projektu, który tworzy zestaw, należy odwołać się do projektu, a nie użyć odwołania do pliku (patrz poniżej). Zaletą odwołania projektu do projektu jest utworzenie zależności między projektami w systemie kompilacji. Projekt zależny zostanie skompilowany, jeśli został zmieniony od czasu skompilowania projektu, który odwołuje się do niego. Odwołanie do pliku nie tworzy zależności kompilacji, więc możliwe jest skompilowanie odwołującego się projektu bez kompilowania projektu zależnego, a odwołanie może stać się przestarzałe. (Oznacza to, że projekt może odwoływać się do poprzednio skompilowanej wersji projektu). Może to spowodować, że w katalogu *bin* jest wymagana kilka wersji pojedynczej biblioteki DLL, co nie jest możliwe. Po wystąpieniu tego konfliktu zostanie wyświetlony komunikat, taki jak "Ostrzeżenie: nie można skopiować pliku zależności" w projekcie projektu "do katalogu uruchomieniowego, ponieważ spowodowałoby to zastąpienie odwołania" plik ". Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z uszkodzonymi odwołaniami](../ide/troubleshooting-broken-references.md) i [instrukcje: Tworzenie i usuwanie zależności projektu](../ide/how-to-create-and-remove-project-dependencies.md).

> [!NOTE]
> Odwołanie do pliku zamiast odwołania projektu do projektu jest tworzone, jeśli docelowa wersja .NET Framework jednego projektu jest w wersji 4,5, a docelowa wersja innego projektu to wersja 2, 3, 3,5 lub 4,0.

## <a name="shared-project-references"></a>Odwołania do projektu udostępnionego

W przeciwieństwie do większości innych typów projektów, *projekt udostępniony* nie ma żadnych danych wyjściowych binarnych. Zamiast tego, kod jest kompilowany do każdego projektu, który odwołuje się do niego. [Projekty udostępnione](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) umożliwiają pisanie wspólnych kodów, do których odwołują się różne projekty aplikacji. Kod jest kompilowany jako część każdego odwołującego się projektu i może zawierać dyrektywy kompilatora, aby pomóc w uwzględnieniu funkcji specyficznych dla platformy w bazie kodu udostępnionego. Dodaj odwołanie do projektu udostępnionego na karcie **projekty udostępnione** okna dialogowego Menedżer odwołań.

## <a name="file-references"></a>Odwołania do pliku

Odwołania do plików są bezpośrednimi odwołaniami do zestawów poza kontekstem projektu programu Visual Studio. Można je utworzyć za pomocą karty **Przeglądaj** okna dialogowego Menedżer odwołań. Użyj odwołania do pliku, gdy masz tylko zestaw lub składnik, a nie projekt, który tworzy go jako dane wyjściowe.

## <a name="see-also"></a>Zobacz także

- [Rozwiązywanie problemów z przerwanymi odwołaniami](../ide/troubleshooting-broken-references.md)
- [Instrukcje: Dodawanie lub usuwanie odwołań](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
