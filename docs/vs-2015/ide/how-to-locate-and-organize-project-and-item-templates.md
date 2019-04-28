---
title: 'Instrukcje: Znajdź i organizowania projektów i szablonów elementów | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], locations
- custom template locations [Visual Studio]
- item templates, locations
- Visual Studio templates, locations
- project templates [Visual Studio], displaying
- templates [Visual Studio], locations
ms.assetid: 71f9ed52-c9c9-4818-9bce-c279ffaa0438
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4b14a374214a605ec718ad60c6942752f3134edd
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63416723"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Instrukcje: Znajdź i organizowania projektów i szablonów elementów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pliki szablonu muszą być umieszczone w rozpoznawaną przez program Visual Studio, aby szablonów pojawi się w lokalizacji **nowy projekt** i **Dodaj nowy element** okien dialogowych. Możesz utworzyć niestandardowe podkategorii dla szablonów tak, aby podkategorii pojawiają się w interfejsie użytkownika.  
  
## <a name="locating-templates"></a>Znajdowanie szablonów  
 Domyślnie program Visual Studio wyszukuje dwie lokalizacje szablonów projektów i elementów. Jeśli istnieje skompresowany plik, który zawiera plik .vstemplate w tych lokalizacjach, szablon pojawi się w **nowy projekt** lub **Dodaj nowy element** okien dialogowych.  
  
### <a name="installed-templates"></a>Zainstalowane szablony  
 Domyślnie szablony instalowane razem z produktu znajdują się w:  
  
- \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\\*języka*\\*ustawień regionalnych*\  
  
- \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\\*języka*\\*ustawień regionalnych\\*  
  
  Na przykład następujący katalog zawiera [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] szablony projektów w języku angielskim:  
  
  C:\\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\VisualBasic\1033\  
  
### <a name="custom-templates"></a>Szablony niestandardowe  
 Domyślnie szablony niestandardowe znajdują się w:  
  
- Studio \My *wersji*\Templates\ProjectTemplates\\*języka*\  
  
- Studio \My *wersji*\Templates\ItemTemplates\\*języka*\  
  
  Na przykład następujący katalog zawiera niestandardowe [!INCLUDE[csprcs](../includes/csprcs-md.md)] szablony projektu:  
  
  C:\Documents and Settings\UserName\My Documents\\<Visual Studio version\>\Templates\ProjectTemplates\Visual C#\  
  
  Szablony niestandardowe nie dołączaj podkatalogu dla szablonów zlokalizowane. Możesz zmienić domyślny katalog dla szablonów niestandardowych w **opcje** dialogowego **Environment\Projects i rozwiązania**.  
  
## <a name="organizing-templates"></a>Organizowanie szablonów  
 Kategorie w **nowy projekt** i **Dodaj nowy element** okna dialogowe odzwierciedlają struktur katalogów, które istnieją w lokalizacje szablonów zainstalowanych i niestandardowe. Można modyfikować tych struktur katalogów w celu uporządkować w najwygodniejszy dla siebie sposób.  
  
> [!NOTE]
> Nie można utworzyć nową kategorię na poziomie języka programowania. Nowe kategorie można tworzyć tylko w ramach każdego z języków.  
  
 Jeśli struktur katalogów dla zainstalowanych szablonów niestandardowych dla danego języka nie mają tę samą strukturę (oznacza to, że istnieją katalogi w ramach jednego folderu, w których nie ma pod innymi) zestawu kategorii, które pojawiają się w **New Projekt** okno dialogowe będzie łączenia wszystkich kategorii.  
  
### <a name="organizing-installed-templates"></a>Organizowanie zainstalowane szablony  
 Możesz organizować zainstalowanych szablonów, tworząc podkatalogów w folderze języka programowania. Te podkatalogi są wyświetlane w **nowy projekt** i **Dodaj nowy element** okna dialogowe jako wirtualny folderach w ramach każdego z języków.  
  
##### <a name="to-create-new-installed-project-template-categories"></a>Aby utworzyć nowy projekt zainstalowanych kategorie szablonów  
  
1. Utwórz folder w folderze język katalogu zainstalowanych szablonów. Na przykład utwórz kategorię Office [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] szablony, należy utworzyć następujący katalog projektu:  
  
    \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\VisualBasic\1033\Office\  
  
2. Umieścić wszystkie szablony dla tej kategorii w nowym folderze.  
  
3. Zamknij wszystkie wystąpienia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4. Na **Start** menu, kliknij przycisk **Uruchom**, typ **cmd**i kliknij przycisk **OK**.  
  
5. W wierszu polecenia, znajdź katalog, który zawiera devenv.exe i typ **devenv/installvstemplates**.  
  
