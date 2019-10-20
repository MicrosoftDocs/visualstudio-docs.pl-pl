---
title: 'Instrukcje: Lokalizowanie i organizowanie szablonów projektów i elementów | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b5f55de910eb77ec7ccbd205b78d5c95039e6b39
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651870"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Porady: lokalizowanie i organizowanie szablonów projektów i elementów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pliki szablonów należy umieścić w lokalizacji rozpoznawanej przez program Visual Studio tak, aby szablony pojawiły się w oknach dialogowych **Nowy projekt** i **Dodaj nowy element** . Można utworzyć niestandardowe podkategorie dla szablonów, aby podkategorie również pojawiły się w interfejsie użytkownika.

## <a name="locating-templates"></a>Lokalizowanie szablonów
 Domyślnie program Visual Studio przeszukuje dwie lokalizacje dla szablonów projektów i elementów. Jeśli w tych lokalizacjach znajduje się skompresowany plik, który zawiera plik. vstemplate, w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** zostanie wyświetlony szablon.

### <a name="installed-templates"></a>Zainstalowane szablony
 Domyślnie szablony zainstalowane razem z produktem znajdują się w temacie:

- \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates \\*języka* \\*ustawień regionalnych* \

- \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates \\*języka* \\*ustawień regionalnych \\*

  Na przykład następujący katalog zawiera [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] szablonów projektu dla języka angielskiego:

  C: \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\VisualBasic\1033\

### <a name="custom-templates"></a>Szablony niestandardowe
 Domyślnie szablony niestandardowe znajdują się w:

- \Moje Documents\Visual Studio w *wersji*\Templates\ProjectTemplates \\*Language* \

- \Moje Documents\Visual Studio w *wersji*\Templates\ItemTemplates \\*Language* \

  Na przykład następujący katalog zawiera niestandardowe szablony projektu [!INCLUDE[csprcs](../includes/csprcs-md.md)]:

  Dokumenty C:\Documents i Settings\UserName\My \\ < programu Visual Studio w wersji C#\> \templates\projecttemplates\visual \

  Szablony niestandardowe nie obejmują podkatalogu dla zlokalizowanych szablonów. Domyślny katalog szablonów niestandardowych można zmienić w oknie dialogowym **Opcje** , w obszarze **Environment\Projects i rozwiązania**.

## <a name="organizing-templates"></a>Organizowanie szablonów
 Kategorie w oknach dialogowych **Nowy projekt** i **Dodaj nowy element** odzwierciedlają struktury katalogów istniejące w zainstalowanych i niestandardowych lokalizacjach szablonów. Możesz zmodyfikować te struktury katalogów, aby zorganizować szablony w taki sposób, który ma sens.

> [!NOTE]
> Nie można utworzyć nowej kategorii na poziomie języka programowania. Nowe kategorie można tworzyć tylko w obrębie każdego języka.

 Jeśli struktury katalogów dla zainstalowanych i niestandardowych szablonów dla danego języka nie mają tej samej struktury (czyli katalogów znajdujących się w jednym folderze, który nie istnieje pod drugim), zestaw kategorii, które pojawiają się w **nowym projekcie** . okno dialogowe będzie połączeniem wszystkich kategorii.

### <a name="organizing-installed-templates"></a>Organizowanie zainstalowanych szablonów
 Zainstalowane szablony można organizować przez utworzenie podkatalogów w folderze języka programowania. Te podkatalogi pojawiają się w oknach dialogowych **Nowy projekt** i **Dodaj nowy element** jako folderów wirtualnych w każdym języku.

##### <a name="to-create-new-installed-project-template-categories"></a>Aby utworzyć nowe kategorie zainstalowanych szablonów projektu

1. Utwórz folder w folderze języka zainstalowanego katalogu szablonów. Na przykład aby utworzyć kategorię pakietu Office dla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] szablonów projektu, należy utworzyć następujący katalog:

    \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\VisualBasic\1033\Office\

2. Umieść wszystkie szablony dla tej kategorii w nowym folderze.

3. Zamknij wszystkie wystąpienia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

4. W menu **Start** kliknij polecenie **Uruchom**, wpisz polecenie **cmd**, a następnie kliknij przycisk **OK**.

5. W wierszu polecenia Znajdź katalog zawierający devenv. exe, a następnie wpisz **devenv/InstallVSTemplates**.

