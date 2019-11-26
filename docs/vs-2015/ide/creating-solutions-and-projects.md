---
title: Tworzenie rozwiązań i projektów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.openprojectfromweb
- vs.newproject
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], deleting
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
ms.assetid: 836f8ca0-3fc9-4f4b-9090-45f2e4d2e9c8
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 03ecd3fcc253f255afc59c2d6412f3864fe253b8
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300598"
---
# <a name="creating-solutions-and-projects"></a>Tworzenie rozwiązań i projektów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projekty to logiczne kontenery dla wszystkich elementów, które są potrzebne do skompilowania aplikacji. Podczas tworzenia projektu, wybierając pozycję  **&#124; plik nowy &#124; projekt** z menu głównego, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tworzy rozwiązanie, które je zawiera. W razie potrzeby możesz dodać nowe lub istniejące projekty do rozwiązania. Można tworzyć projekty z istniejących plików kodu, a także tworzyć projekty tymczasowe (tylko platforma .NET), które zostaną usunięte po wykonaniu tych czynności.

> [!NOTE]
> Opisy w tym temacie są oparte na wersji programu Visual Studio Community. Polecenia menu i okien dialogowych mogą różnić się od tych opisanych w tym miejscu, w zależności od ustawień lub wersji programu Visual Studio. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-project-from-an-installed-project-template"></a>Tworzenie projektu na podstawie zainstalowanego szablonu projektu
 **Plik &#124; nowy &#124; projekt** z menu głównego, aby wyświetlić okno dialogowe Nowy projekt. W okienku po lewej stronie w obszarze  **&#124; szablony z niewyższym** wybieraniem języka programowania i platformy lub technologii, a następnie wybierz spośród dostępnych szablonów w środkowym okienku.

 W oknie dialogowym **Nowy projekt** lista rozwijana **rozwiązanie** umożliwia utworzenie nowego projektu w nowym lub istniejącym rozwiązaniu lub w nowym wystąpieniu programu Visual Studio.

## <a name="create-a-project-from-existing-code-files"></a>Tworzenie projektu z istniejących plików kodu
 Jeśli masz kolekcję luźnych plików źródłowych, możesz łatwo utworzyć projekt, który go zawiera. Wybierz **pozycję &#124; plik &#124;nowy projekt z istniejącego kodu** , aby uruchomić **Kreatora tworzenia projektu z istniejących plików z kodem** i postępuj zgodnie z monitami.

> [!TIP]
> Ta opcja działa najlepiej w przypadku stosunkowo prostych kolekcji plików.

## <a name="create-a-temporary-project-c-and-visual-basic"></a>Utwórz projekt tymczasowy (C# i Visual Basic)
 Pracując z projektami tymczasowymi, można tworzyć i eksperymentować z projektem .NET bez określania lokalizacji dysku. Podczas tworzenia projektu, wystarczy wybrać typ projektu i szablon i określić nazwę w oknie dialogowym **Nowy projekt** . W dowolnym momencie podczas pracy z projektem tymczasowym można go zapisać lub można go odrzucić.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Tworzenie projektu platformy .NET, który jest przeznaczony dla określonej wersji programu .NET Framework
 Można utworzyć projekt, który ma być przeznaczony dla wcześniejszych wersji .NET Framework przy użyciu menu rozwijanego wersja **.NET Framework** w górnej części okna dialogowego **Nowy projekt** . Ustaw tę wartość przed wybraniem szablonu projektu, ponieważ na liście pojawią się tylko szablony zgodne z tą .NET Framework wersją.

 Aby uzyskać dostęp do wersji Framework wcześniejszych niż 4,0, w systemie musi być zainstalowany .NET Framework 3,5.

## <a name="downloading-sample-solutions"></a>Pobieranie przykładowych rozwiązań
 Możesz użyć programu Visual Studio do pobrania i zainstalowania przykładowych rozwiązań z [galerii kodu MSDN](https://go.microsoft.com/fwlink/?LinkId=254185).

 Możesz pobrać przykłady osobno lub pobrać pakiet przykładowy zawierający powiązane przykłady, które udostępniają technologię lub temat. Otrzymasz powiadomienie, gdy zostaną opublikowane zmiany kodu źródłowego dla pobranych próbek.

 Aby uzyskać więcej informacji, zobacz [przykłady programu Visual Studio](../ide/visual-studio-samples.md).

## <a name="adding-single-files-at-the-solution-level"></a>Dodawanie pojedynczych plików na poziomie rozwiązania
 Czasami może istnieć plik, do którego odwołuje się wiele projektów, lub zawierający tekst lub różne dane, które logicznie należą do poziomu rozwiązania, a nie w określonym projekcie.  Aby dodać pojedynczy element do rozwiązania:

1. Kliknij prawym przyciskiem myszy węzeł rozwiązanie w **Eksplorator rozwiązań** i wybierz **polecenie &#124; Dodaj nowy element** lub  **&#124; Dodaj istniejący element**.

## <a name="creating-empty-solutions"></a>Tworzenie pustych rozwiązań
 Mimo że projekt musi znajdować się w rozwiązaniu, można utworzyć rozwiązanie, które nie ma projektów.

#### <a name="to-create-an-empty-solution"></a>Aby utworzyć puste rozwiązanie

1. W menu **plik** kliknij pozycję **Nowy** , a następnie kliknij pozycję **Nowy projekt**.

2. W lewym okienku wybierz pozycję **zainstalowane**, wybierz pozycję **Inne typy projektów**, a następnie wybierz pozycję **rozwiązania programu Visual Studio** z listy rozwijanej.

3. W środkowym okienku wybierz pozycję **puste rozwiązanie**.

4. Ustaw wartości w polu **Nazwa** i **Lokalizacja** dla rozwiązania, a następnie kliknij przycisk **OK**.

   Po utworzeniu pustego rozwiązania można dodać do niego nowe lub istniejące projekty lub elementy, klikając pozycję **Dodaj nowy element** lub **Dodaj istniejący element** w menu **projekt** .

### <a name="deleting-solutions"></a>Usuwanie rozwiązań
 Rozwiązanie można trwale usunąć, ale nie za pomocą [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Przed usunięciem rozwiązania Przenieś wszystkie projekty, które mogą być używane ponownie w innym rozwiązaniu. Następnie użyj Eksploratora plików, aby usunąć katalog zawierający pliki rozwiązania. sln i. suo.

> [!NOTE]
> Plik SUO to ukryty plik, który nie jest wyświetlany w obszarze domyślne ustawienia Eksploratora plików.

##### <a name="to-delete-a-solution"></a>Aby usunąć rozwiązanie

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie, które chcesz usunąć, a następnie wybierz polecenie **Otwórz folder w Eksploratorze plików**.

2. W Eksploratorze plików Przejdź jeden poziom w górę.

3. Wybierz katalog zawierający rozwiązanie i naciśnij klawisz Delete.

## <a name="see-also"></a>Zobacz też
 [Rozwiązania i projekty](../ide/solutions-and-projects-in-visual-studio.md) [NIB How to: Create-Project Solutions](https://msdn.microsoft.com/02ecd6dd-0114-46fe-b335-ba9c5e3020d6)
