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
ms.openlocfilehash: aa0b73b6608f0dfd5daa4b770b7d780e64704c99
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544433"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: Nazwy typów nie powinny być takie same jak nazwy przestrzeni nazw
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Kategoria|Microsoft. nazewnictwo|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Nazwa typu pasuje do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] nazw przestrzeni nazw w porównaniu z uwzględnieniem wielkości liter.

## <a name="rule-description"></a>Opis reguły
 Nazwy typów nie powinny być zgodne z nazwami przestrzeni nazw, które są zdefiniowane w [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] bibliotece klas. Naruszenie tej zasady może zmniejszyć użyteczność biblioteki.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Wybierz nazwę typu, która nie jest zgodna z nazwą [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] przestrzeni nazw biblioteki klas.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 W przypadku nowych rozwiązań nie występują żadne znane scenariusze, w których należy pominąć ostrzeżenie z tej reguły. Przed pominięciem ostrzeżenia należy uważnie rozważyć, w jaki sposób użytkownicy biblioteki mogą być pomylone ze zgodną nazwą. W przypadku bibliotek wysyłkowych może być konieczne pominięcie ostrzeżenia z tej reguły.