6. Uruchom [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

7. W menu **plik** kliknij pozycję **Nowy**, a następnie kliknij pozycję **projekt**.

8. Sprawdź, czy kategoria pakietu Office jest wyświetlana w oknie dialogowym **Nowy projekt** w okienku **typy projektów** w obszarze [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].

   Podzestaw szablonów elementów projektu można także grupować do folderu niestandardowego.

##### <a name="to-create-new-installed-item-template-categories"></a>Aby utworzyć nowe kategorie szablonów zainstalowanych elementów

1. Utwórz folder w folderze języka zainstalowanego katalogu szablonów. Aby na przykład utworzyć kategorię sieci Web dla szablonów elementów [!INCLUDE[csprcs](../includes/csprcs-md.md)], należy utworzyć następujący katalog:

     \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\CSharp\1033\Web\

2. Umieść wszystkie szablony dla tej kategorii w nowym folderze.

3. Zamknij wszystkie wystąpienia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

4. W menu **Start** kliknij polecenie **Uruchom**, wpisz polecenie **cmd**, a następnie kliknij przycisk **OK**.

5. W wierszu polecenia Znajdź katalog zawierający devenv. exe, a następnie wpisz **devenv/setup**.

6. Uruchom [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

7. Utwórz projekt lub Otwórz istniejący projekt.

8. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

9. Sprawdź, czy kategoria sieci Web pojawia się w oknie dialogowym **Dodaj nowy element** w okienku **typy projektów** .

### <a name="organizing-custom-templates"></a>Organizowanie szablonów niestandardowych
 Szablony niestandardowe można organizować w własne kategorie, dodając nowe foldery w lokalizacji szablonu niestandardowego. Okno dialogowe **Nowy projekt** odzwierciedla wszelkie zmiany wprowadzone w kategorii szablonów.

##### <a name="to-create-new-custom-project-template-categories"></a>Aby utworzyć nowe niestandardowe kategorie szablonów projektu

1. Utwórz folder w folderze języka w niestandardowym katalogu szablonów projektu. Na przykład, aby utworzyć kategorię HelloWorld dla szablonów [!INCLUDE[csprcs](../includes/csprcs-md.md)], należy utworzyć następujący katalog:

    \Moje dokumenty \\ < programu Visual Studio w wersji \> \Templates\ProjectTemplates\CSharp\HelloWorld\

2. Umieść wszystkie szablony dla tej kategorii w nowym folderze.

3. W menu **plik** kliknij pozycję **Nowy**, a następnie kliknij pozycję **projekt**.

4. Sprawdź, czy kategoria HelloWorld pojawia się w oknie dialogowym **Nowy projekt** w okienku **typy projektów** w obszarze [!INCLUDE[csprcs](../includes/csprcs-md.md)].

   Podzestaw szablonów elementów niestandardowych można także grupować do folderu niestandardowego.

##### <a name="to-create-new-custom-item-template-categories"></a>Aby utworzyć nowe kategorie szablonów elementów niestandardowych

1. Utwórz folder w folderze języka w katalogu szablonów elementów niestandardowych. Na przykład, aby utworzyć kategorię HelloWorld dla [!INCLUDE[csprcs](../includes/csprcs-md.md)] szablonów, należy utworzyć następujący katalog:

     \Moje dokumenty \\ < programu Visual Studio w wersji \> \Templates\ItemTemplates\CSharp\HelloWorld\

2. Umieść wszystkie szablony dla tej kategorii w nowym folderze.

3. Utwórz projekt lub Otwórz istniejący projekt.

4. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

5. Sprawdź, czy kategoria HelloWorld pojawia się w oknie dialogowym **Dodaj nowy element** w okienku **typy projektów** .

### <a name="displaying-templates-in-parent-categories"></a>Wyświetlanie szablonów w kategoriach nadrzędnych
 Szablony w podkategoriach można włączyć do wyświetlania w swoich kategoriach nadrzędnych za pomocą elementu `NumberOfParentCategoriesToRollUp` w pliku vstemplate. Te kroki są identyczne zarówno w przypadku szablonów projektu, jak i szablonów elementów.

##### <a name="to-display-templates-in-parent-categories"></a>Aby wyświetlić szablony w kategoriach nadrzędnych

1. Znajdź plik zip, który zawiera szablon.

2. Wyodrębnij plik zip.

3. Otwórz plik. vstemplate w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

4. W `TemplateData` elementu Dodaj element `NumberOfParentCategoriesToRollUp`. Na przykład poniższy kod powoduje, że szablon jest widoczny w kategorii nadrzędnej, ale nie jest wyższy.

    ```
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

5. Zapisz i zamknij plik. vstemplate.

6. Wybierz pliki w szablonie, kliknij prawym przyciskiem myszy zaznaczenie, kliknij polecenie **Wyślij do**, a następnie kliknij **folder skompresowany (zip)** . Pliki są kompresowane do pliku zip.

7. Usuń wyodrębnione pliki szablonów i stary plik Template. zip.

8. Umieść nowy plik zip w katalogu, który miał usunięty plik. zip.

## <a name="see-also"></a>Zobacz też
 [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md) [programu Visual Studio szablon odwołania do schematu](../extensibility/visual-studio-template-schema-reference.md) [NumberOfParentCategoriesToRollUp (szablony Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) [instrukcje: Tworzenie szablonów projektu](../ide/how-to-create-project-templates.md) [instrukcje: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)
