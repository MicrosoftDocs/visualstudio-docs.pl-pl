---
title: '&lt;appAddin — &gt; element (Programowanie Office w Visual Studio)'
description: Dowiedz się, w jaki sposób element appAddin przestrzeni nazw vstov4 przechowuje informacje dotyczące dostosowywania dla dodatków narzędzi VSTO.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <appAddin> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 427d7bc0ec59b98394b292745985be7fdf69b904
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950513"
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appAddin — &gt; element (Programowanie Office w Visual Studio)
  Element **appAddin** `vstov4` przestrzeni nazw przechowuje informacje specyficzne dla dostosowywania dla dodatków narzędzi VSTO.

## <a name="syntax"></a>Składnia

```xml
<appAddin
  application
  loadBehavior
  keyName>
  <friendlyName>
  <description>
  <formRegions></formRegions>
</appAddin>
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 Element **appAddin** jest wymagany i znajduje się w `vstov4` przestrzeni nazw. W manifeście aplikacji jest zdefiniowany tylko jeden element **appAddin** .

 Element **appAddin** ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|**aplikacja**|Wymagane. Identyfikuje aplikację Microsoft Office. Może to być jedna z następujących wartości: Excel, InfoPath, Outlook, PowerPoint, Project, Visio lub Word.|
|**loadBehavior**|Opcjonalny. Domyślnie **LoadBehavior** jest włączane przez ustawienie tej wartości na. W przypadku debugowania można wyłączyć dodatek VSTO, ustawiając wartość na dwa. Więcej informacji można znaleźć w tabeli zatytułowanej LoadBehavior wartości w [wpisach rejestru dla dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|
|**keyName**|Wymagane. Ta wartość jest nazwą klucza rejestru, która będzie używana przez aplikację do ładowania dodatku VSTO. Aby uzyskać więcej informacji, zobacz [wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|

 Element **appAddin** ma następujące elementy podrzędne.

### <a name="friendlyname"></a>friendlyName
 Opcjonalny. Element **FriendlyName** jest wyjaśniony w [&#60;FriendlyName&#62; elementu &#40;programowanie Office w&#41;programu Visual Studio](../vsto/friendlyname-element-office-development-in-visual-studio.md).

### <a name="description"></a>description (opis)
 Opcjonalny. Element **Description** został wyjaśniony w [ opisie&#60;&#62; elementu &#40;programowanie Office w&#41;Visual Studio](../vsto/description-element-office-development-in-visual-studio.md).

### <a name="formregions"></a>formRegions
 Wymagane tylko w przypadku dodatków VSTO programu Outlook, które obejmują regiony formularzy. Element **FormRegions** jest wyjaśniony w [&#60;formRegions&#62; elementu &#40;programowanie Office w&#41;Visual Studio](../vsto/formregions-element-office-development-in-visual-studio.md).

## <a name="vsto-add-in-example"></a>Przykład dodatku narzędzi VSTO

### <a name="description"></a>Opis
 Poniższy przykład kodu ilustruje elementy **appAddin** w rozwiązaniu programu Outlook wdrożonym przy użyciu [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Ten przykład kodu jest częścią większego przykładu dostępnego w [manifestach aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
<vstov4:appAddIn
  application="Outlook"
  loadBehavior="3"
  keyName="ContosoOutlookAddIn">
  <vstov4:friendlyName>
    ContosoOutlookAddIn
  </vstov4:friendlyName>
  <vstov4:description>
    ContosoOutlookAddIn - Outlook VSTO Add-in
    created with Visual Studio Tools for Office
  </vstov4:description>
  <vstov4:formRegions>
    <vstov4:formRegion
        name="OutlookAddIn1.FormRegion1">
      <vstov4:messageClass name="IPM.Note" />
      <vstov4:messageClass name="IPM.Contact" />
      <vstov4:messageClass name="IPM.Appointment" />
    </vstov4:formRegion>
  </vstov4:formRegions>
</vstov4:appAddIn>
```

## <a name="see-also"></a>Zobacz też

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)