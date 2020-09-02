---
title: '&lt;customErrorReporting, &gt; element (wdrażanie ClickOnce) | Microsoft Docs'
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
ms.openlocfilehash: 6d42bd1f7304d9f50b6334d9ac8ddd4f626605d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62900374"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;customErrorReporting, &gt; element (wdrażanie ClickOnce)
Określa identyfikator URI, który ma być wyświetlany w przypadku wystąpienia błędu.

## <a name="syntax"></a>Składnia

```xml
<customErrorReporting
   uri
/>
```

## <a name="remarks"></a>Uwagi
 Ten element jest opcjonalny. Bez niej, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wyświetla okno dialogowe błędu, które przedstawia stos wyjątków. Jeśli `customErrorReporting` element jest obecny, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zamiast niego zostanie wyświetlony identyfikator URI wskazywany przez `uri` parametr. Docelowy identyfikator URI będzie zawierać klasę zewnętrznego wyjątku, klasę wyjątku wewnętrznego i komunikat wyjątku wewnętrznego jako parametry.

 Ten element umożliwia dodanie funkcji raportowania błędów do aplikacji. Ponieważ wygenerowany identyfikator URI zawiera informacje o typie błędu, witryna sieci Web może analizować te informacje i wyświetlać, na przykład odpowiedni ekran rozwiązywania problemów.

## <a name="example"></a>Przykład
 Poniższy fragment kodu przedstawia `customErrorReporting` element wraz z wygenerowanym identyfikatorem URI, który może zostać utworzony.

```xml
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />

Example Generated Error:
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.
```

## <a name="see-also"></a>Zobacz też
- [Manifest wdrożenia ClickOnce](../deployment/clickonce-deployment-manifest.md)