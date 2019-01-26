---
title: '&lt;zestaw&gt; — Element (wdrażanie ClickOnce) | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e6192c7705555e817ed82d452d703f0affd9609
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932704"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;zestaw&gt; — element (wdrażanie ClickOnce)
Element najwyższego poziomu do manifestu wdrażania.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Atrybuty i elementy  
 `assembly` Element jest elementem głównym i jest wymagana. Pierwszy element zawarte musi być `assemblyIdentity` elementu. Elementy manifestu musi znajdować się w następujących przestrzeni nazw: `urn:schemas-microsoft-com:asm.v1`, `urn:schemas-microsoft-com:asm.v2`, i `http://www.w3.org/2000/09/xmldsig#`. Elementy podrzędne zestawu również musi być w tych obszarach nazw poprzez dziedziczenie lub oznaczając.  
  
 `assembly` Element ma atrybut.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`manifestVersion`|Wymagana. Ten atrybut musi być równa `1.0`.|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu pokazano `assembly` elementu w manifeście wdrożenia dla aplikacji wdrożonych za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Ten przykład kodu jest częścią większego przykładu przewidzianego dla [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md) tematu.  
  
```xml  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
  manifestVersion="1.0"  
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [\<zestaw > element](../deployment/assembly-element-clickonce-application.md)