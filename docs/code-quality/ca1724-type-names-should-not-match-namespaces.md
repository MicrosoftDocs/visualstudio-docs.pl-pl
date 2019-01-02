---
title: 'CA1724: Nazwy typów nie powinny odpowiadać nazwom'
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c28bf4af55e1c12045357a76e3488ff4083fcee5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848944"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: Nazwy typów nie powinny odpowiadać nazwom

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Nazwa typu, który jest zgodny z nazwą odwołania obszaru nazw, który ma co najmniej jeden typ widoczny na zewnątrz. Porównanie nazwa jest rozróżniana wielkość liter.

## <a name="rule-description"></a>Opis reguły

Nazwy typów utworzonych przez użytkownika nie powinny odpowiadać nazwy przywoływane obszary nazw, które mają typy widoczne na zewnątrz. Naruszenie tej zasady może zmniejszyć użyteczność biblioteki.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Zmień nazwę typu w taki sposób, że nie jest zgodna nazwa przestrzeni nazw, do którego istnieje odwołanie, zawierający typy widoczne na zewnątrz.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

W nowych wdrożeniach Brak znanego scenariusze wystąpić, gdy trzeba Pomijaj ostrzeżeń dla tej reguły. Zanim można pominąć to ostrzeżenie, zastanów się, jak użytkownicy biblioteki mogą być pomylone według tej nazwy. Do wysłania biblioteki, trzeba będzie Pomijaj ostrzeżeń dla tej reguły.