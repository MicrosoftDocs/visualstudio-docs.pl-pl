---
title: Parametry wymienne | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload: office
ms.openlocfilehash: 792c7faf9ed704dd01226c750e9898965111c414
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871952"
---
# <a name="replaceable-parameters"></a>Parametry wymienne
  Parametry wymienne lub *tokenów*, może służyć w plikach projektu o podanie wartości elementów rozwiązania programu SharePoint, w których rzeczywiste wartości nie są znany w czasie projektowania. Są one podobne w funkcji standardu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tokenów szablonu. Aby uzyskać więcej informacji, zobacz [parametry szablonu](../ide/template-parameters.md).  
  
## <a name="token-format"></a>Format tokenu
 Tokeny rozpoczynać się i kończyć znakiem dolara ($). We wdrożeniu, wszystkie tokeny używane są zastępowane wartości rzeczywiste gdy projekt jest pakowana do pakietu rozwiązania programu SharePoint (*.wsp* pliku). Na przykład token **$SharePoint.Package.Name$** może zostać rozwiązana do ciągu "Pakietu testowego programu SharePoint".  
  
## <a name="token-rules"></a>Reguły tokenu
 Obowiązują następujące reguły do tokenów:  
  
- Tokenów można określić w dowolnym miejscu w wierszu.  
  
- Tokeny nie mogą obejmować wiele wierszy.  
  
- Ten sam token można określić więcej niż jeden raz w tym samym wierszu, a w tym samym pliku.  
  
- Różne tokeny mogą być określone w tym samym wierszu.  
  
  Tokenów, które nie podlegają te reguły są ignorowane i nie powodują ostrzeżenia lub błędu.  
  
  Zastąpienia tokenów według wartości ciągu jest wykonywane natychmiast po przekształceniu manifestu. Ta zastępowania umożliwia użytkownikowi edytowanie manifestu szablonów z tokenami.  
  
### <a name="token-name-resolution"></a>Rozpoznawanie nazw tokenu
 W większości przypadków token jest rozpoznawany jako niezależnie od tego, gdzie znajduje się określoną wartością. Jeśli token jest związany z pakietu lub funkcji, wartość tokenu zależy jednak gdzie znajduje się. Na przykład, jeśli funkcja znajduje się w pakiet, a następnie token `$SharePoint.Package.Name$` jest rozpoznawana jako wartość "Pakiet A." Jeśli jedna funkcja jest w pakiet B, wtedy `$SharePoint.Package.Name$` jest rozpoznawana jako "Pakiet B."  
  
## <a name="tokens-list"></a>Lista tokenów
 W poniższej tabeli wymieniono dostępne tokeny.  
  
