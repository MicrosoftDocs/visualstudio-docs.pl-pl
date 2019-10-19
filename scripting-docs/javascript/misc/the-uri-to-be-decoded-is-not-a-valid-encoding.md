---
title: Identyfikator URI, który ma zostać zdekodowany, nie jest prawidłowym kodowaniem | Microsoft Docs
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
ms.openlocfilehash: 99df8739137971e32c14f265460ff3f4a9c03816
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572257"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>Identyfikator URI, który ma być zdekodowany, nie jest poprawnie zakodowany
Podjęto próbę zdekodowania nieprawidłowo uformowanego identyfikatora URI (Uniform Resource Identifier). Identyfikatory URI mają specjalną składnię; Aby można było używać znaków innych niż alfanumeryczne, należy je zakodować. Przy użyciu metod `encodeURI` i `encodeURIComponent` można utworzyć identyfikator URI na podstawie normalnego [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ciągu.  
  
 Pełny identyfikator URI składa się z sekwencji składników i separatorów. Formularz ogólny:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Nazwy w nawiasach kątowych reprezentują składniki, a znaki ":", "/", ";" i "?" są zarezerwowane jako separatory.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że próbujesz zdekodować tylko prawidłowe identyfikatory URI. Nie można zdekodować zwykłych [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ciągów, ponieważ mogą one zawierać nieprawidłowe znaki.  
  
## <a name="see-also"></a>Zobacz także  
   [funkcji decodeURI](../../javascript/reference/decodeuri-function-javascript.md)  
 [decodeURIComponent, funkcja](../../javascript/reference/decodeuricomponent-function-javascript.md)