6. Uruchom [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
7. Na **pliku** menu, kliknij przycisk **New**, a następnie kliknij przycisk **projektu**.  
  
8. Sprawdź, czy kategoria Office jest wyświetlana w **nowy projekt** dialogowym **typów projektów** okienku w obszarze [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].  
  
   Można także grupować podzbiór szablony elementów projektu do folderu niestandardowego.  
  
##### <a name="to-create-new-installed-item-template-categories"></a>Aby utworzyć nowy element zainstalowanych kategorii szablonu  
  
1. Utwórz folder w folderze język katalogu zainstalowanych szablonów. Na przykład utworzyć kategorię sieci Web dla [!INCLUDE[csprcs](../includes/csprcs-md.md)] elementu szablonów, należy utworzyć następującego katalogu:  
  
     \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\CSharp\1033\Web\  
  
2. Umieścić wszystkie szablony dla tej kategorii w nowym folderze.  
  
3. Zamknij wszystkie wystąpienia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4. Na **Start** menu, kliknij przycisk **Uruchom**, typ **cmd**i kliknij przycisk **OK**.  
  
5. W wierszu polecenia, znajdź katalog, który zawiera devenv.exe i typ **devenv/Setup**.  
  
6. Uruchom [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
7. Utwórz projekt lub Otwórz istniejący projekt.  
  
8. Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
9. Sprawdź, czy kategoria sieci Web jest wyświetlana w **Dodaj nowy element** dialogowym **typów projektów** okienka.  
  
### <a name="organizing-custom-templates"></a>Organizowanie szablonów niestandardowych  
 Szablony niestandardowe może można podzielić na ich własnych kategorii, dodając nowe foldery w lokalizacji szablonu niestandardowego. **Nowy projekt** okno dialogowe odzwierciedla wszelkie zmiany wprowadzone do kategorii szablonu.  
  
##### <a name="to-create-new-custom-project-template-categories"></a>Aby utworzyć nowy projekt niestandardowe kategorie szablonów  
  
1. Utwórz folder w folderze język w katalogu szablonu niestandardowego projektu. Na przykład utworzyć kategorię HelloWorld [!INCLUDE[csprcs](../includes/csprcs-md.md)] szablonów, należy utworzyć następującego katalogu:  
  
    \My Documents\\<Visual Studio version\>\Templates\ProjectTemplates\CSharp\HelloWorld\  
  
2. Umieścić wszystkie szablony dla tej kategorii w nowym folderze.  
  
3. Na **pliku** menu, kliknij przycisk **New**, a następnie kliknij przycisk **projektu**.  
  
4. Sprawdź, czy kategoria HelloWorld znajduje się w **nowy projekt** dialogowym **typów projektów** okienku w obszarze [!INCLUDE[csprcs](../includes/csprcs-md.md)].  
  
   Można także grupować podzbiór szablonów niestandardowych elementów do folderu niestandardowego.  
  
##### <a name="to-create-new-custom-item-template-categories"></a>Tworzenie nowego niestandardowego elementu kategorii szablonu  
  
1. Utwórz folder w folderze język w katalogu szablonu niestandardowego elementu. Na przykład utworzyć kategorię HelloWorld [!INCLUDE[csprcs](../includes/csprcs-md.md)] szablonów należy utworzyć następującego katalogu:  
  
     \My Documents\\<Visual Studio version\>\Templates\ItemTemplates\CSharp\HelloWorld\  
  
2. Umieścić wszystkie szablony dla tej kategorii w nowym folderze.  
  
3. Utwórz projekt lub Otwórz istniejący projekt.  
  
4. Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
5. Sprawdź, czy kategoria HelloWorld znajduje się w **Dodaj nowy element** dialogowym **typów projektów** okienka.  
  
### <a name="displaying-templates-in-parent-categories"></a>Wyświetlanie szablonów w kategorii nadrzędnych  
 Możesz włączyć szablonów w podkategorii, które mają być wyświetlane w ich kategorii nadrzędnych przy użyciu `NumberOfParentCategoriesToRollUp` elementu w pliku .vstemplate. Te kroki są identyczne dla szablonów projektów i szablonów elementów.  
  
##### <a name="to-display-templates-in-parent-categories"></a>Aby wyświetlić szablony w kategorii nadrzędnych  
  
1. Zlokalizuj plik .zip zawierający szablon.  
  
2. Wyodrębnij plik zip.  
  
3. Otwórz plik .vstemplate w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4. W `TemplateData` elementu Dodawanie `NumberOfParentCategoriesToRollUp` elementu. Na przykład poniższy kod powoduje, że szablon widoczne w kategorii nadrzędnej, ale nie jest wyższa.  
  
    ```  
    <TemplateData>  
        ...  
        <NumberOfParentCategoriesToRollUp>  
            1  
        </NumberOfParentCategoriesToRollUp>  
        ...  
    </TemplateData>  
    ```  
  
5. Zapisz i zamknij plik .vstemplate.  
  
6. Wybierz pliki do szablonu, kliknij prawym przyciskiem myszy zaznaczenie, kliknij przycisk **Wyślij do**, a następnie kliknij przycisk **skompresowany Folder (zip)**. Pliki są kompresowane w pliku zip.  
  
7. Usuń pliki szablonów wyodrębniony i stary plik zip szablonu.  
  
8. W katalogu zawierającego plik zip usunięte, należy umieścić nowy plik zip.  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)   
 [Visual Studio Template Schema Reference](../extensibility/visual-studio-template-schema-reference.md)   
 [NumberOfParentCategoriesToRollUp (szablony Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)   
 [Instrukcje: Create Project Templates](../ide/how-to-create-project-templates.md)   
 [Instrukcje: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)
