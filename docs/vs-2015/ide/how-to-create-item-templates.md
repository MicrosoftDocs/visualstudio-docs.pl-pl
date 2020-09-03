---
title: 'Instrukcje: Tworzenie szablonów elementów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project item templates, XML reference
- project item templates, custom template locations
- project item templates, creating
- project item templates, metadata files
ms.assetid: 77bc53d4-d607-4820-a032-7e3b365891b5
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c9edc79002a4a2d7c2fe135d7eb4669f5f010599
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668077"
---
# <a name="how-to-create-item-templates"></a>Porady: tworzenie szablonów elementu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kroki opisane w [pierwszej procedurze](#to-add-a-custom-project-item-template-to-the-add-new-item-dialog-box) w tym temacie pokazują, jak utworzyć szablon elementu przy użyciu kreatora **eksportu szablonów** . Jeśli szablon będzie zawierać wiele plików, zobacz [jak: Tworzenie szablonów elementów wieloplikowych](../ide/how-to-create-multi-file-item-templates.md).

 Kreator wykonuje wiele zadań, aby utworzyć podstawowy szablon, ale w wielu przypadkach trzeba ręcznie zmodyfikować plik vstemplate po wyeksportowaniu szablonu. Na przykład jeśli chcesz, aby element pojawił się w oknie dialogowym **Dodaj nowy element** dla [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] projektu aplikacji, musisz wykonać kilka dodatkowych kroków. [Druga procedura](#to-enable-the-item-template-to-be-used-in-a-store-project) w tym temacie pomaga zrealizować to zadanie.

 W niektórych przypadkach może być konieczne lub konieczne ręczne utworzenie szablonu elementu od podstaw. [Trzecia procedura](#to-enable-templates-for-specific-project-sub-types) pokazuje, jak to zrobić.

 Zobacz [Dokumentacja schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md) , aby uzyskać informacje o elementach, których można użyć w pliku. vstemplate.

### <a name="to-add-a-custom-project-item-template-to-the-add-new-item-dialog-box"></a>Aby dodać niestandardowy szablon elementu projektu do okna dialogowego Dodaj nowy element

1. Utwórz lub Otwórz projekt w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

2. Dodaj element do projektu i zmodyfikuj go, jeśli chcesz.

3. Zmodyfikuj plik kodu, aby wskazać miejsce zastąpienia parametrów. Aby uzyskać więcej informacji, zobacz [jak: zastępowanie parametrów w szablonie](../ide/how-to-substitute-parameters-in-a-template.md).

4. W menu **plik** kliknij polecenie **Eksportuj szablon**.

5. Kliknij pozycję **szablon elementu**, wybierz projekt, który zawiera element, a następnie kliknij przycisk **dalej**.

6. Wybierz element, dla którego chcesz utworzyć szablon, a następnie kliknij przycisk **dalej**.

7. Wybierz odwołania do zestawu do uwzględnienia w szablonie, a następnie kliknij przycisk **dalej**.

8. Wpisz nazwę pliku ikony, obraz podglądu, nazwę szablonu i opis szablonu, a następnie kliknij przycisk **Zakończ**.

     Pliki szablonu są dodawane do pliku zip i kopiowane z dowolnego katalogu określonego w oknie dialogowym. Domyślna lokalizacja to **.. \Users \\<username \> \Documents\Visual Studio \<Version> \Moje wyeksportowany szablon \\ ** folder.

    > [!WARNING]
    > W starszych wersjach programu Visual Studio domyślna lokalizacja to **.. \Users \\<username \> \Documents\Visual Studio \<Version> \Templates\ItemTemplates**.

### <a name="to-enable-the-item-template-to-be-used-in-a-store-project"></a>Aby włączyć szablon elementu, który ma być używany w projekcie magazynu

1. Wykonaj kroki opisane w powyższej procedurze, aby wyeksportować szablon elementu.

2. Wyodrębnij plik. vstemplate z pliku zip, który został skopiowany do.. Folder \Users \\ *username*\Documents\Visual Studio w *wersji*\Templates\itemtemplates\folder. (lub **Moje wyeksportowane szablony**).

3. Otwórz plik. vstemplate w programie Visual Studio.

4. W przypadku projektu w języku C# Windows 8.1 Store w pliku. vstemplate Dodaj następujący kod XML w tagu otwierającym i zamykającym `<TemplateData>` : `<TemplateGroupID>WinRT-Managed</TemplateGroupID>` .

    Projekt programu C++ Windows 8.1 Store używa wartości `WinRT-Native-6.3` . W przypadku systemu Windows 10 i innych typów projektów zobacz [TemplateGroupID element (szablony Visual Studio)](../extensibility/templategroupid-element-visual-studio-templates.md).

    Poniższy przykład pokazuje całą zawartość pliku. vstemplate po wierszu XML `<TemplateGroupID>WinRT-Managed</TemplateGroupID>` został do niego dodany. Ten przykład dotyczy projektów w języku C#. Można zmodyfikować \<ProjectType> elementy i, \< [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)> Aby określić inne typy języka i projektu.

   ```xml
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
     <TemplateData>
       <DefaultName>MyItemStoreTemplate.xaml</DefaultName>
       <Name>MyItemStoreTemplate</Name>
       <Description>This is an example itemtemplate</Description>
       <ProjectType>CSharp</ProjectType>
       <SortOrder>10</SortOrder>
       <Icon>__TemplateIcon.ico</Icon>
       <TemplateGroupID>WinRT-Managed</TemplateGroupID>
     </TemplateData>
     <TemplateContent>
       <References />
       <ProjectItem SubType="Designer" TargetFileName="$fileinputname$.xaml" ReplaceParameters="true">MyItemTemplate.xaml</ProjectItem>
       <ProjectItem SubType="Code" TargetFileName="$fileinputname$.xaml.cs" ReplaceParameters="true">MyItemTemplate.xaml.cs</ProjectItem>
     </TemplateContent>
   </VSTemplate>
   ```

    Inne możliwe wartości TemplateGroupID można znaleźć w temacie [TemplateGroupID element (szablony Visual Studio)](../extensibility/templategroupid-element-visual-studio-templates.md)). Aby uzyskać pełne odwołanie. vstemplate, zobacz [Dokumentacja schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)

5. W programie Visual Studio Zapisz plik. vstemplate i zamknij go.

6. Skopiuj i wklej plik. vstemplate z powrotem do pliku zip znajdującego się w.. Folder \Users \\ *username*\Documents\Visual Studio w *wersji*\templates\itemtemplates\folder..

    Jeśli pojawi się okno dialogowe **Kopiuj plik** , wybierz opcję **Kopiuj i Zamień** .

   Teraz można dodać element oparty na tym szablonie do [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] projektu za pomocą okna dialogowego **Dodaj nowy element** .

   Aby uzyskać więcej informacji na temat nazw parametrów, zobacz [Parametry szablonu](../ide/template-parameters.md).

### <a name="to-enable-templates-for-specific-project-sub-types"></a>Aby włączyć szablony dla określonych podtypów projektów

1. Środowisko programistyczne umożliwia udostępnianie elementów projektu w oknie dialogowym Dodaj element dla niektórych projektów. Ta procedura umożliwia udostępnienie niestandardowych elementów dla projektów systemu Windows, sieci Web lub pakietu Office lub baz danych.

    Znajdź element ProjectType w pliku vstemplate szablonu elementu.

    Dodaj element [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) bezpośrednio po elemencie ProjectType.

2. Ustaw wartość tekstową elementu na jedną z następujących wartości:

   1. Windows

   2. Office

   3. baza danych

   4. Sieć Web

      Na przykład: `<ProjectSubType>Database</ProjectSubType>`.

      W poniższym przykładzie przedstawiono szablon elementu dostępny dla projektów pakietu Office.

   ```
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

### <a name="to-manually-create-an-item-template-without-using-the-export-template-wizard"></a>Aby ręcznie utworzyć szablon elementu bez użycia Kreatora eksportu szablonów

1. Utwórz projekt i element projektu.

2. Zmodyfikuj element projektu do momentu, gdy będzie on gotowy do zapisania jako szablon.

3. W razie potrzeby zmodyfikuj plik kodu, aby wskazać, gdzie powinien zostać zamieniony parametr. Aby uzyskać więcej informacji na temat zastępowania parametrów, zobacz How to: zastępowanie parametrów w szablonie.

4. Utwórz plik XML i Zapisz go przy użyciu rozszerzenia nazwy pliku. vstemplate w tym samym katalogu, w którym znajduje się nowy szablon elementu.

5. Utwórz plik XML. vstemplate, aby dostarczyć metadane szablonu elementu. Aby uzyskać więcej informacji, zobacz [Dokumentacja schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md) i przykład w poprzedniej sekcji.

6. Zapisz plik. vstemplate i zamknij go.

7. W Eksploratorze Windows wybierz pliki, które chcesz dołączyć do szablonu, kliknij prawym przyciskiem myszy zaznaczenie, kliknij polecenie Wyślij do, a następnie kliknij folder skompresowany (zip). Wybrane pliki są kompresowane do pliku zip.

8. Skopiuj plik zip i wklej go w lokalizacji szablonu elementu użytkownika. W programie Visual Studio 2015 katalog domyślny to.. \Users \\<username \> \Documents\Visual Studio 2015 \ Templates\ItemTemplates \\ . Aby uzyskać więcej informacji, zobacz How to: Lokalizowanie i organizowanie szablonów projektów i elementów.

## <a name="see-also"></a>Zobacz też
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md) [— instrukcje: Tworzenie szablonów elementów wieloplikowych](../ide/how-to-create-multi-file-item-templates.md) [Dokumentacja schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
