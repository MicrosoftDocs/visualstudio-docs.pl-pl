---
title: Odmowa dostępu | Dokumentacja firmy Microsoft
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
- VS.WebClient.Help.SCRIPT5
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9b49f60395a853d7dfda91738ccccaba9d585b46
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295166"
---
# <a name="access-is-denied"></a>Odmowa dostępu
Skrypt próbował uzyskać dostęp do danych ze źródła innego niż host bieżącej strony. Te Same zasady pochodzenia następuje programu Internet Explorer i innych przeglądarek umożliwia skryptów, aby uzyskać dostęp do danych tylko z źródeł za pomocą tego samego schematu, hosta i portu, adresu URL bieżącej strony.  
  
 Na przykład, jeśli bieżąca strona jest `https://employees.mycompany.com`, nie masz dostępu do danych z następującymi adresami URL:  
  
-   `http://data.contoso.com`, ponieważ korzysta ona z protokołu HTTP zamiast HTTPS.  
  
-   `https://somedatasource.com`, ponieważ jest w innej domenie.  
  
-   `https://employees.mycompany.com:8888`, ponieważ używa ona inny port.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Sprawdź, czy próbujesz wywołać interfejs API obsługuje JSONP lub mechanizmu CORS są dwie opcje umożliwiające bezpieczne skryptów cross-origin.  
  
-   Jeśli próbujesz wywołać interfejs API REST, Refaktoryzuj tego wywołania w kodzie po stronie serwera, a następnie udostępnić nowy punkt końcowy REST dla skryptów po stronie klienta.  
  
     Aby uzyskać dodatkowe informacje Wyszukaj dokumentację w trybie online związane z zasadami tego samego źródła, JSONP i mechanizmu CORS.
