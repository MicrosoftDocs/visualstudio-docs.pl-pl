---
title: '&lt;assemblyIdentity, &gt; element (wdrażanie ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bfc2ff97a2eb465fe7306ebe368a20e2a7fd8638
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155725"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;assemblyIdentity, &gt; element (wdrażanie ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikuje podstawowy zestaw [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
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
 Poniższy przykład kodu ilustruje `assemblyIdentity` element w [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifeście wdrożenia. Ten przykład kodu jest częścią większego przykładu dostarczonego w temacie [manifestu wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md) .  
  
```  
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
 [Manifest wdrożenia ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [\<assemblyIdentity> Postaci](../deployment/assemblyidentity-element-clickonce-application.md)
