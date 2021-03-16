---
description: Skrypt próbował uzyskać dostęp do danych ze źródła innego niż host bieżącej strony.
title: Odmowa dostępu | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 6be3bce0643a5892973235871191766cac140962
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571938"
---
# <a name="access-is-denied"></a>Odmowa dostępu
Skrypt próbował uzyskać dostęp do danych ze źródła innego niż host bieżącej strony. Te same zasady pochodzenia, a za pomocą programu Internet Explorer i innych przeglądarek, umożliwiają skryptom dostęp do danych tylko ze źródeł przy użyciu tego samego schematu, hosta i portu adresu URL bieżącej strony.  
  
 Jeśli na przykład bieżąca strona to `https://employees.mycompany.com` , nie możesz uzyskać dostępu do danych z następujących adresów URL:  
  
- `http://data.contoso.com`, ponieważ używa protokołu HTTP zamiast HTTPS.  
  
- `https://somedatasource.com`, ponieważ jest to inna domena.  
  
- `https://employees.mycompany.com:8888`, ponieważ używa innego portu.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Sprawdź, czy interfejs API, który próbujesz wywołać, obsługuje JSONP lub CORS, które są dwa podejścia umożliwiające bezpieczne wykonywanie skryptów między źródłami.  
  
- Jeśli próbujesz wywołać interfejs API REST, Refaktoryzacja to wywołanie kodu po stronie serwera, a następnie udostępnienie nowego punktu końcowego REST dla skryptów po stronie klienta.  
  
     Aby uzyskać dodatkowe informacje, zapoznaj się z dokumentacją online powiązaną z tymi samymi zasadami pochodzenia, JSONP i CORS.
