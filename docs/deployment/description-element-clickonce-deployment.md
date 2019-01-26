---
title: '&lt;Opis&gt; — Element (wdrażanie ClickOnce) | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 6c926da377688b1248daa01f015cda7914434a36
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013902"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;Opis&gt; — element (wdrażanie ClickOnce)
Określa informacje o aplikacji, które pozwala utworzyć obecności powłoki i **apletu Dodaj lub usuń programy** w Panelu sterowania.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## <a name="elements-and-attributes"></a>Atrybuty i elementy  
 `description` Element jest wymagany i znajduje się w `urn:schemas-microsoft-com:asm.v1` przestrzeni nazw. Go nie zawiera żadnych elementów podrzędnych i ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`publisher`|Wymagana. Określa nazwę firmy, używane do umieszczenia ikony w Windows **Start** menu i **apletu Dodaj lub usuń programy** w Panelu sterowania, gdy wdrożenie jest skonfigurowane do instalacji.|  
|`product`|Wymagana. Identyfikuje Pełna nazwa produktu. Używane jako tytuł na ikonę zainstalowane w Windows **Start** menu.|  
|`suiteName`|Opcjonalna. Identyfikuje podfolder w `publisher` folderu w Windows **Start** menu.|  
|`supportUrl`|Opcjonalna. Określa adres URL pomocy technicznej, która jest wyświetlana w **apletu Dodaj lub usuń programy** w Panelu sterowania. Skrót do tego adresu URL tworzona jest również obsługę aplikacji w Windows **Start** menu, gdy wdrożenie jest skonfigurowane do instalacji.|  
  
## <a name="remarks"></a>Uwagi  
 Opis elementu jest wymagany we wszystkich konfiguracjach wdrażania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu pokazano `description` element [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest wdrożenia. Ten przykład kodu jest częścią większego przykładu przewidzianego dla [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md) tematu.  
  
```xml  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md)