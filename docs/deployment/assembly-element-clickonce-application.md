---
title: '&lt;Assembly — &gt; element (Aplikacja ClickOnce) | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62900763"
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;Assembly — &gt; element (Aplikacja ClickOnce)
Element najwyższego poziomu dla manifestu aplikacji.

## <a name="syntax"></a>Składnia

```xml

      <assembly
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `assembly`Element jest elementem głównym i jest wymagany. Jego pierwszy element zawarty musi być `assemblyIdentity` elementem. Elementy manifestu muszą znajdować się w jednej z następujących przestrzeni nazw:

 `urn:schemas-microsoft-com:asm.v1`

 `urn:schemas-microsoft-com:asm.v2`

 `http://www.w3.org/2000/09/xmldsig#`

 Elementy podrzędne zestawu muszą również znajdować się w tych obszarach nazw, dziedziczenie lub znakowanie.

 `assembly`Element ma następujący atrybut.

|Atrybut|Opis|
|---------------|-----------------|
|`manifestVersion`|Wymagany. `manifestVersion`Atrybut musi być ustawiony na `1.0` .|

## <a name="example"></a>Przykład
 Poniższy przykład kodu ilustruje `assembly` element w manifeście aplikacji dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. Ten przykład kodu jest częścią większego przykładu dostarczonego w [manifeście aplikacji ClickOnce](../deployment/clickonce-application-manifest.md).

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

## <a name="see-also"></a>Zobacz też
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<assembly> postaci](../deployment/assembly-element-clickonce-deployment.md)
