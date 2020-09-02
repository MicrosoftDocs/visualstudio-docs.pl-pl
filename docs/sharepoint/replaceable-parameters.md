---
title: Parametry wymienne | Microsoft Docs
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
ms.openlocfilehash: 165ef1256a0150e0942d85c4f876c8b3f5e15c72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64825316"
---
# <a name="replaceable-parameters"></a>Parametry wymienne
  Parametry wymienne lub *tokeny*mogą być używane wewnątrz plików projektu w celu zapewnienia wartości dla elementów rozwiązania programu SharePoint, których wartości rzeczywiste nie są znane w czasie projektowania. Są one podobne do standardowych [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tokenów szablonów. Aby uzyskać więcej informacji, zobacz [Parametry szablonu](../ide/template-parameters.md).

## <a name="token-format"></a>Format tokenu
 Tokeny zaczynają się i kończą znakiem dolara ($). We wdrożeniu wszystkie użyte tokeny są zastępowane wartościami rzeczywistymi, gdy projekt jest spakowany w pakiecie rozwiązania programu SharePoint (plik*wsp* ). Na przykład token **$SharePoint. Package.Name $** może zostać rozpoznany jako ciąg "test Package programu SharePoint".

## <a name="token-rules"></a>Reguły tokenów
 Do tokenów mają zastosowanie następujące reguły:

- Tokeny można określać w dowolnym miejscu w wierszu.

- Tokeny nie mogą obejmować wielu wierszy.

- Ten sam token może być określony więcej niż raz w tym samym wierszu i w tym samym pliku.

- Różne tokeny mogą być określone w tym samym wierszu.

  Tokeny, które nie są zgodne z tymi regułami, są ignorowane i nie powodują ostrzeżenia ani błędu.

  Zastąpienie tokenów przez wartości ciągu jest wykonywane natychmiast po przekształceniu manifestu. To zastąpienie pozwala użytkownikowi edytować szablony manifestu przy użyciu tokenów.

### <a name="token-name-resolution"></a>Rozpoznawanie nazw tokenów
 W większości przypadków token jest rozpoznawany jako określona wartość, bez względu na to, gdzie jest zawarty. Jeśli jednak token jest powiązany z pakietem lub funkcją, wartość tokenu zależy od miejsca, w którym jest on zawarty. Jeśli na przykład funkcja znajduje się w pakiecie A, token jest `$SharePoint.Package.Name$` rozpoznawany jako wartość "Package a." Jeśli ta sama funkcja znajduje się w pakiecie B, jest `$SharePoint.Package.Name$` rozpoznawana jako "pakiet b".

## <a name="tokens-list"></a>Lista tokenów
 W poniższej tabeli wymieniono dostępne tokeny.

|Nazwa|Opis|
|----------|-----------------|
|$SharePoint. Project. FileName $|Nazwa zawierającego plik projektu, na przykład *NewProj. csproj*.|
|$SharePoint. Project. FileNameWithoutExtension $|Nazwa zawierającego plik projektu bez rozszerzenia nazwy pliku. Na przykład "NewProj".|
|$SharePoint. Project. AssemblyFullName $|Nazwa wyświetlana (silna nazwa) zawierającego zestaw danych wyjściowych projektu.|
|$SharePoint. Project. AssemblyFileName $|Nazwa zestawu wyjściowego projektu zawierającego.|
|$SharePoint. Project. AssemblyFileNameWithoutExtension $|Nazwa wyjściowego zestawu projektu, bez rozszerzenia nazwy pliku.|
|$SharePoint. Project. AssemblyPublicKeyToken $|Token klucza publicznego zawierającego zestaw danych wyjściowych projektu, konwertowany na ciąg. (16 znaków w formacie szesnastkowym "X2").|
|$SharePoint. Package.Name $|Nazwa zawierającego pakiet.|
|$SharePoint. Package. FileName $|Nazwa pliku definicji zawierającego pakiet.|
|$SharePoint. Package. FileNameWithoutExtension $|Nazwa (bez rozszerzenia) pliku definicji zawierającego pakiet.|
|$SharePoint. Package.Id $|Identyfikator programu SharePoint dla zawierającego go pakietu. Jeśli funkcja jest używana w więcej niż jednym pakiecie, ta wartość zostanie zmieniona.|
|$SharePoint. feature. FileName $|Nazwa pliku definicji funkcji zawierającej, takiej jak *Feature1. feature*.|
|$SharePoint. feature. FileNameWithoutExtension $|Nazwa pliku definicji funkcji bez rozszerzenia nazwy pliku.|
|$SharePoint. feature. DeploymentPath $|Nazwa folderu, który zawiera funkcję w pakiecie. Ten token odpowiada właściwości "ścieżka wdrożenia" w Projektancie funkcji. Przykładem jest wartość "Project1_Feature1".|
|$SharePoint. Feature.Id $|Identyfikator programu SharePoint funkcji zawierającej. Ten token, podobnie jak w przypadku wszystkich tokenów poziomu funkcji, może być używany tylko przez pliki zawarte w pakiecie za pośrednictwem funkcji, ale nie został dodany bezpośrednio do pakietu poza funkcją.|
|$SharePoint. ProjectItem.Name $|Nazwa elementu projektu (nie jego nazwa pliku), uzyskana z **ISharePointProjectItem.Name**.|
|$SharePoint. Type. \<GUID> . AssemblyQualifiedName $|Kwalifikowana nazwa zestawu odpowiadająca typowi [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] tokenu. Format [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] jest małymi literami i odpowiada formatowi Guid. ToString ("D") (czyli xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|
|$SharePoint. Type. \<GUID> . FullName $|Pełna nazwa typu odpowiadającego identyfikatorowi GUID w tokenie. Format identyfikatora GUID jest małymi literami i odpowiada formatowi Guid. ToString ("D") (czyli xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|

## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>Dodawanie rozszerzeń do listy rozszerzeń plików zastępujących tokeny
 Chociaż tokeny mogą być teoretycznie używane przez dowolny plik, który należy do elementu projektu programu SharePoint znajdującego się w pakiecie, domyślnie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wyszukuje tokeny tylko w plikach pakietu, plikach manifestu i plikach, które mają następujące rozszerzenia:

- [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]

- ASCX

- ASPX

- Part

- DWP

  Te rozszerzenia są definiowane przez `<TokenReplacementFileExtensions>` element w pliku Microsoft. VisualStudio. SharePoint. targets znajdującym się w folderze... \\<Program Files \> \MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools.

  Można jednak dodać do listy dodatkowe rozszerzenia plików. Dodaj `<TokenReplacementFileExtensions>` element do dowolnej właściwości w pliku projektu programu SharePoint, który jest zdefiniowany przed \<Import> plikiem obiektów docelowych programu SharePoint.

> [!NOTE]
> Ponieważ Zastępowanie tokenu następuje po skompilowaniu projektu, nie należy dodawać rozszerzeń plików dla typów plików, które są kompilowane, takich jak *. cs*, *. vb* lub *. resx*. Tokeny są zastępowane tylko w plikach, które nie są kompilowane.

 Na przykład, aby dodać rozszerzenia nazw plików (*...* *yourextension*) do listy rozszerzeń nazw plików zastępujących tokeny, należy dodać następujący kod do pliku projektu (*. csproj*):

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

 Rozszerzenie można dodać bezpośrednio do pliku TARGETS (*. targets*). Jednak dodanie rozszerzenia powoduje zmianę listy rozszerzeń dla wszystkich projektów programu SharePoint spakowanych w systemie lokalnym, a nie tylko własnych. To rozszerzenie może być wygodne, gdy jesteś jedynym deweloperem w systemie lub jeśli jest to potrzebne w większości projektów. Ponieważ jednak jest to właściwe dla systemu, to podejście nie jest przenośne i dlatego zaleca się dodanie dowolnych rozszerzeń do pliku projektu.

## <a name="see-also"></a>Zobacz też
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