|Nazwa|Opis|  
|----------|-----------------|  
|$SharePoint.Project.FileName$|Nazwa zawierającego projektu pliku, takie jak *NewProj.csproj*.|  
|$SharePoint.Project.FileNameWithoutExtension$|Nazwa pliku projektu zawierającego bez rozszerzenia nazwy pliku. Na przykład "NewProj".|  
|$SharePoint.Project.AssemblyFullName$|Nazwa wyświetlana (silnej nazwy) zawierającego projekt wyjściowym zestawu.|  
|$SharePoint.Project.AssemblyFileName$|Nazwa projektu zawierającego wyjściowym zestawu.|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|Nazwa projektu zawierającego wyjściowym zestawu bez rozszerzenia nazwy pliku.|  
|$SharePoint.Project.AssemblyPublicKeyToken$|Token klucza publicznego projektu zawierającego wyjściowym zestawu, konwertowana na ciąg. (16-znaków "x2" formacie szesnastkowym.)|  
|$SharePoint.Package.Name$|Nazwa pakietu.|  
|$SharePoint.Package.FileName$|Nazwa pliku definicji pakietu zawierającego.|  
|$SharePoint.Package.FileNameWithoutExtension$|Nazwa (bez rozszerzenia) pliku definicji pakietu zawierającego.|  
|$SharePoint.Package.Id$|Identyfikator programu SharePoint zawierającego pakiet. Jeśli funkcja jest używana w więcej niż jeden pakiet, ta wartość zostanie zmieniona.|  
|$SharePoint.Feature.FileName$|Nazwa pliku definicji zawierającego funkcji, takich jak *Feature1.feature*.|  
|$SharePoint.Feature.FileNameWithoutExtension$|Nazwa pliku definicji funkcji, bez rozszerzenia nazwy pliku.|  
|$SharePoint.Feature.DeploymentPath$|Nazwa folderu, który zawiera tę funkcję w pakiecie. Token ten jest równa właściwości "Deployment Path" w Projektancie funkcji. Przykładowa wartość to "Project1_Feature1".|  
|$SharePoint.Feature.Id$|Identyfikator programu SharePoint zawierającego funkcji. Ten token, jak za pomocą wszystkich tokenów poziom funkcji, może być użyty tylko przez pliki zawarte w pakiecie za pośrednictwem funkcji nie dodał bezpośrednio do pakietu poza funkcją.|  
|$SharePoint.ProjectItem.Name$|Nazwa elementu projektu (nie jego nazwa pliku), jako uzyskany z **ISharePointProjectItem.Name**.|  
|$SharePoint.Type. \<GUID >. AssemblyQualifiedName$|Nazwy kwalifikowanej zestawu zgodnych typów [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] tokenu. Format [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] jest pisana małymi literami i odnosi się do formatu Guid.ToString("D") (czyli xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|  
|$SharePoint.Type.\<GUID>.FullName$|Pełna nazwa typu dopasowania identyfikatora GUID w tokenie. Format identyfikatora GUID jest pisana małymi literami i odnosi się do formatu Guid.ToString("D") (czyli xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|  
  
## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>Dodawanie rozszerzeń do listy rozszerzeń plików zastępowania tokenu
 Mimo że tokeny, teoretycznie mogą być używane przez dowolny plik, który należy do projektu programu SharePoint, elementu uwzględniony w pakiecie, domyślnie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wyszukuje tokenów tylko w przypadku plików pakietu, pliki manifestu i plików, które mają następujące rozszerzenia:  
  
- [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
- ASCX  
  
- ASPX  
  
- Składnik Web Part  
  
- DWP  
  
  Te rozszerzenia są definiowane przez `<TokenReplacementFileExtensions>` elementu w pliku Microsoft.VisualStudio.SharePoint.targets na terenie... \\< plików programu\>\MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools folderu.  
  
  Można jednak dodać dodatkowe rozszerzenia plików do listy. Dodaj `<TokenReplacementFileExtensions>` elementu do dowolnego PropertyGroup w pliku projektu programu SharePoint, która jest zdefiniowana przed \<Import > pliku obiektów docelowych programu SharePoint.  
  
> [!NOTE]  
>  Ponieważ zastępowania tokenu odbywa się to skompilowany projekt, nie należy dodawać rozszerzenia plików dla typów plików, które są kompilowane, takich jak *.cs*, *.vb* lub *resx*. Tokeny są zastępowane tylko w plikach, które nie są kompilowane.  
  
 Na przykład, aby dodać rozszerzenia nazw plików (*.myextension* i *.yourextension*) do listy rozszerzeń nazw plików zastępowania tokenu, należy dodać następujące polecenie, aby projekt (*csproj* ) pliku:  
  
```xml  
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
.  
.  
.  
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->  
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>  
</PropertyGroup>  
```  
  
 Rozszerzenie można dodać bezpośrednio do elementów docelowych (*.targets*) pliku. Jednak dodanie rozszerzenia zmienia się na liście rozszerzeń dla wszystkich projektów programu SharePoint w pakiecie w systemie lokalnym, nie po prostu własne. To rozszerzenie może być wygodne, gdy jesteś jedynym developer w systemie, czy większość swoje projekty wymagają tego. Jednak jest specyficzne dla systemu, takie podejście nie jest przenośny i dlatego zalecane jest, należy dodać wszystkie rozszerzenia do pliku projektu, zamiast tego.  
  
## <a name="see-also"></a>Zobacz także
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
