---
title: 'CA1726: Użyj preferowanych warunków | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 96e0614bc5c08c83008af4e67a2aa865f08f74f3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547813"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Używaj preferowanych terminów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [CA1726: use preferowane terminy](/visualstudio/code-quality/ca1726-use-preferred-terms).

|Element|Wartość|
|-|-|
|TypeName|UsePreferredTerms|
|CheckId|CA1726|
|Kategoria|Microsoft. nazewnictwo|
|Zmiana kluczowa|Przerywanie — gdy są uruchamiane w zestawach<br /><br /> Rozdzielenie — gdy jest uruchamiany w parametrach typu|

## <a name="cause"></a>Przyczyna
 Nazwa widocznego na zewnątrz identyfikatora zawiera termin, dla którego istnieje alternatywny, preferowany zamiennik. Alternatywnie, nazwa zawiera flagę lub flagi warunku.

## <a name="rule-description"></a>Opis reguły
 Ta reguła analizuje identyfikator w tokenach. Każdy pojedynczy token i każda ciągła kombinacja podwójnego tokenu jest porównywana z terminami, które są wbudowane w regułę i w sekcji przestarzałe w dowolnym słowniku niestandardowym. W poniższej tabeli przedstawiono warunki, które są wbudowane w regułę i ich preferowane alternatywy.

|Przestarzały termin|Preferowany termin|
|-------------------|--------------------|
|`Arent`|`AreNot`|
|`Cancelled`|`Canceled`|
|`Cant`|`Cannot`|
|`ComPlus`|`EnterpriseServices`|
|`Couldnt`|`CouldNot`|
|`Didnt`|`DidNot`|
|`Doesnt`|`DoesNot`|
|`Dont`|`DoNot`|
|`Flag` lub `Flags`|Nie istnieje termin zastępczy. Nie używaj.|
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
 Aby naprawić naruszenie tej zasady, należy zamienić termin na preferowany termin alternatywny.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń ostrzeżenie z tej reguły tylko wtedy, gdy nazwa identyfikatora jest zacelowa i odnosi się do oryginalnego terminu, a nie od preferowanego okresu.

## <a name="related-rules"></a>Powiązane reguły
 [Ostrzeżenia dotyczące nazewnictwa](../code-quality/naming-warnings.md)
