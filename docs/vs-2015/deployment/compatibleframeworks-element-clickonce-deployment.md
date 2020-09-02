---
title: '&lt;compatibleFrameworks, &gt; element (wdrażanie ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ef54062bd74c9395e187503dd12db1c0cd70d822
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675412"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks, &gt; element (wdrażanie ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikuje wersje .NET Framework, w których ta aplikacja może zostać zainstalowana i uruchomiona.  
  
> [!NOTE]
> [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14) nie obsługuje `compatibleFrameworks` elementu podczas zapisywania manifestu aplikacji, który został już podpisany za pomocą certyfikatu przy użyciu [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). Zamiast tego należy użyć [Mage.exe](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 `compatibleFrameworks`Element jest wymagany dla manifestów wdrożenia przeznaczonych dla [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] środowiska uruchomieniowego dostarczonego przez [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] lub później. `compatibleFrameworks`Element zawiera jeden lub więcej `framework` elementów, które określają wersje .NET Framework, w których ta aplikacja może zostać uruchomiona. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Środowisko uruchomieniowe uruchomi aplikację na pierwszej dostępnej `framework` z tej listy.  
  
 Poniższa tabela zawiera listę atrybutów obsługiwanych przez `compatibleFrameworks` element.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`S` `upportUrl`|Opcjonalny. Określa adres URL, pod którym można pobrać preferowaną zgodną .NET Framework wersję.|  
  
## <a name="framework"></a>szablon  
 Wymagany. W poniższej tabeli wymieniono atrybuty obsługiwane przez `framework` element.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`targetVersion`|Wymagany. Określa numer wersji .NET Framework docelowej.|  
|`profile`|Wymagany. Określa profil .NET Framework docelowej.|  
|`supportedRuntime`|Wymagany. Określa numer wersji środowiska uruchomieniowego skojarzonego z .NET Framework docelowej.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu przedstawia `compatibleFrameworks` element w [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifeście wdrożenia. To wdrożenie można uruchomić na serwerze [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] . Można go również uruchomić na, [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] ponieważ jest nadzbiorem [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] .  
  
```  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest wdrożenia ClickOnce](../deployment/clickonce-deployment-manifest.md)
