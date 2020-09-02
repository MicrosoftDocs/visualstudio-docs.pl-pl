---
title: '&lt;assemblyIdentity, &gt; element (Aplikacja ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7870fcf644103ec7f048a809e439cb962f63bd07
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62900670"
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;assemblyIdentity, &gt; element (Aplikacja ClickOnce)
Identyfikuje aplikację wdrożoną we [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożeniu.

## <a name="syntax"></a>Składnia

```xml

      <assemblyIdentity
   name
   version
   publicKeyToken
   processorArchitecture
   language
/>
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `assemblyIdentity`Element jest wymagany. Nie zawiera żadnych elementów podrzędnych i ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`Name`|Wymagany. Identyfikuje nazwę aplikacji.<br /><br /> Jeśli `Name` zawiera znaki specjalne, takie jak pojedyncze lub podwójne cudzysłowy, uruchomienie aplikacji może się nie powieść.|
|`Version`|Wymagany. Określa numer wersji aplikacji w następującym formacie: `major.minor.build.revision`|
|`publicKeyToken`|Opcjonalny. Określa 16-znakowy ciąg szesnastkowy, który reprezentuje ostatnie 8 bajtów `SHA-1` wartości skrótu klucza publicznego, w którym aplikacja lub zestaw są podpisane. Klucz publiczny używany do podpisywania wykazu musi mieć wartość 2048 bitów lub większą.<br /><br /> Chociaż podpisywanie zestawu jest zalecane, ale opcjonalne, ten atrybut jest wymagany. Jeśli zestaw nie jest podpisany, należy skopiować wartość z zestawu z podpisem własnym lub użyć wartości "fikcyjnej" wszystkich zer.|
|`processorArchitecture`|Wymagany. Określa procesor. Prawidłowe wartości są `msil` dla wszystkich procesorów, `x86` 32-bitowych systemu Windows, `IA64` dla 64-bitowego systemu Windows oraz `Itanium` dla procesorów Intel 64-bit.|
|`language`|Wymagany. Identyfikuje dwa kody języka części (na przykład `en-US` ) zestawu. Ten element znajduje się w `asmv2` przestrzeni nazw. Jeśli nie zostanie określony, wartość domyślna to `neutral` .|

## <a name="examples"></a>Przykłady

### <a name="description"></a>Opis
 Poniższy przykład kodu ilustruje `assemblyIdentity` element w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeście aplikacji. Ten przykład kodu jest częścią większego przykładu dostarczonego w [manifeście aplikacji ClickOnce](../deployment/clickonce-application-manifest.md).

### <a name="code"></a>Kod

```xml
<asmv1:assemblyIdentity
  name="My Application Deployment.exe"
  version="1.0.0.0"
  publicKeyToken="43cb1e8e7a352766"
  language="neutral"
  processorArchitecture="x86"
  type="win32" />
```

## <a name="see-also"></a>Zobacz też
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<assemblyIdentity> postaci](../deployment/assemblyidentity-element-clickonce-deployment.md)