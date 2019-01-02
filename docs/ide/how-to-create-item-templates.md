---
title: Tworzenie szablonów elementów
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- item templates [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: d921257e202e3b8175fcfd01910c00ece4306136
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952264"
---
# <a name="how-to-create-item-templates"></a>Instrukcje: Tworzenie szablonów elementów

W tym artykule pokazano, jak utworzyć szablon elementu za pomocą **Kreatora eksportowania szablonu**. Jeśli Twój szablon będzie składać się z wielu plików, zobacz [jak: Tworzenie szablonów elementów wielu plików](../ide/how-to-create-multi-file-item-templates.md).

## <a name="to-add-a-user-item-template-to-the-add-new-item-dialog-box"></a>Aby dodać szablon elementu użytkownika do okna dialogowego Dodaj nowy element

1. Utwórz lub Otwórz projekt w programie Visual Studio.

1. Dodaj element do projektu i zmodyfikuj go, jeśli chcesz.

1. Zmodyfikuj plik kodu, aby wskazać, gdzie wymiany parametru powinny zostać wykonane. Aby uzyskać więcej informacji, zobacz [jak: Zastępowanie parametrów w szablonie](../ide/how-to-substitute-parameters-in-a-template.md).

1. Na **projektu** menu, wybierz **Eksportuj szablon**.

1. Na **wybierz typ szablonu** wybierz **szablon elementu**, wybierz projekt, który zawiera element, a następnie wybierz **dalej**.

1. Na **wybierz element do eksportowania** wybierz element, który chcesz utworzyć szablon, a następnie wybierz **dalej**.

1. Na **wybierz odwołania do elementu** wybierz odwołania do zestawów do uwzględnienia w szablonie, a następnie wybierz **dalej**.

1. Na **wybierz opcje szablonu** strony, wprowadź nazwę szablonu i opcjonalny opis, obraz ikony i obraz podglądu, a następnie wybierz **Zakończ**.

    Pliki szablonu zostaną dodane do *zip* pliku i kopiowane do katalogu, określone w kreatorze. Domyślna lokalizacja to *%USERPROFILE%\Documents\Visual Studio \<wersji\>\My wyeksportowane szablony*.

1. Jeśli nie wybrana opcja **automatycznie zaimportuj szablon do programu Visual Studio** w **Kreatora eksportowania szablonu**, zlokalizuj wyeksportowanego szablonu. Następnie skopiuj go do katalogu szablonów elementu użytkownika. Domyślna lokalizacja to *%USERPROFILE%\Documents\Visual Studio \<wersji\>\Templates\ItemTemplates*.

1. Zamknij program Visual Studio, a następnie otwórz go ponownie.

1. Utwórz nowy projekt lub Otwórz istniejący projekt, a następnie wybierz **projektu** > **Dodaj nowy element** lub naciśnij **Ctrl** +  **SHIFT**+**A**.

   Szablon elementu jest wyświetlany w **Dodaj nowy element** okno dialogowe. Jeśli dodano opis w **Kreatora eksportowania szablonu**, opis, który jest wyświetlany po prawej stronie okna dialogowego.

## <a name="to-enable-the-item-template-to-be-used-in-a-universal-windows-app-project"></a>Aby włączyć szablon elementu, który ma być używany w projekcie aplikacji uniwersalnej Windows

Kreator wykonuje większość pracy, aby utworzyć podstawowy szablon, ale w wielu przypadkach należy ręcznie zmodyfikować *.vstemplate* pliku po wyeksportowaniu szablonu. Na przykład, jeśli chcesz, aby element był wyświetlany w **Dodaj nowy element** okno dialogowe projektu aplikacji uniwersalnej Windows, należy wykonać kilka dodatkowych kroków.

1. Wykonaj kroki opisane w poprzedniej sekcji, aby wyeksportować szablon elementu.

1. Wyodrębnij *zip* pliku, który został utworzony i otwarty *.vstemplate* pliku w programie Visual Studio.

1. Aby uzyskać C# Universal Windows projektu, Dodaj następujący kod XML wewnątrz `<TemplateData>` elementu:

   ```xml
   <TemplateID>Microsoft.CSharp.Class</TemplateID>
   ```

1. W programie Visual Studio, należy zapisać *.vstemplate* plik i zamknij go.

1. Skopiuj i Wklej *.vstemplate* pliku z powrotem na *zip* pliku.

     Jeśli **kopiowania pliku** pojawi się okno dialogowe, wybierz **Kopiuj i Zamień** opcji.

Możesz teraz dodać element oparty na tym szablonie do projektu Windows Universal z **Dodaj nowy element** okno dialogowe.

## <a name="to-enable-templates-for-specific-project-subtypes"></a>Aby umożliwić szablony dla określonego projektu podtypów

Można określić, czy szablon powinien pojawić się tylko dla tylko niektórych podtypy projektów, takich jak Windows, Office, bazy danych lub w sieci Web.

1. Znajdź `ProjectType` element *.vstemplate* w pliku szablonu elementu.

1. Dodaj [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) element natychmiast po `ProjectType` elementu.

1. Ustaw wartość tekstowego elementu do jednego z następujących wartości:

    - Windows
    - Office
    - Baza danych
    - sieć Web

Na przykład: `<ProjectSubType>Database</ProjectSubType>`.

W poniższym przykładzie pokazano szablon elementu dla **Office** projektów.

```xml
<VSTemplate Version="2.0.0" Type="Item" Version="2.0.0">
   <TemplateData>
      <Name>Class</Name>
      <Description>An empty class file</Description>
      <Icon>Class.ico</Icon>
      <ProjectType>CSharp</ProjectType>
      <ProjectSubType>Office</ProjectSubType>
      <DefaultName>Class.cs</DefaultName>
   </TemplateData>
   <TemplateContent>
      <ProjectItem>Class1.cs</ProjectItem>
   </TemplateContent>
</VSTemplate>
```

## <a name="to-manually-create-an-item-template-without-using-the-export-template-wizard"></a>Aby ręcznie utworzyć szablon elementu bez użycia Kreatora eksportowania szablonu

W niektórych przypadkach możesz chcieć ręcznie utworzyć szablon elementu od podstaw.

1. Tworzenie projektu i elementu projektu.

1. Zmodyfikuj element projektu, dopóki nie jest gotowa do zapisania jako szablonu.

1. Zmodyfikuj plik kodu, aby wskazać, gdzie wymiany parametru wystąpi, jeśli w dowolnym miejscu. Aby uzyskać więcej informacji na temat wymiany parametru zobacz [jak: Zastępowanie parametrów w szablonie.](../ide/how-to-substitute-parameters-in-a-template.md)

1. Utwórz plik XML i zapisz go z *.vstemplate* rozszerzenie pliku, w tym samym katalogu co plik elementu projektu.

1. Edytuj *.vstemplate* plik XML do udostępnienia metadanych szablonu elementu. Aby uzyskać więcej informacji, zobacz [odwołanie do schematu szablonu (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md) i w przykładzie w poprzedniej sekcji.

1. Zapisz *.vstemplate* plik i zamknij go.

1. W **Eksplorator Windows**, zaznacz pliki, które chcesz uwzględnić w szablonie. Kliknij prawym przyciskiem myszy zaznaczenie, a następnie wybierz **wysyłać** > **skompresowany folder (zip)**. Wybrane pliki są kompresowane do *zip* pliku.

1. Kopiuj *zip* plików i wklej go w lokalizacji szablonów elementów użytkownika. W programie Visual Studio 2017, domyślnym katalogiem jest *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ItemTemplates*. Aby uzyskać więcej informacji, zobacz [jak: Lokalizowanie i organizowanie szablonów projektów i elementów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Instrukcje: Tworzenie szablonów elementów wielu plików](../ide/how-to-create-multi-file-item-templates.md)
- [Visual Studio odwołanie do schematu szablonu (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md)
