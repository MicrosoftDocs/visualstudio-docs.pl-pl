---
title: Tworzenie szablonów elementów wieloplikowych
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 82047b4a49db4edbea4ce965d1987f87a799a9f7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655941"
---
# <a name="how-to-create-multi-file-item-templates"></a>Instrukcje: Tworzenie szablonów elementów wieloplikowych

Szablony elementów mogą określać tylko jeden element, ale czasami element składa się z wielu plików. Na przykład szablon elementu Windows Forms wymaga trzech następujących plików:

- Plik zawierający kod dla formularza

- Plik, który zawiera informacje dotyczące projektanta formularza

- Plik zawierający osadzone zasoby formularza

Szablony elementów wieloplikowych wymagają parametrów, aby upewnić się, że podczas tworzenia elementu są używane poprawne rozszerzenia plików. Jeśli utworzysz szablon elementu wieloplikowego za pomocą **Kreatora eksportu szablonów**, te parametry są generowane automatycznie i nie jest wymagane dalsze edytowanie.

## <a name="use-the-export-template-wizard"></a>Korzystanie z Kreatora eksportu szablonów

Szablon elementu wieloplikowego można utworzyć w taki sam sposób jak szablon elementu jednoplikowego. Zobacz [How to: Create Item templates](../ide/how-to-create-item-templates.md). Na stronie **Wybierz element do eksportowania** kreatora wybierz plik, który ma pliki zależne (na przykład Windows Forms plik formularza). Kreator automatycznie dołącza do szablonu wszystkie pliki zależne, takie jak projektant i pliki zasobów.

## <a name="manually-create-a-multi-file-item-template"></a>Ręcznie Utwórz szablon elementu wieloplikowego

1. Utwórz szablon elementu, jak utworzysz ręcznie szablon elementu jednoplikowego, ale Uwzględnij każdy plik stanowiący element wieloplikowy.

1. W pliku XML *. vstemplate* dodaj element `ProjectItem` dla każdego pojedynczego pliku i dodaj atrybut `TargetFileName` do tego elementu. Ustaw wartość atrybutu `TargetFileName` na *$fileinputname $. FileExtension*, gdzie *FileExtension* to rozszerzenie pliku, który jest dołączany do szablonu. Na przykład:

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
     > Gdy element pochodzący z tego szablonu zostanie dodany do projektu, nazwy plików będą pochodzić od nazwy, którą użytkownik wprowadza w oknie dialogowym **Dodaj nowy element** .

1. Wybierz pliki do uwzględnienia w szablonie, kliknij prawym przyciskiem myszy zaznaczenie, a następnie wybierz polecenie **Wyślij do**  > **folderu skompresowanego (spakowanego)** .

   Wybrane pliki są kompresowane do pliku *zip* .

1. Skopiuj plik *zip* do lokalizacji szablonu elementu użytkownika. Domyślnie katalog jest *%USERPROFILE%\Documents\Visual Studio \<Version \> \templates\itemtemplates*. Aby uzyskać więcej informacji, zobacz [How to: Lokalizowanie i organizowanie szablonów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

1. Zamknij program Visual Studio, a następnie otwórz go ponownie.

1. Utwórz nowy projekt lub Otwórz istniejący projekt, a następnie wybierz **projekt**  > **Dodaj nowy element** lub naciśnij **klawisze CTRL** +**SHIFT** +**a**.

   Szablon elementu wieloplikowego jest wyświetlany w oknie dialogowym **Dodaj nowy element** .

## <a name="example"></a>Przykład

Poniższy przykład przedstawia szablon Windows Forms. Po utworzeniu elementu na podstawie tego szablonu nazwy trzech utworzonych plików będą zgodne z nazwą wprowadzoną w oknie dialogowym **Dodaj nowy element** .

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
- [Instrukcje: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [Instrukcje: zastępowanie parametrów w szablonie](../ide/how-to-substitute-parameters-in-a-template.md)