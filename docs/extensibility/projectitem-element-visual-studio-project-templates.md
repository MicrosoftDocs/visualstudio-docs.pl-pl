---
title: Element ProjectItem (szablony projektów programu Visual Studio) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11052d8e585f1d06f6d787402001cfbbe2b6810f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701838"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>Element ProjectItem (szablony projektów programu Visual Studio)
Określa plik, który znajduje się w szablonie projektu.

> [!NOTE]
> Element `ProjectItem` akceptuje różne atrybuty w zależności od tego, czy szablon jest dla projektu lub elementu. W tym `ProjectItem` temacie wyjaśniono element szablonów projektów. Aby uzyskać wyjaśnienie `ProjectItem` elementu dla szablonów elementów, zobacz [ProjectItem Element (Szablony elementów programu Visual Studio).](../extensibility/projectitem-element-visual-studio-item-templates.md)

 \<>> \<szablonu>>> \< \<projektu>

## <a name="syntax"></a>Składnia

```
<ProjectItem
    TargetFileName="TargetFileName.ext"
    ReplaceParameters="true/false"
    OpenInEditor="true/false"
    OpenInWebBrowser="true/false"
    OpenInHelpBrowser="true/false"
    OpenOrder="Value">
        FileName.ext
</ProjectItem>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

| Atrybut | Opis |
|---------------------| - |
| `TargetFileName` | Atrybut opcjonalny.<br /><br /> Określa nazwę i ścieżkę elementu projektu podczas tworzenia projektu na podstawie szablonu. Ten atrybut jest przydatny do tworzenia struktury katalogów innej niż struktura katalogów w pliku *.zip* szablonu lub do tworzenia nazwy elementu przy użyciu zastępowania parametrów. |
| `ReplaceParameters` | Atrybut opcjonalny.<br /><br /> Wartość logiczna określająca, czy element ma wartości parametrów, które muszą zostać zastąpione podczas tworzenia projektu na podstawie szablonu. Wartością `false`domyślną jest . |
| `OpenInEditor` | Atrybut opcjonalny.<br /><br /> Wartość logiczna, która określa, czy element powinien zostać [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] otwarty w odpowiednim edytorze podczas tworzenia projektu na podstawie szablonu.<br /><br /> `OpenInWebBrowser` Atrybuty `OpenInHelpBrowser` i atrybuty są ignorowane `true`w elemencie o `OpenInEditor` wartości .<br /><br /> Wartością domyślną jest `false`. |
| `OpenInWebBrowser` | Atrybut opcjonalny.<br /><br /> Wartość logiczna określająca, czy element powinien zostać otwarty w przeglądarce sieci Web podczas tworzenia projektu na podstawie szablonu.<br /><br /> W przeglądarce sieci Web można otwierać tylko pliki HTML i pliki tekstowe lokalne projektu. Przy tym atrybucie nie można otworzyć zewnętrznych adresów URL.<br /><br /> Wartością domyślną jest `false`. |
| `OpenInHelpBrowser` | Atrybut opcjonalny.<br /><br /> Wartość logiczna określająca, czy element powinien zostać otwarty w przeglądarce Pomocy podczas tworzenia projektu na podstawie szablonu.<br /><br /> W przeglądarce Pomocy można otwierać tylko pliki HTML i pliki tekstowe lokalne projektu. Przy tym atrybucie nie można otworzyć zewnętrznych adresów URL.<br /><br /> Wartością domyślną jest `false`. |
| `OpenOrder` | Atrybut opcjonalny.<br /><br /> Określa wartość liczbową reprezentującą kolejność, wą otworzyć elementy w odpowiednich edytorach. Wszystkie wartości muszą być wielokrotności 10. Elementy o `OpenOrder` wyższych wartościach są otwierane jako pierwsze. |

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Projekt](../extensibility/project-element-visual-studio-templates.md)|Określa pliki lub katalogi, które mają być dodane do projektu.|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 A `string` reprezentujący nazwę lub ścieżkę do pliku w pliku *zip* szablonu.

## <a name="remarks"></a>Uwagi
 `ProjectItem`jest opcjonalnym `Project`dzieckiem .

 Atrybut `TargetFileName` może służyć do tworzenia struktury katalogów różni się od struktury katalogów w pliku *zip* szablonu. Na przykład, jeśli plik *MyFile.vb* istnieje w katalogu głównym pliku *.zip* szablonu, ale chcesz, aby plik został umieszczony w katalogu o nazwie *CustomFiles* we wszystkich projektach utworzonych na podstawie szablonu, należy użyć następującego pliku XML:

```xml
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>
```

 Atrybut `TargetFileName` może również służyć do zmiany nazwy plików, które zawierają znaki międzynarodowe w ich nazwy plików. Na przykład plik *.zip* szablonu nie może zawierać nazw plików ze znakami Unicode, więc plik musi zostać zmieniony, zanim będzie można go skompresować do pliku *zip.* Atrybut `TargetFileName` może służyć do ustawiania nazwy pliku z powrotem do oryginalnej nazwy pliku Unicode.

 Atrybut `TargetFileName` może również służyć do zmiany nazwy plików z parametrami. Poniższa procedura wyjaśnia, jak zmienić nazwę pliku *MyFile.vb*, który istnieje w katalogu głównym szablonu *.zip* pliku, do nazwy pliku na podstawie nazwy projektu.

### <a name="to-rename-files-with-parameters"></a>Aby zmienić nazwę plików z parametrami

1. Użyj następującego pliku XML w pliku *vstemplate:*

   ```xml
   <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>
   ```

2. Otwórz plik projektu (*.vbproj* dla [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projektu) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]w edytorze tekstu lub .

3. Znajdź wiersz w pliku projektu, który wygląda podobnie do następującego kodu XML:

   ```xml
   <Compile Include="MyFile.vb">
   ```

4. Zastąp wiersz kodu następującym kodem XML:

   ```xml
   <Compile Include="$safeprojectname$.vb">
   ```

    Po utworzeniu projektu na podstawie tego szablonu nazwa pliku będzie oparta na nazwie wprowadzonej przez użytkownika w oknie dialogowym **Nowy projekt,** a wszystkie niebezpieczne znaki i spacje zostaną usunięte. Aby uzyskać więcej informacji, zobacz [Parametry szablonu](../ide/template-parameters.md).

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono metadane dla szablonu projektu dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikacji.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem ReplaceParameters="true">Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [Element ProjectItem (szablony elementów programu Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
