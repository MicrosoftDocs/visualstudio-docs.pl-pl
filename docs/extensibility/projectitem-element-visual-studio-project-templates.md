---
title: ProjectItem, element (szablony projektów Visual Studio) | Microsoft Docs
description: Dowiedz się więcej na temat elementu ProjectItem dla szablonów projektu i sposobu, w jaki akceptuje różne atrybuty, w zależności od tego, czy szablon dotyczy projektu czy elementu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
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
ms.openlocfilehash: bf2d41fe83b440e2a3b4bfebd4fac6f5d06094a4
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671327"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>ProjectItem, element (szablony projektów Visual Studio)
Określa plik, który jest dołączony do szablonu projektu.

> [!NOTE]
> `ProjectItem`Element akceptuje różne atrybuty w zależności od tego, czy szablon dotyczy projektu lub elementu. W tym temacie objaśniono `ProjectItem` element szablonów projektu. Aby uzyskać wyjaśnienie `ProjectItem` elementu szablonów elementów, zobacz [ProjectItem element (szablony elementów Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md).

 \<VSTemplate> \<TemplateContent>
 \<Project>
 \<ProjectItem>

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
| `TargetFileName` | Atrybut opcjonalny.<br /><br /> Określa nazwę i ścieżkę elementu projektu, gdy projekt jest tworzony na podstawie szablonu. Ten atrybut jest przydatny do tworzenia struktury katalogów innej niż struktura katalogów w pliku template *. zip* lub do użycia zastąpienia parametrów w celu utworzenia nazwy elementu. |
| `ReplaceParameters` | Atrybut opcjonalny.<br /><br /> Wartość logiczna określająca, czy element zawiera wartości parametrów, które muszą zostać zastąpione, gdy projekt jest tworzony na podstawie szablonu. Wartość domyślna to `false`. |
| `OpenInEditor` | Atrybut opcjonalny.<br /><br /> Wartość logiczna określająca, czy element powinien być otwarty w odpowiednim edytorze w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] momencie tworzenia projektu na podstawie szablonu.<br /><br /> `OpenInWebBrowser`Atrybuty i `OpenInHelpBrowser` są ignorowane dla elementu o `OpenInEditor` wartości `true` .<br /><br /> Wartość domyślna to `false`. |
| `OpenInWebBrowser` | Atrybut opcjonalny.<br /><br /> Wartość logiczna określająca, czy element powinien zostać otwarty w przeglądarce sieci Web po utworzeniu projektu na podstawie szablonu.<br /><br /> W przeglądarce sieci Web można otwierać tylko pliki HTML i pliki tekstowe, które są lokalne dla projektu. Nie można otworzyć zewnętrznych adresów URL z tym atrybutem.<br /><br /> Wartość domyślna to `false`. |
| `OpenInHelpBrowser` | Atrybut opcjonalny.<br /><br /> Wartość logiczna określająca, czy element powinien być otwarty w podglądzie pomocy, gdy projekt jest tworzony na podstawie szablonu.<br /><br /> W przeglądarce pomocy można otwierać tylko pliki HTML i pliki tekstowe, które są lokalne dla projektu. Nie można otworzyć zewnętrznych adresów URL z tym atrybutem.<br /><br /> Wartość domyślna to `false`. |
| `OpenOrder` | Atrybut opcjonalny.<br /><br /> Określa wartość liczbową reprezentującą kolejność, w której elementy będą otwierane w odpowiednich edytorach. Wszystkie wartości muszą być wielokrotnościami 10. Elementy o wyższych `OpenOrder` wartości są otwierane jako pierwsze. |

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Project](../extensibility/project-element-visual-studio-templates.md)|Określa pliki lub katalogi, które mają zostać dodane do projektu.|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 `string`Reprezentuje nazwę lub ścieżkę do pliku w pliku template *. zip* .

## <a name="remarks"></a>Uwagi
 `ProjectItem` jest opcjonalnym elementem podrzędnym `Project` .

 Ten `TargetFileName` atrybut może służyć do tworzenia struktury katalogów innej niż struktura katalogów w pliku template *. zip* . Na przykład jeśli plik *. vb* istnieje w katalogu głównym pliku template *. zip* , ale plik ma być umieszczony w katalogu o nazwie *CustomFiles* we wszystkich projektach utworzonych na podstawie szablonu, użyj następującego kodu XML:

```xml
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>
```

 Ten `TargetFileName` atrybut może być również używany do zmiany nazwy plików, które zawierają znaki międzynarodowe w ich nazwach. Na przykład plik template *. zip* nie może zawierać nazw plików ze znakami Unicode, dlatego należy zmienić nazwę pliku, aby można było go skompresować do pliku *zip* . Ten `TargetFileName` atrybut może służyć do ustawienia nazwy pliku z powrotem na oryginalną nazwę pliku w formacie Unicode.

 Ten `TargetFileName` atrybut może być również używany do zmiany nazwy plików z parametrami. Poniższa procedura wyjaśnia, jak zmienić nazwę pliku *. vb*, który istnieje w katalogu głównym pliku template *. zip* , do nazwy pliku na podstawie nazwy projektu.

### <a name="to-rename-files-with-parameters"></a>Aby zmienić nazwy plików z parametrami

1. Użyj poniższego kodu XML w pliku *. vstemplate* :

   ```xml
   <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>
   ```

2. Otwórz plik projektu (*. vbproj* dla [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projektu) w edytorze tekstu lub [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

3. Znajdź wiersz w pliku projektu, który wygląda podobnie do następującego kodu XML:

   ```xml
   <Compile Include="MyFile.vb">
   ```

4. Zastąp wiersz kodu następującym kodem XML:

   ```xml
   <Compile Include="$safeprojectname$.vb">
   ```

    Gdy projekt jest tworzony na podstawie tego szablonu, nazwa pliku będzie oparta na nazwie wprowadzonej przez użytkownika w oknie dialogowym **Nowy projekt** z usuniętymi wszystkimi niebezpiecznymi znakami i spacjami. Aby uzyskać więcej informacji, zobacz [Parametry szablonu](../ide/template-parameters.md).

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

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [ProjectItem, element (szablony elementów Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
