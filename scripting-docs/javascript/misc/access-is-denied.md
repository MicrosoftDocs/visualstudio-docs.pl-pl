---
title: Odmowa dostępu | Dokumentacja firmy Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 75f1bb08031769c06f7d94d4f8c120496fffc02d
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56843756"
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
