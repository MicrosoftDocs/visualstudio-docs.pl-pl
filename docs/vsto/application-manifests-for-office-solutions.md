---
title: Manifesty aplikacji dla rozwiązań pakietu Office
ms.date: 02/02/2017
ms.topic: reference
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
ms.openlocfilehash: a6272f145ee2c7ef2a91cc635112e440e6404457
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85531511"
---
# <a name="application-manifests-for-office-solutions"></a>Manifesty aplikacji dla rozwiązań pakietu Office
  Manifest aplikacji jest plikiem XML, który opisuje zestawy, które są ładowane do Microsoft Office rozwiązanie. Narzędzia programistyczne Microsoft Office w programie Visual Studio używają [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] schematu manifestu aplikacji zdefiniowanego w Kompendium [manifestu aplikacji ClickOnce](../deployment/clickonce-application-manifest.md) .

 Manifesty aplikacji dla rozwiązań pakietu Office używają następujących [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] elementów i atrybutów.

|Element|Opis|Atrybuty|
|-------------|-----------------|----------------|
|[&#60;zestawu&#62; elementu &#40;aplikacji ClickOnce&#41;](../deployment/assembly-element-clickonce-deployment.md)|Wymagany. Element najwyższego poziomu.|**manifestVersion**|
|[&#60;element&#62; assemblyIdentity &#40;aplikacji ClickOnce&#41;](../deployment/assemblyidentity-element-clickonce-deployment.md)|Wymagany. Identyfikuje [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] podstawowy zestaw aplikacji.|**Nazwij**<br /><br /> **Wersja**<br /><br /> **publicKeyToken**<br /><br /> **processorArchitecture**<br /><br /> **językowe**|
|[&#60;element&#62; trustInfo &#40;aplikacji ClickOnce&#41;](../deployment/trustinfo-element-clickonce-application.md)|Identyfikuje wymagania dotyczące zabezpieczeń aplikacji.|Brak|
|[&#60;element&#62; entryPoint &#40;aplikacji ClickOnce&#41;](../deployment/entrypoint-element-clickonce-application.md)|Wymagany. Identyfikuje punkt wejścia kodu aplikacji do wykonania.|**Nazwij**<br /><br /> **element dependencyname**<br /><br /> **customHostSpecified**|
|[&#60;zależność&#62; elementu &#40;aplikacji ClickOnce&#41;](../deployment/dependency-element-clickonce-deployment.md)|Wymagany. Identyfikuje każdą zależność wymaganą do uruchomienia aplikacji. Opcjonalnie identyfikuje zestawy, które muszą być preinstalowane.|Brak|
|[&#60;&#62; pliku &#40;aplikacji ClickOnce&#41;](../deployment/file-element-clickonce-application.md)|Wymagany. Identyfikuje każdy plik niebędący zestawem, który jest używany przez aplikację. Może zawierać dane izolacji Component Object Model (COM) skojarzone z plikiem.|**Nazwij**<br /><br /> **zmienia**|

 Manifesty aplikacji dla rozwiązań pakietu Office mają następujący element w `co.v1` przestrzeni nazw.

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

 Te manifesty aplikacji mają również następujące elementy i atrybuty w `vstav3` przestrzeni nazw.

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
|[&#60;customHostSpecified&#62; elementu &#40;Programowanie Office w Visual Studio&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|Wymagany. Oznacza manifest w odniesieniu do rozwiązania pakietu Office.|Brak|
|[&#60;addin&#62; element &#40;Programowanie Office w Visual Studio&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|Wymagany. Przechowuje punkty wejścia w pojedynczej przestrzeni nazw.|Brak|
|[&#60;entryPointsCollection&#62; elementu &#40;Programowanie Office w Visual Studio&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|Wymagany. Grupuje wszystkie zestawy dla jednego lub kilku rozwiązań pakietu Office.|**#c1**|
|[&#60;punkt wejścia&#62; elementu &#40;Programowanie Office w Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|Wymagany. Grupuje wszystkie zestawy do uruchamiania rozwiązania pakietu Office.|Brak|
|[&#60;element&#62; entryPoint &#40;Programowanie Office w Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|Wymagany. Identyfikuje zestaw do uruchomienia w rozwiązaniu pakietu Office.|**określonej**<br /><br /> **przedsiębiorc**|
|[&#60;Update&#62; element &#40;Office Development w programie Visual Studio&#41;](../vsto/update-element-office-development-in-visual-studio.md)|Wymagany. Konfiguruje aktualizacje dla rozwiązania.|**dostępny**<br /><br /> **datę**|
|[&#60;postActions&#62; elementu &#40;Programowanie Office w Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|Opcjonalny. Grupuje wszystkie akcje po wdrożeniu, które są uruchamiane po zainstalowaniu rozwiązań pakietu Office.|Brak|
|[&#60;postAction&#62; elementu &#40;Programowanie Office w Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|Opcjonalny. Identyfikuje akcję po wdrożeniu.|Brak|
|[&#60;postActionData&#62; elementu &#40;Programowanie Office w Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|Opcjonalny. Konfiguruje dane dla akcji wykonywanej po wdrożeniu.|Brak|
|[&#60;aplikacji&#62; elementu &#40;Programowanie Office w Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md)|Wymagany. Zawija informacje specyficzne dla aplikacji w jednym węźle.|Brak|
|[&#60;dostosowań&#62; elementu &#40;Programowanie Office w Visual Studio&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|Wymagany. Przechowuje wszystkie informacje specyficzne dla hosta aplikacji w oddzielnym obszarze nazw.|Brak|
|[&#60;dostosowanie&#62; elementu &#40;Programowanie Office w Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|Wymagany. Przechowuje informacje specyficzne dla hosta aplikacji w oddzielnym obszarze nazw.|**'xmlns**|
|[&#60;dokument&#62; elementu &#40;Programowanie Office w Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md)|Wymagane tylko w przypadku rozwiązań na poziomie dokumentu. Przechowuje informacje specyficzne dla dostosowywania.|**solutionId**|
|[&#60;appAddin&#62; elementu &#40;Programowanie Office w Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|Wymagane tylko w przypadku rozwiązań na poziomie aplikacji. Przechowuje informacje specyficzne dla dostosowywania.|**aplikacja**<br /><br /> **loadBehavior**<br /><br /> **keyName**|
|[&#60;FriendlyName&#62; element &#40;Programowanie Office w Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|Opcjonalny. Przechowuje nazwę dodatku VSTO, który pojawia się na liście zainstalowanych dodatków narzędzi VSTO.|Brak|
|[&#60;opis&#62; elementu &#40;Programowanie Office w Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md)|Wymagane tylko w przypadku dodatków VSTO. przechowuje opis wyświetlany na liście zainstalowanych programów.|Brak|
|[&#60;formRegions&#62; elementu &#40;Programowanie Office w Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|Wymagane tylko w przypadku dodatków VSTO programu Outlook, które obejmują regiony formularzy.|Brak|
|[&#60;formRegion&#62; elementu &#40;Programowanie Office w Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|Wymagane tylko w przypadku dodatków VSTO programu Outlook, które obejmują regiony formularzy.|**Nazwa**|
|[&#60;vstoRuntime&#62; elementu &#40;Programowanie Office w Visual Studio&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|Wymagany. Opisuje określoną wersję Visual Studio Tools pakietu Office dla środowiska uruchomieniowego, która jest obsługiwana przez rozwiązanie pakietu Office.|**Usuwanie**<br /><br /> **Wersja**<br /><br /> **supportUrl (adres URL pomocy technicznej)**|

## <a name="remarks"></a>Uwagi
 Możesz ręcznie edytować manifesty aplikacji i wdrożenia w rozwiązaniach pakietu Office. Następnie należy ponowne podpisać aplikacje i manifesty wdrożenia przy użyciu Narzędzie tworzenia i edycji manifestów (*mage.exe* i *mageui.exe*). Aby uzyskać więcej informacji, zobacz [jak: ponowne podpisywanie aplikacji i manifestów wdrożenia](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="file-location"></a>Lokalizacja pliku
 Manifest aplikacji jest specyficzny dla pojedynczej wersji rozwiązania. Z tego powodu manifesty aplikacji powinny być przechowywane oddzielnie od manifestów wdrożenia. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]umieszcza pliki specyficzne dla wersji w podkatalogu o nazwie po skojarzonej wersji w podkatalogu *pliki aplikacji* w folderze publikowanie.

## <a name="file-name-syntax"></a>Składnia nazwy pliku
 Nazwa pliku manifestu aplikacji powinna być pełną nazwą i rozszerzeniem aplikacji, jak określono w elemencie **assemblyIdentity** , po którym następuje rozszerzenie *. manifest*. Na przykład manifest aplikacji, który odwołuje się do dostosowania *OutlookAddIn1.dll* , użyje następującej składni nazw plików.

 `OutlookAddIn1.dll.manifest`

## <a name="see-also"></a>Zobacz też

- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)