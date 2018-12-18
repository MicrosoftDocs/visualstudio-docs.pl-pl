---
title: '&lt;appAddin&gt; — element (Office development w programie Visual Studio)'
titleSuffix: ''
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <appAddin> element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3160f153bb6775cf5b2541abf4f75069c818f82b
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248075"
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appAddin&gt; — element (Office development w programie Visual Studio)
  **AppAddin** elementu `vstov4` przestrzeni nazw są przechowywane informacje dotyczące dostosowywania dotyczące dodatków narzędzi VSTO.  
  
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
  
## <a name="elements-and-attributes"></a>Atrybuty i elementy  
 **AppAddin** element jest wymagany i znajduje się w `vstov4` przestrzeni nazw. Jest tylko jedna **appAddin** elementu zdefiniowanego w manifeście aplikacji.  
  
 **AppAddin** element ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**Aplikacja**|Wymagana. Identyfikuje aplikację Microsoft Office. Wartość może być jedną z następujących czynności: Programu Excel, InfoPath, Outlook, PowerPoint, projektu, programu Visio lub programu Word.|  
|**LoadBehavior**|Opcjonalna. Domyślnie **loadBehavior** został włączony przez ustawienie tej wartości. Do debugowania, dodatku narzędzi VSTO można wyłączyć, ustawiając wartość do dwóch. Aby uzyskać więcej informacji, zobacz tabelę o nazwie wartości Loadbehaviour w [wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|  
|**keyName**|Wymagana. Ta wartość jest nazwa klucza rejestru, który będzie używany przez aplikację można załadować dodatku narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|  
  
 **AppAddin** element ma następujących elementów podrzędnych.  
  
### <a name="friendlyname"></a>FriendlyName  
 Opcjonalna. **FriendlyName** element została wyjaśniona w [ &#60;friendlyName&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md).  
  
### <a name="description"></a>opis  
 Opcjonalna. **Opis** element została wyjaśniona w [ &#60;opis&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md).  
  
### <a name="formregions"></a>formRegions  
 Wymagane tylko dla dodatków narzędzi VSTO dla programu Outlook, obejmujących regionów formularza. **FormRegions** element została wyjaśniona w [ &#60;formRegions&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md).  
  
## <a name="vsto-add-in-example"></a>Przykładu dodatku narzędzi VSTO  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie kodu pokazano **appAddin** elementów w rozwiązaniu programu Outlook wdrażane za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykład kodu jest częścią większego przykładu przewidzianego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
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
  
## <a name="see-also"></a>Zobacz także  
 [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  