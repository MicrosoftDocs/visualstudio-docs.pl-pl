---
title: Tworzenie rozwiązań i projektów | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7fd6d8c63d8b0b56af20ac1211802524336d06bc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437581"
---
# <a name="creating-solutions-and-projects"></a>Tworzenie rozwiązań i projektów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projekty są kontenery logiczne dla wszystko, co jest potrzebne do budowania aplikacji. Po utworzeniu projektu, wybierając **pliku &#124; New &#124; projektu** z menu głównego [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tworzy rozwiązanie dla niej. Następnie można dodać więcej nowych lub istniejących projektów w rozwiązaniu, jeśli to konieczne. Możesz tworzyć projekty z istniejących plików kodu i utworzeniem projektów tymczasowych (tylko platforma .NET), zostaną usunięte po wykonaniu tych czynności z nimi.  
  
> [!NOTE]
> Opisy w tym temacie są oparte na wersji programu Visual Studio Community. Polecenia menu i okien dialogowych mogą różnić się od tych opisanych w tym miejscu, w zależności od ustawień lub wersji programu Visual Studio. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="create-a-project-from-an-installed-project-template"></a>Tworzenie projektu z szablonem projektu zainstalowane  
 **Plik &#124; New &#124; projektu** z menu głównego, aby wyświetlić okno dialogowe Nowy projekt. W okienku po lewej stronie w obszarze **Intalled &#124; szablony** Wybrany język programowania i platform lub technologii, a następnie wybierz spośród dostępnych szablonów w środkowym okienku.  
  
 W **nowy projekt** okno dialogowe, **rozwiązania** listy rozwijanej zapewnia możliwość tworzenia nowego projektu w nowym lub istniejącym rozwiązaniu lub w nowym wystąpieniu programu Visual Studio.  
  
## <a name="create-a-project-from-existing-code-files"></a>Tworzenie projektu z istniejących plików kodu  
 W przypadku kolekcji plików źródłowych nie będzie można łatwo utworzyć projekt, który je zawiera. Wybierz **pliku &#124; New &#124;projekt z istniejącego kodu** można uruchomić **Utwórz projekt z istniejących Kreatora plików kodu** i postępuj zgodnie z monitami.  
  
> [!TIP]
> Ta opcja jest najlepsza dla stosunkowo prostych kolekcji plików.  
  
## <a name="create-a-temporary-project-c-and-visual-basic"></a>Utwórz projekt tymczasowy (C# i Visual Basic)  
 Praca z projektów tymczasowych, można tworzyć i eksperymentować z projektem .NET bez określania lokalizacji na dysku. Podczas tworzenia projektu są po prostu zaznacz typ projektu i szablon i podaj nazwę w **nowy projekt** okno dialogowe. W dowolnym momencie podczas pracy z projektem tymczasowej, można go zapisać lub odrzucić je.  
  
## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Tworzenie projektu platformy .NET, który jest przeznaczony dla określonej wersji programu .NET Framework  
 Możesz utworzyć projekt pod kątem starszej wersji programu .NET Framework za pomocą **.NET Framework** wersji listy rozwijanej w górnej części **nowy projekt** okno dialogowe. Przed wybraniem szablon projektu, należy ustawić tę wartość, ponieważ tylko szablony zgodne z tej wersji programu .NET Framework będą wyświetlane na liście.  
  
 Musisz mieć program .NET Framework 3.5 zainstalowany w systemie do uzyskania dostępu framework w wersji starszej niż 4.0.  
  
## <a name="downloading-sample-solutions"></a>Pobieranie przykładowe rozwiązania  
 Visual Studio można użyć do pobrania i zainstalowania rozwiązań próbki z [galerii kodu MSDN](http://go.microsoft.com/fwlink/?LinkId=254185).  
  
 Przykłady można pobrać osobno lub możesz pobrać pakiet przykładowy, który zawiera powiązane próbki, które współużytkują technologię lub temat. Otrzymasz powiadomienie po zmianach kodu źródłowego są publikowane do przykładów, które można pobrać.  
  
 Aby uzyskać więcej informacji, zobacz [Visual Studio Samples](../ide/visual-studio-samples.md).  
  
## <a name="adding-single-files-at-the-solution-level"></a>Dodawanie pojedynczych plików na poziomie rozwiązania  
 Czasami może być plikiem wiele projektów, odwołując się do lub zawierający tekst lub inne dane, które logicznie należą na poziomie rozwiązania, a nie w ramach określonego projektu.  Aby dodać pojedynczego elementu rozwiązania:  
  
1. Kliknij prawym przyciskiem myszy węzeł rozwiązania w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj &#124; nowy element** lub **Dodaj &#124; istniejący element**.  
  
## <a name="creating-empty-solutions"></a>Tworzenie pustego rozwiązań  
 Chociaż projektu musi znajdować się w rozwiązaniu, można utworzyć rozwiązanie, które ma żadne projekty.  
  
#### <a name="to-create-an-empty-solution"></a>Aby utworzyć puste rozwiązanie  
  
1. Na **pliku** menu, kliknij przycisk **New** a następnie kliknij przycisk **nowy projekt**.  
  
2. W okienku po lewej stronie wybierz **zainstalowane**, wybierz opcję **inne typy projektów**, a następnie wybierz pozycję **Visual Studio Solutions** z rozwiniętej listy.  
  
3. W środkowym okienku wybierz **puste rozwiązanie**.  
  
4. Ustaw **nazwa** i **lokalizacji** wartości dla rozwiązania, następnie kliknij przycisk **OK**.  
  
   Po utworzeniu puste rozwiązanie, nowe lub istniejące projekty lub elementy można dodać do niego, klikając **Dodaj nowy element** lub **Dodaj istniejący element** na **projektu** menu.  
  
### <a name="deleting-solutions"></a>Usuwanie rozwiązania  
 Rozwiązanie można usunąć trwale, ale nie przy użyciu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Zanim usuniesz to rozwiązanie, Przenieś wszystkie projekty, które możesz chcieć użyć ponownie w innym rozwiązaniem. Następnie użyj Eksploratora plików, aby usunąć katalog zawierający pliki rozwiązania .sln i .suo.  
  
> [!NOTE]
> Plik .suo jest ukryty plik, który nie jest wyświetlany w obszarze domyślne ustawienia Eksploratora plików.  
  
##### <a name="to-delete-a-solution"></a>Aby usunąć rozwiązanie  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie do usunięcia i wybierz **Otwórz folder w Eksploratorze plików**.  
  
2. W Eksploratorze plików Przejdź jeden poziom w górę.  
  
3. Wybierz katalog, zawierająca dane rozwiązanie, a następnie naciśnij klawisz Delete.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązania i projekty](../ide/solutions-and-projects-in-visual-studio.md)   
 [NIB jak: Create Multi-Project Solutions](http://msdn.microsoft.com/02ecd6dd-0114-46fe-b335-ba9c5e3020d6)
