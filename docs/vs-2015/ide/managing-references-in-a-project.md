---
title: Zarządzanie odwołaniami w projekcie | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1f2f3c26d89616f083c218c6b11610fe5e329a9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651318"
---
# <a name="managing-references-in-a-project"></a>Zarządzanie odwołaniami w projekcie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przed napisaniem kodu w składniku zewnętrznym lub połączonej usłudze, projekt musi zawierać odwołanie do niego. Odwołanie jest zasadniczo wpisem w pliku projektu, który zawiera informacje, które program Visual Studio musi zlokalizować składnik lub usługę.

 Aby dodać odwołanie, kliknij prawym przyciskiem myszy węzeł odwołania w Eksplorator rozwiązań i wybierz polecenie **Dodaj odwołanie**. Aby uzyskać więcej informacji, zobacz [How to: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

 ![Dodaj odwołanie w Visual C&#43;&#43;](../ide/media/vs2015-cpp-add-reference.png "vs2015_cpp_add_reference")

 Można utworzyć odwołanie do następujących typów składników/usług:

- Odwołania do aplikacji ze sklepu Windows

- .NET Framework biblioteki lub zestawy klas

- COM — Składniki

- Inne zestawy lub biblioteki klas projektów w tym samym rozwiązaniu

- Usługi sieci Web XML

## <a name="windows-store-app-references"></a>Odwołania do aplikacji ze sklepu Windows

### <a name="project-references"></a>Informacje o projekcie
 Projekty platforma uniwersalna systemu Windows (platformy UWP), które są przeznaczone dla systemu Windows 10, mogą tworzyć odwołania do innych projektów platformy UWP w rozwiązaniu lub do projektów Windows Store lub plików binarnych, które są przeznaczone dla [!INCLUDE[win81](../includes/win81-md.md)], pod warunkiem, że te projekty nie używają interfejsów API przestarzałych w programie System Windows 10. Aby uzyskać więcej informacji, zobacz [przenoszenie z środowisko wykonawcze systemu Windows 8 do platformy UWP](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx).

 Jeśli zdecydujesz się przekierować projekty [!INCLUDE[win81](../includes/win81-md.md)] do systemu Windows 10, zobacz Przenoszenie [, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)

### <a name="extension-sdk-references"></a>Odwołania do zestawu SDK rozszerzeń
 Visual Basic, C# C++ i projekty języka JavaScript dla systemu Windows przeznaczone dla platforma uniwersalna systemu Windows (platformy UWP) mogą odwoływać się do zestawów SDK rozszerzeń, które są przeznaczone dla [!INCLUDE[win81](../includes/win81-md.md)], o ile te zestawy SDK rozszerzenia nie używają interfejsów API przestarzałych w systemie Windows 10. Sprawdź witrynę dostawcy zestawu SDK rozszerzenia, aby dowiedzieć się, czy można odwoływać się do niej projekty sklepu Windows przeznaczone dla platformy UWP.

 Jeśli określisz, że zestaw SDK, do którego odwołuje się aplikacja, nie jest obsługiwany, należy wykonać następujące czynności:

1. Spójrz na nazwę projektu, który powoduje błąd. Platforma, do której należy projekt, jest zapisywana w nawiasach obok nazwy projektu. Na przykład, **. ProjectName (Windows 8.1)** oznacza, że projekt **ProjectName jest** ukierunkowany na wersję platformy [!INCLUDE[win81](../includes/win81-md.md)].

2. Przejdź do lokacji dostawcy, który jest właścicielem nieobsługiwanego zestawu SDK rozszerzenia i Zainstaluj wersję zestawu SDK rozszerzenia z zależnościami, które są zgodne z wersją platformy, dla której projekt jest przeznaczony.

    > [!NOTE]
    > Jednym ze sposobów ustalenia, czy rozszerzenie SDK ma zależności od innych zestawów SDK rozszerzeń, jest ponowne uruchomienie programu Visual Studio, utworzenie C# nowego projektu Windows Store, kliknięcie prawym przyciskiem myszy nad projektem i wybierz polecenie **Dodaj odwołanie**, przejdź do karty **Windows** , przejdź do okna Podkartę **rozszerzenia** , wybierz zestaw SDK rozszerzeń i Sprawdź okienko po prawej stronie w **Menedżerze odwołań**. Jeśli ma zależności, zostaną one wyświetlone.

    > [!IMPORTANT]
    > Jeśli projekt jest przeznaczony dla systemu Windows 10, a rozszerzenie SDK zainstalowane w poprzednim kroku jest zależne od pakietu Microsoft Visual C++ Runtime, wersja pakietu Microsoft Visual C++ Runtime, która jest zgodna z systemem Windows 10, to v 14.0 i Program jest instalowany z programem Visual Studio 2015.

3. Jeśli zestaw SDK rozszerzenia zainstalowany w poprzednim kroku ma zależności od innych zestawów SDK rozszerzeń, przejdź do witryn dostawców, którzy są właścicielami zależności, i zainstaluj wersje tych zależności, które są zgodne z wersją platformy. projekt jest celem.

4. Uruchom ponownie program Visual Studio i Otwórz aplikację.

5. Kliknij prawym przyciskiem myszy węzeł **odwołania** w projekcie, który spowodował błąd, i wybierz polecenie **Dodaj odwołanie**

6. Kliknij kartę **Windows** , a następnie podkartę **rozszerzenia** , a następnie usuń zaznaczenie pól wyboru dla starych zestawów SDK rozszerzenia i zaznacz pola wyboru dla nowych zestawów SDK rozszerzenia. Kliknij przycisk **OK**.

## <a name="adding-a-reference-at-design-time"></a>Dodawanie odwołania w czasie projektowania
 Gdy wprowadzisz odwołanie do zestawu w projekcie, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wyszukuje zestaw w następujących lokalizacjach:

- Bieżący katalog projektu. (Zestawy te można znaleźć za pomocą karty **Przeglądaj** ).

- Inne katalogi projektu w tym samym rozwiązaniu. (Te zestawy można znaleźć na karcie **projekty** ).

> [!NOTE]
> Wszystkie projekty zawierają implikowane odwołanie do biblioteki mscorlib. Projekty Visual Basic zawierają implikowane odwołanie do `Microsoft.VisualBasic`.
>
> Wszystkie projekty w programie Visual Studio zawierają implikowane odwołanie do `System.Core` nawet wtedy, gdy `System.Core` zostanie usunięty z listy odwołań.

## <a name="references-to-shared-components-at-run-time"></a>Odwołania do współużytkowanych składników w czasie wykonywania
 W czasie wykonywania składniki muszą znajdować się w ścieżce wyjściowej projektu lub w [globalnej pamięci podręcznej zestawów](https://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) (GAC). Jeśli projekt zawiera odwołanie do obiektu, który nie znajduje się w jednej z tych lokalizacji, należy skopiować odwołanie do ścieżki wyjściowej projektu podczas kompilowania projektu. Właściwość <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> wskazuje, czy należy wykonać tę kopię. Jeśli wartość jest **równa true**, odwołanie jest kopiowane do katalogu projektu podczas kompilowania projektu. Jeśli wartość jest równa **false**, odwołanie nie jest kopiowane.

 W przypadku wdrożenia aplikacji, która zawiera odwołanie do składnika niestandardowego, który jest zarejestrowany w pamięci podręcznej GAC, składnik nie zostanie wdrożony z aplikacją, bez względu na ustawienie <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A>. We wcześniejszych wersjach [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] można ustawić właściwość <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> na odwołanie, aby upewnić się, że zestaw został wdrożony. Teraz musisz ręcznie dodać zestaw do folderu \Bin. Powoduje to umieszczenie całego niestandardowego kodu w ramach kontroli, co zmniejsza ryzyko związane z publikowaniem niestandardowego kodu, którego nie znasz.

 Domyślnie właściwość <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> jest ustawiona na **false** , jeśli zestaw lub składnik znajduje się w globalnej pamięci podręcznej zestawów lub jest składnikiem struktury. W przeciwnym razie wartość jest równa **true**. Odwołania między projektami są zawsze ustawione na **wartość true**.

## <a name="referencing-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Odwoływanie się do projektu lub zestawu, który jest przeznaczony dla innej wersji .NET Framework
 Można tworzyć aplikacje odwołujące się do projektów lub zestawów przeznaczonych dla różnych wersji .NET Framework. Można na przykład utworzyć aplikację, która jest przeznaczona dla [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)], która odwołuje się do zestawu, który jest przeznaczony [!INCLUDE[dnprdnext](../includes/dnprdnext-md.md)]. W przypadku utworzenia projektu, który jest przeznaczony dla starszej wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], nie można ustawić odwołania w tym projekcie do projektu lub zestawu, który jest przeznaczony dla [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] lub .NET Framework wersji 4.

 Aby uzyskać więcej informacji, zobacz [Określanie konkretnej wersji .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).

## <a name="project-to-project-references"></a>Odwołania projektu do projektu
 Odwołania między projektami są odwołaniami do projektów, które zawierają zestawy; można je utworzyć za pomocą karty **projekt** . program Visual Studio może znaleźć zestaw, gdy nadana ścieżka do projektu.

 W przypadku projektu, który tworzy zestaw, należy odwołać się do projektu, a nie użyć odwołania do pliku (patrz poniżej). Zaletą odwołania projektu do projektu jest utworzenie zależności między projektami w systemie kompilacji. Projekt zależny zostanie skompilowany, jeśli został zmieniony od czasu skompilowania projektu, który odwołuje się do niego. Odwołanie do pliku nie tworzy zależności kompilacji, więc możliwe jest skompilowanie odwołującego się projektu bez kompilowania projektu zależnego, a odwołanie może stać się przestarzałe. (Oznacza to, że projekt może odwoływać się do poprzednio skompilowanej wersji projektu). Może to spowodować, że w katalogu bin jest wymagana kilka wersji pojedynczej biblioteki DLL, co nie jest możliwe. Po wystąpieniu tego konfliktu zostanie wyświetlony komunikat, taki jak [Ostrzeżenie: nie można skopiować zależności "plik" w projekcie projektu "do katalogu uruchomieniowego, ponieważ spowodowałoby to zastąpienie odwołania" File ".](../misc/warning-the-dependency-file-in-project-project-cannot-be-copied.md) Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z uszkodzonymi odwołaniami](../ide/troubleshooting-broken-references.md) i [instrukcje: Tworzenie i usuwanie zależności projektu](../ide/how-to-create-and-remove-project-dependencies.md).

> [!NOTE]
> Odwołanie do pliku zamiast odwołania projektu do projektu jest tworzone, jeśli docelowa wersja .NET Framework jednego projektu jest w wersji 4,5, a docelowa wersja innego projektu to wersja 2, 3, 3,5 lub 4,0.

## <a name="file-references"></a>Odwołania do pliku
 Odwołania do plików są bezpośrednimi odwołaniami do zestawów poza kontekstem projektu programu Visual Studio; można je utworzyć za pomocą karty **Przeglądaj** w **Menedżerze odwołań**. Użyj odwołania do pliku, gdy masz tylko zestaw lub składnik i nie masz projektu, który tworzy go jako dane wyjściowe.

## <a name="see-also"></a>Zobacz też
 [Rozwiązywanie problemów z programowaniem uszkodzonych odwołań](../ide/troubleshooting-broken-references.md) [za pomocą zestawów](https://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6) [instrukcje: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
