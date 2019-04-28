---
title: '&lt;assemblyIdentity&gt; — Element (aplikacja ClickOnce) | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62900670"
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;assemblyIdentity&gt; — element (aplikacja ClickOnce)
Identyfikuje aplikacji wdrożonej w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia.

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

## <a name="elements-and-attributes"></a>Atrybuty i elementy
 `assemblyIdentity` Element jest wymagany. Go nie zawiera żadnych elementów podrzędnych i ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`Name`|Wymagana. Określa nazwę aplikacji.<br /><br /> Jeśli `Name` zawiera znaki specjalne, takie jak pojedynczym lub podwójnym cudzysłowie, aplikacja może zakończyć się niepowodzeniem do aktywowania.|
|`Version`|Wymagana. Określa numer wersji aplikacji w następującym formacie: `major.minor.build.revision`|
|`publicKeyToken`|Opcjonalna. Określa ciąg szesnastkowy 16-znakowy, który reprezentuje ostatnie 8 bajtów `SHA-1` wyznaczania wartości skrótu wartość klucza publicznego, w ramach której aplikacja lub zestaw jest podpisany. Klucz publiczny, który jest używany do podpisywania katalogu musi wynosić 2048 bitów lub nowszej.<br /><br /> Mimo że zaleca się podpisywanie zestawu, ale opcjonalny, ten atrybut jest wymagany. Jeśli zestaw jest podpisany, możesz Kopiowanie wartości z podpisem własnym zestawu lub użyj wartości "fikcyjny" samych zer.|
|`processorArchitecture`|Wymagana. Określa procesor. Prawidłowe wartości to `msil` dla wszystkich procesorów `x86` dla Windows 32-bitowych `IA64` dla Windows 64-bitowych i `Itanium` dla procesorów Intel 64-bitowych procesorach Itanium.|
|`language`|Wymagana. Identyfikuje części dwóch kodów języka (na przykład `en-US`) zestawu. Tego elementu jest `asmv2` przestrzeni nazw. Jeśli nie zostanie podany, wartość domyślna to `neutral`.|

## <a name="examples"></a>Przykłady

### <a name="description"></a>Opis
 W poniższym przykładzie kodu pokazano `assemblyIdentity` element [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestu aplikacji. Ten przykład kodu jest częścią większego przykładu przewidzianego w [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md).

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

## <a name="see-also"></a>Zobacz także
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<assemblyIdentity > element](../deployment/assemblyidentity-element-clickonce-deployment.md)