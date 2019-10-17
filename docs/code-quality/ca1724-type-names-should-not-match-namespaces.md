---
title: 'CA1724: Nazwy typów nie powinny odpowiadać nazwom pól'
ms.date: 09/28/2018
ms.topic: reference
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e5ab83a73da6035df985b93294f850b5a49248f
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72443450"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: nazwy typów nie powinny być zgodne z przestrzeniami nazw

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Kategoria|Microsoft. nazewnictwo|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Nazwa typu jest zgodna z nazwą przestrzeni nazw przywoływanej, która ma co najmniej jeden typ widoczny na zewnątrz. W porównaniu do nazw nie jest rozróżniana wielkość liter.

## <a name="rule-description"></a>Opis reguły

Nazwy typów utworzone przez użytkownika nie powinny być zgodne z nazwami przywoływanych obszarów nazw, które mają typy widoczne na zewnątrz. Naruszenie tej reguły może zmniejszyć użyteczność biblioteki.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Zmień nazwę typu na taki, który nie jest zgodny z nazwą przywoływanej przestrzeni nazw, która ma typy widoczne na zewnątrz.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

W przypadku nowych rozwiązań nie występują żadne znane scenariusze, w których należy pominąć ostrzeżenie z tej reguły. Przed pominięciem ostrzeżenia należy uważnie rozważyć, w jaki sposób użytkownicy biblioteki mogą być pomylone ze zgodną nazwą. W przypadku bibliotek wysyłkowych może być konieczne pominięcie ostrzeżenia z tej reguły.
