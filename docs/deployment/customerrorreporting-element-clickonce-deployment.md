---
title: '&lt;customErrorReporting&gt; — Element (wdrażanie ClickOnce) | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7254f5735be3efa45b7ba3be0541996cb6c2cc69
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54997640"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;customErrorReporting&gt; — element (wdrażanie ClickOnce)
Określa identyfikator URI do wyświetlenia, gdy wystąpi błąd.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<customErrorReporting  
   uri  
/>  
```  
  
## <a name="remarks"></a>Uwagi  
 Ten element jest opcjonalny. Bez tego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Wyświetla okno dialogowe błędu przedstawiający stos wyjątków. Jeśli `customErrorReporting` element jest obecny, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zamiast tego wyświetli wskazywanym przez identyfikator URI `uri` parametru. Docelowy identyfikator URI będzie zawierać klasy wewnętrzny wyjątek, komunikat wyjątku wewnętrznego i klasy wyjątków zewnętrzne jako parametry.  
  
 Ten element umożliwia dodawanie raportów o błędach funkcji do aplikacji. Ponieważ wygenerowanego identyfikatora URI zawiera informacje o typie błędu, witryny sieci Web można analizować tych informacji i ekran, na przykład odpowiednie ekranu rozwiązywania problemów.  
  
## <a name="example"></a>Przykład  
 Poniższy fragment kodu przedstawia `customErrorReporting` elementu, wraz z wygenerowanego identyfikatora URI może powodować generowanie.  
  
```xml
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md)