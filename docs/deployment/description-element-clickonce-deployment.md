---
title: '&lt;Description — &gt; element (wdrożenie ClickOnce) | Microsoft Docs'
description: Element Description identyfikuje informacje o aplikacji używane do tworzenia obecności powłoki i apletu Dodaj lub usuń programy w panelu sterowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4eb1de8f5692eedc9673f1a22cb448ac8d102ae5
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382835"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;Description — &gt; element (wdrażanie ClickOnce)
Identyfikuje informacje o aplikacji używane do tworzenia obecności powłoki i apletu **Dodaj lub usuń programy** w panelu sterowania.

## <a name="syntax"></a>Składnia

```xml

      <description 
   publisher 
   product
   suiteName
   supportUrl
/>
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `description`Element jest wymagany i znajduje się w `urn:schemas-microsoft-com:asm.v1` przestrzeni nazw. Nie zawiera żadnych elementów podrzędnych i ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`publisher`|Wymagane. Identyfikuje nazwę firmy używaną do umieszczania ikon w menu **Start** systemu Windows i apletu **Dodaj lub usuń programy** w panelu sterowania, jeśli wdrożenie jest skonfigurowane do instalacji.|
|`product`|Wymagane. Identyfikuje pełną nazwę produktu. Używany jako tytuł ikony zainstalowanej w menu **Start** systemu Windows.|
|`suiteName`|Opcjonalny. Identyfikuje podfolder w `publisher` folderze w menu **Start** systemu Windows.|
|`supportUrl`|Opcjonalny. Określa adres URL pomocy technicznej, który jest wyświetlany w aplecie **Dodaj lub usuń programy** w panelu sterowania. Skrót do tego adresu URL jest również tworzony na potrzeby obsługi aplikacji w menu **Start** systemu Windows, jeśli wdrożenie jest skonfigurowane do instalacji.|

## <a name="remarks"></a>Uwagi
 Element Description jest wymagany we wszystkich konfiguracjach wdrożenia.

## <a name="example"></a>Przykład
 Poniższy przykład kodu ilustruje `description` element w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeście wdrożenia. Ten przykład kodu jest częścią większego przykładu dostarczonego w temacie [manifestu wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md) .

```xml
<description
  asmv2:publisher="My Company Name"
  asmv2:product="My Application"
  xmlns="urn:schemas-microsoft-com:asm.v1" />
```

## <a name="see-also"></a>Zobacz też
- [Manifest wdrożenia ClickOnce](../deployment/clickonce-deployment-manifest.md)