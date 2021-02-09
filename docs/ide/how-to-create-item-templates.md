---
title: Tworzenie szablonów elementów
description: Dowiedz się, jak za pomocą Kreatora eksportu szablonów utworzyć szablon elementu w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- item templates [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 3f8dc8ddb5cc17f2ac575ea023283f60f579ccbd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875396"
---
# <a name="how-to-create-item-templates"></a>Instrukcje: Tworzenie szablonów elementów

W tym artykule przedstawiono sposób tworzenia szablonu elementu przy użyciu **Kreatora eksportu szablonów**. Jeśli szablon będzie zawierać wiele plików, zobacz [jak: Tworzenie szablonów elementów wieloplikowych](../ide/how-to-create-multi-file-item-templates.md).

## <a name="add-an-item-template-to-the-add-new-item-dialog-box"></a>Dodaj szablon elementu do okna dialogowego Dodaj nowy element

1. Utwórz lub Otwórz projekt w programie Visual Studio.

1. Dodaj element do projektu i zmodyfikuj go, jeśli chcesz.

1. Zmodyfikuj plik kodu, aby wskazać miejsce zastąpienia parametrów. Aby uzyskać więcej informacji, zobacz [jak: zastępowanie parametrów w szablonie](../ide/how-to-substitute-parameters-in-a-template.md).

1. W menu **projekt** wybierz polecenie **Eksportuj szablon**.

1. Na stronie **Wybieranie typu szablonu** wybierz **szablon elementu**, wybierz projekt, który zawiera element, a następnie wybierz **dalej**.

1. Na stronie **Wybierz element do eksportowania** wybierz element, dla którego chcesz utworzyć szablon, a następnie wybierz przycisk **dalej**.

1. Na stronie **Wybierz odwołania do elementów** wybierz odwołania do zestawu do uwzględnienia w szablonie, a następnie wybierz **dalej**.

1. Na stronie **Wybieranie opcji szablonu** wprowadź nazwę szablonu i opcjonalny opis, obraz ikony i obraz podglądu, a następnie wybierz przycisk **Zakończ**.

    Pliki szablonu są dodawane do pliku *zip* i kopiowane do katalogu określonego w kreatorze. Domyślna lokalizacja to *%USERPROFILE%\Documents\Visual Studio \<version\> \Moje wyeksportowany szablon*.

1. Jeśli nie wybrano opcji **automatycznie Importuj szablon do programu Visual Studio** w **Kreatorze eksportu szablonów**, zlokalizuj wyeksportowany szablon. Następnie skopiuj go do katalogu szablonów elementu użytkownika. Domyślna lokalizacja to *%USERPROFILE%\Documents\Visual Studio \<version\> \Templates\ItemTemplates*.

1. Zamknij program Visual Studio, a następnie otwórz go ponownie.

1. Utwórz nowy projekt lub Otwórz istniejący projekt, a następnie wybierz pozycję **projekt**  >  **Dodaj nowy element** lub naciśnij **klawisze CTRL** + **SHIFT** + **a**.

   Szablon elementu pojawia się w oknie dialogowym **Dodaj nowy element** . Jeśli dodano opis w **Kreatorze eksportu szablonów**, opis pojawia się po prawej stronie okna dialogowego.

## <a name="enable-the-item-template-to-be-used-in-a-universal-windows-app-project"></a>Włącz szablon elementu, który ma być używany w projekcie aplikacji uniwersalnej systemu Windows

Kreator wykonuje wiele zadań, aby utworzyć podstawowy szablon, ale w wielu przypadkach trzeba ręcznie zmodyfikować plik *vstemplate* po wyeksportowaniu szablonu. Na przykład jeśli chcesz, aby element pojawił się w oknie dialogowym **Dodaj nowy element** dla projektu uniwersalnej aplikacji systemu Windows, musisz wykonać kilka dodatkowych kroków.

1. Wykonaj kroki opisane w poprzedniej sekcji, aby wyeksportować szablon elementu.

1. Wyodrębnij utworzony plik *zip* , a następnie otwórz plik *. vstemplate* w programie Visual Studio.

1. W przypadku projektu uniwersalnego systemu Windows w języku C# Dodaj następujący kod XML wewnątrz `<TemplateData>` elementu:

   ```xml
   <TemplateID>Microsoft.CSharp.Class</TemplateID>
   ```

1. W programie Visual Studio Zapisz plik *. vstemplate* i zamknij go.

1. Skopiuj i wklej plik *. vstemplate* z powrotem do pliku *zip* .

     Jeśli pojawi się okno dialogowe **Kopiuj plik** , wybierz opcję **Kopiuj i Zamień** .

Teraz można dodać element oparty na tym szablonie do uniwersalnego projektu systemu Windows w oknie dialogowym **Dodaj nowy element** .

## <a name="enable-templates-for-specific-project-subtypes"></a>Włączanie szablonów dla określonych podtypów projektów

Można określić, że szablon powinien występować tylko w przypadku niektórych podtypów projektów, takich jak Windows, Office, Database lub Web.

1. Znajdź `ProjectType` element w pliku *vstemplate* szablonu elementu.

1. Dodaj element [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) bezpośrednio po `ProjectType` elemencie.

1. Ustaw wartość tekstową elementu na jedną z następujących wartości:

    - Windows
    - Office
    - baza danych
    - Internet

Na przykład: `<ProjectSubType>Database</ProjectSubType>`.

Poniższy przykład pokazuje szablon elementu dla projektów **pakietu Office** .

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

## <a name="manually-create-an-item-template"></a>Ręcznie Utwórz szablon elementu

W niektórych przypadkach może być konieczne ręczne utworzenie szablonu elementu od podstaw.

1. Utwórz projekt i element projektu.

2. Zmodyfikuj element projektu do momentu, gdy będzie on gotowy do zapisania jako szablon.

3. Zmodyfikuj plik kodu, aby wskazać miejsce zastąpienia parametru, jeśli jest to możliwe. Aby uzyskać więcej informacji na temat zastępowania parametrów, zobacz [How to: zastępowanie parametrów w szablonie.](../ide/how-to-substitute-parameters-in-a-template.md)

4. Utwórz plik XML i Zapisz go przy użyciu rozszerzenia pliku *. vstemplate* w tym samym katalogu, w którym znajduje się plik elementu projektu.

5. Edytuj plik XML *. vstemplate* , aby dostarczyć metadane szablonu elementu. Aby uzyskać więcej informacji, zobacz [Dokumentacja schematu szablonu (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md) i przykład w poprzedniej sekcji.

6. Zapisz plik *. vstemplate* i zamknij go.

7. W **Eksploratorze Windows** wybierz pliki, które chcesz uwzględnić w szablonie. Kliknij prawym przyciskiem myszy zaznaczenie, a następnie wybierz polecenie **Wyślij do**  >  **folderu skompresowanego (spakowanego)**. Wybrane pliki są kompresowane do pliku *zip* .

::: moniker range="vs-2017"

8. Skopiuj plik *zip* i wklej go w lokalizacji szablonu elementu użytkownika. Domyślnym katalogiem jest *%USERPROFILE%\Documents\Visual Studio 2017 \ Templates\ItemTemplates*. Aby uzyskać więcej informacji, zobacz [How to: Lokalizowanie i organizowanie szablonów projektów i elementów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

::: moniker range=">=vs-2019"

8. Skopiuj plik *zip* i wklej go w lokalizacji szablonu elementu użytkownika. Domyślnym katalogiem jest *%USERPROFILE%\Documents\Visual Studio 2019 \ Templates\ItemTemplates*. Aby uzyskać więcej informacji, zobacz [How to: Lokalizowanie i organizowanie szablonów projektów i elementów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Instrukcje: Tworzenie szablonów elementów wieloplikowych](../ide/how-to-create-multi-file-item-templates.md)
- [Odwołanie do schematu szablonu programu Visual Studio (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md)
