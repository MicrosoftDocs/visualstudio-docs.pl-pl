---
title: 'CA1724: nazwy typów nie powinny być zgodne z przestrzeniami nazw | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 53c99e34bf253b0962d054685ce637c3849a2857
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671595"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: Nazwy typów nie powinny odpowiadać nazwom pól
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Kategoria|Microsoft. nazewnictwo|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Nazwa typu jest zgodna [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] nazw przestrzeni nazw w porównaniu do wielkości liter.

## <a name="rule-description"></a>Opis reguły
 Nazwy typów nie powinny być zgodne z nazwami przestrzeni nazw, które są zdefiniowane w bibliotece klas [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Naruszenie tej zasady może zmniejszyć użyteczność biblioteki.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Wybierz nazwę typu, która nie jest zgodna z nazwą [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] nazw biblioteki klas.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 W przypadku nowych rozwiązań nie występują żadne znane scenariusze, w których należy pominąć ostrzeżenie z tej reguły. Przed pominięciem ostrzeżenia należy uważnie rozważyć, w jaki sposób użytkownicy biblioteki mogą być pomylone ze zgodną nazwą. W przypadku bibliotek wysyłkowych może być konieczne pominięcie ostrzeżenia z tej reguły.
