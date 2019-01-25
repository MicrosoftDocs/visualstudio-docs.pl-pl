---
title: Manifesty aplikacji dla rozwiązań pakietu Office
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c9c15d7435fa6f5267e413e3afd0fd6e4c7ea17c
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873707"
---
# <a name="application-manifests-for-office-solutions"></a>Manifesty aplikacji dla rozwiązań pakietu Office
  Manifest aplikacji jest plikiem XML, który opisuje zestawów, które są ładowane do rozwiązania Microsoft Office. Użyj narzędzia Microsoft Office development w programie Visual Studio [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] schematu manifestu aplikacji zdefiniowane w [manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md) odwołania.

 Manifesty aplikacji dla rozwiązań pakietu Office należy użyć następującego [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] elementów i atrybutów.

|Element|Opis|Atrybuty|
|-------------|-----------------|----------------|
|[&#60;assembly&#62; Element &#40;ClickOnce Application&#41;](../deployment/assembly-element-clickonce-deployment.md)|Wymagana. Element najwyższego poziomu.|**ManifestVersion**|
|[&#60;assemblyIdentity&#62; Element &#40;ClickOnce Application&#41;](../deployment/assemblyidentity-element-clickonce-deployment.md)|Wymagana. Identyfikuje [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] podstawowego zestawu aplikacji.|**Nazwa**<br /><br /> **version**<br /><br /> **publicKeyToken**<br /><br /> **processorArchitecture**<br /><br /> **Język**|
|[&#60;trustInfo&#62; Element &#40;ClickOnce Application&#41;](../deployment/trustinfo-element-clickonce-application.md)|Określa wymagania dotyczące zabezpieczeń aplikacji.|Brak|
|[&#60;entryPoint&#62; Element &#40;ClickOnce Application&#41;](../deployment/entrypoint-element-clickonce-application.md)|Wymagana. Określa punkt wejścia aplikacji kodu do wykonania.|**Nazwa**<br /><br /> **dependencyName**<br /><br /> **customHostSpecified**|
|[&#60;dependency&#62; Element &#40;ClickOnce Application&#41;](../deployment/dependency-element-clickonce-deployment.md)|Wymagana. Identyfikuje poszczególne zależności wymagane do uruchomienia aplikacji. Opcjonalnie określa zestawy, które muszą być wstępnie zainstalowane.|Brak|
|[&#60;file&#62; Element &#40;ClickOnce Application&#41;](../deployment/file-element-clickonce-application.md)|Wymagana. Identyfikuje każdy pliku inny niż zestawu, który jest używany przez aplikację. Może zawierać dane izolacji Component Object Model (COM) skojarzone z plikiem.|**Nazwa**<br /><br /> **Rozmiar**|

 Manifesty aplikacji dla rozwiązań pakietu Office ma następujący element w `co.v1` przestrzeni nazw.

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

 Te manifesty aplikacji ma również następujące elementy i atrybuty w `vstav3` przestrzeni nazw.

```xml
<addIn>
  <entryPointsCollection>
    <entryPoints>
      <entryPoint>
      </entryPoint>
    </entryPoints>
  </entryPointsCollection>
  <update></update>
  <postActions>
    <postAction>
      <postActionData>
      </postActionData>
    <postAction>
  </postActions>
  <application>
    <customizations>
      <customization>
      </customization>
    </customizations>
  </application
</addIn>
```

|Element|Opis|Atrybuty|
|-------------|-----------------|----------------|
|[&#60;customHostSpecified&#62; Element &#40;Office Development in Visual Studio&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|Wymagana. Oznaczenie manifestu specjalnie jako rozwiązania do pakietu Office.|Brak|
|[&#60;Dodatek&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|Wymagana. Przechowuje punkty wejścia w jednej przestrzeni nazw.|Brak|
|[&#60;entryPointsCollection&#62; Element &#40;Office Development in Visual Studio&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|Wymagana. Grupuje wszystkie zestawy dla jednego lub więcej rozwiązań pakietu Office.|**id**|
|[&#60;entryPoints&#62; Element &#40;Office Development in Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|Wymagana. Grupuje wszystkie zestawy, do uruchamiania rozwiązań pakietu Office.|Brak|
|[&#60;entryPoint&#62; Element &#40;Office Development in Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|Wymagana. Określa zestaw, do uruchamiania w rozwiązaniach pakietu Office.|**class**<br /><br /> **kontrakt**|
|[&#60;update&#62; Element &#40;Office Development in Visual Studio&#41;](../vsto/update-element-office-development-in-visual-studio.md)|Wymagana. Konfiguruje aktualizacje dla rozwiązania.|**Włączone**<br /><br /> **expiration**|
|[&#60;postactions —&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|Opcjonalna. Grupuje wszystkie po wdrożeniu akcje, które uruchamiane po zainstalowaniu rozwiązania dla pakietu Office.|Brak|
|[&#60;postAction&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|Opcjonalna. Umożliwia określenie akcji powdrożeniowej.|Brak|
|[&#60;postActionData&#62; Element &#40;Office Development in Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|Opcjonalna. Dane konfiguracji dla akcji powdrożeniowej.|Brak|
|[&#60;Aplikacja&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md)|Wymagana. Opakowuje informacje specyficzne dla aplikacji w jednym węźle.|Brak|
|[&#60;dostosowania&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|Wymagana. Przechowuje wszystkie informacje specyficzne dla hosta aplikacji w oddzielnych przestrzeni nazw.|Brak|
|[&#60;Dostosowywanie&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|Wymagana. Przechowuje informacje specyficzne dla hosta aplikacji w oddzielnych przestrzeni nazw.|**xmlns**|
|[&#60;dokument&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md)|Wymagane tylko w przypadku rozwiązań na poziomie dokumentu. Przechowuje informacje dotyczące dostosowywania.|**solutionId**|
|[&#60;appAddin&#62; Element &#40;Office Development in Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|Wymagane tylko w przypadku rozwiązań na poziomie aplikacji. Przechowuje informacje dotyczące dostosowywania.|**Aplikacja**<br /><br /> **LoadBehavior**<br /><br /> **keyName**|
|[&#60;friendlyName&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|Opcjonalna. Przechowuje nazwę dodatku narzędzi VSTO dla programów, który pojawia się na liście zainstalowanych dodatków narzędzi VSTO dla programów.|Brak|
|[&#60;Opis&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md)|Wymagane tylko dla dodatków narzędzi VSTO. Przechowuje opis, który pojawia się na liście zainstalowanych programów.|Brak|
|[&#60;formRegions&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|Wymagane tylko dla dodatków narzędzi VSTO dla programu Outlook, obejmujących regionów formularza.|Brak|
|[&#60;formRegion&#62; Element &#40;Office Development in Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|Wymagane tylko dla dodatków narzędzi VSTO dla programu Outlook, obejmujących regionów formularza.|**Nazwa**|
|[&#60;vstoruntime —&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|Wymagana. W tym artykule opisano określonej wersji programu Visual Studio Tools for Office runtime, która jest obsługiwana przez rozwiązania dla pakietu Office.|**Wydania**<br /><br /> **version**<br /><br /> **supportUrl**|

## <a name="remarks"></a>Uwagi
 Możesz ręcznie edytować aplikację i manifesty wdrożenia w rozwiązaniach pakietu Office. Później, musisz ją ponownie podpisać aplikację i manifesty wdrożenia za pomocą narzędzia do edytowania i Manifest Generation (*mage.exe* i *mageui.exe*). Aby uzyskać więcej informacji, zobacz [jak: Ponowne podpisywanie manifestów aplikacji i wdrożenia](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="file-location"></a>Lokalizacja pliku
 Manifest aplikacji jest specyficzny dla jednej wersji rozwiązania. Z tego powodu manifestów aplikacji powinny być przechowywane oddzielnie od manifesty wdrożenia. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] umieszcza pliki specyficzny dla wersji w podkatalogu nazwanym tak skojarzoną wersję w *pliki aplikacji* podkatalogu w folderze Publikuj.

## <a name="file-name-syntax"></a>Składnia nazwy pliku
 Nazwa pliku manifestu aplikacji powinna być pełną nazwę i rozszerzenie aplikacji, jak wskazano w **assemblyIdentity** elementu, a następnie rozszerzenia *.manifest*. Na przykład manifest aplikacji, która odwołuje się do *OutlookAddIn1.dll* dostosowywania czy należy użyć następującej składni nazwy pliku.

 `OutlookAddIn1.dll.manifest`

## <a name="see-also"></a>Zobacz także

- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)