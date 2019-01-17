---
title: Identyfikator URI, który ma być zdekodowany jest poprawnie nie zakodowany | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d37ca55dfd701aaeba2af729511a5ae6a4fa5f4
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344385"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>Identyfikator URI, który ma być zdekodowany, nie jest poprawnie zakodowany
Podjęto próbę zdekodowania niepoprawnie sformułowany identyfikator URI (Uniform Resource Identifier). Identyfikatory URI ma specjalnej składni; Większość znaki inne niż alfanumeryczne muszą zostać zakodowane, zanim będzie można ich użyć w identyfikatorze URI. Możesz użyć `encodeURI` i `encodeURIComponent` metody w celu utworzenia identyfikatora URI ze zwykłym [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ciągu.  
  
 Pełny identyfikator URI składa się z sekwencji składników i separatorów. Ogólna postać jest:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Nazwy w nawiasy ostre oznaczają składniki z i ":", "/", ";" i "?" są używane jako separatory znaków zastrzeżonych.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że chcesz odkodować tylko prawidłowymi identyfikatorami URI. Nie można zdekodować normalne [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ciągów, ponieważ mogą one zawierać nieprawidłowych znaków.  
  
## <a name="see-also"></a>Zobacz też  
 [decodeURI — funkcja](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent, funkcja](../../javascript/reference/decodeuricomponent-function-javascript.md)