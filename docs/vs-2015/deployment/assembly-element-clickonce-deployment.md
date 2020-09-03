---
title: '&lt;Assembly — &gt; element (wdrożenie ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3b77cfacf3dca2c2cc20d674f79929e9958a16d4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155737"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;Assembly — &gt; element (wdrażanie ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Element najwyższego poziomu dla manifestu wdrożenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `assembly`Element jest elementem głównym i jest wymagany. Jego pierwszy element zawarty musi być `assemblyIdentity` elementem. Elementy manifestu muszą znajdować się w następujących obszarach nazw: `urn:schemas-microsoft-com:asm.v1` , `urn:schemas-microsoft-com:asm.v2` , i `http://www.w3.org/2000/09/xmldsig#` . Elementy podrzędne zestawu muszą również znajdować się w tych obszarach nazw, dziedziczenie lub znakowanie.  
  
 `assembly`Element ma następujący atrybut.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`manifestVersion`|Wymagany. Ten atrybut musi być ustawiony na `1.0` .|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu ilustruje `assembly` element w manifeście wdrożenia dla aplikacji wdrożonej przy użyciu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Ten przykład kodu jest częścią większego przykładu dostarczonego w temacie [manifestu wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md) .  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Manifest wdrożenia ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [\<assembly> Postaci](../deployment/assembly-element-clickonce-application.md)
