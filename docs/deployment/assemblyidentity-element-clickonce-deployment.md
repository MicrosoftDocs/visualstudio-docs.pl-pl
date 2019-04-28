---
title: '&lt;assemblyIdentity&gt; — Element (wdrażanie ClickOnce) | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929067"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;assemblyIdentity&gt; — element (wdrażanie ClickOnce)
Określa podstawowy zestaw z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.

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

## <a name="elements-and-attributes"></a>Atrybuty i elementy
 `assemblyIdentity` Element jest wymagany. Go nie zawiera żadnych elementów podrzędnych i ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`name`|Wymagana. Identyfikuje zrozumiałą nazwę wdrożenia w celach informacyjnych.<br /><br /> Jeśli `name` zawiera znaki specjalne, takie jak pojedynczym lub podwójnym cudzysłowie, aplikacja może zakończyć się niepowodzeniem do aktywowania.|
|`version`|Wymagana. Określa numer wersji zestawu, w następującym formacie: `major.minor.build.revision`.<br /><br /> Ta wartość muszą być zwiększane w manifeście zaktualizowane w celu wyzwolenia aktualizacji aplikacji.|
|`publicKeyToken`|Wymagana. Określa ciąg szesnastkowy 16-znakowy, który reprezentuje ostatnie 8 bajtów wartości skrótu SHA-1 klucza publicznego, w ramach której manifest wdrożenia jest podpisany. Klucz publiczny, który jest używany do podpisywania musi wynosić 2048 bitów lub nowszej.<br /><br /> Mimo że zaleca się podpisywanie zestawu, ale opcjonalny, ten atrybut jest wymagany. Jeśli zestaw jest podpisany, możesz Kopiowanie wartości z podpisem własnym zestawu lub użyj wartości "fikcyjny" samych zer.|
|`processorArchitecture`|Wymagana. Określa procesor. Prawidłowe wartości to `msil` dla wszystkich procesorów `x86` dla Windows 32-bitowych `IA64` dla Windows 64-bitowych i `Itanium` dla procesorów Intel 64-bitowych procesorach Itanium.|
|`type`|Wymagana. Dla zachowania zgodności z technologii side-by-side instalacji Windows. Jest to jedyna wartość dozwolone `win32`.|

## <a name="remarks"></a>Uwagi

## <a name="example"></a>Przykład
 W poniższym przykładzie kodu pokazano `assemblyIdentity` element [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest wdrożenia. Ten przykład kodu jest częścią większego przykładu przewidzianego dla [manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md) tematu.

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

## <a name="see-also"></a>Zobacz także
- [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [\<assemblyIdentity > element](../deployment/assemblyidentity-element-clickonce-application.md)