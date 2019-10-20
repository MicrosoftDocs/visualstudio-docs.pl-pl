---
title: 'Instrukcje: Tworzenie szablonów elementów wieloplikowych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e70039f361ac3410a8ddcccb0f139d8bdcb32ed9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668094"
---
# <a name="how-to-create-multi-file-item-templates"></a>Porady: tworzenie szablonów elementów wielu plików
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Szablony elementów mogą określać tylko jeden element, ale czasami element składa się z wielu plików. Na przykład szablon elementu Windows Forms dla Visual Basic wymaga następujących trzech plików:

- Plik. vb, który zawiera kod dla formularza.

- Plik. Designer. vb zawierający informacje o projektancie dla formularza.

- Plik. resx zawierający osadzone zasoby formularza.

  Szablony elementów wieloplikowych wymagają parametrów, aby upewnić się, że podczas tworzenia elementu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] są używane poprawne rozszerzenia nazw plików. W przypadku tworzenia szablonu elementu przy użyciu kreatora **eksportu szablonów** te parametry są generowane automatycznie i nie jest wymagane dalsze edytowanie. Poniższe kroki wyjaśniają, jak używać parametrów, aby upewnić się, że tworzone są poprawne rozszerzenia nazw plików.

### <a name="to-manually-create-a-multi-file-item-template"></a>Aby ręcznie utworzyć szablon elementu wieloplikowego

1. Utwórz szablon elementu, jak utworzysz szablon elementu jednoplikowego. Aby uzyskać więcej informacji, zobacz [How to: Create Item templates](../ide/how-to-create-item-templates.md).

2. Dodaj `TargetFileName` atrybuty do każdego elementu `ProjectItem`. Ustaw wartości atrybutów `TargetFileName` na $fileinputname $. *FileExtension*, gdzie *FileExtension* jest rozszerzeniem nazwy pliku, który jest dołączany do szablonu. Na przykład:

    ```
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

     Gdy element pochodzący z tego szablonu zostanie dodany do projektu, nazwy plików będą oparte na nazwie wpisanej przez użytkownika w oknie dialogowym **Dodaj nowy element** .

3. Wybierz pliki do uwzględnienia w szablonie, kliknij prawym przyciskiem myszy zaznaczenie, kliknij polecenie **Wyślij do**, a następnie kliknij **folder skompresowany (zip)** . Wybrane pliki są kompresowane do pliku zip.

4. Umieść plik zip w lokalizacji szablonu elementu użytkownika. Domyślnie katalog to \Moje Documents\Visual Studio w *wersji*\Templates\ItemTemplates \\. Aby uzyskać więcej informacji, zobacz [How to: Lokalizowanie i organizowanie szablonów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia szablon Windows Forms [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Po utworzeniu elementu na podstawie tego szablonu nazwy trzech utworzonych plików będą zgodne z nazwą wprowadzoną w oknie dialogowym **Dodaj nowy element** .

```
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
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md) [jak: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md) [Parametry szablonu](../ide/template-parameters.md) [instrukcje: zastępowanie parametrów w szablonie](../ide/how-to-substitute-parameters-in-a-template.md)
