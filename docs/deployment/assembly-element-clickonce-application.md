---
title: '&lt;zestaw&gt; — Element (aplikacja ClickOnce) | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b629243920021adc3833f43f268f05638029dc7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56640405"
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;zestaw&gt; — Element (aplikacja ClickOnce)
Element najwyższego poziomu w manifeście aplikacji.

## <a name="syntax"></a>Składnia

```xml

      <assembly
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>Atrybuty i elementy
 `assembly` Element jest elementem głównym i jest wymagana. Pierwszy element zawarte musi być `assemblyIdentity` elementu. Elementy manifestu musi należeć do jednej z następujących przestrzeni nazw:

 `urn:schemas-microsoft-com:asm.v1`

 `urn:schemas-microsoft-com:asm.v2`

 `http://www.w3.org/2000/09/xmldsig#`

 Elementy podrzędne zestawu również musi być w tych obszarach nazw poprzez dziedziczenie lub oznaczając.

 `assembly` Element ma atrybut.

|Atrybut|Opis|
|---------------|-----------------|
|`manifestVersion`|Wymagana. `manifestVersion` Atrybutu musi być równa `1.0`.|

## <a name="example"></a>Przykład
 W poniższym przykładzie kodu pokazano `assembly` elementu w manifeście aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. Ten przykład kodu jest częścią większego przykładu przewidzianego w [manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md).

```xml
<asmv1:assembly
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">
```

## <a name="see-also"></a>Zobacz także
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<zestaw > element](../deployment/assembly-element-clickonce-deployment.md)
