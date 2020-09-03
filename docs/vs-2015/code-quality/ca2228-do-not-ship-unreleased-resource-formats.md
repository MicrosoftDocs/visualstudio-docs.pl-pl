---
title: 'CA2228: Nie dostarczaj niezwolnionych formatów zasobów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4adcae1c1cc616cdbcf5a7aa15342d221c2f4300
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540585"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Nie publikuj zasobów w formatach z wersji wstępnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Plik zasobów został utworzony przy użyciu wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , która nie jest obecnie obsługiwana.

## <a name="rule-description"></a>Opis reguły
 Pliki zasobów, które zostały skompilowane przy użyciu wersji wstępnych programu, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] nie mogą być używane przez obsługiwane wersje .NET Framework.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, skompiluj zasób przy użyciu obsługiwanej wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] k.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.
