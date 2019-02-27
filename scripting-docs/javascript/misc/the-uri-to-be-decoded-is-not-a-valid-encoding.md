---
title: Identyfikator URI, który ma być zdekodowany jest poprawnie nie zakodowany | Dokumentacja firmy Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 792403a9a53f11431e87115d7a95345e316dc2ac
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56844298"
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