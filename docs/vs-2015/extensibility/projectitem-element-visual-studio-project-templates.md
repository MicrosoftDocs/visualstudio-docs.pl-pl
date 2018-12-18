---
title: Projectitem — Element (szablony projektu Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bca26cba66169758aa882535c07846cfa451d172
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737069"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>ProjectItem — Element (Szablony projektu Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa plik, który znajduje się w szablonie projektu.  
  
> [!NOTE]
>  `ProjectItem` Akceptuje różnych atrybutów w zależności od tego, czy szablon projektu lub elementu. W tym temacie opisano `ProjectItem` element dla szablonów projektu. Aby uzyskać informacje o `ProjectItem` element dla szablonów elementów, zobacz [ProjectItem, Element (element szablony programu Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md).  
  
 \<VSTemplate>  
 \<TemplateContent >  
 \<Project>  
 \<ProjectItem >  
  
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
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`TargetFileName`|Atrybut opcjonalny.<br /><br /> Określa nazwę i ścieżkę elementu projektu, gdy projekt jest tworzony na podstawie tego szablonu. Ten atrybut jest przydatna do tworzenia struktury katalogu różni się od struktury katalogów w pliku zip szablonu, lub za pomocą zastąpienia parametrów do utworzenia nazwy elementu.|  
|`ReplaceParameters`|Atrybut opcjonalny.<br /><br /> Wartość logiczna określająca, czy element ma wartości parametrów, które muszą zostać przesłonięte, gdy projekt jest tworzony na podstawie tego szablonu. Wartość domyślna to `false`.|  
|`OpenInEditor`|Atrybut opcjonalny.<br /><br /> Wartość logiczna określająca, czy element powinien zostać otwarty w edytorze odpowiednich w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] po utworzeniu projektu z szablonu.<br /><br /> `OpenInWebBrowser` i `OpenInHelpBrowser` atrybuty są ignorowane na element o `OpenInEditor` wartość `true`.<br /><br /> Wartość domyślna to `false`.|  
|`OpenInWebBrowser`|Atrybut opcjonalny.<br /><br /> Wartość logiczna określająca, czy element powinien zostać otwarty w przeglądarce sieci Web podczas tworzenia projektu z szablonu.<br /><br /> Tylko pliki HTML i pliki tekstowe, które są lokalne w projekcie można otworzyć w przeglądarce sieci Web. Zewnętrzne adresy URL nie można otworzyć za pomocą tego atrybutu.<br /><br /> Wartość domyślna to `false`.|  
|`OpenInHelpBrowser`|Atrybut opcjonalny.<br /><br /> Wartość logiczna określająca, czy element powinien zostać otwarty w Podglądzie pomocy, gdy projekt jest tworzony na podstawie tego szablonu.<br /><br /> Tylko pliki HTML i pliki tekstowe, które są lokalne w projekcie można otworzyć w przeglądarce pomocy. Zewnętrzne adresy URL nie można otworzyć za pomocą tego atrybutu.<br /><br /> Wartość domyślna to `false`.|  
|`OpenOrder`|Atrybut opcjonalny.<br /><br /> Określa wartość liczbowa, która reprezentuje porządek, że elementy będą otwierane w ich odpowiednich edytorów. Wszystkie wartości musi być wielokrotnością liczby 10. Elementy z wyższej `OpenOrder` wartości są najpierw otwarte.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|Określa plików lub katalogów do dodania do projektu.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 A `string` reprezentujący nazwę lub ścieżkę do pliku w pliku zip szablonu.  
  
## <a name="remarks"></a>Uwagi  
 `ProjectItem` jest podrzędnym opcjonalne `Project`.  
  
 `TargetFileName` Atrybut może służyć do tworzenia struktury katalogów różni się od struktury katalogów w pliku zip szablonu. Na przykład jeśli plik `MyFile.vb` istnieje w katalogu głównym pliku zip szablonu, ale plik, który ma być umieszczone w katalogu o nazwie `CustomFiles` we wszystkich projektach tworzone na podstawie szablonu, należy użyć następujący kod XML:  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 `TargetFileName` Atrybut można również zmienić nazwy plików, które zawierają znaki międzynarodowe w nazwach swoich plików. Na przykład plik zip szablonu nie może zawierać nazwy plików ze znakami Unicode, więc należy można zmienić nazwy pliku przed można skompresować do pliku zip. `TargetFileName` Atrybut można ustawić oryginalna nazwa pliku Unicode.  
  
 `TargetFileName` Atrybut można również zmienić nazwy plików z parametrami. Poniższa procedura wyjaśnia, jak zmienić nazwę pliku `MyFile.vb`, który istnieje w katalogu głównym pliku zip szablonu do nazwy pliku, w oparciu o nazwę projektu.  
  
### <a name="to-rename-files-with-parameters"></a>Zmień nazwy plików z parametrami  
  
1.  Użyj następujący kod XML w pliku .vstemplate:  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2.  Otwórz plik projektu (.vbproj dla [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projektu) w edytorze tekstu lub [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
3.  Znajdź wiersz w pliku projektu, który przypomina następujący kod XML:  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4.  Zastąp wiersz kodu następujący kod XML:  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     Gdy projekt jest tworzony za pomocą tego szablonu, nazwa pliku będzie zależeć od nazwy użytkownik wprowadzi w **nowy projekt** okno dialogowe, za pomocą wszystkich niebezpiecznych znaków i usunięte spacje. Aby uzyskać więcej informacji, zobacz [parametry szablonu](../ide/template-parameters.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano metadanych szablon projektu służący do [!INCLUDE[csprcs](../includes/csprcs-md.md)] aplikacji.  
  
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
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Parametry szablonu](../ide/template-parameters.md)   
 [ProjectItem, element (szablony elementów Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)

