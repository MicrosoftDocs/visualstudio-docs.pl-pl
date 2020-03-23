---
title: Tworzenie szablonów elementów z wieloma plikami
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e8a6e5358a87e3d64b341c89b8ffd4cd3cf3e325
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593736"
---
# <a name="how-to-create-multi-file-item-templates"></a>Jak: Tworzenie szablonów elementów z wieloma plikami

Szablony elementów mogą określać tylko jeden element, ale czasami element składa się z wielu plików. Na przykład szablon elementu formularzy systemu Windows wymaga następujących trzech plików:

- Plik zawierający kod formularza

- Plik zawierający informacje o projektancie formularza

- Plik zawierający osadzone zasoby formularza

Szablony elementów z wieloma plikami wymagają parametrów, aby upewnić się, że podczas tworzenia elementu są używane poprawne rozszerzenia plików. Jeśli szablon elementu z wieloma plikami zostanie utworzony za pomocą **Kreatora eksportu szablonów,** parametry te są generowane automatycznie i nie jest wymagana dalsza edycja.

## <a name="use-the-export-template-wizard"></a>Korzystanie z Kreatora eksportu szablonów

Szablon elementu z wieloma plikami można utworzyć w taki sam sposób, jak szablon pojedynczego elementu. Zobacz [Jak: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md). Na stronie **Wybierz element do wyeksportowania** kreatora wybierz plik zawierający pliki zależne (na przykład plik formularza Formularze systemu Windows). Kreator automatycznie zawiera wszystkie pliki zależne, takie jak pliki projektanta i zasobów, w szablonie.

## <a name="manually-create-a-multi-file-item-template"></a>Ręczne tworzenie szablonu elementu z wieloma plikami

1. Utwórz szablon elementu tak, jak ręcznie utwórz szablon pojedynczego pliku, ale dołącz każdy plik, który stanowi element wielonamedowy.

1. W pliku XML *.vstemplate* `ProjectItem` dodaj element dla każdego pojedynczego `TargetFileName` pliku i dodaj atrybut do tego elementu. Ustaw wartość atrybutu na `TargetFileName` *$fileinputname$. FileExtension*, gdzie *FileExtension* jest rozszerzeniem pliku, który jest zawarty w szablonie. Przykład:

    ```xml
    <ProjectItem TargetFileName="$fileinputname$.vb">
        Form1.vb
    </ProjectItem>
    <ProjectItem TargetFileName="$fileinputname$.Designer.vb">
        Form1.Designer.vb
    </ProjectItem>
    <ProjectItem TargetFileName="$fileinputname$.resx">
        Form1.resx
    </ProjectItem>
    ```

     > [!NOTE]
     > Gdy element pochodzący z tego szablonu zostanie dodany do projektu, nazwy plików będą pochodzić od nazwy wprowadzonej przez użytkownika w oknie dialogowym **Dodawanie nowego elementu.**

1. Wybierz pliki, które mają zostać uwzględnione w szablonie, kliknij prawym przyciskiem myszy zaznaczenie i wybierz polecenie **Wyślij do** > **skompresowanego (spakowane) folderu**.

   Wybrane pliki zostaną skompresowane do pliku *zip.*

1. Skopiuj plik *zip* do lokalizacji szablonu elementu użytkownika. Domyślnie katalog to *%USERPROFILE%\Documents\Visual \<Studio\>Version \Templates\ItemTemplates*. Aby uzyskać więcej informacji, zobacz [Jak: Lokalizowanie i organizowanie szablonów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

1. Zamknij program Visual Studio, a następnie otwórz go ponownie.

1. Utwórz nowy projekt lub otwórz istniejący projekt, a następnie wybierz pozycję **Project** > **Add New Item** lub Naciśnij klawisz **Ctrl**+**Shift**+**A**.

   Szablon elementu z wieloma plikami pojawi się w oknie dialogowym **Dodawanie nowego elementu.**

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono szablon formularzy systemu Windows. Po utworzeniu elementu na podstawie tego szablonu nazwy trzech utworzonych plików będą zgodne z nazwą wprowadzona w oknie dialogowym **Dodawanie nowego elementu.**

```xml
<VSTemplate Version="2.0.0" Type="Item"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-file Item Template</Name>
        <Icon>Icon.ico</Icon>
        <Description>An example of a multi-file item template</Description>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectItem TargetFileName="$fileinputname$.vb" SubType="Form">
            Form1.vb
        </ProjectItem>
        <ProjectItem TargetFileName="$fileinputname$.Designer.vb">
            Form1.Designer.vb
        </ProjectItem>
        <ProjectItem TargetFileName="$fileinputname$.resx">
            Form1.resx
        </ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Zobacz też

- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Jak: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [Jak: Zastępowanie parametrów w szablonie](../ide/how-to-substitute-parameters-in-a-template.md)
