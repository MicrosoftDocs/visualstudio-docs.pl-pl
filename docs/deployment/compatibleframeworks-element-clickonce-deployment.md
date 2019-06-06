---
title: '&lt;compatibleFrameworks&gt; — Element (wdrażanie ClickOnce) | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 99db3d51414197df469aaa2eabe97e0967c31b05
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746033"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks&gt; — element (wdrażanie ClickOnce)
Identyfikuje wersje programu .NET Framework, gdzie tę aplikację można instalować i uruchamiać.

> [!NOTE]
> [*MageUI.exe* ](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) nie obsługuje `compatibleFrameworks` elementu podczas zapisywania manifestu aplikacji, która została już podpisana za pomocą certyfikatu za pomocą [ *MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Zamiast tego należy użyć [ *Mage.exe*](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

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

## <a name="elements-and-attributes"></a>Atrybuty i elementy
 `compatibleFrameworks` Element jest wymagany, dla których obiektem docelowym manifesty wdrożenia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] runtime udostępnianym przez .NET Framework 4 lub nowszej. `compatibleFrameworks` Elementu zawiera jeden lub więcej `framework` elementy, które określają wersje programu .NET Framework, na których można uruchomić tę aplikację. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Środowisko uruchomieniowe będzie uruchomić aplikację na pierwszy dostępny `framework` na tej liście.

 Poniższa tabela zawiera listę atrybutów, `compatibleFrameworks` obsługuje element.

|Atrybut|Opis|
|---------------|-----------------|
|`S``upportUrl`|Opcjonalna. Określa adres URL, gdzie można pobrać preferowanych zgodnej wersji programu .NET Framework.|

## <a name="framework"></a>szablon
 Wymagana. W poniższej tabeli przedstawiono atrybuty, `framework` obsługuje element.

|Atrybut|Opis|
|---------------|-----------------|
|`targetVersion`|Wymagana. Określa numer wersji obiektu docelowego .NET Framework.|
|`profile`|Wymagana. Określa profil docelową aplikację .NET Framework.|
|`supportedRuntime`|Wymagana. Określa numer wersji środowiska uruchomieniowego, skojarzone z docelową aplikację .NET Framework.|

## <a name="remarks"></a>Uwagi

## <a name="example"></a>Przykład
 Poniższy kod przedstawia przykład `compatibleFrameworks` element [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest wdrożenia. Tego wdrożenia można uruchomić na [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)]. Jego można również uruchomić na .NET Framework 4 jest podzestawem [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].

```xml
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">
  <framework
      targetVersion="4.0"
      profile="Client"
      supportedRuntime="4.0.30319" />
</compatibleFrameworks>
```

## <a name="see-also"></a>Zobacz także
- [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md)