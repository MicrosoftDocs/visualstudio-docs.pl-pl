---
title: 'CA1726: Używaj preferowanych terminów'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 469025e5856f284f4d8887b351865a0304e4d35c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797161"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Używaj preferowanych terminów

|||
|-|-|
|TypeName|UsePreferredTerms|
|CheckId|CA1726|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Istotne — gdy wywoływane zestawów<br /><br /> Podziału non - gdy wywoływane w parametrach typu|

## <a name="cause"></a>Przyczyna

Nazwa widocznego na zewnątrz identyfikatora zawiera termin, dla którego istnieje alternatywny, preferowany zamiennik. Alternatywnie nazwa zawiera określenie Flag lub flag.

## <a name="rule-description"></a>Opis reguły

Ta reguła analizuje identyfikator na tokeny. Każdy pojedynczy token i ciągłe kombinację dwóch tokenu jest porównywany warunki, które są wbudowane w regule, jak i w sekcji uznane za przestarzałe słowników niestandardowych. W poniższej tabeli przedstawiono warunki, które są wbudowane w zasady i ich preferowany alternatyw.

|Przestarzałe termin|Preferowany termin|
|-------------------|--------------------|
|`Arent`|`AreNot`|
|`Cancelled`|`Canceled`|
|`Cant`|`Cannot`|
|`ComPlus`|`EnterpriseServices`|
|`Couldnt`|`CouldNot`|
|`Didnt`|`DidNot`|
|`Doesnt`|`DoesNot`|
|`Dont`|`DoNot`|
|`Flag` lub `Flags`|Nie ma żadnych zastąpienie terminu. Nie używać.|
|`Hadnt`|`HadNot`|
|`Hasnt`|`HasNot`|
|`Havent`|`HaveNot`|
|`Indices`|`Indexes`|
|`Isnt`|`IsNot`|
|`LogIn`|`LogOn`|
|`LogOut`|`LogOff`|
|`Shouldnt`|`ShouldNot`|
|`SignOn`|`SignIn`|
|`SignOff`|`SignOut`|
|`Wasnt`|`WasNot`|
|`Werent`|`WereNot`|
|`Wont`|`WillNot`|
|`Wouldnt`|`WouldNot`|
|`Writeable`|`Writable`|

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Zamień termin na preferowany termin alternatywny.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżeń dla tej reguły, tylko wtedy, gdy nazwa identyfikatora jest zamierzone i dotyczy oryginalnej termin zamiast preferowany termin.

## <a name="related-rules"></a>Powiązane reguły
 [Ostrzeżenia dotyczące nazewnictwa](../code-quality/naming-warnings.md)