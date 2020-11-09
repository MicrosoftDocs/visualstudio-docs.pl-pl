---
title: '&lt;compatibleFrameworks, &gt; element (wdrażanie ClickOnce) | Microsoft Docs'
description: Element compatibleFrameworks identyfikuje wersje .NET Framework, w których ta aplikacja może zostać zainstalowana i uruchomiona.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5da9819cd3df667be5e8fa04372684f82762c037
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383069"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks, &gt; element (wdrażanie ClickOnce)
Identyfikuje wersje .NET Framework, w których ta aplikacja może zostać zainstalowana i uruchomiona.

> [!NOTE]
> [*MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) nie obsługuje `compatibleFrameworks` elementu podczas zapisywania manifestu aplikacji, który został już podpisany za pomocą certyfikatu przy użyciu [*MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Zamiast tego należy użyć [*Mage.exe*](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

## <a name="syntax"></a>Składnia

```xml
<compatibleFrameworks
      SupportUrl> 
   <framework
      targetVersion
      profile
      supportedRuntime
   /> 
</ compatibleFrameworks>
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `compatibleFrameworks`Element jest wymagany dla manifestów wdrożenia przeznaczonych dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] środowiska uruchomieniowego, które są dostępne w .NET Framework 4 lub nowszych. `compatibleFrameworks`Element zawiera jeden lub więcej `framework` elementów, które określają wersje .NET Framework, w których ta aplikacja może zostać uruchomiona. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Środowisko uruchomieniowe uruchomi aplikację na pierwszej dostępnej `framework` z tej listy.

 Poniższa tabela zawiera listę atrybutów obsługiwanych przez `compatibleFrameworks` element.

|Atrybut|Opis|
|---------------|-----------------|
|`S` `upportUrl`|Opcjonalny. Określa adres URL, pod którym można pobrać preferowaną zgodną .NET Framework wersję.|

## <a name="framework"></a>szablon
 Wymagane. W poniższej tabeli wymieniono atrybuty obsługiwane przez `framework` element.

|Atrybut|Opis|
|---------------|-----------------|
|`targetVersion`|Wymagane. Określa numer wersji .NET Framework docelowej.|
|`profile`|Wymagane. Określa profil .NET Framework docelowej.|
|`supportedRuntime`|Wymagane. Określa numer wersji środowiska uruchomieniowego skojarzonego z .NET Framework docelowej.|

## <a name="remarks"></a>Uwagi

## <a name="example"></a>Przykład
 Poniższy przykład kodu przedstawia `compatibleFrameworks` element w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeście wdrożenia. To wdrożenie można uruchomić na serwerze [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] . Można go również uruchomić na .NET Framework 4, ponieważ jest nadzbiorem [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] .

```xml
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">
  <framework
      targetVersion="4.0"
      profile="Client"
      supportedRuntime="4.0.30319" />
</compatibleFrameworks>
```

## <a name="see-also"></a>Zobacz też
- [Manifest wdrożenia ClickOnce](../deployment/clickonce-deployment-manifest.md)