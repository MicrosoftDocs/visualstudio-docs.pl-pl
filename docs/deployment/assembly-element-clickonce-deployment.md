---
title: '&lt;Assembly — &gt; element (wdrożenie ClickOnce) | Microsoft Docs'
description: Element Assembly jest elementem głównym i jest wymagany w przypadku wdrażania ClickOnce. Jego pierwszy element zawarty musi być elementem assemblyIdentity.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: dde3bdb5fc0e9c6ea256aaa4368623a8e8af18d6
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383238"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;Assembly — &gt; element (wdrażanie ClickOnce)
Element najwyższego poziomu dla manifestu wdrożenia.

## <a name="syntax"></a>Składnia

```xml

      <assembly  
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `assembly`Element jest elementem głównym i jest wymagany. Jego pierwszy element zawarty musi być `assemblyIdentity` elementem. Elementy manifestu muszą znajdować się w następujących obszarach nazw: `urn:schemas-microsoft-com:asm.v1` , `urn:schemas-microsoft-com:asm.v2` , i `http://www.w3.org/2000/09/xmldsig#` . Elementy podrzędne zestawu muszą również znajdować się w tych obszarach nazw, dziedziczenie lub znakowanie.

 `assembly`Element ma następujący atrybut.

|Atrybut|Opis|
|---------------|-----------------|
|`manifestVersion`|Wymagane. Ten atrybut musi być ustawiony na `1.0` .|

## <a name="example"></a>Przykład
 Poniższy przykład kodu ilustruje `assembly` element w manifeście wdrożenia dla aplikacji wdrożonej przy użyciu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Ten przykład kodu jest częścią większego przykładu dostarczonego w temacie [manifestu wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md) .

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

## <a name="see-also"></a>Zobacz też
- [Manifest wdrożenia ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [\<assembly> postaci](../deployment/assembly-element-clickonce-application.md)