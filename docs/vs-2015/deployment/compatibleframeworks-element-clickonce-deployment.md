---
title: '&lt;compatibleFrameworks&gt; — Element (wdrażanie ClickOnce) | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675412"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks&gt; — Element (wdrażanie ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikuje wersje programu .NET Framework, gdzie tę aplikację można instalować i uruchamiać.  
  
> [!NOTE]
> [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14) nie obsługuje `compatibleFrameworks` elementu podczas zapisywania manifestu aplikacji, która została już podpisana za pomocą certyfikatu za pomocą [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). Zamiast tego należy użyć [Mage.exe](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
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
  
## <a name="elements-and-attributes"></a>Atrybuty i elementy  
 `compatibleFrameworks` Element jest wymagany, dla których obiektem docelowym manifesty wdrożenia [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] runtime udostępnianym przez [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] lub nowszej. `compatibleFrameworks` Elementu zawiera jeden lub więcej `framework` elementy, które określają wersje programu .NET Framework, na których można uruchomić tę aplikację. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Środowisko uruchomieniowe będzie uruchomić aplikację na pierwszy dostępny `framework` na tej liście.  
  
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
 Poniższy kod przedstawia przykład `compatibleFrameworks` element [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest wdrożenia. Tego wdrożenia można uruchomić na [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)]. Można również uruchomić na [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] jest nadzbiorem [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)].  
  
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
