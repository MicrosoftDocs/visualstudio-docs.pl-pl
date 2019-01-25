---
title: 'CA2228: Dostarczaj niepublikowanych formatów zasobów | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2e49953a95da10653cd29132e003fa36de5b8d4c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54792400"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Nie publikuj zasobów w formatach z wersji wstępnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Plik zasobów został zbudowany przy użyciu wersji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , nie jest obecnie obsługiwane.

## <a name="rule-description"></a>Opis reguły
 Pliki zasobów, które zostały utworzone przy użyciu wersji wstępnych [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] może nie być użyteczne z obsługiwanymi wersjami programu .NET Framework.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, tworzenie ten zasób, używając obsługiwanej wersji programu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]k.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.
