---
title: '&lt;assemblyIdentity, &gt; element (wdrażanie ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56525cc0c0c754a7fa3a1f4c2c5b6cf2e941e9b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62929067"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;assemblyIdentity, &gt; element (wdrażanie ClickOnce)
Identyfikuje podstawowy zestaw [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.

## <a name="syntax"></a>Składnia

```xml

      <assemblyIdentity  
   name 
   version
   publicKeyToken
   processorArchitecture
    type
/>
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `assemblyIdentity`Element jest wymagany. Nie zawiera żadnych elementów podrzędnych i ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`name`|Wymagany. Określa czytelną dla człowieka nazwę wdrożenia do celów informacyjnych.<br /><br /> Jeśli `name` zawiera znaki specjalne, takie jak pojedyncze lub podwójne cudzysłowy, uruchomienie aplikacji może się nie powieść.|
|`version`|Wymagany. Określa numer wersji zestawu w następującym formacie: `major.minor.build.revision` .<br /><br /> Ta wartość musi być zwiększana w zaktualizowanym manifeście, aby wyzwolić aktualizację aplikacji.|
|`publicKeyToken`|Wymagany. Określa 16-znakowy ciąg szesnastkowy, który reprezentuje ostatnie 8 bajtów wartości skrótu SHA-1 klucza publicznego, w którym jest podpisany manifest wdrożenia. Klucz publiczny używany do podpisywania musi mieć wartość 2048 bitów lub większą.<br /><br /> Chociaż podpisywanie zestawu jest zalecane, ale opcjonalne, ten atrybut jest wymagany. Jeśli zestaw nie jest podpisany, należy skopiować wartość z zestawu z podpisem własnym lub użyć wartości "fikcyjnej" wszystkich zer.|
|`processorArchitecture`|Wymagany. Określa procesor. Prawidłowe wartości są `msil` dla wszystkich procesorów, `x86` 32-bitowych systemu Windows, `IA64` dla 64-bitowego systemu Windows oraz `Itanium` dla procesorów Intel 64-bit.|
|`type`|Wymagany. W celu zapewnienia zgodności z technologią instalacji równoległej systemu Windows. Jedyna dozwolona wartość to `win32` .|

## <a name="remarks"></a>Uwagi

## <a name="example"></a>Przykład
 Poniższy przykład kodu ilustruje `assemblyIdentity` element w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeście wdrożenia. Ten przykład kodu jest częścią większego przykładu dostarczonego w temacie [manifestu wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md) .

```xml
<!-- Identify the deployment. -->
<assemblyIdentity
  name="My Application Deployment.app"
  version="1.0.0.0"
  publicKeyToken="43cb1e8e7a352766"
  language="neutral"
  processorArchitecture="x86"
  xmlns="urn:schemas-microsoft-com:asm.v1" />
```

## <a name="see-also"></a>Zobacz też
- [Manifest wdrożenia ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [\<assemblyIdentity> postaci](../deployment/assemblyidentity-element-clickonce-application.md)