---
title: Tworzenie szablonów elementów wielu plików
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: dd2cbe6d7a0ff586c0e673a6eb0e3d42aa4dec4e
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065412"
---
# <a name="how-to-create-multi-file-item-templates"></a>Porady: Tworzenie szablonów elementów wielu plików

Szablony elementów może określić tylko jeden element, ale czasami element składa się z wielu plików. Na przykład szablon elementu formularze Windows wymaga następujących trzech plików:

- Plik, który zawiera kod dla formularza

- Plik, który zawiera informacje o projektancie formularza

- Plik zawierający zasoby osadzone dla formularza

Szablony elementów wielu plików wymagane parametry, aby upewnić się, że rozszerzenia odpowiedniego pliku są używane podczas tworzenia elementu. Jeśli tworzysz szablonów elementów wielu plików za pomocą **Kreatora eksportowania szablonu**, parametry te są generowane automatycznie i nie dalszej edycji jest wymagany.

## <a name="to-create-a-multi-file-item-template-by-using-the-export-template-wizard"></a>Aby utworzyć szablon elementów wielu plików za pomocą Kreatora eksportowania szablonu

Można utworzyć szablon elementów wielu plików w taki sam sposób, jak szablon elementu pojedynczego pliku. Zobacz [porady: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md). Na **wybierz element do eksportowania** strony kreatora, wybierz plik, który zawiera pliki zależne (na przykład plik formularzy Windows Forms). W kreatorze są automatycznie dostępne pliki zależne, takie jak projektant i pliki zasobów w szablonie.

## <a name="to-manually-create-a-multi-file-item-template"></a>Ręczne tworzenie szablonów elementów wielu plików

1. Utwórz szablon elementu po będzie ręcznie utworzyć szablon elementu pojedynczy plik, ale zawierają każdego pliku, który stanowi elementów wielu plików.

1. W *.vstemplate* XML Dodaj `ProjectItem` elementu dla każdego pliku i Dodaj `TargetFileName` atrybutu tego elementu. Ustaw wartość `TargetFileName` atrybutu *$fileinputname$. FileExtension*, gdzie *FileExtension* jest rozszerzeniem pliku, który jest uwzględniane w szablonie. Na przykład:

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
     > Gdy element pochodzące z tego szablonu zostanie dodany do projektu, nazw plików, z której pochodzą z nazwy, który użytkownik wprowadza w **Dodaj nowy element** okno dialogowe.

1. Wybierz pliki do uwzględnienia w szablonie, kliknij prawym przyciskiem myszy zaznaczenie, a następnie wybierz **wysyłać** > **skompresowany folder (zip)**.

   Wybrane pliki są kompresowane do *zip* pliku.

1. Kopiuj *zip* plik do lokalizacji szablonów elementów użytkownika. Domyślnie katalog znajduje się *%USERPROFILE%\Documents\Visual Studio \<wersji\>\Templates\ItemTemplates*. Aby uzyskać więcej informacji, zobacz [porady: lokalizowanie i organizacja szablonów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

1. Zamknij program Visual Studio, a następnie otwórz go ponownie.

1. Utwórz nowy projekt lub Otwórz istniejący projekt, a następnie wybierz **projektu** > **Dodaj nowy element** lub naciśnij **Ctrl** +  **SHIFT**+**A**.

   Szablon elementów wielu plików jest wyświetlany w **Dodaj nowy element** okno dialogowe.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia szablon Windows Forms. Gdy element zostanie utworzony na podstawie tego szablonu, nazwy trzy utworzone pliki będą zgodne nazwy wprowadzone w **Dodaj nowy element** okno dialogowe.

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

## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Porady: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [Instrukcje: zastępowanie parametrów w szablonie](../ide/how-to-substitute-parameters-in-a-template.md)