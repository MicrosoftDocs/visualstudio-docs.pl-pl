---
title: Tworzenie szablonów elementów
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- item templates [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 62004c5c96fa708f98ab49f4810ec2fc1c38eadc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594724"
---
# <a name="how-to-create-item-templates"></a>Jak: Tworzenie szablonów elementów

W tym artykule pokazano, jak utworzyć szablon elementu za pomocą **Kreatora eksportu szablonów**. Jeśli szablon będzie składał się z wielu plików, zobacz [Jak: Tworzenie szablonów elementów z wieloma plikami](../ide/how-to-create-multi-file-item-templates.md).

## <a name="add-an-item-template-to-the-add-new-item-dialog-box"></a>Dodawanie szablonu elementu do okna dialogowego Dodawanie nowego elementu

1. Tworzenie lub otwieranie projektu w programie Visual Studio.

1. Dodaj element do projektu i zmodyfikuj go, jeśli chcesz.

1. Zmodyfikuj plik kodu, aby wskazać, gdzie powinno nastąpić zastąpienie parametrów. Aby uzyskać więcej informacji, zobacz [Jak: Zastępowanie parametrów w szablonie](../ide/how-to-substitute-parameters-in-a-template.md).

1. W menu **Projekt** wybierz polecenie **Eksportuj szablon**.

1. Na stronie **Wybierz typ szablonu** wybierz pozycję **Szablon elementu**, wybierz projekt zawierający element, a następnie wybierz pozycję **Dalej**.

1. Na stronie **Wybierz element do wyeksportowania** wybierz element, dla którego chcesz utworzyć szablon, a następnie wybierz pozycję **Dalej**.

1. Na stronie **Wybierz odwołania do elementu** wybierz odwołania do złożenia do uwzględnienia w szablonie, a następnie wybierz pozycję **Dalej**.

1. Na stronie **Wybierz opcje szablonu** wprowadź nazwę szablonu i opcjonalny opis, obraz ikony i obraz podglądu, a następnie wybierz pozycję **Zakończ**.

    Pliki szablonu są dodawane do pliku *zip* i kopiowane do katalogu określonego w kreatorze. Domyślną lokalizacją jest *%USERPROFILE%\Documents\Visual Studio \<version\>\My Exported Templates*.

1. Jeśli nie zaznaczono opcji **Automatycznie zaimportuj szablon do programu Visual Studio** w **Kreatorze eksportu szablonów,** znajdź wyeksportowany szablon. Następnie skopiuj go do katalogu szablonu elementu użytkownika. Domyślną lokalizacją jest *%USERPROFILE%\Documents\Visual Studio \<version\>\Templates\ItemTemplates*.

1. Zamknij program Visual Studio, a następnie otwórz go ponownie.

1. Utwórz nowy projekt lub otwórz istniejący projekt, a następnie wybierz pozycję **Project** > **Add New Item** lub Naciśnij klawisz **Ctrl**+**Shift**+**A**.

   Szablon elementu pojawi się w oknie dialogowym **Dodawanie nowego elementu.** Jeśli opis został dodany w **Kreatorze eksportu szablonów,** opis pojawi się po prawej stronie okna dialogowego.

## <a name="enable-the-item-template-to-be-used-in-a-universal-windows-app-project"></a>Włączanie użycia szablonu elementu w projekcie aplikacji uniwersalnej systemu Windows

Kreator wykonuje wiele pracy, aby utworzyć podstawowy szablon, ale w wielu przypadkach trzeba ręcznie zmodyfikować plik *vstemplate* po wyeksportowanym szablonie. Na przykład jeśli chcesz, aby element pojawiał się w oknie dialogowym **Dodawanie nowego elementu** dla projektu uniwersalnej aplikacji systemu Windows, musisz wykonać kilka dodatkowych kroków.

1. Postępuj zgodnie z instrukcjami w poprzedniej sekcji, aby wyeksportować szablon towaru.

1. Wyodrębnij utworzony plik *zip* i otwórz plik *vstemplate* w programie Visual Studio.

1. W przypadku projektu systemu Uniwersalnego systemu Windows `<TemplateData>` języka C# dodaj następujący kod XML wewnątrz elementu:

   ```xml
   <TemplateID>Microsoft.CSharp.Class</TemplateID>
   ```

1. W programie Visual Studio zapisz plik *vstemplate* i zamknij go.

1. Skopiuj i wklej plik *vstemplate* z powrotem do pliku *zip.*

     Jeśli zostanie wyświetlone okno dialogowe **Kopiuj plik,** wybierz opcję **Kopiuj i zamień.**

Teraz można dodać element oparty na tym szablonie do projektu systemu Uniwersalnego systemu Windows w oknie dialogowym **Dodawanie nowego elementu.**

## <a name="enable-templates-for-specific-project-subtypes"></a>Włączanie szablonów dla określonych podtypów projektu

Można określić, że szablon powinien być wyświetlany tylko dla niektórych podtypów projektu, takich jak Windows, Office, Database lub Web.

1. Znajdź `ProjectType` element w pliku *vstemplate* dla szablonu elementu.

1. Dodaj [Element ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) bezpośrednio `ProjectType` po elemencie.

1. Ustaw wartość tekstową elementu na jedną z następujących wartości:

    - Windows
    - Office
    - baza danych
    - sieć Web

Na przykład: `<ProjectSubType>Database</ProjectSubType>`.

W poniższym przykładzie przedstawiono szablon elementu dla projektów **pakietu Office.**

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

## <a name="manually-create-an-item-template"></a>Ręczne tworzenie szablonu elementu

W niektórych przypadkach można utworzyć szablon elementu ręcznie, od podstaw.

1. Tworzenie elementu projektu i projektu.

2. Zmodyfikuj element projektu, dopóki nie będzie gotowy do zapisania go jako szablonu.

3. Zmodyfikuj plik kodu, aby wskazać, gdzie ma nastąpić zastąpienie parametrów, jeśli w dowolnym miejscu. Aby uzyskać więcej informacji na temat zastępowania [parametrów, zobacz Jak: Zastępowanie parametrów w szablonie.](../ide/how-to-substitute-parameters-in-a-template.md)

4. Utwórz plik XML i zapisz go z rozszerzeniem pliku *vstemplate* w tym samym katalogu co plik elementu projektu.

5. Edytuj plik XML *vstemplate,* aby podać metadane szablonu elementu. Aby uzyskać więcej informacji, zobacz [odwołanie do schematu szablonu (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md) i przykład w poprzedniej sekcji.

6. Zapisz plik *vstemplate* i zamknij go.

7. W **Eksploratorze Windows**wybierz pliki, które chcesz uwzględnić w szablonie. Kliknij prawym przyciskiem myszy zaznaczenie i wybierz polecenie **Wyślij do** > **folderu skompresowanego (spakowane).** Wybrane pliki zostaną skompresowane do pliku *zip.*

::: moniker range="vs-2017"

8. Skopiuj plik *zip* i wklej go w lokalizacji szablonu elementu użytkownika. Katalog domyślny to *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ItemTemplates*. Aby uzyskać więcej informacji, zobacz [Jak: Lokalizowanie i organizowanie szablonów projektów i elementów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

::: moniker range=">=vs-2019"

8. Skopiuj plik *zip* i wklej go w lokalizacji szablonu elementu użytkownika. Katalog domyślny to *%USERPROFILE%\Documents\Visual Studio 2019\Templates\ItemTemplates*. Aby uzyskać więcej informacji, zobacz [Jak: Lokalizowanie i organizowanie szablonów projektów i elementów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Jak: Tworzenie szablonów elementów z wieloma plikami](../ide/how-to-create-multi-file-item-templates.md)
- [Odwołanie do schematu szablonu programu Visual Studio (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md)
