---
description: Podjęto próbę zdekodowania nieprawidłowo uformowanego identyfikatora URI.
title: Identyfikator URI, który ma zostać zdekodowany, nie jest prawidłowym kodowaniem | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: db9d2f89a193ca4542ff5d1ca5ed5c2ae6419f53
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571990"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>Identyfikator URI, który ma być zdekodowany, nie jest poprawnie zakodowany
Podjęto próbę zdekodowania nieprawidłowo uformowanego identyfikatora URI (Uniform Resource Identifier). Identyfikatory URI mają specjalną składnię; Aby można było używać znaków innych niż alfanumeryczne, należy je zakodować. Przy użyciu `encodeURI` metod i można `encodeURIComponent` utworzyć identyfikator URI z normalnego [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ciągu.  
  
 Pełny identyfikator URI składa się z sekwencji składników i separatorów. Formularz ogólny:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Nazwy w nawiasach kątowych reprezentują składniki, a znaki ":", "/", ";" i "?" są zarezerwowane jako separatory.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że próbujesz zdekodować tylko prawidłowe identyfikatory URI. Nie można zdekodować zwykłych [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ciągów, ponieważ mogą one zawierać nieprawidłowe znaki.  
  
## <a name="see-also"></a>Zobacz też  
 [decodeURI, funkcja](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/decodeuri)   
 [decodeURIComponent, funkcja](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/decodeuricomponent)
